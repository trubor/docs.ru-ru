---
description: 'Дополнительные сведения о методе: INotifyConnection2:: Унрегистернотифисаурце'
title: Метод INotifyConnection2::UnregisterNotifySource
ms.date: 03/30/2017
api_name:
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
ms.openlocfilehash: d3b82665375f54d33b6a5581241788d828060a83
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800309"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="8a756-103">Метод INotifyConnection2::UnregisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="8a756-103">INotifyConnection2::UnregisterNotifySource Method</span></span>

<span data-ttu-id="8a756-104">Удаляет указанный объект источника уведомления из соединения.</span><span class="sxs-lookup"><span data-stu-id="8a756-104">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a756-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8a756-105">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a756-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8a756-106">Parameters</span></span>  

 `in_pNotifySource`  
 <span data-ttu-id="8a756-107">окне Отменяется регистрация объекта уведомления.</span><span class="sxs-lookup"><span data-stu-id="8a756-107">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a756-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8a756-108">Return Value</span></span>  

 <span data-ttu-id="8a756-109">S_OK, если метод выполнен.</span><span class="sxs-lookup"><span data-stu-id="8a756-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a756-110">Требования</span><span class="sxs-lookup"><span data-stu-id="8a756-110">Requirements</span></span>  

 <span data-ttu-id="8a756-111">**Заголовок:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="8a756-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a756-112">См. также</span><span class="sxs-lookup"><span data-stu-id="8a756-112">See also</span></span>

- [<span data-ttu-id="8a756-113">Интерфейс INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="8a756-113">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="8a756-114">Интерфейс INotifySource2</span><span class="sxs-lookup"><span data-stu-id="8a756-114">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="8a756-115">Интерфейс INotifySink2</span><span class="sxs-lookup"><span data-stu-id="8a756-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="8a756-116">Метод RegisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="8a756-116">RegisterNotifySource Method</span></span>](inotifyconnection2-registernotifysource-method.md)
