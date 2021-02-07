---
description: 'Дополнительные сведения о методе: IValidator:: FormatEventInfo'
title: Метод IValidator::FormatEventInfo
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
ms.openlocfilehash: 28ecf9ab2b14cd2fdd178a4ad9d8e218f7038a9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680165"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="d0db4-103">Метод IValidator::FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="d0db4-103">IValidator::FormatEventInfo Method</span></span>

<span data-ttu-id="d0db4-104">Возвращает сообщение об ошибке, соответствующее указанной ошибке проверки.</span><span class="sxs-lookup"><span data-stu-id="d0db4-104">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0db4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d0db4-105">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0db4-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d0db4-106">Parameters</span></span>  

 `hVECode`  
 <span data-ttu-id="d0db4-107">окне Значение HRESULT, которое было передано обработчику ошибок проверки.</span><span class="sxs-lookup"><span data-stu-id="d0db4-107">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="d0db4-108">окне `VEContext` Экземпляр, содержащий контекстные сведения об ошибке проверки.</span><span class="sxs-lookup"><span data-stu-id="d0db4-108">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="d0db4-109">[вход, выход] Строка, содержащая возвращенное сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="d0db4-109">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="d0db4-110">окне Максимальная длина сообщения об ошибке.</span><span class="sxs-lookup"><span data-stu-id="d0db4-110">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="d0db4-111">окне Защищенный массив, содержащий дополнительные параметры, описывающие ошибку.</span><span class="sxs-lookup"><span data-stu-id="d0db4-111">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0db4-112">Требования</span><span class="sxs-lookup"><span data-stu-id="d0db4-112">Requirements</span></span>  

 <span data-ttu-id="d0db4-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0db4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0db4-114">**Заголовок:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="d0db4-114">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="d0db4-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0db4-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0db4-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0db4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
