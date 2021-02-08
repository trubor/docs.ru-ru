---
description: 'Дополнительные сведения о методе IMetaDataImport:: Global'
title: Метод IMetaDataImport::IsGlobal
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsGlobal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type:
- apiref
ms.openlocfilehash: 5230b2967990e3c52b429d62dd03566c3043e45f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789077"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="c819b-103">Метод IMetaDataImport::IsGlobal</span><span class="sxs-lookup"><span data-stu-id="c819b-103">IMetaDataImport::IsGlobal Method</span></span>

<span data-ttu-id="c819b-104">Возвращает значение, указывающее на наличие глобальной области у поля, метода или типа, представленного заданным токеном метаданных.</span><span class="sxs-lookup"><span data-stu-id="c819b-104">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c819b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c819b-105">Syntax</span></span>  
  
```cpp  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c819b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c819b-106">Parameters</span></span>  

 `pd`  
 <span data-ttu-id="c819b-107">окне Токен метаданных, представляющий тип, поле или метод.</span><span class="sxs-lookup"><span data-stu-id="c819b-107">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="c819b-108">[out] 1, если объект имеет глобальную область видимости; в противном случае — 0 (ноль).</span><span class="sxs-lookup"><span data-stu-id="c819b-108">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c819b-109">Требования</span><span class="sxs-lookup"><span data-stu-id="c819b-109">Requirements</span></span>  

 <span data-ttu-id="c819b-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c819b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c819b-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="c819b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c819b-112">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c819b-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c819b-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c819b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c819b-114">См. также</span><span class="sxs-lookup"><span data-stu-id="c819b-114">See also</span></span>

- [<span data-ttu-id="c819b-115">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c819b-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c819b-116">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c819b-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
