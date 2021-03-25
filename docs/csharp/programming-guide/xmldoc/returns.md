---
title: <returns> Руководство по программированию на C#.
description: Сведения о теге <returns> в XML. Этот тег используется в комментариях к объявлению метода для описания возвращаемого значения.
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 6a098208a51ca31fe2278b7c696deb15a13f8e1e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477805"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="ba732-105">\<returns> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="ba732-105">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="ba732-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ba732-106">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="ba732-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="ba732-107">Parameters</span></span>

- `description`

  <span data-ttu-id="ba732-108">Описание возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="ba732-108">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba732-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="ba732-109">Remarks</span></span>

<span data-ttu-id="ba732-110">Тег `<returns>` следует использовать в комментариях к объявлению метода для описания возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="ba732-110">The `<returns>` tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="ba732-111">Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="ba732-111">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="ba732-112">Пример</span><span class="sxs-lookup"><span data-stu-id="ba732-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="ba732-113">См. также</span><span class="sxs-lookup"><span data-stu-id="ba732-113">See also</span></span>

- [<span data-ttu-id="ba732-114">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="ba732-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="ba732-115">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="ba732-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
