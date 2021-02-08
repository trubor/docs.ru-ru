---
description: 'Дополнительные сведения: ошибка службы автоматизации'
title: Ошибка автоматизации
ms.date: 07/20/2015
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
ms.openlocfilehash: e4d283b16b4c54e2488fedfc58d3c881cf6b0218
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797124"
---
# <a name="automation-error"></a><span data-ttu-id="cf5f6-103">Ошибка автоматизации</span><span class="sxs-lookup"><span data-stu-id="cf5f6-103">Automation error</span></span>

<span data-ttu-id="cf5f6-104">При выполнении метода либо при получении либо установке значения свойства переменной объекта возникла ошибка.</span><span class="sxs-lookup"><span data-stu-id="cf5f6-104">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="cf5f6-105">О ней сообщило приложение, создавшее этот объект.</span><span class="sxs-lookup"><span data-stu-id="cf5f6-105">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cf5f6-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="cf5f6-106">To correct this error</span></span>  
  
1. <span data-ttu-id="cf5f6-107">Проверьте свойства объекта `Err`, чтобы определить причину и характер ошибки.</span><span class="sxs-lookup"><span data-stu-id="cf5f6-107">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2. <span data-ttu-id="cf5f6-108">Используйте инструкцию `On Error Resume Next` непосредственно перед инструкцией доступа, а затем выполните проверку на наличие ошибок сразу после инструкции доступа.</span><span class="sxs-lookup"><span data-stu-id="cf5f6-108">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf5f6-109">См. также</span><span class="sxs-lookup"><span data-stu-id="cf5f6-109">See also</span></span>

- [<span data-ttu-id="cf5f6-110">Типы ошибок</span><span class="sxs-lookup"><span data-stu-id="cf5f6-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="cf5f6-111">Обращайтесь к нам</span><span class="sxs-lookup"><span data-stu-id="cf5f6-111">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
