---
description: 'Дополнительные сведения о методе: ICorDebugNativeFrame:: Жетлокалрегистервалуе'
title: Метод ICorDebugNativeFrame::GetLocalRegisterValue
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type:
- apiref
ms.openlocfilehash: ae21134db11c4d0449ed5f6d583f435a259b83fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729163"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a><span data-ttu-id="fa87b-103">Метод ICorDebugNativeFrame::GetLocalRegisterValue</span><span class="sxs-lookup"><span data-stu-id="fa87b-103">ICorDebugNativeFrame::GetLocalRegisterValue Method</span></span>

<span data-ttu-id="fa87b-104">Возвращает значение аргумента или локальной переменной, хранящейся в указанном регистре для этого собственного кадра.</span><span class="sxs-lookup"><span data-stu-id="fa87b-104">Gets the value of an argument or local variable that is stored in the specified register for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa87b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fa87b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa87b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fa87b-106">Parameters</span></span>  

 `reg`  
 <span data-ttu-id="fa87b-107">окне Значение перечисления "CorDebugRegister", указывающее регистр, содержащий значение.</span><span class="sxs-lookup"><span data-stu-id="fa87b-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="fa87b-108">окне Целое число, указывающее размер подписи двоичных метаданных, на которую ссылается `pvSigBlob` параметр.</span><span class="sxs-lookup"><span data-stu-id="fa87b-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="fa87b-109">окне `PCCOR_SIGNATURE` Значение, которое указывает на сигнатуру двоичных метаданных для типа значения.</span><span class="sxs-lookup"><span data-stu-id="fa87b-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="fa87b-110">заполняет Указатель на адрес объекта ICorDebugValue, представляющего извлеченное значение, хранящееся в указанном регистре.</span><span class="sxs-lookup"><span data-stu-id="fa87b-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa87b-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="fa87b-111">Remarks</span></span>  

 <span data-ttu-id="fa87b-112">`GetLocalRegisterValue`Метод можно использовать либо в машинном кадре, либо в кадре JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="fa87b-112">The `GetLocalRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa87b-113">Требования</span><span class="sxs-lookup"><span data-stu-id="fa87b-113">Requirements</span></span>  

 <span data-ttu-id="fa87b-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa87b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa87b-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa87b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa87b-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa87b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa87b-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa87b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa87b-118">См. также</span><span class="sxs-lookup"><span data-stu-id="fa87b-118">See also</span></span>
