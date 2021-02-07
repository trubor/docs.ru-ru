---
description: 'Дополнительные сведения о методе: IMetaDataEmit2::D Ефинеженерикпарам'
title: Метод IMetaDataEmit2::DefineGenericParam
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: 813661adca162f47a864b19c9754b49072bb4c7b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745792"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="e8d53-103">Метод IMetaDataEmit2::DefineGenericParam</span><span class="sxs-lookup"><span data-stu-id="e8d53-103">IMetaDataEmit2::DefineGenericParam Method</span></span>

<span data-ttu-id="e8d53-104">Создает определение для параметра универсального типа и получает маркер для этого параметра универсального типа.</span><span class="sxs-lookup"><span data-stu-id="e8d53-104">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8d53-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e8d53-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineGenericParam (
    [in]  mdToken         tk,
    [in]  ULONG           ulParamSeq,
    [in]  DWORD           dwParamFlags,
    [in]  LPCWSTR         szname,
    [in]  DWORD           reserved,
    [in]  mdToken         rtkConstraints[],
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8d53-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e8d53-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="e8d53-107">окне `mdTypeDef` Токен или `mdMethodDef` , представляющий метод или конструктор, для которого необходимо определить универсальный параметр.</span><span class="sxs-lookup"><span data-stu-id="e8d53-107">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="e8d53-108">окне Индекс универсального параметра.</span><span class="sxs-lookup"><span data-stu-id="e8d53-108">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="e8d53-109">окне Значение перечисления [корженерикпараматтр](corgenericparamattr-enumeration.md) , описывающее тип универсального параметра.</span><span class="sxs-lookup"><span data-stu-id="e8d53-109">[in] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="e8d53-110">окне Имя параметра.</span><span class="sxs-lookup"><span data-stu-id="e8d53-110">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="e8d53-111">окне Этот параметр зарезервирован для расширения в будущем.</span><span class="sxs-lookup"><span data-stu-id="e8d53-111">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="e8d53-112">окне Массив ограничений типа, заканчивающийся нулем.</span><span class="sxs-lookup"><span data-stu-id="e8d53-112">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="e8d53-113">Элементы массива должны быть `mdTypeDef` `mdTypeRef` `mdTypeSpec` маркером метаданных, или.</span><span class="sxs-lookup"><span data-stu-id="e8d53-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="e8d53-114">заполняет Токен, представляющий универсальный параметр.</span><span class="sxs-lookup"><span data-stu-id="e8d53-114">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8d53-115">Требования</span><span class="sxs-lookup"><span data-stu-id="e8d53-115">Requirements</span></span>  

 <span data-ttu-id="e8d53-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8d53-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8d53-117">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="e8d53-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8d53-118">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8d53-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e8d53-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8d53-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d53-120">См. также</span><span class="sxs-lookup"><span data-stu-id="e8d53-120">See also</span></span>

- [<span data-ttu-id="e8d53-121">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="e8d53-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="e8d53-122">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="e8d53-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
