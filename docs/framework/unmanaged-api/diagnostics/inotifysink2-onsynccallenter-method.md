---
description: 'Дополнительные сведения о методе: INotifySink2:: OnSyncCallEnter'
title: Метод INotifySink2::OnSyncCallEnter
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallEnter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallEnter
helpviewer_keywords:
- INotifySink2::OnSyncCallEnter method [.NET Framework debugging]
- OnSyncCallEnter method [.NET Framework debugging]
ms.assetid: e33265be-c25d-4145-ad02-c3e89d6f26c1
topic_type:
- apiref
ms.openlocfilehash: e7537b16ec8ea8d92ad92498c1bfdac5a9de6475
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800283"
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="8ca93-103">Метод INotifySink2::OnSyncCallEnter</span><span class="sxs-lookup"><span data-stu-id="8ca93-103">INotifySink2::OnSyncCallEnter Method</span></span>

<span data-ttu-id="8ca93-104">Вызывается при вводе вызова.</span><span class="sxs-lookup"><span data-stu-id="8ca93-104">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca93-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8ca93-105">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ca93-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8ca93-106">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="8ca93-107">окне Идентификатор вводимых вызовов.</span><span class="sxs-lookup"><span data-stu-id="8ca93-107">[in] ID of the call being entered.</span></span> <span data-ttu-id="8ca93-108">См. раздел [структура CALL_ID](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="8ca93-108">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="8ca93-109">окне Буфер вызова.</span><span class="sxs-lookup"><span data-stu-id="8ca93-109">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="8ca93-110">окне Размер буфера вызова в байтах.</span><span class="sxs-lookup"><span data-stu-id="8ca93-110">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ca93-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="8ca93-111">Return Value</span></span>  

 <span data-ttu-id="8ca93-112">S_OK, если метод выполнен.</span><span class="sxs-lookup"><span data-stu-id="8ca93-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ca93-113">Требования</span><span class="sxs-lookup"><span data-stu-id="8ca93-113">Requirements</span></span>  

 <span data-ttu-id="8ca93-114">**Заголовок:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="8ca93-114">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca93-115">См. также</span><span class="sxs-lookup"><span data-stu-id="8ca93-115">See also</span></span>

- [<span data-ttu-id="8ca93-116">Интерфейс INotifySink2</span><span class="sxs-lookup"><span data-stu-id="8ca93-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="8ca93-117">Интерфейс INotifySource2</span><span class="sxs-lookup"><span data-stu-id="8ca93-117">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="8ca93-118">Интерфейс INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="8ca93-118">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
