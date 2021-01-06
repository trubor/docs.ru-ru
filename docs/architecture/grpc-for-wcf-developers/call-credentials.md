---
title: Вызов учетных данных — gRPC для разработчиков WCF
description: Как реализовать и использовать учетные данные вызова gRPC в ASP.NET Core 3,0.
ms.date: 12/15/2020
ms.openlocfilehash: 66394c75929bf068f83d631e022b467386e59ec5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938446"
---
# <a name="call-credentials"></a><span data-ttu-id="f5bdc-103">Учетные данные вызова</span><span class="sxs-lookup"><span data-stu-id="f5bdc-103">Call credentials</span></span>

<span data-ttu-id="f5bdc-104">Учетные данные вызова основаны на маркере, переданном в метаданных с каждым запросом.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-104">Call credentials are all based on a token passed in metadata with each request.</span></span>

## <a name="ws-federation"></a><span data-ttu-id="f5bdc-105">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="f5bdc-105">WS-Federation</span></span>

<span data-ttu-id="f5bdc-106">ASP.NET Core поддерживает WS-Federation с помощью пакета NuGet [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) .</span><span class="sxs-lookup"><span data-stu-id="f5bdc-106">ASP.NET Core supports WS-Federation using the [WsFederation](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.WsFederation) NuGet package.</span></span> <span data-ttu-id="f5bdc-107">WS-Federation является ближайшей доступной альтернативой проверки подлинности Windows, которая не поддерживается по протоколу HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-107">WS-Federation is the closest available alternative to Windows Authentication, which isn't supported over HTTP/2.</span></span> <span data-ttu-id="f5bdc-108">Проверка подлинности пользователей осуществляется с помощью службы федерации Active Directory (AD FS) (AD FS), который предоставляет маркер, который можно использовать для проверки подлинности с помощью ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-108">Users are authenticated by using Active Directory Federation Services (AD FS), which provides a token that can be used to authenticate with ASP.NET Core.</span></span>

<span data-ttu-id="f5bdc-109">Дополнительные сведения о том, как приступить к работе с этим методом проверки подлинности, см. [в разделе Проверка подлинности пользователей с WS-Federation в ASP.NET Core](/aspnet/core/security/authentication/ws-federation).</span><span class="sxs-lookup"><span data-stu-id="f5bdc-109">For more information on how to get started with this authentication method, see [Authenticate users with WS-Federation in ASP.NET Core](/aspnet/core/security/authentication/ws-federation).</span></span>

## <a name="jwt-bearer-tokens"></a><span data-ttu-id="f5bdc-110">Токены носителя JWT</span><span class="sxs-lookup"><span data-stu-id="f5bdc-110">JWT Bearer tokens</span></span>

<span data-ttu-id="f5bdc-111">Стандарт [JSON Web Token](https://jwt.io) (JWT) предоставляет способ кодирования сведений о пользователе и их утверждениях в закодированной строке.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-111">The [JSON Web Token](https://jwt.io) (JWT) standard provides a way to encode information about a user and their claims in an encoded string.</span></span> <span data-ttu-id="f5bdc-112">Он также предоставляет способ подписи маркера, чтобы потребитель мог проверить целостность маркера с помощью шифрования с открытым ключом.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-112">It also provides a way to sign that token, so that the consumer can verify the integrity of the token by using public key cryptography.</span></span> <span data-ttu-id="f5bdc-113">Можно использовать различные службы, например IdentityServer4, для проверки подлинности пользователей и создания маркеров OpenID Connect Connect (OIDC) для использования с gRPC и API HTTP.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-113">You can use various services, such as IdentityServer4, to authenticate users and generate OpenID Connect (OIDC) tokens to use with gRPC and HTTP APIs.</span></span>

<span data-ttu-id="f5bdc-114">ASP.NET Core 5,0 может работать с JWT с помощью пакета носителя JWT.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-114">ASP.NET Core 5.0 can handle JWTs by using the JWT Bearer package.</span></span> <span data-ttu-id="f5bdc-115">Конфигурация одинакова для приложения gRPC, так же как для приложения ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-115">The configuration is exactly the same for a gRPC application as it is for an ASP.NET Core MVC application.</span></span> <span data-ttu-id="f5bdc-116">Здесь мы рассмотрим токены носителя JWT, так как их проще разрабатывать, чем WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-116">Here, we'll focus on JWT Bearer tokens, because they're easier to develop with than WS-Federation.</span></span>

## <a name="add-authentication-and-authorization-to-the-server"></a><span data-ttu-id="f5bdc-117">Добавление проверки подлинности и авторизации на сервер</span><span class="sxs-lookup"><span data-stu-id="f5bdc-117">Add authentication and authorization to the server</span></span>

<span data-ttu-id="f5bdc-118">Пакет носителя JWT не входит в ASP.NET Core 5,0 по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-118">The JWT Bearer package isn't included in ASP.NET Core 5.0 by default.</span></span> <span data-ttu-id="f5bdc-119">Установите пакет NuGet [Microsoft. AspNetCore. Authentication. JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) в приложении.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-119">Install the [Microsoft.AspNetCore.Authentication.JwtBearer](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer) NuGet package in your app.</span></span>

<span data-ttu-id="f5bdc-120">Добавьте службу проверки подлинности в класс Startup и настройте обработчик носителя JWT:</span><span class="sxs-lookup"><span data-stu-id="f5bdc-120">Add the Authentication service in the Startup class, and configure the JWT Bearer handler:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();

    var signingKey = ObtainSigningKeySomehow();

    services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
        .AddJwtBearer(options =>
        {
            options.TokenValidationParameters =
                new TokenValidationParameters
                {
                    ValidateAudience = false,
                    ValidateIssuer = false,
                    ValidateActor = false,
                    ValidateLifetime = true,
                    IssuerSigningKey = signingKey
                };
        });

}
```

<span data-ttu-id="f5bdc-121">`IssuerSigningKey`Для этого свойства требуется реализация `Microsoft.IdentityModels.Tokens.SecurityKey` с использованием криптографических данных, необходимых для проверки подписанных токенов.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-121">The `IssuerSigningKey` property requires an implementation of `Microsoft.IdentityModels.Tokens.SecurityKey` with the cryptographic data necessary to validate the signed tokens.</span></span> <span data-ttu-id="f5bdc-122">Безопасно Храните этот маркер на *сервере секретов*, например Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-122">Store this token securely in a *secrets server*, like Azure Key Vault.</span></span>

<span data-ttu-id="f5bdc-123">Затем добавьте службу авторизации, которая управляет доступом к системе:</span><span class="sxs-lookup"><span data-stu-id="f5bdc-123">Next, add the Authorization service, which controls access to the system:</span></span>

```csharp
    services.AddAuthorization(options =>
    {
        options.AddPolicy(JwtBearerDefaults.AuthenticationScheme, policy =>
        {
            policy.AddAuthenticationSchemes(JwtBearerDefaults.AuthenticationScheme);
            policy.RequireClaim(ClaimTypes.Name);
        });
    });

```

> [!TIP]
> <span data-ttu-id="f5bdc-124">Проверка подлинности и авторизация — это два отдельных шага.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-124">Authentication and authorization are two separate steps.</span></span> <span data-ttu-id="f5bdc-125">Для определения удостоверения пользователя используется проверка подлинности.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-125">You use authentication to determine the user's identity.</span></span> <span data-ttu-id="f5bdc-126">С помощью авторизации можно определить, разрешено ли этому пользователю доступ к различным частям системы.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-126">You use authorization to decide whether that user is allowed to access various parts of the system.</span></span>

<span data-ttu-id="f5bdc-127">Теперь добавьте по промежуточного слоя проверки подлинности и авторизации в ASP.NET Core конвейер в `Configure` методе:</span><span class="sxs-lookup"><span data-stu-id="f5bdc-127">Now add the authentication and authorization middleware to the ASP.NET Core pipeline in the `Configure` method:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    // Authenticate, then Authorize
    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

<span data-ttu-id="f5bdc-128">Наконец, примените `[Authorize]` атрибут к любым службам или методам, которые необходимо защитить, и используйте `User` свойство из базового `HttpContext` для проверки разрешений.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-128">Finally, apply the `[Authorize]` attribute to any services or methods to be secured, and use the `User` property from the underlying `HttpContext` to verify permissions.</span></span>

```csharp
[Authorize]
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!TryValidateUser(request.TraderId, context.GetHttpContext().User))
    {
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Denied."));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}
```

## <a name="provide-call-credentials-in-the-client-application"></a><span data-ttu-id="f5bdc-129">Предоставление учетных данных вызова в клиентском приложении</span><span class="sxs-lookup"><span data-stu-id="f5bdc-129">Provide call credentials in the client application</span></span>

<span data-ttu-id="f5bdc-130">После получения маркера JWT с сервера удостоверений его можно использовать для проверки подлинности вызовов gRPC из клиента, добавив его в качестве заголовка метаданных в вызове следующим образом:</span><span class="sxs-lookup"><span data-stu-id="f5bdc-130">After you've obtained a JWT token from an identity server, you can use it to authenticate gRPC calls from the client by adding it as a metadata header on the call, as follows:</span></span>

```csharp
public async Task ShowPortfolioAsync(int portfolioId)
{
    var headers = new Grpc.Core.Metadata
    {
        { "Authorization", $"Bearer {_userToken}" }
    };
    var request = new GetRequest
    {
        TraderId = _userId,
        PortfolioId = portfolioId
    };
    var response = await _portfoliosClient.GetAsync(request, headers);

    // Display portfolio
}
```

<span data-ttu-id="f5bdc-131">Теперь вы защитили службу gRPC с помощью токенов носителя JWT в качестве учетных данных вызова.</span><span class="sxs-lookup"><span data-stu-id="f5bdc-131">Now you've secured your gRPC service by using JWT bearer tokens as call credentials.</span></span> <span data-ttu-id="f5bdc-132">В GitHub будет [добавлена версия примера gRPC приложения с проверкой подлинности и авторизацией](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) .</span><span class="sxs-lookup"><span data-stu-id="f5bdc-132">A version of the [portfolios sample gRPC application with authentication and authorization added](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/grpc/TraderSysAuth) is on GitHub.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f5bdc-133">[Назад](security.md)
>[Вперед](channel-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="f5bdc-133">[Previous](security.md)
[Next](channel-credentials.md)</span></span>
