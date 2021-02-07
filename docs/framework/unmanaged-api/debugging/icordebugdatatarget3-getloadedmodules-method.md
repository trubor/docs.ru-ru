---
description: 'Дополнительные сведения о методе: ICorDebugDataTarget3:: GetLoadedModules'
title: Метод ICorDebugDataTarget3::GetLoadedModules
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: ea6350155fd79b52a37133cad95f624635433a3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764350"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="77386-103">Метод ICorDebugDataTarget3::GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="77386-103">ICorDebugDataTarget3::GetLoadedModules Method</span></span>

<span data-ttu-id="77386-104">Возвращает список модулей, загруженных на данный момент.</span><span class="sxs-lookup"><span data-stu-id="77386-104">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77386-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="77386-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77386-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="77386-106">Parameters</span></span>  

 `cRequestedModules`  
 <span data-ttu-id="77386-107">[in] Число модулей, для которых запрашиваются сведения.</span><span class="sxs-lookup"><span data-stu-id="77386-107">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="77386-108">[out] Указатель на число модулей, о которых возвращаются сведения.</span><span class="sxs-lookup"><span data-stu-id="77386-108">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="77386-109">заполняет Указатель на массив объектов [икордебуглоадедмодуле](icordebugloadedmodule-interface.md) , которые предоставляют сведения о загруженных модулях.</span><span class="sxs-lookup"><span data-stu-id="77386-109">[out] A pointer to an array of [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77386-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="77386-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77386-111">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="77386-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77386-112">Требования</span><span class="sxs-lookup"><span data-stu-id="77386-112">Requirements</span></span>  

 <span data-ttu-id="77386-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77386-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77386-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77386-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77386-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77386-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77386-116">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77386-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77386-117">См. также</span><span class="sxs-lookup"><span data-stu-id="77386-117">See also</span></span>

- [<span data-ttu-id="77386-118">Интерфейс ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="77386-118">ICorDebugDataTarget3 Interface</span></span>](icordebugdatatarget3-interface.md)
- [<span data-ttu-id="77386-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="77386-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
