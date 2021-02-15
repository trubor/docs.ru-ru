---
description: 'Дополнительные сведения: <paramref> (Visual Basic)'
title: <paramref>
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 0ce748213e26c258b290828c42454b0e7fd316f1
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456839"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="aaeeb-102">\<paramref> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aaeeb-102">\<paramref> (Visual Basic)</span></span>

<span data-ttu-id="aaeeb-103">Форматирует слово как параметр.</span><span class="sxs-lookup"><span data-stu-id="aaeeb-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaeeb-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aaeeb-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaeeb-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="aaeeb-105">Parameters</span></span>  

 `name`  
 <span data-ttu-id="aaeeb-106">Имя параметра, на который указывается ссылка.</span><span class="sxs-lookup"><span data-stu-id="aaeeb-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="aaeeb-107">Имя заключается в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="aaeeb-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaeeb-108">Примечания</span><span class="sxs-lookup"><span data-stu-id="aaeeb-108">Remarks</span></span>  

 <span data-ttu-id="aaeeb-109">`<paramref>`Тег дает возможность указать, что слово является параметром.</span><span class="sxs-lookup"><span data-stu-id="aaeeb-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="aaeeb-110">XML-файл может быть обработан для того, чтобы отформатировать этот параметр определенным образом.</span><span class="sxs-lookup"><span data-stu-id="aaeeb-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="aaeeb-111">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="aaeeb-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaeeb-112">Пример</span><span class="sxs-lookup"><span data-stu-id="aaeeb-112">Example</span></span>  

 <span data-ttu-id="aaeeb-113">В этом примере `<paramref>` тег используется для ссылки на `id` параметр.</span><span class="sxs-lookup"><span data-stu-id="aaeeb-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="aaeeb-114">См. также</span><span class="sxs-lookup"><span data-stu-id="aaeeb-114">See also</span></span>

- [<span data-ttu-id="aaeeb-115">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="aaeeb-115">XML Comment Tags</span></span>](index.md)
