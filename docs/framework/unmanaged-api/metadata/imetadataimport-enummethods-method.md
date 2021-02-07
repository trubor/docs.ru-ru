---
description: 'Дополнительные сведения: метод IMetaDataImport:: Enummethods-'
title: Метод IMetaDataImport::EnumMethods
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
ms.openlocfilehash: 4fce3593d088a8d401335869eb49e598ac4c3fd2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670683"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="f14b7-103">Метод IMetaDataImport::EnumMethods</span><span class="sxs-lookup"><span data-stu-id="f14b7-103">IMetaDataImport::EnumMethods Method</span></span>

<span data-ttu-id="f14b7-104">Перечисляет токены MethodDef, представляющие методы указанного типа.</span><span class="sxs-lookup"><span data-stu-id="f14b7-104">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f14b7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f14b7-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,
   [in]  mdTypeDef      cl,
   [out] mdMethodDef    rMethods[],
   [in]  ULONG          cMax,
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f14b7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f14b7-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="f14b7-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="f14b7-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="f14b7-108">При первом вызове этого метода это значение должно быть равно NULL.</span><span class="sxs-lookup"><span data-stu-id="f14b7-108">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="f14b7-109">окне Токен TypeDef, представляющий тип с методами для перечисления.</span><span class="sxs-lookup"><span data-stu-id="f14b7-109">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="f14b7-110">заполняет Массив для хранения токенов MethodDef.</span><span class="sxs-lookup"><span data-stu-id="f14b7-110">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f14b7-111">окне Максимальный размер `rMethods` массива MethodDef.</span><span class="sxs-lookup"><span data-stu-id="f14b7-111">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="f14b7-112">заполняет Число токенов MethodDef, возвращаемых в `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="f14b7-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f14b7-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f14b7-113">Return Value</span></span>  
  
|<span data-ttu-id="f14b7-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f14b7-114">HRESULT</span></span>|<span data-ttu-id="f14b7-115">Описание</span><span class="sxs-lookup"><span data-stu-id="f14b7-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f14b7-116">`EnumMethods` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="f14b7-116">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f14b7-117">Отсутствуют токены MethodDef для перечисления.</span><span class="sxs-lookup"><span data-stu-id="f14b7-117">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="f14b7-118">В этом случае значение `pcTokens` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="f14b7-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f14b7-119">Требования</span><span class="sxs-lookup"><span data-stu-id="f14b7-119">Requirements</span></span>  

 <span data-ttu-id="f14b7-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f14b7-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f14b7-121">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="f14b7-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f14b7-122">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f14b7-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f14b7-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f14b7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f14b7-124">См. также</span><span class="sxs-lookup"><span data-stu-id="f14b7-124">See also</span></span>

- [<span data-ttu-id="f14b7-125">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f14b7-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f14b7-126">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="f14b7-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
