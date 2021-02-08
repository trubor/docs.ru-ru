---
description: 'Дополнительные сведения: IMetaDataEmit::D метод Ефинесекуритяттрибутесет'
title: Метод IMetaDataEmit::DefineSecurityAttributeSet
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineSecurityAttributeSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type:
- apiref
ms.openlocfilehash: 3512857ca23d65389b0e150bd24234d272ddd9b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784058"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="68930-103">Метод IMetaDataEmit::DefineSecurityAttributeSet</span><span class="sxs-lookup"><span data-stu-id="68930-103">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>

<span data-ttu-id="68930-104">Создает набор разрешений безопасности для присоединения к объекту, на который ссылается указанный токен.</span><span class="sxs-lookup"><span data-stu-id="68930-104">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68930-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="68930-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (
    [in]  mdToken       tkObj,
    [in]  COR_SECATTR   rSecAttrs[],
    [in]  ULONG         cSecAttrs,
    [out] ULONG         *pulErrorAttr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68930-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="68930-106">Parameters</span></span>  

 `tkObj`  
 <span data-ttu-id="68930-107">окне Токен, к которому присоединены сведения о безопасности.</span><span class="sxs-lookup"><span data-stu-id="68930-107">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="68930-108">окне Массив `COR_SECATTR` структур.</span><span class="sxs-lookup"><span data-stu-id="68930-108">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="68930-109">окне Количество элементов в `rSecAttrs` .</span><span class="sxs-lookup"><span data-stu-id="68930-109">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="68930-110">заполняет В случае сбоя метода указывает индекс в `rSecAttrs` элементе, вызвавшем проблему.</span><span class="sxs-lookup"><span data-stu-id="68930-110">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68930-111">Требования</span><span class="sxs-lookup"><span data-stu-id="68930-111">Requirements</span></span>  

 <span data-ttu-id="68930-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68930-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68930-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="68930-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68930-114">**Библиотека:** Используется в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68930-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68930-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68930-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68930-116">См. также</span><span class="sxs-lookup"><span data-stu-id="68930-116">See also</span></span>

- [<span data-ttu-id="68930-117">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="68930-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="68930-118">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="68930-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
