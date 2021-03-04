---
description: 'Дополнительные сведения о: класс не поддерживает автоматизацию или не поддерживает ожидаемый интерфейс'
title: Класс не поддерживает автоматизацию или не поддерживает ожидаемый интерфейс
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: c173eeddf3a34d6af169b91066199ce7d03cf4ba
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106635"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="168c4-103">Класс не поддерживает автоматизацию или не поддерживает ожидаемый интерфейс</span><span class="sxs-lookup"><span data-stu-id="168c4-103">Class does not support Automation or does not support expected interface</span></span>

<span data-ttu-id="168c4-104">Либо класс, указанный вами в вызове функции `GetObject` или `CreateObject`, не предоставил интерфейс программирования, либо вы изменили проект с .DLL на .EXE или наоборот.</span><span class="sxs-lookup"><span data-stu-id="168c4-104">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="168c4-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="168c4-105">To correct this error</span></span>  
  
1. <span data-ttu-id="168c4-106">Просмотрите документацию по приложению, которое создало данный объект, чтобы узнать об ограничениях на использование автоматизации с объектом такого класса.</span><span class="sxs-lookup"><span data-stu-id="168c4-106">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2. <span data-ttu-id="168c4-107">Если вы изменили проект с .DLL на .EXE или наоборот, необходимо вручную отменить регистрацию старого проекта .DLL или .EXE.</span><span class="sxs-lookup"><span data-stu-id="168c4-107">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="168c4-108">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="168c4-108">See also</span></span>

- [<span data-ttu-id="168c4-109">Типы ошибок</span><span class="sxs-lookup"><span data-stu-id="168c4-109">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="168c4-110">Параметры обратной связи Visual Studio</span><span class="sxs-lookup"><span data-stu-id="168c4-110">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
