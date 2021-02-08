---
description: 'Дополнительные сведения о: интерфейс ICorDebugILFrame2'
title: Интерфейс ICorDebugILFrame2
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
ms.openlocfilehash: 8379fda39a210e1df902dab3ac85132f04aee5fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791313"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="ccbda-103">Интерфейс ICorDebugILFrame2</span><span class="sxs-lookup"><span data-stu-id="ccbda-103">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="ccbda-104">Логическое расширение интерфейса ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="ccbda-104">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ccbda-105">Методы</span><span class="sxs-lookup"><span data-stu-id="ccbda-105">Methods</span></span>  
  
|<span data-ttu-id="ccbda-106">Метод</span><span class="sxs-lookup"><span data-stu-id="ccbda-106">Method</span></span>|<span data-ttu-id="ccbda-107">Описание</span><span class="sxs-lookup"><span data-stu-id="ccbda-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ccbda-108">Метод EnumerateTypeParameters</span><span class="sxs-lookup"><span data-stu-id="ccbda-108">EnumerateTypeParameters Method</span></span>](icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="ccbda-109">Возвращает объект ICorDebugTypeEnum, содержащий <xref:System.Type> Параметры в этом кадре.</span><span class="sxs-lookup"><span data-stu-id="ccbda-109">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="ccbda-110">Метод RemapFunction</span><span class="sxs-lookup"><span data-stu-id="ccbda-110">RemapFunction Method</span></span>](icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="ccbda-111">Повторно сопоставляет отредактированную функцию, указывая новое смещение MSIL.</span><span class="sxs-lookup"><span data-stu-id="ccbda-111">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccbda-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="ccbda-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ccbda-113">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="ccbda-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccbda-114">Требования</span><span class="sxs-lookup"><span data-stu-id="ccbda-114">Requirements</span></span>  

 <span data-ttu-id="ccbda-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccbda-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccbda-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ccbda-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ccbda-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccbda-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccbda-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccbda-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccbda-119">См. также</span><span class="sxs-lookup"><span data-stu-id="ccbda-119">See also</span></span>

- [<span data-ttu-id="ccbda-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="ccbda-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
