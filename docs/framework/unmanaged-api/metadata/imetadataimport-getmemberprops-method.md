---
description: 'Дополнительные сведения: метод IMetaDataImport:: Жетмемберпропс'
title: Метод IMetaDataImport::GetMemberProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
ms.openlocfilehash: 073c8fae06c3df69f0b3152b109417b818637d1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783902"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="b075e-103">Метод IMetaDataImport::GetMemberProps</span><span class="sxs-lookup"><span data-stu-id="b075e-103">IMetaDataImport::GetMemberProps Method</span></span>

<span data-ttu-id="b075e-104">Возвращает сведения, хранящиеся в метаданных для указанного определения элемента, включая имя, двоичную подпись и относительный виртуальный адрес элемента, <xref:System.Type> на который ссылается указанный токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="b075e-104">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="b075e-105">Это простой вспомогательный метод: Если *МБ* является MethodDef, то вызывается **жетмесодпропс** . Если *МБ* является FieldDef, вызывается **жетфиелдпропс** .</span><span class="sxs-lookup"><span data-stu-id="b075e-105">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="b075e-106">Дополнительные сведения см. в этих других методах.</span><span class="sxs-lookup"><span data-stu-id="b075e-106">See these other methods for details.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="b075e-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b075e-107">Syntax</span></span>  
  
```cpp  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,
   [in]  ULONG             cchMember,
   [out] ULONG             *pchMember,
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] ULONG             *pulCodeRVA,
   [out] DWORD             *pdwImplFlags,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b075e-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="b075e-108">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="b075e-109">окне Токен, ссылающийся на элемент, для которого необходимо получить связанные метаданные.</span><span class="sxs-lookup"><span data-stu-id="b075e-109">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="b075e-110">заполняет Указатель на маркер метаданных, представляющий класс члена.</span><span class="sxs-lookup"><span data-stu-id="b075e-110">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="b075e-111">заполняет Имя элемента.</span><span class="sxs-lookup"><span data-stu-id="b075e-111">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="b075e-112">окне Размер в расширенных символах `szMember` буфера.</span><span class="sxs-lookup"><span data-stu-id="b075e-112">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="b075e-113">заполняет Размер в расширенных символах возвращаемого имени.</span><span class="sxs-lookup"><span data-stu-id="b075e-113">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="b075e-114">заполняет Все значения флагов, примененные к элементу.</span><span class="sxs-lookup"><span data-stu-id="b075e-114">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="b075e-115">заполняет Указатель на сигнатуру двоичных метаданных элемента.</span><span class="sxs-lookup"><span data-stu-id="b075e-115">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="b075e-116">заполняет Размер в байтах для `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="b075e-116">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="b075e-117">заполняет Указатель на относительный виртуальный адрес элемента.</span><span class="sxs-lookup"><span data-stu-id="b075e-117">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="b075e-118">заполняет Любые флаги реализации метода, связанные с элементом.</span><span class="sxs-lookup"><span data-stu-id="b075e-118">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="b075e-119">заполняет Флаг, помечающий <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="b075e-119">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="b075e-120">Это одно из `ELEMENT_TYPE_*` значений.</span><span class="sxs-lookup"><span data-stu-id="b075e-120">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="b075e-121">заполняет Константное строковое значение, возвращаемое этим элементом.</span><span class="sxs-lookup"><span data-stu-id="b075e-121">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="b075e-122">заполняет Размер в символах `ppValue` или нуль, если не содержит `ppValue` строку.</span><span class="sxs-lookup"><span data-stu-id="b075e-122">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b075e-123">Требования</span><span class="sxs-lookup"><span data-stu-id="b075e-123">Requirements</span></span>  

 <span data-ttu-id="b075e-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b075e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b075e-125">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="b075e-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b075e-126">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b075e-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b075e-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b075e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b075e-128">См. также</span><span class="sxs-lookup"><span data-stu-id="b075e-128">See also</span></span>

- [<span data-ttu-id="b075e-129">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b075e-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b075e-130">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b075e-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
