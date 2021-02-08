---
description: 'Дополнительные сведения о методе: INotifySink2:: Онсинккаллретурн'
title: Метод INotifySink2::OnSyncCallReturn
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallReturn
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type:
- apiref
ms.openlocfilehash: 01518de4e5a9e1374edddadb3c49f16e8fe679a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800257"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="33d4c-103">Метод INotifySink2::OnSyncCallReturn</span><span class="sxs-lookup"><span data-stu-id="33d4c-103">INotifySink2::OnSyncCallReturn Method</span></span>

<span data-ttu-id="33d4c-104">Вызывается при возвращении вызова.</span><span class="sxs-lookup"><span data-stu-id="33d4c-104">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33d4c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="33d4c-105">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33d4c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="33d4c-106">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="33d4c-107">окне Идентификатор возвращаемого вызова.</span><span class="sxs-lookup"><span data-stu-id="33d4c-107">[in] ID of the call being returned from.</span></span> <span data-ttu-id="33d4c-108">См. раздел [структура CALL_ID](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="33d4c-108">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="33d4c-109">окне Буфер вызова.</span><span class="sxs-lookup"><span data-stu-id="33d4c-109">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="33d4c-110">окне Размер буфера вызова в байтах.</span><span class="sxs-lookup"><span data-stu-id="33d4c-110">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33d4c-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="33d4c-111">Return Value</span></span>  

 <span data-ttu-id="33d4c-112">S_OK, если метод выполнен.</span><span class="sxs-lookup"><span data-stu-id="33d4c-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33d4c-113">Требования</span><span class="sxs-lookup"><span data-stu-id="33d4c-113">Requirements</span></span>  

 <span data-ttu-id="33d4c-114">**Заголовок:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="33d4c-114">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33d4c-115">См. также</span><span class="sxs-lookup"><span data-stu-id="33d4c-115">See also</span></span>

- [<span data-ttu-id="33d4c-116">Интерфейс INotifySink2</span><span class="sxs-lookup"><span data-stu-id="33d4c-116">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="33d4c-117">Интерфейс INotifySource2</span><span class="sxs-lookup"><span data-stu-id="33d4c-117">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="33d4c-118">Интерфейс INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="33d4c-118">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
