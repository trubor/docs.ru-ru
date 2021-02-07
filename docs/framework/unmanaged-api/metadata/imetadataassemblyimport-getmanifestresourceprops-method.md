---
description: 'Дополнительные сведения о методе: IMetaDataAssemblyImport:: Жетманифестресаурцепропс'
title: Метод IMetaDataAssemblyImport::GetManifestResourceProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: d8f390f8eede5153df282cc30479ceff22fb552d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728292"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="61a7e-103">Метод IMetaDataAssemblyImport::GetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="61a7e-103">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>

<span data-ttu-id="61a7e-104">Возвращает набор свойств ресурса манифеста с указанной сигнатурой метаданных.</span><span class="sxs-lookup"><span data-stu-id="61a7e-104">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61a7e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="61a7e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] mdToken              *ptkImplementation,
    [out] DWORD                *pdwOffset,
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61a7e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="61a7e-106">Parameters</span></span>  

 `mdmr`  
 <span data-ttu-id="61a7e-107">окне `mdManifestResource` Токен, представляющий ресурс, для которого необходимо получить свойства.</span><span class="sxs-lookup"><span data-stu-id="61a7e-107">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="61a7e-108">заполняет Имя ресурса.</span><span class="sxs-lookup"><span data-stu-id="61a7e-108">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="61a7e-109">окне Размер (в расширенных символах) для `szName` .</span><span class="sxs-lookup"><span data-stu-id="61a7e-109">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="61a7e-110">заполняет Указатель на число расширенных символов, фактически возвращаемых в `szName` .</span><span class="sxs-lookup"><span data-stu-id="61a7e-110">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="61a7e-111">заполняет Указатель на `mdFile` маркер или `mdAssemblyRef` маркер, представляющий файл или сборку соответственно, который содержит ресурс.</span><span class="sxs-lookup"><span data-stu-id="61a7e-111">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="61a7e-112">заполняет Указатель на значение, указывающее смещение к началу ресурса в файле.</span><span class="sxs-lookup"><span data-stu-id="61a7e-112">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="61a7e-113">заполняет Указатель на флаги, описывающие метаданные, применяемые к ресурсу.</span><span class="sxs-lookup"><span data-stu-id="61a7e-113">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="61a7e-114">Значение Flags является сочетанием одного или нескольких значений [корманифестресаурцефлагс](cormanifestresourceflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="61a7e-114">The flags value is a combination of one or more [CorManifestResourceFlags](cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61a7e-115">Требования</span><span class="sxs-lookup"><span data-stu-id="61a7e-115">Requirements</span></span>  

 <span data-ttu-id="61a7e-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61a7e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61a7e-117">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="61a7e-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61a7e-118">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="61a7e-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="61a7e-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61a7e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a7e-120">См. также</span><span class="sxs-lookup"><span data-stu-id="61a7e-120">See also</span></span>

- [<span data-ttu-id="61a7e-121">Интерфейс IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="61a7e-121">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
