---
description: 'Дополнительные сведения о: интерфейсы размещения CLR, добавленные в платформа .NET Framework 4 и 4,5'
title: Интерфейсы размещения CLR, добавленные в версиях .NET Framework 4 и 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: e7c5dd042822be8653d9c068e85a751aed622f06
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799919"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="7628d-103">Интерфейсы размещения CLR, добавленные в версиях .NET Framework 4 и 4.5</span><span class="sxs-lookup"><span data-stu-id="7628d-103">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>

<span data-ttu-id="7628d-104">В этом разделе описываются интерфейсы, которые могут использоваться неуправляемыми узлами для интеграции среды CLR в платформа .NET Framework 4, платформа .NET Framework 4,5 и более поздних версий в свои приложения.</span><span class="sxs-lookup"><span data-stu-id="7628d-104">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework 4, .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="7628d-105">Эти интерфейсы предоставляют основному приложению методы для настройки и загрузки среды выполнения в процесс.</span><span class="sxs-lookup"><span data-stu-id="7628d-105">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="7628d-106">Начиная с платформа .NET Framework 4, все интерфейсы размещения имеют следующие характеристики.</span><span class="sxs-lookup"><span data-stu-id="7628d-106">Starting with the .NET Framework 4, all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="7628d-107">Они используют управление жизненным циклом ( `AddRef` и `Release` ), инкапсуляцию (неявный контекст) и `QueryInterface` из com.</span><span class="sxs-lookup"><span data-stu-id="7628d-107">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="7628d-108">Они не используют типы COM, такие как `BSTR` , `SAFEARRAY` или `VARIANT` .</span><span class="sxs-lookup"><span data-stu-id="7628d-108">They do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="7628d-109">Нет моделей апартамента, агрегирования или активации реестра, использующих [функцию CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).</span><span class="sxs-lookup"><span data-stu-id="7628d-109">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7628d-110">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="7628d-110">In This Section</span></span>  

 [<span data-ttu-id="7628d-111">Интерфейс ICLRAppDomainResourceMonitor</span><span class="sxs-lookup"><span data-stu-id="7628d-111">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="7628d-112">Предоставляет методы для проверки использования памяти и ЦП домена приложения.</span><span class="sxs-lookup"><span data-stu-id="7628d-112">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="7628d-113">Интерфейс ICLRDomainManager</span><span class="sxs-lookup"><span data-stu-id="7628d-113">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)  
 <span data-ttu-id="7628d-114">Позволяет узлу указать Диспетчер домена приложения, который будет использоваться для инициализации домена приложения по умолчанию, а также для указания свойств инициализации.</span><span class="sxs-lookup"><span data-stu-id="7628d-114">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="7628d-115">Интерфейс ICLRGCManager2</span><span class="sxs-lookup"><span data-stu-id="7628d-115">ICLRGCManager2 Interface</span></span>](iclrgcmanager2-interface.md)  
 <span data-ttu-id="7628d-116">Предоставляет метод [SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) , который позволяет основному приложению задать размер сегмента сборки мусора и максимальный размер поколения 0 в результате создания системы сборки мусора для значений, превышающих `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="7628d-116">Provides the [SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="7628d-117">Интерфейс ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="7628d-117">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)  
 <span data-ttu-id="7628d-118">Предоставляет методы, возвращающие определенную версию среды CLR, список всех установленных CLR, список всех выполняемых в процессе сред выполнения, возвращение интерфейса активации и обнаружение версии среды CLR, используемой для компиляции сборки.</span><span class="sxs-lookup"><span data-stu-id="7628d-118">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="7628d-119">Интерфейс ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="7628d-119">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="7628d-120">Предоставляет метод [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) , ПРЕДОСТАВЛЯЮЩИЙ интерфейс CLR на основе критериев политики, управляемой сборки, версии и файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="7628d-120">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="7628d-121">Интерфейс ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="7628d-121">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)  
 <span data-ttu-id="7628d-122">Предоставляет методы, возвращающие сведения о конкретной среде выполнения, включая версию, каталог и состояние загрузки.</span><span class="sxs-lookup"><span data-stu-id="7628d-122">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="7628d-123">Интерфейс ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="7628d-123">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)  
 <span data-ttu-id="7628d-124">Предоставляет базовые глобальные статические функции для подписи сборок со строгими именами.</span><span class="sxs-lookup"><span data-stu-id="7628d-124">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="7628d-125">Все методы [метод iclrstrongname](iclrstrongname-interface.md) возвращают стандартные значения HRESULT для com.</span><span class="sxs-lookup"><span data-stu-id="7628d-125">All the [ICLRStrongName](iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="7628d-126">Интерфейс ICLRStrongName2</span><span class="sxs-lookup"><span data-stu-id="7628d-126">ICLRStrongName2 Interface</span></span>](iclrstrongname2-interface.md)  
 <span data-ttu-id="7628d-127">Предоставляет возможность создания строгих имен с помощью группы SHA-2 алгоритмов безопасных хэширования (SHA-256, SHA-384 и SHA-512).</span><span class="sxs-lookup"><span data-stu-id="7628d-127">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="7628d-128">Интерфейс ICLRTask2</span><span class="sxs-lookup"><span data-stu-id="7628d-128">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)  
 <span data-ttu-id="7628d-129">Предоставляет все функциональные возможности [интерфейса ICLRTask](iclrtask-interface.md); Кроме того, предоставляет методы, которые позволяют задерживать прерывания потока в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="7628d-129">Provides all the functionality of the [ICLRTask Interface](iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7628d-130">См. также</span><span class="sxs-lookup"><span data-stu-id="7628d-130">Related Sections</span></span>  

 [<span data-ttu-id="7628d-131">Устаревшие интерфейсы размещения CLR и CoClasses</span><span class="sxs-lookup"><span data-stu-id="7628d-131">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="7628d-132">Описание интерфейсов размещения, поставляемых с платформа .NET Framework версиями 1,0 и 1,1.</span><span class="sxs-lookup"><span data-stu-id="7628d-132">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="7628d-133">Интерфейсы размещения CLR</span><span class="sxs-lookup"><span data-stu-id="7628d-133">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="7628d-134">Описывает интерфейсы размещения, предоставляемые с платформа .NET Framework версиями 2,0, 3,0 и 3,5.</span><span class="sxs-lookup"><span data-stu-id="7628d-134">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="7628d-135">Размещение</span><span class="sxs-lookup"><span data-stu-id="7628d-135">Hosting</span></span>](index.md)  
 <span data-ttu-id="7628d-136">Введение в размещение в платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7628d-136">Introduces hosting in the .NET Framework.</span></span>
