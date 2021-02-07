---
description: 'Дополнительные сведения: метод IMetaDataImport:: Енуммодулерефс'
title: Метод IMetaDataImport::EnumModuleRefs
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
ms.openlocfilehash: 3e12d3da8ff556cb3add73ade77e11a68bf60223
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688823"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="da545-103">Метод IMetaDataImport::EnumModuleRefs</span><span class="sxs-lookup"><span data-stu-id="da545-103">IMetaDataImport::EnumModuleRefs Method</span></span>

<span data-ttu-id="da545-104">Перечисляет токены ModuleRef, представляющие импортируемые модули.</span><span class="sxs-lookup"><span data-stu-id="da545-104">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da545-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="da545-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da545-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="da545-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="da545-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="da545-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="da545-108">При первом вызове этого метода это значение должно быть равно NULL.</span><span class="sxs-lookup"><span data-stu-id="da545-108">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="da545-109">заполняет Массив, используемый для хранения маркеров ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="da545-109">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="da545-110">[in] Максимальный размер массива `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="da545-110">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="da545-111">заполняет Число токенов ModuleRef, возвращаемых в `rModuleRefs` .</span><span class="sxs-lookup"><span data-stu-id="da545-111">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da545-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="da545-112">Return Value</span></span>  
  
|<span data-ttu-id="da545-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="da545-113">HRESULT</span></span>|<span data-ttu-id="da545-114">Описание</span><span class="sxs-lookup"><span data-stu-id="da545-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="da545-115">`EnumModuleRefs` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="da545-115">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="da545-116">Нет токенов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="da545-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="da545-117">В этом случае значение `pcModuleRefs` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="da545-117">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="da545-118">Требования</span><span class="sxs-lookup"><span data-stu-id="da545-118">Requirements</span></span>  

 <span data-ttu-id="da545-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da545-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da545-120">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="da545-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da545-121">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da545-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da545-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da545-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da545-123">См. также</span><span class="sxs-lookup"><span data-stu-id="da545-123">See also</span></span>

- [<span data-ttu-id="da545-124">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="da545-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="da545-125">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="da545-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
