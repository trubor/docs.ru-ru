---
description: 'Дополнительные сведения о: интерфейс IMetaDataConverter'
title: Интерфейс IMetaDataConverter
ms.date: 03/30/2017
api_name:
- IMetaDataConverter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter
helpviewer_keywords:
- IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type:
- apiref
ms.openlocfilehash: 6ed84083bad924e760c576afe485bd7ccad012cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789259"
---
# <a name="imetadataconverter-interface"></a><span data-ttu-id="be65d-103">Интерфейс IMetaDataConverter</span><span class="sxs-lookup"><span data-stu-id="be65d-103">IMetaDataConverter Interface</span></span>

<span data-ttu-id="be65d-104">Предоставляет методы для сопоставления библиотек типов с их сигнатурами метаданных и для преобразования из одних в другие.</span><span class="sxs-lookup"><span data-stu-id="be65d-104">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be65d-105">Методы</span><span class="sxs-lookup"><span data-stu-id="be65d-105">Methods</span></span>  
  
|<span data-ttu-id="be65d-106">Метод</span><span class="sxs-lookup"><span data-stu-id="be65d-106">Method</span></span>|<span data-ttu-id="be65d-107">Описание</span><span class="sxs-lookup"><span data-stu-id="be65d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be65d-108">Метод GetMetaDataFromTypeInfo</span><span class="sxs-lookup"><span data-stu-id="be65d-108">GetMetaDataFromTypeInfo Method</span></span>](imetadataconverter-getmetadatafromtypeinfo-method.md)|<span data-ttu-id="be65d-109">Возвращает указатель на экземпляр [IMetaDataImport](imetadataimport-interface.md) , представляющий сигнатуру метаданных для библиотеки типов, на которую ссылается указанный `ITypeInfo` экземпляр.</span><span class="sxs-lookup"><span data-stu-id="be65d-109">Gets a pointer to an [IMetaDataImport](imetadataimport-interface.md) instance that represents the metadata signature for the type library referenced by the specified `ITypeInfo` instance.</span></span>|  
|[<span data-ttu-id="be65d-110">Метод GetMetaDataFromTypeLib</span><span class="sxs-lookup"><span data-stu-id="be65d-110">GetMetaDataFromTypeLib Method</span></span>](imetadataconverter-getmetadatafromtypelib-method.md)|<span data-ttu-id="be65d-111">Возвращает указатель на `IMetaDataImport` экземпляр, представляющий сигнатуру метаданных для библиотеки типов, представленной указанным `ITypeLib` экземпляром.</span><span class="sxs-lookup"><span data-stu-id="be65d-111">Gets a pointer to an `IMetaDataImport` instance that represents the metadata signature for the type library represented by the specified `ITypeLib` instance.</span></span>|  
|[<span data-ttu-id="be65d-112">Метод GetTypeLibFromMetaData</span><span class="sxs-lookup"><span data-stu-id="be65d-112">GetTypeLibFromMetaData Method</span></span>](imetadataconverter-gettypelibfrommetadata-method.md)|<span data-ttu-id="be65d-113">Возвращает указатель на `ITypeLib` экземпляр, представляющий библиотеку типов с указанными именами модуля и библиотеки.</span><span class="sxs-lookup"><span data-stu-id="be65d-113">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified module and library names.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be65d-114">Требования</span><span class="sxs-lookup"><span data-stu-id="be65d-114">Requirements</span></span>  

 <span data-ttu-id="be65d-115">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be65d-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be65d-116">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="be65d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be65d-117">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be65d-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be65d-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be65d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be65d-119">См. также</span><span class="sxs-lookup"><span data-stu-id="be65d-119">See also</span></span>

- [<span data-ttu-id="be65d-120">Интерфейсы метаданных</span><span class="sxs-lookup"><span data-stu-id="be65d-120">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="be65d-121">Интерфейс IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="be65d-121">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
