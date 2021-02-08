---
description: 'Дополнительные сведения о методе: IMetaDataConverter:: Жеттипелибфромметадата'
title: Метод IMetaDataConverter::GetTypeLibFromMetaData
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
ms.openlocfilehash: 5eecc87f938740366b7938d6ec3d1460ebcfb7eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789272"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="2753d-103">Метод IMetaDataConverter::GetTypeLibFromMetaData</span><span class="sxs-lookup"><span data-stu-id="2753d-103">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>

<span data-ttu-id="2753d-104">Возвращает указатель на `ITypeLib` экземпляр, представляющий библиотеку типов с указанными именами библиотеки и модуля.</span><span class="sxs-lookup"><span data-stu-id="2753d-104">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2753d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2753d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2753d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2753d-106">Parameters</span></span>  

 `strModule`  
 <span data-ttu-id="2753d-107">окне Имя модуля библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="2753d-107">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="2753d-108">окне Имя библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="2753d-108">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="2753d-109">заполняет Указатель на расположение, которое получает адрес `ITypeLib` экземпляра, представляющий библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="2753d-109">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2753d-110">Требования</span><span class="sxs-lookup"><span data-stu-id="2753d-110">Requirements</span></span>  

 <span data-ttu-id="2753d-111">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2753d-111">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2753d-112">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="2753d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2753d-113">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2753d-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2753d-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2753d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2753d-115">См. также</span><span class="sxs-lookup"><span data-stu-id="2753d-115">See also</span></span>

- [<span data-ttu-id="2753d-116">Интерфейс IMetaDataConverter</span><span class="sxs-lookup"><span data-stu-id="2753d-116">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)
