---
description: 'Дополнительные сведения: Юникод (Visual Basic)'
title: Юникод
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: b0c71d8fdefe3f0d240201e0d57265e5c6081d50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700719"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="722ed-103">Юникод (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="722ed-103">Unicode (Visual Basic)</span></span>

<span data-ttu-id="722ed-104">Указывает, что Visual Basic должны маршалировать все строки в значения Юникода независимо от имени объявляемой внешней процедуры.</span><span class="sxs-lookup"><span data-stu-id="722ed-104">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="722ed-105">При вызове процедуры, определенной вне проекта, Visual Basic компилятор не имеет доступа к информации, которая необходима для правильного вызова процедуры.</span><span class="sxs-lookup"><span data-stu-id="722ed-105">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="722ed-106">Эти сведения включают в себя расположение процедуры, способ ее определения, последовательность вызова и тип возвращаемого значения, а также используемую строковую кодировку.</span><span class="sxs-lookup"><span data-stu-id="722ed-106">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="722ed-107">[Инструкция DECLARE](../statements/declare-statement.md) создает ссылку на внешнюю процедуру и предоставляет эти необходимые сведения.</span><span class="sxs-lookup"><span data-stu-id="722ed-107">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="722ed-108">`charsetmodifier`Часть в `Declare` инструкции предоставляет сведения о кодировке для маршалирования строк во время вызова внешней процедуры.</span><span class="sxs-lookup"><span data-stu-id="722ed-108">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="722ed-109">Он также влияет на то, как Visual Basic ищет имя внешней процедуры во внешнем файле.</span><span class="sxs-lookup"><span data-stu-id="722ed-109">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="722ed-110">`Unicode`Модификатор указывает, что Visual Basic должен маршалировать все строки в значения Юникода и выполнять поиск процедуры, не изменяя ее имя во время поиска.</span><span class="sxs-lookup"><span data-stu-id="722ed-110">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="722ed-111">Если модификатор кодировки не указан, используется значение `Ansi` по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="722ed-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="722ed-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="722ed-112">Remarks</span></span>  

 <span data-ttu-id="722ed-113">`Unicode`Модификатор можно использовать в этом контексте:</span><span class="sxs-lookup"><span data-stu-id="722ed-113">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="722ed-114">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="722ed-114">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="722ed-115">Примечания для разработчиков смарт-устройств</span><span class="sxs-lookup"><span data-stu-id="722ed-115">Smart Device Developer Notes</span></span>  

 <span data-ttu-id="722ed-116">Это ключевое слово не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="722ed-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="722ed-117">См. также</span><span class="sxs-lookup"><span data-stu-id="722ed-117">See also</span></span>

- [<span data-ttu-id="722ed-118">Ansi</span><span class="sxs-lookup"><span data-stu-id="722ed-118">Ansi</span></span>](ansi.md)
- [<span data-ttu-id="722ed-119">Автоматически</span><span class="sxs-lookup"><span data-stu-id="722ed-119">Auto</span></span>](auto.md)
- [<span data-ttu-id="722ed-120">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="722ed-120">Keywords</span></span>](../keywords/index.md)
