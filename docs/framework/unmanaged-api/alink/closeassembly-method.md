---
description: Дополнительные сведения о методе Клосеассембли
title: Метод CloseAssembly
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
ms.openlocfilehash: 927a66f948f691c00a695c626d9c31950a722cb5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638396"
---
# <a name="closeassembly-method"></a><span data-ttu-id="72028-103">Метод CloseAssembly</span><span class="sxs-lookup"><span data-stu-id="72028-103">CloseAssembly Method</span></span>

<span data-ttu-id="72028-104">Завершает операции сборки.</span><span class="sxs-lookup"><span data-stu-id="72028-104">Finalizes assembly operations.</span></span> <span data-ttu-id="72028-105">Вызовите этот метод перед началом новой сборки или несвязанного модуля.</span><span class="sxs-lookup"><span data-stu-id="72028-105">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72028-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="72028-106">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="72028-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="72028-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="72028-108">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="72028-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72028-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="72028-109">Return Value</span></span>  

 <span data-ttu-id="72028-110">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="72028-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72028-111">Требования</span><span class="sxs-lookup"><span data-stu-id="72028-111">Requirements</span></span>  

 <span data-ttu-id="72028-112">Требуется ALink. h.</span><span class="sxs-lookup"><span data-stu-id="72028-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72028-113">См. также</span><span class="sxs-lookup"><span data-stu-id="72028-113">See also</span></span>

- [<span data-ttu-id="72028-114">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="72028-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="72028-115">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="72028-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="72028-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="72028-116">ALink API</span></span>](index.md)
