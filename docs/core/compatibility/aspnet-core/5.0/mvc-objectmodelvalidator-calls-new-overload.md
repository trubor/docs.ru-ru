---
title: Критическое изменение. MVC. ObjectModelValidator вызывает новую перегрузку ValidationVisitor.Validate
description: 'Сведения о критическом изменении в ASP.NET Core 5.0 под названием MVC: ObjectModelValidator вызывает новую перегрузку ValidationVisitor.Validate'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 7bf07360f5d5e93641b7fbc6634fda2e9f3e649f
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497597"
---
# <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a>MVC. ObjectModelValidator вызывает новую перегрузку ValidationVisitor.Validate

В ASP.NET Core 5.0 была добавлена перегрузка <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>. Новая перегрузка принимает экземпляр модели верхнего уровня, содержащий свойства:

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> вызывает эту новую перегрузку `ValidationVisitor` для выполнения проверки. Эта новая перегрузка является актуальной, если ваша библиотека проверки интегрируется с системой проверки модели MVC ASP.NET Core.

Обсуждение этого вопроса см. на странице GitHub [dotnet/aspnetcore#26020](https://github.com/dotnet/aspnetcore/issues/26020).

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="old-behavior"></a>Старое поведение

`ObjectModelValidator` вызывает следующую перегрузку во время проверки модели:

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

## <a name="new-behavior"></a>Новое поведение

`ObjectModelValidator` вызывает следующую перегрузку во время проверки модели:

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

## <a name="reason-for-change"></a>Причина изменения

Это изменение было введено для поддержки средств проверки, например, <xref:System.ComponentModel.DataAnnotations.CompareAttribute>, которые используют проверку других свойств.

## <a name="recommended-action"></a>Рекомендованное действие

Платформы проверки, использующие `ObjectModelValidator` для вызова существующей перегрузки `ValidationVisitor`, должны переопределять новый метод при нацеливании на .NET 5.0 или более поздней версии:

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

## <a name="affected-apis"></a>Затронутые API

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
