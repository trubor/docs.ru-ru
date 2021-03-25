---
title: Руководство по программированию на C#. <c>
description: Сведения о теге <c> в XML. С помощью этого тега можно пометить однострочный текст в описании как код, если код <code> представлен несколькими строкамиindicates multiple lines..
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: fc445c7245287c3835543e4bbe4b3b46ec46fd35
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478697"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="47f80-104">\<c> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="47f80-104">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="47f80-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="47f80-105">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="47f80-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="47f80-106">Parameters</span></span>

- `text`

  <span data-ttu-id="47f80-107">Текст, который нужно указать в качестве кода.</span><span class="sxs-lookup"><span data-stu-id="47f80-107">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="47f80-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="47f80-108">Remarks</span></span>

<span data-ttu-id="47f80-109">С помощью тега `<c>` можно указать, что текст в описании необходимо пометить как код.</span><span class="sxs-lookup"><span data-stu-id="47f80-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="47f80-110">Чтобы определить несколько строк в качестве кода, используйте тег [\<code>](./code.md).</span><span class="sxs-lookup"><span data-stu-id="47f80-110">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="47f80-111">Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="47f80-111">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="47f80-112">Пример</span><span class="sxs-lookup"><span data-stu-id="47f80-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="47f80-113">См. также</span><span class="sxs-lookup"><span data-stu-id="47f80-113">See also</span></span>

- [<span data-ttu-id="47f80-114">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="47f80-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="47f80-115">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="47f80-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
