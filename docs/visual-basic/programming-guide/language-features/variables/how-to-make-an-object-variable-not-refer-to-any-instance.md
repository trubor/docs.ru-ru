---
description: 'Дополнительные сведения о: инструкции: как сделать объектную переменную не ссылаться на какой-либо экземпляр (Visual Basic)'
title: Практическое руководство. Как сделать так, чтобы объектная переменная не указывала ни на какой экземпляр
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 2897720b52e708847fdd139be512e578a7420241
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100481874"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="fe2c2-103">Практическое руководство. Как сделать так, чтобы объектная переменная не указывала ни на какой экземпляр (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe2c2-103">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>

<span data-ttu-id="fe2c2-104">Можно разорвать связь объектной переменной с любым экземпляром объекта, задав для него значение [Nothing](../../../language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="fe2c2-104">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="fe2c2-105">Отмена связывания объектной переменной с любым экземпляром объекта</span><span class="sxs-lookup"><span data-stu-id="fe2c2-105">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="fe2c2-106">Присвойте переменной значение `Nothing` в операторе присваивания.</span><span class="sxs-lookup"><span data-stu-id="fe2c2-106">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="fe2c2-107">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="fe2c2-107">Robust Programming</span></span>  

 <span data-ttu-id="fe2c2-108">Если код пытается получить доступ к члену объектной переменной, для которой задано значение `Nothing` , <xref:System.NullReferenceException> возникает.</span><span class="sxs-lookup"><span data-stu-id="fe2c2-108">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="fe2c2-109">Если переменная объекта задана как `Nothing` часто или если переменная не инициализирована, рекомендуется заключить доступ к членам в `Try...Catch...Finally` блок.</span><span class="sxs-lookup"><span data-stu-id="fe2c2-109">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fe2c2-110">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fe2c2-110">.NET Framework Security</span></span>  

 <span data-ttu-id="fe2c2-111">При использовании объектной переменной для объектов, содержащих конфиденциальные или конфиденциальные данные, можно присвоить переменной значение, `Nothing` Если вы не работаете с одним из этих объектов.</span><span class="sxs-lookup"><span data-stu-id="fe2c2-111">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="fe2c2-112">Это снижает вероятность того, что вредоносный код получает доступ к данным.</span><span class="sxs-lookup"><span data-stu-id="fe2c2-112">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe2c2-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="fe2c2-113">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="fe2c2-114">Объектные переменные</span><span class="sxs-lookup"><span data-stu-id="fe2c2-114">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="fe2c2-115">Присваивание объектных переменных</span><span class="sxs-lookup"><span data-stu-id="fe2c2-115">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="fe2c2-116">Nothing</span><span class="sxs-lookup"><span data-stu-id="fe2c2-116">Nothing</span></span>](../../../language-reference/nothing.md)
- [<span data-ttu-id="fe2c2-117">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="fe2c2-117">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
