---
description: 'Дополнительные сведения о: структура Стакковерфловинфо'
title: Структура StackOverflowInfo
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
ms.openlocfilehash: cca65e4293c05b89ebefc3c6dd36a6b8898eb15f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679398"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="37602-103">Структура StackOverflowInfo</span><span class="sxs-lookup"><span data-stu-id="37602-103">StackOverflowInfo Structure</span></span>

<span data-ttu-id="37602-104">Хранит тип произошедшего переполнения и сведения об исключении, порождаемом из-за переполнения.</span><span class="sxs-lookup"><span data-stu-id="37602-104">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37602-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="37602-105">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="37602-106">Члены</span><span class="sxs-lookup"><span data-stu-id="37602-106">Members</span></span>  
  
|<span data-ttu-id="37602-107">Член</span><span class="sxs-lookup"><span data-stu-id="37602-107">Member</span></span>|<span data-ttu-id="37602-108">Описание</span><span class="sxs-lookup"><span data-stu-id="37602-108">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="37602-109">Значение перечисления [StackOverflowType](stackoverflowtype-enumeration.md) , указывающее тип переполнения.</span><span class="sxs-lookup"><span data-stu-id="37602-109">A value of the [StackOverflowType](stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="37602-110">Указатель на `EXCEPTION_POINTERS` объект Win32, который содержит запись исключения с независимым от компьютера описанием исключения и записью контекста с зависящим от компьютера описанием контекста процессора на момент возникновения исключения.</span><span class="sxs-lookup"><span data-stu-id="37602-110">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37602-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="37602-111">Remarks</span></span>  

 <span data-ttu-id="37602-112">`StackOverflowInfo`Объект передается в метод [иактиононклревент:: oneven](iactiononclrevent-onevent-method.md) для `Event_StackOverflow` событий.</span><span class="sxs-lookup"><span data-stu-id="37602-112">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37602-113">Требования</span><span class="sxs-lookup"><span data-stu-id="37602-113">Requirements</span></span>  

 <span data-ttu-id="37602-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37602-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37602-115">**Заголовок:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="37602-115">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="37602-116">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="37602-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37602-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37602-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37602-118">См. также</span><span class="sxs-lookup"><span data-stu-id="37602-118">See also</span></span>

- [<span data-ttu-id="37602-119">Структуры размещения</span><span class="sxs-lookup"><span data-stu-id="37602-119">Hosting Structures</span></span>](hosting-structures.md)
