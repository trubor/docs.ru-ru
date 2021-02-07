---
description: 'Дополнительные сведения о: интерфейс IMetaDataFilter'
title: Интерфейс IMetaDataFilter
ms.date: 03/30/2017
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
ms.openlocfilehash: c994574207ccb26a5cb317e1673145a41f0d837d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677929"
---
# <a name="imetadatafilter-interface"></a><span data-ttu-id="2ac76-103">Интерфейс IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="2ac76-103">IMetaDataFilter Interface</span></span>

<span data-ttu-id="2ac76-104">Предоставляет методы для пометки и фильтрации лексем метаданных во избежание повторения действий, которые уже были выполнены.</span><span class="sxs-lookup"><span data-stu-id="2ac76-104">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2ac76-105">Методы</span><span class="sxs-lookup"><span data-stu-id="2ac76-105">Methods</span></span>  
  
|<span data-ttu-id="2ac76-106">Метод</span><span class="sxs-lookup"><span data-stu-id="2ac76-106">Method</span></span>|<span data-ttu-id="2ac76-107">Описание</span><span class="sxs-lookup"><span data-stu-id="2ac76-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2ac76-108">Метод IsTokenMarked</span><span class="sxs-lookup"><span data-stu-id="2ac76-108">IsTokenMarked Method</span></span>](imetadatafilter-istokenmarked-method.md)|<span data-ttu-id="2ac76-109">Возвращает значение, указывающее, был ли обработан заданный маркер метаданных.</span><span class="sxs-lookup"><span data-stu-id="2ac76-109">Gets a value indicating whether the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="2ac76-110">Метод MarkToken</span><span class="sxs-lookup"><span data-stu-id="2ac76-110">MarkToken Method</span></span>](imetadatafilter-marktoken-method.md)|<span data-ttu-id="2ac76-111">Задает значение, указывающее, что указанный токен метаданных был обработан.</span><span class="sxs-lookup"><span data-stu-id="2ac76-111">Sets a value indicating that the specified metadata token has been processed.</span></span>|  
|[<span data-ttu-id="2ac76-112">Метод UnmarkAll</span><span class="sxs-lookup"><span data-stu-id="2ac76-112">UnmarkAll Method</span></span>](imetadatafilter-unmarkall-method.md)|<span data-ttu-id="2ac76-113">Удаляет метки обработки из всех токенов в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="2ac76-113">Removes the processing marks from all the tokens in the current metadata scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2ac76-114">Требования</span><span class="sxs-lookup"><span data-stu-id="2ac76-114">Requirements</span></span>  

 <span data-ttu-id="2ac76-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ac76-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ac76-116">**Заголовок:** COR. h</span><span class="sxs-lookup"><span data-stu-id="2ac76-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2ac76-117">**Библиотека:** Используется в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ac76-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ac76-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ac76-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac76-119">См. также</span><span class="sxs-lookup"><span data-stu-id="2ac76-119">See also</span></span>

- [<span data-ttu-id="2ac76-120">Интерфейсы метаданных</span><span class="sxs-lookup"><span data-stu-id="2ac76-120">Metadata Interfaces</span></span>](metadata-interfaces.md)
