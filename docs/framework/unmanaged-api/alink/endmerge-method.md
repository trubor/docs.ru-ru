---
description: Дополнительные сведения о методе EndMerge
title: Метод EndMerge
ms.date: 03/30/2017
api_name:
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
ms.openlocfilehash: aac23d6d87f3fe74c1094bdd4a7f9c9f7f3fa7cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638162"
---
# <a name="endmerge-method"></a><span data-ttu-id="33f88-103">Метод EndMerge</span><span class="sxs-lookup"><span data-stu-id="33f88-103">EndMerge Method</span></span>

<span data-ttu-id="33f88-104">Указывает, что все пользовательские атрибуты были объединены в область действия Emit.</span><span class="sxs-lookup"><span data-stu-id="33f88-104">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33f88-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="33f88-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="33f88-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="33f88-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="33f88-107">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="33f88-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33f88-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="33f88-108">Return Value</span></span>  

 <span data-ttu-id="33f88-109">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="33f88-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33f88-110">Требования</span><span class="sxs-lookup"><span data-stu-id="33f88-110">Requirements</span></span>  

 <span data-ttu-id="33f88-111">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="33f88-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33f88-112">См. также</span><span class="sxs-lookup"><span data-stu-id="33f88-112">See also</span></span>

- [<span data-ttu-id="33f88-113">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="33f88-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="33f88-114">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="33f88-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="33f88-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="33f88-115">ALink API</span></span>](index.md)
