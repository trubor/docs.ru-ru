---
title: Руководство по программированию на C#. <exception>
description: Сведения о теге <exception> в XML. Этот тег позволяет указать, какие исключения могут быть созданы. Он может применяться к методам, свойствам, событиям и индексаторам.
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 37d119e3cde115104d149d8f35b8937efddd70d4
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103479110"
---
# <a name="exception-c-programming-guide"></a><span data-ttu-id="23ae0-104">\<exception> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="23ae0-104">\<exception> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="23ae0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="23ae0-105">Syntax</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a><span data-ttu-id="23ae0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="23ae0-106">Parameters</span></span>

- <span data-ttu-id="23ae0-107">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="23ae0-107">cref = " `member`"</span></span>

  <span data-ttu-id="23ae0-108">Ссылка на исключение, которое доступно из текущей среды компиляции.</span><span class="sxs-lookup"><span data-stu-id="23ae0-108">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="23ae0-109">Компилятор проверяет, существует ли исключение, и приводит `member` к каноническому имени элемента в выходных XML-данных.</span><span class="sxs-lookup"><span data-stu-id="23ae0-109">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="23ae0-110">`member` необходимо заключать в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="23ae0-110">`member` must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="23ae0-111">См. подробнее о том, как форматировать `member`, чтобы создать ссылку на универсальный тип, в руководстве по [обработке XML-файла](processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="23ae0-111">For more information on how to format `member` to reference a generic type, see [Processing the XML File](processing-the-xml-file.md).</span></span>

- `description`

  <span data-ttu-id="23ae0-112">Описание исключения.</span><span class="sxs-lookup"><span data-stu-id="23ae0-112">A description of the exception.</span></span>

## <a name="remarks"></a><span data-ttu-id="23ae0-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="23ae0-113">Remarks</span></span>

<span data-ttu-id="23ae0-114">Тег `<exception>` служит для указания возможных исключений.</span><span class="sxs-lookup"><span data-stu-id="23ae0-114">The `<exception>` tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="23ae0-115">Этот тег может применяться к определениям методов, свойств, событий и индексаторов.</span><span class="sxs-lookup"><span data-stu-id="23ae0-115">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>

<span data-ttu-id="23ae0-116">Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="23ae0-116">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

<span data-ttu-id="23ae0-117">Дополнительные сведения об обработке исключений см. в разделе [Исключения и обработка исключений](../exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="23ae0-117">For more information about exception handling, see [Exceptions and Exception Handling](../exceptions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="23ae0-118">Пример</span><span class="sxs-lookup"><span data-stu-id="23ae0-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a><span data-ttu-id="23ae0-119">См. также</span><span class="sxs-lookup"><span data-stu-id="23ae0-119">See also</span></span>

- [<span data-ttu-id="23ae0-120">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="23ae0-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="23ae0-121">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="23ae0-121">Recommended tags for documentation comments</span></span>](recommended-tags-for-documentation-comments.md)
