---
title: Критическое изменение. MVC. ObjectModelValidator вызывает новую перегрузку ValidationVisitor.Validate
description: 'Сведения о критическом изменении в ASP.NET Core 5.0 под названием MVC: ObjectModelValidator вызывает новую перегрузку ValidationVisitor.Validate'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b28c357f51291a4f73889d5d413a983f79e09daf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760015"
---
# <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a><span data-ttu-id="fc691-103">MVC. ObjectModelValidator вызывает новую перегрузку ValidationVisitor.Validate</span><span class="sxs-lookup"><span data-stu-id="fc691-103">MVC: ObjectModelValidator calls a new overload of ValidationVisitor.Validate</span></span>

<span data-ttu-id="fc691-104">В ASP.NET Core 5.0 была добавлена перегрузка <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fc691-104">In ASP.NET Core 5.0, an overload of the <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> was added.</span></span> <span data-ttu-id="fc691-105">Новая перегрузка принимает экземпляр модели верхнего уровня, содержащий свойства:</span><span class="sxs-lookup"><span data-stu-id="fc691-105">The new overload accepts the top-level model instance that contains properties:</span></span>

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<span data-ttu-id="fc691-106"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> вызывает эту новую перегрузку `ValidationVisitor` для выполнения проверки.</span><span class="sxs-lookup"><span data-stu-id="fc691-106"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> invokes this new overload of `ValidationVisitor` to perform validation.</span></span> <span data-ttu-id="fc691-107">Эта новая перегрузка является актуальной, если ваша библиотека проверки интегрируется с системой проверки модели MVC ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="fc691-107">This new overload is pertinent if your validation library integrates with ASP.NET Core MVC's model validation system.</span></span>

<span data-ttu-id="fc691-108">Обсуждение этого вопроса см. на странице GitHub [dotnet/aspnetcore#26020](https://github.com/dotnet/aspnetcore/issues/26020).</span><span class="sxs-lookup"><span data-stu-id="fc691-108">For discussion, see GitHub issue [dotnet/aspnetcore#26020](https://github.com/dotnet/aspnetcore/issues/26020).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="fc691-109">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="fc691-109">Version introduced</span></span>

<span data-ttu-id="fc691-110">5.0</span><span class="sxs-lookup"><span data-stu-id="fc691-110">5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="fc691-111">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="fc691-111">Old behavior</span></span>

<span data-ttu-id="fc691-112">`ObjectModelValidator` вызывает следующую перегрузку во время проверки модели:</span><span class="sxs-lookup"><span data-stu-id="fc691-112">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

## <a name="new-behavior"></a><span data-ttu-id="fc691-113">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="fc691-113">New behavior</span></span>

<span data-ttu-id="fc691-114">`ObjectModelValidator` вызывает следующую перегрузку во время проверки модели:</span><span class="sxs-lookup"><span data-stu-id="fc691-114">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

## <a name="reason-for-change"></a><span data-ttu-id="fc691-115">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="fc691-115">Reason for change</span></span>

<span data-ttu-id="fc691-116">Это изменение было введено для поддержки средств проверки, например, <xref:System.ComponentModel.DataAnnotations.CompareAttribute>, которые используют проверку других свойств.</span><span class="sxs-lookup"><span data-stu-id="fc691-116">This change was introduced to support validators, such as <xref:System.ComponentModel.DataAnnotations.CompareAttribute>, that rely on inspection of other properties.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="fc691-117">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="fc691-117">Recommended action</span></span>

<span data-ttu-id="fc691-118">Платформы проверки, использующие `ObjectModelValidator` для вызова существующей перегрузки `ValidationVisitor`, должны переопределять новый метод при нацеливании на .NET 5.0 или более поздней версии:</span><span class="sxs-lookup"><span data-stu-id="fc691-118">Validation frameworks that rely on `ObjectModelValidator` to invoke the existing overload of `ValidationVisitor` must override the new method when targeting .NET 5.0 or later:</span></span>

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

## <a name="affected-apis"></a><span data-ttu-id="fc691-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="fc691-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
