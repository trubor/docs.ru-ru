---
title: Ilasm.exe (ассемблер IL)
description: Начните работу с Ilasm.exe, ассемблером IL. Это средство создает переносимый исполняемый файл (PE) из сборки на промежуточном языке (IL).
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
ms.openlocfilehash: be654c27af2b3e0e281c734069f2de469b901446
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258043"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="25841-104">Ilasm.exe (ассемблер IL)</span><span class="sxs-lookup"><span data-stu-id="25841-104">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="25841-105">Ассемблер IL создает переносимый исполняемый (PE) файл из сборки на промежуточном языке (IL).</span><span class="sxs-lookup"><span data-stu-id="25841-105">The IL Assembler generates a portable executable (PE) file from intermediate language (IL) assembly.</span></span> <span data-ttu-id="25841-106">(Дополнительные сведения о промежуточном языке см. в разделе [Процесс управляемого выполнения](../../standard/managed-execution-process.md).) Можно запустить полученный исполняемый файл, содержащий код на промежуточном языке и необходимые метаданные, чтобы проверить, выполняется ли код IL так, как ожидалось.</span><span class="sxs-lookup"><span data-stu-id="25841-106">(For more information on IL, see [Managed Execution Process](../../standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="25841-107">Эта программа автоматически устанавливается вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="25841-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="25841-108">Чтобы запустить инструмент, используйте [оболочку командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell).</span><span class="sxs-lookup"><span data-stu-id="25841-108">To run the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>

<span data-ttu-id="25841-109">В командной строке введите следующее.</span><span class="sxs-lookup"><span data-stu-id="25841-109">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="25841-110">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="25841-110">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="25841-111">Параметры</span><span class="sxs-lookup"><span data-stu-id="25841-111">Parameters</span></span>

| <span data-ttu-id="25841-112">Аргумент</span><span class="sxs-lookup"><span data-stu-id="25841-112">Argument</span></span> | <span data-ttu-id="25841-113">Описание</span><span class="sxs-lookup"><span data-stu-id="25841-113">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="25841-114">Имя исходного файла с расширением IL.</span><span class="sxs-lookup"><span data-stu-id="25841-114">The name of the .il source file.</span></span> <span data-ttu-id="25841-115">В этом файле содержатся директивы объявления метаданных и символические инструкции IL.</span><span class="sxs-lookup"><span data-stu-id="25841-115">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="25841-116">Программа *Ilasm.exe* может создать один PE-файл из нескольких исходных файлов, для чего следует указать несколько аргументов исходных файлов.</span><span class="sxs-lookup"><span data-stu-id="25841-116">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="25841-117">**Примечание.** Убедитесь, что последняя строка кода в исходном IL-файле имеет либо конечный пробел, либо символ конца строки.</span><span class="sxs-lookup"><span data-stu-id="25841-117">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="25841-118">Параметр</span><span class="sxs-lookup"><span data-stu-id="25841-118">Option</span></span> | <span data-ttu-id="25841-119">Описание:</span><span class="sxs-lookup"><span data-stu-id="25841-119">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="25841-120">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="25841-120">**/32bitpreferred**</span></span>|<span data-ttu-id="25841-121">Создает предпочтительно 32-разрядный образ (PE32).</span><span class="sxs-lookup"><span data-stu-id="25841-121">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="25841-122">**/alignment:** `integer`</span><span class="sxs-lookup"><span data-stu-id="25841-122">**/alignment:** `integer`</span></span>|<span data-ttu-id="25841-123">Параметр `integer` задает значение "FileAlignment" в необязательном заголовке NT.</span><span class="sxs-lookup"><span data-stu-id="25841-123">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="25841-124">Если в файле указана IL-директива ALIGNMENT, этот параметр ее переопределяет.</span><span class="sxs-lookup"><span data-stu-id="25841-124">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="25841-125">**/appcontainer**</span><span class="sxs-lookup"><span data-stu-id="25841-125">**/appcontainer**</span></span>|<span data-ttu-id="25841-126">Создает файл *DLL* или *EXE*, выполняющийся в контейнере приложения Windows, в качестве выходных данных.</span><span class="sxs-lookup"><span data-stu-id="25841-126">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="25841-127">**/arm**</span><span class="sxs-lookup"><span data-stu-id="25841-127">**/arm**</span></span>|<span data-ttu-id="25841-128">Задает Advanced RISC Machine (ARM) как целевой процессор.</span><span class="sxs-lookup"><span data-stu-id="25841-128">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="25841-129">Если разрядность образа не задана, в качестве значения по умолчанию используется **/32bitpreferred**.</span><span class="sxs-lookup"><span data-stu-id="25841-129">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="25841-130">**/base:** `integer`</span><span class="sxs-lookup"><span data-stu-id="25841-130">**/base:** `integer`</span></span>|<span data-ttu-id="25841-131">Параметр `integer` задает значение "ImageBase" в необязательном заголовке NT.</span><span class="sxs-lookup"><span data-stu-id="25841-131">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="25841-132">Если в файле указана IL-директива IMAGEBASE, этот параметр ее переопределяет.</span><span class="sxs-lookup"><span data-stu-id="25841-132">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="25841-133">**/clock**</span><span class="sxs-lookup"><span data-stu-id="25841-133">**/clock**</span></span>|<span data-ttu-id="25841-134">Измеряет и выводит следующие значения времени компиляции указанного исходного IL-файла в миллисекундах.</span><span class="sxs-lookup"><span data-stu-id="25841-134">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="25841-135">**Total Run**: общее время, затраченное на перечисленные ниже операции.</span><span class="sxs-lookup"><span data-stu-id="25841-135">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="25841-136">**Startup**: загрузка и открытие файла.</span><span class="sxs-lookup"><span data-stu-id="25841-136">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="25841-137">**Emitting MD**: порождение метаданных.</span><span class="sxs-lookup"><span data-stu-id="25841-137">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="25841-138">**Ref to Def Resolution**: разрешение ссылок на определения в файле.</span><span class="sxs-lookup"><span data-stu-id="25841-138">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="25841-139">**CEE File Generation**: создание образа файла в памяти.</span><span class="sxs-lookup"><span data-stu-id="25841-139">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="25841-140">**PE File Writing**: запись образа в PE-файл.</span><span class="sxs-lookup"><span data-stu-id="25841-140">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="25841-141">**/debug**[:**IMPL**&#124;**OPT**]</span><span class="sxs-lookup"><span data-stu-id="25841-141">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="25841-142">Включает отладочные сведения (имена локальных переменных и аргументов, номера строк).</span><span class="sxs-lookup"><span data-stu-id="25841-142">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="25841-143">Создает PDB-файл.</span><span class="sxs-lookup"><span data-stu-id="25841-143">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="25841-144">**/debug** без дополнительных значений отключает JIT-оптимизацию и использует точки последовательности из PDB-файла.</span><span class="sxs-lookup"><span data-stu-id="25841-144">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="25841-145">**IMPL** отключает JIT-оптимизацию и использует неявные точки последовательности.</span><span class="sxs-lookup"><span data-stu-id="25841-145">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="25841-146">**OPT** включает JIT-оптимизацию и использует неявные точки последовательности.</span><span class="sxs-lookup"><span data-stu-id="25841-146">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="25841-147">**/dll**</span><span class="sxs-lookup"><span data-stu-id="25841-147">**/dll**</span></span>|<span data-ttu-id="25841-148">Выходным файлом будет библиотека *DLL*.</span><span class="sxs-lookup"><span data-stu-id="25841-148">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="25841-149">**/enc:** `file`</span><span class="sxs-lookup"><span data-stu-id="25841-149">**/enc:** `file`</span></span>|<span data-ttu-id="25841-150">Создает разности "Изменить и продолжить" из указанного файла источника.</span><span class="sxs-lookup"><span data-stu-id="25841-150">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="25841-151">Данный аргумент предназначен только для использования в учебных заведениях и не поддерживается для коммерческого использования.</span><span class="sxs-lookup"><span data-stu-id="25841-151">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="25841-152">**/exe**</span><span class="sxs-lookup"><span data-stu-id="25841-152">**/exe**</span></span>|<span data-ttu-id="25841-153">Выходным файлом будет исполняемый файл.</span><span class="sxs-lookup"><span data-stu-id="25841-153">Produces an executable file as output.</span></span> <span data-ttu-id="25841-154">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="25841-154">This is the default.</span></span>|
|<span data-ttu-id="25841-155">**/flags:** `integer`</span><span class="sxs-lookup"><span data-stu-id="25841-155">**/flags:** `integer`</span></span>|<span data-ttu-id="25841-156">Параметр `integer` задает значение "ImageFlags" в заголовке среды CLR.</span><span class="sxs-lookup"><span data-stu-id="25841-156">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="25841-157">Если в файле указана IL-директива CORFLAGS, этот параметр ее переопределяет.</span><span class="sxs-lookup"><span data-stu-id="25841-157">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="25841-158">Список допустимых значений параметра *integer* см. в CorHdr.h, COMIMAGE_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="25841-158">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="25841-159">**/fold**</span><span class="sxs-lookup"><span data-stu-id="25841-159">**/fold**</span></span>|<span data-ttu-id="25841-160">Свертывает идентичные тела методов в один.</span><span class="sxs-lookup"><span data-stu-id="25841-160">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="25841-161">/**highentropyva**</span><span class="sxs-lookup"><span data-stu-id="25841-161">/**highentropyva**</span></span>|<span data-ttu-id="25841-162">На выходе создает исполняемый файл, который поддерживает технологию Address Space Layout Randomization (ASLR) с высокой энтропией.</span><span class="sxs-lookup"><span data-stu-id="25841-162">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="25841-163">(Используется по умолчанию для **/appcontainer**.)</span><span class="sxs-lookup"><span data-stu-id="25841-163">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="25841-164">**/include:** `includePath`</span><span class="sxs-lookup"><span data-stu-id="25841-164">**/include:** `includePath`</span></span>|<span data-ttu-id="25841-165">Задает путь для поиска файлов, включенных с помощью команды `#include`.</span><span class="sxs-lookup"><span data-stu-id="25841-165">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="25841-166">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="25841-166">**/itanium**</span></span>|<span data-ttu-id="25841-167">Задает Intel Itanium в качестве целевого процессора.</span><span class="sxs-lookup"><span data-stu-id="25841-167">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="25841-168">Если разрядность образа не задана, в качестве значения по умолчанию используется **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="25841-168">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="25841-169">**/key:** `keyFile`</span><span class="sxs-lookup"><span data-stu-id="25841-169">**/key:** `keyFile`</span></span>|<span data-ttu-id="25841-170">Компилирует файл `filename` со строгой подписью с помощью закрытого ключа в `keyFile`.</span><span class="sxs-lookup"><span data-stu-id="25841-170">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="25841-171">**/key:**  @`keySource`</span><span class="sxs-lookup"><span data-stu-id="25841-171">**/key:** @`keySource`</span></span>|<span data-ttu-id="25841-172">Компилирует файл `filename` со строгой подписью с помощью закрытого ключа, созданного в `keySource`.</span><span class="sxs-lookup"><span data-stu-id="25841-172">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="25841-173">**/listing**</span><span class="sxs-lookup"><span data-stu-id="25841-173">**/listing**</span></span>|<span data-ttu-id="25841-174">Создает файл списка со стандартными выходными данными.</span><span class="sxs-lookup"><span data-stu-id="25841-174">Produces a listing file on the standard output.</span></span> <span data-ttu-id="25841-175">Если этот параметр не задан, файл списка не создается.</span><span class="sxs-lookup"><span data-stu-id="25841-175">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="25841-176">Этот параметр не поддерживается в .NET Framework 2.0 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="25841-176">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="25841-177">**/mdv:** `versionString`</span><span class="sxs-lookup"><span data-stu-id="25841-177">**/mdv:** `versionString`</span></span>|<span data-ttu-id="25841-178">Задает строку версии метаданных.</span><span class="sxs-lookup"><span data-stu-id="25841-178">Sets the metadata version string.</span></span>|
|<span data-ttu-id="25841-179">**/msv:** `major`.`minor`</span><span class="sxs-lookup"><span data-stu-id="25841-179">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="25841-180">Задает версию потока метаданных, где `major` и `minor` являются целыми числами.</span><span class="sxs-lookup"><span data-stu-id="25841-180">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="25841-181">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="25841-181">**/noautoinherit**</span></span>|<span data-ttu-id="25841-182">Отключает наследование по умолчанию из класса <xref:System.Object> , если базовый класс не указан.</span><span class="sxs-lookup"><span data-stu-id="25841-182">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="25841-183">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="25841-183">**/nocorstub**</span></span>|<span data-ttu-id="25841-184">Запрещает создание заглушки CORExeMain.</span><span class="sxs-lookup"><span data-stu-id="25841-184">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="25841-185">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="25841-185">**/nologo**</span></span>|<span data-ttu-id="25841-186">Отключает отображение эмблемы Майкрософт при запуске.</span><span class="sxs-lookup"><span data-stu-id="25841-186">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="25841-187">**/output:** `file.ext`</span><span class="sxs-lookup"><span data-stu-id="25841-187">**/output:** `file.ext`</span></span>|<span data-ttu-id="25841-188">Задает имя и расширение выходного файла.</span><span class="sxs-lookup"><span data-stu-id="25841-188">Specifies the output file name and extension.</span></span> <span data-ttu-id="25841-189">По умолчанию имя выходного файла совпадает с именем первого исходного файла.</span><span class="sxs-lookup"><span data-stu-id="25841-189">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="25841-190">Расширение по умолчанию — *EXE*.</span><span class="sxs-lookup"><span data-stu-id="25841-190">The default extension is *.exe*.</span></span> <span data-ttu-id="25841-191">Если задан параметр **/dll** , по умолчанию используется расширение *DLL*.</span><span class="sxs-lookup"><span data-stu-id="25841-191">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="25841-192">**Примечание.** Задание параметра **/output**:myfile.dll не равносильно указанию параметра **/dll**.</span><span class="sxs-lookup"><span data-stu-id="25841-192">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="25841-193">Если параметр **/dll** не задан, будет создан исполняемый файл с именем *myfile.dll*.</span><span class="sxs-lookup"><span data-stu-id="25841-193">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="25841-194">**/optimize**</span><span class="sxs-lookup"><span data-stu-id="25841-194">**/optimize**</span></span>|<span data-ttu-id="25841-195">Оптимизирует длинные инструкции в короткие.</span><span class="sxs-lookup"><span data-stu-id="25841-195">Optimizes long instructions to short.</span></span> <span data-ttu-id="25841-196">Например, `br` в `br.s`.</span><span class="sxs-lookup"><span data-stu-id="25841-196">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="25841-197">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="25841-197">**/pe64**</span></span>|<span data-ttu-id="25841-198">Создает 64-разрядный образ (PE32+).</span><span class="sxs-lookup"><span data-stu-id="25841-198">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="25841-199">Если целевой процессор не задан, по умолчанию используется `/itanium`.</span><span class="sxs-lookup"><span data-stu-id="25841-199">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="25841-200">**/pdb**</span><span class="sxs-lookup"><span data-stu-id="25841-200">**/pdb**</span></span>|<span data-ttu-id="25841-201">Создает PDB-файл, отслеживание отладочной информации не включается.</span><span class="sxs-lookup"><span data-stu-id="25841-201">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="25841-202">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="25841-202">**/quiet**</span></span>|<span data-ttu-id="25841-203">Задает тихий режим и отключает вывод сведений о ходе сборки.</span><span class="sxs-lookup"><span data-stu-id="25841-203">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="25841-204">**/resource:** `file.res`</span><span class="sxs-lookup"><span data-stu-id="25841-204">**/resource:** `file.res`</span></span>|<span data-ttu-id="25841-205">Включает указанный файл ресурсов формате \*RES в выходной *EXE*-файл или *DLL*-файл.</span><span class="sxs-lookup"><span data-stu-id="25841-205">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="25841-206">С параметром **/resource** может быть указан только один RES-файл.</span><span class="sxs-lookup"><span data-stu-id="25841-206">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="25841-207">**/ssver:** `int`.`int`</span><span class="sxs-lookup"><span data-stu-id="25841-207">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="25841-208">Задает номер версии подсистемы в необязательном заголовке NT.</span><span class="sxs-lookup"><span data-stu-id="25841-208">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="25841-209">Для **/appcontainer** и **/arm** минимальным номером версии является 6.02.</span><span class="sxs-lookup"><span data-stu-id="25841-209">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="25841-210">**/stack:** `stackSize`</span><span class="sxs-lookup"><span data-stu-id="25841-210">**/stack:** `stackSize`</span></span>|<span data-ttu-id="25841-211">Задает `stackSize`в качестве значения "SizeOfStackReserve" в необязательном заголовке NT.</span><span class="sxs-lookup"><span data-stu-id="25841-211">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="25841-212">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="25841-212">**/stripreloc**</span></span>|<span data-ttu-id="25841-213">Указывает, что перемещения базового адреса не требуются.</span><span class="sxs-lookup"><span data-stu-id="25841-213">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="25841-214">**/subsystem:** `integer`</span><span class="sxs-lookup"><span data-stu-id="25841-214">**/subsystem:** `integer`</span></span>|<span data-ttu-id="25841-215">Параметр `integer` задает значение "subsystem" в необязательном заголовке NT.</span><span class="sxs-lookup"><span data-stu-id="25841-215">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="25841-216">Если в файле указана IL-директива SUBSYSTEM, этот параметр ее переопределяет.</span><span class="sxs-lookup"><span data-stu-id="25841-216">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="25841-217">Список допустимых значений параметра `integer` см. в winnt.h, IMAGE_SUBSYSTEM.</span><span class="sxs-lookup"><span data-stu-id="25841-217">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="25841-218">**/x64**</span><span class="sxs-lookup"><span data-stu-id="25841-218">**/x64**</span></span>|<span data-ttu-id="25841-219">Задает 64-разрядный процессор AMD в качестве целевого процессора.</span><span class="sxs-lookup"><span data-stu-id="25841-219">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="25841-220">Если разрядность образа не задана, в качестве значения по умолчанию используется **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="25841-220">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="25841-221">**/?**</span><span class="sxs-lookup"><span data-stu-id="25841-221">**/?**</span></span>|<span data-ttu-id="25841-222">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="25841-222">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="25841-223">Параметры программы *Ilasm.exe* не учитывают регистр и распознаются по первым трем буквам.</span><span class="sxs-lookup"><span data-stu-id="25841-223">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="25841-224">Например, **/lis** равнозначно **/listing** , а **/res:** myresfile.res равнозначно **/resource:** myresfile.res. Разделителем параметра и его аргумента может служить двоеточие (:) или знак равенства (=).</span><span class="sxs-lookup"><span data-stu-id="25841-224">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="25841-225">Например, **/output:** *file.ext* эквивалентно **/output**=*file.ext*.</span><span class="sxs-lookup"><span data-stu-id="25841-225">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="25841-226">Примечания</span><span class="sxs-lookup"><span data-stu-id="25841-226">Remarks</span></span>

<span data-ttu-id="25841-227">Ассемблер IL весьма полезен разработчикам ПО для создания и внедрения генераторов IL.</span><span class="sxs-lookup"><span data-stu-id="25841-227">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="25841-228">Используя программу *Ilasm.exe*, компилятор и другие средства, разработчики могут сосредоточить свои усилия на работе с IL и создании метаданных, а не на преобразовании IL в формат PE-файла.</span><span class="sxs-lookup"><span data-stu-id="25841-228">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="25841-229">Аналогично таким компиляторам для среды выполнения, как C# и Visual Basic, программа *Ilasm.exe* не создает промежуточные объектные файлы и при создании PE-файла позволяет пропустить этап связывания.</span><span class="sxs-lookup"><span data-stu-id="25841-229">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="25841-230">Ассемблер IL может выразить все существующие метаданные и возможности IL языков программирования, предназначенные для взаимодействия со средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="25841-230">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="25841-231">С его помощью можно адекватно выразить на ассемблере IL и скомпилировать с помощью программы *Ilasm.exe* управляемый код, написанный на любом из этих языков.</span><span class="sxs-lookup"><span data-stu-id="25841-231">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="25841-232">Компиляция может завершиться ошибкой, если последняя строка кода в исходном IL-файле не имеет конечного пробела или символа конца строки.</span><span class="sxs-lookup"><span data-stu-id="25841-232">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="25841-233">Программа *Ilasm.exe* может применяться совместно с сопутствующей программой — [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="25841-233">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="25841-234">Программа *Ildasm.exe* анализирует PE-файл, содержащий IL-код, и создает текстовый файл, подходящий для обработки программой *Ildasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="25841-234">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="25841-235">Это полезно, к примеру, при компиляции кода на языке программирования, не поддерживающем все атрибуты метаданных среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="25841-235">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="25841-236">После компиляции кода и обработки результатов с помощью программы *Ildasm.exe* можно вручную добавить недостающие атрибуты в полученный текстовый IL-файл.</span><span class="sxs-lookup"><span data-stu-id="25841-236">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="25841-237">Чтобы создать итоговый исполняемый файл, этот текстовый файл следует обработать с помощью программы *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="25841-237">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="25841-238">Эту технологию можно также использовать для создания одного PE-файла из нескольких PE-файлов, созданных различными компиляторами.</span><span class="sxs-lookup"><span data-stu-id="25841-238">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="25841-239">На данный момент такая технология не применяется к PE-файлам, содержащим встроенный машинный код (например, к PE-файлам, созданным компилятором Microsoft Visual C++).</span><span class="sxs-lookup"><span data-stu-id="25841-239">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="25841-240">Чтобы обеспечить наибольшую точность совместной работы программ *Ildasm.exe* и *Ilasm.exe*, по умолчанию ассемблер не заменяет короткие коды на длинные, которые могут быть в источниках IL (или созданы другим компилятором).</span><span class="sxs-lookup"><span data-stu-id="25841-240">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="25841-241">С помощью параметра **/optimize** можно заменить короткие коды там, где это возможно.</span><span class="sxs-lookup"><span data-stu-id="25841-241">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="25841-242">Программа *Ildasm.exe* работает только с файлами, расположенными на жестком диске.</span><span class="sxs-lookup"><span data-stu-id="25841-242">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="25841-243">Программа не обрабатывает файлы, установленные в глобальном кэше сборок.</span><span class="sxs-lookup"><span data-stu-id="25841-243">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="25841-244">Дополнительные сведения о грамматике IL см. в файле asmparse.grammar в составе Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="25841-244">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="version-information"></a><span data-ttu-id="25841-245">Сведения о версии</span><span class="sxs-lookup"><span data-stu-id="25841-245">Version Information</span></span>

<span data-ttu-id="25841-246">Начиная с .NET Framework 4.5 к реализации интерфейса можно добавить свой атрибут с помощью кода, похожего на следующий:</span><span class="sxs-lookup"><span data-stu-id="25841-246">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

```il
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

<span data-ttu-id="25841-247">Начиная с .NET Framework 4.5 можно указать произвольный большой двоичный объект (BLOB) маршала с помощью необработанного двоичного представления, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="25841-247">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="25841-248">Дополнительные сведения о грамматике IL см. в файле asmparse.grammar в составе Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="25841-248">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="25841-249">Примеры</span><span class="sxs-lookup"><span data-stu-id="25841-249">Examples</span></span>

<span data-ttu-id="25841-250">Следующая команда выполняет сборку IL-файла *myTestFile.il* и создает исполняемый файл *myTestFile.exe*.</span><span class="sxs-lookup"><span data-stu-id="25841-250">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="25841-251">Следующая команда выполняет сборку IL-файла *myTestFile.il* и создает *DLL*-файл *myTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="25841-251">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="25841-252">Следующая команда выполняет сборку IL-файла *myTestFile.il* и создает *DLL*-файл *myNewTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="25841-252">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="25841-253">В приведенном ниже примере кода показано очень простое приложение, выводящее сообщение "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="25841-253">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="25841-254">в консоль.</span><span class="sxs-lookup"><span data-stu-id="25841-254">to the console.</span></span> <span data-ttu-id="25841-255">Можно скомпилировать этот код и создать IL-файл с помощью программы [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="25841-255">You can compile this code and then use the [*Ildasm.exe*](ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

<span data-ttu-id="25841-256">Следующий пример кода IL соответствует предыдущему примеру кода на C#.</span><span class="sxs-lookup"><span data-stu-id="25841-256">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="25841-257">Можно скомпилировать этот код в сборку с помощью ассемблера IL.</span><span class="sxs-lookup"><span data-stu-id="25841-257">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="25841-258">В обоих примерах кода (на IL и C#) на консоли отображается</span><span class="sxs-lookup"><span data-stu-id="25841-258">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="25841-259">в консоль.</span><span class="sxs-lookup"><span data-stu-id="25841-259">to the console.</span></span>

```il
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a><span data-ttu-id="25841-260">См. также</span><span class="sxs-lookup"><span data-stu-id="25841-260">See also</span></span>

- [<span data-ttu-id="25841-261">Инструменты</span><span class="sxs-lookup"><span data-stu-id="25841-261">Tools</span></span>](index.md)
- [<span data-ttu-id="25841-262">*Ildasm.exe* (дизассемблер IL)</span><span class="sxs-lookup"><span data-stu-id="25841-262">*Ildasm.exe* (IL Disassembler)</span></span>](ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="25841-263">Процесс управляемого выполнения</span><span class="sxs-lookup"><span data-stu-id="25841-263">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="25841-264">Оболочки командной строки для разработчиков</span><span class="sxs-lookup"><span data-stu-id="25841-264">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
