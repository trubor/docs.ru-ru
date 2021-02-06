---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Сетфиелдмаршал'
title: Метод IMetaDataEmit::SetFieldMarshal
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
ms.openlocfilehash: 4694487479b0249e875abfd9ecd963a5dc404d46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658052"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="0a433-103">Метод IMetaDataEmit::SetFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="0a433-103">IMetaDataEmit::SetFieldMarshal Method</span></span>

<span data-ttu-id="0a433-104">Задает сведения о маршалировании PInvoke для поля, возвращаемого метода или параметра метода, на который ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="0a433-104">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a433-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0a433-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a433-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0a433-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="0a433-107">окне Токен для целевого элемента данных.</span><span class="sxs-lookup"><span data-stu-id="0a433-107">[in] The token for target data item.</span></span> <span data-ttu-id="0a433-108">Это либо маркер, либо `mdFieldDef` `mdParamDef` .</span><span class="sxs-lookup"><span data-stu-id="0a433-108">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="0a433-109">окне Сигнатура для неуправляемого типа.</span><span class="sxs-lookup"><span data-stu-id="0a433-109">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="0a433-110">окне Число байтов в `pvNativeType` .</span><span class="sxs-lookup"><span data-stu-id="0a433-110">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a433-111">Требования</span><span class="sxs-lookup"><span data-stu-id="0a433-111">Requirements</span></span>  

 <span data-ttu-id="0a433-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a433-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a433-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="0a433-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0a433-114">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a433-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a433-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a433-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a433-116">См. также</span><span class="sxs-lookup"><span data-stu-id="0a433-116">See also</span></span>

- [<span data-ttu-id="0a433-117">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="0a433-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="0a433-118">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="0a433-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
