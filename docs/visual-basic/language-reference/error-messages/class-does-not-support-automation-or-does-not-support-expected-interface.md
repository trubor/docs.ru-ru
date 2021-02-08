---
description: 'Дополнительные сведения о: класс не поддерживает автоматизацию или не поддерживает ожидаемый интерфейс'
title: Класс не поддерживает автоматизацию или не поддерживает ожидаемый интерфейс
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: cc5ae539064b8d049e2808d916f9f4b75f7e94c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796799"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="eec1b-103">Класс не поддерживает автоматизацию или не поддерживает ожидаемый интерфейс</span><span class="sxs-lookup"><span data-stu-id="eec1b-103">Class does not support Automation or does not support expected interface</span></span>

<span data-ttu-id="eec1b-104">Либо класс, указанный вами в вызове функции `GetObject` или `CreateObject`, не предоставил интерфейс программирования, либо вы изменили проект с .DLL на .EXE или наоборот.</span><span class="sxs-lookup"><span data-stu-id="eec1b-104">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eec1b-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="eec1b-105">To correct this error</span></span>  
  
1. <span data-ttu-id="eec1b-106">Просмотрите документацию по приложению, которое создало данный объект, чтобы узнать об ограничениях на использование автоматизации с объектом такого класса.</span><span class="sxs-lookup"><span data-stu-id="eec1b-106">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2. <span data-ttu-id="eec1b-107">Если вы изменили проект с .DLL на .EXE или наоборот, необходимо вручную отменить регистрацию старого проекта .DLL или .EXE.</span><span class="sxs-lookup"><span data-stu-id="eec1b-107">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eec1b-108">См. также</span><span class="sxs-lookup"><span data-stu-id="eec1b-108">See also</span></span>

- [<span data-ttu-id="eec1b-109">Типы ошибок</span><span class="sxs-lookup"><span data-stu-id="eec1b-109">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="eec1b-110">Обращайтесь к нам</span><span class="sxs-lookup"><span data-stu-id="eec1b-110">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
