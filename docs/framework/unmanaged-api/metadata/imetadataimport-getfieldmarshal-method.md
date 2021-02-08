---
description: 'Дополнительные сведения: метод IMetaDataImport:: GetFieldMarshal'
title: Метод IMetaDataImport::GetFieldMarshal
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldMarshal
helpviewer_keywords:
- GetFieldMarshal method [.NET Framework metadata]
- IMetaDataImport::GetFieldMarshal method [.NET Framework metadata]
ms.assetid: 4e2d88c6-8a3a-4fbe-900b-b4f4c06bf6bf
topic_type:
- apiref
ms.openlocfilehash: d6ca1f80a8b9bae4d9c02466042300bc3662f7c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803533"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="ced6b-103">Метод IMetaDataImport::GetFieldMarshal</span><span class="sxs-lookup"><span data-stu-id="ced6b-103">IMetaDataImport::GetFieldMarshal Method</span></span>

<span data-ttu-id="ced6b-104">Возвращает указатель на собственный неуправляемый тип поля, представленного заданным токеном метаданных поля.</span><span class="sxs-lookup"><span data-stu-id="ced6b-104">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ced6b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ced6b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ced6b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ced6b-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="ced6b-107">окне Токен метаданных, представляющий поле, для которого необходимо получить сведения о маршалинге взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="ced6b-107">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="ced6b-108">заполняет Указатель на сигнатуру метаданных собственного типа поля.</span><span class="sxs-lookup"><span data-stu-id="ced6b-108">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="ced6b-109">заполняет Размер в байтах для `ppvNativeType` .</span><span class="sxs-lookup"><span data-stu-id="ced6b-109">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ced6b-110">Требования</span><span class="sxs-lookup"><span data-stu-id="ced6b-110">Requirements</span></span>  

 <span data-ttu-id="ced6b-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ced6b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ced6b-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="ced6b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ced6b-113">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ced6b-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ced6b-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ced6b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ced6b-115">См. также</span><span class="sxs-lookup"><span data-stu-id="ced6b-115">See also</span></span>

- [<span data-ttu-id="ced6b-116">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="ced6b-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ced6b-117">Интерфейс IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="ced6b-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
