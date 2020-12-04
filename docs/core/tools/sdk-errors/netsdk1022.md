---
title: 'NETSDK1022: Duplicate items were included.'
description: Как разрешить сообщение о повторяющемся элементе на основе параметров по умолчанию.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: c2bdbbb5503e5e4f6e6826f95f5a2cb08c908ceb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717878"
---
# <a name="netsdk1022-duplicate-items-were-included"></a><span data-ttu-id="8d148-103">NETSDK1022: Duplicate items were included.</span><span class="sxs-lookup"><span data-stu-id="8d148-103">NETSDK1022: Duplicate items were included.</span></span>

<span data-ttu-id="8d148-104">**Эта статья относится к:** ✔️ пакету SDK для .NET Core 2.1.100 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="8d148-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="8d148-105">Начиная с Visual Studio 2017 или MSBuild версии 15.3 пакет SDK для .NET автоматически включает элементы из каталога проекта по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8d148-105">Starting in Visual Studio 2017 / MSBuild version 15.3, the .NET SDK automatically includes items from the project directory by default.</span></span>  <span data-ttu-id="8d148-106">Сюда входят целевые объекты `Compile` и `Content`.</span><span class="sxs-lookup"><span data-stu-id="8d148-106">This includes `Compile` and `Content` targets.</span></span>  <span data-ttu-id="8d148-107">Это поможет значительно очистить файл проекта и упростить его.</span><span class="sxs-lookup"><span data-stu-id="8d148-107">This should greatly clean up your project file and reduce the complexity you have there.</span></span>

<span data-ttu-id="8d148-108">Можно вернуться к предыдущему поведению, задав для свойства значение false.</span><span class="sxs-lookup"><span data-stu-id="8d148-108">You can revert to the earlier behavior by setting the correct property to false.</span></span>

<span data-ttu-id="8d148-109">Пример для элементов `Compile`:</span><span class="sxs-lookup"><span data-stu-id="8d148-109">Example for `Compile` items:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
