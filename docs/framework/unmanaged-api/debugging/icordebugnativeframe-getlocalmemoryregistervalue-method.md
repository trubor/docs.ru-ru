---
description: 'Дополнительные сведения о методе: ICorDebugNativeFrame:: GetLocalMemoryRegisterValue'
title: Метод ICorDebugNativeFrame::GetLocalMemoryRegisterValue
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalMemoryRegisterValue method [.NET Framework debugging]
- GetLocalMemoryRegisterValue method
ms.assetid: 33a19f6e-1029-4d53-af64-19591c6e58ee
topic_type:
- apiref
ms.openlocfilehash: a0858aa11713bb71c485174c2f1624a0c7cda821
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718035"
---
# <a name="icordebugnativeframegetlocalmemoryregistervalue-method"></a><span data-ttu-id="fe8bb-103">Метод ICorDebugNativeFrame::GetLocalMemoryRegisterValue</span><span class="sxs-lookup"><span data-stu-id="fe8bb-103">ICorDebugNativeFrame::GetLocalMemoryRegisterValue Method</span></span>

<span data-ttu-id="fe8bb-104">Возвращает значение аргумента или локальной переменной, из которых младшее слово и верхнее слово хранятся в указанном регистре и расположении в памяти соответственно для этого кадра машинного кода.</span><span class="sxs-lookup"><span data-stu-id="fe8bb-104">Gets the value of an argument or local variable, of which the low word and high word are stored in the specified register and memory location, respectively, for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe8bb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fe8bb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryRegisterValue (  
    [in] CORDB_ADDRESS      highWordAddress,  
    [in] CorDebugRegister   lowWordRegister,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe8bb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fe8bb-106">Parameters</span></span>  

 `highWordAddress`  
 <span data-ttu-id="fe8bb-107">окне `CORDB_ADDRESS` Значение типа, указывающее место в памяти, содержащее верхнее слово значения.</span><span class="sxs-lookup"><span data-stu-id="fe8bb-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the high word of the value.</span></span>  
  
 `lowWordRegister`  
 <span data-ttu-id="fe8bb-108">окне Значение перечисления "CorDebugRegister", указывающее регистр, содержащий нижнее слово значения.</span><span class="sxs-lookup"><span data-stu-id="fe8bb-108">[in] A value of the "CorDebugRegister" enumeration that specifies the register containing the low word of the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="fe8bb-109">окне Целое число, указывающее размер подписи двоичных метаданных, на которую ссылается `pvSigBlob` параметр.</span><span class="sxs-lookup"><span data-stu-id="fe8bb-109">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="fe8bb-110">окне `PCCOR_SIGNATURE` Значение, которое указывает на сигнатуру двоичных метаданных для типа значения.</span><span class="sxs-lookup"><span data-stu-id="fe8bb-110">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="fe8bb-111">заполняет Указатель на адрес объекта ICorDebugValue, представляющего извлеченное значение, хранящееся в указанном регистре и расположении в памяти.</span><span class="sxs-lookup"><span data-stu-id="fe8bb-111">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified register and memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe8bb-112">Требования</span><span class="sxs-lookup"><span data-stu-id="fe8bb-112">Requirements</span></span>  

 <span data-ttu-id="fe8bb-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe8bb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe8bb-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe8bb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe8bb-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe8bb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe8bb-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe8bb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe8bb-117">См. также</span><span class="sxs-lookup"><span data-stu-id="fe8bb-117">See also</span></span>
