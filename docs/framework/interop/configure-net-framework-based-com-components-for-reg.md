---
title: Практическое руководство. Настройка COM-компонентов на основе платформы .NET Framework для активации без регистрации
description: Настройка COM-компонентов на основе .NET для активации без регистрации. Для настройки требуется манифест приложения в стиле Win32 и манифест компонента .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: ffeb342f286663ee7fe733ee617741e0ab30d0d8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96282877"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="072a1-104">Практическое руководство. Настройка COM-компонентов на основе платформы .NET Framework для активации без регистрации</span><span class="sxs-lookup"><span data-stu-id="072a1-104">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>

<span data-ttu-id="072a1-105">Активация компонентов на основе платформы .NET Framework без регистрации осуществляется лишь немного сложнее, чем для COM-компонентов.</span><span class="sxs-lookup"><span data-stu-id="072a1-105">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="072a1-106">При установке требуются два манифеста:</span><span class="sxs-lookup"><span data-stu-id="072a1-106">The setup requires two manifests:</span></span>  
  
- <span data-ttu-id="072a1-107">Для определения управляемого компонента в COM-приложениях используется манифест приложения в стиле Win32.</span><span class="sxs-lookup"><span data-stu-id="072a1-107">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
- <span data-ttu-id="072a1-108">Компоненты на основе платформы .NET Framework используют манифест компонента для получения необходимых для активации сведений во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="072a1-108">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="072a1-109">В этом разделе описывается, как связать манифест приложения с приложением, манифест компонента с компонентом и внедрить манифест компонента в сборку.</span><span class="sxs-lookup"><span data-stu-id="072a1-109">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
## <a name="create-an-application-manifest"></a><span data-ttu-id="072a1-110">Создание манифеста приложения</span><span class="sxs-lookup"><span data-stu-id="072a1-110">Create an application manifest</span></span>  
  
1. <span data-ttu-id="072a1-111">С помощью редактора XML создайте (или измените) манифест приложения, принадлежащий COM-приложению, которое взаимодействует с одним или несколькими управляемыми компонентами.</span><span class="sxs-lookup"><span data-stu-id="072a1-111">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2. <span data-ttu-id="072a1-112">Вставьте следующий стандартный заголовок в начало файла:</span><span class="sxs-lookup"><span data-stu-id="072a1-112">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
     <span data-ttu-id="072a1-113">Дополнительные сведения об элементах манифеста и их атрибутах см. в статье [Application Manifests](/windows/desktop/SbsCs/application-manifests) (Манифесты приложений).</span><span class="sxs-lookup"><span data-stu-id="072a1-113">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3. <span data-ttu-id="072a1-114">Определите владельца манифеста.</span><span class="sxs-lookup"><span data-stu-id="072a1-114">Identify the owner of the manifest.</span></span> <span data-ttu-id="072a1-115">В следующем примере владельцем файла манифеста является `myComApp` версии 1.</span><span class="sxs-lookup"><span data-stu-id="072a1-115">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="msil"
      />
    </assembly>  
    ```  
  
4. <span data-ttu-id="072a1-116">Определите зависимые сборки.</span><span class="sxs-lookup"><span data-stu-id="072a1-116">Identify dependent assemblies.</span></span> <span data-ttu-id="072a1-117">В следующем примере `myComApp` зависит от `myManagedComp`.</span><span class="sxs-lookup"><span data-stu-id="072a1-117">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="x86"
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myManagedComp"
                        version="6.0.0.0"
                        processorArchitecture="X86"
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5. <span data-ttu-id="072a1-118">Сохраните файл манифеста под соответствующим именем.</span><span class="sxs-lookup"><span data-stu-id="072a1-118">Save and name the manifest file.</span></span> <span data-ttu-id="072a1-119">Имя манифеста приложения состоит из имени исполняемого файла сборки и расширения manifest.</span><span class="sxs-lookup"><span data-stu-id="072a1-119">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="072a1-120">Например, для приложения myComApp.exe файл манифеста будет носить имя myComApp.exe.manifest.</span><span class="sxs-lookup"><span data-stu-id="072a1-120">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
<span data-ttu-id="072a1-121">Манифест приложения можно установить в тот же каталог, что и COM-приложение.</span><span class="sxs-lookup"><span data-stu-id="072a1-121">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="072a1-122">Также его можно добавить в качестве ресурса в EXE-файл приложения.</span><span class="sxs-lookup"><span data-stu-id="072a1-122">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="072a1-123">Дополнительные сведения см. в разделе [О параллельных сборках](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span><span class="sxs-lookup"><span data-stu-id="072a1-123">For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
## <a name="create-a-component-manifest"></a><span data-ttu-id="072a1-124">Создание манифеста компонента</span><span class="sxs-lookup"><span data-stu-id="072a1-124">Create a component manifest</span></span>  
  
1. <span data-ttu-id="072a1-125">С помощью редактора XML создайте манифест компонента, описывающий управляемую сборку.</span><span class="sxs-lookup"><span data-stu-id="072a1-125">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2. <span data-ttu-id="072a1-126">Вставьте следующий стандартный заголовок в начало файла:</span><span class="sxs-lookup"><span data-stu-id="072a1-126">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
3. <span data-ttu-id="072a1-127">Определите владельца файла.</span><span class="sxs-lookup"><span data-stu-id="072a1-127">Identify the owner of the file.</span></span> <span data-ttu-id="072a1-128">Элемент `<assemblyIdentity>` элемента `<dependentAssembly>` в файле манифеста приложения должен соответствовать аналогичному элементу в манифесте компонента.</span><span class="sxs-lookup"><span data-stu-id="072a1-128">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="072a1-129">В следующем примере владельцем файла манифеста является `myManagedComp` версии 1.2.3.4.</span><span class="sxs-lookup"><span data-stu-id="072a1-129">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />
    </assembly>
    ```  
  
4. <span data-ttu-id="072a1-130">Определите каждый класс в сборке.</span><span class="sxs-lookup"><span data-stu-id="072a1-130">Identify each class in the assembly.</span></span> <span data-ttu-id="072a1-131">Используйте `<clrClass>` элемент для уникальной идентификации каждого класса в управляемой сборке.</span><span class="sxs-lookup"><span data-stu-id="072a1-131">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="072a1-132">Атрибуты элемента, вложенного в `<assembly>`, определены в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="072a1-132">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="072a1-133">Атрибут</span><span class="sxs-lookup"><span data-stu-id="072a1-133">Attribute</span></span>|<span data-ttu-id="072a1-134">Описание</span><span class="sxs-lookup"><span data-stu-id="072a1-134">Description</span></span>|<span data-ttu-id="072a1-135">Обязательное значение</span><span class="sxs-lookup"><span data-stu-id="072a1-135">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="072a1-136">Идентификатор, который задает активируемый класс.</span><span class="sxs-lookup"><span data-stu-id="072a1-136">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="072a1-137">Да</span><span class="sxs-lookup"><span data-stu-id="072a1-137">Yes</span></span>|  
    |`description`|<span data-ttu-id="072a1-138">Строка, которая сообщает пользователю о компоненте.</span><span class="sxs-lookup"><span data-stu-id="072a1-138">A string that informs the user about the component.</span></span> <span data-ttu-id="072a1-139">По умолчанию используется пустая строка.</span><span class="sxs-lookup"><span data-stu-id="072a1-139">An empty string is the default.</span></span>|<span data-ttu-id="072a1-140">Нет</span><span class="sxs-lookup"><span data-stu-id="072a1-140">No</span></span>|  
    |`name`|<span data-ttu-id="072a1-141">Строка, представляющая управляемый класс.</span><span class="sxs-lookup"><span data-stu-id="072a1-141">A string that represents the managed class.</span></span>|<span data-ttu-id="072a1-142">Да</span><span class="sxs-lookup"><span data-stu-id="072a1-142">Yes</span></span>|  
    |`progid`|<span data-ttu-id="072a1-143">Идентификатор, который используется для отложенной активации.</span><span class="sxs-lookup"><span data-stu-id="072a1-143">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="072a1-144">Нет</span><span class="sxs-lookup"><span data-stu-id="072a1-144">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="072a1-145">Потоковая модель COM.</span><span class="sxs-lookup"><span data-stu-id="072a1-145">The COM threading model.</span></span> <span data-ttu-id="072a1-146">По умолчанию используется значение "Both" (Оба).</span><span class="sxs-lookup"><span data-stu-id="072a1-146">"Both" is the default value.</span></span>|<span data-ttu-id="072a1-147">Нет</span><span class="sxs-lookup"><span data-stu-id="072a1-147">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="072a1-148">Используемая версия среды CLR.</span><span class="sxs-lookup"><span data-stu-id="072a1-148">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="072a1-149">Если этот атрибут не задан, а среда CLR еще не загружена, компонент загружает последнюю установленную версию среды CLR, предшествующую версии 4.</span><span class="sxs-lookup"><span data-stu-id="072a1-149">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="072a1-150">Если указать v1.0.3705, v1.1.4322 или v2.0.50727, автоматически выполняется накат версии до последней установленной версии среды CLR, предшествующей версии 4 (как правило, v2.0.50727).</span><span class="sxs-lookup"><span data-stu-id="072a1-150">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="072a1-151">Если уже загружена другая версия среды CLR и не удается загрузить указанную версию в рамках параллельного процесса, загружается указанная версия. В противном случае используется загруженная версия CLR.</span><span class="sxs-lookup"><span data-stu-id="072a1-151">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="072a1-152">Это может привести к сбою загрузки.</span><span class="sxs-lookup"><span data-stu-id="072a1-152">This might cause a load failure.</span></span>|<span data-ttu-id="072a1-153">Нет</span><span class="sxs-lookup"><span data-stu-id="072a1-153">No</span></span>|  
    |`tlbid`|<span data-ttu-id="072a1-154">Идентификатор библиотеки типов, содержащей сведения о типе класса.</span><span class="sxs-lookup"><span data-stu-id="072a1-154">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="072a1-155">Нет</span><span class="sxs-lookup"><span data-stu-id="072a1-155">No</span></span>|  
  
     <span data-ttu-id="072a1-156">Во всех тегах атрибутов учитывается регистр символов.</span><span class="sxs-lookup"><span data-stu-id="072a1-156">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="072a1-157">Просматривая библиотеку типов, экспортированную для сборки с помощью средства ObjectViewer OLE/COM (Oleview.exe), можно получить идентификаторы классов (CLSID), программ (ProgID), потоковые модели и версию среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="072a1-157">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="072a1-158">В следующем манифесте компонента определяются два класса: `testClass1` и `testClass2`.</span><span class="sxs-lookup"><span data-stu-id="072a1-158">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5. <span data-ttu-id="072a1-159">Сохраните файл манифеста под соответствующим именем.</span><span class="sxs-lookup"><span data-stu-id="072a1-159">Save and name the manifest file.</span></span> <span data-ttu-id="072a1-160">Имя манифеста компонента состоит из имени библиотеки сборки и расширения manifest.</span><span class="sxs-lookup"><span data-stu-id="072a1-160">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="072a1-161">Например, манифест для myManagedComp.dll будет носить имя myManagedComp.manifest.</span><span class="sxs-lookup"><span data-stu-id="072a1-161">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="072a1-162">Манифест компонента необходимо внедрить в сборку в качестве ресурса.</span><span class="sxs-lookup"><span data-stu-id="072a1-162">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="072a1-163">Внедрение манифеста компонента в управляемую сборку</span><span class="sxs-lookup"><span data-stu-id="072a1-163">To embed a component manifest in a managed assembly</span></span>  
  
1. <span data-ttu-id="072a1-164">Создайте скрипт ресурсов, содержащий следующую инструкцию:</span><span class="sxs-lookup"><span data-stu-id="072a1-164">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="072a1-165">В этой инструкции `myManagedComp.manifest` определяет имя внедряемого манифеста компонента.</span><span class="sxs-lookup"><span data-stu-id="072a1-165">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="072a1-166">В этом примере файл скрипта будет носить имя `myresource.rc`.</span><span class="sxs-lookup"><span data-stu-id="072a1-166">For this example, the script file name is `myresource.rc`.</span></span>  
  
2. <span data-ttu-id="072a1-167">Скомпилируйте скрипт с помощью средства компиляции ресурсов Microsoft Windows (Rc.exe).</span><span class="sxs-lookup"><span data-stu-id="072a1-167">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="072a1-168">В командной строке введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="072a1-168">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="072a1-169">Программа Rc.exe создает файл ресурсов `myresource.res`.</span><span class="sxs-lookup"><span data-stu-id="072a1-169">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3. <span data-ttu-id="072a1-170">Снова скомпилируйте исходный файл сборки и укажите файл ресурсов с помощью параметра **/win32res**:</span><span class="sxs-lookup"><span data-stu-id="072a1-170">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    `/win32res:myresource.res`  
  
     <span data-ttu-id="072a1-171">Файл, содержащий внедренные ресурсы, также носит имя `myresource.res`.</span><span class="sxs-lookup"><span data-stu-id="072a1-171">Again, `myresource.res` is the name of the resource file containing embedded resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="072a1-172">См. также</span><span class="sxs-lookup"><span data-stu-id="072a1-172">See also</span></span>

- [<span data-ttu-id="072a1-173">COM-взаимодействие без регистрации</span><span class="sxs-lookup"><span data-stu-id="072a1-173">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)
- <span data-ttu-id="072a1-174">[Требования для COM-взаимодействия без регистрации](/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="072a1-174">[Requirements for Registration-Free COM Interop](/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span></span>
- <span data-ttu-id="072a1-175">[Настройка COM-компонентов для активации без регистрации](/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="072a1-175">[Configuring COM Components for Registration-Free Activation](/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span></span>
- <span data-ttu-id="072a1-176">[Активация компонентов на основе платформы .NET без регистрации. Пошаговое руководство](/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="072a1-176">[Registration-Free Activation of .NET-Based Components: A Walkthrough](/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span></span>
