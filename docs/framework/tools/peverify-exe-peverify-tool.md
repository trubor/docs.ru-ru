---
title: Peverify.exe (средство PEVerify)
description: Использование средства Peverify.exe (проверка переносимых исполняемых файлов), чтобы определить, соответствуют ли код и метаданные на промежуточном языке Microsoft (MSIL) стандартам безопасности типов в .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
ms.openlocfilehash: b51b01e639719df7ecfde53819e3137813f7c46f
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102259253"
---
# <a name="peverifyexe-peverify-tool"></a><span data-ttu-id="9e8e0-103">Peverify.exe (средство PEVerify)</span><span class="sxs-lookup"><span data-stu-id="9e8e0-103">Peverify.exe (PEVerify tool)</span></span>

<span data-ttu-id="9e8e0-104">Средство PEVerify помогает разработчикам, создающим код на языке MSIL, — авторам компиляторов, обработчиков скриптов и т. д. — определить, соответствует ли этот код и связанные с ним метаданные требованиям безопасности типов.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-104">The PEVerify tool helps developers who generate Microsoft intermediate language (MSIL) (such as compiler writers and script engine developers) to determine whether their MSIL code and associated metadata meet type safety requirements.</span></span> <span data-ttu-id="9e8e0-105">Некоторые компиляторы создают проверяемый типобезопасный код только в том случае, если разработчик не применяет определенные языковые конструкции.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-105">Some compilers generate verifiably type-safe code only if you avoid using certain language constructs.</span></span> <span data-ttu-id="9e8e0-106">При работе с таким компилятором иногда требуется проверить, сохранена ли в коде безопасность типов.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-106">If you're using such a compiler, you may want to verify that you have not compromised the type safety of your code.</span></span> <span data-ttu-id="9e8e0-107">В этом случае для проверки кода MSIL и метаданных в файлах можно использовать инструмент PEVerify.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-107">You can run the PEVerify tool on your files to check the MSIL and metadata.</span></span>  
  
 <span data-ttu-id="9e8e0-108">Эта программа автоматически устанавливается вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="9e8e0-109">Чтобы запустить инструмент, используйте [оболочку командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell).</span><span class="sxs-lookup"><span data-stu-id="9e8e0-109">To run the tool, use a [command-line shell for developers](/visualstudio/ide/reference/command-prompt-powershell).</span></span>
  
## <a name="syntax"></a><span data-ttu-id="9e8e0-110">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9e8e0-110">Syntax</span></span>  
  
```console  
peverify filename [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e8e0-111">Параметры</span><span class="sxs-lookup"><span data-stu-id="9e8e0-111">Parameters</span></span>  
  
|<span data-ttu-id="9e8e0-112">Аргумент</span><span class="sxs-lookup"><span data-stu-id="9e8e0-112">Argument</span></span>|<span data-ttu-id="9e8e0-113">Описание</span><span class="sxs-lookup"><span data-stu-id="9e8e0-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="9e8e0-114">*filename*</span><span class="sxs-lookup"><span data-stu-id="9e8e0-114">*filename*</span></span>|<span data-ttu-id="9e8e0-115">Переносимый исполняемый файл (PE-файл), который требуется проверить на корректность CIL и метаданных.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-115">The portable executable (PE) file for which to check the MSIL and metadata.</span></span>|  
  
|<span data-ttu-id="9e8e0-116">Параметр</span><span class="sxs-lookup"><span data-stu-id="9e8e0-116">Option</span></span>|<span data-ttu-id="9e8e0-117">Описание</span><span class="sxs-lookup"><span data-stu-id="9e8e0-117">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="9e8e0-118">**/break=** *maxErrorCount*</span><span class="sxs-lookup"><span data-stu-id="9e8e0-118">**/break=** *maxErrorCount*</span></span>|<span data-ttu-id="9e8e0-119">Прекращает проверку, если число ошибок в файле достигло значения параметра *maxErrorCount*.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-119">Aborts verification after *maxErrorCount* errors.</span></span><br /><br /> <span data-ttu-id="9e8e0-120">Этот параметр не поддерживается в .NET Framework 2.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-120">This parameter is not supported in .NET Framework version 2.0 or later.</span></span>|  
|<span data-ttu-id="9e8e0-121">**/clock**</span><span class="sxs-lookup"><span data-stu-id="9e8e0-121">**/clock**</span></span>|<span data-ttu-id="9e8e0-122">Измеряет и выводит значения времени следующих проверок (в миллисекундах):</span><span class="sxs-lookup"><span data-stu-id="9e8e0-122">Measures and reports the following verification times in milliseconds:</span></span><br /><br /> <span data-ttu-id="9e8e0-123">**MD Val. cycle**</span><span class="sxs-lookup"><span data-stu-id="9e8e0-123">**MD Val. cycle**</span></span><br /> <span data-ttu-id="9e8e0-124">Цикл проверки метаданных</span><span class="sxs-lookup"><span data-stu-id="9e8e0-124">Metadata validation cycle</span></span><br /><br /> <span data-ttu-id="9e8e0-125">**MD Val. pure**</span><span class="sxs-lookup"><span data-stu-id="9e8e0-125">**MD Val. pure**</span></span><br /> <span data-ttu-id="9e8e0-126">Чистое время проверки метаданных</span><span class="sxs-lookup"><span data-stu-id="9e8e0-126">Metadata validation pure</span></span><br /><br /> <span data-ttu-id="9e8e0-127">**IL Ver. cycle**</span><span class="sxs-lookup"><span data-stu-id="9e8e0-127">**IL Ver. cycle**</span></span><br /> <span data-ttu-id="9e8e0-128">Цикл проверки языка CIL</span><span class="sxs-lookup"><span data-stu-id="9e8e0-128">Microsoft intermediate language (MSIL) verification cycle</span></span><br /><br /> <span data-ttu-id="9e8e0-129">**IL Ver pure**</span><span class="sxs-lookup"><span data-stu-id="9e8e0-129">**IL Ver pure**</span></span><br /> <span data-ttu-id="9e8e0-130">Чистое время проверки языка CIL</span><span class="sxs-lookup"><span data-stu-id="9e8e0-130">MSIL verification pure</span></span><br /><br /> <span data-ttu-id="9e8e0-131">Значения **MD Val. cycle** и **IL Ver. cycle** включают время, затраченное на необходимые процедуры запуска и завершения проверки.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-131">The **MD Val. cycle** and **IL Ver. cycle** times include the time required to perform necessary startup and shutdown procedures.</span></span> <span data-ttu-id="9e8e0-132">Значения **MD Val. pure** и **IL Ver pure** отражают время, требуемое только для проверки.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-132">The **MD Val. pure** and **IL Ver pure** times reflect the time required to perform the validation or verification only.</span></span>|  
|<span data-ttu-id="9e8e0-133">**/help**</span><span class="sxs-lookup"><span data-stu-id="9e8e0-133">**/help**</span></span>|<span data-ttu-id="9e8e0-134">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-134">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="9e8e0-135">**/hresult**</span><span class="sxs-lookup"><span data-stu-id="9e8e0-135">**/hresult**</span></span>|<span data-ttu-id="9e8e0-136">Отображает коды ошибок в шестнадцатеричном формате.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-136">Displays error codes in hexadecimal format.</span></span>|  
|<span data-ttu-id="9e8e0-137">**/ignore=** *hex.code* [, *hex.code*]</span><span class="sxs-lookup"><span data-stu-id="9e8e0-137">**/ignore=** *hex.code* [, *hex.code*]</span></span>|<span data-ttu-id="9e8e0-138">Игнорирует ошибки с заданными кодами.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-138">Ignores the specified error codes.</span></span>|  
|<span data-ttu-id="9e8e0-139">**/ignore=@** *responseFile*</span><span class="sxs-lookup"><span data-stu-id="9e8e0-139">**/ignore=@** *responseFile*</span></span>|<span data-ttu-id="9e8e0-140">Игнорирует ошибки с кодами, перечисленными в указанном файле ответов.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-140">Ignores the error codes listed in the specified response file.</span></span>|  
|<span data-ttu-id="9e8e0-141">**/il**</span><span class="sxs-lookup"><span data-stu-id="9e8e0-141">**/il**</span></span>|<span data-ttu-id="9e8e0-142">Проверяет безопасность типов CIL для методов, реализованных в сборке, указанной в параметре *filename*.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-142">Performs MSIL type safety verification checks for methods implemented in the assembly specified by *filename*.</span></span> <span data-ttu-id="9e8e0-143">Если не задан параметр **/quiet**, средство выводит подробное описание всех обнаруженных проблем.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-143">The tool returns detailed descriptions for each problem found unless you specify the **/quiet** option.</span></span>|  
|<span data-ttu-id="9e8e0-144">**/md**</span><span class="sxs-lookup"><span data-stu-id="9e8e0-144">**/md**</span></span>|<span data-ttu-id="9e8e0-145">Проверяет метаданные в сборке, указанной в параметре *filename*.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-145">Performs metadata validation checks on the assembly specified by *filename*.</span></span> <span data-ttu-id="9e8e0-146">Средство проверяет всю структуру метаданных в файле и выводит описание всех обнаруженных проблем.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-146">This option walks the full metadata structure within the file and reports all validation problems encountered.</span></span>|  
|<span data-ttu-id="9e8e0-147">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="9e8e0-147">**/nologo**</span></span>|<span data-ttu-id="9e8e0-148">Отключает отображение сведений о версии продукта и авторских правах.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-148">Suppresses the display of product version and copyright information.</span></span>|  
|<span data-ttu-id="9e8e0-149">**/nosymbols**</span><span class="sxs-lookup"><span data-stu-id="9e8e0-149">**/nosymbols**</span></span>|<span data-ttu-id="9e8e0-150">В платформе .NET Framework версии 2.0 отключает номера строк для обеспечения обратной совместимости.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-150">In the .NET Framework version 2.0, suppresses line numbers for backward compatibility.</span></span>|  
|<span data-ttu-id="9e8e0-151">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="9e8e0-151">**/quiet**</span></span>|<span data-ttu-id="9e8e0-152">Задает тихий режим. Отключает вывод сообщений об обнаруженных проблемах.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-152">Specifies quiet mode; suppresses output of the verification problem reports.</span></span> <span data-ttu-id="9e8e0-153">Средство Peverify.exe все равно уведомляет, соблюдается ли безопасность типов в файле, однако не сообщает об обнаруженных проблемах.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-153">Peverify.exe still reports whether the file is type safe, but does not report information on problems preventing type safety verification.</span></span>|  
|`/transparent`|<span data-ttu-id="9e8e0-154">Ограничивает проверку только прозрачными методами.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-154">Verify only the transparent methods.</span></span>|  
|<span data-ttu-id="9e8e0-155">**/unique**</span><span class="sxs-lookup"><span data-stu-id="9e8e0-155">**/unique**</span></span>|<span data-ttu-id="9e8e0-156">Игнорирует повторяющиеся коды ошибок.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-156">Ignores repeating error codes.</span></span>|  
|<span data-ttu-id="9e8e0-157">**/verbose**</span><span class="sxs-lookup"><span data-stu-id="9e8e0-157">**/verbose**</span></span>|<span data-ttu-id="9e8e0-158">В платформе .NET Framework версии 2.0 отображает дополнительные сведения в сообщениях проверки CIL.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-158">In the .NET Framework version 2.0, displays additional information in MSIL verification messages.</span></span>|  
|<span data-ttu-id="9e8e0-159">**/?**</span><span class="sxs-lookup"><span data-stu-id="9e8e0-159">**/?**</span></span>|<span data-ttu-id="9e8e0-160">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-160">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e8e0-161">Примечания</span><span class="sxs-lookup"><span data-stu-id="9e8e0-161">Remarks</span></span>  

 <span data-ttu-id="9e8e0-162">В среде CLR реализация механизмов безопасности и изоляции основана на типобезопасном выполнении кода приложения.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-162">The common language runtime relies on the type-safe execution of application code to help enforce security and isolation mechanisms.</span></span> <span data-ttu-id="9e8e0-163">Обычно код, для которого невозможно [проверить типобезопасность](../../standard/security/key-security-concepts.md#type-safety-and-security), не выполняется, хотя можно настроить политику безопасности таким образом, чтобы допускалось выполнение доверенного непроверяемого кода.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-163">Normally, code that is not [verifiably type safe](../../standard/security/key-security-concepts.md#type-safety-and-security) cannot run, although you can set security policy to allow the execution of trusted but unverifiable code.</span></span>  
  
 <span data-ttu-id="9e8e0-164">Если параметры **/md** и **/il** не заданы, Peverify.exe проверяет как CIL, так и метаданные.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-164">If neither the **/md** nor **/il** options are specified, Peverify.exe performs both types of checks.</span></span> <span data-ttu-id="9e8e0-165">Сначала Peverify.exe проверяет метаданные (параметр **/md**).</span><span class="sxs-lookup"><span data-stu-id="9e8e0-165">Peverify.exe performs **/md** checks first.</span></span> <span data-ttu-id="9e8e0-166">Если ошибок нет, выполняется проверка CIL (параметр **/il**).</span><span class="sxs-lookup"><span data-stu-id="9e8e0-166">If there are no errors, **/il** checks are made.</span></span> <span data-ttu-id="9e8e0-167">Если задан и параметр **/md**, и параметр **/il**, проверка по параметру **/il** производится даже при наличии ошибок в метаданных.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-167">If you specify both **/md** and **/il**, **/il** checks are made even if there are errors in the metadata.</span></span> <span data-ttu-id="9e8e0-168">Поэтому при отсутствии ошибок в метаданных команда **peverify** *имя_файла* эквивалентна команде **peverify** *имя_файла* **/md** **/il**.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-168">Thus, if there are no metadata errors, **peverify** *filename* is equivalent to **peverify** *filename* **/md** **/il**.</span></span>  
  
 <span data-ttu-id="9e8e0-169">Средство Peverify.exe осуществляет полную проверку CIL на основе анализа потоков данных и проверяет правильность метаданных на основе списка из нескольких сотен правил.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-169">Peverify.exe performs comprehensive MSIL verification checks based on dataflow analysis plus a list of several hundred rules on valid metadata.</span></span> <span data-ttu-id="9e8e0-170">Дополнительные сведения о проверках, выполняемых Peverify.exe, см. в документах со спецификацией проверки метаданных и спецификацией набора инструкций MSIL в папке Tools Developers Guide в Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-170">For detailed information on the checks Peverify.exe performs, see the "Metadata Validation Specification" and the "MSIL Instruction Set Specification" in the Tools Developers Guide folder in the Windows SDK.</span></span>  
  
<span data-ttu-id="9e8e0-171">На платформе .NET Framework 2.0 и более поздних версий поддерживается возврат проверяемых значений `byref`, заданных с использованием следующих инструкций MSIL: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call` и `unbox`.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-171">.NET Framework version 2.0 or later supports verifiable `byref` returns specified using the following MSIL instructions: `dup`, `ldsflda`, `ldflda`, `ldelema`, `call`, and `unbox`.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9e8e0-172">Примеры</span><span class="sxs-lookup"><span data-stu-id="9e8e0-172">Examples</span></span>  

 <span data-ttu-id="9e8e0-173">Следующая команда проверяет метаданные и безопасность типов CIL для методов, реализованных в сборке `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-173">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span>  
  
```console  
peverify myAssembly.exe /md /il  
```  
  
 <span data-ttu-id="9e8e0-174">После успешного завершения обработки этого запроса Peverify.exe отображает следующее сообщение.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-174">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
```  
  
 <span data-ttu-id="9e8e0-175">Следующая команда проверяет метаданные и безопасность типов CIL для методов, реализованных в сборке `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-175">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="9e8e0-176">Средство отображает затраченное на проверку время.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-176">The tool displays the time required to perform these checks.</span></span>  
  
```console  
peverify myAssembly.exe /md /il /clock  
```  
  
 <span data-ttu-id="9e8e0-177">После успешного завершения обработки этого запроса Peverify.exe отображает следующее сообщение.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-177">Upon successful completion of the above request, Peverify.exe displays the following message.</span></span>  
  
```output
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 <span data-ttu-id="9e8e0-178">Следующая команда проверяет метаданные и безопасность типов CIL для методов, реализованных в сборке `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-178">The following command performs metadata validation checks and MSIL type safety verification checks for methods implemented in the assembly `myAssembly.exe`.</span></span> <span data-ttu-id="9e8e0-179">Однако Peverify.exe останавливается, если число ошибок достигло максимального — то есть 100.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-179">Peverify.exe stops, however, when it reaches the maximum error count of 100.</span></span> <span data-ttu-id="9e8e0-180">Средство также игнорирует ошибки с заданными кодами.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-180">The tool also ignores the specified error codes.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 <span data-ttu-id="9e8e0-181">Следующая команда дает тот же результат, что и команда из предыдущего примера, но коды игнорируемых ошибок извлекаются из файла ответов `ignoreErrors.rsp`.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-181">The following command produces the same result as the above previous example, but specifies the error codes to ignore in the response file `ignoreErrors.rsp`.</span></span>  
  
```console  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 <span data-ttu-id="9e8e0-182">Файл ответов содержит список кодов ошибок, разделенных запятыми.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-182">The response file can contain a comma-separated list of error codes.</span></span>  
  
```text
0x12345678, 0xABCD1234  
```  
  
 <span data-ttu-id="9e8e0-183">Ошибки в файле ответов можно также задавать по одной в строке.</span><span class="sxs-lookup"><span data-stu-id="9e8e0-183">Alternatively, the response file can be formatted with one error code per line.</span></span>  
  
```text
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e8e0-184">См. также</span><span class="sxs-lookup"><span data-stu-id="9e8e0-184">See also</span></span>

- [<span data-ttu-id="9e8e0-185">Инструменты</span><span class="sxs-lookup"><span data-stu-id="9e8e0-185">Tools</span></span>](index.md)
- [<span data-ttu-id="9e8e0-186">Написание проверяемого типобезопасного кода</span><span class="sxs-lookup"><span data-stu-id="9e8e0-186">Writing Verifiably Type-Safe Code</span></span>](../misc/code-access-security-basics.md#typesafe_code)
- [<span data-ttu-id="9e8e0-187">Безопасность типа и безопасность</span><span class="sxs-lookup"><span data-stu-id="9e8e0-187">Type Safety and Security</span></span>](../../standard/security/key-security-concepts.md#type-safety-and-security)
- [<span data-ttu-id="9e8e0-188">Оболочки командной строки для разработчиков</span><span class="sxs-lookup"><span data-stu-id="9e8e0-188">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)
