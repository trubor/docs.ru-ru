---
description: 'Дополнительные сведения о: ANSI (Visual Basic)'
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: c93472cbf6a8203f05353e0394b52c44686c0070
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701200"
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="753cf-103">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="753cf-103">Ansi (Visual Basic)</span></span>

<span data-ttu-id="753cf-104">Указывает, что Visual Basic должны маршалировать все строки в значения Американский национальный институт стандартов (ANSI) (ANSI) независимо от имени объявляемой внешней процедуры.</span><span class="sxs-lookup"><span data-stu-id="753cf-104">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="753cf-105">При вызове процедуры, определенной вне проекта, Visual Basic компилятор не имеет доступа к информации, которая необходима для правильного вызова процедуры.</span><span class="sxs-lookup"><span data-stu-id="753cf-105">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="753cf-106">Эти сведения включают в себя расположение процедуры, способ ее определения, последовательность вызова и тип возвращаемого значения, а также используемую строковую кодировку.</span><span class="sxs-lookup"><span data-stu-id="753cf-106">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="753cf-107">[Инструкция DECLARE](../statements/declare-statement.md) создает ссылку на внешнюю процедуру и предоставляет эти необходимые сведения.</span><span class="sxs-lookup"><span data-stu-id="753cf-107">The [Declare Statement](../statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="753cf-108">`charsetmodifier`Часть в `Declare` инструкции предоставляет сведения о кодировке для упаковки строк во время вызова внешней процедуры.</span><span class="sxs-lookup"><span data-stu-id="753cf-108">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="753cf-109">Он также влияет на то, как Visual Basic ищет имя внешней процедуры во внешнем файле.</span><span class="sxs-lookup"><span data-stu-id="753cf-109">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="753cf-110">`Ansi`Модификатор указывает, что Visual Basic должен маршалировать все строки в значения ANSI и выполнять поиск процедуры, не изменяя ее имя во время поиска.</span><span class="sxs-lookup"><span data-stu-id="753cf-110">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="753cf-111">Если модификатор кодировки не указан, используется значение `Ansi` по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="753cf-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="753cf-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="753cf-112">Remarks</span></span>  

 <span data-ttu-id="753cf-113">`Ansi`Модификатор можно использовать в этом контексте:</span><span class="sxs-lookup"><span data-stu-id="753cf-113">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="753cf-114">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="753cf-114">Declare Statement</span></span>](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="753cf-115">Примечания для разработчиков смарт-устройств</span><span class="sxs-lookup"><span data-stu-id="753cf-115">Smart Device Developer Notes</span></span>  

 <span data-ttu-id="753cf-116">Это ключевое слово не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="753cf-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753cf-117">См. также</span><span class="sxs-lookup"><span data-stu-id="753cf-117">See also</span></span>

- [<span data-ttu-id="753cf-118">Автоматически</span><span class="sxs-lookup"><span data-stu-id="753cf-118">Auto</span></span>](auto.md)
- [<span data-ttu-id="753cf-119">Юникод</span><span class="sxs-lookup"><span data-stu-id="753cf-119">Unicode</span></span>](unicode.md)
- [<span data-ttu-id="753cf-120">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="753cf-120">Keywords</span></span>](../keywords/index.md)
