---
description: 'Дополнительные сведения: метод IMetaDataImport:: Енуммемберрефс'
title: Метод IMetaDataImport::EnumMemberRefs
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMemberRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type:
- apiref
ms.openlocfilehash: 0c9b10342f73ae5b604ac25b6ff8ccec58deb5ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670948"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="98fa7-103">Метод IMetaDataImport::EnumMemberRefs</span><span class="sxs-lookup"><span data-stu-id="98fa7-103">IMetaDataImport::EnumMemberRefs Method</span></span>

<span data-ttu-id="98fa7-104">Перечисляет токены MemberRef, представляющие члены указанного типа.</span><span class="sxs-lookup"><span data-stu-id="98fa7-104">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98fa7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="98fa7-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,
   [in]   mdToken        tkParent,
   [out]  mdMemberRef    rMemberRefs[],
   [in]   ULONG          cMax,
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98fa7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="98fa7-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="98fa7-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="98fa7-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="98fa7-108">окне Токен TypeDef, TypeRef, MethodDef или ModuleRef для типа, элементы которого необходимо перечислить.</span><span class="sxs-lookup"><span data-stu-id="98fa7-108">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="98fa7-109">заполняет Массив, используемый для хранения токенов MemberRef.</span><span class="sxs-lookup"><span data-stu-id="98fa7-109">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="98fa7-110">[in] Максимальный размер массива `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="98fa7-110">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="98fa7-111">заполняет Фактическое число токенов MemberRef, возвращаемых в `rMemberRefs` .</span><span class="sxs-lookup"><span data-stu-id="98fa7-111">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98fa7-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="98fa7-112">Return Value</span></span>  
  
|<span data-ttu-id="98fa7-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98fa7-113">HRESULT</span></span>|<span data-ttu-id="98fa7-114">Описание</span><span class="sxs-lookup"><span data-stu-id="98fa7-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="98fa7-115">`EnumMemberRefs` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="98fa7-115">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="98fa7-116">Отсутствуют токены MemberRef для перечисления.</span><span class="sxs-lookup"><span data-stu-id="98fa7-116">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="98fa7-117">В этом случае значение `pcTokens` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="98fa7-117">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98fa7-118">Требования</span><span class="sxs-lookup"><span data-stu-id="98fa7-118">Requirements</span></span>  

 <span data-ttu-id="98fa7-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98fa7-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98fa7-120">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="98fa7-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98fa7-121">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="98fa7-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="98fa7-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98fa7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98fa7-123">См. также</span><span class="sxs-lookup"><span data-stu-id="98fa7-123">See also</span></span>

- [<span data-ttu-id="98fa7-124">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="98fa7-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="98fa7-125">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="98fa7-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
