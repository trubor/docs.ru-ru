---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: ApplyEditAndContinue'
title: Метод IMetaDataEmit::ApplyEditAndContinue
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.ApplyEditAndContinue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type:
- apiref
ms.openlocfilehash: 46454c4141aa220b43820307c86765a1827251df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753501"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="a92d0-103">Метод IMetaDataEmit::ApplyEditAndContinue</span><span class="sxs-lookup"><span data-stu-id="a92d0-103">IMetaDataEmit::ApplyEditAndContinue Method</span></span>

<span data-ttu-id="a92d0-104">Обновляет текущую область сборки изменениями, внесенными в указанные метаданные.</span><span class="sxs-lookup"><span data-stu-id="a92d0-104">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a92d0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a92d0-105">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a92d0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a92d0-106">Parameters</span></span>  

 `pImport`  
 <span data-ttu-id="a92d0-107">\[в \] указателе на объект [IUnknown](/cpp/atl/iunknown) , представляющий разностные метаданные из переносимого исполняемого файла (PE).</span><span class="sxs-lookup"><span data-stu-id="a92d0-107">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="a92d0-108">Разностные метаданные — это блок метаданных, включающий изменения, внесенные в копию фактических метаданных модуля.</span><span class="sxs-lookup"><span data-stu-id="a92d0-108">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a92d0-109">Требования</span><span class="sxs-lookup"><span data-stu-id="a92d0-109">Requirements</span></span>  

 <span data-ttu-id="a92d0-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a92d0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a92d0-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="a92d0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a92d0-112">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a92d0-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a92d0-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a92d0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a92d0-114">См. также</span><span class="sxs-lookup"><span data-stu-id="a92d0-114">See also</span></span>

- [<span data-ttu-id="a92d0-115">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="a92d0-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a92d0-116">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="a92d0-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
