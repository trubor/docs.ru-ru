---
title: <example> Руководство по программированию на C#.
description: Сведения о теге <example> в XML. Этот тег позволяет указать пример использования метода или другого элемента библиотеки.
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: 8f9b4fa4ac447b853008576a46be9beeb583b018
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103479120"
---
# <a name="example-c-programming-guide"></a><span data-ttu-id="52316-105">\<example> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="52316-105">\<example> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="52316-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="52316-106">Syntax</span></span>

```xml
<example>description</example>
```

## <a name="parameters"></a><span data-ttu-id="52316-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="52316-107">Parameters</span></span>

- `description`

  <span data-ttu-id="52316-108">Описание примера кода.</span><span class="sxs-lookup"><span data-stu-id="52316-108">A description of the code sample.</span></span>

## <a name="remarks"></a><span data-ttu-id="52316-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="52316-109">Remarks</span></span>

<span data-ttu-id="52316-110">Тег `<example>` позволяет указать пример использования метода или другого элемента библиотеки.</span><span class="sxs-lookup"><span data-stu-id="52316-110">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="52316-111">Вместе с ним часто применяется тег [\<code>](./code.md).</span><span class="sxs-lookup"><span data-stu-id="52316-111">This commonly involves using the [\<code>](./code.md) tag.</span></span>

<span data-ttu-id="52316-112">Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="52316-112">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="52316-113">Пример</span><span class="sxs-lookup"><span data-stu-id="52316-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a><span data-ttu-id="52316-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="52316-114">See also</span></span>

- [<span data-ttu-id="52316-115">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="52316-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="52316-116">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="52316-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
