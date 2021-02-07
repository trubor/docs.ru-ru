---
description: 'Дополнительные сведения о методе: Iclrerrorreportingmanagergetbucketparametersforcurrentexception:: Жетбуккетпараметерсфоркуррентексцептион'
title: Метод ICLRErrorReportingManager::GetBucketParametersForCurrentException
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.GetBucketParametersForCurrentException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException
helpviewer_keywords:
- ICLRErrorReportingManager::GetBucketParametersForCurrentException method [.NET Framework hosting]
- GetBucketParametersForCurrentException method [.NET Framework hosting]
ms.assetid: a13ec8a6-8e18-4acb-8054-77f5b1a0e0b9
topic_type:
- apiref
ms.openlocfilehash: ba2b6cf1215e5d57f608a76a870b0a9c846ee8ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689408"
---
# <a name="iclrerrorreportingmanagergetbucketparametersforcurrentexception-method"></a><span data-ttu-id="79753-103">Метод ICLRErrorReportingManager::GetBucketParametersForCurrentException</span><span class="sxs-lookup"><span data-stu-id="79753-103">ICLRErrorReportingManager::GetBucketParametersForCurrentException Method</span></span>

<span data-ttu-id="79753-104">Возвращает контейнер Watson для текущего исключения в вызывающем потоке.</span><span class="sxs-lookup"><span data-stu-id="79753-104">Gets the Watson bucket for the current exception on the calling thread.</span></span>  
  
 <span data-ttu-id="79753-105">*Контейнер* — это коллекция данных об ошибках, которая связана с тем же дефектом кода.</span><span class="sxs-lookup"><span data-stu-id="79753-105">A *bucket* is a collection of error data that is related to the same code defect.</span></span> <span data-ttu-id="79753-106">*Watson* относится к набору технологий для сбора и анализа данных, связанных с исключением.</span><span class="sxs-lookup"><span data-stu-id="79753-106">*Watson* refers to a set of technologies for collecting and analyzing data that is associated with an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79753-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="79753-107">Syntax</span></span>  
  
```cpp  
HRESULT GetBucketParametersForCurrentException(  
    [out] BucketParameters *pParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79753-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="79753-108">Parameters</span></span>  

 `pParams`  
 <span data-ttu-id="79753-109">заполняет Указатель на структуру [буккетпараметерс](bucketparameters-structure.md) , содержащую данные об ошибке для исключения.</span><span class="sxs-lookup"><span data-stu-id="79753-109">[out] A pointer to a [BucketParameters](bucketparameters-structure.md) structure that contains error data for the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79753-110">Требования</span><span class="sxs-lookup"><span data-stu-id="79753-110">Requirements</span></span>  

 <span data-ttu-id="79753-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79753-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79753-112">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="79753-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79753-113">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="79753-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79753-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79753-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79753-115">См. также</span><span class="sxs-lookup"><span data-stu-id="79753-115">See also</span></span>

- [<span data-ttu-id="79753-116">Интерфейс ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="79753-116">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
