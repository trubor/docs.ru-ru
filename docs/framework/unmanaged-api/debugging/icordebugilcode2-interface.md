---
description: 'Дополнительные сведения о: интерфейс ICorDebugILCode2'
title: Интерфейс ICorDebugILCode2
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
ms.openlocfilehash: 52e47b8cbf8f9926797e193944fd7e97b2e4dbcd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791417"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="64fa2-103">Интерфейс ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="64fa2-103">ICorDebugILCode2 Interface</span></span>

<span data-ttu-id="64fa2-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="64fa2-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="64fa2-105">Логически расширяет интерфейс [икордебугилкоде](icordebugilcode-interface.md) , чтобы предоставить методы, которые возвращают маркер для сигнатуры локальной переменной функции и сопоставляют смещенные промежуточные языки (IL) профилировщика с исходными смещениями Il метода.</span><span class="sxs-lookup"><span data-stu-id="64fa2-105">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64fa2-106">Методы</span><span class="sxs-lookup"><span data-stu-id="64fa2-106">Methods</span></span>  
  
|<span data-ttu-id="64fa2-107">Метод</span><span class="sxs-lookup"><span data-stu-id="64fa2-107">Method</span></span>|<span data-ttu-id="64fa2-108">Описание</span><span class="sxs-lookup"><span data-stu-id="64fa2-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64fa2-109">Метод GetInstrumentedILMap</span><span class="sxs-lookup"><span data-stu-id="64fa2-109">GetInstrumentedILMap Method</span></span>](icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="64fa2-110">Возвращает сопоставление смещений инструментированного профилировщиком промежуточного языка со смещениями промежуточного языка исходного метода для этого экземпляра.</span><span class="sxs-lookup"><span data-stu-id="64fa2-110">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="64fa2-111">Метод GetLocalVarSigToken</span><span class="sxs-lookup"><span data-stu-id="64fa2-111">GetLocalVarSigToken Method</span></span>](icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="64fa2-112">Получает маркер метаданных для подписи локальной переменной, предназначенной для представленной этим экземпляром функции.</span><span class="sxs-lookup"><span data-stu-id="64fa2-112">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="64fa2-113">Требования</span><span class="sxs-lookup"><span data-stu-id="64fa2-113">Requirements</span></span>  

 <span data-ttu-id="64fa2-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64fa2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64fa2-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64fa2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64fa2-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64fa2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64fa2-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64fa2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64fa2-118">См. также</span><span class="sxs-lookup"><span data-stu-id="64fa2-118">See also</span></span>

- [<span data-ttu-id="64fa2-119">Интерфейс ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="64fa2-119">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="64fa2-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="64fa2-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="64fa2-121">Отладка</span><span class="sxs-lookup"><span data-stu-id="64fa2-121">Debugging</span></span>](index.md)
