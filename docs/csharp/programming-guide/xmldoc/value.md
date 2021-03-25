---
title: <value> Руководство по программированию на C#.
description: Сведения о теге <value> в XML. Этот тег позволяет описать значение, которое представляется свойством.
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: c910a60a50e95621c1e3ad773000cbac0d43bb10
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477641"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="bfc0b-105">\<value> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="bfc0b-105">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="bfc0b-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bfc0b-106">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="bfc0b-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="bfc0b-107">Parameters</span></span>

- `property-description`

  <span data-ttu-id="bfc0b-108">Описание свойства.</span><span class="sxs-lookup"><span data-stu-id="bfc0b-108">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfc0b-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="bfc0b-109">Remarks</span></span>

<span data-ttu-id="bfc0b-110">Тег `<value>` позволяет описывать значение, которое представляется свойством.</span><span class="sxs-lookup"><span data-stu-id="bfc0b-110">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="bfc0b-111">При добавлении свойства с помощью мастера создания кода из среды разработки Visual Studio .NET для нового свойства будет добавлен тег [\<summary>](./summary.md).</span><span class="sxs-lookup"><span data-stu-id="bfc0b-111">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="bfc0b-112">После этого следует вручную добавить тег `<value>` для описания значения, которое представляется свойством.</span><span class="sxs-lookup"><span data-stu-id="bfc0b-112">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="bfc0b-113">Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="bfc0b-113">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="bfc0b-114">Пример</span><span class="sxs-lookup"><span data-stu-id="bfc0b-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="bfc0b-115">См. также</span><span class="sxs-lookup"><span data-stu-id="bfc0b-115">See also</span></span>

- [<span data-ttu-id="bfc0b-116">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="bfc0b-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="bfc0b-117">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="bfc0b-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
