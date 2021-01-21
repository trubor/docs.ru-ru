---
title: Тестирование служб и веб-приложений ASP.NET Core
description: Архитектура микрослужб .NET для упакованных в контейнеры приложений .NET | Архитектура тестирования служб и веб-приложений ASP.NET Core в контейнерах.
ms.date: 01/13/2021
ms.openlocfilehash: dfd0a320491f92154bc9e2804d56c00120224e62
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188007"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="bf08f-103">Тестирование служб и веб-приложений ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bf08f-103">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="bf08f-104">Контроллеры — это центральный элемент любой службы ASP.NET Core API или веб-приложения ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="bf08f-104">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="bf08f-105">Поэтому необходимо убедиться в том, что они работают так, как это требуется вашему приложению.</span><span class="sxs-lookup"><span data-stu-id="bf08f-105">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="bf08f-106">Это можно сделать с помощью автоматических тестов, которые помогут также обнаружить имеющиеся ошибки до ввода контроллеров в рабочую среду.</span><span class="sxs-lookup"><span data-stu-id="bf08f-106">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="bf08f-107">Необходимо протестировать работу контроллера при допустимых и недопустимых значениях входных данных, а также проверить реакцию контроллера в сопоставлении с результатами бизнес-операции, которую он выполняет.</span><span class="sxs-lookup"><span data-stu-id="bf08f-107">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="bf08f-108">Вместе с тем вам необходимо выполнить следующие тесты микрослужб.</span><span class="sxs-lookup"><span data-stu-id="bf08f-108">However, you should have these types of tests for your microservices:</span></span>

- <span data-ttu-id="bf08f-109">Модульные тесты.</span><span class="sxs-lookup"><span data-stu-id="bf08f-109">Unit tests.</span></span> <span data-ttu-id="bf08f-110">Эти тесты позволяют проверить правильность работы отдельных компонентов приложения.</span><span class="sxs-lookup"><span data-stu-id="bf08f-110">These tests ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="bf08f-111">С помощью утверждений тестируется API компонента.</span><span class="sxs-lookup"><span data-stu-id="bf08f-111">Assertions test the component API.</span></span>

- <span data-ttu-id="bf08f-112">Интеграционные тесты.</span><span class="sxs-lookup"><span data-stu-id="bf08f-112">Integration tests.</span></span> <span data-ttu-id="bf08f-113">Такие тесты позволяют проверить правильность взаимодействия компонента с внешними устройствами, например с базами данных.</span><span class="sxs-lookup"><span data-stu-id="bf08f-113">These tests ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="bf08f-114">С помощью утверждений можно тестировать API компонента, пользовательский интерфейс и побочные эффекты от таких операций, как операции ввода-вывода в базах данных, ведение журнала и т. д.</span><span class="sxs-lookup"><span data-stu-id="bf08f-114">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

- <span data-ttu-id="bf08f-115">Функциональные тесты для каждой микрослужбы.</span><span class="sxs-lookup"><span data-stu-id="bf08f-115">Functional tests for each microservice.</span></span> <span data-ttu-id="bf08f-116">Позволяют проверить правильность работы приложения с точки зрения пользователя.</span><span class="sxs-lookup"><span data-stu-id="bf08f-116">These tests ensure that the application works as expected from the user's perspective.</span></span>

- <span data-ttu-id="bf08f-117">Тесты служб.</span><span class="sxs-lookup"><span data-stu-id="bf08f-117">Service tests.</span></span> <span data-ttu-id="bf08f-118">Позволяют проверить, были ли протестированы варианты сквозного использования служб, включая одновременное тестирование нескольких служб.</span><span class="sxs-lookup"><span data-stu-id="bf08f-118">These tests ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="bf08f-119">Для такого тестирования необходимо сначала подготовить среду.</span><span class="sxs-lookup"><span data-stu-id="bf08f-119">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="bf08f-120">В данном случае это означает запуск служб (например, с помощью docker-compose up).</span><span class="sxs-lookup"><span data-stu-id="bf08f-120">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="bf08f-121">Реализация модульных тестов для веб-API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bf08f-121">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="bf08f-122">Модульное тестирование — это тестирование части приложения изолированно от его инфраструктуры и зависимостей.</span><span class="sxs-lookup"><span data-stu-id="bf08f-122">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="bf08f-123">При модульном тестировании логики контроллера проверяется только содержимое отдельного действия или метода, а работа его зависимостей и самой платформы в целом не проверяется.</span><span class="sxs-lookup"><span data-stu-id="bf08f-123">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="bf08f-124">Модульные тесты не выявляют проблемы с взаимодействием между компонентами. Для этого предназначены интеграционные тесты.</span><span class="sxs-lookup"><span data-stu-id="bf08f-124">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="bf08f-125">Выполняя модульное тестирование действий контроллера, следует сосредоточиться только на этих действиях.</span><span class="sxs-lookup"><span data-stu-id="bf08f-125">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="bf08f-126">Модульное тестирование контроллера не учитывает такие аспекты, как фильтры, маршрутизация и привязка модели (сопоставление данных запроса с ViewModel или DTO).</span><span class="sxs-lookup"><span data-stu-id="bf08f-126">A controller unit test avoids things like filters, routing, or model binding (the mapping of request data to a ViewModel or DTO).</span></span> <span data-ttu-id="bf08f-127">Благодаря их узкой направленности модульные тесты, как правило, проще создавать, а выполняются они быстрее.</span><span class="sxs-lookup"><span data-stu-id="bf08f-127">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="bf08f-128">Правильно составленный набор модульных тестов можно выполнять часто без значительных затрат.</span><span class="sxs-lookup"><span data-stu-id="bf08f-128">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="bf08f-129">Модульные тесты реализуются на основе платформ тестирования, таких как xUnit.net MSTest, Moq и NUnit.</span><span class="sxs-lookup"><span data-stu-id="bf08f-129">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="bf08f-130">Для примера приложения eShopOnContainers мы используем xUnit.</span><span class="sxs-lookup"><span data-stu-id="bf08f-130">For the eShopOnContainers sample application, we are using xUnit.</span></span>

<span data-ttu-id="bf08f-131">При разработке модульного теста для контроллера веб-API можно создать экземпляр класса контроллера непосредственно с помощью ключевого слова new в языке C\#, таким образом, тест будет выполняться с максимально возможной скоростью.</span><span class="sxs-lookup"><span data-stu-id="bf08f-131">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="bf08f-132">В следующем примере показано, как это можно сделать в случае использования платформы тестирования [xUnit](https://xunit.net/).</span><span class="sxs-lookup"><span data-stu-id="bf08f-132">The following example shows how to do this when using [xUnit](https://xunit.net/) as the Test framework.</span></span>

```csharp
[Fact]
public async Task Get_order_detail_success()
{
    //Arrange
    var fakeOrderId = "12";
    var fakeOrder = GetFakeOrder();

    //...

    //Act
    var orderController = new OrderController(
        _orderServiceMock.Object,
        _basketServiceMock.Object,
        _identityParserMock.Object);

    orderController.ControllerContext.HttpContext = _contextMock.Object;
    var actionResult = await orderController.Detail(fakeOrderId);

    //Assert
    var viewResult = Assert.IsType<ViewResult>(actionResult);
    Assert.IsAssignableFrom<Order>(viewResult.ViewData.Model);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="bf08f-133">Реализация интеграционных и функциональных тестов для каждой микрослужбы</span><span class="sxs-lookup"><span data-stu-id="bf08f-133">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="bf08f-134">Как уже отмечалось, интеграционные и функциональные тесты имеют разное назначение.</span><span class="sxs-lookup"><span data-stu-id="bf08f-134">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="bf08f-135">Однако способы реализации тех и других при тестировании контроллеров ASP.NET Core похожи. Поэтому в этом разделе мы сосредоточимся на интеграционных тестах.</span><span class="sxs-lookup"><span data-stu-id="bf08f-135">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="bf08f-136">При интеграционном тестировании проверяется, будут ли компоненты приложения правильно работать после сборки.</span><span class="sxs-lookup"><span data-stu-id="bf08f-136">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="bf08f-137">Платформа ASP.NET Core поддерживает интеграционное тестирование с использованием платформ модульного тестирования и встроенного веб-сервера тестирования, который может использоваться для обработки запросов без нагрузки на сеть.</span><span class="sxs-lookup"><span data-stu-id="bf08f-137">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="bf08f-138">В отличие от модульного тестирования, при интеграционном тестировании часто затрагиваются различные аспекты инфраструктуры приложения, например базы данных, файловые системы, сетевые ресурсы, веб-запросы и ответы.</span><span class="sxs-lookup"><span data-stu-id="bf08f-138">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="bf08f-139">При модульном тестировании используются имитации или макеты объектов вместо реальных объектов.</span><span class="sxs-lookup"><span data-stu-id="bf08f-139">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="bf08f-140">Интеграционное тестирование предназначено для проверки того, что система работает должным образом с реальными объектами, поэтому при интеграционном тестировании не используются имитации.</span><span class="sxs-lookup"><span data-stu-id="bf08f-140">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="bf08f-141">В процесс тестирования вовлекается инфраструктура — проверяется, например, выполнение запросов на доступ к базам данных или вызов одной службы другой службой.</span><span class="sxs-lookup"><span data-stu-id="bf08f-141">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="bf08f-142">Так как при интеграционном тестировании отрабатывается значительно больший, чем при модульном тестировании, объем кода, а также из-за того, что при этом затрагивается инфраструктура элементов, такие тесты обычно выполняются на порядки медленнее, чем модульные тесты.</span><span class="sxs-lookup"><span data-stu-id="bf08f-142">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="bf08f-143">Поэтому рекомендуется ограничить количество интеграционных тестов.</span><span class="sxs-lookup"><span data-stu-id="bf08f-143">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="bf08f-144">Платформа ASP.NET Core содержит встроенный веб-сервер тестирования, который можно использовать для обработки HTTP-запросов без нагрузки на сеть. Это позволяет выполнять тесты быстрее, чем при работе с реальными веб-серверами.</span><span class="sxs-lookup"><span data-stu-id="bf08f-144">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster than when using a real web host.</span></span> <span data-ttu-id="bf08f-145">Веб-сервер тестирования (TestServer) доступен в компоненте NuGet как Microsoft.AspNetCore.TestHost.</span><span class="sxs-lookup"><span data-stu-id="bf08f-145">The test web host (TestServer) is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="bf08f-146">Его можно добавлять в проекты интеграционного тестирования и использовать для размещения приложений ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="bf08f-146">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="bf08f-147">Как можно видеть в следующем коде, при создании интеграционных тестов для контроллеров ASP.NET Core создается экземпляр контроллера на сервере тестирования.</span><span class="sxs-lookup"><span data-stu-id="bf08f-147">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="bf08f-148">Это похоже на HTTP-запрос, но выполняется быстрее.</span><span class="sxs-lookup"><span data-stu-id="bf08f-148">This functionality is comparable to an HTTP request, but it runs faster.</span></span>

```csharp
public class PrimeWebDefaultRequestShould
{
    private readonly TestServer _server;
    private readonly HttpClient _client;

    public PrimeWebDefaultRequestShould()
    {
        // Arrange
        _server = new TestServer(new WebHostBuilder()
           .UseStartup<Startup>());
           _client = _server.CreateClient();
    }

    [Fact]
    public async Task ReturnHelloWorld()
    {
        // Act
        var response = await _client.GetAsync("/");
        response.EnsureSuccessStatusCode();
        var responseString = await response.Content.ReadAsStringAsync();
        // Assert
        Assert.Equal("Hello World!", responseString);
    }
}
```

#### <a name="additional-resources"></a><span data-ttu-id="bf08f-149">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="bf08f-149">Additional resources</span></span>

- <span data-ttu-id="bf08f-150">**Стив Смит (Steve Smith). Тестирование контроллеров** (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="bf08f-150">**Steve Smith. Testing controllers** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- <span data-ttu-id="bf08f-151">**Стив Смит (Steve Smith). Тестирование интеграции** (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="bf08f-151">**Steve Smith. Integration testing** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- <span data-ttu-id="bf08f-152">**Модульное тестирование в .NET с помощью команды dotnet test** </span><span class="sxs-lookup"><span data-stu-id="bf08f-152">**Unit testing in .NET using dotnet test** </span></span>\
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- <span data-ttu-id="bf08f-153">**xUnit.net**.</span><span class="sxs-lookup"><span data-stu-id="bf08f-153">**xUnit.net**.</span></span> <span data-ttu-id="bf08f-154">Официальный сайт</span><span class="sxs-lookup"><span data-stu-id="bf08f-154">Official site.</span></span> \
    <https://xunit.net/>

- <span data-ttu-id="bf08f-155">**Основные сведения о модульных тестах**.</span><span class="sxs-lookup"><span data-stu-id="bf08f-155">**Unit Test Basics.**</span></span> \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- <span data-ttu-id="bf08f-156">**Moq**.</span><span class="sxs-lookup"><span data-stu-id="bf08f-156">**Moq**.</span></span> <span data-ttu-id="bf08f-157">Репозиторий GitHub.</span><span class="sxs-lookup"><span data-stu-id="bf08f-157">GitHub repo.</span></span> \
    <https://github.com/moq/moq>

- <span data-ttu-id="bf08f-158">**NUnit**.</span><span class="sxs-lookup"><span data-stu-id="bf08f-158">**NUnit**.</span></span> <span data-ttu-id="bf08f-159">Официальный сайт</span><span class="sxs-lookup"><span data-stu-id="bf08f-159">Official site.</span></span> \
    <https://nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="bf08f-160">Реализация тестов служб в приложении с несколькими контейнерами</span><span class="sxs-lookup"><span data-stu-id="bf08f-160">Implementing service tests on a multi-container application</span></span>

<span data-ttu-id="bf08f-161">Как уже упоминалось, при тестировании приложения с несколькими контейнерами необходимо, чтобы все микрослужбы были запущены на узле Docker или в кластере контейнера.</span><span class="sxs-lookup"><span data-stu-id="bf08f-161">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="bf08f-162">Для выполнения сквозного тестирования служб, включающего в себя множество операций, затрагивающих несколько микрослужб, требуется развертывание и запуск всего приложения на узле Docker с помощью docker-compose up (или аналогичного механизма, если используется оркестратор).</span><span class="sxs-lookup"><span data-stu-id="bf08f-162">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="bf08f-163">После запуска приложения и всех его служб вы можете выполнять сквозное интеграционное и функциональное тестирование.</span><span class="sxs-lookup"><span data-stu-id="bf08f-163">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="bf08f-164">Здесь можно использовать несколько методов.</span><span class="sxs-lookup"><span data-stu-id="bf08f-164">There are a few approaches you can use.</span></span> <span data-ttu-id="bf08f-165">В файле docker-compose.yml, который используется для развертывания приложения, на уровне решения можно развернуть точку входа, чтобы можно было использовать [тест dotnet](../../../core/tools/dotnet-test.md).</span><span class="sxs-lookup"><span data-stu-id="bf08f-165">In the docker-compose.yml file that you use to deploy the application at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="bf08f-166">Можно также использовать другой файл Compose, который будет запускать ваши тесты в целевом образе.</span><span class="sxs-lookup"><span data-stu-id="bf08f-166">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="bf08f-167">Используя другой файл Compose для интеграционного тестирования, включающего в себя микрослужбы и базы данных в контейнерах, можно гарантировать, что соответствующие данные будут всегда переведены в исходное состояние перед выполнением тестов.</span><span class="sxs-lookup"><span data-stu-id="bf08f-167">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="bf08f-168">После того как приложение Compose будет установлено и запущено, вы сможете воспользоваться преимуществами точек останова и исключений, если используется Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bf08f-168">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="bf08f-169">Интеграционные тесты можно выполнять автоматически в конвейере непрерывной интеграции Azure DevOps Services или в любой другой системе CI/CD, которая поддерживает контейнеры Docker.</span><span class="sxs-lookup"><span data-stu-id="bf08f-169">Or you can run the integration tests automatically in your CI pipeline in Azure DevOps Services or any other CI/CD system that supports Docker containers.</span></span>

## <a name="testing-in-eshoponcontainers"></a><span data-ttu-id="bf08f-170">Тестирование в eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="bf08f-170">Testing in eShopOnContainers</span></span>

<span data-ttu-id="bf08f-171">Тесты для примера приложения (eShopOnContainers) были недавно реструктуризованы, и теперь существует четыре категории:</span><span class="sxs-lookup"><span data-stu-id="bf08f-171">The reference application (eShopOnContainers) tests were recently restructured and now there are four categories:</span></span>

1. <span data-ttu-id="bf08f-172">**модульные** тесты, обычные старые модульные тесты, содержащиеся в проектах **{MicroserviceName}.UnitTests**;</span><span class="sxs-lookup"><span data-stu-id="bf08f-172">**Unit** tests, just plain old regular unit tests, contained in the **{MicroserviceName}.UnitTests** projects</span></span>

2. <span data-ttu-id="bf08f-173">**функциональные и интеграционные тесты микрослужб** с тестовыми случаями, включающими инфраструктуру для каждой микрослужбы, но изолированные от других и содержащиеся в проектах **{MicroserviceName}.FunctionalTests**;</span><span class="sxs-lookup"><span data-stu-id="bf08f-173">**Microservice functional/integration tests**, with test cases involving the infrastructure for each microservice but isolated from the others and are contained in the **{MicroserviceName}.FunctionalTests** projects.</span></span>

3. <span data-ttu-id="bf08f-174">**функциональные и интеграционные тесты приложений**, ориентированные на интеграцию микрослужб, с тестовыми случаями, которые воздействуют на несколько микрослужб</span><span class="sxs-lookup"><span data-stu-id="bf08f-174">**Application functional/integration tests**, which focus on microservices integration, with test cases that exert several microservices.</span></span> <span data-ttu-id="bf08f-175">(содержатся в проекте **Application.FunctionalTests**);</span><span class="sxs-lookup"><span data-stu-id="bf08f-175">These tests are located in project **Application.FunctionalTests**.</span></span>

<span data-ttu-id="bf08f-176">Модульные и интеграционные тесты помещены в папку тестов в проекте микрослужб. Но управление тестами приложений и нагрузочными тестами отдельно осуществляется в корневой папке, как показано на рисунке 6-25.</span><span class="sxs-lookup"><span data-stu-id="bf08f-176">While unit and integration tests are organized in a test folder within the microservice project, application and load tests are managed separately under the root folder, as shown in Figure 6-25.</span></span>

![Снимок экрана VS, на котором стрелками показаны некоторые тестовые проекты в решении.](./media/test-aspnet-core-services-web-apps/eshoponcontainers-test-folder-structure.png)

<span data-ttu-id="bf08f-178">**Рис. 6-25**.</span><span class="sxs-lookup"><span data-stu-id="bf08f-178">**Figure 6-25**.</span></span> <span data-ttu-id="bf08f-179">Структура папок тестов в eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="bf08f-179">Test folder structure in eShopOnContainers</span></span>

<span data-ttu-id="bf08f-180">Функциональные и интеграционные тесты микрослужбы и приложения выполняются из Visual Studio с помощью обычного средства запуска тестов. При этом сначала нужно запустить необходимые службы инфраструктуры с помощью набора файлов docker-compose, содержащихся в папке test решения:</span><span class="sxs-lookup"><span data-stu-id="bf08f-180">Microservice and Application functional/integration tests are run from Visual Studio, using the regular tests runner, but first you need to start the required infrastructure services, with a set of docker-compose files contained in the solution test folder:</span></span>

<span data-ttu-id="bf08f-181">**docker-compose-test.yml**</span><span class="sxs-lookup"><span data-stu-id="bf08f-181">**docker-compose-test.yml**</span></span>

```yml
version: '3.4'

services:
  redis.data:
    image: redis:alpine
  rabbitmq:
    image: rabbitmq:3-management-alpine
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
  nosqldata:
    image: mongo
```

<span data-ttu-id="bf08f-182">**docker-compose-test.override.yml**</span><span class="sxs-lookup"><span data-stu-id="bf08f-182">**docker-compose-test.override.yml**</span></span>

```yml
version: '3.4'

services:
  redis.data:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"
  sqldata:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
```

<span data-ttu-id="bf08f-183">Таким образом, для запуска функциональных и интеграционных тестов необходимо сначала выполнить следующую команду из папки test решения:</span><span class="sxs-lookup"><span data-stu-id="bf08f-183">So, to run the functional/integration tests you must first run this command, from the solution test folder:</span></span>

```console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

<span data-ttu-id="bf08f-184">Как видите, эти файлы docker-compose всего лишь запускают микрослужбы Redis, RabbitMQ, SQL Server и MongoDB.</span><span class="sxs-lookup"><span data-stu-id="bf08f-184">As you can see, these docker-compose files only start the Redis, RabbitMQ, SQL Server, and MongoDB microservices.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bf08f-185">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="bf08f-185">Additional resources</span></span>

- <span data-ttu-id="bf08f-186">**Модульное и интеграционное тестирование** в eShopOnContainers </span><span class="sxs-lookup"><span data-stu-id="bf08f-186">**Unit & Integration testing** on the eShopOnContainers </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/wiki/Unit-and-integration-testing>

- <span data-ttu-id="bf08f-187">**Нагрузочное тестирование** в eShopOnContainers </span><span class="sxs-lookup"><span data-stu-id="bf08f-187">**Load testing** on the eShopOnContainers </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/wiki/Load-testing>

> [!div class="step-by-step"]
> <span data-ttu-id="bf08f-188">[Назад](subscribe-events.md)
> [Вперед](background-tasks-with-ihostedservice.md)</span><span class="sxs-lookup"><span data-stu-id="bf08f-188">[Previous](subscribe-events.md)
[Next](background-tasks-with-ihostedservice.md)</span></span>
