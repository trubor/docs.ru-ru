---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyImport:: Енумфилес'
title: Метод IMetaDataAssemblyImport::EnumFiles
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
ms.openlocfilehash: 25282edd081e937e4c84334f9f004e201b9db46f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671026"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="17f3f-103">Метод IMetaDataAssemblyImport::EnumFiles</span><span class="sxs-lookup"><span data-stu-id="17f3f-103">IMetaDataAssemblyImport::EnumFiles Method</span></span>

<span data-ttu-id="17f3f-104">Перечисляет файлы, на которые ссылается текущий манифест сборки.</span><span class="sxs-lookup"><span data-stu-id="17f3f-104">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17f3f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="17f3f-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17f3f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="17f3f-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="17f3f-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="17f3f-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="17f3f-108">При первом вызове этого метода это значение должно быть нулевым.</span><span class="sxs-lookup"><span data-stu-id="17f3f-108">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="17f3f-109">заполняет Массив, используемый для хранения `mdFile` маркеров метаданных.</span><span class="sxs-lookup"><span data-stu-id="17f3f-109">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="17f3f-110">окне Максимальное число `mdFile` токенов, которые могут быть помещены в `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="17f3f-110">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="17f3f-111">заполняет Количество маркеров, которые `mdFile` в действительности помещаются в `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="17f3f-111">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17f3f-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="17f3f-112">Return Value</span></span>  
  
|<span data-ttu-id="17f3f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="17f3f-113">HRESULT</span></span>|<span data-ttu-id="17f3f-114">Описание</span><span class="sxs-lookup"><span data-stu-id="17f3f-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="17f3f-115">`EnumFiles` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="17f3f-115">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="17f3f-116">Нет токенов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="17f3f-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="17f3f-117">В этом случае `pcTokens` имеет значение 0.</span><span class="sxs-lookup"><span data-stu-id="17f3f-117">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="17f3f-118">Требования</span><span class="sxs-lookup"><span data-stu-id="17f3f-118">Requirements</span></span>  

 <span data-ttu-id="17f3f-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17f3f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17f3f-120">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="17f3f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17f3f-121">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17f3f-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="17f3f-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17f3f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17f3f-123">См. также</span><span class="sxs-lookup"><span data-stu-id="17f3f-123">See also</span></span>

- [<span data-ttu-id="17f3f-124">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="17f3f-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
