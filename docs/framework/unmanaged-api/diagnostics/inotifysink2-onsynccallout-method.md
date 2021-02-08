---
description: 'Дополнительные сведения о методе: INotifySink2:: OnSyncCallOut'
title: Метод INotifySink2::OnSyncCallOut
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
ms.openlocfilehash: 03028b138a7d95c618ae20530f66aa692d314cab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800244"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="b409e-103">Метод INotifySink2::OnSyncCallOut</span><span class="sxs-lookup"><span data-stu-id="b409e-103">INotifySink2::OnSyncCallOut Method</span></span>

<span data-ttu-id="b409e-104">Вызывается, когда вызывается метод out.</span><span class="sxs-lookup"><span data-stu-id="b409e-104">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b409e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b409e-105">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b409e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b409e-106">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="b409e-107">окне Идентификатор выходного вызова. См. раздел [структура CALL_ID](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="b409e-107">[in] ID of the call that is out. See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="b409e-108">заполняет Буфер вызова.</span><span class="sxs-lookup"><span data-stu-id="b409e-108">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="b409e-109">заполняет Размер буфера вызова в байтах.</span><span class="sxs-lookup"><span data-stu-id="b409e-109">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b409e-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b409e-110">Return Value</span></span>  

 <span data-ttu-id="b409e-111">S_OK, если метод выполнен.</span><span class="sxs-lookup"><span data-stu-id="b409e-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b409e-112">Требования</span><span class="sxs-lookup"><span data-stu-id="b409e-112">Requirements</span></span>  

 <span data-ttu-id="b409e-113">**Заголовок:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="b409e-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b409e-114">См. также</span><span class="sxs-lookup"><span data-stu-id="b409e-114">See also</span></span>

- [<span data-ttu-id="b409e-115">Интерфейс INotifySink2</span><span class="sxs-lookup"><span data-stu-id="b409e-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="b409e-116">Интерфейс INotifySource2</span><span class="sxs-lookup"><span data-stu-id="b409e-116">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="b409e-117">Интерфейс INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="b409e-117">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
