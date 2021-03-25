---
title: <para> Руководство по программированию на C#.
description: Сведения о теге <para> в XML. Этот тег позволяет добавить структуру к тексту в другом теге, например <summary>, <remarks>или <returns>.
ms.date: 07/20/2015
f1_keywords:
- <para>
- para
helpviewer_keywords:
- <para> C# XML tag
- para C# XML tag
ms.assetid: c74b8705-29df-40b1-bff5-237492b0e978
ms.openlocfilehash: 5cb1c22dceae7a45a47fcb8807303d11e1220935
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478005"
---
# <a name="para-c-programming-guide"></a><span data-ttu-id="64803-108">\<para> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="64803-108">\<para> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="64803-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="64803-109">Syntax</span></span>

```xml
<para>content</para>
```

## <a name="parameters"></a><span data-ttu-id="64803-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="64803-110">Parameters</span></span>

- `content`

  <span data-ttu-id="64803-111">Текст абзаца.</span><span class="sxs-lookup"><span data-stu-id="64803-111">The text of the paragraph.</span></span>

## <a name="remarks"></a><span data-ttu-id="64803-112">Примечания</span><span class="sxs-lookup"><span data-stu-id="64803-112">Remarks</span></span>

<span data-ttu-id="64803-113">Тег `<para>` используется внутри другого тега, например [\<summary>](./summary.md), [\<remarks>](./remarks.md) или [\<returns>](./returns.md), и позволяет добавить к тексту структуру.</span><span class="sxs-lookup"><span data-stu-id="64803-113">The `<para>` tag is for use inside a tag, such as [\<summary>](./summary.md), [\<remarks>](./remarks.md), or [\<returns>](./returns.md), and lets you add structure to the text.</span></span>

<span data-ttu-id="64803-114">Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="64803-114">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="64803-115">Пример</span><span class="sxs-lookup"><span data-stu-id="64803-115">Example</span></span>

<span data-ttu-id="64803-116">См. [\<summary>](./summary.md) с примером использования `<para>`.</span><span class="sxs-lookup"><span data-stu-id="64803-116">See [\<summary>](./summary.md) for an example of using `<para>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="64803-117">См. также</span><span class="sxs-lookup"><span data-stu-id="64803-117">See also</span></span>

- [<span data-ttu-id="64803-118">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="64803-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="64803-119">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="64803-119">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
