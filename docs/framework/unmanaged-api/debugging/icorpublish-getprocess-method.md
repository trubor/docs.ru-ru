---
description: 'Дополнительные сведения о методе: ICorPublish:: onprocess'
title: Метод ICorPublish::GetProcess
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
ms.openlocfilehash: d288a772274618cc99b63a68b37e84e543957b44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721987"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="f9c75-103">Метод ICorPublish::GetProcess</span><span class="sxs-lookup"><span data-stu-id="f9c75-103">ICorPublish::GetProcess Method</span></span>

<span data-ttu-id="f9c75-104">Возвращает экземпляр [ICorPublishProcess](icorpublishprocess-interface.md) , представляющий процесс с указанным идентификатором.</span><span class="sxs-lookup"><span data-stu-id="f9c75-104">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9c75-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f9c75-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9c75-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f9c75-106">Parameters</span></span>  

 `pid`  
 <span data-ttu-id="f9c75-107">окне Идентификатор процесса.</span><span class="sxs-lookup"><span data-stu-id="f9c75-107">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="f9c75-108">заполняет Указатель на адрес `ICorPublishProcess` экземпляра, который представляет процесс.</span><span class="sxs-lookup"><span data-stu-id="f9c75-108">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9c75-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="f9c75-109">Remarks</span></span>  

 <span data-ttu-id="f9c75-110">`GetProcess` завершается ошибкой, если процесс не существует или не является управляемым процессом, который может быть отлажен текущим пользователем.</span><span class="sxs-lookup"><span data-stu-id="f9c75-110">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9c75-111">Требования</span><span class="sxs-lookup"><span data-stu-id="f9c75-111">Requirements</span></span>  

 <span data-ttu-id="f9c75-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9c75-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9c75-113">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="f9c75-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f9c75-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9c75-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9c75-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9c75-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9c75-116">См. также</span><span class="sxs-lookup"><span data-stu-id="f9c75-116">See also</span></span>

- [<span data-ttu-id="f9c75-117">Интерфейс ICorPublish</span><span class="sxs-lookup"><span data-stu-id="f9c75-117">ICorPublish Interface</span></span>](icorpublish-interface.md)
