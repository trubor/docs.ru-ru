---
description: 'Дополнительные сведения: метод IMetaDataImport:: Жеттипедефпропс'
title: Метод IMetaDataImport::GetTypeDefProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
ms.openlocfilehash: da5c6117f636098ed0cfeddc541979d235729d63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799282"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="8fc7e-103">Метод IMetaDataImport::GetTypeDefProps</span><span class="sxs-lookup"><span data-stu-id="8fc7e-103">IMetaDataImport::GetTypeDefProps Method</span></span>

<span data-ttu-id="8fc7e-104">Возвращает сведения о метаданных для, <xref:System.Type> представленного указанным маркером TypeDef.</span><span class="sxs-lookup"><span data-stu-id="8fc7e-104">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc7e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8fc7e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fc7e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8fc7e-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="8fc7e-107">окне Токен TypeDef, представляющий тип, для которого возвращаются метаданные.</span><span class="sxs-lookup"><span data-stu-id="8fc7e-107">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="8fc7e-108">заполняет Буфер, содержащий имя типа.</span><span class="sxs-lookup"><span data-stu-id="8fc7e-108">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="8fc7e-109">окне Размер в расширенных символах `szTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="8fc7e-109">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="8fc7e-110">заполняет Число расширенных символов, возвращаемых в `szTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="8fc7e-110">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="8fc7e-111">заполняет Указатель на любые флаги, изменяющие определение типа.</span><span class="sxs-lookup"><span data-stu-id="8fc7e-111">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="8fc7e-112">Это значение является битовой маской из перечисления [кортипеаттр](cortypeattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="8fc7e-112">This value is a bitmask from the [CorTypeAttr](cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="8fc7e-113">заполняет Токен метаданных TypeDef или TypeRef, представляющий базовый тип запрошенного типа.</span><span class="sxs-lookup"><span data-stu-id="8fc7e-113">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fc7e-114">Требования</span><span class="sxs-lookup"><span data-stu-id="8fc7e-114">Requirements</span></span>  

 <span data-ttu-id="8fc7e-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fc7e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fc7e-116">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="8fc7e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8fc7e-117">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8fc7e-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8fc7e-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fc7e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc7e-119">См. также</span><span class="sxs-lookup"><span data-stu-id="8fc7e-119">See also</span></span>

- [<span data-ttu-id="8fc7e-120">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="8fc7e-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8fc7e-121">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="8fc7e-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
