---
description: 'Дополнительные сведения: <see> (Visual Basic)'
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 46dd67710f83d6c4549ddfeb6b7bbc1503b7aa1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640346"
---
# <a name="see-visual-basic"></a><span data-ttu-id="eccf9-102">\<see> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eccf9-102">\<see> (Visual Basic)</span></span>

<span data-ttu-id="eccf9-103">Указывает ссылку на другой элемент.</span><span class="sxs-lookup"><span data-stu-id="eccf9-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eccf9-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="eccf9-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="eccf9-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="eccf9-105">Parameters</span></span>  

 `member`  
 <span data-ttu-id="eccf9-106">Ссылка на член или поле, которые доступны для вызова из текущей среды компиляции.</span><span class="sxs-lookup"><span data-stu-id="eccf9-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="eccf9-107">Компилятор проверяет, существует ли элемент кода, и передает `member` в имя элемента в выходных XML-данных.</span><span class="sxs-lookup"><span data-stu-id="eccf9-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="eccf9-108">`member` необходимо заключать в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="eccf9-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eccf9-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="eccf9-109">Remarks</span></span>  

 <span data-ttu-id="eccf9-110">Используйте `<see>` тег, чтобы указать ссылку в тексте.</span><span class="sxs-lookup"><span data-stu-id="eccf9-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="eccf9-111">Используется [\<seealso>](seealso.md) для обозначения текста, который может потребоваться отобразить в разделе "см. также".</span><span class="sxs-lookup"><span data-stu-id="eccf9-111">Use [\<seealso>](seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="eccf9-112">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="eccf9-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eccf9-113">Пример</span><span class="sxs-lookup"><span data-stu-id="eccf9-113">Example</span></span>  

 <span data-ttu-id="eccf9-114">В этом примере используется `<see>` тег в `UpdateRecord` разделе "Примечания" для ссылки на `DoesRecordExist` метод.</span><span class="sxs-lookup"><span data-stu-id="eccf9-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="eccf9-115">См. также</span><span class="sxs-lookup"><span data-stu-id="eccf9-115">See also</span></span>

- [<span data-ttu-id="eccf9-116">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="eccf9-116">XML Comment Tags</span></span>](index.md)
