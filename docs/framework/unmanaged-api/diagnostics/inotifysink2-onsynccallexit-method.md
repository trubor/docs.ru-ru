---
description: 'Дополнительные сведения о методе: INotifySink2:: Онсинккаллексит'
title: Метод INotifySink2::OnSyncCallExit
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallExit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type:
- apiref
ms.openlocfilehash: 2de55c3b7956576049e4ad65b2cb6fbc69fa84af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800270"
---
# <a name="inotifysink2onsynccallexit-method"></a><span data-ttu-id="237d4-103">Метод INotifySink2::OnSyncCallExit</span><span class="sxs-lookup"><span data-stu-id="237d4-103">INotifySink2::OnSyncCallExit Method</span></span>

<span data-ttu-id="237d4-104">Вызывается при выходе из вызова.</span><span class="sxs-lookup"><span data-stu-id="237d4-104">Gets invoked when exiting a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="237d4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="237d4-105">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="237d4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="237d4-106">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="237d4-107">окне Идентификатор выходного вызова.</span><span class="sxs-lookup"><span data-stu-id="237d4-107">[in] ID of the call being exited.</span></span> <span data-ttu-id="237d4-108">См. раздел [структура CALL_ID](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="237d4-108">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="237d4-109">заполняет Буфер вызова.</span><span class="sxs-lookup"><span data-stu-id="237d4-109">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="237d4-110">заполняет Размер буфера вызова в байтах.</span><span class="sxs-lookup"><span data-stu-id="237d4-110">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="237d4-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="237d4-111">Return Value</span></span>  

 <span data-ttu-id="237d4-112">S_OK, если метод выполнен.</span><span class="sxs-lookup"><span data-stu-id="237d4-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="237d4-113">Требования</span><span class="sxs-lookup"><span data-stu-id="237d4-113">Requirements</span></span>  

 <span data-ttu-id="237d4-114">**Заголовок:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="237d4-114">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="237d4-115">См. также</span><span class="sxs-lookup"><span data-stu-id="237d4-115">See also</span></span>

- [<span data-ttu-id="237d4-116">Интерфейс INotifySink2</span><span class="sxs-lookup"><span data-stu-id="237d4-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="237d4-117">Интерфейс INotifySource2</span><span class="sxs-lookup"><span data-stu-id="237d4-117">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="237d4-118">Интерфейс INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="237d4-118">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
