---
description: 'Дополнительные сведения о: интерфейс IMetaDataDispenser'
title: Интерфейс IMetaDataDispenser
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser
helpviewer_keywords:
- IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 989840b3-9822-4ce5-a6c5-b375d3340a7a
topic_type:
- apiref
ms.openlocfilehash: 5ba37fc05a4e1897b100967d32b268f91a0e4402
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721012"
---
# <a name="imetadatadispenser-interface"></a><span data-ttu-id="2db2a-103">Интерфейс IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="2db2a-103">IMetaDataDispenser Interface</span></span>

<span data-ttu-id="2db2a-104">Предоставляет методы для создания новой области метаданных или открытия существующей.</span><span class="sxs-lookup"><span data-stu-id="2db2a-104">Provides methods to create a new metadata scope, or open an existing one.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2db2a-105">Методы</span><span class="sxs-lookup"><span data-stu-id="2db2a-105">Methods</span></span>  
  
|<span data-ttu-id="2db2a-106">Метод</span><span class="sxs-lookup"><span data-stu-id="2db2a-106">Method</span></span>|<span data-ttu-id="2db2a-107">Описание</span><span class="sxs-lookup"><span data-stu-id="2db2a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2db2a-108">Метод DefineScope</span><span class="sxs-lookup"><span data-stu-id="2db2a-108">DefineScope Method</span></span>](imetadatadispenser-definescope-method.md)|<span data-ttu-id="2db2a-109">Создает новую область в памяти, в которой можно создавать новые метаданные.</span><span class="sxs-lookup"><span data-stu-id="2db2a-109">Creates a new area in memory where you can create new metadata.</span></span>|  
|[<span data-ttu-id="2db2a-110">Метод OpenScope</span><span class="sxs-lookup"><span data-stu-id="2db2a-110">OpenScope Method</span></span>](imetadatadispenser-openscope-method.md)|<span data-ttu-id="2db2a-111">Открывает существующий файл на диске и сопоставляет его метаданные с памятью.</span><span class="sxs-lookup"><span data-stu-id="2db2a-111">Opens an existing, on-disk file and maps its metadata into memory.</span></span>|  
|[<span data-ttu-id="2db2a-112">Метод OpenScopeOnMemory</span><span class="sxs-lookup"><span data-stu-id="2db2a-112">OpenScopeOnMemory Method</span></span>](imetadatadispenser-openscopeonmemory-method.md)|<span data-ttu-id="2db2a-113">Открывает область памяти, которая содержит существующие метаданные.</span><span class="sxs-lookup"><span data-stu-id="2db2a-113">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="2db2a-114">Это значит, что этот метод открывает указанную область памяти, в которой существующие данные обрабатываются как метаданные.</span><span class="sxs-lookup"><span data-stu-id="2db2a-114">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2db2a-115">Требования</span><span class="sxs-lookup"><span data-stu-id="2db2a-115">Requirements</span></span>  

 <span data-ttu-id="2db2a-116">**Платформа:** См. раздел [требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2db2a-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2db2a-117">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="2db2a-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2db2a-118">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2db2a-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2db2a-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2db2a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2db2a-120">См. также</span><span class="sxs-lookup"><span data-stu-id="2db2a-120">See also</span></span>

- [<span data-ttu-id="2db2a-121">Интерфейс IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="2db2a-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="2db2a-122">Интерфейсы метаданных</span><span class="sxs-lookup"><span data-stu-id="2db2a-122">Metadata Interfaces</span></span>](metadata-interfaces.md)
