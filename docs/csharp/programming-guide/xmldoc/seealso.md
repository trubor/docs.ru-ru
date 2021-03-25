---
title: <seealso> Руководство по программированию на C#.
description: Сведения об использовании тега <seealso> в XML. Этот тег позволяет указать текст, который должен отображаться в разделе "См. также".
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: c5baefbfca3a94095a90eb43c2bf13eb924c8cdc
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477754"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="4323f-105">\<seealso> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="4323f-105">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="4323f-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4323f-106">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="4323f-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="4323f-107">Parameters</span></span>

- <span data-ttu-id="4323f-108">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="4323f-108">cref = " `member`"</span></span>

  <span data-ttu-id="4323f-109">Ссылка на член или поле, которые доступны для вызова из текущей среды компиляции.</span><span class="sxs-lookup"><span data-stu-id="4323f-109">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="4323f-110">Компилятор проверяет, существует ли элемент кода, и передает `member` в имя элемента в выходных XML-данных. `member`</span><span class="sxs-lookup"><span data-stu-id="4323f-110">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="4323f-111">необходимо заключать в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="4323f-111">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="4323f-112">Сведения о создании ссылки cref на универсальный тип см. в статье об [атрибуте cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="4323f-112">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="4323f-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="4323f-113">Remarks</span></span>

<span data-ttu-id="4323f-114">С помощью тега `<seealso>` можно указать текст, который должен отображаться в разделе "См. также".</span><span class="sxs-lookup"><span data-stu-id="4323f-114">The `<seealso>` tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="4323f-115">Тег [\<see>](./see.md) позволяет задать ссылку из текста.</span><span class="sxs-lookup"><span data-stu-id="4323f-115">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="4323f-116">Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="4323f-116">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="4323f-117">Пример</span><span class="sxs-lookup"><span data-stu-id="4323f-117">Example</span></span>

<span data-ttu-id="4323f-118">См. [\<summary>](./summary.md) с примером использования \<seealso>.</span><span class="sxs-lookup"><span data-stu-id="4323f-118">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="4323f-119">См. также</span><span class="sxs-lookup"><span data-stu-id="4323f-119">See also</span></span>

- [<span data-ttu-id="4323f-120">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="4323f-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="4323f-121">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="4323f-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
