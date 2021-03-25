---
title: <param> Руководство по программированию на C#.
description: Сведения о теге <param> в XML. Этот тег используется в комментариях к объявлению метода для описания одного из параметров такого метода.
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 1385365b2cdf18563686fdf4a5a1b17b89feafcd
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477996"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="1e0b5-105">\<param> (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="1e0b5-105">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="1e0b5-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1e0b5-106">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="1e0b5-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="1e0b5-107">Parameters</span></span>

- `name`

  <span data-ttu-id="1e0b5-108">Имя параметра метода.</span><span class="sxs-lookup"><span data-stu-id="1e0b5-108">The name of a method parameter.</span></span> <span data-ttu-id="1e0b5-109">Имя заключается в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="1e0b5-109">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="1e0b5-110">Описание параметра.</span><span class="sxs-lookup"><span data-stu-id="1e0b5-110">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="1e0b5-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="1e0b5-111">Remarks</span></span>

<span data-ttu-id="1e0b5-112">Тег `<param>` следует использовать в комментариях к объявлению метода для описания одного из параметров такого метода.</span><span class="sxs-lookup"><span data-stu-id="1e0b5-112">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="1e0b5-113">Чтобы задокументировать несколько параметров, используйте несколько тегов `<param>`.</span><span class="sxs-lookup"><span data-stu-id="1e0b5-113">To document multiple parameters, use multiple `<param>` tags.</span></span>

<span data-ttu-id="1e0b5-114">Текст тега `<param>` отображается в IntelliSense, обозревателе объектов и веб-отчете по комментариям к коду.</span><span class="sxs-lookup"><span data-stu-id="1e0b5-114">The text for the `<param>` tag is displayed in IntelliSense, the Object Browser, and the Code Comment Web Report.</span></span>

<span data-ttu-id="1e0b5-115">Чтобы обработать комментарии в документации и сохранить их в файл, выполните компиляцию с использованием параметра [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile).</span><span class="sxs-lookup"><span data-stu-id="1e0b5-115">Compile with [**DocumentationFile**](../../language-reference/compiler-options/output.md#documentationfile) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="1e0b5-116">Пример</span><span class="sxs-lookup"><span data-stu-id="1e0b5-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="1e0b5-117">См. также</span><span class="sxs-lookup"><span data-stu-id="1e0b5-117">See also</span></span>

- [<span data-ttu-id="1e0b5-118">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="1e0b5-118">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="1e0b5-119">Рекомендуемые теги для комментариев документации</span><span class="sxs-lookup"><span data-stu-id="1e0b5-119">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
