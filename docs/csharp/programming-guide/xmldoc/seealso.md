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
ms.openlocfilehash: 35420536ef14e91dcf8bf904573ab758d5448a63
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494106"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="abc28-105">\<seealso> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="abc28-105">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="abc28-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="abc28-106">Syntax</span></span>

```csharp
/// <seealso cref="member"/>
// or
/// <seealso href="link">Link Text</seealso>
```

## <a name="parameters"></a><span data-ttu-id="abc28-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="abc28-107">Parameters</span></span>

- `cref="member"`

  <span data-ttu-id="abc28-108">Ссылка на член или поле, которые доступны для вызова из текущей среды компиляции.</span><span class="sxs-lookup"><span data-stu-id="abc28-108">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="abc28-109">Компилятор проверяет, существует ли элемент кода, и передает `member` в имя элемента в выходных XML-данных. `member`</span><span class="sxs-lookup"><span data-stu-id="abc28-109">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="abc28-110">необходимо заключать в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="abc28-110">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="abc28-111">Сведения о создании ссылки cref на универсальный тип см. в статье об [атрибуте cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="abc28-111">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

- `href="link"`

  <span data-ttu-id="abc28-112">Гиперссылка на заданный URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="abc28-112">A clickable link to a given URL.</span></span> <span data-ttu-id="abc28-113">Например, `<seealso href="https://github.com">GitHub</seealso>` формирует гиперссылку с текстом :::no-loc text="GitHub":::, которая ведет на сайт `https://github.com`.</span><span class="sxs-lookup"><span data-stu-id="abc28-113">For example, `<seealso href="https://github.com">GitHub</seealso>` produces a clickable link with text :::no-loc text="GitHub"::: that links to `https://github.com`.</span></span>

## <a name="remarks"></a><span data-ttu-id="abc28-114">Примечания</span><span class="sxs-lookup"><span data-stu-id="abc28-114">Remarks</span></span>

<span data-ttu-id="abc28-115">С помощью тега `<seealso>` можно указать текст, который должен отображаться в разделе "См. также".</span><span class="sxs-lookup"><span data-stu-id="abc28-115">The `<seealso>` tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="abc28-116">Тег [\<see>](./see.md) позволяет задать ссылку из текста.</span><span class="sxs-lookup"><span data-stu-id="abc28-116">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="abc28-117">Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="abc28-117">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="abc28-118">Пример</span><span class="sxs-lookup"><span data-stu-id="abc28-118">Example</span></span>

<span data-ttu-id="abc28-119">См. [\<summary>](./summary.md) с примером использования \<seealso>.</span><span class="sxs-lookup"><span data-stu-id="abc28-119">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="abc28-120">См. также</span><span class="sxs-lookup"><span data-stu-id="abc28-120">See also</span></span>

- [<span data-ttu-id="abc28-121">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="abc28-121">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="abc28-122">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="abc28-122">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
