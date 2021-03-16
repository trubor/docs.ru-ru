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
ms.openlocfilehash: a989ddf8b14806879917e4078f60486f225b00e3
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259207"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="a5c53-104">Regsvcs.exe (программа установки служб .NET)</span><span class="sxs-lookup"><span data-stu-id="a5c53-104">Regsvcs.exe (.NET Services Installation Tool)</span></span>

<span data-ttu-id="a5c53-105">Программа установки служб .NET выполняет следующие действия.</span><span class="sxs-lookup"><span data-stu-id="a5c53-105">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="a5c53-106">Загружает и регистрирует сборку.</span><span class="sxs-lookup"><span data-stu-id="a5c53-106">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="a5c53-107">Создает, регистрирует и устанавливает библиотеку типов в указанное приложение COM+.</span><span class="sxs-lookup"><span data-stu-id="a5c53-107">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="a5c53-108">Настраивает службы, которые были программно добавлены в создаваемый класс.</span><span class="sxs-lookup"><span data-stu-id="a5c53-108">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="a5c53-109">Чтобы запустить инструмент, используйте [оболочку командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell).</span><span class="sxs-lookup"><span data-stu-id="a5c53-109">To run the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="a5c53-110">В командной строке введите следующее.</span><span class="sxs-lookup"><span data-stu-id="a5c53-110">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c53-111">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a5c53-111">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a><span data-ttu-id="a5c53-112">Параметры</span><span class="sxs-lookup"><span data-stu-id="a5c53-112">Parameters</span></span>  
  
|<span data-ttu-id="a5c53-113">Аргумент</span><span class="sxs-lookup"><span data-stu-id="a5c53-113">Argument</span></span>|<span data-ttu-id="a5c53-114">Описание</span><span class="sxs-lookup"><span data-stu-id="a5c53-114">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a5c53-115">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="a5c53-115">*assemblyFile.dll*</span></span>|<span data-ttu-id="a5c53-116">Исходный файл сборки.</span><span class="sxs-lookup"><span data-stu-id="a5c53-116">The source assembly file.</span></span> <span data-ttu-id="a5c53-117">Сборка должна быть подписана с использованием строгого имени.</span><span class="sxs-lookup"><span data-stu-id="a5c53-117">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="a5c53-118">Дополнительные сведения см. в разделе [Подпись сборки строгим именем](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="a5c53-118">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="a5c53-119">Параметр</span><span class="sxs-lookup"><span data-stu-id="a5c53-119">Option</span></span>|<span data-ttu-id="a5c53-120">Описание:</span><span class="sxs-lookup"><span data-stu-id="a5c53-120">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a5c53-121">**/appdir:** *path*</span><span class="sxs-lookup"><span data-stu-id="a5c53-121">**/appdir:** *path*</span></span>|<span data-ttu-id="a5c53-122">Определяет корневой каталог приложения.</span><span class="sxs-lookup"><span data-stu-id="a5c53-122">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="a5c53-123">**/appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="a5c53-123">**/appname:** *applicationName*</span></span>|<span data-ttu-id="a5c53-124">Задает имя приложения COM+, которое следует найти или создать.</span><span class="sxs-lookup"><span data-stu-id="a5c53-124">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="a5c53-125">**/c**</span><span class="sxs-lookup"><span data-stu-id="a5c53-125">**/c**</span></span>|<span data-ttu-id="a5c53-126">Создает конечное приложение.</span><span class="sxs-lookup"><span data-stu-id="a5c53-126">Creates the target application.</span></span>|  
|<span data-ttu-id="a5c53-127">**/componly**</span><span class="sxs-lookup"><span data-stu-id="a5c53-127">**/componly**</span></span>|<span data-ttu-id="a5c53-128">Выполняет только конфигурирование компонентов, методы и интерфейсы игнорируются.</span><span class="sxs-lookup"><span data-stu-id="a5c53-128">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="a5c53-129">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="a5c53-129">**/exapp**</span></span>|<span data-ttu-id="a5c53-130">Указывает, что программа будет работать с существующим приложением.</span><span class="sxs-lookup"><span data-stu-id="a5c53-130">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="a5c53-131">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="a5c53-131">**/extlb**</span></span>|<span data-ttu-id="a5c53-132">Использует существующую библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="a5c53-132">Uses an existing type library.</span></span>|  
|<span data-ttu-id="a5c53-133">**/fc**</span><span class="sxs-lookup"><span data-stu-id="a5c53-133">**/fc**</span></span>|<span data-ttu-id="a5c53-134">Находит или создает конечное приложение.</span><span class="sxs-lookup"><span data-stu-id="a5c53-134">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="a5c53-135">**/help**</span><span class="sxs-lookup"><span data-stu-id="a5c53-135">**/help**</span></span>|<span data-ttu-id="a5c53-136">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="a5c53-136">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="a5c53-137">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="a5c53-137">**/noreconfig**</span></span>|<span data-ttu-id="a5c53-138">Запрещает изменять конфигурации существующего конечного приложения.</span><span class="sxs-lookup"><span data-stu-id="a5c53-138">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="a5c53-139">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="a5c53-139">**/nologo**</span></span>|<span data-ttu-id="a5c53-140">Отключает отображение эмблемы Майкрософт при запуске.</span><span class="sxs-lookup"><span data-stu-id="a5c53-140">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="a5c53-141">**/parname:** *name*</span><span class="sxs-lookup"><span data-stu-id="a5c53-141">**/parname:** *name*</span></span>|<span data-ttu-id="a5c53-142">Задает имя или идентификатор приложения COM+, которое следует найти или создать.</span><span class="sxs-lookup"><span data-stu-id="a5c53-142">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="a5c53-143">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="a5c53-143">**/reconfig**</span></span>|<span data-ttu-id="a5c53-144">Изменяет конфигурацию существующего конечного приложения.</span><span class="sxs-lookup"><span data-stu-id="a5c53-144">Reconfigures an existing target application.</span></span> <span data-ttu-id="a5c53-145">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a5c53-145">This is the default.</span></span>|  
|<span data-ttu-id="a5c53-146">**/tlb:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="a5c53-146">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="a5c53-147">Задает устанавливаемый файл библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="a5c53-147">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="a5c53-148">**/u**</span><span class="sxs-lookup"><span data-stu-id="a5c53-148">**/u**</span></span>|<span data-ttu-id="a5c53-149">Удаляет конечное приложение.</span><span class="sxs-lookup"><span data-stu-id="a5c53-149">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="a5c53-150">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="a5c53-150">**/quiet**</span></span>|<span data-ttu-id="a5c53-151">Задает тихий режим, логотип и сообщения об успешном завершении операций не отображаются.</span><span class="sxs-lookup"><span data-stu-id="a5c53-151">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="a5c53-152">**/?**</span><span class="sxs-lookup"><span data-stu-id="a5c53-152">**/?**</span></span>|<span data-ttu-id="a5c53-153">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="a5c53-153">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5c53-154">Примечания</span><span class="sxs-lookup"><span data-stu-id="a5c53-154">Remarks</span></span>  

 <span data-ttu-id="a5c53-155">Программе Regsvcs.exe требуется исходный файл сборки, заданный библиотекой *assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="a5c53-155">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="a5c53-156">Эта сборка должна быть подписана с использованием строгого имени.</span><span class="sxs-lookup"><span data-stu-id="a5c53-156">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="a5c53-157">Дополнительные сведения о подписи с использованием строгого имени см. в разделе [Подпись сборки строгим именем](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="a5c53-157">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="a5c53-158">Имена конечного приложения и файла библиотеки типов не являются обязательными.</span><span class="sxs-lookup"><span data-stu-id="a5c53-158">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="a5c53-159">Аргумент *applicationName* может быть создан из исходного файла сборки, и в случае его отсутствия он будет создан программой Regsvcs.exe.</span><span class="sxs-lookup"><span data-stu-id="a5c53-159">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="a5c53-160">Аргумент *typelibraryfile* может задавать имя библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="a5c53-160">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="a5c53-161">Если имя библиотеки типов не указано, программа Regsvcs.exe по умолчанию использует имя сборки.</span><span class="sxs-lookup"><span data-stu-id="a5c53-161">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="a5c53-162">Когда программа Regsvcs.exe регистрирует методы компонента, к ней применяются [требования](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) и [требования ссылки](../misc/link-demands.md) для этих методов.</span><span class="sxs-lookup"><span data-stu-id="a5c53-162">When Regsvcs.exe registers a component's methods, it is subject to the [demands](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="a5c53-163">Поскольку эта программа выполняется в полностью доверенной среде, большинство требований на получение разрешения удовлетворяется.</span><span class="sxs-lookup"><span data-stu-id="a5c53-163">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="a5c53-164">Однако программа Regsvcs.exe не может регистрировать компоненты с помощью методов, защищенных требованием или требованием связи для <xref:System.Security.Permissions.StrongNameIdentityPermission> или <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="a5c53-164">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="a5c53-165">Для работы с программой Regsvcs.exe требуются права администратора на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="a5c53-165">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="a5c53-166">Если программа Regsvcs.exe не может выполнить какие-либо из этих действий, на экран выводится соответствующее сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="a5c53-166">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a5c53-167">Примеры</span><span class="sxs-lookup"><span data-stu-id="a5c53-167">Examples</span></span>  

 <span data-ttu-id="a5c53-168">Следующая команда добавляет все открытые классы, содержащиеся в `myTest.dll`, в `myTargetApp` (существующее приложение COM+) и создает библиотеку типов `myTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="a5c53-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="a5c53-169">Следующая команда добавляет все открытые классы, содержащиеся в `myTest.dll`, в `myTargetApp` (существующее приложение COM+) и создает библиотеку типов `newTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="a5c53-169">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5c53-170">См. также</span><span class="sxs-lookup"><span data-stu-id="a5c53-170">See also</span></span>

- [<span data-ttu-id="a5c53-171">Инструменты</span><span class="sxs-lookup"><span data-stu-id="a5c53-171">Tools</span></span>](index.md)
- [<span data-ttu-id="a5c53-172">Практическое руководство. Подписание сборки строгим именем</span><span class="sxs-lookup"><span data-stu-id="a5c53-172">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="a5c53-173">Оболочки командной строки для разработчиков</span><span class="sxs-lookup"><span data-stu-id="a5c53-173">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
