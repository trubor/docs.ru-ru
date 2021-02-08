---
description: 'Дополнительные сведения о: интерфейс Икордебугстатикфиелдсимбол'
title: Интерфейс ICorDebugStaticFieldSymbol
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: 3aa9c98cef4cdc7edc519b06b6cf9b4b2192b4e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794680"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="56363-103">Интерфейс ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="56363-103">ICorDebugStaticFieldSymbol Interface</span></span>

<span data-ttu-id="56363-104">Представляет сведения символа отладки для статического поля.</span><span class="sxs-lookup"><span data-stu-id="56363-104">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56363-105">Методы</span><span class="sxs-lookup"><span data-stu-id="56363-105">Methods</span></span>  
  
|<span data-ttu-id="56363-106">Метод</span><span class="sxs-lookup"><span data-stu-id="56363-106">Method</span></span>|<span data-ttu-id="56363-107">Описание</span><span class="sxs-lookup"><span data-stu-id="56363-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56363-108">Метод GetAddress</span><span class="sxs-lookup"><span data-stu-id="56363-108">GetAddress Method</span></span>](icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="56363-109">Получает адрес статического поля.</span><span class="sxs-lookup"><span data-stu-id="56363-109">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="56363-110">Метод GetName</span><span class="sxs-lookup"><span data-stu-id="56363-110">GetName Method</span></span>](icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="56363-111">Получает имя статического поля.</span><span class="sxs-lookup"><span data-stu-id="56363-111">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="56363-112">Метод GetSize</span><span class="sxs-lookup"><span data-stu-id="56363-112">GetSize Method</span></span>](icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="56363-113">Получает размер статического поля в байтах.</span><span class="sxs-lookup"><span data-stu-id="56363-113">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56363-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="56363-114">Remarks</span></span>  

 <span data-ttu-id="56363-115">Интерфейс `ICorDebugStaticFieldSymbol` используется для извлечения сведений отладочного символа для статического поля.</span><span class="sxs-lookup"><span data-stu-id="56363-115">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56363-116">Этот интерфейс доступен только в .NET Native.</span><span class="sxs-lookup"><span data-stu-id="56363-116">This interface is available with .NET Native only.</span></span> <span data-ttu-id="56363-117">При реализации этого интерфейса для сценариев ICorDebug вне .NET Native среда CLR будет игнорировать этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="56363-117">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56363-118">Требования</span><span class="sxs-lookup"><span data-stu-id="56363-118">Requirements</span></span>  

 <span data-ttu-id="56363-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56363-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56363-120">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56363-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56363-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56363-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56363-122">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56363-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56363-123">См. также</span><span class="sxs-lookup"><span data-stu-id="56363-123">See also</span></span>

- [<span data-ttu-id="56363-124">Интерфейс ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="56363-124">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="56363-125">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="56363-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="56363-126">Отладка</span><span class="sxs-lookup"><span data-stu-id="56363-126">Debugging</span></span>](index.md)
