---
description: 'Дополнительные сведения о методе: ICorDebugProcess6:: EnableVirtualModuleSplitting'
title: Метод ICorDebugProcess6::EnableVirtualModuleSplitting
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
ms.openlocfilehash: e56e66744ab971deba18f3bdc66d0cfb2053087f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722026"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a><span data-ttu-id="0f617-103">Метод ICorDebugProcess6::EnableVirtualModuleSplitting</span><span class="sxs-lookup"><span data-stu-id="0f617-103">ICorDebugProcess6::EnableVirtualModuleSplitting Method</span></span>

<span data-ttu-id="0f617-104">Позволяет включить или отключить разделение виртуальных модулей.</span><span class="sxs-lookup"><span data-stu-id="0f617-104">Enables or disables virtual module splitting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f617-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0f617-105">Syntax</span></span>  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f617-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0f617-106">Parameters</span></span>  

 `enableSplitting`  
 <span data-ttu-id="0f617-107">`true`, чтобы включить разделение виртуальных модулей; `false`, чтобы отключить его.</span><span class="sxs-lookup"><span data-stu-id="0f617-107">`true` to enable virtual module splitting; `false` to disable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f617-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="0f617-108">Remarks</span></span>  

 <span data-ttu-id="0f617-109">Разделение виртуальных [модулей заставляет препроцессор](icordebug-interface.md) распознать модули, Объединенные в ходе процесса сборки, и представлять их как группу отдельных модулей, а не один большой модуль.</span><span class="sxs-lookup"><span data-stu-id="0f617-109">Virtual module splitting causes [ICorDebug](icordebug-interface.md) to recognize modules that were merged together during the build process and present them as a group of separate modules rather than a single large module.</span></span> <span data-ttu-id="0f617-110">Это изменяет поведение различных методов [ICorDebug](icordebug-interface.md) , описанных ниже.</span><span class="sxs-lookup"><span data-stu-id="0f617-110">Doing this changes the behavior of various [ICorDebug](icordebug-interface.md) methods described below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f617-111">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="0f617-111">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="0f617-112">Этот метод может быть вызван, и значение `enableSplitting` может быть изменено, в любое время.</span><span class="sxs-lookup"><span data-stu-id="0f617-112">This method can be called and the value of `enableSplitting` can be changed at any time.</span></span> <span data-ttu-id="0f617-113">Он не вызывает функциональных изменений с отслеживанием состояния в объекте [ICorDebug](icordebug-interface.md) , кроме изменения поведения методов, перечисленных в разделе [разделение виртуального модуля, и раздела API неуправляемой отладки](#APIs) в момент их вызова.</span><span class="sxs-lookup"><span data-stu-id="0f617-113">It does not cause any stateful functional changes in an [ICorDebug](icordebug-interface.md) object, other than altering the behavior of the methods listed in the [Virtual module splitting and the unmanaged debugging APIs](#APIs) section at the time they are called.</span></span> <span data-ttu-id="0f617-114">Применение виртуальных модулей приводит к ухудшению производительности при вызове этих методов.</span><span class="sxs-lookup"><span data-stu-id="0f617-114">Using virtual modules does incur a performance penalty when calling those methods.</span></span> <span data-ttu-id="0f617-115">Кроме того, для правильной реализации интерфейсов [API интерфейса](../metadata/imetadataimport-interface.md) пользователя может потребоваться значительное кэширование в памяти, и эти кэши могут храниться даже после выключения разделения виртуальных модулей.</span><span class="sxs-lookup"><span data-stu-id="0f617-115">In addition, significant in-memory caching of the virtualized metadata may be required to correctly implement the [IMetaDataImport](../metadata/imetadataimport-interface.md) APIs, and these caches may be retained even after virtual module splitting has been turned off.</span></span>  
  
## <a name="terminology"></a><span data-ttu-id="0f617-116">Терминология</span><span class="sxs-lookup"><span data-stu-id="0f617-116">Terminology</span></span>  

 <span data-ttu-id="0f617-117">При описании разделения виртуальных модулей используются следующие термины:</span><span class="sxs-lookup"><span data-stu-id="0f617-117">The following terms are used when describing virtual module splitting:</span></span>  
  
 <span data-ttu-id="0f617-118">контейнерные модули или контейнеры</span><span class="sxs-lookup"><span data-stu-id="0f617-118">container modules, or containers</span></span>  
 <span data-ttu-id="0f617-119">Агрегатные модули.</span><span class="sxs-lookup"><span data-stu-id="0f617-119">The aggregate modules.</span></span>  
  
 <span data-ttu-id="0f617-120">вложенные модули или виртуальные модули</span><span class="sxs-lookup"><span data-stu-id="0f617-120">sub-modules, or virtual modules</span></span>  
 <span data-ttu-id="0f617-121">Модули, находящиеся в контейнере.</span><span class="sxs-lookup"><span data-stu-id="0f617-121">The modules found in a container.</span></span>  
  
 <span data-ttu-id="0f617-122">обычные модули</span><span class="sxs-lookup"><span data-stu-id="0f617-122">regular modules</span></span>  
 <span data-ttu-id="0f617-123">Модули, которые не были объединены во время построения.</span><span class="sxs-lookup"><span data-stu-id="0f617-123">Modules that were not merged at build time.</span></span> <span data-ttu-id="0f617-124">Они не являются ни вложенными, ни контейнерными модулями.</span><span class="sxs-lookup"><span data-stu-id="0f617-124">They are neither container modules nor sub-modules.</span></span>  
  
 <span data-ttu-id="0f617-125">Контейнерные модули и вложенные модули представляются объектами интерфейса ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="0f617-125">Both container modules and sub-modules are represented by ICorDebugModule interface objects.</span></span> <span data-ttu-id="0f617-126">Однако поведение интерфейса немного различается в каждом случае, как \<x-ref to section> описано в разделе.</span><span class="sxs-lookup"><span data-stu-id="0f617-126">However, the behavior of the interface is slightly different in each case, as the \<x-ref to section> section describes.</span></span>  
  
## <a name="modules-and-assemblies"></a><span data-ttu-id="0f617-127">Модули и сборки</span><span class="sxs-lookup"><span data-stu-id="0f617-127">Modules and assemblies</span></span>  

 <span data-ttu-id="0f617-128">Сборки с несколькими модулями не поддерживаются для сценариев объединения сборок, поэтому существует однозначное соответствие между модулем и сборкой.</span><span class="sxs-lookup"><span data-stu-id="0f617-128">Multi-module assemblies are not supported for assembly merging scenarios, so there is a one-to-one relationship between a module and an assembly.</span></span> <span data-ttu-id="0f617-129">Каждый объект ICorDebugModule, независимо от того, представляет он контейнерный или вложенный модуль, имеет соответствующий объект ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="0f617-129">Each ICorDebugModule object, regardless of whether it represents a container module or a sub-module, has a corresponding ICorDebugAssembly object.</span></span> <span data-ttu-id="0f617-130">Метод [ICorDebugModule:: Assembly](icordebugmodule-getassembly-method.md) преобразует из модуля в сборку.</span><span class="sxs-lookup"><span data-stu-id="0f617-130">The [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) method converts from the module to the assembly.</span></span> <span data-ttu-id="0f617-131">Для отображения в другом направлении метод [ICorDebugAssembly:: енумератемодулес](icordebugassembly-enumeratemodules-method.md) перечисляет только 1 модуль.</span><span class="sxs-lookup"><span data-stu-id="0f617-131">To map in the other direction, the [ICorDebugAssembly::EnumerateModules](icordebugassembly-enumeratemodules-method.md) method enumerates only 1 module.</span></span> <span data-ttu-id="0f617-132">Так как сборка и модуль образуют в данном случае тесно связанную пару, термины «сборка и модуль» становятся в значительной степени взаимозаменяемыми.</span><span class="sxs-lookup"><span data-stu-id="0f617-132">Because assembly and module form a tightly coupled pair in this case, the terms assembly and module become largely interchangeable.</span></span>  
  
## <a name="behavioral-differences"></a><span data-ttu-id="0f617-133">Различия в поведении</span><span class="sxs-lookup"><span data-stu-id="0f617-133">Behavioral differences</span></span>  

 <span data-ttu-id="0f617-134">Контейнерные модули имеют следующие режимы поведения и характеристики:</span><span class="sxs-lookup"><span data-stu-id="0f617-134">Container modules have the following behaviors and characteristics:</span></span>  
  
- <span data-ttu-id="0f617-135">Их метаданные для всех составных вложенных модулей объединяются друг с другом.</span><span class="sxs-lookup"><span data-stu-id="0f617-135">Their metadata for all of the constituent sub-modules is merged together.</span></span>  
  
- <span data-ttu-id="0f617-136">Имена типов можно изменять.</span><span class="sxs-lookup"><span data-stu-id="0f617-136">Their type names may be mangled.</span></span>  
  
- <span data-ttu-id="0f617-137">Метод [ICorDebugModule::-Name](icordebugmodule-getname-method.md) Возвращает путь к модулю на диске.</span><span class="sxs-lookup"><span data-stu-id="0f617-137">The [ICorDebugModule::GetName](icordebugmodule-getname-method.md) method returns the path to an on-disk module.</span></span>  
  
- <span data-ttu-id="0f617-138">Метод [ICorDebugModule:: resize](icordebugmodule-getsize-method.md) возвращает размер этого изображения.</span><span class="sxs-lookup"><span data-stu-id="0f617-138">The [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) method returns the size of that image.</span></span>  
  
- <span data-ttu-id="0f617-139">Метод ICorDebugAssembly3.EnumerateContainedAssemblies перечисляет вложенные модули.</span><span class="sxs-lookup"><span data-stu-id="0f617-139">The ICorDebugAssembly3.EnumerateContainedAssemblies method lists the sub-modules.</span></span>  
  
- <span data-ttu-id="0f617-140">Метод ICorDebugAssembly3.GetContainerAssembly возвращает `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="0f617-140">The ICorDebugAssembly3.GetContainerAssembly method returns `S_FALSE`.</span></span>  
  
 <span data-ttu-id="0f617-141">Вложенные модули имеют следующие режимы поведения и характеристики:</span><span class="sxs-lookup"><span data-stu-id="0f617-141">Sub-modules have the following behaviors and characteristics:</span></span>  
  
- <span data-ttu-id="0f617-142">Они имеют сокращенный набор метаданных, соответствующий исходной сборке, которая была объединена.</span><span class="sxs-lookup"><span data-stu-id="0f617-142">They have a reduced set of metadata that corresponds only to the original assembly that was merged.</span></span>  
  
- <span data-ttu-id="0f617-143">Имена метаданных не изменяются.</span><span class="sxs-lookup"><span data-stu-id="0f617-143">The metadata names are not mangled.</span></span>  
  
- <span data-ttu-id="0f617-144">Маловероятно, что токены метаданных будут совпадать с токенами в исходной сборке перед тем, как она была объединена в процессе построения.</span><span class="sxs-lookup"><span data-stu-id="0f617-144">Metadata tokens are unlikely to match the tokens in the original assembly before it was merged in the build process.</span></span>  
  
- <span data-ttu-id="0f617-145">Метод [ICorDebugModule::-Name](icordebugmodule-getname-method.md) возвращает имя сборки, а не путь к файлу.</span><span class="sxs-lookup"><span data-stu-id="0f617-145">The [ICorDebugModule::GetName](icordebugmodule-getname-method.md) method returns the assembly name, not a file path.</span></span>  
  
- <span data-ttu-id="0f617-146">Метод [ICorDebugModule:: resize](icordebugmodule-getsize-method.md) возвращает исходный необъединенный размер изображения.</span><span class="sxs-lookup"><span data-stu-id="0f617-146">The [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) method returns the original unmerged image size.</span></span>  
  
- <span data-ttu-id="0f617-147">Метод ICorDebugModule3.EnumerateContainedAssemblies возвращает `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="0f617-147">The ICorDebugModule3.EnumerateContainedAssemblies method returns `S_FALSE`.</span></span>  
  
- <span data-ttu-id="0f617-148">Метод ICorDebugAssembly3.GetContainerAssembly возвращает составной модуль.</span><span class="sxs-lookup"><span data-stu-id="0f617-148">The ICorDebugAssembly3.GetContainerAssembly method returns the containing module.</span></span>  
  
## <a name="interfaces-retrieved-from-modules"></a><span data-ttu-id="0f617-149">Интерфейсы, извлеченные из модулей</span><span class="sxs-lookup"><span data-stu-id="0f617-149">Interfaces retrieved from modules</span></span>  

 <span data-ttu-id="0f617-150">Из модулей можно создать или извлечь различные интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="0f617-150">A variety of interfaces can be created or retrieved from modules.</span></span> <span data-ttu-id="0f617-151">Ниже перечислены некоторые из них.</span><span class="sxs-lookup"><span data-stu-id="0f617-151">Some of these include:</span></span>  
  
- <span data-ttu-id="0f617-152">Объект ICorDebugClass, возвращаемый методом [ICorDebugModule:: жетклассфромтокен](icordebugmodule-getclassfromtoken-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0f617-152">An ICorDebugClass object, which is returned by the [ICorDebugModule::GetClassFromToken](icordebugmodule-getclassfromtoken-method.md) method.</span></span>  
  
- <span data-ttu-id="0f617-153">Объект ICorDebugAssembly, возвращаемый методом [ICorDebugModule::](icordebugmodule-getassembly-method.md) GetObject.</span><span class="sxs-lookup"><span data-stu-id="0f617-153">An ICorDebugAssembly object, which is returned by the [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) method.</span></span>  
  
 <span data-ttu-id="0f617-154">Эти объекты всегда кэшируются в [ICorDebug](icordebug-interface.md), и они будут иметь одинаковое удостоверение указателя независимо от того, были ли они созданы или запрошены из модуля контейнера или из подмодуля.</span><span class="sxs-lookup"><span data-stu-id="0f617-154">These objects are always cached by [ICorDebug](icordebug-interface.md), and they will have the same pointer identity regardless of whether they were created or queried from the container module or a sub-module.</span></span> <span data-ttu-id="0f617-155">Вложенный модуль обеспечивает отфильтрованное представление этих кэшированных объектов, но не отдельный кэш со своими собственными копиями.</span><span class="sxs-lookup"><span data-stu-id="0f617-155">The sub-module provides a filtered view of these cached objects, not a separate cache with its own copies.</span></span>  
  
<a name="APIs"></a>

## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a><span data-ttu-id="0f617-156">Разделение виртуальных модулей и неуправляемые интерфейсы API отладки</span><span class="sxs-lookup"><span data-stu-id="0f617-156">Virtual module splitting and the unmanaged debugging APIs</span></span>  

 <span data-ttu-id="0f617-157">В следующей таблице показано, как разделение виртуальных модулей влияет на поведение других методов в неуправляемом интерфейсе API отладки.</span><span class="sxs-lookup"><span data-stu-id="0f617-157">The following table shows how virtual module splitting affects the behavior of other methods in the unmanaged debugging API.</span></span>  
  
|<span data-ttu-id="0f617-158">Метод</span><span class="sxs-lookup"><span data-stu-id="0f617-158">Method</span></span>|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[<span data-ttu-id="0f617-159">ICorDebugFunction::GetModule</span><span class="sxs-lookup"><span data-stu-id="0f617-159">ICorDebugFunction::GetModule</span></span>](icordebugfunction-getmodule-method.md)|<span data-ttu-id="0f617-160">Возвращает вложенный модуль, в котором эта функция была изначально определена</span><span class="sxs-lookup"><span data-stu-id="0f617-160">Returns the sub-module this function was originally defined in</span></span>|<span data-ttu-id="0f617-161">Возвращает контейнерный модуль, в который была добавлена эта функция</span><span class="sxs-lookup"><span data-stu-id="0f617-161">Returns the container module this function was merged into</span></span>|  
|[<span data-ttu-id="0f617-162">ICorDebugClass::GetModule</span><span class="sxs-lookup"><span data-stu-id="0f617-162">ICorDebugClass::GetModule</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="0f617-163">Возвращает вложенный модуль, в котором этот класс был изначально определен.</span><span class="sxs-lookup"><span data-stu-id="0f617-163">Returns the sub-module this class was originally defined in.</span></span>|<span data-ttu-id="0f617-164">Возвращает контейнерный модуль, в который был добавлен этот класс.</span><span class="sxs-lookup"><span data-stu-id="0f617-164">Returns the container module this class was merged into.</span></span>|  
|<span data-ttu-id="0f617-165">ICorDebugModuleDebugEvent::GetModule</span><span class="sxs-lookup"><span data-stu-id="0f617-165">ICorDebugModuleDebugEvent::GetModule</span></span>|<span data-ttu-id="0f617-166">Возвращает контейнерный модуль, который был загружен.</span><span class="sxs-lookup"><span data-stu-id="0f617-166">Returns the container module that was loaded.</span></span> <span data-ttu-id="0f617-167">Независимо от данного параметра, вложенные модули не получают события загрузки.</span><span class="sxs-lookup"><span data-stu-id="0f617-167">Sub-modules are not given load events regardless of this setting.</span></span>|<span data-ttu-id="0f617-168">Возвращает контейнерный модуль, который был загружен.</span><span class="sxs-lookup"><span data-stu-id="0f617-168">Returns the container module that was loaded.</span></span>|  
|[<span data-ttu-id="0f617-169">ICorDebugAppDomain::EnumerateAssemblies</span><span class="sxs-lookup"><span data-stu-id="0f617-169">ICorDebugAppDomain::EnumerateAssemblies</span></span>](icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="0f617-170">Возвращает перечень сборочных узлов и регулярных сборок; контейнерные сборки не включаются.</span><span class="sxs-lookup"><span data-stu-id="0f617-170">Returns a list of sub-assemblies and regular assemblies; no container assemblies are included.</span></span> <span data-ttu-id="0f617-171">**Примечание.**  Если в любой сборке контейнера отсутствуют символы, ни одна из ее вложенных сборок не будет перечисляться.</span><span class="sxs-lookup"><span data-stu-id="0f617-171">**Note:**  If any container assembly is missing symbols, none of its sub-assemblies will be enumerated.</span></span> <span data-ttu-id="0f617-172">Если в любой регулярной сборке отсутствуют символы, то она может быть перечислена или не перечислена.</span><span class="sxs-lookup"><span data-stu-id="0f617-172">If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|<span data-ttu-id="0f617-173">Возвращает перечень контейнерных сборок и регулярных сборок; сборочные узлы не включаются.</span><span class="sxs-lookup"><span data-stu-id="0f617-173">Returns a list of container assemblies and regular assemblies; no sub-assemblies are included.</span></span> <span data-ttu-id="0f617-174">**Примечание.**  Если в любой обычной сборке отсутствуют символы, она может быть или не перечисляться.</span><span class="sxs-lookup"><span data-stu-id="0f617-174">**Note:**  If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|  
|<span data-ttu-id="0f617-175">[ICorDebugCode::-Code](icordebugcode-getcode-method.md) (при ссылке только на код IL)</span><span class="sxs-lookup"><span data-stu-id="0f617-175">[ICorDebugCode::GetCode](icordebugcode-getcode-method.md) (when referring to IL code only)</span></span>|<span data-ttu-id="0f617-176">Возвращает IL-код, который будет действителен в образе сборки перед слиянием.</span><span class="sxs-lookup"><span data-stu-id="0f617-176">Returns IL that would be valid in a pre-merge assembly image.</span></span> <span data-ttu-id="0f617-177">В частности, любыми правильными встроенными токенами метаданных будут TypeRef или MemberRef, когда типы, на которые выполняется ссылка, не определены в виртуальном модуле, содержащем IL-код.</span><span class="sxs-lookup"><span data-stu-id="0f617-177">Specifically, any inline metadata tokens will correctly be TypeRef or MemberRef tokens when the types being referred to are not defined in the virtual module containing the IL.</span></span> <span data-ttu-id="0f617-178">Эти токены TypeRef или MemberRef можно искать в объекте [IMetaDataImport](../metadata/imetadataimport-interface.md) для соответствующего виртуального объекта ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="0f617-178">These TypeRef or MemberRef tokens can be looked up in the [IMetaDataImport](../metadata/imetadataimport-interface.md) object for the corresponding virtual ICorDebugModule object.</span></span>|<span data-ttu-id="0f617-179">Возвращает IL-код в образе сборки после слияния.</span><span class="sxs-lookup"><span data-stu-id="0f617-179">Returns the IL in the post-merge assembly image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f617-180">Требования</span><span class="sxs-lookup"><span data-stu-id="0f617-180">Requirements</span></span>  

 <span data-ttu-id="0f617-181">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f617-181">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f617-182">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f617-182">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f617-183">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f617-183">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f617-184">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f617-184">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f617-185">См. также</span><span class="sxs-lookup"><span data-stu-id="0f617-185">See also</span></span>

- [<span data-ttu-id="0f617-186">Интерфейс ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="0f617-186">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="0f617-187">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="0f617-187">Debugging Interfaces</span></span>](debugging-interfaces.md)
