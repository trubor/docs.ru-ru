---
description: 'Дополнительные сведения: Fusion Global static functions'
title: Глобальные статические функции Fusion
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
ms.openlocfilehash: c696908f72d67ecff5e7383e7a2754dd5436b819
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761087"
---
# <a name="fusion-global-static-functions"></a><span data-ttu-id="a1c13-103">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="a1c13-103">Fusion Global Static Functions</span></span>

<span data-ttu-id="a1c13-104">В этом разделе описаны неуправляемые глобальные статические функции, используемые API Fusion.</span><span class="sxs-lookup"><span data-stu-id="a1c13-104">This section describes the unmanaged global static functions that the fusion API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1c13-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="a1c13-105">In This Section</span></span>  

 [<span data-ttu-id="a1c13-106">Функция ClearDownloadCache</span><span class="sxs-lookup"><span data-stu-id="a1c13-106">ClearDownloadCache Function</span></span>](cleardownloadcache-function.md)  
 <span data-ttu-id="a1c13-107">Очищает глобальный кэш сборок скачанных сборок.</span><span class="sxs-lookup"><span data-stu-id="a1c13-107">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
 [<span data-ttu-id="a1c13-108">Функция CompareAssemblyIdentity</span><span class="sxs-lookup"><span data-stu-id="a1c13-108">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)  
 <span data-ttu-id="a1c13-109">Сравнивает два идентификатора сборки, чтобы определить, являются ли они эквивалентными.</span><span class="sxs-lookup"><span data-stu-id="a1c13-109">Compares two assembly identities to determine whether they are equivalent.</span></span>  
  
 [<span data-ttu-id="a1c13-110">Функция CreateApplicationContext</span><span class="sxs-lookup"><span data-stu-id="a1c13-110">CreateApplicationContext Function</span></span>](createapplicationcontext-function.md)  
 <span data-ttu-id="a1c13-111">Только для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="a1c13-111">Internal only.</span></span> <span data-ttu-id="a1c13-112">(Эта функция поддерживает инфраструктуру платформа .NET Framework и не предназначена для непосредственного использования в коде.)</span><span class="sxs-lookup"><span data-stu-id="a1c13-112">(This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.)</span></span>  
  
 [<span data-ttu-id="a1c13-113">Функция CreateAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="a1c13-113">CreateAssemblyCache Function</span></span>](createassemblycache-function.md)  
 <span data-ttu-id="a1c13-114">Возвращает указатель на новый экземпляр [IAssemblyCache](iassemblycache-interface.md) , представляющий глобальный кэш сборок.</span><span class="sxs-lookup"><span data-stu-id="a1c13-114">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
 [<span data-ttu-id="a1c13-115">Функция CreateAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="a1c13-115">CreateAssemblyEnum Function</span></span>](createassemblyenum-function.md)  
 <span data-ttu-id="a1c13-116">Возвращает указатель на экземпляр [IAssemblyEnum](iassemblyenum-interface.md) , представляющий список объектов, существующих в указанной сборке.</span><span class="sxs-lookup"><span data-stu-id="a1c13-116">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that represents a list of objects that exist in the specified assembly.</span></span>  
  
 [<span data-ttu-id="a1c13-117">Функция CreateAssemblyNameObject</span><span class="sxs-lookup"><span data-stu-id="a1c13-117">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)  
 <span data-ttu-id="a1c13-118">Возвращает указатель на экземпляр [IAssemblyName](iassemblyname-interface.md) , представляющий уникальный идентификатор сборки с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="a1c13-118">Gets a pointer to an [IAssemblyName](iassemblyname-interface.md) instance that represents the unique identity of the assembly with the specified name.</span></span>  
  
 [<span data-ttu-id="a1c13-119">Функция CreateHistoryReader</span><span class="sxs-lookup"><span data-stu-id="a1c13-119">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)  
 <span data-ttu-id="a1c13-120">Создает средство чтения журнала для указанного файла.</span><span class="sxs-lookup"><span data-stu-id="a1c13-120">Creates a history reader for the specified file.</span></span>  
  
 [<span data-ttu-id="a1c13-121">Функция CreateInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="a1c13-121">CreateInstallReferenceEnum Function</span></span>](createinstallreferenceenum-function.md)  
 <span data-ttu-id="a1c13-122">Возвращает указатель на экземпляр [IInstallReferenceEnum](iinstallreferenceenum-interface.md) , представляющий список ссылок приложения на указанную сборку.</span><span class="sxs-lookup"><span data-stu-id="a1c13-122">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
 [<span data-ttu-id="a1c13-123">Функция GetAppIdAuthority</span><span class="sxs-lookup"><span data-stu-id="a1c13-123">GetAppIdAuthority Function</span></span>](getappidauthority-function.md)  
 <span data-ttu-id="a1c13-124">Возвращает указатель на экземпляр [иаппидаусорити](iappidauthority-interface.md) , который управляет ключами для удостоверений приложений и ссылок.</span><span class="sxs-lookup"><span data-stu-id="a1c13-124">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="a1c13-125">Функция GetAssemblyIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="a1c13-125">GetAssemblyIdentityFromFile Function</span></span>](getassemblyidentityfromfile-function.md)  
 <span data-ttu-id="a1c13-126">Возвращает указатель на `IUnknown` объект с указанным `IID` в сборке по указанному пути к файлу.</span><span class="sxs-lookup"><span data-stu-id="a1c13-126">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
 [<span data-ttu-id="a1c13-127">Функция GetCachePath</span><span class="sxs-lookup"><span data-stu-id="a1c13-127">GetCachePath Function</span></span>](getcachepath-function.md)  
 <span data-ttu-id="a1c13-128">Возвращает путь к кэшированной сборке с использованием указанных флагов.</span><span class="sxs-lookup"><span data-stu-id="a1c13-128">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
 [<span data-ttu-id="a1c13-129">Функция GetHistoryFileDirectory</span><span class="sxs-lookup"><span data-stu-id="a1c13-129">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)  
 <span data-ttu-id="a1c13-130">Возвращает путь к каталогу журнала приложения.</span><span class="sxs-lookup"><span data-stu-id="a1c13-130">Retrieves the path of the application history directory.</span></span>  
  
 [<span data-ttu-id="a1c13-131">Функция GetIdentityAuthority</span><span class="sxs-lookup"><span data-stu-id="a1c13-131">GetIdentityAuthority Function</span></span>](getidentityauthority-function.md)  
 <span data-ttu-id="a1c13-132">Возвращает указатель на экземпляр [IIdentityAuthority](iidentityauthority-interface.md) , который управляет ключами для объектов кода.</span><span class="sxs-lookup"><span data-stu-id="a1c13-132">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
 [<span data-ttu-id="a1c13-133">Функция IsFrameworkAssembly</span><span class="sxs-lookup"><span data-stu-id="a1c13-133">IsFrameworkAssembly Function</span></span>](isframeworkassembly-function.md)  
 <span data-ttu-id="a1c13-134">Возвращает значение, указывающее, является ли указанная сборка управляемой.</span><span class="sxs-lookup"><span data-stu-id="a1c13-134">Gets a value that indicates whether the specified assembly is managed.</span></span>  
  
 [<span data-ttu-id="a1c13-135">Функция NukeDownloadedCache</span><span class="sxs-lookup"><span data-stu-id="a1c13-135">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)  
 <span data-ttu-id="a1c13-136">Удаляет кэш загрузки среды CLR.</span><span class="sxs-lookup"><span data-stu-id="a1c13-136">Deletes the common language runtime download cache.</span></span>  
  
 [<span data-ttu-id="a1c13-137">Функция PreBindAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="a1c13-137">PreBindAssemblyEx Function</span></span>](prebindassemblyex-function.md)  
 <span data-ttu-id="a1c13-138">Возвращает отображаемое имя после применения политики для сборки.</span><span class="sxs-lookup"><span data-stu-id="a1c13-138">Gets the post-policy display name for an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a1c13-139">См. также</span><span class="sxs-lookup"><span data-stu-id="a1c13-139">Related Sections</span></span>  

 [<span data-ttu-id="a1c13-140">Fusion-интерфейсы</span><span class="sxs-lookup"><span data-stu-id="a1c13-140">Fusion Interfaces</span></span>](fusion-interfaces.md)  
  
 [<span data-ttu-id="a1c13-141">Перечисления Fusion</span><span class="sxs-lookup"><span data-stu-id="a1c13-141">Fusion Enumerations</span></span>](fusion-enumerations.md)  
  
 [<span data-ttu-id="a1c13-142">Структуры Fusion</span><span class="sxs-lookup"><span data-stu-id="a1c13-142">Fusion Structures</span></span>](fusion-structures.md)  
  
 [<span data-ttu-id="a1c13-143">Глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="a1c13-143">Global Assembly Cache</span></span>](../../app-domains/gac.md)
