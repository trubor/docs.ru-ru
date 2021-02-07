---
description: 'Дополнительные сведения: метод IMetaDataImport:: Финдмемберреф'
title: Метод IMetaDataImport::FindMemberRef
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: 301d4dc88b36ca2284ca3b8d70444820befdc0aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745584"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="1e4f7-103">Метод IMetaDataImport::FindMemberRef</span><span class="sxs-lookup"><span data-stu-id="1e4f7-103">IMetaDataImport::FindMemberRef Method</span></span>

<span data-ttu-id="1e4f7-104">Возвращает указатель на токен MemberRef для ссылки на элемент, заключенный в заданный объект с <xref:System.Type> указанным именем и сигнатурой метаданных.</span><span class="sxs-lookup"><span data-stu-id="1e4f7-104">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e4f7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1e4f7-105">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e4f7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1e4f7-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="1e4f7-107">окне Токен TypeRef для класса или интерфейса, который заключает в себя ссылку на элемент для поиска.</span><span class="sxs-lookup"><span data-stu-id="1e4f7-107">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="1e4f7-108">Если это значение равно `mdTokenNil` , поиск выполняется для глобальной переменной или ссылки на глобальную функцию.</span><span class="sxs-lookup"><span data-stu-id="1e4f7-108">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="1e4f7-109">окне Имя искомой ссылки на член.</span><span class="sxs-lookup"><span data-stu-id="1e4f7-109">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="1e4f7-110">окне Указатель на сигнатуру двоичных метаданных ссылки на элемент.</span><span class="sxs-lookup"><span data-stu-id="1e4f7-110">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="1e4f7-111">окне Размер в байтах для `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="1e4f7-111">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="1e4f7-112">заполняет Указатель на соответствующий токен MemberRef.</span><span class="sxs-lookup"><span data-stu-id="1e4f7-112">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e4f7-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="1e4f7-113">Remarks</span></span>  

 <span data-ttu-id="1e4f7-114">Элемент указывается с помощью включающего класса или интерфейса ( `td` ), его имени ( `szName` ) и (при необходимости) его сигнатуры ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="1e4f7-114">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="1e4f7-115">Подпись, передаваемая в `FindMemberRef` , должна быть создана в текущей области, так как сигнатуры привязаны к определенной области.</span><span class="sxs-lookup"><span data-stu-id="1e4f7-115">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="1e4f7-116">Сигнатура может внедрять маркер, идентифицирующий включающий класс или тип значения.</span><span class="sxs-lookup"><span data-stu-id="1e4f7-116">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="1e4f7-117">Токен является индексом локальной таблицы TypeDef.</span><span class="sxs-lookup"><span data-stu-id="1e4f7-117">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="1e4f7-118">Нельзя построить подпись времени выполнения вне контекста текущей области и использовать эту сигнатуру в качестве входных данных для `FindMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="1e4f7-118">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="1e4f7-119">`FindMemberRef` находит только ссылки на элементы, которые были определены непосредственно в классе или интерфейсе; Он не находит унаследованные ссылки на члены.</span><span class="sxs-lookup"><span data-stu-id="1e4f7-119">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e4f7-120">Требования</span><span class="sxs-lookup"><span data-stu-id="1e4f7-120">Requirements</span></span>  

 <span data-ttu-id="1e4f7-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e4f7-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e4f7-122">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="1e4f7-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1e4f7-123">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1e4f7-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1e4f7-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e4f7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e4f7-125">См. также</span><span class="sxs-lookup"><span data-stu-id="1e4f7-125">See also</span></span>

- [<span data-ttu-id="1e4f7-126">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="1e4f7-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="1e4f7-127">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="1e4f7-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
