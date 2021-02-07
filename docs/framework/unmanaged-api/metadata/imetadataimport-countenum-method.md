---
description: 'Дополнительные сведения: метод IMetaDataImport:: Каунтенум'
title: Метод IMetaDataImport::CountEnum
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
ms.openlocfilehash: c579ef7ce440e3552ab28572fc6c96ad12d66400
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677695"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="c6af8-103">Метод IMetaDataImport::CountEnum</span><span class="sxs-lookup"><span data-stu-id="c6af8-103">IMetaDataImport::CountEnum Method</span></span>

<span data-ttu-id="c6af8-104">Возвращает количество элементов в перечислении, полученных указанным перечислителем.</span><span class="sxs-lookup"><span data-stu-id="c6af8-104">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6af8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c6af8-105">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6af8-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c6af8-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="c6af8-107">окне Маркер для перечислителя.</span><span class="sxs-lookup"><span data-stu-id="c6af8-107">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="c6af8-108">заполняет Число перечисленных элементов.</span><span class="sxs-lookup"><span data-stu-id="c6af8-108">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6af8-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="c6af8-109">Remarks</span></span>  

 <span data-ttu-id="c6af8-110">Маркер, заданный параметром, `hEnum` получается из предыдущего `Enum` вызова *имени* (например, [IMetaDataImport:: EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="c6af8-110">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6af8-111">Требования</span><span class="sxs-lookup"><span data-stu-id="c6af8-111">Requirements</span></span>  

 <span data-ttu-id="c6af8-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6af8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6af8-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="c6af8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c6af8-114">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6af8-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6af8-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6af8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6af8-116">См. также</span><span class="sxs-lookup"><span data-stu-id="c6af8-116">See also</span></span>

- [<span data-ttu-id="c6af8-117">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c6af8-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c6af8-118">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c6af8-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
