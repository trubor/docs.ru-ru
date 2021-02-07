---
description: 'Дополнительные сведения о методе: IMetaDataError:: OnError'
title: Метод IMetaDataError::OnError
ms.date: 03/30/2017
api_name:
- IMetaDataError.OnError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type:
- apiref
ms.openlocfilehash: 9556f1bd7758755d9160e3a2e91a1fe5786aa562
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670974"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="b00f0-103">Метод IMetaDataError::OnError</span><span class="sxs-lookup"><span data-stu-id="b00f0-103">IMetaDataError::OnError Method</span></span>

<span data-ttu-id="b00f0-104">Предоставляет уведомление об ошибках, возникающих во время слияния метаданных.</span><span class="sxs-lookup"><span data-stu-id="b00f0-104">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b00f0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b00f0-105">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b00f0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b00f0-106">Parameters</span></span>  

 `hrError`  
 <span data-ttu-id="b00f0-107">окне Значение ошибки HRESULT, возвращаемое вызывающему методу.</span><span class="sxs-lookup"><span data-stu-id="b00f0-107">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="b00f0-108">окне Токен метаданных объекта кода, который был объединен при возникновении ошибки.</span><span class="sxs-lookup"><span data-stu-id="b00f0-108">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b00f0-109">Требования</span><span class="sxs-lookup"><span data-stu-id="b00f0-109">Requirements</span></span>  

 <span data-ttu-id="b00f0-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b00f0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b00f0-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="b00f0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b00f0-112">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b00f0-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b00f0-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b00f0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b00f0-114">См. также</span><span class="sxs-lookup"><span data-stu-id="b00f0-114">See also</span></span>

- [<span data-ttu-id="b00f0-115">Интерфейс IMetaDataError</span><span class="sxs-lookup"><span data-stu-id="b00f0-115">IMetaDataError Interface</span></span>](imetadataerror-interface.md)
