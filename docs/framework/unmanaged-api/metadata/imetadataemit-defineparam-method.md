---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Ефинепарам'
title: Метод IMetaDataEmit::DefineParam
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 300de3183b329773a8e6813d6b92c6d049d63195
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784097"
---
# <a name="imetadataemitdefineparam-method"></a><span data-ttu-id="ca1e7-103">Метод IMetaDataEmit::DefineParam</span><span class="sxs-lookup"><span data-stu-id="ca1e7-103">IMetaDataEmit::DefineParam Method</span></span>

<span data-ttu-id="ca1e7-104">Создает определение параметра с указанной сигнатурой для метода, на который ссылается указанный токен, и получает маркер для этого определения параметра.</span><span class="sxs-lookup"><span data-stu-id="ca1e7-104">Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca1e7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ca1e7-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,
    [in]  ULONG       ulParamSeq,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,
    [out] mdParamDef  *ppd
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca1e7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ca1e7-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="ca1e7-107">окне Токен для метода, параметр которого определяется.</span><span class="sxs-lookup"><span data-stu-id="ca1e7-107">[in] The token for the method whose parameter is being defined.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="ca1e7-108">окне Порядковый номер параметра.</span><span class="sxs-lookup"><span data-stu-id="ca1e7-108">[in] The parameter sequence number.</span></span>  
  
 `szName`  
 <span data-ttu-id="ca1e7-109">окне Имя параметра в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="ca1e7-109">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="ca1e7-110">окне Флаги для параметра.</span><span class="sxs-lookup"><span data-stu-id="ca1e7-110">[in] Flags for the parameter.</span></span> <span data-ttu-id="ca1e7-111">Это битовая маска `CorParamAttr` значений.</span><span class="sxs-lookup"><span data-stu-id="ca1e7-111">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="ca1e7-112">[входные] `ELEMENT_TYPE_` *\** для постоянного значения.</span><span class="sxs-lookup"><span data-stu-id="ca1e7-112">[in] `ELEMENT_TYPE_`*\** for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="ca1e7-113">окне Постоянное значение для параметра.</span><span class="sxs-lookup"><span data-stu-id="ca1e7-113">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="ca1e7-114">окне Размер (в символах Юникода) `pValue` .</span><span class="sxs-lookup"><span data-stu-id="ca1e7-114">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
 `ppd`  
 <span data-ttu-id="ca1e7-115">заполняет `mdParamDef` Назначенный маркер.</span><span class="sxs-lookup"><span data-stu-id="ca1e7-115">[out] The `mdParamDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca1e7-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="ca1e7-116">Remarks</span></span>  

 <span data-ttu-id="ca1e7-117">Значения последовательности в `ulParamSeq` аргументе начинаются с 1 для параметров.</span><span class="sxs-lookup"><span data-stu-id="ca1e7-117">The sequence values in `ulParamSeq` begin with 1 for parameters.</span></span> <span data-ttu-id="ca1e7-118">Возвращаемое значение имеет порядковый номер 0.</span><span class="sxs-lookup"><span data-stu-id="ca1e7-118">A return value has a sequence number of 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca1e7-119">Требования</span><span class="sxs-lookup"><span data-stu-id="ca1e7-119">Requirements</span></span>  

 <span data-ttu-id="ca1e7-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca1e7-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca1e7-121">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="ca1e7-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca1e7-122">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca1e7-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca1e7-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca1e7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca1e7-124">См. также</span><span class="sxs-lookup"><span data-stu-id="ca1e7-124">See also</span></span>

- [<span data-ttu-id="ca1e7-125">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="ca1e7-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ca1e7-126">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="ca1e7-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
