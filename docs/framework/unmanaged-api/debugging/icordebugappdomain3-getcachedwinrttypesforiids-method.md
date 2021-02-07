---
description: 'Дополнительные сведения о методе: ICorDebugAppDomain3:: GetCachedWinRTTypesForIIDs'
title: Метод ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
ms.openlocfilehash: 76b93cdb8c465935a4aaf36090ee44f2b6253a3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754177"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="7eafb-103">Метод ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="7eafb-103">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>

<span data-ttu-id="7eafb-104">Возвращает перечислитель для кэшированных среда выполнения Windowsных типов в домене приложения на основе их идентификаторов интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="7eafb-104">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eafb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7eafb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7eafb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7eafb-106">Parameters</span></span>  

 `cReqTypes`  
 <span data-ttu-id="7eafb-107">окне Число обязательных типов.</span><span class="sxs-lookup"><span data-stu-id="7eafb-107">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="7eafb-108">окне Указатель на массив, содержащий идентификаторы интерфейса, соответствующие управляемым представлениям возвращаемых типов среда выполнения Windows.</span><span class="sxs-lookup"><span data-stu-id="7eafb-108">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="7eafb-109">заполняет Указатель на адрес объекта "ICorDebugTypeEnum" интерфейса, который позволяет перечислить кэшированные управляемые представления возвращаемых типов среда выполнения Windows на основе идентификаторов интерфейса в `iidsToResolve` .</span><span class="sxs-lookup"><span data-stu-id="7eafb-109">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7eafb-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="7eafb-110">Remarks</span></span>  

 <span data-ttu-id="7eafb-111">Если методу не удается получить сведения для определенного идентификатора интерфейса, соответствующая запись в коллекции "ICorDebugTypeEnum" будет иметь тип `ELEMENT_TYPE_END` для ошибок из-за проблем, связанных с получением данных, или `ELEMENT_TYPE_VOID` для неизвестных идентификаторов интерфейса.</span><span class="sxs-lookup"><span data-stu-id="7eafb-111">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eafb-112">Требования</span><span class="sxs-lookup"><span data-stu-id="7eafb-112">Requirements</span></span>  

 <span data-ttu-id="7eafb-113">**Платформы:** среда выполнения Windows</span><span class="sxs-lookup"><span data-stu-id="7eafb-113">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="7eafb-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7eafb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7eafb-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7eafb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7eafb-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eafb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eafb-117">См. также</span><span class="sxs-lookup"><span data-stu-id="7eafb-117">See also</span></span>

- [<span data-ttu-id="7eafb-118">Интерфейс ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="7eafb-118">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
