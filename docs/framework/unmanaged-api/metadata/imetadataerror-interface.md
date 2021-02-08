---
description: 'Дополнительные сведения о: Интерфейс IMetaDataError'
title: Интерфейс IMetaDataError
ms.date: 03/30/2017
api_name:
- IMetaDataError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError
helpviewer_keywords:
- IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type:
- apiref
ms.openlocfilehash: f32c8abc3cccce770b86ce47016d9b7e18acad23
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771695"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="0f38e-103">Интерфейс IMetaDataError</span><span class="sxs-lookup"><span data-stu-id="0f38e-103">IMetaDataError Interface</span></span>

<span data-ttu-id="0f38e-104">Предоставляет механизм обратного вызова для сообщения об ошибках во время слияния метаданных.</span><span class="sxs-lookup"><span data-stu-id="0f38e-104">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f38e-105">`IMetaDataError`Интерфейс должен быть реализован клиентом.</span><span class="sxs-lookup"><span data-stu-id="0f38e-105">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f38e-106">Методы</span><span class="sxs-lookup"><span data-stu-id="0f38e-106">Methods</span></span>  
  
|<span data-ttu-id="0f38e-107">Метод</span><span class="sxs-lookup"><span data-stu-id="0f38e-107">Method</span></span>|<span data-ttu-id="0f38e-108">Описание</span><span class="sxs-lookup"><span data-stu-id="0f38e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0f38e-109">Метод OnError</span><span class="sxs-lookup"><span data-stu-id="0f38e-109">OnError Method</span></span>](imetadataerror-onerror-method.md)|<span data-ttu-id="0f38e-110">Предоставляет уведомление об ошибках, возникающих во время слияния метаданных.</span><span class="sxs-lookup"><span data-stu-id="0f38e-110">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f38e-111">Требования</span><span class="sxs-lookup"><span data-stu-id="0f38e-111">Requirements</span></span>  

 <span data-ttu-id="0f38e-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f38e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f38e-113">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="0f38e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0f38e-114">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0f38e-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0f38e-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f38e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f38e-116">См. также</span><span class="sxs-lookup"><span data-stu-id="0f38e-116">See also</span></span>

- [<span data-ttu-id="0f38e-117">Интерфейсы метаданных</span><span class="sxs-lookup"><span data-stu-id="0f38e-117">Metadata Interfaces</span></span>](metadata-interfaces.md)
