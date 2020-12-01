---
title: SqlMetal.exe (средство создания кода)
description: Общие сведения об SqlMetal.exe, средстве создания кода. Используйте средство для создания кода и сопоставления с компонентом LINQ to SQL в .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: 4edf11315892ed8267bee17d69a70033348eca5c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272570"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="97c5a-104">SqlMetal.exe (средство создания кода)</span><span class="sxs-lookup"><span data-stu-id="97c5a-104">SqlMetal.exe (Code Generation Tool)</span></span>

<span data-ttu-id="97c5a-105">Средство командной строки SqlMetal создает код и сопоставление для компонента [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="97c5a-105">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="97c5a-106">С помощью описанных ниже параметров можно настраивать SqlMetal на выполнение различных действий, включая следующие.</span><span class="sxs-lookup"><span data-stu-id="97c5a-106">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="97c5a-107">Создание исходного кода и атрибутов сопоставления или файла сопоставления на основе базы данных.</span><span class="sxs-lookup"><span data-stu-id="97c5a-107">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="97c5a-108">Создание DBLM-файла для настройки на основе базы данных.</span><span class="sxs-lookup"><span data-stu-id="97c5a-108">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="97c5a-109">Создание кода и атрибутов сопоставления или файла сопоставления на основе DBML-файла.</span><span class="sxs-lookup"><span data-stu-id="97c5a-109">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="97c5a-110">Эта программа автоматически устанавливается вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="97c5a-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="97c5a-111">По умолчанию файл располагается в папке `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span><span class="sxs-lookup"><span data-stu-id="97c5a-111">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="97c5a-112">Если Visual Studio не установлена, файл SQLMetal можно получить, скачав [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span><span class="sxs-lookup"><span data-stu-id="97c5a-112">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97c5a-113">Разработчики, работающие в Visual Studio, также могут использовать реляционный конструктор объектов для создания классов сущностей.</span><span class="sxs-lookup"><span data-stu-id="97c5a-113">Developers who use Visual Studio can also use the Object Relational Designer to generate entity classes.</span></span> <span data-ttu-id="97c5a-114">Командная строка удобна при работе с большими базами данных.</span><span class="sxs-lookup"><span data-stu-id="97c5a-114">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="97c5a-115">Поскольку SqlMetal представляет собой программу командной строки, ее можно использовать в процессе построения.</span><span class="sxs-lookup"><span data-stu-id="97c5a-115">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="97c5a-116">Чтобы применить этот инструмент, воспользуйтесь командной строкой разработчика для Visual Studio (или командной строкой Visual Studio в Windows 7).</span><span class="sxs-lookup"><span data-stu-id="97c5a-116">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="97c5a-117">Подробнее см. в разделе [Командная строка](developer-command-prompt-for-vs.md). В командной строке введите следующее:</span><span class="sxs-lookup"><span data-stu-id="97c5a-117">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97c5a-118">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="97c5a-118">Syntax</span></span>  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="97c5a-119">Параметры</span><span class="sxs-lookup"><span data-stu-id="97c5a-119">Options</span></span>  

 <span data-ttu-id="97c5a-120">Чтобы просмотреть текущий список параметров, в командной строке введите `sqlmetal /?` в каталоге установки.</span><span class="sxs-lookup"><span data-stu-id="97c5a-120">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="97c5a-121">**Параметры подключения**</span><span class="sxs-lookup"><span data-stu-id="97c5a-121">**Connection Options**</span></span>  
  
|<span data-ttu-id="97c5a-122">Параметр</span><span class="sxs-lookup"><span data-stu-id="97c5a-122">Option</span></span>|<span data-ttu-id="97c5a-123">Описание</span><span class="sxs-lookup"><span data-stu-id="97c5a-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="97c5a-124">**/server:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="97c5a-124">**/server:** *\<name>*</span></span>|<span data-ttu-id="97c5a-125">Задает имя сервера базы данных.</span><span class="sxs-lookup"><span data-stu-id="97c5a-125">Specifies database server name.</span></span>|  
|<span data-ttu-id="97c5a-126">**/database:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="97c5a-126">**/database:** *\<name>*</span></span>|<span data-ttu-id="97c5a-127">Задает каталог базы данных на сервере.</span><span class="sxs-lookup"><span data-stu-id="97c5a-127">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="97c5a-128">**/user:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="97c5a-128">**/user:** *\<name>*</span></span>|<span data-ttu-id="97c5a-129">Задает идентификатор пользователя для входа. Значение по умолчанию: использование проверки подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="97c5a-129">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="97c5a-130">**/password:** *\<password>*</span><span class="sxs-lookup"><span data-stu-id="97c5a-130">**/password:** *\<password>*</span></span>|<span data-ttu-id="97c5a-131">Задает пароль для входа.</span><span class="sxs-lookup"><span data-stu-id="97c5a-131">Specifies logon password.</span></span> <span data-ttu-id="97c5a-132">Значение по умолчанию: использование проверки подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="97c5a-132">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="97c5a-133">**/conn:** *\<connection string>*</span><span class="sxs-lookup"><span data-stu-id="97c5a-133">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="97c5a-134">Задает строку подключения к базе данных.</span><span class="sxs-lookup"><span data-stu-id="97c5a-134">Specifies database connection string.</span></span> <span data-ttu-id="97c5a-135">Нельзя использовать с параметрами **/server**, **/database**, **/user** или **/password** .</span><span class="sxs-lookup"><span data-stu-id="97c5a-135">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="97c5a-136">В строке подключения не следует указывать имя файла.</span><span class="sxs-lookup"><span data-stu-id="97c5a-136">Do not include the file name in the connection string.</span></span> <span data-ttu-id="97c5a-137">Вместо этого добавьте имя файла в командную строку в качестве входного файла.</span><span class="sxs-lookup"><span data-stu-id="97c5a-137">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="97c5a-138">Например, в следующей строке указывается входной файл "c:\northwnd.mdf": **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"** .</span><span class="sxs-lookup"><span data-stu-id="97c5a-138">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="97c5a-139">**/timeout:** *\<seconds>*</span><span class="sxs-lookup"><span data-stu-id="97c5a-139">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="97c5a-140">Задает время ожидания для доступа SqlMetal к базе данных.</span><span class="sxs-lookup"><span data-stu-id="97c5a-140">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="97c5a-141">Значение по умолчанию: 0 (то есть время не ограничено).</span><span class="sxs-lookup"><span data-stu-id="97c5a-141">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="97c5a-142">**Параметры извлечения**</span><span class="sxs-lookup"><span data-stu-id="97c5a-142">**Extraction options**</span></span>  
  
|<span data-ttu-id="97c5a-143">Параметр</span><span class="sxs-lookup"><span data-stu-id="97c5a-143">Option</span></span>|<span data-ttu-id="97c5a-144">Описание</span><span class="sxs-lookup"><span data-stu-id="97c5a-144">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="97c5a-145">**/views**</span><span class="sxs-lookup"><span data-stu-id="97c5a-145">**/views**</span></span>|<span data-ttu-id="97c5a-146">Извлекает представления базы данных.</span><span class="sxs-lookup"><span data-stu-id="97c5a-146">Extracts database views.</span></span>|  
|<span data-ttu-id="97c5a-147">**/functions**</span><span class="sxs-lookup"><span data-stu-id="97c5a-147">**/functions**</span></span>|<span data-ttu-id="97c5a-148">Извлекает функции базы данных.</span><span class="sxs-lookup"><span data-stu-id="97c5a-148">Extracts database functions.</span></span>|  
|<span data-ttu-id="97c5a-149">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="97c5a-149">**/sprocs**</span></span>|<span data-ttu-id="97c5a-150">Извлекает хранимые процедуры.</span><span class="sxs-lookup"><span data-stu-id="97c5a-150">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="97c5a-151">**Параметры вывода**</span><span class="sxs-lookup"><span data-stu-id="97c5a-151">**Output options**</span></span>  
  
|<span data-ttu-id="97c5a-152">Параметр</span><span class="sxs-lookup"><span data-stu-id="97c5a-152">Option</span></span>|<span data-ttu-id="97c5a-153">Описание</span><span class="sxs-lookup"><span data-stu-id="97c5a-153">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="97c5a-154">**/dbml** *[:файл]*</span><span class="sxs-lookup"><span data-stu-id="97c5a-154">**/dbml** *[:file]*</span></span>|<span data-ttu-id="97c5a-155">Направляет вывод в DBML-файл.</span><span class="sxs-lookup"><span data-stu-id="97c5a-155">Sends output as .dbml.</span></span> <span data-ttu-id="97c5a-156">Не может использоваться с параметром **/map** .</span><span class="sxs-lookup"><span data-stu-id="97c5a-156">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="97c5a-157">**/code** *[:файл]*</span><span class="sxs-lookup"><span data-stu-id="97c5a-157">**/code** *[:file]*</span></span>|<span data-ttu-id="97c5a-158">Направляет вывод в файл исходного кода.</span><span class="sxs-lookup"><span data-stu-id="97c5a-158">Sends output as source code.</span></span> <span data-ttu-id="97c5a-159">Не может использоваться с параметром **/dbml** .</span><span class="sxs-lookup"><span data-stu-id="97c5a-159">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="97c5a-160">**/map** *[:файл]*</span><span class="sxs-lookup"><span data-stu-id="97c5a-160">**/map** *[:file]*</span></span>|<span data-ttu-id="97c5a-161">Создает XML-файл сопоставления вместо атрибутов.</span><span class="sxs-lookup"><span data-stu-id="97c5a-161">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="97c5a-162">Не может использоваться с параметром **/dbml** .</span><span class="sxs-lookup"><span data-stu-id="97c5a-162">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="97c5a-163">**Прочее**</span><span class="sxs-lookup"><span data-stu-id="97c5a-163">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="97c5a-164">Параметр</span><span class="sxs-lookup"><span data-stu-id="97c5a-164">Option</span></span>|<span data-ttu-id="97c5a-165">Описание</span><span class="sxs-lookup"><span data-stu-id="97c5a-165">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="97c5a-166">**/language:** *\<language>*</span><span class="sxs-lookup"><span data-stu-id="97c5a-166">**/language:** *\<language>*</span></span>|<span data-ttu-id="97c5a-167">Задает язык исходного кода.</span><span class="sxs-lookup"><span data-stu-id="97c5a-167">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="97c5a-168">*\<language>* (допускается): vb, csharp.</span><span class="sxs-lookup"><span data-stu-id="97c5a-168">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="97c5a-169">Значение по умолчанию: определяется по расширению имени файла кода.</span><span class="sxs-lookup"><span data-stu-id="97c5a-169">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="97c5a-170">**/namespace:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="97c5a-170">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="97c5a-171">Задает пространство имен сгенерированного кода.</span><span class="sxs-lookup"><span data-stu-id="97c5a-171">Specifies namespace of the generated code.</span></span> <span data-ttu-id="97c5a-172">Значение по умолчанию: пространство имен не определяется.</span><span class="sxs-lookup"><span data-stu-id="97c5a-172">Default value: no namespace.</span></span>|  
|<span data-ttu-id="97c5a-173">**/context:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="97c5a-173">**/context:** *\<type>*</span></span>|<span data-ttu-id="97c5a-174">Задает имя класса контекста данных.</span><span class="sxs-lookup"><span data-stu-id="97c5a-174">Specifies name of data context class.</span></span> <span data-ttu-id="97c5a-175">Значение по умолчанию: определяется по имени базы данных.</span><span class="sxs-lookup"><span data-stu-id="97c5a-175">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="97c5a-176">**/entitybase:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="97c5a-176">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="97c5a-177">Задает базовый класс для классов сущностей в сгенерированном коде.</span><span class="sxs-lookup"><span data-stu-id="97c5a-177">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="97c5a-178">Значение по умолчанию: базовый класс для сущностей не определяется.</span><span class="sxs-lookup"><span data-stu-id="97c5a-178">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="97c5a-179">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="97c5a-179">**/pluralize**</span></span>|<span data-ttu-id="97c5a-180">Автоматически преобразует имена классов и членов в форму множественного или единственного числа.</span><span class="sxs-lookup"><span data-stu-id="97c5a-180">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="97c5a-181">Этот вариант доступен только в английской версии (США).</span><span class="sxs-lookup"><span data-stu-id="97c5a-181">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="97c5a-182">**/serialization:** *\<option>*</span><span class="sxs-lookup"><span data-stu-id="97c5a-182">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="97c5a-183">Создает сериализуемые классы.</span><span class="sxs-lookup"><span data-stu-id="97c5a-183">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="97c5a-184">*\<option>* (допускается): нет, однонаправленный.</span><span class="sxs-lookup"><span data-stu-id="97c5a-184">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="97c5a-185">Значение по умолчанию: Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="97c5a-185">Default value: None.</span></span><br /><br /> <span data-ttu-id="97c5a-186">Дополнительные сведения см. в разделе [Сериализация](../data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="97c5a-186">For more information, see [Serialization](../data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="97c5a-187">**Входной файл**</span><span class="sxs-lookup"><span data-stu-id="97c5a-187">**Input File**</span></span>  
  
|<span data-ttu-id="97c5a-188">Параметр</span><span class="sxs-lookup"><span data-stu-id="97c5a-188">Option</span></span>|<span data-ttu-id="97c5a-189">Описание</span><span class="sxs-lookup"><span data-stu-id="97c5a-189">Description</span></span>|  
|------------|-----------------|  
|**\<input file>**|<span data-ttu-id="97c5a-190">Задает MDF-файл SQL Server, экспресс-выпуск, SDF-файл SQL Server Compact 3.5 или промежуточный DBML-файл.</span><span class="sxs-lookup"><span data-stu-id="97c5a-190">Specifies a SQL Server Express .mdf file, a SQL Server Compact 3.5 .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97c5a-191">Примечания</span><span class="sxs-lookup"><span data-stu-id="97c5a-191">Remarks</span></span>  

 <span data-ttu-id="97c5a-192">Функции SqlMetal фактически выполняются в два этапа.</span><span class="sxs-lookup"><span data-stu-id="97c5a-192">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="97c5a-193">Метаданные базы данных извлекаются в DBML-файл.</span><span class="sxs-lookup"><span data-stu-id="97c5a-193">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="97c5a-194">Создается выходной файл кода.</span><span class="sxs-lookup"><span data-stu-id="97c5a-194">Generating a code output file.</span></span>  
  
     <span data-ttu-id="97c5a-195">Используя соответствующие параметры командной строки, можно получать исходный код Visual Basic или C# либо XML-файл сопоставления.</span><span class="sxs-lookup"><span data-stu-id="97c5a-195">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="97c5a-196">Чтобы извлечь метаданные из MDF-файла, необходимо указать его имя после всех остальных параметров.</span><span class="sxs-lookup"><span data-stu-id="97c5a-196">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="97c5a-197">Если не **/server** указан, предполагается **localhost/sqlexpress** .</span><span class="sxs-lookup"><span data-stu-id="97c5a-197">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="97c5a-198">Microsoft SQL Server 2005 выдает исключение в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="97c5a-198">Microsoft SQL Server 2005 throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="97c5a-199">SqlMetal пытается извлечь хранимую процедуру, вызывающую саму себя.</span><span class="sxs-lookup"><span data-stu-id="97c5a-199">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="97c5a-200">Уровень вложенности хранимой процедуры, функции или представления превышает 32 уровня.</span><span class="sxs-lookup"><span data-stu-id="97c5a-200">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="97c5a-201">SqlMetal перехватывает это исключение и сообщает о нем в виде предупреждения.</span><span class="sxs-lookup"><span data-stu-id="97c5a-201">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="97c5a-202">Чтобы указать имя входного файла, добавьте имя в командную строку в качестве входного файла.</span><span class="sxs-lookup"><span data-stu-id="97c5a-202">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="97c5a-203">Включение имени файла в строку подключения (параметром **/conn** ) не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="97c5a-203">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="97c5a-204">Примеры</span><span class="sxs-lookup"><span data-stu-id="97c5a-204">Examples</span></span>  

 <span data-ttu-id="97c5a-205">Создание DBML-файла, содержащего извлеченные метаданные SQL.</span><span class="sxs-lookup"><span data-stu-id="97c5a-205">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="97c5a-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="97c5a-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="97c5a-207">Создание DBML-файла, содержащего извлеченные метаданные SQL из MDF-файла, с помощью SQL Server, экспресс-выпуск.</span><span class="sxs-lookup"><span data-stu-id="97c5a-207">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="97c5a-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="97c5a-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="97c5a-209">Создание DBML-файла, содержащего извлеченные метаданные SQL из SQL Server, экспресс-выпуск.</span><span class="sxs-lookup"><span data-stu-id="97c5a-209">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="97c5a-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="97c5a-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="97c5a-211">Создание исходного кода из DBML-файла метаданных.</span><span class="sxs-lookup"><span data-stu-id="97c5a-211">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="97c5a-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="97c5a-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="97c5a-213">Создание исходного кода непосредственно из метаданных SQL.</span><span class="sxs-lookup"><span data-stu-id="97c5a-213">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="97c5a-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="97c5a-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97c5a-215">При использовании параметра **/pluralize** вместе с учебной базой данных Northwind необходимо иметь в виду следующее.</span><span class="sxs-lookup"><span data-stu-id="97c5a-215">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="97c5a-216">Когда SqlMetal создает имена типов строк для таблиц, имена таблиц представляются в единственном числе.</span><span class="sxs-lookup"><span data-stu-id="97c5a-216">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="97c5a-217">При создании свойств <xref:System.Data.Linq.DataContext> для таблиц имена таблиц представляются во множественном числе.</span><span class="sxs-lookup"><span data-stu-id="97c5a-217">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="97c5a-218">Однако таблицы в учебной базе данных Northwind уже имеют имена в форме множественного числа.</span><span class="sxs-lookup"><span data-stu-id="97c5a-218">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="97c5a-219">Поэтому данная часть процедуры не будет иметь видимого эффекта.</span><span class="sxs-lookup"><span data-stu-id="97c5a-219">Therefore, you do not see that part working.</span></span> <span data-ttu-id="97c5a-220">Если таблицам базы данных принято присваивать имена в единственном числе, то коллекциям .NET принято присваивать имена во множественном числе.</span><span class="sxs-lookup"><span data-stu-id="97c5a-220">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97c5a-221">См. также</span><span class="sxs-lookup"><span data-stu-id="97c5a-221">See also</span></span>

- [<span data-ttu-id="97c5a-222">Практическое руководство. Создание модели объектов на языке Visual Basic или C#</span><span class="sxs-lookup"><span data-stu-id="97c5a-222">How to: Generate the Object Model in Visual Basic or C#</span></span>](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="97c5a-223">Создание кода в LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="97c5a-223">Code Generation in LINQ to SQL</span></span>](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="97c5a-224">Внешнее сопоставление</span><span class="sxs-lookup"><span data-stu-id="97c5a-224">External Mapping</span></span>](../data/adonet/sql/linq/external-mapping.md)
