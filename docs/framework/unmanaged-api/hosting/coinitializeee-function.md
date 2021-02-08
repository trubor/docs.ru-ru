---
description: 'Дополнительные сведения: функция CoInitialize'
title: Функция CoInitializeEE
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
ms.openlocfilehash: 9664324c569ed4de73262491cf8eda8296b3c3a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799828"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="a01ec-103">Функция CoInitializeEE</span><span class="sxs-lookup"><span data-stu-id="a01ec-103">CoInitializeEE Function</span></span>

<span data-ttu-id="a01ec-104">Гарантирует, что подсистема выполнения среды CLR загружается в процесс.</span><span class="sxs-lookup"><span data-stu-id="a01ec-104">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="a01ec-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a01ec-105">This function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="a01ec-106">Используйте вместо этого метод [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a01ec-106">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a01ec-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a01ec-107">Syntax</span></span>  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a01ec-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="a01ec-108">Parameters</span></span>  

 `fFlags`  
 <span data-ttu-id="a01ec-109">окне Одна из констант перечисления [коинитии](../metadata/coinitiee-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="a01ec-109">[in] One of the [COINITIEE](../metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a01ec-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a01ec-110">Return Value</span></span>  

 <span data-ttu-id="a01ec-111">Этот метод возвращает стандартные коды ошибок COM, определенные в файле Winerror. h, и значения, приведенные в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="a01ec-111">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="a01ec-112">Код возврата</span><span class="sxs-lookup"><span data-stu-id="a01ec-112">Return code</span></span>|<span data-ttu-id="a01ec-113">Описание</span><span class="sxs-lookup"><span data-stu-id="a01ec-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a01ec-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a01ec-114">S_OK</span></span>|<span data-ttu-id="a01ec-115">Подсистема выполнения успешно загружена.</span><span class="sxs-lookup"><span data-stu-id="a01ec-115">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="a01ec-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a01ec-116">S_FALSE</span></span>|<span data-ttu-id="a01ec-117">Подсистема выполнения уже загружена.</span><span class="sxs-lookup"><span data-stu-id="a01ec-117">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="a01ec-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a01ec-118">E_FAIL</span></span>|<span data-ttu-id="a01ec-119">Не удалось загрузить подсистему выполнения.</span><span class="sxs-lookup"><span data-stu-id="a01ec-119">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a01ec-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="a01ec-120">Remarks</span></span>  

 <span data-ttu-id="a01ec-121">Этот метод загружает подсистему выполнения, если он не был загружен ранее.</span><span class="sxs-lookup"><span data-stu-id="a01ec-121">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a01ec-122">Требования</span><span class="sxs-lookup"><span data-stu-id="a01ec-122">Requirements</span></span>  

 <span data-ttu-id="a01ec-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a01ec-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a01ec-124">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="a01ec-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a01ec-125">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a01ec-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a01ec-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a01ec-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a01ec-127">См. также</span><span class="sxs-lookup"><span data-stu-id="a01ec-127">See also</span></span>

- [<span data-ttu-id="a01ec-128">Глобальные статические функции метаданных</span><span class="sxs-lookup"><span data-stu-id="a01ec-128">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
