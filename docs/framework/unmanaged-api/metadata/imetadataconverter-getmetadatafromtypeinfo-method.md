---
description: 'Дополнительные сведения о методе: IMetaDataConverter:: Жетметадатафромтипеинфо'
title: Метод IMetaDataConverter::GetMetaDataFromTypeInfo
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeInfo
helpviewer_keywords:
- GetMetaDataFromTypeInfo method [.NET Framework metadata]
- IMetaDataConverter::GetMetaDataFromTypeInfo method [.NET Framework metadata]
ms.assetid: d44484bb-23a3-49c3-9e46-69d0d9ab4f0f
topic_type:
- apiref
ms.openlocfilehash: 224be07463b19ed9e22bef1a9d454d91a8086304
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753631"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a><span data-ttu-id="75782-103">Метод IMetaDataConverter::GetMetaDataFromTypeInfo</span><span class="sxs-lookup"><span data-stu-id="75782-103">IMetaDataConverter::GetMetaDataFromTypeInfo Method</span></span>

<span data-ttu-id="75782-104">Возвращает указатель на экземпляр [IMetaDataImport](imetadataimport-interface.md) , представляющий сигнатуру метаданных библиотеки типов, на которую ссылается указанный `ITypeInfo` экземпляр.</span><span class="sxs-lookup"><span data-stu-id="75782-104">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature of the type library referenced by the specified `ITypeInfo` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75782-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="75782-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75782-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="75782-106">Parameters</span></span>  

 `pITI`  
 <span data-ttu-id="75782-107">окне Указатель на `ITypeInfo` объект, который ссылается на библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="75782-107">[in] A pointer to an `ITypeInfo` object that refers to the type library.</span></span>  
  
 `ppMDI`  
 <span data-ttu-id="75782-108">заполняет Указатель на расположение, которое получает адрес `IMetaDataImport` экземпляра, представляющий подпись метаданных.</span><span class="sxs-lookup"><span data-stu-id="75782-108">[out] A pointer to a location that receives the address of the `IMetaDataImport` instance that represents the metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75782-109">Требования</span><span class="sxs-lookup"><span data-stu-id="75782-109">Requirements</span></span>  

 <span data-ttu-id="75782-110">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75782-110">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75782-111">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="75782-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75782-112">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75782-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75782-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75782-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75782-114">См. также</span><span class="sxs-lookup"><span data-stu-id="75782-114">See also</span></span>

- [<span data-ttu-id="75782-115">Интерфейс IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="75782-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="75782-116">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="75782-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
