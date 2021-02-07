---
description: 'Дополнительные сведения: перечисление NOTIFY_FILTER'
title: Перечисление NOTIFY_FILTER
ms.date: 03/30/2017
api_name:
- NOTIFY_FILTER
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- NOTIFY_FILTER
helpviewer_keywords:
- NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type:
- apiref
ms.openlocfilehash: 0ed09af0af302b08102b7b08fa72a2d255c5b231
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761490"
---
# <a name="notify_filter-enumeration"></a><span data-ttu-id="ab97b-103">Перечисление NOTIFY_FILTER</span><span class="sxs-lookup"><span data-stu-id="ab97b-103">NOTIFY_FILTER Enumeration</span></span>

<span data-ttu-id="ab97b-104">Определяет обратные вызовы для функций отладчика.</span><span class="sxs-lookup"><span data-stu-id="ab97b-104">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="ab97b-105">Дополнительные сведения см. в описании метода [INotifySource2:: сетнотифифилтер](inotifysource2-setnotifyfilter-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ab97b-105">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab97b-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ab97b-106">Syntax</span></span>  
  
```cpp  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a><span data-ttu-id="ab97b-107">Члены</span><span class="sxs-lookup"><span data-stu-id="ab97b-107">Members</span></span>  
  
|<span data-ttu-id="ab97b-108">Член</span><span class="sxs-lookup"><span data-stu-id="ab97b-108">Member</span></span>|<span data-ttu-id="ab97b-109">Описание</span><span class="sxs-lookup"><span data-stu-id="ab97b-109">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="ab97b-110">Указывает, что должен быть вызван метод [INotifySink2:: OnSyncCallOut](inotifysink2-onsynccallout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ab97b-110">Indicates that the [INotifySink2::OnSyncCallOut](inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="ab97b-111">Указывает, что должен быть вызван метод [INotifySink2:: OnSyncCallEnter](inotifysink2-onsynccallenter-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ab97b-111">Indicates that the [INotifySink2::OnSyncCallEnter](inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="ab97b-112">Указывает, что должен быть вызван метод [INotifySink2:: онсинккаллексит](inotifysink2-onsynccallexit-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ab97b-112">Indicates that the [INotifySink2::OnSyncCallExit](inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="ab97b-113">Указывает, что должен быть вызван метод [INotifySink2:: онсинккаллретурн](inotifysink2-onsynccallreturn-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ab97b-113">Indicates that the [INotifySink2::OnSyncCallReturn](inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="ab97b-114">Указывает, что должны быть вызваны все методы [INotifySink2](inotifysink2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ab97b-114">Indicates that all of the [INotifySink2](inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="ab97b-115">Активирует все существующие и будущие уведомления.</span><span class="sxs-lookup"><span data-stu-id="ab97b-115">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="ab97b-116">Указывает, что методы уведомления вызывать не нужно.</span><span class="sxs-lookup"><span data-stu-id="ab97b-116">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab97b-117">Требования</span><span class="sxs-lookup"><span data-stu-id="ab97b-117">Requirements</span></span>  

 <span data-ttu-id="ab97b-118">**Заголовок:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="ab97b-118">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab97b-119">См. также</span><span class="sxs-lookup"><span data-stu-id="ab97b-119">See also</span></span>

- [<span data-ttu-id="ab97b-120">Перечисления хранилища символов диагностики</span><span class="sxs-lookup"><span data-stu-id="ab97b-120">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
