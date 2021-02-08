---
description: 'Дополнительные сведения о методе: Ибиндингдисплай:: Жеткуррентдисплай'
title: Метод IBindingDisplay::GetCurrentDisplay
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
ms.openlocfilehash: 680a91c8025ac3247701c14c23f442da5e304ecb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800426"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="db0c0-103">Метод IBindingDisplay::GetCurrentDisplay</span><span class="sxs-lookup"><span data-stu-id="db0c0-103">IBindingDisplay::GetCurrentDisplay Method</span></span>

<span data-ttu-id="db0c0-104">Возвращает текущие отображаемые сведения о привязке.</span><span class="sxs-lookup"><span data-stu-id="db0c0-104">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db0c0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="db0c0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db0c0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="db0c0-106">Parameters</span></span>  

 `display`  
 <span data-ttu-id="db0c0-107">[out, retval] Указатель на массив SafeArray, содержащий сведения, отображаемые при привязке.</span><span class="sxs-lookup"><span data-stu-id="db0c0-107">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db0c0-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="db0c0-108">Remarks</span></span>  

 <span data-ttu-id="db0c0-109">Метод [ибиндингдисплай:: инитиализефорпроцесс](ibindingdisplay-initializeforprocess-method.md) должен быть ранее успешно завершен, и программа должна быть остановлена отладчиком.</span><span class="sxs-lookup"><span data-stu-id="db0c0-109">The [IBindingDisplay::InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="db0c0-110">Вызывающий объект должен освободить возвращенную `SAFEARRAY` память с помощью [сафеаррайдестрой](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="db0c0-110">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db0c0-111">Требования</span><span class="sxs-lookup"><span data-stu-id="db0c0-111">Requirements</span></span>  

 <span data-ttu-id="db0c0-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db0c0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db0c0-113">**Заголовок:** Биндингдисплай. h</span><span class="sxs-lookup"><span data-stu-id="db0c0-113">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="db0c0-114">**Библиотека:** Биндингдисплай. idl</span><span class="sxs-lookup"><span data-stu-id="db0c0-114">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="db0c0-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db0c0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db0c0-116">См. также</span><span class="sxs-lookup"><span data-stu-id="db0c0-116">See also</span></span>

- [<span data-ttu-id="db0c0-117">Интерфейс IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="db0c0-117">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
- [<span data-ttu-id="db0c0-118">Метод InitializeForProcess</span><span class="sxs-lookup"><span data-stu-id="db0c0-118">InitializeForProcess Method</span></span>](ibindingdisplay-initializeforprocess-method.md)
