---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetModuleRefProps'
title: Метод IMetaDataImport::GetModuleRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
ms.openlocfilehash: 3e6b212ddad5eefb06942c3fd4b89411b277f761
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753358"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="aa17c-103">Метод IMetaDataImport::GetModuleRefProps</span><span class="sxs-lookup"><span data-stu-id="aa17c-103">IMetaDataImport::GetModuleRefProps Method</span></span>

<span data-ttu-id="aa17c-104">Возвращает имя модуля, на который ссылается указанный токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="aa17c-104">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa17c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aa17c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,
   [in]  ULONG               cchName,
   [out] ULONG               *pchName
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa17c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="aa17c-106">Parameters</span></span>  

 `mur`  
 <span data-ttu-id="aa17c-107">окне Токен метаданных ModuleRef, который ссылается на модуль для получения сведений о метаданных.</span><span class="sxs-lookup"><span data-stu-id="aa17c-107">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="aa17c-108">заполняет Буфер для хранения имени модуля.</span><span class="sxs-lookup"><span data-stu-id="aa17c-108">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="aa17c-109">окне Запрошенный размер `szName` в расширенных символах.</span><span class="sxs-lookup"><span data-stu-id="aa17c-109">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="aa17c-110">заполняет Возвращаемый размер `szName` в расширенных символах.</span><span class="sxs-lookup"><span data-stu-id="aa17c-110">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa17c-111">Требования</span><span class="sxs-lookup"><span data-stu-id="aa17c-111">Requirements</span></span>  

 <span data-ttu-id="aa17c-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa17c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa17c-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="aa17c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aa17c-114">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aa17c-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aa17c-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa17c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa17c-116">См. также</span><span class="sxs-lookup"><span data-stu-id="aa17c-116">See also</span></span>

- [<span data-ttu-id="aa17c-117">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="aa17c-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="aa17c-118">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="aa17c-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
