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
ms.openlocfilehash: 154feca5e7e4f4d3f5313c4ae05cd991e69e298f
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477777"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="2562f-104">\<see> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="2562f-104">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="2562f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2562f-105">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="2562f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2562f-106">Parameters</span></span>

- <span data-ttu-id="2562f-107">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="2562f-107">cref = "`member`"</span></span>

  <span data-ttu-id="2562f-108">Ссылка на член или поле, которые доступны для вызова из текущей среды компиляции.</span><span class="sxs-lookup"><span data-stu-id="2562f-108">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="2562f-109">Компилятор проверяет, существует ли элемент кода, и передает `member` в имя элемента в выходных XML-данных.</span><span class="sxs-lookup"><span data-stu-id="2562f-109">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="2562f-110">*member* необходимо заключать в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="2562f-110">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="2562f-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="2562f-111">Remarks</span></span>

<span data-ttu-id="2562f-112">Тег `<see>` позволяет задать ссылку из текста.</span><span class="sxs-lookup"><span data-stu-id="2562f-112">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="2562f-113">С помощью тега [\<seealso>](./seealso.md) можно указать, что текст должен быть размещен в разделе "См. также".</span><span class="sxs-lookup"><span data-stu-id="2562f-113">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="2562f-114">Используйте [cref Attribute](./cref-attribute.md) для создания внутренних гиперссылок на страницы документации для элементов кода.</span><span class="sxs-lookup"><span data-stu-id="2562f-114">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="2562f-115">Кроме того, ``href`` является допустимым атрибутом, который будет функционировать как гиперссылка.</span><span class="sxs-lookup"><span data-stu-id="2562f-115">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="2562f-116">Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="2562f-116">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

<span data-ttu-id="2562f-117">В следующем примере показан тег `<see>` в разделе сводки.</span><span class="sxs-lookup"><span data-stu-id="2562f-117">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="2562f-118">См. также</span><span class="sxs-lookup"><span data-stu-id="2562f-118">See also</span></span>

- [<span data-ttu-id="2562f-119">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="2562f-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="2562f-120">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="2562f-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
