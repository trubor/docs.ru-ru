---
description: Дополнительные сведения см. в разделе как ссылаться на текущий экземпляр объекта (Visual Basic).
title: Практическое руководство. Ссылка на текущий экземпляр объекта
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 84a52c9d0a8b1f588630b31d022490f37595850d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481744"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="4a6a2-103">Практическое руководство. Ссылка на текущий экземпляр объекта (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a6a2-103">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>

<span data-ttu-id="4a6a2-104">*Текущим экземпляром* объекта является экземпляр, в котором в данный момент выполняется код.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-104">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="4a6a2-105">Используйте `Me` ключевое слово для ссылки на текущий экземпляр.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-105">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="4a6a2-106">Ссылка на текущий экземпляр</span><span class="sxs-lookup"><span data-stu-id="4a6a2-106">To refer to the current instance</span></span>  
  
- <span data-ttu-id="4a6a2-107">Используйте `Me` ключевое слово, в котором обычно используется имя объектной переменной.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-107">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="4a6a2-108">Несмотря `Me` на то, что ведет себя как объектная переменная, вы не можете объявить ее или присвоить ей что-либо.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-108">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="4a6a2-109">`Me` всегда ссылается на текущий экземпляр.</span><span class="sxs-lookup"><span data-stu-id="4a6a2-109">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a6a2-110">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4a6a2-110">See also</span></span>

- [<span data-ttu-id="4a6a2-111">Объектные переменные</span><span class="sxs-lookup"><span data-stu-id="4a6a2-111">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="4a6a2-112">Присваивание объектных переменных</span><span class="sxs-lookup"><span data-stu-id="4a6a2-112">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="4a6a2-113">Me, My, MyBase и MyClass</span><span class="sxs-lookup"><span data-stu-id="4a6a2-113">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
