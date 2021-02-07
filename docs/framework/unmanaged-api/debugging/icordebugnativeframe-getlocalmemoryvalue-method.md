---
description: 'Дополнительные сведения о методе: ICorDebugNativeFrame:: GetLocalMemoryValue'
title: Метод ICorDebugNativeFrame::GetLocalMemoryValue
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryValue
helpviewer_keywords:
- GetLocalMemoryValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalMemoryValue method [.NET Framework debugging]
ms.assetid: b600b3a2-9908-42d8-8093-ab6f39e9a2c9
topic_type:
- apiref
ms.openlocfilehash: 5fbdf9474ca8c5849b7d917ecddff491b329113b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729244"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a><span data-ttu-id="e7d20-103">Метод ICorDebugNativeFrame::GetLocalMemoryValue</span><span class="sxs-lookup"><span data-stu-id="e7d20-103">ICorDebugNativeFrame::GetLocalMemoryValue Method</span></span>

<span data-ttu-id="e7d20-104">Возвращает значение аргумента или локальной переменной, которая хранится в указанном месте в памяти для этого машинного кадра.</span><span class="sxs-lookup"><span data-stu-id="e7d20-104">Gets the value of an argument or local variable that is stored in the specified memory location for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7d20-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e7d20-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7d20-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e7d20-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="e7d20-107">окне `CORDB_ADDRESS` Значение типа, указывающее место в памяти, содержащее значение.</span><span class="sxs-lookup"><span data-stu-id="e7d20-107">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="e7d20-108">окне Целое число, указывающее размер подписи двоичных метаданных, на которую ссылается `pvSigBlob` параметр.</span><span class="sxs-lookup"><span data-stu-id="e7d20-108">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="e7d20-109">окне `PCCOR_SIGNATURE` Значение, которое указывает на сигнатуру двоичных метаданных для типа значения.</span><span class="sxs-lookup"><span data-stu-id="e7d20-109">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="e7d20-110">заполняет Указатель на адрес объекта ICorDebugValue, представляющего извлеченное значение, хранящееся в указанном расположении в памяти.</span><span class="sxs-lookup"><span data-stu-id="e7d20-110">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7d20-111">Требования</span><span class="sxs-lookup"><span data-stu-id="e7d20-111">Requirements</span></span>  

 <span data-ttu-id="e7d20-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7d20-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7d20-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7d20-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7d20-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7d20-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7d20-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7d20-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d20-116">См. также</span><span class="sxs-lookup"><span data-stu-id="e7d20-116">See also</span></span>
