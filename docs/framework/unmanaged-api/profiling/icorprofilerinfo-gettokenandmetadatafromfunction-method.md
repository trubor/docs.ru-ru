---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: GetTokenAndMetadataFromFunction'
title: Метод ICorProfilerInfo::GetTokenAndMetadataFromFunction
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetTokenAndMetadataFromFunction
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction
helpviewer_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction method [.NET Framework profiling]
- GetTokenAndMetadataFromFunction method [.NET Framework profiling]
ms.assetid: e525aa16-c923-4b16-833b-36f1f0dd70fc
topic_type:
- apiref
ms.openlocfilehash: 0cea6564df15c7a7f4c46097714cc0956002599b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783850"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="fb9b8-103">Метод ICorProfilerInfo::GetTokenAndMetadataFromFunction</span><span class="sxs-lookup"><span data-stu-id="fb9b8-103">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>

<span data-ttu-id="fb9b8-104">Возвращает маркер метаданных и экземпляр интерфейса метаданных, который может использоваться для токена указанной функции.</span><span class="sxs-lookup"><span data-stu-id="fb9b8-104">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb9b8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fb9b8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb9b8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fb9b8-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="fb9b8-107">окне Идентификатор функции, для которой необходимо получить токен метаданных и интерфейс метаданных.</span><span class="sxs-lookup"><span data-stu-id="fb9b8-107">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="fb9b8-108">окне Идентификатор ссылки интерфейса метаданных для получения экземпляра.</span><span class="sxs-lookup"><span data-stu-id="fb9b8-108">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="fb9b8-109">заполняет Указатель на адрес экземпляра интерфейса метаданных, который может использоваться с токеном для указанной функции.</span><span class="sxs-lookup"><span data-stu-id="fb9b8-109">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="fb9b8-110">заполняет Указатель на маркер метаданных для указанной функции.</span><span class="sxs-lookup"><span data-stu-id="fb9b8-110">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb9b8-111">Требования</span><span class="sxs-lookup"><span data-stu-id="fb9b8-111">Requirements</span></span>  

 <span data-ttu-id="fb9b8-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb9b8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb9b8-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb9b8-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb9b8-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb9b8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb9b8-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb9b8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb9b8-116">См. также</span><span class="sxs-lookup"><span data-stu-id="fb9b8-116">See also</span></span>

- [<span data-ttu-id="fb9b8-117">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="fb9b8-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
