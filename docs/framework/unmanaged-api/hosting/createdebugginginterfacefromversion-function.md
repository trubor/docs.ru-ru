---
description: Дополнительные сведения о функции CreateDebuggingInterfaceFromVersion
title: Функция CreateDebuggingInterfaceFromVersion
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
ms.openlocfilehash: 163ada49f028071b48c93ee3c565152a773782ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760636"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="e816d-103">Функция CreateDebuggingInterfaceFromVersion</span><span class="sxs-lookup"><span data-stu-id="e816d-103">CreateDebuggingInterfaceFromVersion Function</span></span>

<span data-ttu-id="e816d-104">Создает объект [ICorDebug](../debugging/icordebug-interface.md) на основе указанных сведений о версии.</span><span class="sxs-lookup"><span data-stu-id="e816d-104">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="e816d-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e816d-105">This function is obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="e816d-106">Вместо этого для получения интерфейса для среды CLR 2,0 используйте метод [ICLRRuntimeInfo::](iclrruntimeinfo-getinterface-method.md) coclass и укажите идентификатор класса CLSID_CLRDebuggingLegacy и идентификатор интерфейса IID_ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="e816d-106">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="e816d-107">Чтобы получить интерфейс для CLR 4 или более поздней версии, вызовите функцию [клркреатеинстанце](clrcreateinstance-function.md) и укажите идентификатор класса CLSID_CLRDebugging и идентификатор интерфейса IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="e816d-107">To get an interface for CLR 4 or later, call the [CLRCreateInstance](clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e816d-108">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e816d-108">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e816d-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="e816d-109">Parameters</span></span>  

 `iDebuggerVersion`  
 <span data-ttu-id="e816d-110">окне Версия `ICorDebug` , ожидаемая отладчиком.</span><span class="sxs-lookup"><span data-stu-id="e816d-110">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="e816d-111">Допустимые значения см. в описании перечисления [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="e816d-111">See the [CorDebugInterfaceVersion](../debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="e816d-112">окне Версия среды CLR, связанная с приложением или процессом для отладки.</span><span class="sxs-lookup"><span data-stu-id="e816d-112">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="e816d-113">Сведения о получении этого значения см. в описании метода [GetVersionFromProcess](getversionfromprocess-function.md) или [жетрекуестедрунтимеверсион](getrequestedruntimeversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="e816d-113">See the [GetVersionFromProcess](getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="e816d-114">заполняет Расположение, которое получает указатель на `ICorDebug` объект.</span><span class="sxs-lookup"><span data-stu-id="e816d-114">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e816d-115">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="e816d-115">Return Value</span></span>  

 <span data-ttu-id="e816d-116">Этот метод возвращает стандартные коды ошибок COM, определенные в файле WinError. h, а также следующие значения.</span><span class="sxs-lookup"><span data-stu-id="e816d-116">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="e816d-117">Код возврата</span><span class="sxs-lookup"><span data-stu-id="e816d-117">Return code</span></span>|<span data-ttu-id="e816d-118">Описание</span><span class="sxs-lookup"><span data-stu-id="e816d-118">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="e816d-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="e816d-119">S_OK</span></span>|<span data-ttu-id="e816d-120">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="e816d-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="e816d-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e816d-121">E_INVALIDARG</span></span>|<span data-ttu-id="e816d-122">`szDebuggeeVersion` или `ppCordb` имеет значение null, или строка версии неверна.</span><span class="sxs-lookup"><span data-stu-id="e816d-122">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e816d-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="e816d-123">Remarks</span></span>  

 <span data-ttu-id="e816d-124">`szDebuggeeVersion`Параметр сопоставляется с соответствующей версией MSCorDbi.dll.</span><span class="sxs-lookup"><span data-stu-id="e816d-124">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e816d-125">Требования</span><span class="sxs-lookup"><span data-stu-id="e816d-125">Requirements</span></span>  

 <span data-ttu-id="e816d-126">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e816d-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e816d-127">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e816d-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e816d-128">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e816d-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e816d-129">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e816d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e816d-130">См. также</span><span class="sxs-lookup"><span data-stu-id="e816d-130">See also</span></span>

- [<span data-ttu-id="e816d-131">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="e816d-131">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
