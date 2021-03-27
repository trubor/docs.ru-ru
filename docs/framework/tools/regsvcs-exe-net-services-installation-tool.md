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
ms.openlocfilehash: 03787ecacc00c35f31f1fa5101fff5882e5314f6
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653313"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="a7275-104">Regsvcs.exe (программа установки служб .NET)</span><span class="sxs-lookup"><span data-stu-id="a7275-104">Regsvcs.exe (.NET Services Installation Tool)</span></span>

<span data-ttu-id="a7275-105">Программа установки служб .NET выполняет следующие действия.</span><span class="sxs-lookup"><span data-stu-id="a7275-105">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="a7275-106">Загружает и регистрирует сборку.</span><span class="sxs-lookup"><span data-stu-id="a7275-106">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="a7275-107">Создает, регистрирует и устанавливает библиотеку типов в указанное приложение COM+.</span><span class="sxs-lookup"><span data-stu-id="a7275-107">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="a7275-108">Настраивает службы, которые были программно добавлены в создаваемый класс.</span><span class="sxs-lookup"><span data-stu-id="a7275-108">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="a7275-109">Для запуска этого средства используйте [Командную строку разработчика или PowerShell для разработчиков в Visual Studio](/visualstudio/ide/reference/command-prompt-powershell).</span><span class="sxs-lookup"><span data-stu-id="a7275-109">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="a7275-110">В командной строке введите следующее.</span><span class="sxs-lookup"><span data-stu-id="a7275-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7275-111">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a7275-111">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a><span data-ttu-id="a7275-112">Параметры</span><span class="sxs-lookup"><span data-stu-id="a7275-112">Parameters</span></span>  
  
|<span data-ttu-id="a7275-113">Аргумент</span><span class="sxs-lookup"><span data-stu-id="a7275-113">Argument</span></span>|<span data-ttu-id="a7275-114">Описание</span><span class="sxs-lookup"><span data-stu-id="a7275-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a7275-115">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="a7275-115">*assemblyFile.dll*</span></span>|<span data-ttu-id="a7275-116">Исходный файл сборки.</span><span class="sxs-lookup"><span data-stu-id="a7275-116">The source assembly file.</span></span> <span data-ttu-id="a7275-117">Сборка должна быть подписана с использованием строгого имени.</span><span class="sxs-lookup"><span data-stu-id="a7275-117">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="a7275-118">Дополнительные сведения см. в разделе [Подпись сборки строгим именем](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="a7275-118">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="a7275-119">Параметр</span><span class="sxs-lookup"><span data-stu-id="a7275-119">Option</span></span>|<span data-ttu-id="a7275-120">Описание:</span><span class="sxs-lookup"><span data-stu-id="a7275-120">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a7275-121">**/appdir:** *path*</span><span class="sxs-lookup"><span data-stu-id="a7275-121">**/appdir:** *path*</span></span>|<span data-ttu-id="a7275-122">Определяет корневой каталог приложения.</span><span class="sxs-lookup"><span data-stu-id="a7275-122">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="a7275-123">**/appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="a7275-123">**/appname:** *applicationName*</span></span>|<span data-ttu-id="a7275-124">Задает имя приложения COM+, которое следует найти или создать.</span><span class="sxs-lookup"><span data-stu-id="a7275-124">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="a7275-125">**/c**</span><span class="sxs-lookup"><span data-stu-id="a7275-125">**/c**</span></span>|<span data-ttu-id="a7275-126">Создает конечное приложение.</span><span class="sxs-lookup"><span data-stu-id="a7275-126">Creates the target application.</span></span>|  
|<span data-ttu-id="a7275-127">**/componly**</span><span class="sxs-lookup"><span data-stu-id="a7275-127">**/componly**</span></span>|<span data-ttu-id="a7275-128">Выполняет только конфигурирование компонентов, методы и интерфейсы игнорируются.</span><span class="sxs-lookup"><span data-stu-id="a7275-128">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="a7275-129">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="a7275-129">**/exapp**</span></span>|<span data-ttu-id="a7275-130">Указывает, что программа будет работать с существующим приложением.</span><span class="sxs-lookup"><span data-stu-id="a7275-130">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="a7275-131">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="a7275-131">**/extlb**</span></span>|<span data-ttu-id="a7275-132">Использует существующую библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="a7275-132">Uses an existing type library.</span></span>|  
|<span data-ttu-id="a7275-133">**/fc**</span><span class="sxs-lookup"><span data-stu-id="a7275-133">**/fc**</span></span>|<span data-ttu-id="a7275-134">Находит или создает конечное приложение.</span><span class="sxs-lookup"><span data-stu-id="a7275-134">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="a7275-135">**/help**</span><span class="sxs-lookup"><span data-stu-id="a7275-135">**/help**</span></span>|<span data-ttu-id="a7275-136">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="a7275-136">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="a7275-137">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="a7275-137">**/noreconfig**</span></span>|<span data-ttu-id="a7275-138">Запрещает изменять конфигурации существующего конечного приложения.</span><span class="sxs-lookup"><span data-stu-id="a7275-138">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="a7275-139">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="a7275-139">**/nologo**</span></span>|<span data-ttu-id="a7275-140">Отключает отображение эмблемы Майкрософт при запуске.</span><span class="sxs-lookup"><span data-stu-id="a7275-140">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="a7275-141">**/parname:** *name*</span><span class="sxs-lookup"><span data-stu-id="a7275-141">**/parname:** *name*</span></span>|<span data-ttu-id="a7275-142">Задает имя или идентификатор приложения COM+, которое следует найти или создать.</span><span class="sxs-lookup"><span data-stu-id="a7275-142">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="a7275-143">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="a7275-143">**/reconfig**</span></span>|<span data-ttu-id="a7275-144">Изменяет конфигурацию существующего конечного приложения.</span><span class="sxs-lookup"><span data-stu-id="a7275-144">Reconfigures an existing target application.</span></span> <span data-ttu-id="a7275-145">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a7275-145">This is the default.</span></span>|  
|<span data-ttu-id="a7275-146">**/tlb:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="a7275-146">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="a7275-147">Задает устанавливаемый файл библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="a7275-147">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="a7275-148">**/u**</span><span class="sxs-lookup"><span data-stu-id="a7275-148">**/u**</span></span>|<span data-ttu-id="a7275-149">Удаляет конечное приложение.</span><span class="sxs-lookup"><span data-stu-id="a7275-149">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="a7275-150">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="a7275-150">**/quiet**</span></span>|<span data-ttu-id="a7275-151">Задает тихий режим, логотип и сообщения об успешном завершении операций не отображаются.</span><span class="sxs-lookup"><span data-stu-id="a7275-151">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="a7275-152">**/?**</span><span class="sxs-lookup"><span data-stu-id="a7275-152">**/?**</span></span>|<span data-ttu-id="a7275-153">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="a7275-153">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7275-154">Примечания</span><span class="sxs-lookup"><span data-stu-id="a7275-154">Remarks</span></span>  

 <span data-ttu-id="a7275-155">Программе Regsvcs.exe требуется исходный файл сборки, заданный библиотекой *assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="a7275-155">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="a7275-156">Эта сборка должна быть подписана с использованием строгого имени.</span><span class="sxs-lookup"><span data-stu-id="a7275-156">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="a7275-157">Дополнительные сведения о подписи с использованием строгого имени см. в разделе [Подпись сборки строгим именем](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="a7275-157">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="a7275-158">Имена конечного приложения и файла библиотеки типов не являются обязательными.</span><span class="sxs-lookup"><span data-stu-id="a7275-158">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="a7275-159">Аргумент *applicationName* может быть создан из исходного файла сборки, и в случае его отсутствия он будет создан программой Regsvcs.exe.</span><span class="sxs-lookup"><span data-stu-id="a7275-159">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="a7275-160">Аргумент *typelibraryfile* может задавать имя библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="a7275-160">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="a7275-161">Если имя библиотеки типов не указано, программа Regsvcs.exe по умолчанию использует имя сборки.</span><span class="sxs-lookup"><span data-stu-id="a7275-161">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="a7275-162">Когда программа Regsvcs.exe регистрирует методы компонента, к ней применяются [требования](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) и [требования ссылки](../misc/link-demands.md) для этих методов.</span><span class="sxs-lookup"><span data-stu-id="a7275-162">When Regsvcs.exe registers a component's methods, it is subject to the [demands](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="a7275-163">Поскольку эта программа выполняется в полностью доверенной среде, большинство требований на получение разрешения удовлетворяется.</span><span class="sxs-lookup"><span data-stu-id="a7275-163">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="a7275-164">Однако программа Regsvcs.exe не может регистрировать компоненты с помощью методов, защищенных требованием или требованием связи для <xref:System.Security.Permissions.StrongNameIdentityPermission> или <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="a7275-164">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="a7275-165">Для работы с программой Regsvcs.exe требуются права администратора на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="a7275-165">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="a7275-166">Если программа Regsvcs.exe не может выполнить какие-либо из этих действий, на экран выводится соответствующее сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="a7275-166">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a7275-167">Примеры</span><span class="sxs-lookup"><span data-stu-id="a7275-167">Examples</span></span>  

 <span data-ttu-id="a7275-168">Следующая команда добавляет все открытые классы, содержащиеся в `myTest.dll`, в `myTargetApp` (существующее приложение COM+) и создает библиотеку типов `myTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="a7275-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="a7275-169">Следующая команда добавляет все открытые классы, содержащиеся в `myTest.dll`, в `myTargetApp` (существующее приложение COM+) и создает библиотеку типов `newTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="a7275-169">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7275-170">См. также</span><span class="sxs-lookup"><span data-stu-id="a7275-170">See also</span></span>

- [<span data-ttu-id="a7275-171">Инструменты</span><span class="sxs-lookup"><span data-stu-id="a7275-171">Tools</span></span>](index.md)
- [<span data-ttu-id="a7275-172">Практическое руководство. Подписание сборки строгим именем</span><span class="sxs-lookup"><span data-stu-id="a7275-172">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="a7275-173">Оболочки командной строки для разработчиков</span><span class="sxs-lookup"><span data-stu-id="a7275-173">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
