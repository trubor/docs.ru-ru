---
description: 'Дополнительные сведения о: интерфейс Иклрвалидатор'
title: Интерфейс ICLRValidator
ms.date: 03/30/2017
api_name:
- ICLRValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator
helpviewer_keywords:
- ICLRValidator interface [.NET Framework hosting]
ms.assetid: 2edd0a10-77fb-4173-91eb-f2970cc364d0
topic_type:
- apiref
ms.openlocfilehash: 72ff94915d35967b6a8a87b022789ca697f61711
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636758"
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="0a62b-103">Интерфейс ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="0a62b-103">ICLRValidator Interface</span></span>

<span data-ttu-id="0a62b-104">Предоставляет методы для проверки переносимых исполняемых (PE) образов и создания отчетов об ошибках проверки.</span><span class="sxs-lookup"><span data-stu-id="0a62b-104">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a62b-105">Методы</span><span class="sxs-lookup"><span data-stu-id="0a62b-105">Methods</span></span>  
  
|<span data-ttu-id="0a62b-106">Метод</span><span class="sxs-lookup"><span data-stu-id="0a62b-106">Method</span></span>|<span data-ttu-id="0a62b-107">Описание</span><span class="sxs-lookup"><span data-stu-id="0a62b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a62b-108">Метод FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="0a62b-108">FormatEventInfo Method</span></span>](iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="0a62b-109">Возвращает подробное сообщение об указанной ошибке проверки.</span><span class="sxs-lookup"><span data-stu-id="0a62b-109">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="0a62b-110">Метод Validate</span><span class="sxs-lookup"><span data-stu-id="0a62b-110">Validate Method</span></span>](iclrvalidator-validate-method.md)|<span data-ttu-id="0a62b-111">Проверяет переносимый исполняемый файл или язык MSIL в указанном файле.</span><span class="sxs-lookup"><span data-stu-id="0a62b-111">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a62b-112">Требования</span><span class="sxs-lookup"><span data-stu-id="0a62b-112">Requirements</span></span>  

 <span data-ttu-id="0a62b-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a62b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a62b-114">**Заголовок:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="0a62b-114">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="0a62b-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a62b-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a62b-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a62b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a62b-117">См. также</span><span class="sxs-lookup"><span data-stu-id="0a62b-117">See also</span></span>

- [<span data-ttu-id="0a62b-118">Интерфейс ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="0a62b-118">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="0a62b-119">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="0a62b-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="0a62b-120">Кокласс CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0a62b-120">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
