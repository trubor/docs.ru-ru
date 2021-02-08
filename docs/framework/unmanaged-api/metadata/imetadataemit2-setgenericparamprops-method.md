---
description: 'Дополнительные сведения о методе: IMetaDataEmit2:: Сетженерикпарампропс'
title: Метод IMetaDataEmit2::SetGenericParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
ms.openlocfilehash: 9c6946bbd301450203bc6fb2b1202352119dc792
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771656"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="089eb-103">Метод IMetaDataEmit2::SetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="089eb-103">IMetaDataEmit2::SetGenericParamProps Method</span></span>

<span data-ttu-id="089eb-104">Задает значения свойств для определения универсального параметра, на которое ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="089eb-104">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="089eb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="089eb-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="089eb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="089eb-106">Parameters</span></span>  

 `gp`  
 <span data-ttu-id="089eb-107">окне Токен для определения универсального параметра, для которого задаются значения.</span><span class="sxs-lookup"><span data-stu-id="089eb-107">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="089eb-108">окне Значение перечисления [корженерикпараматтр](corgenericparamattr-enumeration.md) , описывающее тип универсального параметра.</span><span class="sxs-lookup"><span data-stu-id="089eb-108">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="089eb-109">[в] Необязательно.</span><span class="sxs-lookup"><span data-stu-id="089eb-109">[in] Optional.</span></span> <span data-ttu-id="089eb-110">Имя параметра, для которого задаются значения.</span><span class="sxs-lookup"><span data-stu-id="089eb-110">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="089eb-111">окне Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="089eb-111">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="089eb-112">[в] Необязательно.</span><span class="sxs-lookup"><span data-stu-id="089eb-112">[in] Optional.</span></span> <span data-ttu-id="089eb-113">Массив ограничений типа, заканчивающийся нулем.</span><span class="sxs-lookup"><span data-stu-id="089eb-113">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="089eb-114">Элементы массива должны быть `mdTypeDef` `mdTypeRef` `mdTypeSpec` маркером метаданных, или.</span><span class="sxs-lookup"><span data-stu-id="089eb-114">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="089eb-115">Требования</span><span class="sxs-lookup"><span data-stu-id="089eb-115">Requirements</span></span>  

 <span data-ttu-id="089eb-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="089eb-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="089eb-117">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="089eb-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="089eb-118">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="089eb-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="089eb-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="089eb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="089eb-120">См. также</span><span class="sxs-lookup"><span data-stu-id="089eb-120">See also</span></span>

- [<span data-ttu-id="089eb-121">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="089eb-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="089eb-122">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="089eb-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
