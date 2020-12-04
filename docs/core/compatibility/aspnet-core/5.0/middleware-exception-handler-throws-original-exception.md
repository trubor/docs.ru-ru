---
title: 'Критическое изменение. ПО промежуточного слоя: ПО промежуточного слоя обработчика исключений создает исходное исключение, если обработчик не найден'
description: Сведения о критическом изменении в ASP.NET Core 5.0 — ПО промежуточного слоя. ПО промежуточного слоя обработчика исключений создает исходное исключение, если обработчик не найден
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 8801d3e6950d66fd9f24e051fd8729c50eb0b282
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759979"
---
# <a name="middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found"></a><span data-ttu-id="3ac9e-103">ПО промежуточного слоя: ПО промежуточного слоя обработчика исключений создает исходное исключение, если обработчик не найден</span><span class="sxs-lookup"><span data-stu-id="3ac9e-103">Middleware: Exception Handler Middleware throws original exception if handler not found</span></span>

<span data-ttu-id="3ac9e-104">В версиях, предшествующих ASP.NET Core 5.0, [ПО промежуточного слоя обработчика исключений](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) выполняет настроенный обработчик исключений при возникновении исключения.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-104">Before ASP.NET Core 5.0, the [Exception Handler Middleware](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) executes the configured exception handler when an exception has occurred.</span></span> <span data-ttu-id="3ac9e-105">Если обработчик исключений, настроенный с помощью <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath>, не найден, создается ответ HTTP 404.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-105">If the exception handler, configured via <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath>, can't be found, an HTTP 404 response is produced.</span></span> <span data-ttu-id="3ac9e-106">Ответ является ошибочным в том, что:</span><span class="sxs-lookup"><span data-stu-id="3ac9e-106">The response is misleading in that it:</span></span>

* <span data-ttu-id="3ac9e-107">Ошибка, похоже, вызвана пользователем.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-107">Seems to be a user error.</span></span>
* <span data-ttu-id="3ac9e-108">Сообщение не отображает тот факт, что на сервере произошло исключение.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-108">Obscures the fact that an exception occurred on the server.</span></span>

<span data-ttu-id="3ac9e-109">Чтобы устранить ошибку, возникшую в ASP.NET Core 5.0, `ExceptionHandlerMiddleware` создает исходное исключение, если не удается найти обработчик исключений.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-109">To address the misleading error in ASP.NET Core 5.0, the `ExceptionHandlerMiddleware` throws the original exception if the exception handler can't be found.</span></span> <span data-ttu-id="3ac9e-110">В результате на сервере создается ответ HTTP 500.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-110">As a result, an HTTP 500 response is produced by the server.</span></span> <span data-ttu-id="3ac9e-111">Ответ будет проще изучить в журналах сервера при отладке возникшей ошибки.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-111">The response will be easier to examine in the server logs when debugging the error that occurred.</span></span>

<span data-ttu-id="3ac9e-112">Обсуждение этого вопроса см. на странице GitHub [dotnet/aspnetcore#25288](https://github.com/dotnet/aspnetcore/issues/25288).</span><span class="sxs-lookup"><span data-stu-id="3ac9e-112">For discussion, see GitHub issue [dotnet/aspnetcore#25288](https://github.com/dotnet/aspnetcore/issues/25288).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3ac9e-113">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="3ac9e-113">Version introduced</span></span>

<span data-ttu-id="3ac9e-114">5.0 RC 1</span><span class="sxs-lookup"><span data-stu-id="3ac9e-114">5.0 RC 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="3ac9e-115">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="3ac9e-115">Old behavior</span></span>

<span data-ttu-id="3ac9e-116">ПО промежуточного слоя обработчика исключений создает ответ HTTP 404, если не удается найти настроенный обработчик исключений.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-116">The Exception Handler Middleware produces an HTTP 404 response if the configured exception handler can't be found.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="3ac9e-117">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="3ac9e-117">New behavior</span></span>

<span data-ttu-id="3ac9e-118">ПО промежуточного слоя обработчика исключений создает исходное исключение, если не удается найти настроенный обработчик исключений.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-118">The Exception Handler Middleware throws the original exception if the configured exception handler can't be found.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="3ac9e-119">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="3ac9e-119">Reason for change</span></span>

<span data-ttu-id="3ac9e-120">Ошибка HTTP 404 не позволяет понять, что на сервере возникло исключение.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-120">The HTTP 404 error doesn't make it obvious that an exception occurred on the server.</span></span> <span data-ttu-id="3ac9e-121">Это изменение выдает ошибку HTTP 500, чтобы сделать это очевидным:</span><span class="sxs-lookup"><span data-stu-id="3ac9e-121">This change produces an HTTP 500 error to make it obvious that:</span></span>

* <span data-ttu-id="3ac9e-122">Проблема не вызвана ошибкой пользователя.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-122">The problem isn't caused by a user error.</span></span>
* <span data-ttu-id="3ac9e-123">На сервере обнаружено исключение.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-123">An exception was encountered on the server.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3ac9e-124">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="3ac9e-124">Recommended action</span></span>

<span data-ttu-id="3ac9e-125">Изменения в API не требуются.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-125">There are no API changes.</span></span> <span data-ttu-id="3ac9e-126">Все существующие приложения будут по прежнему компилироваться и выполняться.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-126">All existing apps will continue to compile and run.</span></span> <span data-ttu-id="3ac9e-127">Созданное исключение обрабатывается сервером.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-127">The exception thrown is handled by the server.</span></span> <span data-ttu-id="3ac9e-128">Например, исключение преобразуется в ответ об ошибке HTTP 500 [Kestrel](/aspnet/core/fundamentals/servers/kestrel) или [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys).</span><span class="sxs-lookup"><span data-stu-id="3ac9e-128">For example, the exception is converted to an HTTP 500 error response by [Kestrel](/aspnet/core/fundamentals/servers/kestrel) or [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="3ac9e-129">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="3ac9e-129">Affected APIs</span></span>

<span data-ttu-id="3ac9e-130">None</span><span class="sxs-lookup"><span data-stu-id="3ac9e-130">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
