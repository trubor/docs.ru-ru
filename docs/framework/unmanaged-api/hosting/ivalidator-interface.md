---
description: 'Дополнительные сведения о: интерфейс IValidator'
title: Интерфейс IValidator
ms.date: 03/30/2017
api_name:
- IValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IValidator
helpviewer_keywords:
- IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type:
- apiref
ms.openlocfilehash: bc18b68d0e9a0e978789ab92afaed28751925870
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680100"
---
# <a name="ivalidator-interface"></a><span data-ttu-id="515cf-103">Интерфейс IValidator</span><span class="sxs-lookup"><span data-stu-id="515cf-103">IValidator Interface</span></span>

<span data-ttu-id="515cf-104">Предоставляет методы для проверки переносимых исполняемых (PE) образов и создания отчетов об ошибках проверки.</span><span class="sxs-lookup"><span data-stu-id="515cf-104">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="515cf-105">Методы</span><span class="sxs-lookup"><span data-stu-id="515cf-105">Methods</span></span>  
  
|<span data-ttu-id="515cf-106">Метод</span><span class="sxs-lookup"><span data-stu-id="515cf-106">Method</span></span>|<span data-ttu-id="515cf-107">Description</span><span class="sxs-lookup"><span data-stu-id="515cf-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="515cf-108">Проверить</span><span class="sxs-lookup"><span data-stu-id="515cf-108">Validate</span></span>|<span data-ttu-id="515cf-109">Проверяет указанный PE-файл или промежуточный язык MSIL.</span><span class="sxs-lookup"><span data-stu-id="515cf-109">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="515cf-110">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="515cf-110">FormatEventInfo</span></span>|<span data-ttu-id="515cf-111">Возвращает сообщение об ошибке, соответствующее указанной ошибке проверки.</span><span class="sxs-lookup"><span data-stu-id="515cf-111">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="515cf-112">Требования</span><span class="sxs-lookup"><span data-stu-id="515cf-112">Requirements</span></span>  

 <span data-ttu-id="515cf-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="515cf-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="515cf-114">**Заголовок:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="515cf-114">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="515cf-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="515cf-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="515cf-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="515cf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="515cf-117">См. также</span><span class="sxs-lookup"><span data-stu-id="515cf-117">See also</span></span>

- [<span data-ttu-id="515cf-118">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="515cf-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="515cf-119">Компонентный класс CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="515cf-119">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
