---
title: Критическое изменение. IIS. Строки запросов ПО промежуточного слоя UrlRewrite сохраняются
description: 'Сведения о критическом изменении в ASP.NET Core 5.0 — IIS: Строки запросов ПО промежуточного слоя UrlRewrite сохраняются'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 3439844f04c89059a027c1264401efc46cd0d57e
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497670"
---
# <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a><span data-ttu-id="a1dfc-103">IIS. Строки запросов ПО промежуточного слоя UrlRewrite сохраняются</span><span class="sxs-lookup"><span data-stu-id="a1dfc-103">IIS: UrlRewrite middleware query strings are preserved</span></span>

<span data-ttu-id="a1dfc-104">Ошибки в ПО промежуточного слоя IIS UrlRewrite не позволили сохранить строку запроса в правиле перезаписи.</span><span class="sxs-lookup"><span data-stu-id="a1dfc-104">An IIS UrlRewrite middleware defect prevented the query string from being preserved in rewrite rules.</span></span> <span data-ttu-id="a1dfc-105">Эта ошибка исправлена, чтобы обеспечить соответствие поведению модуля IIS UrlRewrite.</span><span class="sxs-lookup"><span data-stu-id="a1dfc-105">That defect has been fixed to maintain consistency with the IIS UrlRewrite Module's behavior.</span></span>

<span data-ttu-id="a1dfc-106">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#22972](https://github.com/dotnet/aspnetcore/issues/22972).</span><span class="sxs-lookup"><span data-stu-id="a1dfc-106">For discussion, see issue [dotnet/aspnetcore#22972](https://github.com/dotnet/aspnetcore/issues/22972).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a1dfc-107">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="a1dfc-107">Version introduced</span></span>

<span data-ttu-id="a1dfc-108">ASP.NET Core 5.0 (предварительная версия 7)</span><span class="sxs-lookup"><span data-stu-id="a1dfc-108">ASP.NET Core 5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="a1dfc-109">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="a1dfc-109">Old behavior</span></span>

<span data-ttu-id="a1dfc-110">Рассмотрим следующее правило перезаписи.</span><span class="sxs-lookup"><span data-stu-id="a1dfc-110">Consider the following rewrite rule:</span></span>

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

<span data-ttu-id="a1dfc-111">Предыдущее правило не присоединяет строку запроса.</span><span class="sxs-lookup"><span data-stu-id="a1dfc-111">The preceding rule doesn't append the query string.</span></span> <span data-ttu-id="a1dfc-112">Универсальный код ресурса (URI), такой как `/about?id=1`, перенаправляет в `/contact` вместо `/contact?id=1`.</span><span class="sxs-lookup"><span data-stu-id="a1dfc-112">A URI like `/about?id=1` redirects to `/contact` instead of `/contact?id=1`.</span></span> <span data-ttu-id="a1dfc-113">По умолчанию атрибут `appendQueryString` имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="a1dfc-113">The `appendQueryString` attribute defaults to `true` as well.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="a1dfc-114">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="a1dfc-114">New behavior</span></span>

<span data-ttu-id="a1dfc-115">Строка запроса сохраняется.</span><span class="sxs-lookup"><span data-stu-id="a1dfc-115">The query string is preserved.</span></span> <span data-ttu-id="a1dfc-116">Код URI из примера в разделе [Старое поведение](#old-behavior) будет иметь значение `/contact?id=1`.</span><span class="sxs-lookup"><span data-stu-id="a1dfc-116">The URI from the example in [Old behavior](#old-behavior) would be `/contact?id=1`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a1dfc-117">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="a1dfc-117">Reason for change</span></span>

<span data-ttu-id="a1dfc-118">Старое поведение не соответствовало поведению модуля IIS UrlRewrite.</span><span class="sxs-lookup"><span data-stu-id="a1dfc-118">The old behavior didn't match the IIS UrlRewrite Module's behavior.</span></span> <span data-ttu-id="a1dfc-119">Для поддержки переноса между ПО промежуточного слоя и модулем важно обеспечить согласованное поведение.</span><span class="sxs-lookup"><span data-stu-id="a1dfc-119">To support porting between the middleware and module, the goal is to maintain consistent behaviors.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a1dfc-120">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="a1dfc-120">Recommended action</span></span>

<span data-ttu-id="a1dfc-121">Если удаление строки запроса является предпочтительным поведением, следует установить для элемента `action` значение `appendQueryString="false"`.</span><span class="sxs-lookup"><span data-stu-id="a1dfc-121">If the behavior of removing the query string is preferred, set the `action` element to `appendQueryString="false"`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a1dfc-122">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="a1dfc-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->
