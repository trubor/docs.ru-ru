---
description: 'Дополнительные сведения о: интерфейс Икордебугмержедассемблирекорд'
title: Интерфейс ICorDebugMergedAssemblyRecord
ms.date: 03/30/2017
ms.assetid: fe280b11-9479-4e34-a07c-0d1ea8088422
ms.openlocfilehash: e64c0ee30a8e8956dd336a30e6c81962c75f04e9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650304"
---
# <a name="icordebugmergedassemblyrecord-interface"></a><span data-ttu-id="491d9-103">Интерфейс ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="491d9-103">ICorDebugMergedAssemblyRecord Interface</span></span>

<span data-ttu-id="491d9-104">Предоставляет сведения о сборке после слияния.</span><span class="sxs-lookup"><span data-stu-id="491d9-104">Provides information about a merged assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="491d9-105">Методы</span><span class="sxs-lookup"><span data-stu-id="491d9-105">Methods</span></span>  
  
|<span data-ttu-id="491d9-106">Метод</span><span class="sxs-lookup"><span data-stu-id="491d9-106">Method</span></span>|<span data-ttu-id="491d9-107">Описание</span><span class="sxs-lookup"><span data-stu-id="491d9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="491d9-108">Метод GetCulture</span><span class="sxs-lookup"><span data-stu-id="491d9-108">GetCulture Method</span></span>](icordebugmergedassemblyrecord-getculture-method.md)|<span data-ttu-id="491d9-109">Возвращает строку с названием языка и региональных параметров сборки.</span><span class="sxs-lookup"><span data-stu-id="491d9-109">Gets the culture name string of the assembly.</span></span>|  
|[<span data-ttu-id="491d9-110">Метод GetIndex</span><span class="sxs-lookup"><span data-stu-id="491d9-110">GetIndex Method</span></span>](icordebugmergedassemblyrecord-getindex-method.md)|<span data-ttu-id="491d9-111">Возвращает индекс префикса сборки.</span><span class="sxs-lookup"><span data-stu-id="491d9-111">Gets the assembly's prefix index.</span></span>|  
|[<span data-ttu-id="491d9-112">Метод GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="491d9-112">GetPublicKey Method</span></span>](icordebugmergedassemblyrecord-getpublickey-method.md)|<span data-ttu-id="491d9-113">Возвращает открытый ключ сборки.</span><span class="sxs-lookup"><span data-stu-id="491d9-113">Gets the assembly's public key.</span></span>|  
|[<span data-ttu-id="491d9-114">Метод GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="491d9-114">GetPublicKeyToken Method</span></span>](icordebugmergedassemblyrecord-getpublickeytoken-method.md)|<span data-ttu-id="491d9-115">Возвращает токен открытого ключа сборки.</span><span class="sxs-lookup"><span data-stu-id="491d9-115">Gets the assembly's public key token.</span></span>|  
|[<span data-ttu-id="491d9-116">Метод GetSimpleName</span><span class="sxs-lookup"><span data-stu-id="491d9-116">GetSimpleName Method</span></span>](icordebugmergedassemblyrecord-getsimplename-method.md)|<span data-ttu-id="491d9-117">Получает простое имя сборки.</span><span class="sxs-lookup"><span data-stu-id="491d9-117">Gets the simple name of the assembly.</span></span>|  
|[<span data-ttu-id="491d9-118">Метод GetVersion</span><span class="sxs-lookup"><span data-stu-id="491d9-118">GetVersion Method</span></span>](icordebugmergedassemblyrecord-getversion-method.md)|<span data-ttu-id="491d9-119">Возвращает сведения о версии сборки.</span><span class="sxs-lookup"><span data-stu-id="491d9-119">Gets the assembly's version information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="491d9-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="491d9-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="491d9-121">Этот интерфейс доступен только в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="491d9-121">This interface is available with .NET Native only.</span></span> <span data-ttu-id="491d9-122">При реализации этого интерфейса для сценариев ICorDebug вне .NET Native среда CLR будет игнорировать этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="491d9-122">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="491d9-123">Требования</span><span class="sxs-lookup"><span data-stu-id="491d9-123">Requirements</span></span>  

 <span data-ttu-id="491d9-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="491d9-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="491d9-125">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="491d9-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="491d9-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="491d9-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="491d9-127">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="491d9-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="491d9-128">См. также</span><span class="sxs-lookup"><span data-stu-id="491d9-128">See also</span></span>

- [<span data-ttu-id="491d9-129">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="491d9-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="491d9-130">Отладка</span><span class="sxs-lookup"><span data-stu-id="491d9-130">Debugging</span></span>](index.md)
