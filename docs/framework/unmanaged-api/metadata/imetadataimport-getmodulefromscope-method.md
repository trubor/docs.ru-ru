---
description: 'Дополнительные сведения: метод IMetaDataImport:: Жетмодулефромскопе'
title: Метод IMetaDataImport::GetModuleFromScope
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
ms.openlocfilehash: 8c1e952a45b3827717102428fbd18ceac3951baf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753371"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="e053e-103">Метод IMetaDataImport::GetModuleFromScope</span><span class="sxs-lookup"><span data-stu-id="e053e-103">IMetaDataImport::GetModuleFromScope Method</span></span>

<span data-ttu-id="e053e-104">Возвращает маркер метаданных для модуля, на который ссылается текущая область метаданных.</span><span class="sxs-lookup"><span data-stu-id="e053e-104">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e053e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e053e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e053e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e053e-106">Parameters</span></span>  

 `pmd`  
 <span data-ttu-id="e053e-107">заполняет Указатель на маркер, представляющий модуль, на который ссылается текущая область метаданных.</span><span class="sxs-lookup"><span data-stu-id="e053e-107">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e053e-108">Требования</span><span class="sxs-lookup"><span data-stu-id="e053e-108">Requirements</span></span>  

 <span data-ttu-id="e053e-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e053e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e053e-110">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="e053e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e053e-111">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e053e-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e053e-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e053e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e053e-113">См. также</span><span class="sxs-lookup"><span data-stu-id="e053e-113">See also</span></span>

- [<span data-ttu-id="e053e-114">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e053e-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e053e-115">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="e053e-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
