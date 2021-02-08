---
description: 'Дополнительные сведения о методе: ICorRuntimeHost:: метода конфигурации'
title: Метод ICorRuntimeHost::GetConfiguration
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
ms.openlocfilehash: d3e3f065c3957fb29daa11ed7c46858a53865c91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784838"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="f0c27-103">Метод ICorRuntimeHost::GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="f0c27-103">ICorRuntimeHost::GetConfiguration Method</span></span>

<span data-ttu-id="f0c27-104">Возвращает объект, позволяющий основному приложению указывать конфигурацию обратного вызова среды CLR.</span><span class="sxs-lookup"><span data-stu-id="f0c27-104">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0c27-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f0c27-105">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0c27-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f0c27-106">Parameters</span></span>  

 `pConfiguration`  
 <span data-ttu-id="f0c27-107">заполняет Указатель на адрес объекта [ICorConfiguration](icorconfiguration-interface.md) , который может использоваться для настройки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="f0c27-107">[out] A pointer to the address of an [ICorConfiguration](icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0c27-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="f0c27-108">Remarks</span></span>  

 <span data-ttu-id="f0c27-109">Прежде чем инициализировать среду CLR, ее необходимо настроить. в противном случае `GetConfiguration` метод возвращает значение HRESULT, указывающее на ошибку.</span><span class="sxs-lookup"><span data-stu-id="f0c27-109">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0c27-110">Требования</span><span class="sxs-lookup"><span data-stu-id="f0c27-110">Requirements</span></span>  

 <span data-ttu-id="f0c27-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0c27-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0c27-112">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f0c27-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0c27-113">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0c27-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0c27-114">**Платформа .NET Framework версии:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="f0c27-114">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0c27-115">См. также</span><span class="sxs-lookup"><span data-stu-id="f0c27-115">See also</span></span>

- [<span data-ttu-id="f0c27-116">Интерфейс ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="f0c27-116">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
