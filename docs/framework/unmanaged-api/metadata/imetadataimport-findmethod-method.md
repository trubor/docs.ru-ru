---
description: 'Дополнительные сведения: метод IMetaDataImport:: FindMethod'
title: Метод IMetaDataImport::FindMethod
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: 0d2866554fcb4dcf3984310e4da24d501f1fc7b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803559"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="dd168-103">Метод IMetaDataImport::FindMethod</span><span class="sxs-lookup"><span data-stu-id="dd168-103">IMetaDataImport::FindMethod Method</span></span>

<span data-ttu-id="dd168-104">Возвращает указатель на токен MethodDef для метода, заключенного в заданный объект с <xref:System.Type> указанным именем и сигнатурой метаданных.</span><span class="sxs-lookup"><span data-stu-id="dd168-104">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd168-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dd168-105">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd168-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dd168-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="dd168-107">окне `mdTypeDef` Токен для типа (класса или интерфейса), который включает член для поиска.</span><span class="sxs-lookup"><span data-stu-id="dd168-107">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="dd168-108">Если это значение равно `mdTokenNil` , то поиск выполняется для глобальной функции.</span><span class="sxs-lookup"><span data-stu-id="dd168-108">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="dd168-109">окне Имя искомого метода.</span><span class="sxs-lookup"><span data-stu-id="dd168-109">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="dd168-110">окне Указатель на сигнатуру двоичных метаданных метода.</span><span class="sxs-lookup"><span data-stu-id="dd168-110">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="dd168-111">окне Размер в байтах для `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="dd168-111">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="dd168-112">заполняет Указатель на соответствующий токен MethodDef.</span><span class="sxs-lookup"><span data-stu-id="dd168-112">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd168-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="dd168-113">Remarks</span></span>  

 <span data-ttu-id="dd168-114">Метод указывается с помощью включающего класса или интерфейса ( `td` ), его имени ( `szName` ) и (при необходимости) его сигнатуры ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="dd168-114">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="dd168-115">В классе или интерфейсе может быть несколько методов с одинаковым именем.</span><span class="sxs-lookup"><span data-stu-id="dd168-115">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="dd168-116">В этом случае передайте сигнатуру метода, чтобы найти уникальное совпадение.</span><span class="sxs-lookup"><span data-stu-id="dd168-116">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="dd168-117">Подпись, передаваемая в `FindMethod` , должна быть создана в текущей области, так как сигнатуры привязаны к определенной области.</span><span class="sxs-lookup"><span data-stu-id="dd168-117">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="dd168-118">Сигнатура может внедрять маркер, идентифицирующий включающий класс или тип значения.</span><span class="sxs-lookup"><span data-stu-id="dd168-118">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="dd168-119">Токен является индексом локальной таблицы TypeDef.</span><span class="sxs-lookup"><span data-stu-id="dd168-119">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="dd168-120">Нельзя построить сигнатуру времени выполнения вне контекста текущей области и использовать эту сигнатуру в качестве входных данных для входных данных `FindMethod` .</span><span class="sxs-lookup"><span data-stu-id="dd168-120">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="dd168-121">`FindMethod` находит только методы, которые были определены непосредственно в классе или интерфейсе; Он не находит унаследованные методы.</span><span class="sxs-lookup"><span data-stu-id="dd168-121">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd168-122">Требования</span><span class="sxs-lookup"><span data-stu-id="dd168-122">Requirements</span></span>  

 <span data-ttu-id="dd168-123">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd168-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd168-124">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="dd168-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd168-125">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dd168-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd168-126">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd168-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd168-127">См. также</span><span class="sxs-lookup"><span data-stu-id="dd168-127">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="dd168-128">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="dd168-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="dd168-129">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="dd168-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
