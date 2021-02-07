---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetParamProps'
title: Метод IMetaDataImport::GetParamProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamProps
helpviewer_keywords:
- IMetaDataImport::GetParamProps method [.NET Framework metadata]
- GetParamProps method [.NET Framework metadata]
ms.assetid: 4d5e5f00-bcab-4f41-b191-176511a186a7
topic_type:
- apiref
ms.openlocfilehash: 2c48215836dfb3ae44edc9a2bf10d4028fd82bb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728123"
---
# <a name="imetadataimportgetparamprops-method"></a><span data-ttu-id="c4a63-103">Метод IMetaDataImport::GetParamProps</span><span class="sxs-lookup"><span data-stu-id="c4a63-103">IMetaDataImport::GetParamProps Method</span></span>

<span data-ttu-id="c4a63-104">Возвращает значения метаданных для параметра, на который ссылается указанный токен ParamDef.</span><span class="sxs-lookup"><span data-stu-id="c4a63-104">Gets metadata values for the parameter referenced by the specified ParamDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4a63-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c4a63-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParamProps (  
   [in]  mdParamDef      tk,  
   [out] mdMethodDef     *pmd,  
   [out] ULONG           *pulSequence,  
   [out] LPWSTR          szName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName,  
   [out] DWORD           *pdwAttr,  
   [out] DWORD           *pdwCPlusTypeFlag,  
   [out] UVCP_CONSTANT   *ppValue,  
   [out] ULONG           *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4a63-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c4a63-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="c4a63-107">окне Токен Парамдеф, представляющий параметр, для которого возвращаются метаданные.</span><span class="sxs-lookup"><span data-stu-id="c4a63-107">[in] A ParamDef token that represents the parameter to return metadata for.</span></span>  
  
 `pmd`  
 <span data-ttu-id="c4a63-108">заполняет Указатель на токен MethodDef, представляющий метод, который принимает параметр.</span><span class="sxs-lookup"><span data-stu-id="c4a63-108">[out] A pointer to a MethodDef token representing the method that takes the parameter.</span></span>  
  
 `pulSequence`  
 <span data-ttu-id="c4a63-109">заполняет Порядковый номер параметра в списке аргументов метода.</span><span class="sxs-lookup"><span data-stu-id="c4a63-109">[out] The ordinal position of the parameter in the method argument list.</span></span>  
  
 `szName`  
 <span data-ttu-id="c4a63-110">заполняет Буфер для хранения имени параметра.</span><span class="sxs-lookup"><span data-stu-id="c4a63-110">[out] A buffer to hold the name of the parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c4a63-111">окне Запрошенный размер в расширенных символах `szName` .</span><span class="sxs-lookup"><span data-stu-id="c4a63-111">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="c4a63-112">заполняет Возвращаемый размер в расширенных символах `szName` .</span><span class="sxs-lookup"><span data-stu-id="c4a63-112">[out] The returned size in wide characters of `szName`.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="c4a63-113">заполняет Указатель на любые флаги атрибутов, связанные с параметром.</span><span class="sxs-lookup"><span data-stu-id="c4a63-113">[out] A pointer to any attribute flags associated with the parameter.</span></span> <span data-ttu-id="c4a63-114">Это битовая маска `CorParamAttr` значений.</span><span class="sxs-lookup"><span data-stu-id="c4a63-114">This is a bitmask of `CorParamAttr` values.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="c4a63-115">заполняет Указатель на флаг, указывающий, что параметр является <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="c4a63-115">[out] A pointer to a flag specifying that the parameter is a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c4a63-116">заполняет Указатель на константную строку, возвращенную параметром.</span><span class="sxs-lookup"><span data-stu-id="c4a63-116">[out] A pointer to a constant string returned by the parameter.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="c4a63-117">заполняет Размер `ppValue` в расширенных символах или нуль, если не содержит `ppValue` строку.</span><span class="sxs-lookup"><span data-stu-id="c4a63-117">[out] The size of `ppValue` in wide characters, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4a63-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="c4a63-118">Remarks</span></span>

<span data-ttu-id="c4a63-119">Значения последовательности в `pulSequence` аргументе начинаются с 1 для параметров.</span><span class="sxs-lookup"><span data-stu-id="c4a63-119">The sequence values in `pulSequence` begin with 1 for parameters.</span></span> <span data-ttu-id="c4a63-120">Возвращаемое значение имеет порядковый номер 0.</span><span class="sxs-lookup"><span data-stu-id="c4a63-120">A return value has a sequence number of 0.</span></span>

## <a name="requirements"></a><span data-ttu-id="c4a63-121">Требования</span><span class="sxs-lookup"><span data-stu-id="c4a63-121">Requirements</span></span>  

 <span data-ttu-id="c4a63-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4a63-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4a63-123">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="c4a63-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c4a63-124">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c4a63-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c4a63-125">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4a63-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a63-126">См. также</span><span class="sxs-lookup"><span data-stu-id="c4a63-126">See also</span></span>

- [<span data-ttu-id="c4a63-127">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c4a63-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c4a63-128">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c4a63-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
