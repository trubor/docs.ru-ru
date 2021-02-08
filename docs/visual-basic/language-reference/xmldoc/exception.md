---
description: 'Дополнительные сведения: <exception> (Visual Basic)'
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 14b7f78dd2521f7d5b3d62f635baa5b50969afa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787478"
---
# <a name="exception-visual-basic"></a><span data-ttu-id="87e5f-102">\<exception> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87e5f-102">\<exception> (Visual Basic)</span></span>

<span data-ttu-id="87e5f-103">Указывает, какие исключения могут быть созданы.</span><span class="sxs-lookup"><span data-stu-id="87e5f-103">Specifies which exceptions can be thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e5f-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="87e5f-104">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a><span data-ttu-id="87e5f-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="87e5f-105">Parameters</span></span>  

 `member`  
 <span data-ttu-id="87e5f-106">Ссылка на исключение, которое доступно из текущей среды компиляции.</span><span class="sxs-lookup"><span data-stu-id="87e5f-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="87e5f-107">Компилятор проверяет, существует ли исключение, и приводит `member` к каноническому имени элемента в выходных XML-данных.</span><span class="sxs-lookup"><span data-stu-id="87e5f-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="87e5f-108">`member` необходимо заключать в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="87e5f-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="87e5f-109">Описание.</span><span class="sxs-lookup"><span data-stu-id="87e5f-109">A description.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87e5f-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="87e5f-110">Remarks</span></span>  

 <span data-ttu-id="87e5f-111">Используйте `<exception>` тег, чтобы указать, какие исключения могут быть созданы.</span><span class="sxs-lookup"><span data-stu-id="87e5f-111">Use the `<exception>` tag to specify which exceptions can be thrown.</span></span> <span data-ttu-id="87e5f-112">Этот тег применяется к определению метода.</span><span class="sxs-lookup"><span data-stu-id="87e5f-112">This tag is applied to a method definition.</span></span>  
  
 <span data-ttu-id="87e5f-113">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="87e5f-113">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87e5f-114">Пример</span><span class="sxs-lookup"><span data-stu-id="87e5f-114">Example</span></span>  

 <span data-ttu-id="87e5f-115">В этом примере `<exception>` тег используется для описания исключения, которое `IntDivide` может выдаваться функцией.</span><span class="sxs-lookup"><span data-stu-id="87e5f-115">This example uses the `<exception>` tag to describe an exception that the `IntDivide` function can throw.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="87e5f-116">См. также</span><span class="sxs-lookup"><span data-stu-id="87e5f-116">See also</span></span>

- [<span data-ttu-id="87e5f-117">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="87e5f-117">XML Comment Tags</span></span>](index.md)
