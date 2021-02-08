---
description: 'Дополнительные сведения о методе: IMetaDataConverter:: Жетметадатафромтипелиб'
title: Метод IMetaDataConverter::GetMetaDataFromTypeLib
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeLib
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib
helpviewer_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib method [.NET Framework metadata]
- GetMetaDataFromTypeLib method [.NET Framework metadata]
ms.assetid: 97dc3a56-adfa-431f-889e-06a35ac84d51
topic_type:
- apiref
ms.openlocfilehash: d1ed5feb9f42ea0f8dc802c4dad527be5d2ed25f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789285"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a><span data-ttu-id="b0c06-103">Метод IMetaDataConverter::GetMetaDataFromTypeLib</span><span class="sxs-lookup"><span data-stu-id="b0c06-103">IMetaDataConverter::GetMetaDataFromTypeLib Method</span></span>

<span data-ttu-id="b0c06-104">Возвращает указатель интерфейса на экземпляр [IMetaDataImport](imetadataimport-interface.md) , представляющий сигнатуру метаданных библиотеки типов, представленной указанным `ITypeLib` экземпляром.</span><span class="sxs-lookup"><span data-stu-id="b0c06-104">Gets an interface pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library represented by the specified `ITypeLib` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0c06-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b0c06-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0c06-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0c06-106">Parameters</span></span>  

 `pITL`  
 <span data-ttu-id="b0c06-107">окне Указатель на `ITypeLib` объект, представляющий библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="b0c06-107">[in] Pointer to an `ITypeLib` object that represents the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="b0c06-108">заполняет Указатель на расположение, которое получает адрес `IMetaDataImport` экземпляра, представляющий подпись метаданных.</span><span class="sxs-lookup"><span data-stu-id="b0c06-108">[out] Pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0c06-109">Требования</span><span class="sxs-lookup"><span data-stu-id="b0c06-109">Requirements</span></span>  

 <span data-ttu-id="b0c06-110">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0c06-110">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0c06-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="b0c06-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b0c06-112">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0c06-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b0c06-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0c06-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0c06-114">См. также</span><span class="sxs-lookup"><span data-stu-id="b0c06-114">See also</span></span>

- [<span data-ttu-id="b0c06-115">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b0c06-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b0c06-116">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b0c06-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
