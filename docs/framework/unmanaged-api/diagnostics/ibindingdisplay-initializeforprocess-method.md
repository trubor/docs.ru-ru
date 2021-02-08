---
description: 'Дополнительные сведения о методе: Ибиндингдисплай:: Инитиализефорпроцесс'
title: Метод IBindingDisplay::InitializeForProcess
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
ms.openlocfilehash: cf7f0f4d057659089bd7da173e5fac98a7c00dad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800415"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="d2358-103">Метод IBindingDisplay::InitializeForProcess</span><span class="sxs-lookup"><span data-stu-id="d2358-103">IBindingDisplay::InitializeForProcess Method</span></span>

<span data-ttu-id="d2358-104">Инициализирует объект [ибиндингдисплай](ibindingdisplay-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d2358-104">Initializes the [IBindingDisplay](ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2358-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d2358-105">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2358-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d2358-106">Parameters</span></span>  

 `pid`  
 <span data-ttu-id="d2358-107">окне Идентификатор процесса.</span><span class="sxs-lookup"><span data-stu-id="d2358-107">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2358-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="d2358-108">Remarks</span></span>  

 <span data-ttu-id="d2358-109">Отладчик вызывает `InitializeForProcess` метод во время создания, чтобы инициализировать отображение привязки.</span><span class="sxs-lookup"><span data-stu-id="d2358-109">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="d2358-110">`InitializeForProcess` должен вызываться во время создания до вызова любого другого метода `IBindingDisplay` .</span><span class="sxs-lookup"><span data-stu-id="d2358-110">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2358-111">Требования</span><span class="sxs-lookup"><span data-stu-id="d2358-111">Requirements</span></span>  

 <span data-ttu-id="d2358-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2358-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2358-113">**Заголовок:** Биндингдисплай. h</span><span class="sxs-lookup"><span data-stu-id="d2358-113">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="d2358-114">**Библиотека:** Биндингдисплай. idl</span><span class="sxs-lookup"><span data-stu-id="d2358-114">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="d2358-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2358-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2358-116">См. также</span><span class="sxs-lookup"><span data-stu-id="d2358-116">See also</span></span>

- [<span data-ttu-id="d2358-117">Интерфейс IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="d2358-117">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
