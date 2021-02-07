---
description: 'Дополнительные сведения: метод IMetaDataImport:: EnumTypeDefs'
title: Метод IMetaDataImport::EnumTypeDefs
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: 28bd06b70573b780b687da9de0e13e17c29bb39a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670689"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="e8278-103">Метод IMetaDataImport::EnumTypeDefs</span><span class="sxs-lookup"><span data-stu-id="e8278-103">IMetaDataImport::EnumTypeDefs Method</span></span>

<span data-ttu-id="e8278-104">Перечисляет токены TypeDef, представляющие все типы в текущей области.</span><span class="sxs-lookup"><span data-stu-id="e8278-104">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8278-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e8278-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8278-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e8278-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="e8278-107">заполняет Указатель на новый перечислитель.</span><span class="sxs-lookup"><span data-stu-id="e8278-107">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="e8278-108">При первом вызове этого метода это значение должно быть равно NULL.</span><span class="sxs-lookup"><span data-stu-id="e8278-108">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="e8278-109">окне Массив, используемый для хранения токенов TypeDef.</span><span class="sxs-lookup"><span data-stu-id="e8278-109">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e8278-110">[in] Максимальный размер массива `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="e8278-110">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="e8278-111">заполняет Число токенов TypeDef, возвращаемых в `rTypeDefs` .</span><span class="sxs-lookup"><span data-stu-id="e8278-111">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8278-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e8278-112">Return Value</span></span>  
  
|<span data-ttu-id="e8278-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8278-113">HRESULT</span></span>|<span data-ttu-id="e8278-114">Описание</span><span class="sxs-lookup"><span data-stu-id="e8278-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e8278-115">`EnumTypeDefs` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="e8278-115">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e8278-116">Нет токенов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="e8278-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="e8278-117">В этом случае значение `pcTypeDefs` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="e8278-117">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8278-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="e8278-118">Remarks</span></span>  

 <span data-ttu-id="e8278-119">Маркер TypeDef представляет тип, например класс или интерфейс, а также любой тип, добавленный с помощью механизма расширяемости.</span><span class="sxs-lookup"><span data-stu-id="e8278-119">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8278-120">Требования</span><span class="sxs-lookup"><span data-stu-id="e8278-120">Requirements</span></span>  

 <span data-ttu-id="e8278-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8278-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8278-122">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="e8278-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8278-123">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8278-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e8278-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8278-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8278-125">См. также</span><span class="sxs-lookup"><span data-stu-id="e8278-125">See also</span></span>

- [<span data-ttu-id="e8278-126">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e8278-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e8278-127">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="e8278-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
