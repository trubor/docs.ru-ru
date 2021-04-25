---
title: Руководство по программированию на C#. <see>
description: Сведения о теге <see> в XML. Этот тег позволяет указать ссылку в тексте, например с помощью атрибута cref.
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 351dd2e4c7dbc76efa2edbed708fb342c553ce70
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494861"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="6dc12-104">\<see> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="6dc12-104">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="6dc12-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6dc12-105">Syntax</span></span>

```csharp
/// <see cref="member"/>
// or
/// <see href="link">Link Text</see>
// or
/// <see langword="keyword"/>
```

## <a name="parameters"></a><span data-ttu-id="6dc12-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6dc12-106">Parameters</span></span>

- `cref="member"`

  <span data-ttu-id="6dc12-107">Ссылка на член или поле, которые доступны для вызова из текущей среды компиляции.</span><span class="sxs-lookup"><span data-stu-id="6dc12-107">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="6dc12-108">Компилятор проверяет, существует ли элемент кода, и передает `member` в имя элемента в выходных XML-данных.</span><span class="sxs-lookup"><span data-stu-id="6dc12-108">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="6dc12-109">*member* необходимо заключать в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="6dc12-109">Place *member* within double quotation marks (" ").</span></span>

- `href="link"`

  <span data-ttu-id="6dc12-110">Гиперссылка на заданный URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="6dc12-110">A clickable link to a given URL.</span></span> <span data-ttu-id="6dc12-111">Например, `<see href="https://github.com">GitHub</see>` формирует гиперссылку с текстом :::no-loc text="GitHub":::, которая ведет на сайт `https://github.com`.</span><span class="sxs-lookup"><span data-stu-id="6dc12-111">For example, `<see href="https://github.com">GitHub</see>` produces a clickable link with text :::no-loc text="GitHub"::: that links to `https://github.com`.</span></span>

- `langword="keyword"`

  <span data-ttu-id="6dc12-112">Ключевое слово языка, например `true`.</span><span class="sxs-lookup"><span data-stu-id="6dc12-112">A language keyword, such as `true`.</span></span>

## <a name="remarks"></a><span data-ttu-id="6dc12-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="6dc12-113">Remarks</span></span>

<span data-ttu-id="6dc12-114">Тег `<see>` позволяет задать ссылку из текста.</span><span class="sxs-lookup"><span data-stu-id="6dc12-114">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="6dc12-115">С помощью тега [\<seealso>](./seealso.md) можно указать, что текст должен быть размещен в разделе "См. также".</span><span class="sxs-lookup"><span data-stu-id="6dc12-115">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="6dc12-116">Используйте [cref Attribute](./cref-attribute.md) для создания внутренних гиперссылок на страницы документации для элементов кода.</span><span class="sxs-lookup"><span data-stu-id="6dc12-116">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="6dc12-117">Кроме того, ``href`` является допустимым атрибутом, который будет функционировать как гиперссылка.</span><span class="sxs-lookup"><span data-stu-id="6dc12-117">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="6dc12-118">Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="6dc12-118">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

<span data-ttu-id="6dc12-119">В следующем примере показан тег `<see>` в разделе сводки.</span><span class="sxs-lookup"><span data-stu-id="6dc12-119">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="6dc12-120">См. также</span><span class="sxs-lookup"><span data-stu-id="6dc12-120">See also</span></span>

- [<span data-ttu-id="6dc12-121">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="6dc12-121">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="6dc12-122">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="6dc12-122">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
