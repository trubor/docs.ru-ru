---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyImport:: EnumExportedTypes'
title: Метод IMetaDataAssemblyImport::EnumExportedTypes
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
ms.openlocfilehash: ecddcbd87586f5f61c57f8c04ea3bd68dc652839
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678033"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="2d99a-103">Метод IMetaDataAssemblyImport::EnumExportedTypes</span><span class="sxs-lookup"><span data-stu-id="2d99a-103">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>

<span data-ttu-id="2d99a-104">Перечисляет экспортированные типы, на которые ссылается манифест сборки в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="2d99a-104">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d99a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2d99a-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d99a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2d99a-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="2d99a-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="2d99a-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2d99a-108">Это значение должно быть null, если `EnumExportedTypes` метод вызывается в первый раз.</span><span class="sxs-lookup"><span data-stu-id="2d99a-108">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="2d99a-109">заполняет Перечисление `mdExportedType` токенов метаданных.</span><span class="sxs-lookup"><span data-stu-id="2d99a-109">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2d99a-110">окне Максимальное число `mdExportedType` токенов, которые могут быть помещены в `rExportedTypes` массив.</span><span class="sxs-lookup"><span data-stu-id="2d99a-110">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="2d99a-111">заполняет Количество маркеров, которые `mdExportedType` в действительности помещаются в `rExportedTypes` .</span><span class="sxs-lookup"><span data-stu-id="2d99a-111">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d99a-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2d99a-112">Return Value</span></span>  
  
|<span data-ttu-id="2d99a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d99a-113">HRESULT</span></span>|<span data-ttu-id="2d99a-114">Описание</span><span class="sxs-lookup"><span data-stu-id="2d99a-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2d99a-115">`EnumExportedTypes` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="2d99a-115">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2d99a-116">Нет токенов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="2d99a-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="2d99a-117">В этом случае `pcTokens` имеет значение 0.</span><span class="sxs-lookup"><span data-stu-id="2d99a-117">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2d99a-118">Требования</span><span class="sxs-lookup"><span data-stu-id="2d99a-118">Requirements</span></span>  

 <span data-ttu-id="2d99a-119">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d99a-119">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d99a-120">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="2d99a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d99a-121">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2d99a-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2d99a-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d99a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d99a-123">См. также</span><span class="sxs-lookup"><span data-stu-id="2d99a-123">See also</span></span>

- [<span data-ttu-id="2d99a-124">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="2d99a-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
