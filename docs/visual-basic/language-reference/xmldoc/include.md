---
description: Дополнительные сведения <include> (Visual Basic)
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 8207b74ed74bd529f2da865777e287320b23d293
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787465"
---
# <a name="include-visual-basic"></a><span data-ttu-id="ee6b4-103">\<include> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee6b4-103">\<include> (Visual Basic)</span></span>

<span data-ttu-id="ee6b4-104">Ссылается на другой файл, описывающий типы и члены в исходном коде.</span><span class="sxs-lookup"><span data-stu-id="ee6b4-104">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee6b4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ee6b4-105">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee6b4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ee6b4-106">Parameters</span></span>  

 `filename`  
 <span data-ttu-id="ee6b4-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="ee6b4-107">Required.</span></span> <span data-ttu-id="ee6b4-108">Имя файла, содержащего документацию.</span><span class="sxs-lookup"><span data-stu-id="ee6b4-108">The name of the file containing the documentation.</span></span> <span data-ttu-id="ee6b4-109">Имя файла может быть дополнено с указанием пути.</span><span class="sxs-lookup"><span data-stu-id="ee6b4-109">The file name can be qualified with a path.</span></span> <span data-ttu-id="ee6b4-110">Заключите `filename` в двойные кавычки ("").</span><span class="sxs-lookup"><span data-stu-id="ee6b4-110">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="ee6b4-111">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="ee6b4-111">Required.</span></span> <span data-ttu-id="ee6b4-112">Путь тегов в `filename`, который ведет к тегу `name`.</span><span class="sxs-lookup"><span data-stu-id="ee6b4-112">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="ee6b4-113">Заключите путь в двойные кавычки ("").</span><span class="sxs-lookup"><span data-stu-id="ee6b4-113">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="ee6b4-114">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="ee6b4-114">Required.</span></span> <span data-ttu-id="ee6b4-115">Описатель имени в теге, который предшествует комментариям.</span><span class="sxs-lookup"><span data-stu-id="ee6b4-115">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="ee6b4-116">`Name` будет иметь `id` .</span><span class="sxs-lookup"><span data-stu-id="ee6b4-116">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="ee6b4-117">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="ee6b4-117">Required.</span></span> <span data-ttu-id="ee6b4-118">Идентификатор тега, который предшествует комментариям.</span><span class="sxs-lookup"><span data-stu-id="ee6b4-118">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="ee6b4-119">Заключите идентификатор в одинарные кавычки (' ').</span><span class="sxs-lookup"><span data-stu-id="ee6b4-119">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee6b4-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="ee6b4-120">Remarks</span></span>  

 <span data-ttu-id="ee6b4-121">Используйте `<include>` тег для ссылки на комментарии в другом файле, описывающем типы и члены в исходном коде.</span><span class="sxs-lookup"><span data-stu-id="ee6b4-121">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="ee6b4-122">Этот способ является альтернативой размещению комментариев документации непосредственно в файле исходного кода.</span><span class="sxs-lookup"><span data-stu-id="ee6b4-122">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="ee6b4-123">`<include>`Тег использует рекомендацию W3C по языку XML Path (XPath) версии 1,0.</span><span class="sxs-lookup"><span data-stu-id="ee6b4-123">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="ee6b4-124">Дополнительные сведения о способах настройки `<include>` использования см. в разделе <https://www.w3.org/TR/xpath> .</span><span class="sxs-lookup"><span data-stu-id="ee6b4-124">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee6b4-125">Пример</span><span class="sxs-lookup"><span data-stu-id="ee6b4-125">Example</span></span>  

 <span data-ttu-id="ee6b4-126">В этом примере `<include>` тег используется для импорта комментариев документации элемента из файла с именем `commentFile.xml` .</span><span class="sxs-lookup"><span data-stu-id="ee6b4-126">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 <span data-ttu-id="ee6b4-127">Формат `commentFile.xml` имеет следующий вид.</span><span class="sxs-lookup"><span data-stu-id="ee6b4-127">The format of the `commentFile.xml` is as follows.</span></span>  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee6b4-128">См. также</span><span class="sxs-lookup"><span data-stu-id="ee6b4-128">See also</span></span>

- [<span data-ttu-id="ee6b4-129">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="ee6b4-129">XML Comment Tags</span></span>](index.md)
