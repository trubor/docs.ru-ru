---
description: 'Дополнительные сведения: Метод IMetaDataEmit:: Сеткустоматтрибутевалуе'
title: Метод IMetaDataEmit::SetCustomAttributeValue
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetCustomAttributeValue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type:
- apiref
ms.openlocfilehash: 1eede765f27b371deb670242086d59b3d4320530
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706582"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="656db-103">Метод IMetaDataEmit::SetCustomAttributeValue</span><span class="sxs-lookup"><span data-stu-id="656db-103">IMetaDataEmit::SetCustomAttributeValue Method</span></span>

<span data-ttu-id="656db-104">Задает или обновляет значение настраиваемого атрибута, определенного при предыдущем вызове метода [IMetaDataEmit::D ефинекустоматтрибуте](imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="656db-104">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="656db-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="656db-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (
    [in]  mdCustomAttribute       pcv,
    [in]  void const              *pCustomAttribute,
    [in]  ULONG                   cbCustomAttribute
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="656db-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="656db-106">Parameters</span></span>  

 `pcv`  
 <span data-ttu-id="656db-107">окне Токен целевого настраиваемого атрибута.</span><span class="sxs-lookup"><span data-stu-id="656db-107">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="656db-108">окне Указатель на массив, содержащий настраиваемый атрибут.</span><span class="sxs-lookup"><span data-stu-id="656db-108">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="656db-109">окне Размер настраиваемого атрибута в байтах.</span><span class="sxs-lookup"><span data-stu-id="656db-109">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="656db-110">Требования</span><span class="sxs-lookup"><span data-stu-id="656db-110">Requirements</span></span>  

 <span data-ttu-id="656db-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="656db-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="656db-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="656db-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="656db-113">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="656db-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="656db-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="656db-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="656db-115">См. также</span><span class="sxs-lookup"><span data-stu-id="656db-115">See also</span></span>

- [<span data-ttu-id="656db-116">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="656db-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="656db-117">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="656db-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
