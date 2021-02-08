---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Сетпарент'
title: Метод IMetaDataEmit::SetParent
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
ms.openlocfilehash: 9025d4a37de85a0e657059f63ef781dc4377c036
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772007"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="9c43e-103">Метод IMetaDataEmit::SetParent</span><span class="sxs-lookup"><span data-stu-id="9c43e-103">IMetaDataEmit::SetParent Method</span></span>

<span data-ttu-id="9c43e-104">Устанавливает, что указанный элемент, как определено в предыдущем вызове [IMetaDataEmit::D ефинемемберреф](imetadataemit-definememberref-method.md), является членом указанного типа, как определено в предыдущем вызове [IMetaDataEmit::D ефинетипедеф](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="9c43e-104">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c43e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9c43e-105">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c43e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9c43e-106">Parameters</span></span>  

 `mr`  
 <span data-ttu-id="9c43e-107">окне `mdMemberRef` Токен для получения нового родителя.</span><span class="sxs-lookup"><span data-stu-id="9c43e-107">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="9c43e-108">окне `mdToken` Для нового родителя.</span><span class="sxs-lookup"><span data-stu-id="9c43e-108">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c43e-109">Требования</span><span class="sxs-lookup"><span data-stu-id="9c43e-109">Requirements</span></span>  

 <span data-ttu-id="9c43e-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c43e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c43e-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="9c43e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c43e-112">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9c43e-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c43e-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c43e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c43e-114">См. также</span><span class="sxs-lookup"><span data-stu-id="9c43e-114">See also</span></span>

- [<span data-ttu-id="9c43e-115">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="9c43e-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9c43e-116">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="9c43e-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
