# Práctica UD07: Pipeline CI/CD con ASP.NET Core, Blazor y Playwright

## 🏢 Contexto

Tienes una **API RESTful desarrollada con ASP.NET Core 10 y C# 14** con frontend en Blazor Server. Necesitas implementar un pipeline CI/CD completo que automatice el build, tests (NUnit, integración, Playwright) y despliegue a producción.

## 🎯 Objetivos

1. Configurar pipeline de CI con GitHub Actions para .NET
2. Implementar tests unitarios (NUnit + Moq)
3. Implementar tests de integración (WebApplicationFactory)
4. Implementar tests E2E con Playwright
5. Configurar protección de ramas
6. Desplegar automáticamente a Render

---

## 📝 Tareas

### 1. Estructura del Proyecto

```
mi-api/
├── src/
│   ├── MiApi/                      # API ASP.NET Core 10
│   │   ├── Program.cs
│   │   ├── Controllers/
│   │   ├── Models/
│   │   ├── Services/
│   │   └── MiApi.csproj
│   ├── MiApi.Tests/                # Tests NUnit
│   │   ├── Controllers/
│   │   │   └── UsersControllerTests.cs
│   │   ├── Services/
│   │   └── MiApi.Tests.csproj
│   └── MiApi.Blazor/              # Frontend Blazor
│       ├── Pages/
│       └── MiApi.Blazor.csproj
├── tests/
│   └── E2E/                       # Playwright
│       ├── tests/
│       │   └── users.spec.js
│       ├── playwright.config.js
│       └── package.json
├── .github/
│   └── workflows/
│       ├── ci.yml
│       └── cd.yml
├── Dockerfile
├── docker-compose.yml
└── README.md
```

### 2. Proyectos .NET

#### 2.1. MiApi.csproj

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>
    <TargetFramework>net10.0</TargetFramework>
    <Nullable>enable</Nullable>
    <ImplicitUsings>enable</ImplicitUsings>
  </PropertyGroup>
  
  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.OpenApi" Version="10.0.0" />
    <PackageReference Include="Swashbuckle.AspNetCore" Version="6.5.0" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.InMemory" Version="10.0.0" />
  </ItemGroup>
</Project>
```

#### 2.2. MiApi.Tests.csproj (NUnit)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net10.0</TargetFramework>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
    <IsPackable>false</IsPackable>
  </PropertyGroup>
  
  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Mvc.Testing" Version="10.0.0" />
    <PackageReference Include="Microsoft.NET.Test.Sdk" Version="17.10.0" />
    <PackageReference Include="NUnit" Version="4.2.2" />
    <PackageReference Include="NUnit3TestAdapter" Version="4.6.0" />
    <PackageReference Include="Moq" Version="4.20.72" />
    <PackageReference Include="FluentAssertions" Version="6.12.0" />
  </ItemGroup>
  
  <ItemGroup>
    <ProjectReference Include="..\MiApi\MiApi.csproj" />
  </ItemGroup>
</Project>
```

---

### 3. Tests Unitarios con NUnit y Moq

```csharp
// src/MiApi.Tests/UsersControllerTests.cs
using Microsoft.AspNetCore.Mvc;
using MiApi.Controllers;
using MiApi.Services;
using Moq;
using NUnit.Framework;

namespace MiApi.Tests;

[TestFixture]
public class UsersControllerTests
{
    private Mock<IUserService> _userServiceMock;
    private UsersController _controller;

    [SetUp]
    public void Setup()
    {
        _userServiceMock = new Mock<IUserService>();
        _controller = new UsersController(_userServiceMock.Object);
    }

    [Test]
    public async Task GetUsers_ReturnsOkResult()
    {
        // Arrange
        var users = new List<User>
        {
            new User { Id = 1, Name = "Juan", Email = "juan@test.com" }
        };
        _userServiceMock.Setup(s => s.GetAllUsersAsync()).ReturnsAsync(users);

        // Act
        var result = await _controller.GetUsers();

        // Assert
        Assert.That(result, Is.TypeOf<OkObjectResult>());
        var okResult = result as OkObjectResult;
        Assert.That(okResult.Value, Is.EqualTo(users));
    }

    [Test]
    public async Task GetUser_ExistingUser_ReturnsOk()
    {
        // Arrange
        var userId = 1;
        var user = new User { Id = userId, Name = "Juan", Email = "juan@test.com" };
        _userServiceMock.Setup(s => s.GetUserByIdAsync(userId)).ReturnsAsync(user);

        // Act
        var result = await _controller.GetUser(userId);

        // Assert
        Assert.That(result, Is.TypeOf<OkObjectResult>());
    }

    [Test]
    public async Task GetUser_NonExistingUser_ReturnsNotFound()
    {
        // Arrange
        var userId = 999;
        _userServiceMock.Setup(s => s.GetUserByIdAsync(userId)).ReturnsAsync((User?)null);

        // Act
        var result = await _controller.GetUser(userId);

        // Assert
        Assert.That(result, Is.TypeOf<NotFoundResult>());
    }

    [Test]
    [TestCase("", "juan@test.com")]
    [TestCase("Juan", "")]
    public async Task CreateUser_InvalidData_ReturnsBadRequest(string name, string email)
    {
        // Arrange
        var newUser = new CreateUserDto { Name = name, Email = email };

        // Act
        var result = await _controller.CreateUser(newUser);

        // Assert
        Assert.That(result, Is.TypeOf<BadRequestResult>());
    }
}
```

---

### 4. Tests de Integración con NUnit y WebApplicationFactory

```csharp
// src/MiApi.Tests/UsersIntegrationTests.cs
using Microsoft.AspNetCore.Mvc.Testing;
using FluentAssertions;
using NUnit.Framework;

namespace MiApi.Tests.Integration;

[TestFixture]
public class UsersIntegrationTests
{
    private WebApplicationFactory<Program> _factory;
    private HttpClient _client;

    [OneTimeSetUp]
    public void OneTimeSetUp()
    {
        _factory = new WebApplicationFactory<Program>();
        _client = _factory.CreateClient();
    }

    [OneTimeTearDown]
    public void OneTimeTearDown()
    {
        _client.Dispose();
        _factory.Dispose();
    }

    [Test]
    public async Task GetUsers_ReturnsSuccessStatusCode()
    {
        // Act
        var response = await _client.GetAsync("/api/users");

        // Assert
        response.EnsureSuccessStatusCode();
    }

    [Test]
    public async Task PostUser_CreatesNewUser()
    {
        // Arrange
        var newUser = new { Name = "Test User", Email = "test@test.com" };

        // Act
        var response = await _client.PostAsJsonAsync("/api/users", newUser);

        // Assert
        response.StatusCode.Should().Be(System.Net.HttpStatusCode.Created);
    }

    [Test]
    public async Task GetUser_ReturnsNotFound_ForNonExisting()
    {
        // Act
        var response = await _client.GetAsync("/api/users/999999");

        // Assert
        response.StatusCode.Should().Be(System.Net.HttpStatusCode.NotFound);
    }
}
```

---

### 5. Tests E2E con Playwright

```javascript
// tests/e2e/users.spec.js
const { test, expect } = require('@playwright/test');

test.describe('Users E2E Tests', () => {
    test.beforeEach(async ({ page }) => {
        await page.goto('/users');
    });

    test('should display users list', async ({ page }) => {
        await page.waitForSelector('table.users-table');
        const rows = await page.locator('table.users-table tbody tr').count();
        expect(rows).toBeGreaterThan(0);
    });

    test('should create new user', async ({ page }) => {
        await page.click('button:has-text("Nuevo Usuario")');
        await page.fill('input[name="name"]', 'Juan Pérez');
        await page.fill('input[name="email"]', 'juan@test.com');
        await page.click('button:has-text("Guardar")');
        await expect(page.locator('text=Juan Pérez')).toBeVisible();
    });
});
```

```javascript
// tests/e2e/playwright.config.js
const { defineConfig } = require('@playwright/test');

module.exports = defineConfig({
    testDir: './tests',
    use: {
        baseURL: 'http://localhost:5000',
        trace: 'on-first-retry',
    },
    projects: [
        { name: 'chromium', use: { browserName: 'chromium' } },
    ],
    webServer: {
        command: 'dotnet run --project ../src/MiApi',
        url: 'http://localhost:5000',
    },
});
```

---

### 6. Pipeline CI (.github/workflows/ci.yml)

```yaml
name: CI Pipeline

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

env:
  DOTNET_VERSION: '10.0.x'

jobs:
  build:
    name: Build
    runs-on: ubuntu-latest
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup .NET
        uses: actions/setup-dotnet@v4
        with:
          dotnet-version: ${{ env.DOTNET_VERSION }}
      
      - name: Restore dependencies
        run: dotnet restore
      
      - name: Build
        run: dotnet build --configuration Release --no-restore

  test:
    name: Test & Coverage
    runs-on: ubuntu-latest
    needs: build
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup .NET
        uses: actions/setup-dotnet@v4
        with:
          dotnet-version: ${{ env.DOTNET_VERSION }}
      
      - name: Run tests with coverage
        run: dotnet test --configuration Release --collect:"XPlat Code Coverage" --verbosity minimal
      
      - name: Upload coverage report
        uses: actions/upload-artifact@v4
        with:
          name: coverage-report
          path: TestResults/
          retention-days: 7

  playwright:
    name: Playwright E2E
    runs-on: ubuntu-latest
    needs: build
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
      
      - name: Install Playwright
        run: |
          cd tests/E2E
          npm ci
          npx playwright install --with-deps chromium
      
      - name: Run Playwright tests
        run: |
          cd tests/E2E
          npx playwright test
      
      - name: Upload Playwright report
        uses: actions/upload-artifact@v4
        if: always()
        with:
          name: playwright-report
          path: tests/E2E/test-results/

  docker:
    name: Build Docker Image
    runs-on: ubuntu-latest
    needs: test
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Build Docker image
        run: docker build -t miapi:${{ github.sha }} -f Dockerfile .
      
      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKER_USERNAME }}
          password: ${{ secrets.DOCKER_PASSWORD }}
      
      - name: Push Docker image
        run: |
          docker tag miapi:${{ github.sha }} ${{ secrets.DOCKER_USERNAME }}/miapi:latest
          docker push ${{ secrets.DOCKER_USERNAME }}/miapi:latest
```

---

### 7. Pipeline CD (.github/workflows/cd.yml)

```yaml
name: CD Pipeline

on:
  push:
    branches: [main]

jobs:
  deploy-staging:
    name: Deploy to Staging
    runs-on: ubuntu-latest
    environment: staging
    
    steps:
      - name: Deploy to Render
        uses: appleboy/ssh-action@v1
        with:
          host: ${{ secrets.RENDER_HOST }}
          username: ${{ secrets.RENDER_USER }}
          key: ${{ secrets.RENDER_SSH_KEY }}
          script: |
            cd /var/www/miapi
            git pull origin main
            docker-compose pull
            docker-compose up -d --no-deps

  deploy-production:
    name: Deploy to Production
    runs-on: ubuntu-latest
    needs: deploy-staging
    environment: production
    
    steps:
      - name: Deploy to Render
        uses: appleboy/ssh-action@v1
        with:
          host: ${{ secrets.RENDER_HOST_PROD }}
          username: ${{ secrets.RENDER_USER }}
          key: ${{ secrets.RENDER_SSH_KEY_PROD }}
          script: |
            cd /var/www/miapi
            git pull origin main
            docker-compose pull
            docker-compose up -d --no-deps
      
      - name: Health check
        run: |
          sleep 30
          response=$(curl -s -o /dev/null -w "%{http_code}" https://api.midominio.com/health)
          if [ "$response" != "200" ]; then
            echo "Health check failed!"
            exit 1
          fi
```

---

### 8. Dockerfile Multi-stage

```dockerfile
# Build stage
FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build
WORKDIR /src
COPY src/**/*.csproj ./
RUN dotnet restore
COPY . .
RUN dotnet publish -c Release -o /publish

# Runtime stage
FROM mcr.microsoft.com/dotnet/aspnet:10.0 AS runtime
WORKDIR /publish
COPY --from=build /publish .
ENV ASPNETCORE_URLS=http://+:5000
EXPOSE 5000
ENTRYPOINT ["dotnet", "MiApi.dll"]
```

---

### 9. docker-compose.yml

```yaml
version: '3.8'
services:
  api:
    image: ${{ secrets.DOCKER_USERNAME }}/miapi:latest
    ports:
      - "5000:5000"
    environment:
      - ConnectionStrings__DefaultConnection=${{ secrets.DATABASE_URL }}
      - ASPNETCORE_ENVIRONMENT=Production
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:5000/health"]
      interval: 30s
      timeout: 10s
      retries: 3
```

---

## 📦 Entregables

```
📁 practica-07-cicd/
├── 📄 README.md
├── 📄 Dockerfile
├── 📄 docker-compose.yml
├── 📁 .github/
│   └── 📁 workflows/
│       ├── 📄 ci.yml
│       └── 📄 cd.yml
├── 📁 src/
│   ├── 📁 MiApi/
│   └── 📁 MiApi.Tests/
└── 📁 tests/
    └── 📁 E2E/
```

---

## 🧪 Verificación

1. **Pipeline CI**: lint → test → playwright → docker
2. **Tests**: Unitarios (NUnit), integración y E2E (Playwright)
3. **Cobertura**: > 70%
4. **Protección de ramas**: main requiere checks
5. **Deploy**: Automático a staging, manual a producción

---

