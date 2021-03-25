---
title: <remarks> Руководство по программированию на C#.
description: Сведения о теге <remarks> в XML. Этот тег позволяет добавить сведения о типе, дополняющие информацию, которая указана с помощью <summary>.
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 2227dd8bd4d81f5fda8cf529e18c7a613cca6b8e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477824"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="31095-106">\<remarks> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="31095-106">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="31095-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="31095-107">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="31095-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="31095-108">Parameters</span></span>

- `Description`

  <span data-ttu-id="31095-109">Описание элемента.</span><span class="sxs-lookup"><span data-stu-id="31095-109">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="31095-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="31095-110">Remarks</span></span>

<span data-ttu-id="31095-111">Тег `<remarks>` позволяет добавить сведения о типе, дополняющие информацию, указанную с помощью тега [\<summary>](./summary.md).</span><span class="sxs-lookup"><span data-stu-id="31095-111">The `<remarks>` tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="31095-112">Эти сведения отображаются в окне "Обозреватель объектов".</span><span class="sxs-lookup"><span data-stu-id="31095-112">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="31095-113">Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="31095-113">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="31095-114">Пример</span><span class="sxs-lookup"><span data-stu-id="31095-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="31095-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="31095-115">See also</span></span>

- [<span data-ttu-id="31095-116">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="31095-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="31095-117">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="31095-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
