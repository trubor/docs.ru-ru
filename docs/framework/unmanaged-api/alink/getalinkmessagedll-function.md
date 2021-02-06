---
description: Дополнительные сведения о функции Жеталинкмессажедлл
title: Функция GetALinkMessageDll
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
ms.openlocfilehash: 67a294d1f21f50cee938ddeb14d1f30b4ccf911b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637876"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="3a656-103">Функция GetALinkMessageDll</span><span class="sxs-lookup"><span data-stu-id="3a656-103">GetALinkMessageDll Function</span></span>

<span data-ttu-id="3a656-104">Находит и загружает библиотеку DLL сообщений.</span><span class="sxs-lookup"><span data-stu-id="3a656-104">Finds and loads the message DLL.</span></span> <span data-ttu-id="3a656-105">Возвращает 0, если не удалось обнаружить или загрузить библиотеку DLL сообщений.</span><span class="sxs-lookup"><span data-stu-id="3a656-105">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="3a656-106">DLL сообщения должна быть либо в подкаталоге, имя которого является ИДЕНТИФИКАТОРом языка, либо в текущем каталоге.</span><span class="sxs-lookup"><span data-stu-id="3a656-106">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a656-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3a656-107">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="3a656-108">Требования</span><span class="sxs-lookup"><span data-stu-id="3a656-108">Requirements</span></span>  

 <span data-ttu-id="3a656-109">**Заголовок:** ALink. h</span><span class="sxs-lookup"><span data-stu-id="3a656-109">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="3a656-110">**Библиотека**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="3a656-110">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a656-111">См. также</span><span class="sxs-lookup"><span data-stu-id="3a656-111">See also</span></span>

- [<span data-ttu-id="3a656-112">Al.exe (компоновщик сборок)</span><span class="sxs-lookup"><span data-stu-id="3a656-112">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
