---
description: 'Дополнительные сведения о методе: IMetaDataImport2:: EnumMethodSpecs'
title: Метод IMetaDataImport2::EnumMethodSpecs
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 19fff1d78599d968bb1fd0ab27b0f71e41fae20b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677526"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="264a9-103">Метод IMetaDataImport2::EnumMethodSpecs</span><span class="sxs-lookup"><span data-stu-id="264a9-103">IMetaDataImport2::EnumMethodSpecs Method</span></span>

<span data-ttu-id="264a9-104">Возвращает перечислитель для массива токенов MethodSpec, связанных с указанным токеном MethodDef или MemberRef.</span><span class="sxs-lookup"><span data-stu-id="264a9-104">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="264a9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="264a9-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="264a9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="264a9-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="264a9-107">[вход, выход] Указатель на перечислитель для `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="264a9-107">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="264a9-108">окне Токен MemberRef или MethodDef, представляющий метод, для которого необходимо перечислить маркеры MethodSpec.</span><span class="sxs-lookup"><span data-stu-id="264a9-108">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="264a9-109">Если значение `tk` равно 0 (нулю), будут перечислены все токены MethodSpec в области.</span><span class="sxs-lookup"><span data-stu-id="264a9-109">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="264a9-110">заполняет Массив токенов MethodSpec для перечисления.</span><span class="sxs-lookup"><span data-stu-id="264a9-110">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="264a9-111">окне Запрошенное максимальное число токенов для размещения в `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="264a9-111">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="264a9-112">заполняет Возвращенное число токенов, помещенных в `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="264a9-112">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="264a9-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="264a9-113">Return Value</span></span>  
  
|<span data-ttu-id="264a9-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="264a9-114">HRESULT</span></span>|<span data-ttu-id="264a9-115">Описание</span><span class="sxs-lookup"><span data-stu-id="264a9-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="264a9-116">`EnumMethodSpecs` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="264a9-116">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="264a9-117">`phEnum` не содержит элементов Member.</span><span class="sxs-lookup"><span data-stu-id="264a9-117">`phEnum` has no member elements.</span></span> <span data-ttu-id="264a9-118">В этом случае `pcMethodSpecs` имеет значение 0 (ноль).</span><span class="sxs-lookup"><span data-stu-id="264a9-118">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="264a9-119">Требования</span><span class="sxs-lookup"><span data-stu-id="264a9-119">Requirements</span></span>  

 <span data-ttu-id="264a9-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="264a9-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="264a9-121">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="264a9-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="264a9-122">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="264a9-122">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="264a9-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="264a9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="264a9-124">См. также</span><span class="sxs-lookup"><span data-stu-id="264a9-124">See also</span></span>

- [<span data-ttu-id="264a9-125">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="264a9-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="264a9-126">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="264a9-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
