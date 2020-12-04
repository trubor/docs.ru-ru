---
title: 'NETSDK1013: Значение TargetFramework не распознано.'
description: Как определить и задать допустимое значение TargetFramework
author: marcpop
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1013
ms.openlocfilehash: 915ac22ad822d17c082498b469acbfb3f1a93efc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717879"
---
# <a name="netsdk1013-the-targetframework-value-was-not-recognized"></a><span data-ttu-id="9a993-103">NETSDK1013: Значение TargetFramework не распознано</span><span class="sxs-lookup"><span data-stu-id="9a993-103">NETSDK1013: The TargetFramework value was not recognized</span></span>

<span data-ttu-id="9a993-104">**Эта статья относится к:** ✔️ пакету SDK для .NET Core 3.1.100 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="9a993-104">**This article applies to:** ✔️ .NET Core 3.1.100 SDK and later versions</span></span>

<span data-ttu-id="9a993-105">Пакет SDK пытается выполнить синтаксический анализ значений, предоставленных в файле проекта для `<TargetFramework>` или `<TargetFrameworks>`, в хорошо известное значение.</span><span class="sxs-lookup"><span data-stu-id="9a993-105">The SDK tries to parse the values provided in the project file for `<TargetFramework>` or `<TargetFrameworks>` into a well known value.</span></span>  <span data-ttu-id="9a993-106">Если значение не распознано, для `TargetFrameworkIdentifier` или `TargetFrameworkVersion` может быть задана пустая строка или `Unsupported`.</span><span class="sxs-lookup"><span data-stu-id="9a993-106">If the value is not recognized, the `TargetFrameworkIdentifier` or `TargetFrameworkVersion` value may be set to an empty string or `Unsupported`.</span></span>

<span data-ttu-id="9a993-107">Чтобы устранить эту проблему, проверьте правильность написания значения `TargetFramework` из списка [поддерживаемых платформ](../../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="9a993-107">To resolve this, check the spelling of your `TargetFramework` value from the list of [supported frameworks](../../../standard/frameworks.md).</span></span>
<span data-ttu-id="9a993-108">Вы также можете задать свойства `TargetFrameworkIdentifier` и `TargetFrameworkVersion` напрямую в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="9a993-108">You can also set the `TargetFrameworkIdentifier` and `TargetFrameworkVersion` properties directly in your project file.</span></span>

```xml
<PropertyGroup Condition="'$(TargetFrameworkIdentifier)' == ''">
  <TargetFrameworkIdentifier>.NETCOREAPP</TargetFrameworkIdentifier>
  <TargetFrameworkVersion>3.1</TargetFrameworkVersion>
</PropertyGroup>
```
