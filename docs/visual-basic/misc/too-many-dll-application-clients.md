---
description: 'Дополнительные сведения: слишком много клиентов приложения DLL'
title: Слишком много приложений-клиентов DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
ms.openlocfilehash: 053896fb08359de009ebe202ae9691f1761ecdd5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427639"
---
# <a name="too-many-dll-application-clients"></a><span data-ttu-id="d6c40-103">Слишком много приложений-клиентов DLL</span><span class="sxs-lookup"><span data-stu-id="d6c40-103">Too many DLL application clients</span></span>

<span data-ttu-id="d6c40-104">Библиотека динамической компоновки (DLL) для Visual Basic может поддерживать доступ только ограниченное количество ведущих приложений.</span><span class="sxs-lookup"><span data-stu-id="d6c40-104">The dynamic-link library (DLL) for Visual Basic can only accommodate access by a limited number of host applications.</span></span> <span data-ttu-id="d6c40-105">Приложение и другие приложения, Visual Basic узлы (некоторые из которых могут быть доступны приложению), пытаются одновременно получить доступ к библиотеке DLL Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d6c40-105">Your application and other applications that are Visual Basic hosts (some of which may be accessed by your application) are all attempting to access the Visual Basic DLL at the same time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d6c40-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="d6c40-106">To correct this error</span></span>  
  
- <span data-ttu-id="d6c40-107">Сократите число открытых приложений, обращающихся к Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d6c40-107">Reduce the number of open applications accessing Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c40-108">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d6c40-108">See also</span></span>

- [<span data-ttu-id="d6c40-109">Типы ошибок</span><span class="sxs-lookup"><span data-stu-id="d6c40-109">Error Types</span></span>](../programming-guide/language-features/error-types.md)
