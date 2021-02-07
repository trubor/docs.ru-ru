---
description: Дополнительные сведения <param> (Visual Basic)
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 94fe5e11d5846f7fa00eb73c1c4363990ae23b2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700296"
---
# <a name="param-visual-basic"></a><span data-ttu-id="0aa58-103">\<param> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0aa58-103">\<param> (Visual Basic)</span></span>

<span data-ttu-id="0aa58-104">Определяет имя и описание параметра.</span><span class="sxs-lookup"><span data-stu-id="0aa58-104">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aa58-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0aa58-105">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="0aa58-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0aa58-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="0aa58-107">Имя параметра метода.</span><span class="sxs-lookup"><span data-stu-id="0aa58-107">The name of a method parameter.</span></span> <span data-ttu-id="0aa58-108">Имя заключается в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="0aa58-108">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="0aa58-109">Описание параметра.</span><span class="sxs-lookup"><span data-stu-id="0aa58-109">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0aa58-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="0aa58-110">Remarks</span></span>  

 <span data-ttu-id="0aa58-111">Тег `<param>` следует использовать в комментариях к объявлению метода для описания одного из параметров такого метода.</span><span class="sxs-lookup"><span data-stu-id="0aa58-111">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="0aa58-112">Текст для `<param>` тега будет отображаться в следующих местах:</span><span class="sxs-lookup"><span data-stu-id="0aa58-112">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="0aa58-113">Сведения о параметрах IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="0aa58-113">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="0aa58-114">Дополнительные сведения см. в разделе [Using IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="0aa58-114">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="0aa58-115">Обозреватель объектов.</span><span class="sxs-lookup"><span data-stu-id="0aa58-115">Object Browser.</span></span> <span data-ttu-id="0aa58-116">Дополнительные сведения см. [в разделе Просмотр структуры кода](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="0aa58-116">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="0aa58-117">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="0aa58-117">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0aa58-118">Пример</span><span class="sxs-lookup"><span data-stu-id="0aa58-118">Example</span></span>  

 <span data-ttu-id="0aa58-119">В этом примере `<param>` для описания параметра используется тег `id` .</span><span class="sxs-lookup"><span data-stu-id="0aa58-119">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0aa58-120">См. также</span><span class="sxs-lookup"><span data-stu-id="0aa58-120">See also</span></span>

- [<span data-ttu-id="0aa58-121">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="0aa58-121">XML Comment Tags</span></span>](index.md)
