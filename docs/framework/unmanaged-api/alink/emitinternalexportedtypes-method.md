---
description: Дополнительные сведения о методе Емитинтерналекспортедтипес
title: Метод EmitInternalExportedTypes
ms.date: 03/30/2017
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitInternalExportedTypes
helpviewer_keywords:
- EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type:
- apiref
ms.openlocfilehash: 5d23c593988b31c077d3b65b11b73113e164ed74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638305"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="d3071-103">Метод EmitInternalExportedTypes</span><span class="sxs-lookup"><span data-stu-id="d3071-103">EmitInternalExportedTypes Method</span></span>

<span data-ttu-id="d3071-104">Выдает типы, добавленные в сборку.</span><span class="sxs-lookup"><span data-stu-id="d3071-104">Emits types added to the assembly.</span></span> <span data-ttu-id="d3071-105">Вызовите этот метод после добавления известных внутренних типов.</span><span class="sxs-lookup"><span data-stu-id="d3071-105">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3071-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d3071-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3071-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="d3071-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="d3071-108">Идентификатор сборки.</span><span class="sxs-lookup"><span data-stu-id="d3071-108">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3071-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d3071-109">Return Value</span></span>  

 <span data-ttu-id="d3071-110">Возвращает S_OK, если метод завершается с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="d3071-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3071-111">Требования</span><span class="sxs-lookup"><span data-stu-id="d3071-111">Requirements</span></span>  

 <span data-ttu-id="d3071-112">Требуется ALink. h</span><span class="sxs-lookup"><span data-stu-id="d3071-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3071-113">См. также</span><span class="sxs-lookup"><span data-stu-id="d3071-113">See also</span></span>

- [<span data-ttu-id="d3071-114">Интерфейс IALink2</span><span class="sxs-lookup"><span data-stu-id="d3071-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d3071-115">Интерфейс IALink</span><span class="sxs-lookup"><span data-stu-id="d3071-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d3071-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="d3071-116">ALink API</span></span>](index.md)
