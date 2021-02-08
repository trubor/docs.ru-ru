---
description: Дополнительные сведения о функции Корбиндтокуррентрунтиме
title: Функция CorBindToCurrentRuntime
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
ms.openlocfilehash: 7dd2ab7febf4b1f87265a670a1af5d54b1e1102e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790117"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="ddb07-103">Функция CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="ddb07-103">CorBindToCurrentRuntime Function</span></span>

<span data-ttu-id="ddb07-104">Загружает среду CLR в процесс с использованием сведений о версии, хранящихся в XML-файле.</span><span class="sxs-lookup"><span data-stu-id="ddb07-104">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="ddb07-105">Формат XML-файла моделируется после стандартного файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="ddb07-105">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="ddb07-106">Дополнительные сведения о файлах конфигурации см. в разделе [Схема файла конфигурации](../../configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="ddb07-106">For more information about configuration files, see [Configuration File Schema](../../configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="ddb07-107">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ddb07-107">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="ddb07-108">См. раздел [Загрузка среды CLR в процесс](/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ddb07-108">See [Loading the Common Language Runtime into a Process](/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddb07-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ddb07-109">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddb07-110">Параметры</span><span class="sxs-lookup"><span data-stu-id="ddb07-110">Parameters</span></span>  

 `pwszFileName`  
 <span data-ttu-id="ddb07-111">окне Имя файла конфигурации приложения, указывающего версию среды CLR для загрузки.</span><span class="sxs-lookup"><span data-stu-id="ddb07-111">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="ddb07-112">Если имя файла не указано полностью, предполагается, что он находится в том же каталоге, что и исполняемый объект, вызывающий вызов.</span><span class="sxs-lookup"><span data-stu-id="ddb07-112">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="ddb07-113">Версия загружаемой среды выполнения описывается атрибутом Version в [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) элементе файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ddb07-113">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="ddb07-114">Если версия не указана или `<requiredRuntime>` элемент не найден, загружается последняя версия среды CLR, установленная на компьютере.</span><span class="sxs-lookup"><span data-stu-id="ddb07-114">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="ddb07-115">окне Объект `CLSID` coclass, реализующий интерфейс [ICorRuntimeHost](icorruntimehost-interface.md) или [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ddb07-115">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="ddb07-116">Поддерживаемые значения: CLSID_CorRuntimeHost или CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="ddb07-116">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="ddb07-117">окне `IID` Запрашиваемый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ddb07-117">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="ddb07-118">Поддерживаемые значения: IID_ICorRuntimeHost или IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="ddb07-118">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="ddb07-119">заполняет Возвращаемый указатель интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ddb07-119">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddb07-120">Требования</span><span class="sxs-lookup"><span data-stu-id="ddb07-120">Requirements</span></span>  

 <span data-ttu-id="ddb07-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddb07-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddb07-122">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ddb07-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ddb07-123">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ddb07-123">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ddb07-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddb07-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddb07-125">См. также</span><span class="sxs-lookup"><span data-stu-id="ddb07-125">See also</span></span>

- [<span data-ttu-id="ddb07-126">Функция CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="ddb07-126">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="ddb07-127">Функция CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="ddb07-127">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="ddb07-128">Функция CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="ddb07-128">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="ddb07-129">Функция CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ddb07-129">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="ddb07-130">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ddb07-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="ddb07-131">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="ddb07-131">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
