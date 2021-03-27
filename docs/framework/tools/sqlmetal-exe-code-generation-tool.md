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
ms.openlocfilehash: 57229ce767a140e1756fddb2c19fb31893a0ab90
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653625"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="40f81-104">SqlMetal.exe (средство создания кода)</span><span class="sxs-lookup"><span data-stu-id="40f81-104">SqlMetal.exe (Code Generation Tool)</span></span>

<span data-ttu-id="40f81-105">Средство командной строки SqlMetal создает код и сопоставление для компонента [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="40f81-105">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="40f81-106">С помощью описанных ниже параметров можно настраивать SqlMetal на выполнение различных действий, включая следующие.</span><span class="sxs-lookup"><span data-stu-id="40f81-106">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="40f81-107">Создание исходного кода и атрибутов сопоставления или файла сопоставления на основе базы данных.</span><span class="sxs-lookup"><span data-stu-id="40f81-107">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="40f81-108">Создание DBLM-файла для настройки на основе базы данных.</span><span class="sxs-lookup"><span data-stu-id="40f81-108">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="40f81-109">Создание кода и атрибутов сопоставления или файла сопоставления на основе DBML-файла.</span><span class="sxs-lookup"><span data-stu-id="40f81-109">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
<span data-ttu-id="40f81-110">Эта программа автоматически устанавливается вместе с Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="40f81-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="40f81-111">По умолчанию файл располагается в папке `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span><span class="sxs-lookup"><span data-stu-id="40f81-111">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="40f81-112">Если Visual Studio не установлена, файл SQLMetal можно получить, скачав [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span><span class="sxs-lookup"><span data-stu-id="40f81-112">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40f81-113">Разработчики, работающие в Visual Studio, также могут использовать реляционный конструктор объектов для создания классов сущностей.</span><span class="sxs-lookup"><span data-stu-id="40f81-113">Developers who use Visual Studio can also use the Object Relational Designer to generate entity classes.</span></span> <span data-ttu-id="40f81-114">Командная строка удобна при работе с большими базами данных.</span><span class="sxs-lookup"><span data-stu-id="40f81-114">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="40f81-115">Поскольку SqlMetal представляет собой программу командной строки, ее можно использовать в процессе построения.</span><span class="sxs-lookup"><span data-stu-id="40f81-115">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
<span data-ttu-id="40f81-116">Для запуска этого средства используйте [Командную строку разработчика или PowerShell для разработчиков в Visual Studio](/visualstudio/ide/reference/command-prompt-powershell).</span><span class="sxs-lookup"><span data-stu-id="40f81-116">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span> <span data-ttu-id="40f81-117">В командной строке введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="40f81-117">At the command prompt, enter the following command:</span></span>

```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="40f81-118">Параметры</span><span class="sxs-lookup"><span data-stu-id="40f81-118">Options</span></span>  

 <span data-ttu-id="40f81-119">Чтобы просмотреть текущий список параметров, в командной строке введите `sqlmetal /?` в каталоге установки.</span><span class="sxs-lookup"><span data-stu-id="40f81-119">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="40f81-120">**Параметры подключения**</span><span class="sxs-lookup"><span data-stu-id="40f81-120">**Connection Options**</span></span>  
  
|<span data-ttu-id="40f81-121">Параметр</span><span class="sxs-lookup"><span data-stu-id="40f81-121">Option</span></span>|<span data-ttu-id="40f81-122">Описание</span><span class="sxs-lookup"><span data-stu-id="40f81-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="40f81-123">**/server:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="40f81-123">**/server:** *\<name>*</span></span>|<span data-ttu-id="40f81-124">Задает имя сервера базы данных.</span><span class="sxs-lookup"><span data-stu-id="40f81-124">Specifies database server name.</span></span>|  
|<span data-ttu-id="40f81-125">**/database:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="40f81-125">**/database:** *\<name>*</span></span>|<span data-ttu-id="40f81-126">Задает каталог базы данных на сервере.</span><span class="sxs-lookup"><span data-stu-id="40f81-126">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="40f81-127">**/user:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="40f81-127">**/user:** *\<name>*</span></span>|<span data-ttu-id="40f81-128">Задает идентификатор пользователя для входа. Значение по умолчанию: использование проверки подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="40f81-128">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="40f81-129">**/password:** *\<password>*</span><span class="sxs-lookup"><span data-stu-id="40f81-129">**/password:** *\<password>*</span></span>|<span data-ttu-id="40f81-130">Задает пароль для входа.</span><span class="sxs-lookup"><span data-stu-id="40f81-130">Specifies logon password.</span></span> <span data-ttu-id="40f81-131">Значение по умолчанию: использование проверки подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="40f81-131">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="40f81-132">**/conn:** *\<connection string>*</span><span class="sxs-lookup"><span data-stu-id="40f81-132">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="40f81-133">Задает строку подключения к базе данных.</span><span class="sxs-lookup"><span data-stu-id="40f81-133">Specifies database connection string.</span></span> <span data-ttu-id="40f81-134">Нельзя использовать с параметрами **/server**, **/database**, **/user** или **/password** .</span><span class="sxs-lookup"><span data-stu-id="40f81-134">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="40f81-135">В строке подключения не следует указывать имя файла.</span><span class="sxs-lookup"><span data-stu-id="40f81-135">Do not include the file name in the connection string.</span></span> <span data-ttu-id="40f81-136">Вместо этого добавьте имя файла в командную строку в качестве входного файла.</span><span class="sxs-lookup"><span data-stu-id="40f81-136">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="40f81-137">Например, в следующей строке указывается входной файл "c:\northwnd.mdf": **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"** .</span><span class="sxs-lookup"><span data-stu-id="40f81-137">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="40f81-138">**/timeout:** *\<seconds>*</span><span class="sxs-lookup"><span data-stu-id="40f81-138">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="40f81-139">Задает время ожидания для доступа SqlMetal к базе данных.</span><span class="sxs-lookup"><span data-stu-id="40f81-139">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="40f81-140">Значение по умолчанию: 0 (то есть время не ограничено).</span><span class="sxs-lookup"><span data-stu-id="40f81-140">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="40f81-141">**Параметры извлечения**</span><span class="sxs-lookup"><span data-stu-id="40f81-141">**Extraction options**</span></span>  
  
|<span data-ttu-id="40f81-142">Параметр</span><span class="sxs-lookup"><span data-stu-id="40f81-142">Option</span></span>|<span data-ttu-id="40f81-143">Описание</span><span class="sxs-lookup"><span data-stu-id="40f81-143">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="40f81-144">**/views**</span><span class="sxs-lookup"><span data-stu-id="40f81-144">**/views**</span></span>|<span data-ttu-id="40f81-145">Извлекает представления базы данных.</span><span class="sxs-lookup"><span data-stu-id="40f81-145">Extracts database views.</span></span>|  
|<span data-ttu-id="40f81-146">**/functions**</span><span class="sxs-lookup"><span data-stu-id="40f81-146">**/functions**</span></span>|<span data-ttu-id="40f81-147">Извлекает функции базы данных.</span><span class="sxs-lookup"><span data-stu-id="40f81-147">Extracts database functions.</span></span>|  
|<span data-ttu-id="40f81-148">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="40f81-148">**/sprocs**</span></span>|<span data-ttu-id="40f81-149">Извлекает хранимые процедуры.</span><span class="sxs-lookup"><span data-stu-id="40f81-149">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="40f81-150">**Параметры вывода**</span><span class="sxs-lookup"><span data-stu-id="40f81-150">**Output options**</span></span>  
  
|<span data-ttu-id="40f81-151">Параметр</span><span class="sxs-lookup"><span data-stu-id="40f81-151">Option</span></span>|<span data-ttu-id="40f81-152">Описание</span><span class="sxs-lookup"><span data-stu-id="40f81-152">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="40f81-153">**/dbml** *[:файл]*</span><span class="sxs-lookup"><span data-stu-id="40f81-153">**/dbml** *[:file]*</span></span>|<span data-ttu-id="40f81-154">Направляет вывод в DBML-файл.</span><span class="sxs-lookup"><span data-stu-id="40f81-154">Sends output as .dbml.</span></span> <span data-ttu-id="40f81-155">Не может использоваться с параметром **/map** .</span><span class="sxs-lookup"><span data-stu-id="40f81-155">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="40f81-156">**/code** *[:файл]*</span><span class="sxs-lookup"><span data-stu-id="40f81-156">**/code** *[:file]*</span></span>|<span data-ttu-id="40f81-157">Направляет вывод в файл исходного кода.</span><span class="sxs-lookup"><span data-stu-id="40f81-157">Sends output as source code.</span></span> <span data-ttu-id="40f81-158">Не может использоваться с параметром **/dbml** .</span><span class="sxs-lookup"><span data-stu-id="40f81-158">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="40f81-159">**/map** *[:файл]*</span><span class="sxs-lookup"><span data-stu-id="40f81-159">**/map** *[:file]*</span></span>|<span data-ttu-id="40f81-160">Создает XML-файл сопоставления вместо атрибутов.</span><span class="sxs-lookup"><span data-stu-id="40f81-160">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="40f81-161">Не может использоваться с параметром **/dbml** .</span><span class="sxs-lookup"><span data-stu-id="40f81-161">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="40f81-162">**Прочее**</span><span class="sxs-lookup"><span data-stu-id="40f81-162">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="40f81-163">Параметр</span><span class="sxs-lookup"><span data-stu-id="40f81-163">Option</span></span>|<span data-ttu-id="40f81-164">Описание</span><span class="sxs-lookup"><span data-stu-id="40f81-164">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="40f81-165">**/language:** *\<language>*</span><span class="sxs-lookup"><span data-stu-id="40f81-165">**/language:** *\<language>*</span></span>|<span data-ttu-id="40f81-166">Задает язык исходного кода.</span><span class="sxs-lookup"><span data-stu-id="40f81-166">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="40f81-167">*\<language>* (допускается): vb, csharp.</span><span class="sxs-lookup"><span data-stu-id="40f81-167">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="40f81-168">Значение по умолчанию: определяется по расширению имени файла кода.</span><span class="sxs-lookup"><span data-stu-id="40f81-168">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="40f81-169">**/namespace:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="40f81-169">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="40f81-170">Задает пространство имен сгенерированного кода.</span><span class="sxs-lookup"><span data-stu-id="40f81-170">Specifies namespace of the generated code.</span></span> <span data-ttu-id="40f81-171">Значение по умолчанию: пространство имен не определяется.</span><span class="sxs-lookup"><span data-stu-id="40f81-171">Default value: no namespace.</span></span>|  
|<span data-ttu-id="40f81-172">**/context:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="40f81-172">**/context:** *\<type>*</span></span>|<span data-ttu-id="40f81-173">Задает имя класса контекста данных.</span><span class="sxs-lookup"><span data-stu-id="40f81-173">Specifies name of data context class.</span></span> <span data-ttu-id="40f81-174">Значение по умолчанию: определяется по имени базы данных.</span><span class="sxs-lookup"><span data-stu-id="40f81-174">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="40f81-175">**/entitybase:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="40f81-175">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="40f81-176">Задает базовый класс для классов сущностей в сгенерированном коде.</span><span class="sxs-lookup"><span data-stu-id="40f81-176">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="40f81-177">Значение по умолчанию: базовый класс для сущностей не определяется.</span><span class="sxs-lookup"><span data-stu-id="40f81-177">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="40f81-178">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="40f81-178">**/pluralize**</span></span>|<span data-ttu-id="40f81-179">Автоматически преобразует имена классов и членов в форму множественного или единственного числа.</span><span class="sxs-lookup"><span data-stu-id="40f81-179">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="40f81-180">Этот вариант доступен только в английской версии (США).</span><span class="sxs-lookup"><span data-stu-id="40f81-180">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="40f81-181">**/serialization:** *\<option>*</span><span class="sxs-lookup"><span data-stu-id="40f81-181">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="40f81-182">Создает сериализуемые классы.</span><span class="sxs-lookup"><span data-stu-id="40f81-182">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="40f81-183">*\<option>* (допускается): нет, однонаправленный.</span><span class="sxs-lookup"><span data-stu-id="40f81-183">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="40f81-184">Значение по умолчанию: Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="40f81-184">Default value: None.</span></span><br /><br /> <span data-ttu-id="40f81-185">Дополнительные сведения см. в разделе [Сериализация](../data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="40f81-185">For more information, see [Serialization](../data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="40f81-186">**Входной файл**</span><span class="sxs-lookup"><span data-stu-id="40f81-186">**Input File**</span></span>  
  
|<span data-ttu-id="40f81-187">Параметр</span><span class="sxs-lookup"><span data-stu-id="40f81-187">Option</span></span>|<span data-ttu-id="40f81-188">Описание</span><span class="sxs-lookup"><span data-stu-id="40f81-188">Description</span></span>|  
|------------|-----------------|  
|**\<input file>**|<span data-ttu-id="40f81-189">Задает MDF-файл SQL Server, экспресс-выпуск, SDF-файл SQL Server Compact 3.5 или промежуточный DBML-файл.</span><span class="sxs-lookup"><span data-stu-id="40f81-189">Specifies a SQL Server Express .mdf file, a SQL Server Compact 3.5 .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40f81-190">Примечания</span><span class="sxs-lookup"><span data-stu-id="40f81-190">Remarks</span></span>  

 <span data-ttu-id="40f81-191">Функции SqlMetal фактически выполняются в два этапа.</span><span class="sxs-lookup"><span data-stu-id="40f81-191">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="40f81-192">Метаданные базы данных извлекаются в DBML-файл.</span><span class="sxs-lookup"><span data-stu-id="40f81-192">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="40f81-193">Создается выходной файл кода.</span><span class="sxs-lookup"><span data-stu-id="40f81-193">Generating a code output file.</span></span>  
  
     <span data-ttu-id="40f81-194">Используя соответствующие параметры командной строки, можно получать исходный код Visual Basic или C# либо XML-файл сопоставления.</span><span class="sxs-lookup"><span data-stu-id="40f81-194">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="40f81-195">Чтобы извлечь метаданные из MDF-файла, необходимо указать его имя после всех остальных параметров.</span><span class="sxs-lookup"><span data-stu-id="40f81-195">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="40f81-196">Если не **/server** указан, предполагается **localhost/sqlexpress** .</span><span class="sxs-lookup"><span data-stu-id="40f81-196">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="40f81-197">Microsoft SQL Server 2005 выдает исключение в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="40f81-197">Microsoft SQL Server 2005 throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="40f81-198">SqlMetal пытается извлечь хранимую процедуру, вызывающую саму себя.</span><span class="sxs-lookup"><span data-stu-id="40f81-198">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="40f81-199">Уровень вложенности хранимой процедуры, функции или представления превышает 32 уровня.</span><span class="sxs-lookup"><span data-stu-id="40f81-199">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="40f81-200">SqlMetal перехватывает это исключение и сообщает о нем в виде предупреждения.</span><span class="sxs-lookup"><span data-stu-id="40f81-200">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="40f81-201">Чтобы указать имя входного файла, добавьте имя в командную строку в качестве входного файла.</span><span class="sxs-lookup"><span data-stu-id="40f81-201">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="40f81-202">Включение имени файла в строку подключения (параметром **/conn** ) не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="40f81-202">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="40f81-203">Примеры</span><span class="sxs-lookup"><span data-stu-id="40f81-203">Examples</span></span>  

 <span data-ttu-id="40f81-204">Создание DBML-файла, содержащего извлеченные метаданные SQL.</span><span class="sxs-lookup"><span data-stu-id="40f81-204">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="40f81-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="40f81-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="40f81-206">Создание DBML-файла, содержащего извлеченные метаданные SQL из MDF-файла, с помощью SQL Server, экспресс-выпуск.</span><span class="sxs-lookup"><span data-stu-id="40f81-206">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="40f81-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="40f81-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="40f81-208">Создание DBML-файла, содержащего извлеченные метаданные SQL из SQL Server, экспресс-выпуск.</span><span class="sxs-lookup"><span data-stu-id="40f81-208">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="40f81-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="40f81-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="40f81-210">Создание исходного кода из DBML-файла метаданных.</span><span class="sxs-lookup"><span data-stu-id="40f81-210">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="40f81-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="40f81-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="40f81-212">Создание исходного кода непосредственно из метаданных SQL.</span><span class="sxs-lookup"><span data-stu-id="40f81-212">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="40f81-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="40f81-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40f81-214">При использовании параметра **/pluralize** вместе с учебной базой данных Northwind необходимо иметь в виду следующее.</span><span class="sxs-lookup"><span data-stu-id="40f81-214">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="40f81-215">Когда SqlMetal создает имена типов строк для таблиц, имена таблиц представляются в единственном числе.</span><span class="sxs-lookup"><span data-stu-id="40f81-215">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="40f81-216">При создании свойств <xref:System.Data.Linq.DataContext> для таблиц имена таблиц представляются во множественном числе.</span><span class="sxs-lookup"><span data-stu-id="40f81-216">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="40f81-217">Однако таблицы в учебной базе данных Northwind уже имеют имена в форме множественного числа.</span><span class="sxs-lookup"><span data-stu-id="40f81-217">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="40f81-218">Поэтому данная часть процедуры не будет иметь видимого эффекта.</span><span class="sxs-lookup"><span data-stu-id="40f81-218">Therefore, you do not see that part working.</span></span> <span data-ttu-id="40f81-219">Если таблицам базы данных принято присваивать имена в единственном числе, то коллекциям .NET принято присваивать имена во множественном числе.</span><span class="sxs-lookup"><span data-stu-id="40f81-219">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40f81-220">См. также</span><span class="sxs-lookup"><span data-stu-id="40f81-220">See also</span></span>

- [<span data-ttu-id="40f81-221">Практическое руководство. Создание модели объектов на языке Visual Basic или C#</span><span class="sxs-lookup"><span data-stu-id="40f81-221">How to: Generate the Object Model in Visual Basic or C#</span></span>](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="40f81-222">Создание кода в LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="40f81-222">Code Generation in LINQ to SQL</span></span>](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="40f81-223">Внешнее сопоставление</span><span class="sxs-lookup"><span data-stu-id="40f81-223">External Mapping</span></span>](../data/adonet/sql/linq/external-mapping.md)
