---
title: Regsvcs.exe (программа установки служб .NET)
description: Сведения об использовании программы установки служб .NET (Regsvcs.exe), позволяющей загрузить и зарегистрировать сборку, настроить службы, программно добавленные в класс, и выполнять другие действия.
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
ms.openlocfilehash: 58a20084457cb217f3af73f4b4ff9ea251647782
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238553"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="b7316-104">Regsvcs.exe (программа установки служб .NET)</span><span class="sxs-lookup"><span data-stu-id="b7316-104">Regsvcs.exe (.NET Services Installation Tool)</span></span>

<span data-ttu-id="b7316-105">Программа установки служб .NET выполняет следующие действия.</span><span class="sxs-lookup"><span data-stu-id="b7316-105">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="b7316-106">Загружает и регистрирует сборку.</span><span class="sxs-lookup"><span data-stu-id="b7316-106">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="b7316-107">Создает, регистрирует и устанавливает библиотеку типов в указанное приложение COM+.</span><span class="sxs-lookup"><span data-stu-id="b7316-107">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="b7316-108">Настраивает службы, которые были программно добавлены в создаваемый класс.</span><span class="sxs-lookup"><span data-stu-id="b7316-108">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="b7316-109">Чтобы применить этот инструмент, воспользуйтесь командной строкой разработчика для Visual Studio (или командной строкой Visual Studio в Windows 7).</span><span class="sxs-lookup"><span data-stu-id="b7316-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="b7316-110">Дополнительные сведения см. в разделе [Командные строки](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b7316-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="b7316-111">В командной строке введите следующее.</span><span class="sxs-lookup"><span data-stu-id="b7316-111">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7316-112">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b7316-112">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a><span data-ttu-id="b7316-113">Параметры</span><span class="sxs-lookup"><span data-stu-id="b7316-113">Parameters</span></span>  
  
|<span data-ttu-id="b7316-114">Аргумент</span><span class="sxs-lookup"><span data-stu-id="b7316-114">Argument</span></span>|<span data-ttu-id="b7316-115">Описание</span><span class="sxs-lookup"><span data-stu-id="b7316-115">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="b7316-116">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="b7316-116">*assemblyFile.dll*</span></span>|<span data-ttu-id="b7316-117">Исходный файл сборки.</span><span class="sxs-lookup"><span data-stu-id="b7316-117">The source assembly file.</span></span> <span data-ttu-id="b7316-118">Сборка должна быть подписана с использованием строгого имени.</span><span class="sxs-lookup"><span data-stu-id="b7316-118">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="b7316-119">Дополнительные сведения см. в разделе [Подпись сборки строгим именем](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="b7316-119">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="b7316-120">Параметр</span><span class="sxs-lookup"><span data-stu-id="b7316-120">Option</span></span>|<span data-ttu-id="b7316-121">Описание:</span><span class="sxs-lookup"><span data-stu-id="b7316-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b7316-122">**/appdir:** *path*</span><span class="sxs-lookup"><span data-stu-id="b7316-122">**/appdir:** *path*</span></span>|<span data-ttu-id="b7316-123">Определяет корневой каталог приложения.</span><span class="sxs-lookup"><span data-stu-id="b7316-123">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="b7316-124">**/appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="b7316-124">**/appname:** *applicationName*</span></span>|<span data-ttu-id="b7316-125">Задает имя приложения COM+, которое следует найти или создать.</span><span class="sxs-lookup"><span data-stu-id="b7316-125">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="b7316-126">**/c**</span><span class="sxs-lookup"><span data-stu-id="b7316-126">**/c**</span></span>|<span data-ttu-id="b7316-127">Создает конечное приложение.</span><span class="sxs-lookup"><span data-stu-id="b7316-127">Creates the target application.</span></span>|  
|<span data-ttu-id="b7316-128">**/componly**</span><span class="sxs-lookup"><span data-stu-id="b7316-128">**/componly**</span></span>|<span data-ttu-id="b7316-129">Выполняет только конфигурирование компонентов, методы и интерфейсы игнорируются.</span><span class="sxs-lookup"><span data-stu-id="b7316-129">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="b7316-130">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="b7316-130">**/exapp**</span></span>|<span data-ttu-id="b7316-131">Указывает, что программа будет работать с существующим приложением.</span><span class="sxs-lookup"><span data-stu-id="b7316-131">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="b7316-132">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="b7316-132">**/extlb**</span></span>|<span data-ttu-id="b7316-133">Использует существующую библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="b7316-133">Uses an existing type library.</span></span>|  
|<span data-ttu-id="b7316-134">**/fc**</span><span class="sxs-lookup"><span data-stu-id="b7316-134">**/fc**</span></span>|<span data-ttu-id="b7316-135">Находит или создает конечное приложение.</span><span class="sxs-lookup"><span data-stu-id="b7316-135">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="b7316-136">**/help**</span><span class="sxs-lookup"><span data-stu-id="b7316-136">**/help**</span></span>|<span data-ttu-id="b7316-137">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="b7316-137">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="b7316-138">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="b7316-138">**/noreconfig**</span></span>|<span data-ttu-id="b7316-139">Запрещает изменять конфигурации существующего конечного приложения.</span><span class="sxs-lookup"><span data-stu-id="b7316-139">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="b7316-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="b7316-140">**/nologo**</span></span>|<span data-ttu-id="b7316-141">Отключает отображение эмблемы Майкрософт при запуске.</span><span class="sxs-lookup"><span data-stu-id="b7316-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="b7316-142">**/parname:** *name*</span><span class="sxs-lookup"><span data-stu-id="b7316-142">**/parname:** *name*</span></span>|<span data-ttu-id="b7316-143">Задает имя или идентификатор приложения COM+, которое следует найти или создать.</span><span class="sxs-lookup"><span data-stu-id="b7316-143">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="b7316-144">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="b7316-144">**/reconfig**</span></span>|<span data-ttu-id="b7316-145">Изменяет конфигурацию существующего конечного приложения.</span><span class="sxs-lookup"><span data-stu-id="b7316-145">Reconfigures an existing target application.</span></span> <span data-ttu-id="b7316-146">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b7316-146">This is the default.</span></span>|  
|<span data-ttu-id="b7316-147">**/tlb:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="b7316-147">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="b7316-148">Задает устанавливаемый файл библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="b7316-148">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="b7316-149">**/u**</span><span class="sxs-lookup"><span data-stu-id="b7316-149">**/u**</span></span>|<span data-ttu-id="b7316-150">Удаляет конечное приложение.</span><span class="sxs-lookup"><span data-stu-id="b7316-150">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="b7316-151">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="b7316-151">**/quiet**</span></span>|<span data-ttu-id="b7316-152">Задает тихий режим, логотип и сообщения об успешном завершении операций не отображаются.</span><span class="sxs-lookup"><span data-stu-id="b7316-152">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="b7316-153">**/?**</span><span class="sxs-lookup"><span data-stu-id="b7316-153">**/?**</span></span>|<span data-ttu-id="b7316-154">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="b7316-154">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7316-155">Примечания</span><span class="sxs-lookup"><span data-stu-id="b7316-155">Remarks</span></span>  

 <span data-ttu-id="b7316-156">Программе Regsvcs.exe требуется исходный файл сборки, заданный библиотекой *assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="b7316-156">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="b7316-157">Эта сборка должна быть подписана с использованием строгого имени.</span><span class="sxs-lookup"><span data-stu-id="b7316-157">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="b7316-158">Дополнительные сведения о подписи с использованием строгого имени см. в разделе [Подпись сборки строгим именем](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="b7316-158">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="b7316-159">Имена конечного приложения и файла библиотеки типов не являются обязательными.</span><span class="sxs-lookup"><span data-stu-id="b7316-159">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="b7316-160">Аргумент *applicationName* может быть создан из исходного файла сборки, и в случае его отсутствия он будет создан программой Regsvcs.exe.</span><span class="sxs-lookup"><span data-stu-id="b7316-160">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="b7316-161">Аргумент *typelibraryfile* может задавать имя библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="b7316-161">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="b7316-162">Если имя библиотеки типов не указано, программа Regsvcs.exe по умолчанию использует имя сборки.</span><span class="sxs-lookup"><span data-stu-id="b7316-162">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="b7316-163">Когда программа Regsvcs.exe регистрирует методы компонента, к ней применяются [требования](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) и [требования ссылки](../misc/link-demands.md) для этих методов.</span><span class="sxs-lookup"><span data-stu-id="b7316-163">When Regsvcs.exe registers a component's methods, it is subject to the [demands](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="b7316-164">Поскольку эта программа выполняется в полностью доверенной среде, большинство требований на получение разрешения удовлетворяется.</span><span class="sxs-lookup"><span data-stu-id="b7316-164">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="b7316-165">Однако программа Regsvcs.exe не может регистрировать компоненты с помощью методов, защищенных требованием или требованием связи для <xref:System.Security.Permissions.StrongNameIdentityPermission> или <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="b7316-165">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="b7316-166">Для работы с программой Regsvcs.exe требуются права администратора на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="b7316-166">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="b7316-167">Если программа Regsvcs.exe не может выполнить какие-либо из этих действий, на экран выводится соответствующее сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="b7316-167">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b7316-168">Примеры</span><span class="sxs-lookup"><span data-stu-id="b7316-168">Examples</span></span>  

 <span data-ttu-id="b7316-169">Следующая команда добавляет все открытые классы, содержащиеся в `myTest.dll`, в `myTargetApp` (существующее приложение COM+) и создает библиотеку типов `myTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="b7316-169">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="b7316-170">Следующая команда добавляет все открытые классы, содержащиеся в `myTest.dll`, в `myTargetApp` (существующее приложение COM+) и создает библиотеку типов `newTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="b7316-170">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7316-171">См. также</span><span class="sxs-lookup"><span data-stu-id="b7316-171">See also</span></span>

- [<span data-ttu-id="b7316-172">Инструменты</span><span class="sxs-lookup"><span data-stu-id="b7316-172">Tools</span></span>](index.md)
- [<span data-ttu-id="b7316-173">Практическое руководство. Подписание сборки строгим именем</span><span class="sxs-lookup"><span data-stu-id="b7316-173">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="b7316-174">Командные строки</span><span class="sxs-lookup"><span data-stu-id="b7316-174">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
