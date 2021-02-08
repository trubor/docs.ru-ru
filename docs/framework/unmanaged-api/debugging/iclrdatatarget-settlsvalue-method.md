---
description: 'Дополнительные сведения о методе: ICLRDataTarget:: Сеттлсвалуе'
title: Метод ICLRDataTarget::SetTLSValue
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type:
- apiref
ms.openlocfilehash: 2432cd66f604575e35f171c98a0fb313c5ccd94e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785690"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="b1750-103">Метод ICLRDataTarget::SetTLSValue</span><span class="sxs-lookup"><span data-stu-id="b1750-103">ICLRDataTarget::SetTLSValue Method</span></span>

<span data-ttu-id="b1750-104">Задает значение в локальном хранилище потока (TLS) указанного потока в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="b1750-104">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="b1750-105">Этот метод вызывается службами доступа к данным среды CLR.</span><span class="sxs-lookup"><span data-stu-id="b1750-105">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1750-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b1750-106">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1750-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="b1750-107">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="b1750-108">окне Идентификатор операционной системы потока в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="b1750-108">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="b1750-109">окне Индекс расположения.</span><span class="sxs-lookup"><span data-stu-id="b1750-109">[in] The index of the location.</span></span> <span data-ttu-id="b1750-110">Это значение должно быть допустимым индексом в локальном хранилище указанного потока.</span><span class="sxs-lookup"><span data-stu-id="b1750-110">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="b1750-111">окне `CLRDATA_ADDRESS` Значение типа, указывающее значение, помещаемое в заданное расположение TLS.</span><span class="sxs-lookup"><span data-stu-id="b1750-111">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1750-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="b1750-112">Remarks</span></span>  

 <span data-ttu-id="b1750-113">Этот метод реализуется модулем записи отладчика.</span><span class="sxs-lookup"><span data-stu-id="b1750-113">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1750-114">Требования</span><span class="sxs-lookup"><span data-stu-id="b1750-114">Requirements</span></span>  

 <span data-ttu-id="b1750-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1750-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1750-116">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="b1750-116">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b1750-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1750-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1750-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1750-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1750-119">См. также</span><span class="sxs-lookup"><span data-stu-id="b1750-119">See also</span></span>

- [<span data-ttu-id="b1750-120">Интерфейс ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="b1750-120">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
