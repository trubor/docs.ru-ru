---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyImport:: EnumAssemblyRefs'
title: Метод IMetaDataAssemblyImport::EnumAssemblyRefs
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: fc1d74d79edc21c6d3d13c80510440333d083801
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671065"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="85890-103">Метод IMetaDataAssemblyImport::EnumAssemblyRefs</span><span class="sxs-lookup"><span data-stu-id="85890-103">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>

<span data-ttu-id="85890-104">Перечисляет `mdAssemblyRef` экземпляры, определенные в манифесте сборки.</span><span class="sxs-lookup"><span data-stu-id="85890-104">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85890-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="85890-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85890-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="85890-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="85890-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="85890-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="85890-108">Это значение должно быть null, если `EnumAssemblyRefs` метод вызывается в первый раз.</span><span class="sxs-lookup"><span data-stu-id="85890-108">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="85890-109">заполняет Перечисление `mdAssemblyRef` токенов метаданных.</span><span class="sxs-lookup"><span data-stu-id="85890-109">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="85890-110">окне Максимальное число токенов, которые могут быть помещены в `rAssemblyRefs` массив.</span><span class="sxs-lookup"><span data-stu-id="85890-110">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="85890-111">заполняет Количество маркеров, которые в действительности помещаются в `rAssemblyRefs` .</span><span class="sxs-lookup"><span data-stu-id="85890-111">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85890-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="85890-112">Return Value</span></span>  
  
|<span data-ttu-id="85890-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85890-113">HRESULT</span></span>|<span data-ttu-id="85890-114">Описание</span><span class="sxs-lookup"><span data-stu-id="85890-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="85890-115">`EnumAssemblyRefs` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="85890-115">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="85890-116">Нет токенов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="85890-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="85890-117">В этом случае `pcTokens` имеет значение 0.</span><span class="sxs-lookup"><span data-stu-id="85890-117">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85890-118">Требования</span><span class="sxs-lookup"><span data-stu-id="85890-118">Requirements</span></span>  

 <span data-ttu-id="85890-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85890-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85890-120">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="85890-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85890-121">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="85890-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85890-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85890-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85890-123">См. также</span><span class="sxs-lookup"><span data-stu-id="85890-123">See also</span></span>

- [<span data-ttu-id="85890-124">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="85890-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
