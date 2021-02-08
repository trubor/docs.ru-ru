---
description: Дополнительные сведения о функции GetCLRIdentityManager
title: Функция GetCLRIdentityManager
ms.date: 03/30/2017
api_name:
- GetCLRIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetCLRIdentityManager
helpviewer_keywords:
- GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type:
- apiref
ms.openlocfilehash: 483cf0499fa162da4c89e350198a5609f9f1bab6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785371"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="28aa5-103">Функция GetCLRIdentityManager</span><span class="sxs-lookup"><span data-stu-id="28aa5-103">GetCLRIdentityManager Function</span></span>

<span data-ttu-id="28aa5-104">Возвращает указатель на интерфейс, который позволяет среде CLR управлять удостоверениями.</span><span class="sxs-lookup"><span data-stu-id="28aa5-104">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="28aa5-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="28aa5-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28aa5-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="28aa5-106">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28aa5-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="28aa5-107">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="28aa5-108">окне Объект `REFIID` (идентификатор интерфейса), указывающий, какой интерфейс следует получить.</span><span class="sxs-lookup"><span data-stu-id="28aa5-108">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="28aa5-109">Это значение должно быть либо IID_ICLRAssemblyIdentityManager, либо IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="28aa5-109">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="28aa5-110">заполняет Указатель на адрес объекта [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) или [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="28aa5-110">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28aa5-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="28aa5-111">Remarks</span></span>  

 <span data-ttu-id="28aa5-112">Вызовите функцию [жетреалпрокаддресс](getrealprocaddress-function.md) , чтобы получить указатель на `GetCLRIdentityManager` функцию.</span><span class="sxs-lookup"><span data-stu-id="28aa5-112">Call the [GetRealProcAddress](getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28aa5-113">Требования</span><span class="sxs-lookup"><span data-stu-id="28aa5-113">Requirements</span></span>  

 <span data-ttu-id="28aa5-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28aa5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28aa5-115">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="28aa5-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28aa5-116">**Библиотека:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="28aa5-116">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="28aa5-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28aa5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28aa5-118">См. также</span><span class="sxs-lookup"><span data-stu-id="28aa5-118">See also</span></span>

- [<span data-ttu-id="28aa5-119">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="28aa5-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
