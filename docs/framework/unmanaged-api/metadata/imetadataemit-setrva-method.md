---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: SetRVA'
title: Метод IMetaDataEmit::SetRVA
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetRVA
helpviewer_keywords:
- IMetaDataEmit::SetRVA method [.NET Framework metadata]
- SetRVA method [.NET Framework metadata]
ms.assetid: 4d69fb6d-ee35-4318-8224-5eea2bd16818
topic_type:
- apiref
ms.openlocfilehash: 52294250df2b7a677bb4ecb09ea0a97baca595a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771786"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="00d2e-103">Метод IMetaDataEmit::SetRVA</span><span class="sxs-lookup"><span data-stu-id="00d2e-103">IMetaDataEmit::SetRVA Method</span></span>

<span data-ttu-id="00d2e-104">Задает относительный виртуальный адрес указанного метода.</span><span class="sxs-lookup"><span data-stu-id="00d2e-104">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00d2e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="00d2e-105">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,
    [in]  ULONG        ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00d2e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="00d2e-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="00d2e-107">окне Токен для реализации целевого метода или метода.</span><span class="sxs-lookup"><span data-stu-id="00d2e-107">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="00d2e-108">окне Адрес кода или области данных.</span><span class="sxs-lookup"><span data-stu-id="00d2e-108">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00d2e-109">Требования</span><span class="sxs-lookup"><span data-stu-id="00d2e-109">Requirements</span></span>  

 <span data-ttu-id="00d2e-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00d2e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00d2e-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="00d2e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00d2e-112">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00d2e-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00d2e-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00d2e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d2e-114">См. также</span><span class="sxs-lookup"><span data-stu-id="00d2e-114">See also</span></span>

- [<span data-ttu-id="00d2e-115">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="00d2e-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="00d2e-116">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="00d2e-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
