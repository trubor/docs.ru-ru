---
description: 'Дополнительные сведения: метод IMetaDataImport:: Енумунресолведмесодс'
title: Метод IMetaDataImport::EnumUnresolvedMethods
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
ms.openlocfilehash: e894ecdde91a2263783234d73fa50d890a13e413
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799334"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="a1280-103">Метод IMetaDataImport::EnumUnresolvedMethods</span><span class="sxs-lookup"><span data-stu-id="a1280-103">IMetaDataImport::EnumUnresolvedMethods Method</span></span>

<span data-ttu-id="a1280-104">Перечисляет токены MemberDef, представляющие неразрешенные методы в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="a1280-104">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1280-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a1280-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1280-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a1280-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="a1280-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="a1280-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a1280-108">При первом вызове этого метода это значение должно быть равно NULL.</span><span class="sxs-lookup"><span data-stu-id="a1280-108">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="a1280-109">заполняет Массив, используемый для хранения маркеров Мембердеф.</span><span class="sxs-lookup"><span data-stu-id="a1280-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a1280-110">[in] Максимальный размер массива `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="a1280-110">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a1280-111">заполняет Число токенов Мембердеф, возвращаемых в `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="a1280-111">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1280-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a1280-112">Return Value</span></span>  
  
|<span data-ttu-id="a1280-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1280-113">HRESULT</span></span>|<span data-ttu-id="a1280-114">Описание</span><span class="sxs-lookup"><span data-stu-id="a1280-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a1280-115">`EnumUnresolvedMethods` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="a1280-115">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a1280-116">Нет токенов для перечисления.</span><span class="sxs-lookup"><span data-stu-id="a1280-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="a1280-117">В этом случае значение `pcTokens` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="a1280-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1280-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="a1280-118">Remarks</span></span>  

 <span data-ttu-id="a1280-119">Неразрешенный метод — это тот, который был объявлен, но не реализован.</span><span class="sxs-lookup"><span data-stu-id="a1280-119">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="a1280-120">Метод включается в перечисление, если метод помечен `miForwardRef` , а либо `mdPinvokeImpl` либо `miRuntime` имеет значение 0.</span><span class="sxs-lookup"><span data-stu-id="a1280-120">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="a1280-121">Иными словами, неразрешенный метод — это метод класса, который помечен, `miForwardRef` но не реализован в неуправляемом коде (достигается через PInvoke) и не реализуется внутри самой среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="a1280-121">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="a1280-122">Перечисление исключает все методы, определенные либо в области видимости модуля (Globals), либо в интерфейсах или в абстрактных классах.</span><span class="sxs-lookup"><span data-stu-id="a1280-122">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1280-123">Требования</span><span class="sxs-lookup"><span data-stu-id="a1280-123">Requirements</span></span>  

 <span data-ttu-id="a1280-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1280-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1280-125">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="a1280-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a1280-126">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a1280-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a1280-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1280-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1280-128">См. также</span><span class="sxs-lookup"><span data-stu-id="a1280-128">See also</span></span>

- [<span data-ttu-id="a1280-129">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="a1280-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a1280-130">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="a1280-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
