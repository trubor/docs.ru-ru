---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Сеткласслайаут'
title: Метод IMetaDataEmit::SetClassLayout
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
ms.openlocfilehash: e0ce8e93137b9a32a13ca86ead539385523fa8a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706608"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="7606a-103">Метод IMetaDataEmit::SetClassLayout</span><span class="sxs-lookup"><span data-stu-id="7606a-103">IMetaDataEmit::SetClassLayout Method</span></span>

<span data-ttu-id="7606a-104">Завершает компоновку полей для класса, который был определен при предыдущем вызове [метода дефинетипедеф](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="7606a-104">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7606a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7606a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7606a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7606a-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="7606a-107">окне `mdTypeDef` Токен, указывающий класс для размещения.</span><span class="sxs-lookup"><span data-stu-id="7606a-107">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="7606a-108">окне Размер упаковки: 1, 2, 4, 8 или 16 байт.</span><span class="sxs-lookup"><span data-stu-id="7606a-108">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="7606a-109">Размер упаковки — это число байтов между смежными полями.</span><span class="sxs-lookup"><span data-stu-id="7606a-109">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="7606a-110">окне Массив структур [COR_FIELD_OFFSET](cor-field-offset-structure.md) , каждый из которых задает поле класса и смещение поля в пределах класса.</span><span class="sxs-lookup"><span data-stu-id="7606a-110">[in] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="7606a-111">Завершите массив с помощью `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="7606a-111">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="7606a-112">окне Размер класса в байтах.</span><span class="sxs-lookup"><span data-stu-id="7606a-112">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7606a-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="7606a-113">Remarks</span></span>  

 <span data-ttu-id="7606a-114">Класс изначально определяется путем вызова метода [IMetaDataEmit::D ефинетипедеф](imetadataemit-definetypedef-method.md) и указания одного из трех макетов для полей класса: Automatic, последовательный или явный.</span><span class="sxs-lookup"><span data-stu-id="7606a-114">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="7606a-115">Как правило, вы используете автоматическую разметку и позволяете среде выполнения выбрать лучший способ размещения полей.</span><span class="sxs-lookup"><span data-stu-id="7606a-115">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="7606a-116">Однако может потребоваться, чтобы поля были размещены в соответствии с расположением, используемым неуправляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="7606a-116">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="7606a-117">В этом случае выберите последовательный или явный макет и вызов `SetClassLayout` , чтобы завершить компоновку полей:</span><span class="sxs-lookup"><span data-stu-id="7606a-117">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="7606a-118">Последовательный макет: укажите размер упаковки.</span><span class="sxs-lookup"><span data-stu-id="7606a-118">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="7606a-119">Поле выстраивается в соответствии с его естественным размером или упаковочным размером, в зависимости от того, что приводит к уменьшению смещения поля.</span><span class="sxs-lookup"><span data-stu-id="7606a-119">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="7606a-120">Задайте `rFieldOffsets` и `ulClassSize` равным нулю.</span><span class="sxs-lookup"><span data-stu-id="7606a-120">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="7606a-121">Явный макет. либо укажите смещение каждого поля, либо укажите размер класса и размер упаковки.</span><span class="sxs-lookup"><span data-stu-id="7606a-121">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7606a-122">Требования</span><span class="sxs-lookup"><span data-stu-id="7606a-122">Requirements</span></span>  

 <span data-ttu-id="7606a-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7606a-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7606a-124">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="7606a-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7606a-125">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7606a-125">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7606a-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7606a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7606a-127">См. также</span><span class="sxs-lookup"><span data-stu-id="7606a-127">See also</span></span>

- [<span data-ttu-id="7606a-128">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="7606a-128">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7606a-129">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="7606a-129">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
