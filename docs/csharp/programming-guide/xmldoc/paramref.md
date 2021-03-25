---
title: Руководство по программированию на C#. <paramref>
description: Сведения о теге <paramref> в XML. Этот тег позволяет указать, что присутствующее в коде слово является параметром.
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: e559a899aad7806bb7ccef32be49954fabed6a32
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477871"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="3ca5c-104">\<paramref> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="3ca5c-104">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="3ca5c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3ca5c-105">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="3ca5c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3ca5c-106">Parameters</span></span>

- `name`

  <span data-ttu-id="3ca5c-107">Имя параметра, на который указывается ссылка.</span><span class="sxs-lookup"><span data-stu-id="3ca5c-107">The name of the parameter to refer to.</span></span> <span data-ttu-id="3ca5c-108">Имя заключается в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="3ca5c-108">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="3ca5c-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="3ca5c-109">Remarks</span></span>

<span data-ttu-id="3ca5c-110">Тег `<paramref>` позволяет указать, что слово в комментариях к коду, например в блоке `<summary>` или `<remarks>`, ссылается на параметр.</span><span class="sxs-lookup"><span data-stu-id="3ca5c-110">The `<paramref>` tag gives you a way to indicate that a word in the code comments, for example in a `<summary>` or `<remarks>` block refers to a parameter.</span></span> <span data-ttu-id="3ca5c-111">В XML-файл такое слово может выделяться особым образом, например курсивом или полужирным шрифтом.</span><span class="sxs-lookup"><span data-stu-id="3ca5c-111">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="3ca5c-112">Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="3ca5c-112">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="3ca5c-113">Пример</span><span class="sxs-lookup"><span data-stu-id="3ca5c-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="3ca5c-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3ca5c-114">See also</span></span>

- [<span data-ttu-id="3ca5c-115">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="3ca5c-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3ca5c-116">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="3ca5c-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
