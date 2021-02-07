---
description: 'Дополнительные сведения о методе: ICorDebugGuidToTypeEnum:: Next'
title: Метод ICorDebugGuidToTypeEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
ms.openlocfilehash: 0ab05cc0689c76c0bb185205ea00c5ccebfcbe03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661003"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="61795-103">Метод ICorDebugGuidToTypeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="61795-103">ICorDebugGuidToTypeEnum::Next Method</span></span>

<span data-ttu-id="61795-104">Возвращает указанное число экземпляров [кордебуггуидтотипемаппинг](cordebugguidtotypemapping-structure.md) , которые сопоставляют идентификаторы GUID со сведениями о типе.</span><span class="sxs-lookup"><span data-stu-id="61795-104">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61795-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="61795-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61795-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="61795-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="61795-107">окне Число получаемых объектов сопоставления GUID и типа.</span><span class="sxs-lookup"><span data-stu-id="61795-107">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="61795-108">заполняет Массив указателей, каждый из которых указывает на объект [кордебуггуидтотипемаппинг](cordebugguidtotypemapping-structure.md) , который сопоставляет идентификатор GUID среда выполнения Windows с соответствующим объектом ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="61795-108">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="61795-109">заполняет Указатель на число объектов [кордебуггуидтотипемаппинг](cordebugguidtotypemapping-structure.md) , фактически возвращаемых в `values` .</span><span class="sxs-lookup"><span data-stu-id="61795-109">[out] A pointer to the number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61795-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="61795-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61795-111">Требования</span><span class="sxs-lookup"><span data-stu-id="61795-111">Requirements</span></span>  

 <span data-ttu-id="61795-112">**Платформы:** среда выполнения Windows</span><span class="sxs-lookup"><span data-stu-id="61795-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="61795-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61795-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61795-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61795-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61795-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61795-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61795-116">См. также</span><span class="sxs-lookup"><span data-stu-id="61795-116">See also</span></span>

- [<span data-ttu-id="61795-117">Интерфейс ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="61795-117">ICorDebugGuidToTypeEnum Interface</span></span>](icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="61795-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="61795-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
