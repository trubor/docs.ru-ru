---
description: Дополнительные сведения о функции Корбиндторунтимебикфг
title: Функция CorBindToRuntimeByCfg
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
ms.openlocfilehash: c1acf6a8f1d8637bc2d6cd180016ff51cf500107
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790078"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="84812-103">Функция CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="84812-103">CorBindToRuntimeByCfg Function</span></span>

<span data-ttu-id="84812-104">Загружает среду CLR в процесс с использованием сведений о версии, считываемых из XML-файла.</span><span class="sxs-lookup"><span data-stu-id="84812-104">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="84812-105">Эта функция является устаревшей в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="84812-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84812-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="84812-106">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84812-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="84812-107">Parameters</span></span>  

 `pCfgStream`  
 <span data-ttu-id="84812-108">окне Указатель на `IStream` объект, считывающий XML-файл.</span><span class="sxs-lookup"><span data-stu-id="84812-108">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="84812-109">[in] Зарезервирован для будущего использования.</span><span class="sxs-lookup"><span data-stu-id="84812-109">[in] Reserved for future use.</span></span> <span data-ttu-id="84812-110">Используйте 0 (нуль) в качестве значения.</span><span class="sxs-lookup"><span data-stu-id="84812-110">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="84812-111">окне Значение перечисления [STARTUP_FLAGS](startup-flags-enumeration.md) , указывающее поведение среды CLR при запуске.</span><span class="sxs-lookup"><span data-stu-id="84812-111">[in] A value of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="84812-112">окне Объект `CLSID` coclass, реализующий интерфейс [ICorRuntimeHost](icorruntimehost-interface.md) или [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="84812-112">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="84812-113">Поддерживаемые значения: CLSID_CorRuntimeHost или CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="84812-113">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="84812-114">окне `IID` Либо `ICorRuntimeHost` интерфейса, либо `ICLRRuntimeHost` .</span><span class="sxs-lookup"><span data-stu-id="84812-114">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="84812-115">Поддерживаемые значения: IID_ICorRuntimeHost или IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="84812-115">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="84812-116">заполняет Указатель на адрес возвращенного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="84812-116">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84812-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="84812-117">Remarks</span></span>  

 <span data-ttu-id="84812-118">Формат XML-файла моделируется после стандартного файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="84812-118">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="84812-119">Дополнительные сведения о XML-файлах см. в разделе [Схема файла конфигурации](../../configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="84812-119">For more information about XML files, see [Configuration File Schema](../../configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84812-120">Требования</span><span class="sxs-lookup"><span data-stu-id="84812-120">Requirements</span></span>  

 <span data-ttu-id="84812-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84812-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84812-122">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="84812-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84812-123">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="84812-123">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84812-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84812-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84812-125">См. также</span><span class="sxs-lookup"><span data-stu-id="84812-125">See also</span></span>

- [<span data-ttu-id="84812-126">Функция CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="84812-126">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="84812-127">Функция CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="84812-127">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="84812-128">Функция CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="84812-128">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="84812-129">Функция CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="84812-129">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="84812-130">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="84812-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="84812-131">Устаревшие функции размещения CLR</span><span class="sxs-lookup"><span data-stu-id="84812-131">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
