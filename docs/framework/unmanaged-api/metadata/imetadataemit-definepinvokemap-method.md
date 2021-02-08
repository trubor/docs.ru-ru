---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Ефинепинвокемап'
title: Метод IMetaDataEmit::DefinePinvokeMap
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
ms.openlocfilehash: 7b0477ca603241e773a67f335da579daa2ed3d30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784071"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="8a029-103">Метод IMetaDataEmit::DefinePinvokeMap</span><span class="sxs-lookup"><span data-stu-id="8a029-103">IMetaDataEmit::DefinePinvokeMap Method</span></span>

<span data-ttu-id="8a029-104">Задает функции сигнатуры PInvoke метода, на который ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="8a029-104">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a029-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8a029-105">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (
    [in]  mdToken            tk,
    [in]  DWORD              dwMappingFlags,
    [in]  LPCWSTR            szImportName,
    [in]  mdModuleRef        mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a029-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8a029-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="8a029-107">окне Токен для целевого метода.</span><span class="sxs-lookup"><span data-stu-id="8a029-107">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="8a029-108">окне Флаги, используемые PInvoke для сопоставления.</span><span class="sxs-lookup"><span data-stu-id="8a029-108">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="8a029-109">окне Имя целевого метода экспорта в неуправляемой библиотеке DLL.</span><span class="sxs-lookup"><span data-stu-id="8a029-109">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="8a029-110">окне Токен для собственной DLL-библиотеки целевого объекта.</span><span class="sxs-lookup"><span data-stu-id="8a029-110">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a029-111">Требования</span><span class="sxs-lookup"><span data-stu-id="8a029-111">Requirements</span></span>  

 <span data-ttu-id="8a029-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a029-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a029-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="8a029-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a029-114">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8a029-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a029-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a029-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a029-116">См. также</span><span class="sxs-lookup"><span data-stu-id="8a029-116">See also</span></span>

- [<span data-ttu-id="8a029-117">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="8a029-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="8a029-118">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="8a029-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
