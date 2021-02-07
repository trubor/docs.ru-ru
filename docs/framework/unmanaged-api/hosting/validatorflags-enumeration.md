---
description: Дополнительные сведения о перечислении Валидаторфлагс
title: Перечисление ValidatorFlags
ms.date: 03/30/2017
api_name:
- ValidatorFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ValidatorFlags
helpviewer_keywords:
- ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type:
- apiref
ms.openlocfilehash: 473b0eef2851126256e1ea6b6d2b82be32e03e1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679125"
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="2dfbf-103">Перечисление ValidatorFlags</span><span class="sxs-lookup"><span data-stu-id="2dfbf-103">ValidatorFlags Enumeration</span></span>

<span data-ttu-id="2dfbf-104">Содержит значения, указывающие тип проверки, которая должна быть выполнена при вызове метода [иклрвалидатор:: Validate](iclrvalidator-validate-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2dfbf-104">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dfbf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2dfbf-105">Syntax</span></span>  
  
```cpp  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="2dfbf-106">Члены</span><span class="sxs-lookup"><span data-stu-id="2dfbf-106">Members</span></span>  
  
|<span data-ttu-id="2dfbf-107">Член</span><span class="sxs-lookup"><span data-stu-id="2dfbf-107">Member</span></span>|<span data-ttu-id="2dfbf-108">Описание</span><span class="sxs-lookup"><span data-stu-id="2dfbf-108">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="2dfbf-109">Указывает, что следует проверять только промежуточный язык MSIL в исполняемом файле.</span><span class="sxs-lookup"><span data-stu-id="2dfbf-109">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="2dfbf-110">Указывает, что должен проверяться только формат исполняемого файла.</span><span class="sxs-lookup"><span data-stu-id="2dfbf-110">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="2dfbf-111">Указывает, что следует выполнять все типы проверки и сообщать о них.</span><span class="sxs-lookup"><span data-stu-id="2dfbf-111">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="2dfbf-112">Указывает, что формат исполняемого файла не должен проверяться.</span><span class="sxs-lookup"><span data-stu-id="2dfbf-112">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="2dfbf-113">Указывает, что сообщения об ошибках проверки должны включать строки исходного кода, вызывающие ошибки проверки.</span><span class="sxs-lookup"><span data-stu-id="2dfbf-113">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="2dfbf-114">Это значение поля недопустимо в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="2dfbf-114">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2dfbf-115">Требования</span><span class="sxs-lookup"><span data-stu-id="2dfbf-115">Requirements</span></span>  

 <span data-ttu-id="2dfbf-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2dfbf-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2dfbf-117">**Заголовок:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="2dfbf-117">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="2dfbf-118">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2dfbf-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2dfbf-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2dfbf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dfbf-120">См. также</span><span class="sxs-lookup"><span data-stu-id="2dfbf-120">See also</span></span>

- [<span data-ttu-id="2dfbf-121">Интерфейс ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="2dfbf-121">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="2dfbf-122">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="2dfbf-122">Hosting Enumerations</span></span>](hosting-enumerations.md)
