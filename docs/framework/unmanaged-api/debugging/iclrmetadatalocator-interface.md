---
description: 'Дополнительные сведения о: интерфейс Иклрметадаталокатор'
title: Интерфейс ICLRMetadataLocator
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator
helpviewer_keywords:
- ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type:
- apiref
ms.openlocfilehash: 6e7fd45197294563e12da020379d1bd54b088698
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772624"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="cb11e-103">Интерфейс ICLRMetadataLocator</span><span class="sxs-lookup"><span data-stu-id="cb11e-103">ICLRMetadataLocator Interface</span></span>

<span data-ttu-id="cb11e-104">Используется уровнем служб доступа к данным для определения местоположения метаданных сборок в целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="cb11e-104">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cb11e-105">Методы</span><span class="sxs-lookup"><span data-stu-id="cb11e-105">Methods</span></span>  
  
|<span data-ttu-id="cb11e-106">Метод</span><span class="sxs-lookup"><span data-stu-id="cb11e-106">Method</span></span>|<span data-ttu-id="cb11e-107">Описание</span><span class="sxs-lookup"><span data-stu-id="cb11e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb11e-108">Метод Metadata</span><span class="sxs-lookup"><span data-stu-id="cb11e-108">GetMetadata Method</span></span>](iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="cb11e-109">Извлекает метаданные изображения из целевого процесса.</span><span class="sxs-lookup"><span data-stu-id="cb11e-109">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb11e-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="cb11e-110">Remarks</span></span>  

 <span data-ttu-id="cb11e-111">Клиент API (то есть отладчик) должен реализовывать этот интерфейс для определенного целевого процесса по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="cb11e-111">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="cb11e-112">Например, реализация для активного процесса будет отличаться от реализации дампа памяти.</span><span class="sxs-lookup"><span data-stu-id="cb11e-112">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb11e-113">Требования</span><span class="sxs-lookup"><span data-stu-id="cb11e-113">Requirements</span></span>  

 <span data-ttu-id="cb11e-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb11e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb11e-115">**Заголовок:** Клрдата. idl, Клрдата. h</span><span class="sxs-lookup"><span data-stu-id="cb11e-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cb11e-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb11e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb11e-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb11e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb11e-118">См. также</span><span class="sxs-lookup"><span data-stu-id="cb11e-118">See also</span></span>

- [<span data-ttu-id="cb11e-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="cb11e-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
