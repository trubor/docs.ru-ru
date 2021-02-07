---
description: 'Дополнительные сведения о методе: IValidator:: Validate'
title: Метод IValidator::Validate
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
ms.openlocfilehash: 6df70274a788b949686fe2509b525c5a8b04089c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680022"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="c5f09-103">Метод IValidator::Validate</span><span class="sxs-lookup"><span data-stu-id="c5f09-103">IValidator::Validate Method</span></span>

<span data-ttu-id="c5f09-104">Проверяет указанный переносимый исполняемый (PE) или промежуточный язык MSIL-файл.</span><span class="sxs-lookup"><span data-stu-id="c5f09-104">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5f09-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c5f09-105">Syntax</span></span>  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5f09-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c5f09-106">Parameters</span></span>  

 `veh`  
 <span data-ttu-id="c5f09-107">окне Указатель на `IVEHandler` экземпляр, который обрабатывает ошибки проверки.</span><span class="sxs-lookup"><span data-stu-id="c5f09-107">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="c5f09-108">окне Указатель на домен приложения, в который загружается файл.</span><span class="sxs-lookup"><span data-stu-id="c5f09-108">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="c5f09-109">окне Побитовое сочетание значений [валидаторфлагс](validatorflags-enumeration.md) , указывающее, какие проверки должны быть выполнены.</span><span class="sxs-lookup"><span data-stu-id="c5f09-109">[in] A bitwise combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="c5f09-110">окне Максимальное число ошибок, которое необходимо разрешить перед выходом из проверки.</span><span class="sxs-lookup"><span data-stu-id="c5f09-110">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="c5f09-111">[in] Не используется.</span><span class="sxs-lookup"><span data-stu-id="c5f09-111">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="c5f09-112">окне Строка, указывающая имя проверяемого файла.</span><span class="sxs-lookup"><span data-stu-id="c5f09-112">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="c5f09-113">окне Указатель на буфер памяти, в котором хранится файл.</span><span class="sxs-lookup"><span data-stu-id="c5f09-113">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="c5f09-114">окне Размер проверяемого файла в байтах.</span><span class="sxs-lookup"><span data-stu-id="c5f09-114">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5f09-115">Требования</span><span class="sxs-lookup"><span data-stu-id="c5f09-115">Requirements</span></span>  

 <span data-ttu-id="c5f09-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5f09-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5f09-117">**Заголовок:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="c5f09-117">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="c5f09-118">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5f09-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5f09-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5f09-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
