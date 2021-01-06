---
title: Самостоятельные приложения gRPC — gRPC для разработчиков WCF
description: Развертывание ASP.NET Core gRPC приложений как самостоятельных служб.
ms.date: 12/15/2020
ms.openlocfilehash: a5e2316b8d76593f4eb53760d2609b5bbbc9d2c5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938537"
---
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="0bca9-103">Приложения gRPC с самостоятельным размещением</span><span class="sxs-lookup"><span data-stu-id="0bca9-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="0bca9-104">Несмотря на то, что приложения ASP.NET Core 5,0 могут размещаться в IIS в Windows Server, в настоящее время невозможно разместить приложение gRPC в IIS, так как некоторые функции HTTP/2 не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="0bca9-104">Although ASP.NET Core 5.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't supported.</span></span> <span data-ttu-id="0bca9-105">Эта функция является целью для будущего обновления Windows Server.</span><span class="sxs-lookup"><span data-stu-id="0bca9-105">This functionality is a goal for a future update to Windows Server.</span></span>

<span data-ttu-id="0bca9-106">Приложение можно запустить как службу Windows.</span><span class="sxs-lookup"><span data-stu-id="0bca9-106">You can run your application as a Windows service.</span></span> <span data-ttu-id="0bca9-107">Вы также можете запустить его как службу Linux, управляемую [системой](https://en.wikipedia.org/wiki/Systemd), из-за новых возможностей в расширениях размещения .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="0bca9-107">Or you can run it as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), because of new features in the .NET 5.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="0bca9-108">Запуск приложения как службы Windows</span><span class="sxs-lookup"><span data-stu-id="0bca9-108">Run your app as a Windows service</span></span>

<span data-ttu-id="0bca9-109">Чтобы настроить приложение ASP.NET Core для работы в качестве службы Windows, установите пакет [Microsoft. Extensions. Hosting. службы Windows](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) из NuGet.</span><span class="sxs-lookup"><span data-stu-id="0bca9-109">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="0bca9-110">Затем добавьте вызов в `UseWindowsService` `CreateHostBuilder` метод в `Program.cs` .</span><span class="sxs-lookup"><span data-stu-id="0bca9-110">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseWindowsService() // Enable running as a Windows service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> <span data-ttu-id="0bca9-111">Если приложение не работает как служба Windows, метод не выполняет `UseWindowsService` никаких действий.</span><span class="sxs-lookup"><span data-stu-id="0bca9-111">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="0bca9-112">Теперь опубликуйте приложение с помощью одного из следующих методов:</span><span class="sxs-lookup"><span data-stu-id="0bca9-112">Now publish your application by using one of these methods:</span></span>

* <span data-ttu-id="0bca9-113">В Visual Studio, щелкнув проект правой кнопкой мыши и выбрав пункт **опубликовать** в контекстном меню.</span><span class="sxs-lookup"><span data-stu-id="0bca9-113">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="0bca9-114">Из .NET CLI.</span><span class="sxs-lookup"><span data-stu-id="0bca9-114">From the .NET CLI.</span></span>

<span data-ttu-id="0bca9-115">При публикации приложения .NET можно создать *зависимое от платформы* развертывание или *автономное* развертывание.</span><span class="sxs-lookup"><span data-stu-id="0bca9-115">When you publish a .NET application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="0bca9-116">Для развертываний, зависящих от платформы, требуется, чтобы общая среда выполнения .NET была установлена на узле, где они выполняются.</span><span class="sxs-lookup"><span data-stu-id="0bca9-116">Framework-dependent deployments require the .NET Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="0bca9-117">Автономные развертывания публикуются с полной копией среды выполнения и платформы .NET и могут выполняться на любом узле.</span><span class="sxs-lookup"><span data-stu-id="0bca9-117">Self-contained deployments are published with a complete copy of the .NET runtime and framework and can be run on any host.</span></span> <span data-ttu-id="0bca9-118">Дополнительные сведения, включая преимущества и недостатки каждого подхода, см. в документации по [развертыванию приложений .NET](../../core/deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="0bca9-118">For more information, including the advantages and disadvantages of each approach, see the [.NET application deployment](../../core/deploying/index.md) documentation.</span></span>

<span data-ttu-id="0bca9-119">Чтобы опубликовать автономную сборку приложения, которое не требует установки среды выполнения .NET 5,0 на узле, укажите среду выполнения, которая должна быть включена в приложение.</span><span class="sxs-lookup"><span data-stu-id="0bca9-119">To publish a self-contained build of the application that does not require the .NET 5.0 runtime to be installed on the host, specify the runtime to be included with the application.</span></span> <span data-ttu-id="0bca9-120">Используйте `-r` флаг (или `--runtime` ).</span><span class="sxs-lookup"><span data-stu-id="0bca9-120">Use the `-r` (or `--runtime`) flag.</span></span>

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="0bca9-121">Чтобы опубликовать сборку, зависящую от платформы, опустите `-r` флаг.</span><span class="sxs-lookup"><span data-stu-id="0bca9-121">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```dotnetcli
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="0bca9-122">Скопируйте полное содержимое `publish` каталога в папку установки.</span><span class="sxs-lookup"><span data-stu-id="0bca9-122">Copy the complete contents of the `publish` directory to an installation folder.</span></span> <span data-ttu-id="0bca9-123">Затем с помощью [средства SC](/windows/desktop/services/controlling-a-service-using-sc) Создайте службу Windows для исполняемого файла.</span><span class="sxs-lookup"><span data-stu-id="0bca9-123">Then, use the [sc tool](/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable file.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a><span data-ttu-id="0bca9-124">Регистрация в журнале событий Windows</span><span class="sxs-lookup"><span data-stu-id="0bca9-124">Log to the Windows event log</span></span>

<span data-ttu-id="0bca9-125">`UseWindowsService`Метод автоматически добавляет поставщик [ведения журнала](/aspnet/core/fundamentals/logging/) , записывающий сообщения журнала в журнал событий Windows.</span><span class="sxs-lookup"><span data-stu-id="0bca9-125">The `UseWindowsService` method automatically adds a [logging](/aspnet/core/fundamentals/logging/) provider that writes log messages to the Windows event log.</span></span> <span data-ttu-id="0bca9-126">Вы можете настроить ведение журнала для этого поставщика, добавив `EventLog` запись в `Logging` раздел `appsettings.json` или другой источник конфигурации.</span><span class="sxs-lookup"><span data-stu-id="0bca9-126">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or another configuration source.</span></span>

<span data-ttu-id="0bca9-127">Имя источника, используемое в журнале событий, можно переопределить, задав `SourceName` свойство в этих параметрах.</span><span class="sxs-lookup"><span data-stu-id="0bca9-127">You can override the source name used in the event log by setting a `SourceName` property in these settings.</span></span> <span data-ttu-id="0bca9-128">Если не указать имя, будет использоваться имя приложения по умолчанию (обычно имя исполняемой сборки).</span><span class="sxs-lookup"><span data-stu-id="0bca9-128">If you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="0bca9-129">Дополнительные сведения о ведении журнала приведены в конце этой главы.</span><span class="sxs-lookup"><span data-stu-id="0bca9-129">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="0bca9-130">Запуск приложения как службы Linux с помощью системы</span><span class="sxs-lookup"><span data-stu-id="0bca9-130">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="0bca9-131">Чтобы настроить приложение ASP.NET Core для запуска в качестве службы Linux (или *управляющей* программы в Linux терминах), установите пакет [Microsoft.Extensions.Hosting.Sysтемд](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) из NuGet.</span><span class="sxs-lookup"><span data-stu-id="0bca9-131">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="0bca9-132">Затем добавьте вызов в `UseSystemd` `CreateHostBuilder` метод в `Program.cs` .</span><span class="sxs-lookup"><span data-stu-id="0bca9-132">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseSystemd() // Enable running as a Systemd service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> <span data-ttu-id="0bca9-133">Если приложение не работает как служба Linux, метод не выполняет `UseSystemd` никаких действий.</span><span class="sxs-lookup"><span data-stu-id="0bca9-133">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="0bca9-134">Теперь опубликуйте приложение.</span><span class="sxs-lookup"><span data-stu-id="0bca9-134">Now publish your application.</span></span> <span data-ttu-id="0bca9-135">Приложение может быть либо зависимым от платформы, либо самодостаточным для соответствующей среды выполнения Linux (например, `linux-x64` ).</span><span class="sxs-lookup"><span data-stu-id="0bca9-135">The application can be either framework dependent or self-contained for the relevant Linux runtime (for example, `linux-x64`).</span></span> <span data-ttu-id="0bca9-136">Опубликовать можно с помощью одного из следующих методов:</span><span class="sxs-lookup"><span data-stu-id="0bca9-136">You can publish by using one of these methods:</span></span>

* <span data-ttu-id="0bca9-137">В Visual Studio, щелкнув проект правой кнопкой мыши и выбрав пункт **опубликовать** в контекстном меню.</span><span class="sxs-lookup"><span data-stu-id="0bca9-137">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="0bca9-138">В интерфейсе командной строки .NET с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="0bca9-138">From the .NET CLI, by using the following command:</span></span>

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
<span data-ttu-id="0bca9-139">Скопируйте полное содержимое `publish` каталога в папку установки на узле Linux.</span><span class="sxs-lookup"><span data-stu-id="0bca9-139">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="0bca9-140">Для регистрации службы требуется специальный файл, называемый *файлом единицы*, который будет добавлен в `/etc/systemd/system` каталог.</span><span class="sxs-lookup"><span data-stu-id="0bca9-140">Registering the service requires a special file, called a *unit file*, to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="0bca9-141">Для создания файла в этой папке необходимо разрешение root.</span><span class="sxs-lookup"><span data-stu-id="0bca9-141">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="0bca9-142">Присвойте файлу имя с идентификатором, который вы хотите `systemd` использовать, и `.service` расширением.</span><span class="sxs-lookup"><span data-stu-id="0bca9-142">Name the file with the identifier that you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="0bca9-143">Например, воспользуйтесь `/etc/systemd/system/myapp.service`.</span><span class="sxs-lookup"><span data-stu-id="0bca9-143">For example, use `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="0bca9-144">Файл службы использует формат INI, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="0bca9-144">The service file uses INI format, as shown in this example:</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="0bca9-145">`Type=notify`Свойство говорит о том `systemd` , что приложение будет уведомлять его при запуске и завершении работы.</span><span class="sxs-lookup"><span data-stu-id="0bca9-145">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="0bca9-146">Этот `WantedBy=multi-user.target` параметр приведет к запуску службы при достижении системой Linux значения "runlevel 2", что означает, что неграфическая оболочка с несколькими пользователями активна.</span><span class="sxs-lookup"><span data-stu-id="0bca9-146">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2," which means a non-graphical, multi-user shell is active.</span></span>

<span data-ttu-id="0bca9-147">Прежде чем `systemd` будет распознать службу, необходимо перезагрузить ее конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="0bca9-147">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="0bca9-148">Вы управляете с `systemd` помощью `systemctl` команды.</span><span class="sxs-lookup"><span data-stu-id="0bca9-148">You control `systemd` by using the `systemctl` command.</span></span> <span data-ttu-id="0bca9-149">После перезагрузки используйте `status` подкоманду, чтобы убедиться, что приложение успешно зарегистрировано.</span><span class="sxs-lookup"><span data-stu-id="0bca9-149">After reloading, use the `status` subcommand to confirm that the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="0bca9-150">Если служба настроена правильно, вы получите следующие выходные данные:</span><span class="sxs-lookup"><span data-stu-id="0bca9-150">If you've configured the service correctly, you'll get the following output:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="0bca9-151">Используйте `start` команду для запуска службы.</span><span class="sxs-lookup"><span data-stu-id="0bca9-151">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="0bca9-152">`.service`Расширение не является обязательным, если вы используете `systemctl start` .</span><span class="sxs-lookup"><span data-stu-id="0bca9-152">The `.service` extension is optional when you're using `systemctl start`.</span></span>

<span data-ttu-id="0bca9-153">Чтобы настроить `systemd` Автоматический запуск службы при запуске системы, используйте `enable` команду.</span><span class="sxs-lookup"><span data-stu-id="0bca9-153">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="0bca9-154">Регистрация в журнале</span><span class="sxs-lookup"><span data-stu-id="0bca9-154">Log to journald</span></span>

<span data-ttu-id="0bca9-155">В Linux, эквивалентном журналу событий Windows `journald` , входит служба структурированной системной службы ведения журналов `systemd` .</span><span class="sxs-lookup"><span data-stu-id="0bca9-155">The Linux equivalent of the Windows event log is `journald`, a structured logging system service that's part of `systemd`.</span></span> <span data-ttu-id="0bca9-156">Сообщения журнала, записанные в стандартный вывод управляющей программой Linux, автоматически записываются в `journald` .</span><span class="sxs-lookup"><span data-stu-id="0bca9-156">Log messages written to the standard output by a Linux daemon are automatically written to `journald`.</span></span> <span data-ttu-id="0bca9-157">Чтобы настроить уровни ведения журнала, используйте `Console` раздел конфигурации ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="0bca9-157">To configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="0bca9-158">`UseSystemd`Метод построителя узла автоматически настраивает формат вывода консоли в соответствии с журналом.</span><span class="sxs-lookup"><span data-stu-id="0bca9-158">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="0bca9-159">Поскольку `journald` является стандартом для журналов Linux, с ним интегрируется множество средств.</span><span class="sxs-lookup"><span data-stu-id="0bca9-159">Because `journald` is the standard for Linux logs, a variety of tools integrate with it.</span></span> <span data-ttu-id="0bca9-160">Можно легко маршрутизировать журналы из `journald` внешней системы ведения журналов.</span><span class="sxs-lookup"><span data-stu-id="0bca9-160">You can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="0bca9-161">Работая локально на узле, можно использовать `journalctl` команду для просмотра журналов из командной строки.</span><span class="sxs-lookup"><span data-stu-id="0bca9-161">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="0bca9-162">Если на вашем узле доступна среда графического пользовательского интерфейса, для Linux доступны несколько графических средств просмотра журналов, таких как *кжаурналктл* и *GNOME-Logs*.</span><span class="sxs-lookup"><span data-stu-id="0bca9-162">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="0bca9-163">Дополнительные сведения о запросах к `systemd` журналу из командной строки с помощью `journalctl` см. [в разделе манпажес](https://manpages.debian.org/buster/systemd/journalctl.1).</span><span class="sxs-lookup"><span data-stu-id="0bca9-163">To learn more about querying the `systemd` journal from the command line by using `journalctl`, see [the manpages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="0bca9-164">HTTPS-сертификаты для приложений, размещаемых в собственном размещении</span><span class="sxs-lookup"><span data-stu-id="0bca9-164">HTTPS certificates for self-hosted applications</span></span>

<span data-ttu-id="0bca9-165">При запуске приложения gRPC в рабочей среде следует использовать сертификат TLS из доверенного центра сертификации (ЦС).</span><span class="sxs-lookup"><span data-stu-id="0bca9-165">When you're running a gRPC application in production, you should use a TLS certificate from a trusted certificate authority (CA).</span></span> <span data-ttu-id="0bca9-166">Это может быть общедоступный ЦС или внутренний центр для вашей организации.</span><span class="sxs-lookup"><span data-stu-id="0bca9-166">This CA might be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="0bca9-167">На узлах Windows можно загрузить сертификат из безопасного [хранилища сертификатов](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) с помощью <xref:System.Security.Cryptography.X509Certificates.X509Store> класса.</span><span class="sxs-lookup"><span data-stu-id="0bca9-167">On Windows hosts, you can load the certificate from a secure [certificate store](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) by using the <xref:System.Security.Cryptography.X509Certificates.X509Store> class.</span></span> <span data-ttu-id="0bca9-168">Вы также можете использовать `X509Store` класс с хранилищем ключей OpenSSL на некоторых узлах Linux.</span><span class="sxs-lookup"><span data-stu-id="0bca9-168">You can also use the `X509Store` class with the OpenSSL key store on some Linux hosts.</span></span>

<span data-ttu-id="0bca9-169">Сертификаты также можно создавать с помощью одного из [конструкторов X509Certificate2](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A):</span><span class="sxs-lookup"><span data-stu-id="0bca9-169">You can also create certificates by using one of the [X509Certificate2 constructors](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), from either:</span></span>

* <span data-ttu-id="0bca9-170">Файл, например `.pfx` файл, защищенный надежным паролем</span><span class="sxs-lookup"><span data-stu-id="0bca9-170">A file, such as a `.pfx` file protected by a strong password</span></span>
* <span data-ttu-id="0bca9-171">Двоичные данные, полученные из службы безопасного хранения, например [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span><span class="sxs-lookup"><span data-stu-id="0bca9-171">Binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span></span>

<span data-ttu-id="0bca9-172">Настроить Kestrel для использования сертификата можно двумя способами: из конфигурации или в коде.</span><span class="sxs-lookup"><span data-stu-id="0bca9-172">You can configure Kestrel to use a certificate in two ways: from configuration or in code.</span></span>

### <a name="set-https-certificates-by-using-configuration"></a><span data-ttu-id="0bca9-173">Настройка сертификатов HTTPS с помощью конфигурации</span><span class="sxs-lookup"><span data-stu-id="0bca9-173">Set HTTPS certificates by using configuration</span></span>

<span data-ttu-id="0bca9-174">Подход к настройке требует установки пути к `.pfx` файлу сертификата и паролю в разделе конфигурации Kestrel.</span><span class="sxs-lookup"><span data-stu-id="0bca9-174">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="0bca9-175">В это `appsettings.json` будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0bca9-175">In `appsettings.json`, that would look like this:</span></span>

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "cert.pfx",
        "Password": "DO NOT STORE PLAINTEXT PASSWORDS IN APPSETTINGS FILES"
      }
    }
  }
}
```

<span data-ttu-id="0bca9-176">Укажите пароль с помощью безопасного источника конфигурации, например Azure Key Vault или хранилища Hashicorp.</span><span class="sxs-lookup"><span data-stu-id="0bca9-176">Provide the password by using a secure configuration source such as Azure Key Vault or Hashicorp Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0bca9-177">Не храните незашифрованные пароли в файлах конфигурации.</span><span class="sxs-lookup"><span data-stu-id="0bca9-177">Don't store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="0bca9-178">Настройка сертификатов HTTPS в коде</span><span class="sxs-lookup"><span data-stu-id="0bca9-178">Set HTTPS certificates in code</span></span>

<span data-ttu-id="0bca9-179">Чтобы настроить HTTPS для Kestrel в коде, используйте `ConfigureKestrel` метод для `IWebHostBuilder` в `Program` классе.</span><span class="sxs-lookup"><span data-stu-id="0bca9-179">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
            webBuilder.ConfigureKestrel(kestrel =>
            {
                kestrel.ConfigureHttpsDefaults(https =>
                {
                    https.ServerCertificate = new X509Certificate2("mycert.pfx", "password");
                });
            });
        });
```

<span data-ttu-id="0bca9-180">Опять же, обязательно сохраните пароль для `.pfx` файла в и извлеките его из защищенного источника конфигурации.</span><span class="sxs-lookup"><span data-stu-id="0bca9-180">Again, be sure to store the password for the `.pfx` file in, and retrieve it from, a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0bca9-181">[Назад](grpc-in-production.md)
>[Вперед](docker.md)</span><span class="sxs-lookup"><span data-stu-id="0bca9-181">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
