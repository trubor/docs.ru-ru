---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: SetPropertyProps'
title: Метод IMetaDataEmit::SetPropertyProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
ms.openlocfilehash: ad5efa86b4f774bcaa2251cb992c2dd52ac28bdd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771838"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="b7982-103">Метод IMetaDataEmit::SetPropertyProps</span><span class="sxs-lookup"><span data-stu-id="b7982-103">IMetaDataEmit::SetPropertyProps Method</span></span>

<span data-ttu-id="b7982-104">Задает функции, хранимые в метаданных для свойства, определенного при предыдущем вызове [метода DefineProperty](imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="b7982-104">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7982-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b7982-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertyProps (
    [in]  mdProperty      pr,
    [in]  DWORD           dwPropFlags,
    [in]  DWORD           dwCPlusTypeFlag,
    [in]  void const      *pValue,
    [in]  ULONG           cchValue,
    [in]  mdMethodDef     mdSetter,
    [in]  mdMethodDef     mdGetter,
    [in]  mdMethodDef     rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7982-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b7982-106">Parameters</span></span>  

 `pr`  
 <span data-ttu-id="b7982-107">окне Токен изменяемого свойства</span><span class="sxs-lookup"><span data-stu-id="b7982-107">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="b7982-108">окне Флаги свойств.</span><span class="sxs-lookup"><span data-stu-id="b7982-108">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="b7982-109">окне Тип значения свойства по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b7982-109">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="b7982-110">окне Значение по умолчанию для свойства.</span><span class="sxs-lookup"><span data-stu-id="b7982-110">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="b7982-111">окне Число символов Юникода в `pValue` .</span><span class="sxs-lookup"><span data-stu-id="b7982-111">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="b7982-112">окне Метод, который задает значение свойства.</span><span class="sxs-lookup"><span data-stu-id="b7982-112">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="b7982-113">окне Метод, который получает значение свойства.</span><span class="sxs-lookup"><span data-stu-id="b7982-113">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="b7982-114">окне Массив других методов, связанных со свойством.</span><span class="sxs-lookup"><span data-stu-id="b7982-114">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="b7982-115">Завершите этот массив `mdTokenNil` токеном.</span><span class="sxs-lookup"><span data-stu-id="b7982-115">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7982-116">Требования</span><span class="sxs-lookup"><span data-stu-id="b7982-116">Requirements</span></span>  

 <span data-ttu-id="b7982-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7982-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7982-118">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="b7982-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7982-119">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7982-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7982-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7982-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7982-121">См. также</span><span class="sxs-lookup"><span data-stu-id="b7982-121">See also</span></span>

- [<span data-ttu-id="b7982-122">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b7982-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b7982-123">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b7982-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
