---
description: 'Дополнительные сведения о методе: ICLRDataTarget:: GetTLSValue'
title: Метод ICLRDataTarget::GetTLSValue
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type:
- apiref
ms.openlocfilehash: 5c0c4a462d89c2eceada4180ea532f36fc9e48b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718048"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="247a1-103">Метод ICLRDataTarget::GetTLSValue</span><span class="sxs-lookup"><span data-stu-id="247a1-103">ICLRDataTarget::GetTLSValue Method</span></span>

<span data-ttu-id="247a1-104">Возвращает значение из локального хранилища потока (TLS) указанного потока в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="247a1-104">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="247a1-105">Этот метод вызывается службами доступа к данным среды CLR.</span><span class="sxs-lookup"><span data-stu-id="247a1-105">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="247a1-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="247a1-106">Syntax</span></span>  
  
```cpp  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="247a1-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="247a1-107">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="247a1-108">окне Идентификатор операционной системы потока в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="247a1-108">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="247a1-109">окне Индекс расположения.</span><span class="sxs-lookup"><span data-stu-id="247a1-109">[in] The index of the location.</span></span> <span data-ttu-id="247a1-110">Это значение должно быть допустимым индексом в локальном хранилище указанного потока.</span><span class="sxs-lookup"><span data-stu-id="247a1-110">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="247a1-111">заполняет Указатель на `CLRDATA_ADDRESS` значение, указывающее значение, возвращаемое из заданного расположения TLS.</span><span class="sxs-lookup"><span data-stu-id="247a1-111">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="247a1-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="247a1-112">Remarks</span></span>  

 <span data-ttu-id="247a1-113">Этот метод реализуется модулем записи отладчика.</span><span class="sxs-lookup"><span data-stu-id="247a1-113">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="247a1-114">Требования</span><span class="sxs-lookup"><span data-stu-id="247a1-114">Requirements</span></span>  

 <span data-ttu-id="247a1-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="247a1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="247a1-116">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="247a1-116">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="247a1-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="247a1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="247a1-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="247a1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="247a1-119">См. также</span><span class="sxs-lookup"><span data-stu-id="247a1-119">See also</span></span>

- [<span data-ttu-id="247a1-120">Интерфейс ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="247a1-120">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
