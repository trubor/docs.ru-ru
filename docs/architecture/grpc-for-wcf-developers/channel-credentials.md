---
title: Учетные данные канала — gRPC для разработчиков WCF
description: Как реализовать и использовать учетные данные канала gRPC в ASP.NET Core 3,0.
ms.date: 12/15/2020
ms.openlocfilehash: 3663bbf061156db957241e2a32dbb9c64562ade2
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938641"
---
# <a name="channel-credentials"></a><span data-ttu-id="b3b57-103">Учетные данные канала</span><span class="sxs-lookup"><span data-stu-id="b3b57-103">Channel credentials</span></span>

<span data-ttu-id="b3b57-104">Как следует из названия, учетные данные канала присоединяются к базовому каналу gRPC.</span><span class="sxs-lookup"><span data-stu-id="b3b57-104">As the name implies, channel credentials are attached to the underlying gRPC channel.</span></span> <span data-ttu-id="b3b57-105">Стандартная форма учетных данных канала использует проверку подлинности на основе сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="b3b57-105">The standard form of channel credentials uses client certificate authentication.</span></span> <span data-ttu-id="b3b57-106">В этом процессе клиент предоставляет сертификат TLS, когда он создает подключение, а затем сервер проверяет этот сертификат перед тем, как разрешить выполнение любых вызовов.</span><span class="sxs-lookup"><span data-stu-id="b3b57-106">In this process, the client provides a TLS certificate when it's making the connection, and then the server verifies this certificate before allowing any calls to be made.</span></span>

<span data-ttu-id="b3b57-107">Учетные данные канала можно объединить с учетными данными вызова для обеспечения полной безопасности службы gRPC.</span><span class="sxs-lookup"><span data-stu-id="b3b57-107">You can combine channel credentials with call credentials to provide comprehensive security for a gRPC service.</span></span> <span data-ttu-id="b3b57-108">Учетные данные канала подтверждают, что клиентскому приложению разрешен доступ к службе, а учетные данные вызова предоставляют сведения о пользователе, который использует клиентское приложение.</span><span class="sxs-lookup"><span data-stu-id="b3b57-108">The channel credentials prove that the client application is allowed to access the service, and the call credentials provide information about the person who is using the client application.</span></span>

<span data-ttu-id="b3b57-109">Проверка подлинности сертификата клиента работает для gRPC так же, как и для ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b3b57-109">Client certificate authentication works for gRPC the same way it works for ASP.NET Core.</span></span> <span data-ttu-id="b3b57-110">Дополнительные сведения см. [в разделе Настройка проверки подлинности сертификата в ASP.NET Core](/aspnet/core/security/authentication/certauth).</span><span class="sxs-lookup"><span data-stu-id="b3b57-110">For more information, see [Configure certificate authentication in ASP.NET Core](/aspnet/core/security/authentication/certauth).</span></span>

<span data-ttu-id="b3b57-111">В целях разработки можно использовать самозаверяющий сертификат, но для рабочей среды следует использовать правильный HTTPS-сертификат, подписанный доверенным центром сертификации.</span><span class="sxs-lookup"><span data-stu-id="b3b57-111">For development purposes you can use a self-signed certificate, but for production you should use a proper HTTPS certificate signed by a trusted authority.</span></span>

## <a name="add-certificate-authentication-to-the-server"></a><span data-ttu-id="b3b57-112">Добавление проверки подлинности на сертификат на сервер</span><span class="sxs-lookup"><span data-stu-id="b3b57-112">Add certificate authentication to the server</span></span>

<span data-ttu-id="b3b57-113">Настройте проверку подлинности на сертификате на уровне узла (например, на сервере Kestrel) и в конвейере ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b3b57-113">Configure certificate authentication both at the host level (for example, on the Kestrel server), and in the ASP.NET Core pipeline.</span></span>

### <a name="configure-certificate-validation-on-kestrel"></a><span data-ttu-id="b3b57-114">Настройка проверки сертификата в Kestrel</span><span class="sxs-lookup"><span data-stu-id="b3b57-114">Configure certificate validation on Kestrel</span></span>

<span data-ttu-id="b3b57-115">Можно настроить Kestrel (HTTP-сервер ASP.NET Core), чтобы требовать сертификат клиента, и при необходимости выполнить некоторую проверку предоставляемого сертификата перед приемом входящих подключений.</span><span class="sxs-lookup"><span data-stu-id="b3b57-115">You can configure Kestrel (the ASP.NET Core HTTP server) to require a client certificate, and optionally to carry out some validation of the supplied certificate, before accepting incoming connections.</span></span> <span data-ttu-id="b3b57-116">Эта конфигурация указывается в `CreateWebHostBuilder` методе `Program` класса, а не в `Startup` .</span><span class="sxs-lookup"><span data-stu-id="b3b57-116">You specify this configuration in the `CreateWebHostBuilder` method of the `Program` class, rather than in `Startup`.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            var serverCert = ObtainServerCertificate();
            webBuilder.UseStartup<Startup>()
                .ConfigureKestrel(kestrelServerOptions => {
                    kestrelServerOptions.ConfigureHttpsDefaults(opt =>
                    {
                        opt.ClientCertificateMode = ClientCertificateMode.RequireCertificate;

                        // Verify that client certificate was issued by same CA as server certificate
                        opt.ClientCertificateValidation = (certificate, chain, errors) =>
                            certificate.Issuer == serverCert.Issuer;
                    });
                });
        });

```

<span data-ttu-id="b3b57-117">Этот `ClientCertificateMode.RequireCertificate` параметр приводит к тому, что Kestrel немедленно отклоняет любой запрос на подключение, который не предоставляет сертификат клиента, но этот параметр сам по себе не проверяет предоставленный сертификат.</span><span class="sxs-lookup"><span data-stu-id="b3b57-117">The `ClientCertificateMode.RequireCertificate` setting causes Kestrel to immediately reject any connection request that doesn't provide a client certificate, but this setting by itself won't validate a certificate that is provided.</span></span> <span data-ttu-id="b3b57-118">Добавьте `ClientCertificateValidation` обратный вызов, чтобы включить Kestrel для проверки сертификата клиента в момент, когда соединение установлено, до того, как будет задействован конвейер ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b3b57-118">Add the `ClientCertificateValidation` callback to enable Kestrel to validate the client certificate at the point the connection is made, before the ASP.NET Core pipeline is engaged.</span></span> <span data-ttu-id="b3b57-119">(В этом случае обратный вызов гарантирует, что он был выдан тем же *центром сертификации* , что и сертификат сервера.)</span><span class="sxs-lookup"><span data-stu-id="b3b57-119">(In this case, the callback ensures that it was issued by the same *Certificate Authority* as the server certificate.)</span></span>

### <a name="add-aspnet-core-certificate-authentication"></a><span data-ttu-id="b3b57-120">Добавление ASP.NET Core проверки подлинности сертификата</span><span class="sxs-lookup"><span data-stu-id="b3b57-120">Add ASP.NET Core certificate authentication</span></span>

<span data-ttu-id="b3b57-121">Пакет NuGet [Microsoft. AspNetCore. Authentication. Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) обеспечивает проверку подлинности сертификата.</span><span class="sxs-lookup"><span data-stu-id="b3b57-121">The [Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet package provides certificate authentication.</span></span>

<span data-ttu-id="b3b57-122">Добавьте в метод службу проверки подлинности сертификата `ConfigureServices` и добавьте проверку подлинности и авторизацию в ASP.NET Core конвейер в `Configure` методе.</span><span class="sxs-lookup"><span data-stu-id="b3b57-122">Add the certificate authentication service in the `ConfigureServices` method, and add authentication and authorization to the ASP.NET Core pipeline in the `Configure` method.</span></span>

```csharp
public class Startup
{
    private readonly bool _isDevelopment;

    public Startup(IWebHostEnvironment env)
    {
        _isDevelopment = env.IsDevelopment();
    }

    public void ConfigureServices(IServiceCollection services)
    {
        services.AddAuthentication(CertificateAuthenticationDefaults.AuthenticationScheme)
            .AddCertificate(options =>
            {
                if (_isDevelopment)
                {
                    // DO NOT DO THIS IN PRODUCTION!
                    options.RevocationMode = X509RevocationMode.NoCheck;
                }
            });
        services.AddAuthorization();
        services.AddGrpc();
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        app.UseRouting();

        app.UseAuthentication();
        app.UseAuthorization();

        app.UseEndpoints(endpoints => { endpoints.MapGrpcService<GreeterService>(); });
    }
}
```

## <a name="provide-channel-credentials-in-the-client-application"></a><span data-ttu-id="b3b57-123">Указание учетных данных канала в клиентском приложении</span><span class="sxs-lookup"><span data-stu-id="b3b57-123">Provide channel credentials in the client application</span></span>

<span data-ttu-id="b3b57-124">С помощью `Grpc.Net.Client` пакета можно настроить сертификаты на <xref:System.Net.Http.HttpClient> экземпляре, который предоставляется для `GrpcChannel` соединения.</span><span class="sxs-lookup"><span data-stu-id="b3b57-124">With the `Grpc.Net.Client` package, you configure certificates on an <xref:System.Net.Http.HttpClient> instance that is provided to the `GrpcChannel` used for the connection.</span></span>

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        // Assume path to a client .pfx file and password are passed from command line
        // On Windows this would probably be a reference to the Certificate Store
        var cert = new X509Certificate2(args[0], args[1]);

        var handler = new HttpClientHandler();
        handler.ClientCertificates.Add(cert);
        var httpClient = new HttpClient(handler);

        var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
        {
            HttpClient = httpClient
        });

        var grpc = new Greeter.GreeterClient(channel);
        var response = await grpc.SayHelloAsync(new HelloRequest { Name = "Bob" });
        System.Console.WriteLine(response.Message);
    }
}
```

## <a name="combine-channelcredentials-and-callcredentials"></a><span data-ttu-id="b3b57-125">Объединение Чаннелкредентиалс и Каллкредентиалс</span><span class="sxs-lookup"><span data-stu-id="b3b57-125">Combine ChannelCredentials and CallCredentials</span></span>

<span data-ttu-id="b3b57-126">Вы можете настроить сервер для использования проверки подлинности сертификата и маркера.</span><span class="sxs-lookup"><span data-stu-id="b3b57-126">You can configure your server to use both certificate and token authentication.</span></span> <span data-ttu-id="b3b57-127">Для этого примените изменения сертификата к серверу Kestrel и используйте по промежуточного слоя JWT Bearer в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b3b57-127">To do this, apply the certificate changes to the Kestrel server, and use the JWT bearer middleware in ASP.NET Core.</span></span>

<span data-ttu-id="b3b57-128">Чтобы предоставить `ChannelCredentials` и `CallCredentials` на клиенте, используйте `ChannelCredentials.Create` метод для применения учетных данных вызова.</span><span class="sxs-lookup"><span data-stu-id="b3b57-128">To provide both `ChannelCredentials` and `CallCredentials` on the client, use the `ChannelCredentials.Create` method to apply the call credentials.</span></span> <span data-ttu-id="b3b57-129">Вам по-прежнему необходимо применить проверку подлинности с помощью сертификата, используя <xref:System.Net.Http.HttpClient> экземпляр.</span><span class="sxs-lookup"><span data-stu-id="b3b57-129">You still need to apply certificate authentication by using the <xref:System.Net.Http.HttpClient> instance.</span></span> <span data-ttu-id="b3b57-130">При передаче аргументов в `SslCredentials` конструктор внутренний клиентский код создает исключение.</span><span class="sxs-lookup"><span data-stu-id="b3b57-130">If you pass any arguments to the `SslCredentials` constructor, the internal client code throws an exception.</span></span> <span data-ttu-id="b3b57-131">`SslCredentials`Параметр включается только в `Grpc.Net.Client` `Create` метод пакета для обеспечения совместимости с `Grpc.Core` пакетом.</span><span class="sxs-lookup"><span data-stu-id="b3b57-131">The `SslCredentials` parameter is only included in the `Grpc.Net.Client` package's `Create` method to maintain compatibility with the `Grpc.Core` package.</span></span>

```csharp
var handler = new HttpClientHandler();
handler.ClientCertificates.Add(cert);

var httpClient = new HttpClient(handler);

var callCredentials = CallCredentials.FromInterceptor(((context, metadata) =>
    {
        metadata.Add("Authorization", $"Bearer {_token}");
    }));

var channelCredentials = ChannelCredentials.Create(new SslCredentials(), callCredentials);

var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
{
    HttpClient = httpClient,
    Credentials = channelCredentials
});

var grpc = new Portfolios.PortfoliosClient(channel);
```

> [!TIP]
> <span data-ttu-id="b3b57-132">Для клиента можно использовать `ChannelCredentials.Create` метод без проверки подлинности сертификата.</span><span class="sxs-lookup"><span data-stu-id="b3b57-132">You can use the `ChannelCredentials.Create` method for a client without certificate authentication.</span></span> <span data-ttu-id="b3b57-133">Это удобный способ передачи учетных данных маркера при каждом вызове, сделанном в канале.</span><span class="sxs-lookup"><span data-stu-id="b3b57-133">This is a useful way to pass token credentials with every call made on the channel.</span></span>

<span data-ttu-id="b3b57-134">Версия [примера приложения Фуллстокктиккер gRPC с проверкой подлинности с помощью сертификата](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) находится на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="b3b57-134">A version of the [FullStockTicker sample gRPC application with certificate authentication added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b3b57-135">[Назад](call-credentials.md)
>[Вперед](encryption.md)</span><span class="sxs-lookup"><span data-stu-id="b3b57-135">[Previous](call-credentials.md)
[Next](encryption.md)</span></span>
