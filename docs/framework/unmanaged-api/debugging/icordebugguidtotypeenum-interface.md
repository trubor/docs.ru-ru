---
description: 'Дополнительные сведения о: интерфейс ICorDebugGuidToTypeEnum'
title: Интерфейс ICorDebugGuidToTypeEnum
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
ms.openlocfilehash: abcdc9537f6f6ff2e0ac9b2be86734efbf303493
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660990"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="c87e3-103">Интерфейс ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="c87e3-103">ICorDebugGuidToTypeEnum Interface</span></span>

<span data-ttu-id="c87e3-104">Предоставляет перечислитель, который определяет сопоставление между набором идентификаторов GUID и соответствующими типами, которые представлены экземплярами ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="c87e3-104">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="c87e3-105">Этот интерфейс наследует методы от интерфейса ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="c87e3-105">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c87e3-106">Методы</span><span class="sxs-lookup"><span data-stu-id="c87e3-106">Methods</span></span>  
  
|<span data-ttu-id="c87e3-107">Метод</span><span class="sxs-lookup"><span data-stu-id="c87e3-107">Method</span></span>|<span data-ttu-id="c87e3-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c87e3-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c87e3-109">ICorDebugGuidToTypeEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="c87e3-109">ICorDebugGuidToTypeEnum::Next</span></span>](icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="c87e3-110">Возвращает указанное число экземпляров [кордебуггуидтотипемаппинг](cordebugguidtotypemapping-structure.md) , которые сопоставляют идентификаторы GUID со сведениями о типе.</span><span class="sxs-lookup"><span data-stu-id="c87e3-110">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c87e3-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="c87e3-111">Remarks</span></span>  

 <span data-ttu-id="c87e3-112">`ICorDebugGuidToTypeEnum`Объект интерфейса можно извлечь, вызвав метод [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c87e3-112">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="c87e3-113">Отладчик может вызвать [следующий](icordebugguidtotypeenum-next-method.md) метод этого интерфейса для получения объектов [кордебуггуидтотипемаппинг](cordebugguidtotypemapping-structure.md) , представляющих сопоставления управляемых представлений типов Среда выполнения Windows, загруженных в домен приложения, используемый для вызова метода [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c87e3-113">A debugger can call this interface's [Next](icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c87e3-114">Требования</span><span class="sxs-lookup"><span data-stu-id="c87e3-114">Requirements</span></span>  

 <span data-ttu-id="c87e3-115">**Платформы:** среда выполнения Windows</span><span class="sxs-lookup"><span data-stu-id="c87e3-115">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="c87e3-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c87e3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c87e3-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c87e3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c87e3-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c87e3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c87e3-119">См. также</span><span class="sxs-lookup"><span data-stu-id="c87e3-119">See also</span></span>

- [<span data-ttu-id="c87e3-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="c87e3-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
