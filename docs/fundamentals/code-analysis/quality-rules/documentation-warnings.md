---
title: Правила документирования (анализ кода)
description: Дополнительные сведения о правилах документирования для анализа кода
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
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96592665"
---
# <a name="documentation-rules"></a><span data-ttu-id="51859-103">Правила документирования</span><span class="sxs-lookup"><span data-stu-id="51859-103">Documentation rules</span></span>

<span data-ttu-id="51859-104">Правила документации поддерживают написание хорошо задокументированных библиотек путем правильного использования [комментариев XML-документации](../../../csharp/codedoc.md) для видимых извне API-интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="51859-104">Documentation rules support writing well-documented libraries through the correct use of [XML documentation comments](../../../csharp/codedoc.md) for externally visible APIs.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="51859-105">Содержание раздела</span><span class="sxs-lookup"><span data-stu-id="51859-105">In this section</span></span>

| <span data-ttu-id="51859-106">Правило</span><span class="sxs-lookup"><span data-stu-id="51859-106">Rule</span></span> | <span data-ttu-id="51859-107">Описание</span><span class="sxs-lookup"><span data-stu-id="51859-107">Description</span></span> |
| - | - |
| [<span data-ttu-id="51859-108">CA1200: Избегайте использования тегов cref с префиксом</span><span class="sxs-lookup"><span data-stu-id="51859-108">CA1200: Avoid using cref tags with a prefix</span></span>](ca1200.md) | <span data-ttu-id="51859-109">Атрибут [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) в теге XML-документации означает "code reference" (кодовая ссылка).</span><span class="sxs-lookup"><span data-stu-id="51859-109">The [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) attribute in an XML documentation tag means "code reference".</span></span> <span data-ttu-id="51859-110">Он указывает, что текст внутри тега представляет собой элемент кода, например тип, метод или свойство.</span><span class="sxs-lookup"><span data-stu-id="51859-110">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="51859-111">Старайтесь не использовать теги `cref` с префиксами, так как это не позволяет компилятору проверять ссылки.</span><span class="sxs-lookup"><span data-stu-id="51859-111">Avoid using `cref` tags with prefixes, because it prevents the compiler from verifying references.</span></span> <span data-ttu-id="51859-112">Это также мешает поиску и обновлению этих символьных ссылок во время рефакторинга в интегрированной среде разработки (IDE) Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="51859-112">It also prevents the Visual Studio integrated development environment (IDE) from finding and updating these symbol references during refactorings.</span></span> |
