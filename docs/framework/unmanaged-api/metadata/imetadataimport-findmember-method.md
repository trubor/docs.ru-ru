---
description: 'Дополнительные сведения: метод IMetaDataImport:: Финдмембер'
title: Метод IMetaDataImport::FindMember
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
ms.openlocfilehash: fdf02f57b8c4ff912d732515576fc05045474517
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799295"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="6470c-103">Метод IMetaDataImport::FindMember</span><span class="sxs-lookup"><span data-stu-id="6470c-103">IMetaDataImport::FindMember Method</span></span>

<span data-ttu-id="6470c-104">Возвращает указатель на токен Мембердеф для поля или метода, заключенного в заданный объект с <xref:System.Type> указанным именем и сигнатурой метаданных.</span><span class="sxs-lookup"><span data-stu-id="6470c-104">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6470c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6470c-105">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6470c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6470c-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="6470c-107">окне Токен TypeDef для класса или интерфейса, который заключает элемент для поиска.</span><span class="sxs-lookup"><span data-stu-id="6470c-107">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="6470c-108">Если это значение равно `mdTokenNil` , поиск выполняется для глобальной переменной или глобальной функции.</span><span class="sxs-lookup"><span data-stu-id="6470c-108">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="6470c-109">окне Имя искомого элемента.</span><span class="sxs-lookup"><span data-stu-id="6470c-109">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="6470c-110">окне Указатель на сигнатуру двоичных метаданных элемента.</span><span class="sxs-lookup"><span data-stu-id="6470c-110">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="6470c-111">окне Размер в байтах для `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="6470c-111">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="6470c-112">заполняет Указатель на соответствующий токен Мембердеф.</span><span class="sxs-lookup"><span data-stu-id="6470c-112">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6470c-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="6470c-113">Remarks</span></span>  

 <span data-ttu-id="6470c-114">Элемент указывается с помощью включающего класса или интерфейса ( `td` ), его имени ( `szName` ) и (при необходимости) его сигнатуры ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="6470c-114">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="6470c-115">В классе или интерфейсе может быть несколько членов с одним и тем же именем.</span><span class="sxs-lookup"><span data-stu-id="6470c-115">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="6470c-116">В этом случае передайте сигнатуру члена, чтобы найти уникальное совпадение.</span><span class="sxs-lookup"><span data-stu-id="6470c-116">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="6470c-117">Подпись, передаваемая в `FindMember` , должна быть создана в текущей области, так как сигнатуры привязаны к определенной области.</span><span class="sxs-lookup"><span data-stu-id="6470c-117">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="6470c-118">Сигнатура может внедрять маркер, идентифицирующий включающий класс или тип значения.</span><span class="sxs-lookup"><span data-stu-id="6470c-118">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="6470c-119">Токен является индексом локальной таблицы TypeDef.</span><span class="sxs-lookup"><span data-stu-id="6470c-119">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="6470c-120">Нельзя построить сигнатуру времени выполнения вне контекста текущей области и использовать эту сигнатуру в качестве входных данных для входных данных `FindMember` .</span><span class="sxs-lookup"><span data-stu-id="6470c-120">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="6470c-121">`FindMember` находит только элементы, которые были определены непосредственно в классе или интерфейсе; Он не находит наследуемых членов.</span><span class="sxs-lookup"><span data-stu-id="6470c-121">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6470c-122">`FindMember` — Это вспомогательный метод.</span><span class="sxs-lookup"><span data-stu-id="6470c-122">`FindMember` is a helper method.</span></span> <span data-ttu-id="6470c-123">Он вызывает метод [IMetaDataImport:: FindMethod](imetadataimport-findmethod-method.md); Если этот вызов не находит совпадения, `FindMember` то вызывает метод [IMetaDataImport:: финдфиелд](imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="6470c-123">It calls [IMetaDataImport::FindMethod](imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6470c-124">Требования</span><span class="sxs-lookup"><span data-stu-id="6470c-124">Requirements</span></span>  

 <span data-ttu-id="6470c-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6470c-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6470c-126">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="6470c-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6470c-127">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6470c-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6470c-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6470c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6470c-129">См. также</span><span class="sxs-lookup"><span data-stu-id="6470c-129">See also</span></span>

- [<span data-ttu-id="6470c-130">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="6470c-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6470c-131">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="6470c-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
