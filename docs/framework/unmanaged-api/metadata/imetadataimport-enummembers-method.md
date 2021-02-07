---
description: 'Дополнительные сведения: метод IMetaDataImport:: EnumMembers'
title: Метод IMetaDataImport::EnumMembers
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
ms.openlocfilehash: 3b56b25c6c581f6bfc3303a55a49a12ffcc73494
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670818"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="4e2a1-103">Метод IMetaDataImport::EnumMembers</span><span class="sxs-lookup"><span data-stu-id="4e2a1-103">IMetaDataImport::EnumMembers Method</span></span>

<span data-ttu-id="4e2a1-104">Перечисляет токены MemberDef, представляющие члены указанного типа.</span><span class="sxs-lookup"><span data-stu-id="4e2a1-104">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e2a1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4e2a1-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e2a1-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4e2a1-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="4e2a1-107">[вход, выход] Указатель на перечислитель.</span><span class="sxs-lookup"><span data-stu-id="4e2a1-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="4e2a1-108">окне Токен TypeDef, представляющий тип, элементы которого необходимо перечислить.</span><span class="sxs-lookup"><span data-stu-id="4e2a1-108">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="4e2a1-109">заполняет Массив, используемый для хранения маркеров Мембердеф.</span><span class="sxs-lookup"><span data-stu-id="4e2a1-109">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4e2a1-110">[in] Максимальный размер массива `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="4e2a1-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4e2a1-111">заполняет Фактическое число токенов Мембердеф, возвращаемых в `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="4e2a1-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e2a1-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4e2a1-112">Return Value</span></span>  
  
|<span data-ttu-id="4e2a1-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4e2a1-113">HRESULT</span></span>|<span data-ttu-id="4e2a1-114">Описание</span><span class="sxs-lookup"><span data-stu-id="4e2a1-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4e2a1-115">`EnumMembers` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="4e2a1-115">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4e2a1-116">Нет токенов Мембердеф для перечисления.</span><span class="sxs-lookup"><span data-stu-id="4e2a1-116">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="4e2a1-117">В этом случае значение `pcTokens` равно нулю.</span><span class="sxs-lookup"><span data-stu-id="4e2a1-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e2a1-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="4e2a1-118">Remarks</span></span>  

 <span data-ttu-id="4e2a1-119">При перечислении коллекций элементов для класса `EnumMembers` возвращает только элементы (поля и методы, но **не** свойства или события), определенные непосредственно в классе.</span><span class="sxs-lookup"><span data-stu-id="4e2a1-119">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="4e2a1-120">Он не возвращает члены, наследуемые классом, даже если класс предоставляет реализацию для этих унаследованных членов.</span><span class="sxs-lookup"><span data-stu-id="4e2a1-120">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="4e2a1-121">Чтобы перечислить унаследованные члены, вызывающий объект должен явно пройти по цепочке наследования.</span><span class="sxs-lookup"><span data-stu-id="4e2a1-121">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="4e2a1-122">Обратите внимание, что правила для цепочки наследования могут различаться в зависимости от языка или компилятора, который выдал исходные метаданные.</span><span class="sxs-lookup"><span data-stu-id="4e2a1-122">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>

 <span data-ttu-id="4e2a1-123">Свойства и события не перечисляются с помощью `EnumMembers` .</span><span class="sxs-lookup"><span data-stu-id="4e2a1-123">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="4e2a1-124">Чтобы перечислить их, используйте [енумпропертиес](imetadataimport-enumproperties-method.md) или [EnumEvents](imetadataimport-enumevents-method.md).</span><span class="sxs-lookup"><span data-stu-id="4e2a1-124">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="4e2a1-125">Требования</span><span class="sxs-lookup"><span data-stu-id="4e2a1-125">Requirements</span></span>  

 <span data-ttu-id="4e2a1-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e2a1-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e2a1-127">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="4e2a1-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4e2a1-128">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4e2a1-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4e2a1-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e2a1-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e2a1-130">См. также</span><span class="sxs-lookup"><span data-stu-id="4e2a1-130">See also</span></span>

- [<span data-ttu-id="4e2a1-131">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="4e2a1-131">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4e2a1-132">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="4e2a1-132">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
