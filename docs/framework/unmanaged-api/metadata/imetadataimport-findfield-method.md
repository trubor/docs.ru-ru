---
description: 'Дополнительные сведения: метод IMetaDataImport:: Финдфиелд'
title: Метод IMetaDataImport::FindField
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
ms.openlocfilehash: b8041a37b91f22722a05aec99c92c4f17c2b0610
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799308"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="62b70-103">Метод IMetaDataImport::FindField</span><span class="sxs-lookup"><span data-stu-id="62b70-103">IMetaDataImport::FindField Method</span></span>

<span data-ttu-id="62b70-104">Возвращает указатель на токен FieldDef для поля, заключенного в заданный объект с <xref:System.Type> указанным именем и сигнатурой метаданных.</span><span class="sxs-lookup"><span data-stu-id="62b70-104">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62b70-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="62b70-105">Syntax</span></span>  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62b70-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="62b70-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="62b70-107">окне Маркер TypeDef для класса или интерфейса, который заключает поле для поиска.</span><span class="sxs-lookup"><span data-stu-id="62b70-107">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="62b70-108">Если это значение равно `mdTokenNil` , поиск выполняется для глобальной переменной.</span><span class="sxs-lookup"><span data-stu-id="62b70-108">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="62b70-109">окне Имя искомого поля.</span><span class="sxs-lookup"><span data-stu-id="62b70-109">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="62b70-110">окне Указатель на сигнатуру двоичных метаданных поля.</span><span class="sxs-lookup"><span data-stu-id="62b70-110">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="62b70-111">окне Размер в байтах для `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="62b70-111">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="62b70-112">заполняет Указатель на соответствующий токен FieldDef.</span><span class="sxs-lookup"><span data-stu-id="62b70-112">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62b70-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="62b70-113">Remarks</span></span>  

 <span data-ttu-id="62b70-114">Поле указывается с помощью включающего его класса или интерфейса ( `td` ), имени ( `szName` ) и (при необходимости) его сигнатуры ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="62b70-114">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="62b70-115">Подпись, передаваемая в `FindField` , должна быть создана в текущей области, так как сигнатуры привязаны к определенной области.</span><span class="sxs-lookup"><span data-stu-id="62b70-115">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="62b70-116">Сигнатура может внедрять маркер, идентифицирующий включающий класс или тип значения.</span><span class="sxs-lookup"><span data-stu-id="62b70-116">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="62b70-117">(Токен является индексом локальной таблицы TypeDef).</span><span class="sxs-lookup"><span data-stu-id="62b70-117">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="62b70-118">Нельзя построить подпись времени выполнения вне контекста текущей области и использовать эту сигнатуру в качестве входных данных для `FindField` .</span><span class="sxs-lookup"><span data-stu-id="62b70-118">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="62b70-119">`FindField` находит только поля, которые были определены непосредственно в классе или интерфейсе; наследуемые поля не находятся.</span><span class="sxs-lookup"><span data-stu-id="62b70-119">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62b70-120">Требования</span><span class="sxs-lookup"><span data-stu-id="62b70-120">Requirements</span></span>  

 <span data-ttu-id="62b70-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62b70-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62b70-122">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="62b70-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="62b70-123">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62b70-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="62b70-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62b70-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62b70-125">См. также</span><span class="sxs-lookup"><span data-stu-id="62b70-125">See also</span></span>

- [<span data-ttu-id="62b70-126">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="62b70-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="62b70-127">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="62b70-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
