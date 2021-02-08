---
description: 'Дополнительные сведения: метод IMetaDataImport:: Жетинтерфацеимплпропс'
title: Метод IMetaDataImport::GetInterfaceImplProps
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
ms.openlocfilehash: 6b3c9394bcf37f700c84e1fda0b785dc0c3f4713
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783915"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="e0f8b-103">Метод IMetaDataImport::GetInterfaceImplProps</span><span class="sxs-lookup"><span data-stu-id="e0f8b-103">IMetaDataImport::GetInterfaceImplProps Method</span></span>

<span data-ttu-id="e0f8b-104">Возвращает указатель на маркеры метаданных для <xref:System.Type> , который реализует указанный метод, и для интерфейса, объявляющего этот метод.</span><span class="sxs-lookup"><span data-stu-id="e0f8b-104">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="e0f8b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e0f8b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0f8b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e0f8b-106">Parameters</span></span>  

 `iiImpl`  
 <span data-ttu-id="e0f8b-107">окне Токен метаданных, представляющий метод, для которого необходимо вернуть маркеры класса и интерфейса.</span><span class="sxs-lookup"><span data-stu-id="e0f8b-107">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="e0f8b-108">заполняет Маркер метаданных, представляющий класс, реализующий метод.</span><span class="sxs-lookup"><span data-stu-id="e0f8b-108">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="e0f8b-109">заполняет Токен метаданных, представляющий интерфейс, определяющий реализованный метод.</span><span class="sxs-lookup"><span data-stu-id="e0f8b-109">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="e0f8b-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="e0f8b-110">Remarks</span></span>

 <span data-ttu-id="e0f8b-111">Получить значение для можно `iImpl` путем вызова метода [енуминтерфацеимплс](imetadataimport-enuminterfaceimpls-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e0f8b-111">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>

 <span data-ttu-id="e0f8b-112">Например, предположим, что класс имеет `mdTypeDef` значение маркера 0x02000007 и реализует три интерфейса, типы которых имеют токены:</span><span class="sxs-lookup"><span data-stu-id="e0f8b-112">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span>

- <span data-ttu-id="e0f8b-113">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="e0f8b-113">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="e0f8b-114">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="e0f8b-114">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="e0f8b-115">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="e0f8b-115">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="e0f8b-116">По сути, эта информация хранится в таблице реализации интерфейса следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e0f8b-116">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="e0f8b-117">Номер строки</span><span class="sxs-lookup"><span data-stu-id="e0f8b-117">Row number</span></span> | <span data-ttu-id="e0f8b-118">Токен класса</span><span class="sxs-lookup"><span data-stu-id="e0f8b-118">Class token</span></span> | <span data-ttu-id="e0f8b-119">Токен интерфейса</span><span class="sxs-lookup"><span data-stu-id="e0f8b-119">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="e0f8b-120">4</span><span class="sxs-lookup"><span data-stu-id="e0f8b-120">4</span></span>          |             |                 |
| <span data-ttu-id="e0f8b-121">5</span><span class="sxs-lookup"><span data-stu-id="e0f8b-121">5</span></span>          | <span data-ttu-id="e0f8b-122">02000007</span><span class="sxs-lookup"><span data-stu-id="e0f8b-122">02000007</span></span>    | <span data-ttu-id="e0f8b-123">02000003</span><span class="sxs-lookup"><span data-stu-id="e0f8b-123">02000003</span></span>        |
| <span data-ttu-id="e0f8b-124">6</span><span class="sxs-lookup"><span data-stu-id="e0f8b-124">6</span></span>          | <span data-ttu-id="e0f8b-125">02000007</span><span class="sxs-lookup"><span data-stu-id="e0f8b-125">02000007</span></span>    | <span data-ttu-id="e0f8b-126">0100000A</span><span class="sxs-lookup"><span data-stu-id="e0f8b-126">0100000A</span></span>        |
| <span data-ttu-id="e0f8b-127">7</span><span class="sxs-lookup"><span data-stu-id="e0f8b-127">7</span></span>          |             |                 |
| <span data-ttu-id="e0f8b-128">8</span><span class="sxs-lookup"><span data-stu-id="e0f8b-128">8</span></span>          | <span data-ttu-id="e0f8b-129">02000007</span><span class="sxs-lookup"><span data-stu-id="e0f8b-129">02000007</span></span>    | <span data-ttu-id="e0f8b-130">0200001C</span><span class="sxs-lookup"><span data-stu-id="e0f8b-130">0200001C</span></span>        |

<span data-ttu-id="e0f8b-131">Помните, что маркер является 4-байтовым значением:</span><span class="sxs-lookup"><span data-stu-id="e0f8b-131">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="e0f8b-132">3 младших байта содержат номер строки или RID.</span><span class="sxs-lookup"><span data-stu-id="e0f8b-132">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="e0f8b-133">Верхний байт содержит тип токена — 0x09 для `mdtInterfaceImpl` .</span><span class="sxs-lookup"><span data-stu-id="e0f8b-133">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="e0f8b-134">`GetInterfaceImplProps` Возвращает информацию, удерживаемую в строке, токен которой вы задаете в `iImpl` аргументе.</span><span class="sxs-lookup"><span data-stu-id="e0f8b-134">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="e0f8b-135">Требования</span><span class="sxs-lookup"><span data-stu-id="e0f8b-135">Requirements</span></span>  

 <span data-ttu-id="e0f8b-136">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0f8b-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0f8b-137">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="e0f8b-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0f8b-138">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e0f8b-138">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e0f8b-139">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0f8b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f8b-140">См. также</span><span class="sxs-lookup"><span data-stu-id="e0f8b-140">See also</span></span>

- [<span data-ttu-id="e0f8b-141">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e0f8b-141">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e0f8b-142">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="e0f8b-142">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
