---
description: 'Дополнительные сведения о методе: ICorPublish:: EnumProcesses'
title: Метод ICorPublish::EnumProcesses
ms.date: 03/30/2017
api_name:
- ICorPublish.EnumProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::EnumProcesses
helpviewer_keywords:
- ICorPublish::EnumProcesses method [.NET Framework debugging]
- EnumProcesses method [.NET Framework debugging]
ms.assetid: 4ae765f0-93b2-4b6f-aea1-7b0cf44e04a7
topic_type:
- apiref
ms.openlocfilehash: 2451f179301eff4caca966568f966d145e269f51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722000"
---
# <a name="icorpublishenumprocesses-method"></a><span data-ttu-id="be9a3-103">Метод ICorPublish::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="be9a3-103">ICorPublish::EnumProcesses Method</span></span>

<span data-ttu-id="be9a3-104">Возвращает перечислитель для управляемых процессов, выполняющихся на этом компьютере.</span><span class="sxs-lookup"><span data-stu-id="be9a3-104">Gets an enumerator for the managed processes running on this computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be9a3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="be9a3-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
    [in] COR_PUB_ENUMPROCESS       Type,  
    [out] ICorPublishProcessEnum   **ppIEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be9a3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="be9a3-106">Parameters</span></span>  

 `Type`  
 <span data-ttu-id="be9a3-107">Значение перечисления [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) , указывающее тип получаемого процесса.</span><span class="sxs-lookup"><span data-stu-id="be9a3-107">A value of the [COR_PUB_ENUMPROCESS](cor-pub-enumprocess-enumeration.md) enumeration that specifies the type of process to be retrieved.</span></span> <span data-ttu-id="be9a3-108">В текущей версии допускается только COR_PUB_MANAGEDONLY.</span><span class="sxs-lookup"><span data-stu-id="be9a3-108">In the current version, only COR_PUB_MANAGEDONLY is valid.</span></span>  
  
 `ppIEnum`  
 <span data-ttu-id="be9a3-109">Указатель на адрес экземпляра [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) , который является перечислителем процессов.</span><span class="sxs-lookup"><span data-stu-id="be9a3-109">A pointer to the address of an [ICorPublishProcessEnum](icorpublishprocessenum-interface.md) instance that is the enumerator of the processes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be9a3-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="be9a3-110">Remarks</span></span>  

 <span data-ttu-id="be9a3-111">Коллекция процессов перечислителя основана на моментальном снимке процессов, выполняемых при `EnumProcesses` вызове метода.</span><span class="sxs-lookup"><span data-stu-id="be9a3-111">The enumerator's collection of processes is based on a snapshot of the processes that are running when the `EnumProcesses` method is called.</span></span> <span data-ttu-id="be9a3-112">Перечислитель не будет включать процессы, которые завершаются до или запуска после `EnumProcesses` вызова.</span><span class="sxs-lookup"><span data-stu-id="be9a3-112">The enumerator will not include any processes that terminate before or start after `EnumProcesses` is called.</span></span>  
  
 <span data-ttu-id="be9a3-113">`EnumProcesses`Метод может быть вызван более одного раза в этом экземпляре [ICorPublish](icorpublish-interface.md) для создания новой актуальной коллекции процессов.</span><span class="sxs-lookup"><span data-stu-id="be9a3-113">The `EnumProcesses` method may be called more than once on this [ICorPublish](icorpublish-interface.md) instance to create a new up-to-date collection of processes.</span></span> <span data-ttu-id="be9a3-114">Последующие вызовы метода не будут затронуты существующими коллекциями `EnumProcesses` .</span><span class="sxs-lookup"><span data-stu-id="be9a3-114">Existing collections will not be affected by subsequent calls of the `EnumProcesses` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be9a3-115">Требования</span><span class="sxs-lookup"><span data-stu-id="be9a3-115">Requirements</span></span>  

 <span data-ttu-id="be9a3-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be9a3-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be9a3-117">**Заголовок:** Корпуб. idl, Корпуб. h</span><span class="sxs-lookup"><span data-stu-id="be9a3-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="be9a3-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be9a3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be9a3-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be9a3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be9a3-120">См. также</span><span class="sxs-lookup"><span data-stu-id="be9a3-120">See also</span></span>

- [<span data-ttu-id="be9a3-121">Интерфейс ICorPublish</span><span class="sxs-lookup"><span data-stu-id="be9a3-121">ICorPublish Interface</span></span>](icorpublish-interface.md)
