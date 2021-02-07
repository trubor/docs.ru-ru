---
description: Дополнительные сведения о методе SetNonAssemblyFlags
title: Метод SetNonAssemblyFlags
ms.date: 03/30/2017
api_name:
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
ms.openlocfilehash: 9cf311ec8f04f97da03be626e20c1c07065eac38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662316"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="9add4-103">Метод SetNonAssemblyFlags</span><span class="sxs-lookup"><span data-stu-id="9add4-103">SetNonAssemblyFlags Method</span></span>

<span data-ttu-id="9add4-104">Устанавливает флаги, не зависящие от сборки.</span><span class="sxs-lookup"><span data-stu-id="9add4-104">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9add4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9add4-105">Syntax</span></span>  
  
```cpp  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9add4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9add4-106">Parameters</span></span>  

 `afFlags`  
 <span data-ttu-id="9add4-107">Флаги ALink.</span><span class="sxs-lookup"><span data-stu-id="9add4-107">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9add4-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="9add4-108">Return Value</span></span>  

 <span data-ttu-id="9add4-109">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="9add4-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9add4-110">Требования</span><span class="sxs-lookup"><span data-stu-id="9add4-110">Requirements</span></span>  

 <span data-ttu-id="9add4-111">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="9add4-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9add4-112">См. также</span><span class="sxs-lookup"><span data-stu-id="9add4-112">See also</span></span>

- [<span data-ttu-id="9add4-113">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="9add4-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="9add4-114">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="9add4-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="9add4-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="9add4-115">ALink API</span></span>](index.md)
