---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetTypeRefProps'
title: Метод IMetaDataImport::GetTypeRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
ms.openlocfilehash: 8d4741ca2d04aaa4af48fee2cf6485de3403a525
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789129"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="cacb9-103">Метод IMetaDataImport::GetTypeRefProps</span><span class="sxs-lookup"><span data-stu-id="cacb9-103">IMetaDataImport::GetTypeRefProps Method</span></span>

<span data-ttu-id="cacb9-104">Возвращает метаданные, связанные с <xref:System.Type> объектом, на который ссылается указанный токен TypeRef.</span><span class="sxs-lookup"><span data-stu-id="cacb9-104">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cacb9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cacb9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cacb9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cacb9-106">Parameters</span></span>  

 `tr`  
 <span data-ttu-id="cacb9-107">окне Токен TypeRef, представляющий тип, для которого возвращаются метаданные.</span><span class="sxs-lookup"><span data-stu-id="cacb9-107">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="cacb9-108">заполняет Указатель на область, в которой создана ссылка.</span><span class="sxs-lookup"><span data-stu-id="cacb9-108">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="cacb9-109">Это значение является токеном AssemblyRef или ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="cacb9-109">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="cacb9-110">заполняет Буфер, содержащий имя типа.</span><span class="sxs-lookup"><span data-stu-id="cacb9-110">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="cacb9-111">окне Запрошенный размер в расширенных символах `szName` .</span><span class="sxs-lookup"><span data-stu-id="cacb9-111">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="cacb9-112">заполняет Возвращаемый размер в расширенных символах `szName` .</span><span class="sxs-lookup"><span data-stu-id="cacb9-112">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cacb9-113">Требования</span><span class="sxs-lookup"><span data-stu-id="cacb9-113">Requirements</span></span>  

 <span data-ttu-id="cacb9-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cacb9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cacb9-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="cacb9-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cacb9-116">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cacb9-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cacb9-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cacb9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cacb9-118">См. также</span><span class="sxs-lookup"><span data-stu-id="cacb9-118">See also</span></span>

- [<span data-ttu-id="cacb9-119">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="cacb9-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="cacb9-120">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="cacb9-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
