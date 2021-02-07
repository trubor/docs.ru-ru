---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetClassLayout'
title: Метод IMetaDataImport::GetClassLayout
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
ms.openlocfilehash: 74a3170e40a7f857b9150f2d0048af3eac0f2cbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745428"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="4d220-103">Метод IMetaDataImport::GetClassLayout</span><span class="sxs-lookup"><span data-stu-id="4d220-103">IMetaDataImport::GetClassLayout Method</span></span>

<span data-ttu-id="4d220-104">Возвращает сведения о структуре для класса, на который ссылается указанный токен TypeDef.</span><span class="sxs-lookup"><span data-stu-id="4d220-104">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d220-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4d220-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d220-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4d220-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="4d220-107">окне Токен TypeDef для класса с макетом, который должен быть возвращен.</span><span class="sxs-lookup"><span data-stu-id="4d220-107">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="4d220-108">заполняет Одно из значений 1, 2, 4, 8 или 16, представляющее размер пакета класса.</span><span class="sxs-lookup"><span data-stu-id="4d220-108">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="4d220-109">заполняет Массив значений [COR_FIELD_OFFSET](cor-field-offset-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="4d220-109">[out] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4d220-110">[in] Максимальный размер массива `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="4d220-110">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="4d220-111">заполняет Число элементов, возвращаемых в `rFieldOffset` .</span><span class="sxs-lookup"><span data-stu-id="4d220-111">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="4d220-112">заполняет Размер в байтах класса, представленного параметром `td` .</span><span class="sxs-lookup"><span data-stu-id="4d220-112">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d220-113">Требования</span><span class="sxs-lookup"><span data-stu-id="4d220-113">Requirements</span></span>  

 <span data-ttu-id="4d220-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d220-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d220-115">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="4d220-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d220-116">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4d220-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d220-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d220-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d220-118">См. также</span><span class="sxs-lookup"><span data-stu-id="4d220-118">See also</span></span>

- [<span data-ttu-id="4d220-119">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="4d220-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4d220-120">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="4d220-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
