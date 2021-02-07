---
description: 'Дополнительные сведения о методе: IMetaDataImport2:: GetGenericParamConstraintProps'
title: Метод IMetaDataImport2::GetGenericParamConstraintProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamConstraintProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type:
- apiref
ms.openlocfilehash: 03cc4df655f9ab7a1c04840e9d4fa782a90ce1ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688745"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="62ea1-103">Метод IMetaDataImport2::GetGenericParamConstraintProps</span><span class="sxs-lookup"><span data-stu-id="62ea1-103">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>

<span data-ttu-id="62ea1-104">Возвращает метаданные, связанные с ограничением универсального параметра, представленного указанным маркером ограничения.</span><span class="sxs-lookup"><span data-stu-id="62ea1-104">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62ea1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="62ea1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62ea1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="62ea1-106">Parameters</span></span>  

 `gpc`  
 <span data-ttu-id="62ea1-107">окне Токен для ограничения универсального параметра, для которого возвращаются метаданные.</span><span class="sxs-lookup"><span data-stu-id="62ea1-107">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="62ea1-108">заполняет Указатель на маркер, представляющий ограниченный универсальный параметр.</span><span class="sxs-lookup"><span data-stu-id="62ea1-108">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="62ea1-109">заполняет Указатель на маркер TypeDef, TypeRef или TypeSpec, представляющий ограничение на `ptGenericParam` .</span><span class="sxs-lookup"><span data-stu-id="62ea1-109">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62ea1-110">Требования</span><span class="sxs-lookup"><span data-stu-id="62ea1-110">Requirements</span></span>  

 <span data-ttu-id="62ea1-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62ea1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62ea1-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="62ea1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="62ea1-113">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62ea1-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="62ea1-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62ea1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ea1-115">См. также</span><span class="sxs-lookup"><span data-stu-id="62ea1-115">See also</span></span>

- [<span data-ttu-id="62ea1-116">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="62ea1-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="62ea1-117">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="62ea1-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
