---
title: Правила документации (анализ кода)
description: Дополнительные сведения о правилах анализа кода
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- warnings, documentation
author: mavasani
ms.author: mavasani
ms.openlocfilehash: 29d1734eec29bd00d456b4b00c48c2e8ef223441
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2020
ms.locfileid: "96592665"
---
# <a name="documentation-rules"></a><span data-ttu-id="896f3-103">Правила документирования</span><span class="sxs-lookup"><span data-stu-id="896f3-103">Documentation rules</span></span>

<span data-ttu-id="896f3-104">Правила документации поддерживают написание хорошо документированных библиотек посредством правильного использования [комментариев XML-документации](../../../csharp/codedoc.md) для внешних видимых интерфейсов API.</span><span class="sxs-lookup"><span data-stu-id="896f3-104">Documentation rules support writing well-documented libraries through the correct use of [XML documentation comments](../../../csharp/codedoc.md) for externally visible APIs.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="896f3-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="896f3-105">In this section</span></span>

| <span data-ttu-id="896f3-106">Правило</span><span class="sxs-lookup"><span data-stu-id="896f3-106">Rule</span></span> | <span data-ttu-id="896f3-107">Описание</span><span class="sxs-lookup"><span data-stu-id="896f3-107">Description</span></span> |
| - | - |
| [<span data-ttu-id="896f3-108">CA1200: Избегайте использования тегов cref с префиксом</span><span class="sxs-lookup"><span data-stu-id="896f3-108">CA1200: Avoid using cref tags with a prefix</span></span>](ca1200.md) | <span data-ttu-id="896f3-109">Атрибут [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) в ТЕГЕ документации XML означает "ссылка на код".</span><span class="sxs-lookup"><span data-stu-id="896f3-109">The [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) attribute in an XML documentation tag means "code reference".</span></span> <span data-ttu-id="896f3-110">Он указывает, что текст внутри тега представляет собой элемент кода, например тип, метод или свойство.</span><span class="sxs-lookup"><span data-stu-id="896f3-110">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="896f3-111">Старайтесь не использовать `cref` теги с префиксами, так как это не позволяет компилятору проверять ссылки.</span><span class="sxs-lookup"><span data-stu-id="896f3-111">Avoid using `cref` tags with prefixes, because it prevents the compiler from verifying references.</span></span> <span data-ttu-id="896f3-112">Это также предотвращает Поиск и обновление этих ссылок на символы во время рефакторинга в интегрированной среде разработки (IDE) Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="896f3-112">It also prevents the Visual Studio integrated development environment (IDE) from finding and updating these symbol references during refactorings.</span></span> |
