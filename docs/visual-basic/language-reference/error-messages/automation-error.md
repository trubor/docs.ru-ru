---
description: 'Дополнительные сведения: ошибка службы автоматизации'
title: Ошибка автоматизации
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: bf3e61bb9b8fec9a831d211b70abdca322c1fe06
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106609"
---
# <a name="automation-error"></a><span data-ttu-id="9f27e-103">Ошибка автоматизации</span><span class="sxs-lookup"><span data-stu-id="9f27e-103">Automation error</span></span>

<span data-ttu-id="9f27e-104">При выполнении метода либо при получении либо установке значения свойства переменной объекта возникла ошибка.</span><span class="sxs-lookup"><span data-stu-id="9f27e-104">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="9f27e-105">О ней сообщило приложение, создавшее этот объект.</span><span class="sxs-lookup"><span data-stu-id="9f27e-105">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9f27e-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="9f27e-106">To correct this error</span></span>  
  
1. <span data-ttu-id="9f27e-107">Проверьте свойства объекта `Err`, чтобы определить причину и характер ошибки.</span><span class="sxs-lookup"><span data-stu-id="9f27e-107">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="9f27e-108">Используйте инструкцию `On Error Resume Next` непосредственно перед инструкцией доступа, а затем выполните проверку на наличие ошибок сразу после инструкции доступа.</span><span class="sxs-lookup"><span data-stu-id="9f27e-108">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f27e-109">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9f27e-109">See also</span></span>

- [<span data-ttu-id="9f27e-110">Типы ошибок</span><span class="sxs-lookup"><span data-stu-id="9f27e-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="9f27e-111">Параметры обратной связи Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9f27e-111">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
