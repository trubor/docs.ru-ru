---
description: 'Дополнительные сведения о методе: метод iclrdatatarget3:: GetExceptionThreadID'
title: Метод ICLRDataTarget3::GetExceptionThreadID
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionThreadID
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type:
- apiref
ms.openlocfilehash: 8202b6d83d0c81853111c5da7cfb8deec4d4e222
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794823"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="5e0f7-103">Метод ICLRDataTarget3::GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="5e0f7-103">ICLRDataTarget3::GetExceptionThreadID Method</span></span>

<span data-ttu-id="5e0f7-104">Вызывается службами доступа к данным среды CLR для получения идентификатора потока, вызвавшего исключение.</span><span class="sxs-lookup"><span data-stu-id="5e0f7-104">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e0f7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5e0f7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e0f7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5e0f7-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="5e0f7-107">[из] Идентификатор потока, вызвавшего исключение.</span><span class="sxs-lookup"><span data-stu-id="5e0f7-107">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e0f7-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="5e0f7-108">Return Value</span></span>  

 <span data-ttu-id="5e0f7-109">Возвращается значение `S_OK` при успешном выполнении или код ошибки `HRESULT` при сбое.</span><span class="sxs-lookup"><span data-stu-id="5e0f7-109">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="5e0f7-110">Коды `HRESULT` могут включать значения, приведенные в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="5e0f7-110">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="5e0f7-111">Код возврата</span><span class="sxs-lookup"><span data-stu-id="5e0f7-111">Return code</span></span>|<span data-ttu-id="5e0f7-112">Описание</span><span class="sxs-lookup"><span data-stu-id="5e0f7-112">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="5e0f7-113">Метод успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="5e0f7-113">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="5e0f7-114">Не удалось найти допустимый идентификатор потока для исключения.</span><span class="sxs-lookup"><span data-stu-id="5e0f7-114">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e0f7-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="5e0f7-115">Remarks</span></span>  

 <span data-ttu-id="5e0f7-116">Этот метод реализуется модулем записи отладчика.</span><span class="sxs-lookup"><span data-stu-id="5e0f7-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e0f7-117">Требования</span><span class="sxs-lookup"><span data-stu-id="5e0f7-117">Requirements</span></span>  

 <span data-ttu-id="5e0f7-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e0f7-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e0f7-119">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="5e0f7-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5e0f7-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e0f7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e0f7-121">**Платформа .NET Framework версии:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5e0f7-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e0f7-122">См. также</span><span class="sxs-lookup"><span data-stu-id="5e0f7-122">See also</span></span>

- [<span data-ttu-id="5e0f7-123">Интерфейс ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="5e0f7-123">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="5e0f7-124">Метод GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="5e0f7-124">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="5e0f7-125">Метод GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="5e0f7-125">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)
