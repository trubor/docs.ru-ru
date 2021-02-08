---
description: 'Дополнительные сведения о методе: INotifyConnection2:: Регистернотифисаурце'
title: Метод INotifyConnection2::RegisterNotifySource
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
ms.openlocfilehash: 97aacf7f2005a1e9f21acebd6c5f5ed65867b245
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800322"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="064db-103">Метод INotifyConnection2::RegisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="064db-103">INotifyConnection2::RegisterNotifySource Method</span></span>

<span data-ttu-id="064db-104">Устанавливает указанный источник уведомления.</span><span class="sxs-lookup"><span data-stu-id="064db-104">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="064db-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="064db-105">Syntax</span></span>  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="064db-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="064db-106">Parameters</span></span>  

 `in_pNotifySource`  
 <span data-ttu-id="064db-107">окне Указывает объект, который будет использоваться в качестве источника уведомления.</span><span class="sxs-lookup"><span data-stu-id="064db-107">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="064db-108">заполняет Получает объект, который будет использоваться в качестве приемника уведомлений.</span><span class="sxs-lookup"><span data-stu-id="064db-108">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="064db-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="064db-109">Return Value</span></span>  

 <span data-ttu-id="064db-110">S_OK, если метод выполнен.</span><span class="sxs-lookup"><span data-stu-id="064db-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="064db-111">Требования</span><span class="sxs-lookup"><span data-stu-id="064db-111">Requirements</span></span>  

 <span data-ttu-id="064db-112">**Заголовок:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="064db-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="064db-113">См. также</span><span class="sxs-lookup"><span data-stu-id="064db-113">See also</span></span>

- [<span data-ttu-id="064db-114">Интерфейс INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="064db-114">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="064db-115">Интерфейс INotifySource2</span><span class="sxs-lookup"><span data-stu-id="064db-115">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="064db-116">Интерфейс INotifySink2</span><span class="sxs-lookup"><span data-stu-id="064db-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="064db-117">Метод UnregisterNotifySource</span><span class="sxs-lookup"><span data-stu-id="064db-117">UnregisterNotifySource Method</span></span>](inotifyconnection2-unregisternotifysource-method.md)
