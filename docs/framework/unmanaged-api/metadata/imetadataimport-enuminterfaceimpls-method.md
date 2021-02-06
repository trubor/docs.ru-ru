---
description: 'Дополнительные сведения: метод IMetaDataImport:: Енуминтерфацеимплс'
title: Метод IMetaDataImport::EnumInterfaceImpls
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: 5276d1edb3be0cae76b18a06241dc6b9952e1a72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649420"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="f53ee-103">Метод IMetaDataImport::EnumInterfaceImpls</span><span class="sxs-lookup"><span data-stu-id="f53ee-103">IMetaDataImport::EnumInterfaceImpls Method</span></span>

<span data-ttu-id="f53ee-104">Перечисляет все интерфейсы, реализованные указанным `TypeDef` .</span><span class="sxs-lookup"><span data-stu-id="f53ee-104">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="f53ee-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f53ee-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f53ee-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f53ee-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="f53ee-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="f53ee-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="f53ee-108">окне Токен TypeDef, маркеры MethodDef которого представляют реализации интерфейса для перечисления.</span><span class="sxs-lookup"><span data-stu-id="f53ee-108">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="f53ee-109">заполняет Массив, используемый для хранения маркеров MethodDef.</span><span class="sxs-lookup"><span data-stu-id="f53ee-109">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f53ee-110">окне Максимальная длина `rImpls` массива.</span><span class="sxs-lookup"><span data-stu-id="f53ee-110">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="f53ee-111">заполняет Фактическое число токенов, возвращаемых в `rImpls` .</span><span class="sxs-lookup"><span data-stu-id="f53ee-111">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f53ee-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f53ee-112">Return Value</span></span>  
  
|<span data-ttu-id="f53ee-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f53ee-113">HRESULT</span></span>|<span data-ttu-id="f53ee-114">Описание</span><span class="sxs-lookup"><span data-stu-id="f53ee-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f53ee-115">`EnumInterfaceImpls` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="f53ee-115">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f53ee-116">Отсутствуют токены MethodDef для перечисления.</span><span class="sxs-lookup"><span data-stu-id="f53ee-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="f53ee-117">В этом случае `pcImpls` значение равно нулю.</span><span class="sxs-lookup"><span data-stu-id="f53ee-117">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="f53ee-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="f53ee-118">Remarks</span></span>

<span data-ttu-id="f53ee-119">Перечисление Возвращает коллекцию `mdInterfaceImpl` токенов для каждого интерфейса, реализованного с помощью указанного объекта `TypeDef` .</span><span class="sxs-lookup"><span data-stu-id="f53ee-119">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="f53ee-120">Маркеры интерфейса возвращаются в том порядке, в котором были указаны интерфейсы (с помощью `DefineTypeDef` или `SetTypeDefProps` ).</span><span class="sxs-lookup"><span data-stu-id="f53ee-120">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="f53ee-121">Свойства возвращаемых `mdInterfaceImpl` токенов можно запрашивать с помощью [жетинтерфацеимплпропс](imetadataimport-getinterfaceimplprops-method.md).</span><span class="sxs-lookup"><span data-stu-id="f53ee-121">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="f53ee-122">Требования</span><span class="sxs-lookup"><span data-stu-id="f53ee-122">Requirements</span></span>  

 <span data-ttu-id="f53ee-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f53ee-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f53ee-124">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="f53ee-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f53ee-125">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f53ee-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f53ee-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f53ee-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f53ee-127">См. также</span><span class="sxs-lookup"><span data-stu-id="f53ee-127">See also</span></span>

- [<span data-ttu-id="f53ee-128">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f53ee-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f53ee-129">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="f53ee-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
