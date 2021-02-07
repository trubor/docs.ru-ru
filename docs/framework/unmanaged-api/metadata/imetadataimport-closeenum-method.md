---
description: 'Дополнительные сведения: метод IMetaDataImport:: CloseEnum'
title: Метод IMetaDataImport::CloseEnum
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type:
- apiref
ms.openlocfilehash: b18b484cab0d9f4c0ecea21da78535c9a872bb1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677747"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="63739-103">Метод IMetaDataImport::CloseEnum</span><span class="sxs-lookup"><span data-stu-id="63739-103">IMetaDataImport::CloseEnum Method</span></span>

<span data-ttu-id="63739-104">Закрывает перечислитель, идентифицируемый указанным маркером.</span><span class="sxs-lookup"><span data-stu-id="63739-104">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63739-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="63739-105">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63739-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="63739-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="63739-107">окне Маркер для закрытия перечислителя.</span><span class="sxs-lookup"><span data-stu-id="63739-107">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63739-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="63739-108">Remarks</span></span>  

 <span data-ttu-id="63739-109">Маркер, заданный параметром, `hEnum` получается из предыдущего `Enum` вызова *имени* (например, [IMetaDataImport:: EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="63739-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63739-110">Требования</span><span class="sxs-lookup"><span data-stu-id="63739-110">Requirements</span></span>  

 <span data-ttu-id="63739-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63739-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63739-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="63739-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63739-113">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63739-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63739-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63739-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63739-115">См. также</span><span class="sxs-lookup"><span data-stu-id="63739-115">See also</span></span>

- [<span data-ttu-id="63739-116">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="63739-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="63739-117">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="63739-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
