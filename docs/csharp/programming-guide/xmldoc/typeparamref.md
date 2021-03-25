---
title: Руководство по программированию на C#. <typeparamref>
description: Сведения о теге <typeparamref> в XML. Этот тег разрешает получателям файла документации форматировать слово определенным образом, например курсивным шрифтом.
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 1bb9a73f4122f3b9d521565a7172a9b8f75f7a98
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477664"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="0c746-104">\<typeparamref> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="0c746-104">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="0c746-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0c746-105">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="0c746-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0c746-106">Parameters</span></span>

- `name`

  <span data-ttu-id="0c746-107">Имя параметра типа.</span><span class="sxs-lookup"><span data-stu-id="0c746-107">The name of the type parameter.</span></span> <span data-ttu-id="0c746-108">Имя заключается в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="0c746-108">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="0c746-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="0c746-109">Remarks</span></span>

<span data-ttu-id="0c746-110">Дополнительные сведения о параметрах типа в универсальных типах и методах см. в разделе [Универсальные шаблоны](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="0c746-110">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="0c746-111">Используйте этот тег, чтобы разрешить получателям файла документации форматировать слово определенным образом, например курсивным шрифтом.</span><span class="sxs-lookup"><span data-stu-id="0c746-111">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="0c746-112">Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="0c746-112">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="0c746-113">Пример</span><span class="sxs-lookup"><span data-stu-id="0c746-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="0c746-114">См. также</span><span class="sxs-lookup"><span data-stu-id="0c746-114">See also</span></span>

- [<span data-ttu-id="0c746-115">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="0c746-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="0c746-116">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="0c746-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
