---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyImport:: Енумманифестресаурцес'
title: Метод IMetaDataAssemblyImport::EnumManifestResources
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
ms.openlocfilehash: ff819ebb575626af6049558656637e7fabcbc322
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677986"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="a81c7-103">Метод IMetaDataAssemblyImport::EnumManifestResources</span><span class="sxs-lookup"><span data-stu-id="a81c7-103">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>

<span data-ttu-id="a81c7-104">Возвращает указатель на перечислитель для ресурсов, указанных в текущем манифесте сборки.</span><span class="sxs-lookup"><span data-stu-id="a81c7-104">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a81c7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a81c7-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="a81c7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a81c7-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="a81c7-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="a81c7-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a81c7-108">Это значение должно быть null, если `EnumManifestResources` метод вызывается в первый раз.</span><span class="sxs-lookup"><span data-stu-id="a81c7-108">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="a81c7-109">заполняет Массив, используемый для хранения `mdManifestResource` маркеров метаданных.</span><span class="sxs-lookup"><span data-stu-id="a81c7-109">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a81c7-110">окне Максимальное число `mdManifestResource` токенов, которые могут быть помещены в `rManifestResources` .</span><span class="sxs-lookup"><span data-stu-id="a81c7-110">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a81c7-111">заполняет Количество маркеров, которые `mdManifestResource` в действительности помещаются в `rManifestResources` .</span><span class="sxs-lookup"><span data-stu-id="a81c7-111">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a81c7-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a81c7-112">Return Value</span></span>  
  
|<span data-ttu-id="a81c7-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a81c7-113">HRESULT</span></span>|<span data-ttu-id="a81c7-114">Описание</span><span class="sxs-lookup"><span data-stu-id="a81c7-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a81c7-115">`EnumManifestResources` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="a81c7-115">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a81c7-116">Нет токенов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="a81c7-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="a81c7-117">В этом случае `pcTokens` имеет значение 0.</span><span class="sxs-lookup"><span data-stu-id="a81c7-117">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a81c7-118">Требования</span><span class="sxs-lookup"><span data-stu-id="a81c7-118">Requirements</span></span>  

 <span data-ttu-id="a81c7-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a81c7-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a81c7-120">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="a81c7-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a81c7-121">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a81c7-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a81c7-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a81c7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a81c7-123">См. также</span><span class="sxs-lookup"><span data-stu-id="a81c7-123">See also</span></span>

- [<span data-ttu-id="a81c7-124">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="a81c7-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
