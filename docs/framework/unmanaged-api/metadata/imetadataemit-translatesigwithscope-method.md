---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Транслатесигвисскопе'
title: Метод IMetaDataEmit::TranslateSigWithScope
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.TranslateSigWithScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type:
- apiref
ms.openlocfilehash: e5f4e522e993f2f391ca0c29e5fcc2cbb71775e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720937"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="49da6-103">Метод IMetaDataEmit::TranslateSigWithScope</span><span class="sxs-lookup"><span data-stu-id="49da6-103">IMetaDataEmit::TranslateSigWithScope Method</span></span>

<span data-ttu-id="49da6-104">Импортирует сборку в текущую область и получает новую сигнатуру метаданных для Объединенной области.</span><span class="sxs-lookup"><span data-stu-id="49da6-104">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49da6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="49da6-105">Syntax</span></span>  
  
```cpp  
HRESULT TranslateSigWithScope (
    [in]  IMetaDataAssemblyImport   *pAssemImport,
    [in]  const void                *pbHashValue,
    [in]  ULONG                     cbHashValue,
    [in]  IMetaDataImport           *import,
    [in]  PCCOR_SIGNATURE           pbSigBlob,
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,
    [in]  IMetaDataEmit             *emit,
    [out] PCOR_SIGNATURE            pvTranslatedSig,
    [in]  ULONG                     cbTranslatedSigMax,
    [out] ULONG                     *pcbTranslatedSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49da6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="49da6-106">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="49da6-107">окне Интерфейс для импортируемой сборки (где определена сигнатура).</span><span class="sxs-lookup"><span data-stu-id="49da6-107">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="49da6-108">окне Хэш-объект хэша для сборки.</span><span class="sxs-lookup"><span data-stu-id="49da6-108">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="49da6-109">окне Число байтов в `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="49da6-109">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="49da6-110">окне Интерфейс для области действия метаданных импорта.</span><span class="sxs-lookup"><span data-stu-id="49da6-110">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="49da6-111">окне Импортируемая подпись.</span><span class="sxs-lookup"><span data-stu-id="49da6-111">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="49da6-112">окне Размер (в байтах) `pbSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="49da6-112">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="49da6-113">окне Интерфейс для экспорта сборки.</span><span class="sxs-lookup"><span data-stu-id="49da6-113">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="49da6-114">окне Интерфейс для области экспорта метаданных.</span><span class="sxs-lookup"><span data-stu-id="49da6-114">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="49da6-115">заполняет Буфер для хранения переведенного большого двоичного объекта сигнатуры.</span><span class="sxs-lookup"><span data-stu-id="49da6-115">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="49da6-116">окне Емкость (в байтах) `pvTranslatedSig` .</span><span class="sxs-lookup"><span data-stu-id="49da6-116">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="49da6-117">заполняет Число фактических байтов в переведенной сигнатуре.</span><span class="sxs-lookup"><span data-stu-id="49da6-117">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49da6-118">Требования</span><span class="sxs-lookup"><span data-stu-id="49da6-118">Requirements</span></span>  

 <span data-ttu-id="49da6-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49da6-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49da6-120">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="49da6-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="49da6-121">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="49da6-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49da6-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49da6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49da6-123">См. также</span><span class="sxs-lookup"><span data-stu-id="49da6-123">See also</span></span>

- [<span data-ttu-id="49da6-124">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="49da6-124">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="49da6-125">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="49da6-125">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="49da6-126">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="49da6-126">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="49da6-127">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="49da6-127">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="49da6-128">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="49da6-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
