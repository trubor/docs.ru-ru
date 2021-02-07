---
description: 'Дополнительные сведения о методе: ICLRDataTarget:: Request'
title: Метод ICLRDataTarget::Request
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
ms.openlocfilehash: 75c400a51a2fdaf0044d85b5f483d783fae4628b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712172"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="20930-103">Метод ICLRDataTarget::Request</span><span class="sxs-lookup"><span data-stu-id="20930-103">ICLRDataTarget::Request Method</span></span>

<span data-ttu-id="20930-104">Вызывается службами доступа к данным среды CLR для запроса операции, как определено в реализации.</span><span class="sxs-lookup"><span data-stu-id="20930-104">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20930-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="20930-105">Syntax</span></span>  
  
```cpp  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]
        BYTE                *outBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20930-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="20930-106">Parameters</span></span>  

 `reqCode`  
 <span data-ttu-id="20930-107">окне Определяется пользователем.</span><span class="sxs-lookup"><span data-stu-id="20930-107">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="20930-108">окне Размер входного буфера, используемого для входящего запроса.</span><span class="sxs-lookup"><span data-stu-id="20930-108">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="20930-109">окне Буфер, содержащий запрос.</span><span class="sxs-lookup"><span data-stu-id="20930-109">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="20930-110">окне Размер выходного буфера, используемого для ответа.</span><span class="sxs-lookup"><span data-stu-id="20930-110">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="20930-111">заполняет Буфер, содержащий ответ.</span><span class="sxs-lookup"><span data-stu-id="20930-111">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20930-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="20930-112">Remarks</span></span>  

 <span data-ttu-id="20930-113">`Request`Метод упрощает добавление неуказанных пользовательских операций.</span><span class="sxs-lookup"><span data-stu-id="20930-113">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="20930-114">Это значит, что этот метод обеспечивает расширяемость без необходимости пересмотра определения интерфейса.</span><span class="sxs-lookup"><span data-stu-id="20930-114">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="20930-115">Этот метод реализуется модулем записи отладчика.</span><span class="sxs-lookup"><span data-stu-id="20930-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20930-116">Требования</span><span class="sxs-lookup"><span data-stu-id="20930-116">Requirements</span></span>  

 <span data-ttu-id="20930-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20930-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20930-118">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="20930-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="20930-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20930-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20930-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20930-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20930-121">См. также</span><span class="sxs-lookup"><span data-stu-id="20930-121">See also</span></span>

- [<span data-ttu-id="20930-122">Интерфейс ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="20930-122">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
