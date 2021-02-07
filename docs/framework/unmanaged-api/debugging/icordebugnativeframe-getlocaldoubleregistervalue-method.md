---
description: 'Дополнительные сведения о методе: ICorDebugNativeFrame:: Жетлокалдаублерегистервалуе'
title: Метод ICorDebugNativeFrame::GetLocalDoubleRegisterValue
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
ms.openlocfilehash: a478c51ea7bf04b3fc3faf49fef39f9b29a30599
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722429"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a><span data-ttu-id="42c2a-103">Метод ICorDebugNativeFrame::GetLocalDoubleRegisterValue</span><span class="sxs-lookup"><span data-stu-id="42c2a-103">ICorDebugNativeFrame::GetLocalDoubleRegisterValue Method</span></span>

<span data-ttu-id="42c2a-104">Возвращает значение аргумента или локальной переменной, которая хранится в двух указанных регистрах для этого собственного кадра.</span><span class="sxs-lookup"><span data-stu-id="42c2a-104">Gets the value of an argument or local variable that is stored in the two specified registers for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42c2a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="42c2a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42c2a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="42c2a-106">Parameters</span></span>  

 `highWordReg`  
 <span data-ttu-id="42c2a-107">окне Значение перечисления "CorDebugRegister", указывающее регистр, содержащий старшее слово значения.</span><span class="sxs-lookup"><span data-stu-id="42c2a-107">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the high word of the value.</span></span>  
  
 `lowWordReg`  
 <span data-ttu-id="42c2a-108">окне Значение `CorDebugRegister` перечисления, указывающее регистр, содержащий нижнее слово значения.</span><span class="sxs-lookup"><span data-stu-id="42c2a-108">[in] A value of the `CorDebugRegister` enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="42c2a-109">окне Целое число, указывающее размер подписи двоичных метаданных, на которую ссылается `pvSigBlob` параметр.</span><span class="sxs-lookup"><span data-stu-id="42c2a-109">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="42c2a-110">окне `PCCOR_SIGNATURE` Значение, которое указывает на сигнатуру двоичных метаданных для типа значения.</span><span class="sxs-lookup"><span data-stu-id="42c2a-110">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="42c2a-111">заполняет Указатель на адрес объекта ICorDebugValue, представляющего извлеченное значение, хранящееся в указанных регистрах.</span><span class="sxs-lookup"><span data-stu-id="42c2a-111">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified registers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42c2a-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="42c2a-112">Remarks</span></span>  

 <span data-ttu-id="42c2a-113">`GetLocalDoubleRegisterValue`Метод можно использовать либо в машинном кадре, либо в кадре JIT-компиляции.</span><span class="sxs-lookup"><span data-stu-id="42c2a-113">The `GetLocalDoubleRegisterValue` method can be used either in a native frame or a just-in-time (JIT)-compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42c2a-114">Требования</span><span class="sxs-lookup"><span data-stu-id="42c2a-114">Requirements</span></span>  

 <span data-ttu-id="42c2a-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42c2a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42c2a-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42c2a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42c2a-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42c2a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42c2a-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42c2a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c2a-119">См. также</span><span class="sxs-lookup"><span data-stu-id="42c2a-119">See also</span></span>
