---
description: Дополнительные сведения о перечислении Кордебугрекордформат
title: Перечисление CorDebugRecordFormat
ms.date: 03/30/2017
api_name:
- CorDebugRecordFormat
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type:
- apiref
ms.openlocfilehash: 856522497a8f858abdb39ac232fb3034d4d91dfc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801570"
---
# <a name="cordebugrecordformat-enumeration"></a><span data-ttu-id="8babc-103">Перечисление CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="8babc-103">CorDebugRecordFormat Enumeration</span></span>

<span data-ttu-id="8babc-104">Описывает формат данных в массиве байтов, который содержит информацию о событии отладки собственного исключения.</span><span class="sxs-lookup"><span data-stu-id="8babc-104">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8babc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8babc-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="8babc-106">Члены</span><span class="sxs-lookup"><span data-stu-id="8babc-106">Members</span></span>  
  
|<span data-ttu-id="8babc-107">Член</span><span class="sxs-lookup"><span data-stu-id="8babc-107">Member</span></span>|<span data-ttu-id="8babc-108">Описание</span><span class="sxs-lookup"><span data-stu-id="8babc-108">Description</span></span>|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|<span data-ttu-id="8babc-109">Данные представляют собой 32-разрядную запись Windows-исключения.</span><span class="sxs-lookup"><span data-stu-id="8babc-109">The data is a 32-bit Windows exception record.</span></span>|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|<span data-ttu-id="8babc-110">Данные представляют собой 64-разрядную запись Windows-исключения.</span><span class="sxs-lookup"><span data-stu-id="8babc-110">The data is a 64-bit Windows exception record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8babc-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="8babc-111">Remarks</span></span>  

 <span data-ttu-id="8babc-112">Член `CorDebugRecordFormat` перечисления передается в метод [DecodeEvent](icordebugprocess6-decodeevent-method.md) для указания формата массива байтов в его `pRecord` аргументе.</span><span class="sxs-lookup"><span data-stu-id="8babc-112">A member of the `CorDebugRecordFormat` enumeration is passed to the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method to indicate the format of the byte array in its `pRecord` argument.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8babc-113">Это перечисление предназначено для использования только в сценариях отладки .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8babc-113">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8babc-114">Требования</span><span class="sxs-lookup"><span data-stu-id="8babc-114">Requirements</span></span>  

 <span data-ttu-id="8babc-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8babc-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8babc-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8babc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8babc-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8babc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8babc-118">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8babc-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8babc-119">См. также</span><span class="sxs-lookup"><span data-stu-id="8babc-119">See also</span></span>

- [<span data-ttu-id="8babc-120">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="8babc-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
