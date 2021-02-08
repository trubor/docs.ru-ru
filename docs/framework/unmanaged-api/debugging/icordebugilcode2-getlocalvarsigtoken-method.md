---
description: 'Дополнительные сведения о методе: ICorDebugILCode2:: GetLocalVarSigToken'
title: Метод ICorDebugILCode2::GetLocalVarSigToken
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type:
- apiref
ms.openlocfilehash: cdf2725274a132528123534ddd36ae95e265af44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791430"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="c8c25-103">Метод ICorDebugILCode2::GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="c8c25-103">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>

<span data-ttu-id="c8c25-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="c8c25-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c8c25-105">Получает маркер метаданных для подписи локальной переменной, предназначенной для представленной этим экземпляром функции.</span><span class="sxs-lookup"><span data-stu-id="c8c25-105">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8c25-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c8c25-106">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8c25-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="c8c25-107">Parameters</span></span>  

 `pmdSig`  
 <span data-ttu-id="c8c25-108">[из] Указатель на маркер `mdSignature` для подписи локальной переменной, предназначенной для этой функции, или `mdSignatureNil`, если подпись отсутствует (т. е. если функция не имеет локальных переменных).</span><span class="sxs-lookup"><span data-stu-id="c8c25-108">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8c25-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="c8c25-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8c25-110">Требования</span><span class="sxs-lookup"><span data-stu-id="c8c25-110">Requirements</span></span>  

 <span data-ttu-id="c8c25-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8c25-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8c25-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8c25-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8c25-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8c25-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8c25-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8c25-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8c25-115">См. также</span><span class="sxs-lookup"><span data-stu-id="c8c25-115">See also</span></span>

- [<span data-ttu-id="c8c25-116">Интерфейс ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="c8c25-116">ICorDebugILCode2 Interface</span></span>](icordebugilcode2-interface.md)
- [<span data-ttu-id="c8c25-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="c8c25-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
