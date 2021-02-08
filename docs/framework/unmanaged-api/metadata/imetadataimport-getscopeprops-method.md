---
description: 'Дополнительные сведения: метод IMetaDataImport:: Жетскопепропс'
title: Метод IMetaDataImport::GetScopeProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
ms.openlocfilehash: 2ed7c08cc876f467a46fe38c7c27719e5608e623
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789155"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="af651-103">Метод IMetaDataImport::GetScopeProps</span><span class="sxs-lookup"><span data-stu-id="af651-103">IMetaDataImport::GetScopeProps Method</span></span>

<span data-ttu-id="af651-104">Возвращает имя и при необходимости идентификатор версии сборки или модуля в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="af651-104">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af651-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="af651-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af651-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="af651-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="af651-107">заполняет Буфер для имени сборки или модуля.</span><span class="sxs-lookup"><span data-stu-id="af651-107">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="af651-108">окне Размер в расширенных символах `szName` .</span><span class="sxs-lookup"><span data-stu-id="af651-108">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="af651-109">заполняет Число расширенных символов, возвращаемых в `szName` .</span><span class="sxs-lookup"><span data-stu-id="af651-109">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="af651-110">[out, необязательно] Указатель на идентификатор GUID, однозначно определяющий версию сборки или модуля.</span><span class="sxs-lookup"><span data-stu-id="af651-110">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af651-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="af651-111">Remarks</span></span>  

 <span data-ttu-id="af651-112">Для задания этих свойств используется метод [IMetaDataEmit:: сетмодулепропс](imetadataemit-setmoduleprops-method.md) .</span><span class="sxs-lookup"><span data-stu-id="af651-112">The [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af651-113">Требования</span><span class="sxs-lookup"><span data-stu-id="af651-113">Requirements</span></span>  

 <span data-ttu-id="af651-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af651-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af651-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="af651-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="af651-116">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="af651-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="af651-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af651-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af651-118">См. также</span><span class="sxs-lookup"><span data-stu-id="af651-118">See also</span></span>

- [<span data-ttu-id="af651-119">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="af651-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="af651-120">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="af651-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
