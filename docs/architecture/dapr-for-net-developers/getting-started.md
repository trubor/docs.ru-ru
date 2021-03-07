---
title: Начало работы с ДАПР
description: Рекомендации по подготовке локальной среды разработки и созданию своих первых приложений .NET с помощью ДАПР.
author: amolenk
ms.date: 02/25/2021
ms.openlocfilehash: 68b1982c7283e0717ff7e1e254e5f313cd480d7b
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102401906"
---
# <a name="get-started-with-dapr"></a><span data-ttu-id="e322a-103">Начало работы с ДАПР</span><span class="sxs-lookup"><span data-stu-id="e322a-103">Get started with Dapr</span></span>

<span data-ttu-id="e322a-104">В первых двух главах вы узнали основные понятия о ДАПР.</span><span class="sxs-lookup"><span data-stu-id="e322a-104">In the first two chapters, you learned basic concepts about Dapr.</span></span> <span data-ttu-id="e322a-105">Пора использовать его для *тестового диска*.</span><span class="sxs-lookup"><span data-stu-id="e322a-105">It's time to take it for a *test drive*.</span></span> <span data-ttu-id="e322a-106">Эта глава поможет вам подготовить локальную среду разработки и создать два приложения ДАПР .NET.</span><span class="sxs-lookup"><span data-stu-id="e322a-106">This chapter will guide you through preparing your local development environment and building two Dapr .NET applications.</span></span>

## <a name="install-dapr-into-your-local-environment"></a><span data-ttu-id="e322a-107">Установка ДАПР в локальной среде</span><span class="sxs-lookup"><span data-stu-id="e322a-107">Install Dapr into your local environment</span></span>

<span data-ttu-id="e322a-108">Начните с установки ДАПР на компьютере разработчика.</span><span class="sxs-lookup"><span data-stu-id="e322a-108">You'll start by installing Dapr on your development computer.</span></span> <span data-ttu-id="e322a-109">После завершения вы сможете создавать и запускать приложения ДАПР в [собственном режиме](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-overview/).</span><span class="sxs-lookup"><span data-stu-id="e322a-109">Once complete, you can build and run Dapr applications in [self-hosted mode](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-overview/).</span></span>

1. <span data-ttu-id="e322a-110">[Установите интерфейс командной строки ДАПР](https://docs.dapr.io/getting-started/install-dapr-cli/).</span><span class="sxs-lookup"><span data-stu-id="e322a-110">[Install the Dapr CLI](https://docs.dapr.io/getting-started/install-dapr-cli/).</span></span> <span data-ttu-id="e322a-111">Он позволяет запускать, запускать и управлять экземплярами ДАПР.</span><span class="sxs-lookup"><span data-stu-id="e322a-111">It enables you to launch, run, and manage Dapr instances.</span></span> <span data-ttu-id="e322a-112">Он также обеспечивает поддержку отладки.</span><span class="sxs-lookup"><span data-stu-id="e322a-112">It also provides debugging support.</span></span>

1. <span data-ttu-id="e322a-113">Установите [DOCKER Desktop](https://docs.docker.com/get-docker/).</span><span class="sxs-lookup"><span data-stu-id="e322a-113">Install [Docker Desktop](https://docs.docker.com/get-docker/).</span></span> <span data-ttu-id="e322a-114">Если вы используете Windows, убедитесь, что на **рабочем столе DOCKER для Windows** настроено использование контейнеров Linux.</span><span class="sxs-lookup"><span data-stu-id="e322a-114">If you're running on Windows, make sure that **Docker Desktop for Windows** is configured to use Linux containers.</span></span>

> [!NOTE]
> <span data-ttu-id="e322a-115">По умолчанию ДАПР использует контейнеры DOCKER для обеспечения оптимального набора возможностей.</span><span class="sxs-lookup"><span data-stu-id="e322a-115">By default, Dapr uses Docker containers to provide you the best out-of-the-box experience.</span></span> <span data-ttu-id="e322a-116">Чтобы запустить ДАПР за пределами DOCKER, можно пропустить этот шаг и [выполнить *тонкую* инициализацию](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-no-docker/).</span><span class="sxs-lookup"><span data-stu-id="e322a-116">To run Dapr outside of Docker, you can skip this step and [execute a *slim* initialization](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-no-docker/).</span></span> <span data-ttu-id="e322a-117">В примерах, приведенных в этой главе, необходимо использовать контейнеры DOCKER.</span><span class="sxs-lookup"><span data-stu-id="e322a-117">The examples in this chapter require you use Docker containers.</span></span>

1. <span data-ttu-id="e322a-118">[Инициализация ДАПР](https://docs.dapr.io/getting-started/install-dapr/).</span><span class="sxs-lookup"><span data-stu-id="e322a-118">[Initialize Dapr](https://docs.dapr.io/getting-started/install-dapr/).</span></span> <span data-ttu-id="e322a-119">На этом шаге выполняется настройка среды разработки путем установки последних двоичных файлов и образов контейнеров ДАПР.</span><span class="sxs-lookup"><span data-stu-id="e322a-119">This step sets up your development environment by installing the latest Dapr binaries and container images.</span></span>

1. <span data-ttu-id="e322a-120">Установите [пакет SDK для .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1).</span><span class="sxs-lookup"><span data-stu-id="e322a-120">Install the [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet/3.1).</span></span>

<span data-ttu-id="e322a-121">Теперь, когда ДАПР установлен, пришло время создать свое первое приложение ДАПР!</span><span class="sxs-lookup"><span data-stu-id="e322a-121">Now that Dapr is installed, it's time to build your first Dapr application!</span></span>

## <a name="build-your-first-dapr-application"></a><span data-ttu-id="e322a-122">Создание первого приложения ДАПР</span><span class="sxs-lookup"><span data-stu-id="e322a-122">Build your first Dapr application</span></span>

<span data-ttu-id="e322a-123">Начнем с создания простого консольного приложения .NET, которое использует стандартный блок [управления состоянием ДАПР](state-management.md) .</span><span class="sxs-lookup"><span data-stu-id="e322a-123">You'll start by building a simple .NET Console application that consumes the [Dapr state management](state-management.md) building block.</span></span>

### <a name="create-the-application"></a><span data-ttu-id="e322a-124">Создание приложения</span><span class="sxs-lookup"><span data-stu-id="e322a-124">Create the application</span></span>

1. <span data-ttu-id="e322a-125">Откройте командную оболочку или терминал по своему усмотрению.</span><span class="sxs-lookup"><span data-stu-id="e322a-125">Open up the command shell or terminal of your choice.</span></span> <span data-ttu-id="e322a-126">Возможности работы с терминалами можно рассматривать в [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="e322a-126">You might consider the terminal capabilities in [Visual Studio Code](https://code.visualstudio.com/).</span></span> <span data-ttu-id="e322a-127">Перейдите в корневую папку, в которой требуется построить приложение.</span><span class="sxs-lookup"><span data-stu-id="e322a-127">Navigate to the root folder in which you want to build your application.</span></span> <span data-ttu-id="e322a-128">После этого введите следующую команду, чтобы создать новое консольное приложение .NET:</span><span class="sxs-lookup"><span data-stu-id="e322a-128">Once there, enter the following command to create a new .NET Console application:</span></span>

    ```dotnetcli
    dotnet new console -o DaprCounter
    ```

    <span data-ttu-id="e322a-129">Команда формирует шаблон для простого приложения .NET Core "Hello World".</span><span class="sxs-lookup"><span data-stu-id="e322a-129">The command scaffolds a simple "Hello World" .NET Core application.</span></span>

1. <span data-ttu-id="e322a-130">Затем перейдите к новому каталогу, созданному предыдущей командой:</span><span class="sxs-lookup"><span data-stu-id="e322a-130">Then, navigate into the new directory created by the previous command:</span></span>

    ```console
    cd DaprCounter
    ```

1. <span data-ttu-id="e322a-131">Запустите только что созданное приложение с помощью `dotnet run` команды.</span><span class="sxs-lookup"><span data-stu-id="e322a-131">Run the newly created application using the `dotnet run` command.</span></span> <span data-ttu-id="e322a-132">При этом записываются "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e322a-132">Doing so writes "Hello World!"</span></span> <span data-ttu-id="e322a-133">на экран консоли:</span><span class="sxs-lookup"><span data-stu-id="e322a-133">to the console screen:</span></span>

    ```dotnetcli
    dotnet run
    ```

### <a name="add-dapr-state-management"></a><span data-ttu-id="e322a-134">Добавление управления состоянием ДАПР</span><span class="sxs-lookup"><span data-stu-id="e322a-134">Add Dapr State Management</span></span>

<span data-ttu-id="e322a-135">Далее вы будете использовать [стандартный блок управления состоянием](https://docs.dapr.io/developing-applications/building-blocks/state-management/state-management-overview/) ДАПР для реализации счетчика с отслеживанием состояния в программе.</span><span class="sxs-lookup"><span data-stu-id="e322a-135">Next, you'll use the Dapr [state management building block](https://docs.dapr.io/developing-applications/building-blocks/state-management/state-management-overview/) to implement a stateful counter in the program.</span></span>

<span data-ttu-id="e322a-136">Вы можете вызывать API ДАПР на любой платформе разработки, используя встроенную поддержку ДАПР для HTTP и gRPC.</span><span class="sxs-lookup"><span data-stu-id="e322a-136">You can invoke Dapr APIs across any development platform using Dapr's native support for HTTP and gRPC.</span></span> <span data-ttu-id="e322a-137">Однако разработчики .NET смогут найти пакет SDK для ДАПР .NET более естественным и интуитивно понятным.</span><span class="sxs-lookup"><span data-stu-id="e322a-137">However, .NET Developers will find the Dapr .NET SDK more natural and intuitive.</span></span> <span data-ttu-id="e322a-138">Он предоставляет строго типизированный клиент .NET для вызова API-интерфейсов ДАПР.</span><span class="sxs-lookup"><span data-stu-id="e322a-138">It provides a strongly typed .NET client to call the Dapr APIs.</span></span> <span data-ttu-id="e322a-139">Пакет SDK для .NET также тесно интегрируется с ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e322a-139">The .NET SDK also tightly integrates with ASP.NET Core.</span></span>

1. <span data-ttu-id="e322a-140">В окне терминала добавьте `Dapr.Client` пакет NuGet в приложение:</span><span class="sxs-lookup"><span data-stu-id="e322a-140">From the terminal window, add the `Dapr.Client` NuGet package to your application:</span></span>

    ```dotnetcli
    dotnet add package Dapr.Client
    ```

    > [!NOTE]
    > <span data-ttu-id="e322a-141">При работе с предварительной версией ДАПР не забудьте добавить `--prerelease` флаг к команде.</span><span class="sxs-lookup"><span data-stu-id="e322a-141">If you're working with a pre-release version of Dapr, be sure to add the `--prerelease` flag to the command.</span></span>

1. <span data-ttu-id="e322a-142">Откройте `Program.cs` файл в любимом редакторе и обновите его содержимое следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="e322a-142">Open the `Program.cs` file in your favorite editor and update its contents to the following code:</span></span>

    ```csharp
    using System;
    using System.Threading.Tasks;
    using Dapr.Client;

    namespace DaprCounter
    {
        class Program
        {
            static async Task Main(string[] args)
            {
                const string storeName = "statestore";
                const string key = "counter";

                var daprClient = new DaprClientBuilder().Build();
                var counter = await daprClient.GetStateAsync<int>(storeName, key);

                while (true)
                {
                    Console.WriteLine($"Counter = {counter++}");

                    await daprClient.SaveStateAsync(storeName, key, counter);
                    await Task.Delay(1000);
                }
            }
        }
    }
    ```

    <span data-ttu-id="e322a-143">Обновленный код реализует следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="e322a-143">The updated code implements the following steps:</span></span>

    - <span data-ttu-id="e322a-144">Сначала `DaprClient` создается экземпляр нового экземпляра.</span><span class="sxs-lookup"><span data-stu-id="e322a-144">First a new `DaprClient` instance is instantiated.</span></span> <span data-ttu-id="e322a-145">Этот класс позволяет взаимодействовать с ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="e322a-145">This class enables you to interact with the Dapr sidecar.</span></span>
    - <span data-ttu-id="e322a-146">В хранилище состояний `DaprClient.GetStateAsync` получает значение для `counter` ключа.</span><span class="sxs-lookup"><span data-stu-id="e322a-146">From the state store, `DaprClient.GetStateAsync` fetches the value for the `counter` key.</span></span> <span data-ttu-id="e322a-147">Если ключ не существует, возвращается значение по умолчанию `int` (то есть `0` ).</span><span class="sxs-lookup"><span data-stu-id="e322a-147">If the key doesn't exist, the default `int` value (which is `0`) is returned.</span></span>
    - <span data-ttu-id="e322a-148">Затем код выполняет итерацию, записывает `counter` значение в консоль и сохраняет увеличенное значение в хранилище состояний.</span><span class="sxs-lookup"><span data-stu-id="e322a-148">The code then iterates, writing the `counter` value to the console and saving an incremented value to the state store.</span></span>

1. <span data-ttu-id="e322a-149">Команда CLI ДАПР `run` запускает приложение.</span><span class="sxs-lookup"><span data-stu-id="e322a-149">The Dapr CLI `run` command starts the application.</span></span> <span data-ttu-id="e322a-150">Он вызывает базовую среду выполнения ДАПР и обеспечивает совместную работу приложения и ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="e322a-150">It invokes the underlying Dapr runtime and enables both the application and Dapr sidecar to run together.</span></span> <span data-ttu-id="e322a-151">Если опустить `app-id` , ДАПР создаст уникальное имя для приложения.</span><span class="sxs-lookup"><span data-stu-id="e322a-151">If you omit the `app-id`, Dapr will generate a unique name for the application.</span></span> <span data-ttu-id="e322a-152">Последний сегмент команды, `dotnet run` , предписывает среде выполнения ДАПР запустить приложение .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e322a-152">The final segment of the command, `dotnet run`, instructs the Dapr runtime to run the .NET core application.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="e322a-153">Необходимо принять меры, чтобы всегда передавать явный `app-id` параметр при использовании стандартного блока управления состоянием.</span><span class="sxs-lookup"><span data-stu-id="e322a-153">Care must be taken to always pass an explicit `app-id` parameter when consuming the state management building block.</span></span> <span data-ttu-id="e322a-154">Блок использует значение идентификатора приложения в качестве *префикса* для ключа состояния для каждой пары "ключ-значение".</span><span class="sxs-lookup"><span data-stu-id="e322a-154">The block uses the application id value as a *prefix* for its state key for each key/value pair.</span></span> <span data-ttu-id="e322a-155">Если идентификатор приложения изменится, вы больше не сможете получить доступ к сохраненному ранее состоянию.</span><span class="sxs-lookup"><span data-stu-id="e322a-155">If the application id changes, you can no longer access the previously stored state.</span></span>

    <span data-ttu-id="e322a-156">Теперь запустите приложение с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="e322a-156">Now run the application with the following command:</span></span>

    ```console
    dapr run --app-id DaprCounter dotnet run
    ```

    <span data-ttu-id="e322a-157">Попробуйте остановить и перезапустить приложение.</span><span class="sxs-lookup"><span data-stu-id="e322a-157">Try stopping and restarting the application.</span></span> <span data-ttu-id="e322a-158">Вы увидите, что счетчик не сбрасывается.</span><span class="sxs-lookup"><span data-stu-id="e322a-158">You'll see that the counter doesn't reset.</span></span> <span data-ttu-id="e322a-159">Вместо этого он продолжится из ранее сохраненного состояния.</span><span class="sxs-lookup"><span data-stu-id="e322a-159">Instead it continues from the previously saved state.</span></span> <span data-ttu-id="e322a-160">Стандартный блок ДАПР делает приложение с отслеживанием состояния.</span><span class="sxs-lookup"><span data-stu-id="e322a-160">The Dapr building block makes the application stateful.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e322a-161">Важно понимать, что пример приложения взаимодействует с предварительно настроенным компонентом состояния, но не имеет прямой зависимости от него.</span><span class="sxs-lookup"><span data-stu-id="e322a-161">It's important to understand your sample application communicates with a pre-configured state component, but has no direct dependency on it.</span></span> <span data-ttu-id="e322a-162">ДАПР абстракций отделяет зависимость от зависимости.</span><span class="sxs-lookup"><span data-stu-id="e322a-162">Dapr abstracts away the dependency.</span></span> <span data-ttu-id="e322a-163">Как вы вскоре увидите, базовый компонент хранилища состояний можно изменить с помощью простого обновления конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e322a-163">As you'll shortly see, the underlying state store component can be changed with a simple configuration update.</span></span>

<span data-ttu-id="e322a-164">Возможно, вас интересует, где именно хранится состояние?</span><span class="sxs-lookup"><span data-stu-id="e322a-164">You might be wondering, where exactly is the state stored?</span></span>

## <a name="component-configuration-files"></a><span data-ttu-id="e322a-165">Файлы конфигурации компонентов</span><span class="sxs-lookup"><span data-stu-id="e322a-165">Component configuration files</span></span>

<span data-ttu-id="e322a-166">При первой инициализации ДАПР для локальной среды автоматически подготавливается контейнер Redis.</span><span class="sxs-lookup"><span data-stu-id="e322a-166">When you first initialized Dapr for your local environment, it automatically provisioned a Redis container.</span></span> <span data-ttu-id="e322a-167">Затем ДАПР настроил контейнер Redis как компонент хранилища состояний по умолчанию с файлом конфигурации компонента с именем `statestore.yaml` .</span><span class="sxs-lookup"><span data-stu-id="e322a-167">Dapr then configured the Redis container as the default state store component with a component configuration file, entitled `statestore.yaml`.</span></span> <span data-ttu-id="e322a-168">Вот как выглядит его содержимое:</span><span class="sxs-lookup"><span data-stu-id="e322a-168">Here's a look at its contents:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

> [!NOTE]
> <span data-ttu-id="e322a-169">Файлы конфигурации компонентов по умолчанию хранятся в `$HOME/.dapr/components` папке в Linux/macOS и в папке в `%USERPROFILE%\.dapr\components` Windows.</span><span class="sxs-lookup"><span data-stu-id="e322a-169">Default component configuration files are stored in the `$HOME/.dapr/components` folder on Linux/macOS, and in the `%USERPROFILE%\.dapr\components` folder on Windows.</span></span>

<span data-ttu-id="e322a-170">Обратите внимание на формат предыдущего файла конфигурации компонента:</span><span class="sxs-lookup"><span data-stu-id="e322a-170">Note the format of the previous component configuration file:</span></span>

- <span data-ttu-id="e322a-171">У каждого компонента есть имя.</span><span class="sxs-lookup"><span data-stu-id="e322a-171">Each component has a name.</span></span> <span data-ttu-id="e322a-172">В примере выше компонент имеет имя `statestore` .</span><span class="sxs-lookup"><span data-stu-id="e322a-172">In the sample above, the component is named `statestore`.</span></span> <span data-ttu-id="e322a-173">Мы использовали это имя в первом примере кода, чтобы сообщить ДАПР расширения, какой компонент использовать.</span><span class="sxs-lookup"><span data-stu-id="e322a-173">We used that name in our first code example to tell the Dapr sidecar which component to use.</span></span>
- <span data-ttu-id="e322a-174">Каждый файл конфигурации компонента содержит `spec` раздел.</span><span class="sxs-lookup"><span data-stu-id="e322a-174">Each component configuration file has a `spec` section.</span></span> <span data-ttu-id="e322a-175">Он содержит `type` поле, указывающее тип компонента.</span><span class="sxs-lookup"><span data-stu-id="e322a-175">It contains a `type` field that specifies the component type.</span></span> <span data-ttu-id="e322a-176">В `version` поле указывается версия компонента.</span><span class="sxs-lookup"><span data-stu-id="e322a-176">The `version` field specifies the component version.</span></span> <span data-ttu-id="e322a-177">`metadata`Поле содержит сведения, необходимые компоненту, например сведения о соединении и другие параметры.</span><span class="sxs-lookup"><span data-stu-id="e322a-177">The `metadata` field contains information that the component requires, such as connection details and other settings.</span></span> <span data-ttu-id="e322a-178">Значения метаданных будут различаться для различных типов компонентов.</span><span class="sxs-lookup"><span data-stu-id="e322a-178">The metadata values will vary for the different types of components.</span></span>

<span data-ttu-id="e322a-179">ДАПР расширения может использовать любой компонент ДАПР, настроенный в вашем приложении.</span><span class="sxs-lookup"><span data-stu-id="e322a-179">A Dapr sidecar can consume any Dapr component configured in your application.</span></span> <span data-ttu-id="e322a-180">Но что делать, если у вас есть архитектурное обоснование, ограничивающее доступность компонента?</span><span class="sxs-lookup"><span data-stu-id="e322a-180">But, what if you had an architectural justification to limit the accessibility of a component?</span></span> <span data-ttu-id="e322a-181">Как ограничить компонент Redis ДАПР сидекарс, выполняющимся только в рабочей среде?</span><span class="sxs-lookup"><span data-stu-id="e322a-181">How could you restrict the Redis component to Dapr sidecars running only in a production environment?</span></span>

<span data-ttu-id="e322a-182">Для этого можно определить `namespace` для рабочей среды.</span><span class="sxs-lookup"><span data-stu-id="e322a-182">To do so, you could define a `namespace` for the production environment.</span></span> <span data-ttu-id="e322a-183">Вы можете присвоить ему имя `production` .</span><span class="sxs-lookup"><span data-stu-id="e322a-183">You might name it `production`.</span></span> <span data-ttu-id="e322a-184">В автономном режиме укажите пространство имен ДАПР расширения, задав `NAMESPACE` переменную среды.</span><span class="sxs-lookup"><span data-stu-id="e322a-184">In self-hosted mode, you specify the namespace of a Dapr sidecar by setting the `NAMESPACE` environment variable.</span></span> <span data-ttu-id="e322a-185">При настройке ДАПР расширения будет загружать только те компоненты, которые соответствуют пространству имен.</span><span class="sxs-lookup"><span data-stu-id="e322a-185">When configured, the Dapr sidecar will only load the components that match the namespace.</span></span> <span data-ttu-id="e322a-186">Для развертываний Kubernetes пространство имен Kubernetes определяет загруженные компоненты.</span><span class="sxs-lookup"><span data-stu-id="e322a-186">For Kubernetes deployments, the Kubernetes namespace determines the components that are loaded.</span></span> <span data-ttu-id="e322a-187">В следующем примере показан компонент Redis, помещенный в `production` пространство имен.</span><span class="sxs-lookup"><span data-stu-id="e322a-187">The following sample shows the Redis component placed in a `production` namespace.</span></span> <span data-ttu-id="e322a-188">Обратите внимание на `namespace` объявление в `metadata` элементе:</span><span class="sxs-lookup"><span data-stu-id="e322a-188">Note the `namespace` declaration in the `metadata` element:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
  namespace: production
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

> [!IMPORTANT]
> <span data-ttu-id="e322a-189">Компонент пространства имен доступен только для приложений, выполняющихся в том же пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="e322a-189">A namespaced component is only accessible to applications running in the same namespace.</span></span> <span data-ttu-id="e322a-190">Если приложению ДАПР не удается загрузить компонент, убедитесь, что пространство имен приложения соответствует пространству имен компонента.</span><span class="sxs-lookup"><span data-stu-id="e322a-190">If your Dapr application fails to load a component, make sure that the application namespace matches the component namespace.</span></span> <span data-ttu-id="e322a-191">Это может быть особенно непросто в автономном режиме, в котором пространство имен приложения хранится в `NAMESPACE` переменной среды.</span><span class="sxs-lookup"><span data-stu-id="e322a-191">This can be especially tricky in self-hosted mode where the application namespace is stored in a `NAMESPACE` environment variable.</span></span>

<span data-ttu-id="e322a-192">При необходимости можно дополнительно ограничить компонент определенным приложением.</span><span class="sxs-lookup"><span data-stu-id="e322a-192">If needed, you could further restrict a component to a particular application.</span></span> <span data-ttu-id="e322a-193">В `production` пространстве имен может потребоваться ограничить доступ к кэшу Redis только `DaprCounter` приложением.</span><span class="sxs-lookup"><span data-stu-id="e322a-193">Within the `production` namespace, you may want to limit access of the Redis cache to only the `DaprCounter` application.</span></span> <span data-ttu-id="e322a-194">Это можно сделать, указав `scopes` в конфигурации компонента.</span><span class="sxs-lookup"><span data-stu-id="e322a-194">You do so by specifying `scopes` in the component configuration.</span></span> <span data-ttu-id="e322a-195">В следующем примере показано, как ограничить доступ к `statestore` компоненту Redis для приложения `DaprCounter` в `production` пространстве имен:</span><span class="sxs-lookup"><span data-stu-id="e322a-195">The following example shows how to restrict access to the Redis `statestore` component to the application `DaprCounter` in the `production` namespace:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
  namespace: production
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
  scopes:
  - DaprCounter
```

## <a name="build-a-multi-container-dapr-application"></a><span data-ttu-id="e322a-196">Создание приложения ДАПР с несколькими контейнерами</span><span class="sxs-lookup"><span data-stu-id="e322a-196">Build a multi-container Dapr application</span></span>

<span data-ttu-id="e322a-197">В первом примере вы создали простое консольное приложение .NET, которое было запущено параллельно с ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="e322a-197">In the first example, you created a simple .NET console application that ran side-by-side with a Dapr sidecar.</span></span> <span data-ttu-id="e322a-198">Однако современные распределенные приложения часто состоят из множества движущихся частей.</span><span class="sxs-lookup"><span data-stu-id="e322a-198">Modern distributed applications, however, often consist of many moving parts.</span></span> <span data-ttu-id="e322a-199">Они могут одновременно запускать независимые микрослужбы.</span><span class="sxs-lookup"><span data-stu-id="e322a-199">They can simultaneously run independent microservices.</span></span> <span data-ttu-id="e322a-200">Эти современные приложения обычно являются контейнерами и нуждаются в средствах оркестрации контейнеров, таких как Docker Compose или Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="e322a-200">These modern applications are typically containerized and require container orchestration tools such as Docker Compose or Kubernetes.</span></span>

<span data-ttu-id="e322a-201">В следующем примере вы создадите многоконтейнерное приложение.</span><span class="sxs-lookup"><span data-stu-id="e322a-201">In the next example, you'll create a multi-container application.</span></span> <span data-ttu-id="e322a-202">Вы также будете использовать стандартный блок [вызова службы ДАПР](service-invocation.md) для взаимодействия между службами.</span><span class="sxs-lookup"><span data-stu-id="e322a-202">You'll also use the [Dapr service invocation](service-invocation.md) building block to communicate between services.</span></span> <span data-ttu-id="e322a-203">Решение будет состоять из веб-приложения, которое получает прогнозы погоды из веб-API.</span><span class="sxs-lookup"><span data-stu-id="e322a-203">The solution will consist of a web application that retrieves weather forecasts from a web API.</span></span> <span data-ttu-id="e322a-204">Они будут выполняться в контейнере DOCKER.</span><span class="sxs-lookup"><span data-stu-id="e322a-204">They will each run in a Docker container.</span></span> <span data-ttu-id="e322a-205">Вы будете использовать Docker Compose для локального запуска контейнера и включения возможностей отладки.</span><span class="sxs-lookup"><span data-stu-id="e322a-205">You'll use Docker Compose to run the container locally and enable debugging capabilities.</span></span>

<span data-ttu-id="e322a-206">Убедитесь, что вы настроили локальную среду для ДАПР и установили [средства разработки .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1) (инструкции доступны в начале этой главы).</span><span class="sxs-lookup"><span data-stu-id="e322a-206">Make sure you've configured your local environment for Dapr and installed the [.NET Core 3.1 Development Tools](https://dotnet.microsoft.com/download/dotnet-core/3.1) (instructions are available at the beginning of this chapter).</span></span>

<span data-ttu-id="e322a-207">Кроме того, вам потребуется выполнить этот пример с помощью [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) с установленной рабочей нагрузкой **кросс-платформенной разработки .NET Core** .</span><span class="sxs-lookup"><span data-stu-id="e322a-207">Additionally, you'll need complete this sample using [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) with the **.NET Core cross-platform development** workload installed.</span></span>

### <a name="create-the-application"></a><span data-ttu-id="e322a-208">Создание приложения</span><span class="sxs-lookup"><span data-stu-id="e322a-208">Create the application</span></span>

1. <span data-ttu-id="e322a-209">В Visual Studio 2019 создайте проект **веб-приложения ASP.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="e322a-209">In Visual Studio 2019, create an **ASP.NET Core Web App** project:</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-createproject.png" alt-text="Снимок экрана создания нового проекта":::

1. <span data-ttu-id="e322a-211">Назовите проект `DaprFrontEnd` и свое решение `DaprMultiContainer` :</span><span class="sxs-lookup"><span data-stu-id="e322a-211">Name your project `DaprFrontEnd` and your solution `DaprMultiContainer`:</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-configureproject.png" alt-text="Снимок экрана: Настройка нового проекта":::

1. <span data-ttu-id="e322a-213">Выберите **Веб-приложение**, чтобы создать веб-приложение с Razor Pages.</span><span class="sxs-lookup"><span data-stu-id="e322a-213">Select **Web Application** to create a web application with Razor pages.</span></span> <span data-ttu-id="e322a-214">Не выбирайте **Включение поддержки Docker**.</span><span class="sxs-lookup"><span data-stu-id="e322a-214">Don't select **Enable Docker Support**.</span></span> <span data-ttu-id="e322a-215">Поддержка Docker будет добавлена позже.</span><span class="sxs-lookup"><span data-stu-id="e322a-215">You'll add Docker support later.</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-createwebapp.png" alt-text="Снимок экрана создания нового веб-приложения ASP.NET Core":::

1. <span data-ttu-id="e322a-217">Добавьте ASP.NET Core проект веб-API в то же решение и вызовите его _дапрбаккенд_.</span><span class="sxs-lookup"><span data-stu-id="e322a-217">Add a ASP.NET Core Web API project to the same solution and call it _DaprBackEnd_.</span></span> <span data-ttu-id="e322a-218">Выберите **API** в качестве типа проекта.</span><span class="sxs-lookup"><span data-stu-id="e322a-218">Select **API** as the project type.</span></span> <span data-ttu-id="e322a-219">По умолчанию ДАПР расширения полагается на границу сети, чтобы ограничить доступ к общедоступному API.</span><span class="sxs-lookup"><span data-stu-id="e322a-219">By default, a Dapr sidecar relies on the network boundary to limit access to its public API.</span></span> <span data-ttu-id="e322a-220">Поэтому снимите флажок **настроить для HTTPS**.</span><span class="sxs-lookup"><span data-stu-id="e322a-220">So, clear the checkbox for **Configure for HTTPS**.</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-createwebapi.png" alt-text="Снимок экрана создания веб-API":::

### <a name="add-dapr-service-invocation"></a><span data-ttu-id="e322a-222">Добавить вызов службы ДАПР</span><span class="sxs-lookup"><span data-stu-id="e322a-222">Add Dapr service invocation</span></span>

<span data-ttu-id="e322a-223">Теперь вы настраиваете обмен данными между службами с помощью [стандартного блока вызова службы](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/)ДАПР.</span><span class="sxs-lookup"><span data-stu-id="e322a-223">Now, you'll configure communication between the services using Dapr [service invocation building block](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/).</span></span> <span data-ttu-id="e322a-224">Вы включите веб-приложение для получения прогнозов погоды из веб-API.</span><span class="sxs-lookup"><span data-stu-id="e322a-224">You'll enable the web app to retrieve weather forecasts from the web API.</span></span> <span data-ttu-id="e322a-225">Стандартный блок вызова службы обладает многими преимуществами.</span><span class="sxs-lookup"><span data-stu-id="e322a-225">The service invocation building block features many benefits.</span></span> <span data-ttu-id="e322a-226">Она включает обнаружение служб, автоматическую повторную попытку, шифрование сообщений (с помощью mTLS) и улучшенную наблюдаемость.</span><span class="sxs-lookup"><span data-stu-id="e322a-226">It includes service discovery, automatic retries, message encryption (using mTLS), and improved observability.</span></span> <span data-ttu-id="e322a-227">Используйте пакет SDK для ДАПР для .NET, чтобы вызвать API вызова службы на ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="e322a-227">You'll use the Dapr .NET SDK to invoke the service invocation API on the Dapr sidecar.</span></span>

1. <span data-ttu-id="e322a-228">В Visual Studio откройте консоль диспетчера пакетов (**средства > диспетчер пакетов NuGet > консоль диспетчера пакетов**) и убедитесь, что `DaprFrontEnd` это проект по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e322a-228">In Visual Studio, open the Package Manager Console (**Tools > NuGet Package Manager > Package Manager Console**) and make sure that `DaprFrontEnd` is the default project.</span></span> <span data-ttu-id="e322a-229">В консоли добавьте `Dapr.AspNetCore` пакет NuGet в проект:</span><span class="sxs-lookup"><span data-stu-id="e322a-229">From the console, add the `Dapr.AspNetCore` NuGet package to the project:</span></span>

    ```powershell
    Install-Package Dapr.AspNetCore
    ```

    > [!NOTE]
    > <span data-ttu-id="e322a-230">Если целевая версия `Dapr.AspNetCore` предназначена для предварительной версии, необходимо указать `-Prerelease` флаг.</span><span class="sxs-lookup"><span data-stu-id="e322a-230">If you're targeting a version of `Dapr.AspNetCore` that is in prerelease, you need to specify the `-Prerelease` flag.</span></span>

1. <span data-ttu-id="e322a-231">В `DaprFrontEnd` проекте откройте файл *Startup.CS* и замените `ConfigureServices` метод следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="e322a-231">In the `DaprFrontEnd` project, open the *Startup.cs* file, and replace the `ConfigureServices` method with the following code:</span></span>

    ```csharp
    // This method gets called by the runtime. Use this method to add services to the container.
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddControllers().AddDapr();
        services.AddRazorPages();
    }
    ```

    <span data-ttu-id="e322a-232">Вызов функции `AddDapr` регистрирует класс в `DaprClient` ASP.NET Core системе внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="e322a-232">The call to `AddDapr` registers the `DaprClient` class with the ASP.NET Core dependency injection system.</span></span> <span data-ttu-id="e322a-233">Класс будет использоваться `DaprClient` позже для взаимодействия с ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="e322a-233">You'll use the `DaprClient` class later on to communicate with the Dapr sidecar.</span></span>

1. <span data-ttu-id="e322a-234">Добавьте в проект новый файл класса C#  с именем веасерфорекаст `DaprFrontEnd` :</span><span class="sxs-lookup"><span data-stu-id="e322a-234">Add a new C# class file named *WeatherForecast* to the `DaprFrontEnd` project:</span></span>

    ```csharp
    using System;

    namespace DaprFrontEnd
    {
        public class WeatherForecast
        {
            public DateTime Date { get; set; }

            public int TemperatureC { get; set; }

            public int TemperatureF { get; set; }

            public string Summary { get; set; }
        }
    }
    ```

1. <span data-ttu-id="e322a-235">Откройте файл *index.cshtml.CS* в папке *pages* и замените его содержимое следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="e322a-235">Open the *Index.cshtml.cs* file in the *Pages* folder, and replace its contents with the following code:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Net.Http;
    using System.Threading.Tasks;
    using Dapr.Client;
    using Microsoft.AspNetCore.Mvc.RazorPages;

    namespace DaprFrontEnd.Pages
    {
        public class IndexModel : PageModel
        {
            private readonly DaprClient _daprClient;

            public IndexModel(DaprClient daprClient)
            {
                _daprClient = daprClient ?? throw new ArgumentNullException(nameof(daprClient));
            }

            public async Task OnGet()
            {
                var forecasts = await _daprClient.InvokeMethodAsync<IEnumerable<WeatherForecast>>(
                    HttpMethod.Get,
                    "daprbackend",
                    "weatherforecast");

                ViewData["WeatherForecastData"] = forecasts;
            }
        }
    }
    ```

    <span data-ttu-id="e322a-236">Вы добавляете в веб-приложение возможности ДАПР, внедряя `DaprClient` класс в `IndexModel` конструктор.</span><span class="sxs-lookup"><span data-stu-id="e322a-236">You add Dapr capabilities into the web app by injecting the `DaprClient` class into `IndexModel` constructor.</span></span> <span data-ttu-id="e322a-237">В `OnGet` методе вы вызываете службу API с помощью стандартного блока вызова службы ДАПР.</span><span class="sxs-lookup"><span data-stu-id="e322a-237">In the `OnGet` method, you call the API service with the Dapr service invocation building block.</span></span> <span data-ttu-id="e322a-238">`OnGet`Метод вызывается каждый раз, когда пользователь посещает домашнюю страницу.</span><span class="sxs-lookup"><span data-stu-id="e322a-238">The `OnGet` method is invoked whenever a user visits the home page.</span></span> <span data-ttu-id="e322a-239">`DaprClient.InvokeMethodAsync`Метод используется для вызова `weatherforecast` метода `daprbackend` службы.</span><span class="sxs-lookup"><span data-stu-id="e322a-239">You use the `DaprClient.InvokeMethodAsync` method to invoke the `weatherforecast` method of the `daprbackend` service.</span></span> <span data-ttu-id="e322a-240">Вы настроите веб-API для использования в `daprbackend` качестве идентификатора своего приложения позже при настройке его для работы с ДАПР.</span><span class="sxs-lookup"><span data-stu-id="e322a-240">You'll configure the web API to use `daprbackend` as its application ID later on when configuring it to run with Dapr.</span></span> <span data-ttu-id="e322a-241">Наконец, ответ службы сохраняется в представлении данных.</span><span class="sxs-lookup"><span data-stu-id="e322a-241">Finally, the service response is saved in view data.</span></span>

1. <span data-ttu-id="e322a-242">Замените содержимое файла *index. cshtml* в папке *pages* на следующий код.</span><span class="sxs-lookup"><span data-stu-id="e322a-242">Replace the contents of the *Index.cshtml* file in the *Pages* folder, with the following code.</span></span> <span data-ttu-id="e322a-243">В нем отображаются прогнозы погоды, хранящиеся в данных представления для пользователя:</span><span class="sxs-lookup"><span data-stu-id="e322a-243">It displays the weather forecasts stored in the view data to the user:</span></span>

    ```razor
    @page
    @model IndexModel
    @{
        ViewData["Title"] = "Home page";
    }

    <div class="text-center">
        <h1 class="display-4">Welcome</h1>
        <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
        @foreach (var forecast in (IEnumerable<WeatherForecast>)ViewData["WeatherForecastData"])
        {
            <p>The forecast for @forecast.Date is @forecast.Summary!</p>
        }
    </div>
    ```

### <a name="add-container-support"></a><span data-ttu-id="e322a-244">Добавление поддержки контейнеров</span><span class="sxs-lookup"><span data-stu-id="e322a-244">Add container support</span></span>

<span data-ttu-id="e322a-245">В последней части этого примера вы добавите поддержку контейнеров и запустите решение с помощью Docker Compose.</span><span class="sxs-lookup"><span data-stu-id="e322a-245">In the final part of this example, you'll add container support and run the solution using Docker Compose.</span></span>

1. <span data-ttu-id="e322a-246">Щелкните проект правой кнопкой мыши `DaprFrontEnd` и выберите пункт **Добавить**  >  **поддержку контейнера Orchestrator**.</span><span class="sxs-lookup"><span data-stu-id="e322a-246">Right-click the `DaprFrontEnd` project, and choose **Add** > **Container Orchestrator Support**.</span></span> <span data-ttu-id="e322a-247">Откроется диалоговое окно **Добавление поддержки контейнера Orchestrator** :</span><span class="sxs-lookup"><span data-stu-id="e322a-247">The **Add Container Orchestrator Support** dialog appears:</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-addorchestrator.png" alt-text="Снимок экрана добавления поддержки контейнера в контейнере":::

    <span data-ttu-id="e322a-249">Выберите **Docker Compose**.</span><span class="sxs-lookup"><span data-stu-id="e322a-249">Choose **Docker Compose**.</span></span>

1. <span data-ttu-id="e322a-250">В следующем диалоговом окне выберите **Linux** в качестве целевой ОС:</span><span class="sxs-lookup"><span data-stu-id="e322a-250">In the next dialog, select **Linux** as the Target OS:</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-targetos.png" alt-text="Снимок экрана: Выбор целевой ОС DOCKER":::

    <span data-ttu-id="e322a-252">Visual Studio создает файл *DOCKER-Compose. yml* и файл *dockerignore* в папке **DOCKER-композиция** в решении:</span><span class="sxs-lookup"><span data-stu-id="e322a-252">Visual Studio creates a *docker-compose.yml* file and a *.dockerignore* file in the **docker-compose** folder in the solution:</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-dockersolution.png" alt-text="Снимок экрана проекта DOCKER-компоновки":::

    <span data-ttu-id="e322a-254">Файл *DOCKER-Compose. yml* имеет следующее содержимое:</span><span class="sxs-lookup"><span data-stu-id="e322a-254">The *docker-compose.yml* file has the following content:</span></span>

    ```yaml
    version: "3.4"

    services:
      daprfrontend:
        image: ${DOCKER_REGISTRY-}daprfrontend
        build:
          context: .
          dockerfile: DaprFrontEnd/Dockerfile
    ```

    <span data-ttu-id="e322a-255">Файл *DOCKERIGNORE* содержит типы и расширения имен файлов, которые средству Docker не нужно включать в контейнер.</span><span class="sxs-lookup"><span data-stu-id="e322a-255">The *.dockerignore* file contains file types and extensions that you don't want Docker to include in the container.</span></span> <span data-ttu-id="e322a-256">Эти файлы связаны с средой разработки и системой управления версиями, а не с приложением или службой, которые вы развертываете.</span><span class="sxs-lookup"><span data-stu-id="e322a-256">These files are associated with the development environment and source control and not the app or service you're deploying.</span></span>

    <span data-ttu-id="e322a-257">В корне каталога проекта *дапрфронтенд* был создан новый *Dockerfile* .</span><span class="sxs-lookup"><span data-stu-id="e322a-257">In the root of the *DaprFrontEnd* project directory, a new *Dockerfile* was created.</span></span> <span data-ttu-id="e322a-258">*Dockerfile* — это последовательность команд, которые используются для создания образа.</span><span class="sxs-lookup"><span data-stu-id="e322a-258">A *Dockerfile* is a sequence of commands that are used to build an image.</span></span> <span data-ttu-id="e322a-259">Дополнительные сведения см. в разделе [Справочник по Dockerfile](https://docs.docker.com/engine/reference/builder).</span><span class="sxs-lookup"><span data-stu-id="e322a-259">For more information, see [Dockerfile reference](https://docs.docker.com/engine/reference/builder).</span></span>

    <span data-ttu-id="e322a-260">*Dockerfile* содержит YAML:</span><span class="sxs-lookup"><span data-stu-id="e322a-260">The *Dockerfile* contains the YAML:</span></span>

    ```yml
    FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
    WORKDIR /app
    EXPOSE 80
    EXPOSE 443

    FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
    WORKDIR /src
    COPY ["DaprFrontEnd/DaprFrontEnd.csproj", "DaprFrontEnd/"]
    RUN dotnet restore "DaprFrontEnd/DaprFrontEnd.csproj"
    COPY . .
    WORKDIR "/src/DaprFrontEnd"
    RUN dotnet build "DaprFrontEnd.csproj" -c Release -o /app/build

    FROM build AS publish
    RUN dotnet publish "DaprFrontEnd.csproj" -c Release -o /app/publish

    FROM base AS final
    WORKDIR /app
    COPY --from=publish /app/publish .
    ENTRYPOINT ["dotnet", "DaprFrontEnd.dll"]
    ```

    <span data-ttu-id="e322a-261">Предыдущие *Dockerfile* последовательно выполняют следующие шаги при вызове:</span><span class="sxs-lookup"><span data-stu-id="e322a-261">The preceding *Dockerfile* sequentially performs the following steps when invoked:</span></span>

    1. <span data-ttu-id="e322a-262">Извлекает `mcr.microsoft.com/dotnet/aspnet:3.1` изображение и называет его `base` .</span><span class="sxs-lookup"><span data-stu-id="e322a-262">Pulls the `mcr.microsoft.com/dotnet/aspnet:3.1` image and names it `base`.</span></span>
    1. <span data-ttu-id="e322a-263">Задает для рабочего каталога значение */АПП*.</span><span class="sxs-lookup"><span data-stu-id="e322a-263">Sets the working directory to */app*.</span></span>
    1. <span data-ttu-id="e322a-264">Предоставляет порт `80` и `443` .</span><span class="sxs-lookup"><span data-stu-id="e322a-264">Exposes port `80` and `443`.</span></span>
    1. <span data-ttu-id="e322a-265">Извлекает `mcr.microsoft.com/dotnet/sdk:3.1` изображение и называет его `build` .</span><span class="sxs-lookup"><span data-stu-id="e322a-265">Pulls the `mcr.microsoft.com/dotnet/sdk:3.1` image and names it `build`.</span></span>
    1. <span data-ttu-id="e322a-266">Задает для рабочего каталога значение */src*.</span><span class="sxs-lookup"><span data-stu-id="e322a-266">Sets the working directory to */src*.</span></span>
    1. <span data-ttu-id="e322a-267">Копирует _дапрфронтенд/дапрфронтенд. csproj_ в новый каталог с именем *дапрфронтенд/*.</span><span class="sxs-lookup"><span data-stu-id="e322a-267">Copies the _DaprFrontEnd/DaprFrontEnd.csproj_ to a new directory named *DaprFrontEnd/*.</span></span>
    1. <span data-ttu-id="e322a-268">Вызывает [`dotnet restore`](../../core/tools/dotnet-restore.md) в проекте.</span><span class="sxs-lookup"><span data-stu-id="e322a-268">Calls [`dotnet restore`](../../core/tools/dotnet-restore.md) on the project.</span></span>
    1. <span data-ttu-id="e322a-269">Копирует все из корневого каталога в корень образа.</span><span class="sxs-lookup"><span data-stu-id="e322a-269">Copies everything from the root directory into the image's root.</span></span>
    1. <span data-ttu-id="e322a-270">Задает для рабочего каталога значение _/СРК/дапрфронтенд_.</span><span class="sxs-lookup"><span data-stu-id="e322a-270">Sets the working directory to _/src/DaprFrontEnd_.</span></span>
    1. <span data-ttu-id="e322a-271">Вызывает [`dotnet build`](../../core/tools/dotnet-build.md) в проекте.</span><span class="sxs-lookup"><span data-stu-id="e322a-271">Calls [`dotnet build`](../../core/tools/dotnet-build.md) on the project.</span></span>
        - <span data-ttu-id="e322a-272">Нацеливание на конфигурацию **выпуска** и выходные данные */АПП/буилд*.</span><span class="sxs-lookup"><span data-stu-id="e322a-272">Targeting the **Release** configuration and outputs to */app/build*.</span></span>
    1. <span data-ttu-id="e322a-273">Инициализирует новый этап сборки из существующего `build` базового образа и называет его `publish` .</span><span class="sxs-lookup"><span data-stu-id="e322a-273">Initializes a new build stage from the existing `build` base image and names it `publish`.</span></span>
    1. <span data-ttu-id="e322a-274">Вызывает `dotnet publish` в проекте.</span><span class="sxs-lookup"><span data-stu-id="e322a-274">Calls `dotnet publish` on the project.</span></span>
        - <span data-ttu-id="e322a-275">Нацеливание на конфигурацию **выпуска** и выходные данные */АПП/публиш*.</span><span class="sxs-lookup"><span data-stu-id="e322a-275">Targeting the **Release** configuration and outputs to */app/publish*.</span></span>
    1. <span data-ttu-id="e322a-276">Инициализирует новый этап сборки из существующего `publish` базового образа и называет его `final` .</span><span class="sxs-lookup"><span data-stu-id="e322a-276">Initializes a new build stage from the existing `publish` base image and names it `final`.</span></span>
    1. <span data-ttu-id="e322a-277">Задает для рабочего каталога значение */АПП*.</span><span class="sxs-lookup"><span data-stu-id="e322a-277">Sets the working directory to */app*.</span></span>
    1. <span data-ttu-id="e322a-278">Копирует `/app/publish` каталог из `publish` образа в корневую папку `final` образа.</span><span class="sxs-lookup"><span data-stu-id="e322a-278">Copies the `/app/publish` directory from the `publish` image into the root of the `final` image.</span></span>
    1. <span data-ttu-id="e322a-279">Задает точку входа как изображение `dotnet` и передает ее в `DaprFrontEnd.dll` качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="e322a-279">Sets the entry point as the image to `dotnet` and passes the `DaprFrontEnd.dll` as an arg.</span></span>

1. <span data-ttu-id="e322a-280">В `DaprBackEnd` проекте веб-API щелкните правой кнопкой мыши узел проекта и выберите пункт **Добавить**  >  **поддержку контейнера Orchestrator**.</span><span class="sxs-lookup"><span data-stu-id="e322a-280">In the `DaprBackEnd` web API project, right-click on the project node, and choose **Add** > **Container Orchestrator Support**.</span></span> <span data-ttu-id="e322a-281">Выберите **DOCKER Compose**, а затем еще раз выберите **Linux** в качестве целевой операционной системы.</span><span class="sxs-lookup"><span data-stu-id="e322a-281">Choose **Docker Compose**, and then select **Linux** again as the target OS.</span></span>

    <span data-ttu-id="e322a-282">В корне каталога проекта _дапрбаккенд_ был создан новый *Dockerfile* .</span><span class="sxs-lookup"><span data-stu-id="e322a-282">In the root of the _DaprBackEnd_ project directory, a new *Dockerfile* was created.</span></span> <span data-ttu-id="e322a-283">*Dockerfile* содержит следующие YAML:</span><span class="sxs-lookup"><span data-stu-id="e322a-283">The *Dockerfile* contains the following YAML:</span></span>

    ```yml
    FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
    WORKDIR /app
    EXPOSE 80

    FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
    WORKDIR /src
    COPY ["DaprBackEnd/DaprBackEnd.csproj", "DaprBackEnd/"]
    RUN dotnet restore "DaprBackEnd/DaprBackEnd.csproj"
    COPY . .
    WORKDIR "/src/DaprBackEnd"
    RUN dotnet build "DaprBackEnd.csproj" -c Release -o /app/build

    FROM build AS publish
    RUN dotnet publish "DaprBackEnd.csproj" -c Release -o /app/publish

    FROM base AS final
    WORKDIR /app
    COPY --from=publish /app/publish .
    ENTRYPOINT ["dotnet", "DaprBackEnd.dll"]
    ```

    <span data-ttu-id="e322a-284">Снова откройте файл *DOCKER-Compose. yml* и изучите его содержимое.</span><span class="sxs-lookup"><span data-stu-id="e322a-284">Open the *docker-compose.yml* file again and examine its contents.</span></span> <span data-ttu-id="e322a-285">Visual Studio обновил файл **DOCKER Compose** .</span><span class="sxs-lookup"><span data-stu-id="e322a-285">Visual Studio has updated the **Docker Compose** file.</span></span> <span data-ttu-id="e322a-286">Теперь обе службы включены:</span><span class="sxs-lookup"><span data-stu-id="e322a-286">Now both services are included:</span></span>

    ```yaml
    version: '3.4'

    services:
      daprfrontend:
        image: ${DOCKER_REGISTRY-}daprfrontend
        build:
          context: .
          dockerfile: DaprFrontEnd/Dockerfile

      daprbackend:
        image: ${DOCKER_REGISTRY-}daprbackend
        build:
          context: .
          dockerfile: DaprBackEnd/Dockerfile
    ```

1. <span data-ttu-id="e322a-287">Чтобы использовать стандартные блоки ДАПР внутри контейнерного приложения, необходимо добавить контейнеры сидекарс ДАПР в файл создания.</span><span class="sxs-lookup"><span data-stu-id="e322a-287">To use Dapr building blocks from inside a containerized application, you'll need to add the Dapr sidecars containers to your Compose file.</span></span> <span data-ttu-id="e322a-288">Внимательно обновите содержимое файла *DOCKER-Compose. yml* , чтобы оно соответствовало следующему примеру.</span><span class="sxs-lookup"><span data-stu-id="e322a-288">Carefully update the content of the *docker-compose.yml* file to match the following example.</span></span> <span data-ttu-id="e322a-289">Обратите особое внимание на форматирование и отступы и не используйте вкладки.</span><span class="sxs-lookup"><span data-stu-id="e322a-289">Pay close attention to the formatting and spacing and don't use tabs.</span></span>

    ```yaml
    version: '3.4'
    
    services:
      daprfrontend:
        image: ${DOCKER_REGISTRY-}daprfrontend
        build:
          context: .
          dockerfile: DaprFrontEnd/Dockerfile
        ports:
          - "51000:50001"

      daprfrontend-dapr:
        image: "daprio/daprd:latest"
        command: [ "./daprd", "-app-id", "daprfrontend", "-app-port", "80" ]
        depends_on:
          - daprfrontend
        network_mode: "service:daprfrontend"

      daprbackend:
        image: ${DOCKER_REGISTRY-}daprbackend
        build:
          context: .
          dockerfile: DaprBackEnd/Dockerfile
        ports:
          - "52000:50001"

      daprbackend-dapr:
        image: "daprio/daprd:latest"
        command: [ "./daprd", "-app-id", "daprbackend", "-app-port", "80" ]
        depends_on:
          - daprfrontend
        network_mode: "service:daprbackend"
    ```

    <span data-ttu-id="e322a-290">В обновленном файле мы добавили `daprfrontend-dapr` и `daprbackend-dapr` сидекарс для `daprfrontend` `daprbackend` служб и соответственно.</span><span class="sxs-lookup"><span data-stu-id="e322a-290">In the updated file, we've added `daprfrontend-dapr` and `daprbackend-dapr` sidecars for the `daprfrontend` and `daprbackend` services respectively.</span></span> <span data-ttu-id="e322a-291">В обновленном файле Обратите особое внимание на следующие изменения:</span><span class="sxs-lookup"><span data-stu-id="e322a-291">In the updated file, pay close attention to the following changes:</span></span>

    - <span data-ttu-id="e322a-292">Сидекарс использует `daprio/daprd:latest` образ контейнера.</span><span class="sxs-lookup"><span data-stu-id="e322a-292">The sidecars use the `daprio/daprd:latest` container image.</span></span> <span data-ttu-id="e322a-293">Использование `latest` тега не рекомендуется для рабочих сценариев.</span><span class="sxs-lookup"><span data-stu-id="e322a-293">The use of the `latest` tag isn't recommended for production scenarios.</span></span> <span data-ttu-id="e322a-294">В рабочей среде лучше использовать конкретный номер версии.</span><span class="sxs-lookup"><span data-stu-id="e322a-294">For production, it's better to use a specific version number.</span></span>
    - <span data-ttu-id="e322a-295">Каждая служба, определенная в файле создания, имеет собственное сетевое пространство имен для изоляции сети.</span><span class="sxs-lookup"><span data-stu-id="e322a-295">Each service defined in the Compose file has its own network namespace for network isolation purposes.</span></span> <span data-ttu-id="e322a-296">Сидекарс использует, `network_mode: "service:..."` чтобы убедиться в том, что они работают в том же пространстве имен, что и приложение.</span><span class="sxs-lookup"><span data-stu-id="e322a-296">The sidecars use `network_mode: "service:..."` to ensure they run in the same network namespace as the application.</span></span> <span data-ttu-id="e322a-297">Это позволяет расширения и приложению обмениваться данными с помощью `localhost` .</span><span class="sxs-lookup"><span data-stu-id="e322a-297">Doing so allows the sidecar and the application to communicate using `localhost`.</span></span>
    - <span data-ttu-id="e322a-298">Порты, на которых сидекарс ДАПР прослушивают обмен данными gRPC (по умолчанию 50001), должны быть предоставлены, чтобы сидекарс мог взаимодействовать друг с другом.</span><span class="sxs-lookup"><span data-stu-id="e322a-298">The ports on which the Dapr sidecars are listening for gRPC communication (by default 50001) must be exposed to allow the sidecars to communicate with each other.</span></span>

1. <span data-ttu-id="e322a-299">Запустите решение (<kbd>F5</kbd> или <kbd>нажмите клавиши CTRL + F5</kbd>), чтобы убедиться, что оно работает правильно.</span><span class="sxs-lookup"><span data-stu-id="e322a-299">Run the solution (<kbd>F5</kbd> or <kbd>Ctrl+F5</kbd>) to verify that it works as expected.</span></span> <span data-ttu-id="e322a-300">Если все настроено правильно, вы увидите данные прогноза погоды:</span><span class="sxs-lookup"><span data-stu-id="e322a-300">If everything is configured correctly, you should see the weather forecast data:</span></span>

    :::image type="content" source="./media/getting-started/multicontainer-result.png" alt-text="Снимок экрана: окончательное решение, показывающее данные прогноза погоды":::

    <span data-ttu-id="e322a-302">На локальном компьютере с Docker Compose и Visual Studio 2019 можно установить точки останова и выполнить отладку в приложении.</span><span class="sxs-lookup"><span data-stu-id="e322a-302">Running locally with Docker Compose and Visual Studio 2019, you can set breakpoints and debug into the application.</span></span> <span data-ttu-id="e322a-303">В рабочих сценариях рекомендуется размещать приложение в Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="e322a-303">For production scenarios, it's recommended to host your application in Kubernetes.</span></span> <span data-ttu-id="e322a-304">Эта книга включает сопутствующее Справочное приложение [ешопондапр](https://github.com/dotnet-architecture/eShopOnDapr), которое содержит сценарии для развертывания в Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="e322a-304">This book includes an accompanying reference application, [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr), that contains scripts to deploy to Kubernetes.</span></span>

    <span data-ttu-id="e322a-305">Дополнительные сведения о стандартном блоке вызова службы ДАПР, используемом в этом пошаговом руководстве, см. в [главе 6](service-invocation.md).</span><span class="sxs-lookup"><span data-stu-id="e322a-305">To learn more about the Dapr service invocation building block used in this walkthrough, refer to [chapter 6](service-invocation.md).</span></span>

## <a name="summary"></a><span data-ttu-id="e322a-306">Итоги</span><span class="sxs-lookup"><span data-stu-id="e322a-306">Summary</span></span>

<span data-ttu-id="e322a-307">В этой главе вы имели возможность *протестировать ДАПР диска* .</span><span class="sxs-lookup"><span data-stu-id="e322a-307">In this chapter, you had an opportunity to *test drive* Dapr.</span></span> <span data-ttu-id="e322a-308">С помощью пакета SDK для ДАПР .NET вы узнали, как ДАПР интегрируется с платформой приложений .NET.</span><span class="sxs-lookup"><span data-stu-id="e322a-308">Using the Dapr .NET SDK, you saw how Dapr integrates with the .NET application platform.</span></span>

<span data-ttu-id="e322a-309">Первый пример — это простое консольное приложение .NET с отслеживанием состояния, которое использовало Стандартный блок управления состоянием ДАПР.</span><span class="sxs-lookup"><span data-stu-id="e322a-309">The first example was a simple, stateful, .NET Console application that used the Dapr state management building block.</span></span>

<span data-ttu-id="e322a-310">Второй пример включал в себя приложение с несколькими контейнерами, работающее в DOCKER.</span><span class="sxs-lookup"><span data-stu-id="e322a-310">The second example involved a multi-container application running in Docker.</span></span> <span data-ttu-id="e322a-311">Используя Visual Studio с Docker Compose, вы столкнулись с знакомым средством *отладки F5* , доступным во всех приложениях .NET.</span><span class="sxs-lookup"><span data-stu-id="e322a-311">By using Visual Studio with Docker Compose, you experienced the familiar *F5 debugging experience* available across all .NET apps.</span></span>

<span data-ttu-id="e322a-312">Кроме того, вы более подробно рассматриваете файлы конфигурации компонентов ДАПР.</span><span class="sxs-lookup"><span data-stu-id="e322a-312">You also got a closer look at Dapr component configuration files.</span></span> <span data-ttu-id="e322a-313">Они настраивают фактическую реализацию инфраструктуры, используемую стандартными блоками ДАПР.</span><span class="sxs-lookup"><span data-stu-id="e322a-313">They configure the actual infrastructure implementation used by the Dapr building blocks.</span></span> <span data-ttu-id="e322a-314">Пространства имен и области можно использовать для ограничения доступа компонента к определенным средам и приложениям.</span><span class="sxs-lookup"><span data-stu-id="e322a-314">You can use namespaces and scopes to restrict component access to particular environments and applications.</span></span>

<span data-ttu-id="e322a-315">В следующих главах вы узнаете о стандартных блоках, предлагаемых ДАПР.</span><span class="sxs-lookup"><span data-stu-id="e322a-315">In the upcoming chapters, you'll dive deep into the building blocks offered by Dapr.</span></span>

### <a name="references"></a><span data-ttu-id="e322a-316">Ссылки</span><span class="sxs-lookup"><span data-stu-id="e322a-316">References</span></span>

- [<span data-ttu-id="e322a-317">Документация по ДАПР. Приступая к работе</span><span class="sxs-lookup"><span data-stu-id="e322a-317">Dapr documentation - Getting started</span></span>](https://docs.dapr.io/getting-started)
- [<span data-ttu-id="e322a-318">ешопондапр</span><span class="sxs-lookup"><span data-stu-id="e322a-318">eShopOnDapr</span></span>](https://github.com/dotnet-architecture/eShopOnDapr)

> [!div class="step-by-step"]
> <span data-ttu-id="e322a-319">[Назад](dapr-at-20000-feet.md)
> [Вперед](reference-application.md)</span><span class="sxs-lookup"><span data-stu-id="e322a-319">[Previous](dapr-at-20000-feet.md)
[Next](reference-application.md)</span></span>
