---
description: Дополнительные сведения <seealso> (Visual Basic)
title: <seealso>
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 0bf6fa69ad63db016b42e31f717f521f82bbe20e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640320"
---
# <a name="seealso-visual-basic"></a><span data-ttu-id="90c95-103">\<seealso> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90c95-103">\<seealso> (Visual Basic)</span></span>

<span data-ttu-id="90c95-104">Указывает ссылку, которая отображается в разделе "см. также".</span><span class="sxs-lookup"><span data-stu-id="90c95-104">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90c95-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="90c95-105">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="90c95-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="90c95-106">Parameters</span></span>  

 `member`  
 <span data-ttu-id="90c95-107">Ссылка на член или поле, которые доступны для вызова из текущей среды компиляции.</span><span class="sxs-lookup"><span data-stu-id="90c95-107">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="90c95-108">Компилятор проверяет, существует ли элемент кода, и передает `member` в имя элемента в выходных XML-данных.</span><span class="sxs-lookup"><span data-stu-id="90c95-108">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="90c95-109">`member` необходимо заключать в двойные кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="90c95-109">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90c95-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="90c95-110">Remarks</span></span>  

 <span data-ttu-id="90c95-111">Используйте `<seealso>` тег, чтобы указать текст, который должен отображаться в разделе "см. также".</span><span class="sxs-lookup"><span data-stu-id="90c95-111">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="90c95-112">Тег [\<see>](see.md) позволяет задать ссылку из текста.</span><span class="sxs-lookup"><span data-stu-id="90c95-112">Use [\<see>](see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="90c95-113">Чтобы обработать комментарии документации и сохранить их в файл, выполняйте сборку с параметром [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="90c95-113">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90c95-114">Пример</span><span class="sxs-lookup"><span data-stu-id="90c95-114">Example</span></span>  

 <span data-ttu-id="90c95-115">В этом примере используется `<seealso>` тег в `DoesRecordExist` разделе "Примечания" для ссылки на `UpdateRecord` метод.</span><span class="sxs-lookup"><span data-stu-id="90c95-115">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="90c95-116">См. также</span><span class="sxs-lookup"><span data-stu-id="90c95-116">See also</span></span>

- [<span data-ttu-id="90c95-117">XML-теги для комментариев</span><span class="sxs-lookup"><span data-stu-id="90c95-117">XML Comment Tags</span></span>](index.md)
