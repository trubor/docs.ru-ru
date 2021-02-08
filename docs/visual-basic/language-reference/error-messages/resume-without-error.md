---
description: 'Дополнительные сведения: возобновление без ошибок'
title: Выполнение оператора Resume без ошибки
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: a2284484be65ae975c6e09499ec19e3cfd8d4a04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792015"
---
# <a name="resume-without-error"></a><span data-ttu-id="d11df-103">Выполнение оператора Resume без ошибки</span><span class="sxs-lookup"><span data-stu-id="d11df-103">Resume without error</span></span>

<span data-ttu-id="d11df-104">`Resume`Оператор обнаружен за пределами кода обработки ошибок, или код был переведен в обработчик ошибок, несмотря на отсутствие ошибки.</span><span class="sxs-lookup"><span data-stu-id="d11df-104">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d11df-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="d11df-105">To correct this error</span></span>  
  
1. <span data-ttu-id="d11df-106">Переместите `Resume` оператор в обработчик ошибок или удалите его.</span><span class="sxs-lookup"><span data-stu-id="d11df-106">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2. <span data-ttu-id="d11df-107">Переход к меткам не может осуществляться между процедурами, поэтому выполните поиск по этой процедуре для метки, идентифицирующей обработчик ошибок.</span><span class="sxs-lookup"><span data-stu-id="d11df-107">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="d11df-108">Если обнаружена повторяющаяся метка, указанная в качестве целевого объекта `GoTo` инструкции, которая не является `On Error GoTo` инструкцией, измените метку строки, чтобы согласовать ее с предполагаемой целью.</span><span class="sxs-lookup"><span data-stu-id="d11df-108">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d11df-109">См. также</span><span class="sxs-lookup"><span data-stu-id="d11df-109">See also</span></span>

- [<span data-ttu-id="d11df-110">Оператор Resume</span><span class="sxs-lookup"><span data-stu-id="d11df-110">Resume Statement</span></span>](../statements/resume-statement.md)
- [<span data-ttu-id="d11df-111">Оператор On Error</span><span class="sxs-lookup"><span data-stu-id="d11df-111">On Error Statement</span></span>](../statements/on-error-statement.md)
