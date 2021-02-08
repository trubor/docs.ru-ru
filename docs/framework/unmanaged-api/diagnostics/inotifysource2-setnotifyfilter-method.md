---
description: 'Дополнительные сведения о методе: INotifySource2:: Сетнотифифилтер'
title: Метод INotifySource2::SetNotifyFilter
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
ms.openlocfilehash: 2aaf2a5253f8a9acb67c4b538f109a7a62559d12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800231"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="a783a-103">Метод INotifySource2::SetNotifyFilter</span><span class="sxs-lookup"><span data-stu-id="a783a-103">INotifySource2::SetNotifyFilter Method</span></span>

<span data-ttu-id="a783a-104">Назначает фильтр уведомлений для использования с этим источником.</span><span class="sxs-lookup"><span data-stu-id="a783a-104">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a783a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a783a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a783a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a783a-106">Parameters</span></span>  

 `in_NotifyFilter`  
 <span data-ttu-id="a783a-107">окне Побитовое сочетание значений перечисления [NOTIFY_FILTER](notify-filter-enumeration.md) , которые указывают обратные вызовы для API отладчика.</span><span class="sxs-lookup"><span data-stu-id="a783a-107">[in] A bitwise combination of the [NOTIFY_FILTER](notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="a783a-108">окне Указатель на структуру [USER_THREAD](user-thread-structure.md) , которая идентифицирует потоки для API отладчика.</span><span class="sxs-lookup"><span data-stu-id="a783a-108">[in] A pointer to a [USER_THREAD](user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a783a-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a783a-109">Return Value</span></span>  

 <span data-ttu-id="a783a-110">S_OK, если метод выполнен.</span><span class="sxs-lookup"><span data-stu-id="a783a-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a783a-111">Требования</span><span class="sxs-lookup"><span data-stu-id="a783a-111">Requirements</span></span>  

 <span data-ttu-id="a783a-112">**Заголовок:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="a783a-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a783a-113">См. также</span><span class="sxs-lookup"><span data-stu-id="a783a-113">See also</span></span>

- [<span data-ttu-id="a783a-114">Интерфейс INotifySource2</span><span class="sxs-lookup"><span data-stu-id="a783a-114">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="a783a-115">Интерфейс INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="a783a-115">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="a783a-116">Интерфейс INotifySink2</span><span class="sxs-lookup"><span data-stu-id="a783a-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
