---
title: XML Schema Definition Tool (Xsd.exe)
description: Инструмент создания XML-сериализатора создает сборку XML-сериализации для типов в указанной сборке, улучшающую производительность XmlSerializer при запуске.
ms.date: 03/30/2017
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
ms.openlocfilehash: a66ebfee3a461bb800e61e4f1d789f497da2f9d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676612"
---
# <a name="xml-schema-definition-tool-xsdexe"></a><span data-ttu-id="dd0b1-103">XML Schema Definition Tool (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="dd0b1-103">XML Schema Definition Tool (Xsd.exe)</span></span>

<span data-ttu-id="dd0b1-104">Инструмент определения схемы XML (Xsd.exe) создает схему XML или классы CLR из файлов XDR, XML и XSD либо из классов в сборке среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-104">The XML Schema Definition (Xsd.exe) tool generates XML schema or common language runtime classes from XDR, XML, and XSD files, or from classes in a runtime assembly.</span></span>

<span data-ttu-id="dd0b1-105">Инструмент определения схемы XML (Xsd.exe) обычно можно найти по следующему пути:</span><span class="sxs-lookup"><span data-stu-id="dd0b1-105">The XML Schema Definition tool (Xsd.exe) usually can be found in the following path:</span></span>\
<span data-ttu-id="dd0b1-106">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{версия}\\bin\\NETFX {версия} Tools\\_</span><span class="sxs-lookup"><span data-stu-id="dd0b1-106">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span></span>

## <a name="syntax"></a><span data-ttu-id="dd0b1-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dd0b1-107">Syntax</span></span>

<span data-ttu-id="dd0b1-108">Запустите инструмент из командной строки.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-108">Run the tool from the command line.</span></span>

```console
xsd file.xdr [-outputdir:directory][/parameters:file.xml]
xsd file.xml [-outputdir:directory] [/parameters:file.xml]
xsd file.xsd {/classes | /dataset} [/element:element]
             [/enableLinqDataSet] [/language:language]
                          [/namespace:namespace] [-outputdir:directory] [URI:uri]
                          [/parameters:file.xml]
xsd {file.dll | file.exe} [-outputdir:directory] [/type:typename [...]][/parameters:file.xml]
```
  
> [!TIP]
> <span data-ttu-id="dd0b1-109">Для нормальной работы инструментов .NET Framework необходимо правильно настроить переменные среды `Path`, `Include` и `Lib`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-109">For .NET Framework tools to function properly, you must set your `Path`, `Include`, and `Lib` environment variables correctly.</span></span> <span data-ttu-id="dd0b1-110">Эти переменные среды устанавливаются с помощью программы SDKVars.bat, расположенной в каталоге \<SDK>\\\<version>\Bin.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-110">Set these environment variables by running SDKVars.bat, which is located in the \<SDK>\\\<version>\Bin directory.</span></span> <span data-ttu-id="dd0b1-111">Программу SDKVars.bat следует выполнять в каждой командной оболочке.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-111">SDKVars.bat must be executed in every command shell.</span></span>

## <a name="argument"></a><span data-ttu-id="dd0b1-112">Аргумент</span><span class="sxs-lookup"><span data-stu-id="dd0b1-112">Argument</span></span>

|<span data-ttu-id="dd0b1-113">Аргумент</span><span class="sxs-lookup"><span data-stu-id="dd0b1-113">Argument</span></span>|<span data-ttu-id="dd0b1-114">Описание</span><span class="sxs-lookup"><span data-stu-id="dd0b1-114">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="dd0b1-115">*file.extension*</span><span class="sxs-lookup"><span data-stu-id="dd0b1-115">*file.extension*</span></span>|<span data-ttu-id="dd0b1-116">Задает входной файл, который необходимо преобразовать.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-116">Specifies the input file to convert.</span></span> <span data-ttu-id="dd0b1-117">Следует указать одно из следующих расширений: XDR, XML, XSD, DLL или EXE.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-117">You must specify the extension as one of the following: .xdr, .xml, .xsd, .dll, or .exe.</span></span><br /><br /> <span data-ttu-id="dd0b1-118">Если указать файл схемы XDR (расширение XDR), Xsd.exe преобразует схему XDR в схему XSD.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-118">If you specify an XDR schema file (.xdr extension), Xsd.exe converts the XDR schema to an XSD schema.</span></span> <span data-ttu-id="dd0b1-119">Имя выходного файла аналогично имени схемы XDR, но имеет расширение XSD.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-119">The output file has the same name as the XDR schema, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="dd0b1-120">Если указать XML-файл (расширение XML), Xsd.exe определяет схему по данным в файле и создает схему XSD.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-120">If you specify an XML file (.xml extension), Xsd.exe infers a schema from the data in the file and produces an XSD schema.</span></span> <span data-ttu-id="dd0b1-121">Имя выходного файла аналогично имени XML-файла, но имеет расширение XSD.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-121">The output file has the same name as the XML file, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="dd0b1-122">Если указать файл схемы XML (расширение XSD), Xsd.exe создает исходный код для объектов среды выполнения, соответствующих схеме XML.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-122">If you specify an XML schema file (.xsd extension), Xsd.exe generates source code for runtime objects that correspond to the XML schema.</span></span><br /><br /> <span data-ttu-id="dd0b1-123">Если указать файл сборки среды выполнения (расширение EXE или DLL), Xsd.exe создает схемы для одного или нескольких типов в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-123">If you specify a runtime assembly file (.exe or .dll extension), Xsd.exe generates schemas for one or more types in that assembly.</span></span> <span data-ttu-id="dd0b1-124">Чтобы указать типы, для которых необходимо создать схемы, можно использовать параметр `/type`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-124">You can use the `/type` option to specify the types for which to generate schemas.</span></span> <span data-ttu-id="dd0b1-125">Выходным схемам присваиваются имена schema0.xsd, schema1.xsd и т. д.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-125">The output schemas are named schema0.xsd, schema1.xsd, and so on.</span></span> <span data-ttu-id="dd0b1-126">Xsd.exe создает несколько схем, только если указанные типы задают пространство имен с использованием настраиваемого атрибута `XMLRoot`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-126">Xsd.exe produces multiple schemas only if the given types specify a namespace using the `XMLRoot` custom attribute.</span></span>|

## <a name="general-options"></a><span data-ttu-id="dd0b1-127">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="dd0b1-127">General Options</span></span>

|<span data-ttu-id="dd0b1-128">Параметр</span><span class="sxs-lookup"><span data-stu-id="dd0b1-128">Option</span></span>|<span data-ttu-id="dd0b1-129">Описание</span><span class="sxs-lookup"><span data-stu-id="dd0b1-129">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="dd0b1-130">**/h\[elp\]**</span><span class="sxs-lookup"><span data-stu-id="dd0b1-130">**/h\[elp\]**</span></span>|<span data-ttu-id="dd0b1-131">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-131">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="dd0b1-132">**/o\[utputdir\]:** _directory_</span><span class="sxs-lookup"><span data-stu-id="dd0b1-132">**/o\[utputdir\]:**_directory_</span></span>|<span data-ttu-id="dd0b1-133">Задает каталог выходных файлов.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-133">Specifies the directory for output files.</span></span> <span data-ttu-id="dd0b1-134">Этот аргумент отображается только один раз.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-134">This argument can appear only once.</span></span> <span data-ttu-id="dd0b1-135">Значением по умолчанию является текущий каталог.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-135">The default is the current directory.</span></span>|
|<span data-ttu-id="dd0b1-136">**/?**</span><span class="sxs-lookup"><span data-stu-id="dd0b1-136">**/?**</span></span>|<span data-ttu-id="dd0b1-137">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-137">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="dd0b1-138">**/p\[arameters\]:** _file.xml_</span><span class="sxs-lookup"><span data-stu-id="dd0b1-138">**/p\[arameters\]:**_file.xml_</span></span>|<span data-ttu-id="dd0b1-139">Считывает параметры различных режимов операций из указанного XML-файла.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-139">Read options for various operation modes from the specified .xml file.</span></span> <span data-ttu-id="dd0b1-140">Краткая форма: `/p:`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-140">The short form is `/p:`.</span></span> <span data-ttu-id="dd0b1-141">Дополнительные сведения см. в разделе [Примечания](#remarks).</span><span class="sxs-lookup"><span data-stu-id="dd0b1-141">For more information, see the [Remarks](#remarks) section.</span></span>|

## <a name="xsd-file-options"></a><span data-ttu-id="dd0b1-142">Параметры файла XSD</span><span class="sxs-lookup"><span data-stu-id="dd0b1-142">XSD File Options</span></span>

 <span data-ttu-id="dd0b1-143">Для файлов XSD следует указать только один из следующих параметров.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-143">You must specify only one of the following options for .xsd files.</span></span>

|<span data-ttu-id="dd0b1-144">Параметр</span><span class="sxs-lookup"><span data-stu-id="dd0b1-144">Option</span></span>|<span data-ttu-id="dd0b1-145">Описание</span><span class="sxs-lookup"><span data-stu-id="dd0b1-145">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="dd0b1-146">**/c\[lasses\]**</span><span class="sxs-lookup"><span data-stu-id="dd0b1-146">**/c\[lasses\]**</span></span>|<span data-ttu-id="dd0b1-147">Создает классы, соответствующие указанной схеме.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-147">Generates classes that correspond to the specified schema.</span></span> <span data-ttu-id="dd0b1-148">Чтобы считать данные XML в объект, используйте метод <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-148">To read XML data into the object, use the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>|
|<span data-ttu-id="dd0b1-149">**/d\[ataset\]**</span><span class="sxs-lookup"><span data-stu-id="dd0b1-149">**/d\[ataset\]**</span></span>|<span data-ttu-id="dd0b1-150">Создает классы, которые являются производными класса <xref:System.Data.DataSet> и соответствуют указанной схеме.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-150">Generates a class derived from <xref:System.Data.DataSet> that corresponds to the specified schema.</span></span> <span data-ttu-id="dd0b1-151">Чтобы считать данные XML в производный класс, используйте метод <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-151">To read XML data into the derived class, use the <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType> method.</span></span>|

 <span data-ttu-id="dd0b1-152">Для файлов XSD также можно указать любой из следующих параметров.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-152">You can also specify any of the following options for .xsd files.</span></span>

|<span data-ttu-id="dd0b1-153">Параметр</span><span class="sxs-lookup"><span data-stu-id="dd0b1-153">Option</span></span>|<span data-ttu-id="dd0b1-154">Описание</span><span class="sxs-lookup"><span data-stu-id="dd0b1-154">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="dd0b1-155">**/e\[lement\]:** _элемент_</span><span class="sxs-lookup"><span data-stu-id="dd0b1-155">**/e\[lement\]:**_element_</span></span>|<span data-ttu-id="dd0b1-156">Определяет элемент в схеме, для которого создается код.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-156">Specifies the element in the schema to generate code for.</span></span> <span data-ttu-id="dd0b1-157">По умолчанию все элементы имеют тип.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-157">By default all elements are typed.</span></span> <span data-ttu-id="dd0b1-158">Этот аргумент можно задать несколько раз.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-158">You can specify this argument more than once.</span></span>|
|<span data-ttu-id="dd0b1-159">**/enableDataBinding**</span><span class="sxs-lookup"><span data-stu-id="dd0b1-159">**/enableDataBinding**</span></span>|<span data-ttu-id="dd0b1-160">Реализует интерфейс <xref:System.ComponentModel.INotifyPropertyChanged> для всех созданных типов для обеспечения привязки данных.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-160">Implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface on all generated types to enable data binding.</span></span> <span data-ttu-id="dd0b1-161">Краткая форма: `/edb`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-161">The short form is `/edb`.</span></span>|
|<span data-ttu-id="dd0b1-162">**/enableLinqDataSet**</span><span class="sxs-lookup"><span data-stu-id="dd0b1-162">**/enableLinqDataSet**</span></span>|<span data-ttu-id="dd0b1-163">(Сокращенная форма: `/eld`.) Указывает, что созданный набор данных можно запросить с помощью LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-163">(Short form: `/eld`.) Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="dd0b1-164">Этот параметр используется только при указании параметра /dataset.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-164">This option is used when the /dataset option is also specified.</span></span> <span data-ttu-id="dd0b1-165">Дополнительные сведения см. в разделах [Общие сведения о LINQ to DataSet](../../framework/data/adonet/linq-to-dataset-overview.md) и [Запрос к типизированным объектам DataSet](../../framework/data/adonet/querying-typed-datasets.md).</span><span class="sxs-lookup"><span data-stu-id="dd0b1-165">For more information, see [LINQ to DataSet Overview](../../framework/data/adonet/linq-to-dataset-overview.md) and [Querying Typed DataSets](../../framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="dd0b1-166">Общие сведения об использовании LINQ см. в разделе [LINQ — C#](../../csharp/programming-guide/concepts/linq/index.md) или [LINQ — Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="dd0b1-166">For general information about using LINQ, see [Language-Integrated Query (LINQ) - C#](../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>|
|<span data-ttu-id="dd0b1-167">**/f\[ields\]**</span><span class="sxs-lookup"><span data-stu-id="dd0b1-167">**/f\[ields\]**</span></span>|<span data-ttu-id="dd0b1-168">Создает поля вместо свойств.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-168">Generates fields instead of properties.</span></span> <span data-ttu-id="dd0b1-169">По умолчанию создаются свойства.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-169">By default, properties are generated.</span></span>|
|<span data-ttu-id="dd0b1-170">**/l\[anguage\]:** _язык_</span><span class="sxs-lookup"><span data-stu-id="dd0b1-170">**/l\[anguage\]:**_language_</span></span>|<span data-ttu-id="dd0b1-171">Задает используемый язык программирования.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-171">Specifies the programming language to use.</span></span> <span data-ttu-id="dd0b1-172">Доступный выбор: `CS` (C#, по умолчанию), `VB` (Visual Basic), `JS` (JScript) или `VJS` (Visual J#).</span><span class="sxs-lookup"><span data-stu-id="dd0b1-172">Choose from `CS` (C#, which is the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="dd0b1-173">Также можно указать полное имя класса, реализующего <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="dd0b1-173">You can also specify a fully qualified name for a class implementing <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType></span></span>|
|<span data-ttu-id="dd0b1-174">**/n\[amespace\]:** _пространство_имен_</span><span class="sxs-lookup"><span data-stu-id="dd0b1-174">**/n\[amespace\]:**_namespace_</span></span>|<span data-ttu-id="dd0b1-175">Определяет пространство имен среды выполнения для создаваемых типов.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-175">Specifies the runtime namespace for the generated types.</span></span> <span data-ttu-id="dd0b1-176">Пространство имен по умолчанию — `Schemas`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-176">The default namespace is `Schemas`.</span></span>|
|<span data-ttu-id="dd0b1-177">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="dd0b1-177">**/nologo**</span></span>|<span data-ttu-id="dd0b1-178">Отключает баннер.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-178">Suppresses the banner.</span></span>|
|<span data-ttu-id="dd0b1-179">**/order**</span><span class="sxs-lookup"><span data-stu-id="dd0b1-179">**/order**</span></span>|<span data-ttu-id="dd0b1-180">Создает явные идентификаторы порядка для всех примитивных членов.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-180">Generates explicit order identifiers on all particle members.</span></span>|
|<span data-ttu-id="dd0b1-181">**/o\[ut\]:** _имя_каталога_</span><span class="sxs-lookup"><span data-stu-id="dd0b1-181">**/o\[ut\]:**_directoryName_</span></span>|<span data-ttu-id="dd0b1-182">Задает выходной каталог, в котором следует разместить файлы.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-182">Specifies the output directory to place the files in.</span></span> <span data-ttu-id="dd0b1-183">Значением по умолчанию является текущий каталог.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-183">The default is the current directory.</span></span>|
|<span data-ttu-id="dd0b1-184">**/u\[ri\]:** _URI_</span><span class="sxs-lookup"><span data-stu-id="dd0b1-184">**/u\[ri\]:**_uri_</span></span>|<span data-ttu-id="dd0b1-185">Определяет универсальный код ресурса (URI) для элементов схемы, для которого создается код.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-185">Specifies the URI for the elements in the schema to generate code for.</span></span> <span data-ttu-id="dd0b1-186">Этот универсальный код ресурса, если имеется, применяется ко всем элементам, заданным параметром `/element`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-186">This URI, if present, applies to all elements specified with the `/element` option.</span></span>|

## <a name="dll-and-exe-file-options"></a><span data-ttu-id="dd0b1-187">Параметры файлов DLL и EXE</span><span class="sxs-lookup"><span data-stu-id="dd0b1-187">DLL and EXE File Options</span></span>

|<span data-ttu-id="dd0b1-188">Параметр</span><span class="sxs-lookup"><span data-stu-id="dd0b1-188">Option</span></span>|<span data-ttu-id="dd0b1-189">Описание</span><span class="sxs-lookup"><span data-stu-id="dd0b1-189">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="dd0b1-190">**/t\[ype\]:** _имя_типа_</span><span class="sxs-lookup"><span data-stu-id="dd0b1-190">**/t\[ype\]:**_typename_</span></span>|<span data-ttu-id="dd0b1-191">Задает имя типа, для которого следует создать схему.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-191">Specifies the name of the type to create a schema for.</span></span> <span data-ttu-id="dd0b1-192">Можно указать несколько аргументов типа.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-192">You can specify multiple type arguments.</span></span> <span data-ttu-id="dd0b1-193">Если *имя_типа* не указывает пространство имен, Xsd.exe сопоставляет все типы в сборке с указанным типом.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-193">If *typename* does not specify a namespace, Xsd.exe matches all types in the assembly with the specified type.</span></span> <span data-ttu-id="dd0b1-194">Если *имя_типа* задает пространство имен, сопоставляется только этот тип.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-194">If *typename* specifies a namespace, only that type is matched.</span></span> <span data-ttu-id="dd0b1-195">Если *имя_типа* заканчивается знаком звездочки (\*), средство сопоставляет все типы, которые начинаются со строки, предшествующей знаку звездочки (\*).</span><span class="sxs-lookup"><span data-stu-id="dd0b1-195">If *typename* ends with an asterisk character (\*), the tool matches all types that start with the string preceding the \*.</span></span> <span data-ttu-id="dd0b1-196">Если параметр `/type` не задан, Xsd.exe создает схемы для всех типов в сборке.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-196">If you omit the `/type` option, Xsd.exe generates schemas for all types in the assembly.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dd0b1-197">Примечания</span><span class="sxs-lookup"><span data-stu-id="dd0b1-197">Remarks</span></span>

<span data-ttu-id="dd0b1-198">В следующей таблице показаны операции, выполняемые Xsd.exe.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-198">The following table shows the operations that Xsd.exe performs.</span></span>

| | |
|------------|-----------------|
|<span data-ttu-id="dd0b1-199">XDR в XSD</span><span class="sxs-lookup"><span data-stu-id="dd0b1-199">XDR to XSD</span></span>|<span data-ttu-id="dd0b1-200">Создает схему XML из файла схемы XDR.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-200">Generates an XML schema from an XML-Data-Reduced schema file.</span></span> <span data-ttu-id="dd0b1-201">XDR является более ранним форматом схемы, основанной на XML.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-201">XDR is an early XML-based schema format.</span></span>|
|<span data-ttu-id="dd0b1-202">XML в XSD</span><span class="sxs-lookup"><span data-stu-id="dd0b1-202">XML to XSD</span></span>|<span data-ttu-id="dd0b1-203">Создает схему XML из XML-файла.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-203">Generates an XML schema from an XML file.</span></span>|
|<span data-ttu-id="dd0b1-204">XSD в DataSet</span><span class="sxs-lookup"><span data-stu-id="dd0b1-204">XSD to DataSet</span></span>|<span data-ttu-id="dd0b1-205">Создает классы CLR <xref:System.Data.DataSet> из файла схемы XSD.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-205">Generates common language runtime <xref:System.Data.DataSet> classes from an XSD schema file.</span></span> <span data-ttu-id="dd0b1-206">Создаваемые классы представляют собой объектную модель с широкими функциональными возможностями для обычных данных XML.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-206">The generated classes provide a rich object model for regular XML data.</span></span>|
|<span data-ttu-id="dd0b1-207">XSD в классы</span><span class="sxs-lookup"><span data-stu-id="dd0b1-207">XSD to Classes</span></span>|<span data-ttu-id="dd0b1-208">Создает классы среды выполнения из файла схемы XSD.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-208">Generates runtime classes from an XSD schema file.</span></span> <span data-ttu-id="dd0b1-209">Созданные классы можно использовать совместно с <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> для чтения и записи кода XML, соответствующего схеме.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-209">The generated classes can be used in conjunction with <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> to read and write XML code that follows the schema.</span></span>|
|<span data-ttu-id="dd0b1-210">Классы в XSD</span><span class="sxs-lookup"><span data-stu-id="dd0b1-210">Classes to XSD</span></span>| <span data-ttu-id="dd0b1-211">Создает схему XML из типа или типов в файле сборки среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-211">Generates an XML schema from a type or types in a runtime assembly file.</span></span> <span data-ttu-id="dd0b1-212">Созданная схема определяет формат XML, используемый <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-212">The generated schema defines the XML format used by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|

 <span data-ttu-id="dd0b1-213">Xsd.exe позволяет управлять только схемами XML, которые соответствуют языку определения схемы XML (XSD), предложенному консорциумом World Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="dd0b1-213">Xsd.exe only allows you to manipulate XML schemas that follow the XML Schema Definition (XSD) language proposed by the World Wide Web Consortium (W3C).</span></span> <span data-ttu-id="dd0b1-214">Дополнительные сведения о предложенном определении схемы XML или стандарте XML см. в <https://w3.org>.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-214">For more information on the XML Schema Definition proposal or the XML standard, see <https://w3.org>.</span></span>

## <a name="setting-options-with-an-xml-file"></a><span data-ttu-id="dd0b1-215">Установка параметров с помощью XML-файла</span><span class="sxs-lookup"><span data-stu-id="dd0b1-215">Setting Options with an XML File</span></span>

<span data-ttu-id="dd0b1-216">С помощью параметра `/parameters` можно задать один XML-файл, который содержит различные параметры.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-216">By using the `/parameters` switch, you can specify a single XML file that sets various options.</span></span> <span data-ttu-id="dd0b1-217">Задаваемые параметры зависят от способа использования инструмента XSD.exe.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-217">The options you can set depend on how you are using the XSD.exe tool.</span></span> <span data-ttu-id="dd0b1-218">Варианты включают в себя создание схем, файлов кода или создание файлов кода, содержащих функции `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-218">Choices include generating schemas, generating code files, or generating code files that include `DataSet` features.</span></span> <span data-ttu-id="dd0b1-219">Например, можно задать элемент `<assembly>` как имя исполняемого файла (расширение EXE) или файла библиотеки типов (расширение DLL) при создании схемы, но не при создании файла кода.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-219">For example, you can set the `<assembly>` element to the name of an executable (.exe) or type library (.dll) file when generating a schema, but not when generating a code file.</span></span> <span data-ttu-id="dd0b1-220">В следующем примере XML показано, как использовать элемент `<generateSchemas>` с указанным исполняемым файлом:</span><span class="sxs-lookup"><span data-stu-id="dd0b1-220">The following XML shows how to use the `<generateSchemas>` element with a specified executable:</span></span>

```xml
<!-- This is in a file named GenerateSchemas.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <assembly>ConsoleApplication1.exe</assembly>
</generateSchemas>
</xsd>
```

<span data-ttu-id="dd0b1-221">Если предыдущий XML содержится в файле с именем GenerateSchemas.xml, используйте параметр `/parameters`, введя следующий текст в командной строке и нажав клавишу **ВВОД**:</span><span class="sxs-lookup"><span data-stu-id="dd0b1-221">If the preceding XML is contained in a file named GenerateSchemas.xml, then use the `/parameters` switch by typing the following at a command prompt and pressing **Enter**:</span></span>

```console
 xsd /p:GenerateSchemas.xml
```

<span data-ttu-id="dd0b1-222">С другой стороны, при создании схемы для одного типа, найденного в сборке, можно использовать следующий XML:</span><span class="sxs-lookup"><span data-stu-id="dd0b1-222">On the other hand, if you are generating a schema for a single type found in the assembly, you can use the following XML:</span></span>

```xml
<!-- This is in a file named GenerateSchemaFromType.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <type>IDItems</type>
</generateSchemas>
</xsd>
```

<span data-ttu-id="dd0b1-223">Но чтобы использовать предыдущий код, в командной строке следует также указать имя сборки.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-223">But to use preceding code, you must also supply the name of the assembly at the command prompt.</span></span> <span data-ttu-id="dd0b1-224">В командной строке введите следующую команду (допустим, имя XML-файла — GenerateSchemaFromType.xml):</span><span class="sxs-lookup"><span data-stu-id="dd0b1-224">Enter the following at a command prompt (presuming the XML file is named GenerateSchemaFromType.xml):</span></span>

```console
xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe
```

<span data-ttu-id="dd0b1-225">Для элемента `<generateSchemas>` следует указать только один из следующих параметров.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-225">You must specify only one of the following options for the `<generateSchemas>` element.</span></span>

|<span data-ttu-id="dd0b1-226">Элемент</span><span class="sxs-lookup"><span data-stu-id="dd0b1-226">Element</span></span>|<span data-ttu-id="dd0b1-227">Описание</span><span class="sxs-lookup"><span data-stu-id="dd0b1-227">Description</span></span>|
|-------------|-----------------|
|\<assembly>|<span data-ttu-id="dd0b1-228">Определяет сборку, из которой создается схема.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-228">Specifies an assembly to generate the schema from.</span></span>|
|\<type>|<span data-ttu-id="dd0b1-229">Определяет тип, найденный в сборке, для которого создается схема.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-229">Specifies a type found in an assembly to generate a schema for.</span></span>|
|\<xml>|<span data-ttu-id="dd0b1-230">Задает XML-файл, для которого создается схема.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-230">Specifies an XML file to generate a schema for.</span></span>|
|\<xdr>|<span data-ttu-id="dd0b1-231">Определяет файл XDR, для которого создается схема.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-231">Specifies an XDR file to generate a schema for.</span></span>|

<span data-ttu-id="dd0b1-232">Чтобы создать файл кода, используйте элемент `<generateClasses>`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-232">To generate a code file, use the `<generateClasses>` element.</span></span> <span data-ttu-id="dd0b1-233">В следующем примере создается файл кода.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-233">The following example generates a code file.</span></span> <span data-ttu-id="dd0b1-234">Обратите внимание, что также отображаются два атрибута, с помощью которых можно задать язык программирования и пространство имен создаваемого файла.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-234">Note that two attributes are also shown that allow you to set the programming language and namespace of the generated file.</span></span>

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>
</xsd>
<!-- You must supply an .xsd file when typing in the command line.-->
<!-- For example: xsd /p:genClasses mySchema.xsd -->
```

 <span data-ttu-id="dd0b1-235">Параметры, которые можно задать для элемента `<generateClasses>`, включают в себя следующие.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-235">Options you can set for the `<generateClasses>` element include the following.</span></span>

|<span data-ttu-id="dd0b1-236">Элемент</span><span class="sxs-lookup"><span data-stu-id="dd0b1-236">Element</span></span>|<span data-ttu-id="dd0b1-237">Описание</span><span class="sxs-lookup"><span data-stu-id="dd0b1-237">Description</span></span>|
|-------------|-----------------|
|\<element>|<span data-ttu-id="dd0b1-238">Определяет элемент в файле XSD, для которого создается код.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-238">Specifies an element in the .xsd file to generate code for.</span></span>|
|\<schemaImporterExtensions>|<span data-ttu-id="dd0b1-239">Определяет тип, унаследованный от класса <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-239">Specifies a type derived from the <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> class.</span></span>|
|\<schema>|<span data-ttu-id="dd0b1-240">Определяет файл схемы XML, для которой создается код.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-240">Specifies a XML Schema file to generate code for.</span></span> <span data-ttu-id="dd0b1-241">С помощью нескольких элементов \<schema> можно задать несколько файлов схемы XML.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-241">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|

<span data-ttu-id="dd0b1-242">В следующей таблице представлены атрибуты, которые также можно использовать с элементом `<generateClasses>`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-242">The following table shows the attributes that can also be used with the `<generateClasses>` element.</span></span>

|<span data-ttu-id="dd0b1-243">Атрибут</span><span class="sxs-lookup"><span data-stu-id="dd0b1-243">Attribute</span></span>|<span data-ttu-id="dd0b1-244">Описание</span><span class="sxs-lookup"><span data-stu-id="dd0b1-244">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="dd0b1-245">язык</span><span class="sxs-lookup"><span data-stu-id="dd0b1-245">language</span></span>|<span data-ttu-id="dd0b1-246">Задает используемый язык программирования.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-246">Specifies the programming language to use.</span></span> <span data-ttu-id="dd0b1-247">Доступный выбор: `CS` (C#, по умолчанию), `VB` (Visual Basic), `JS` (JScript) или `VJS` (Visual J#).</span><span class="sxs-lookup"><span data-stu-id="dd0b1-247">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="dd0b1-248">Также можно указать полное имя класса, реализующего <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-248">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|
|<span data-ttu-id="dd0b1-249">namespace</span><span class="sxs-lookup"><span data-stu-id="dd0b1-249">namespace</span></span>|<span data-ttu-id="dd0b1-250">Задает пространство имен созданного кода.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-250">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="dd0b1-251">Пространство имен должно соответствовать стандартам CLR (например, отсутствие пробелов или обратной косой черты).</span><span class="sxs-lookup"><span data-stu-id="dd0b1-251">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|
|<span data-ttu-id="dd0b1-252">options</span><span class="sxs-lookup"><span data-stu-id="dd0b1-252">options</span></span>|<span data-ttu-id="dd0b1-253">Одно из следующих значений: `none`, `properties` (создает свойства вместо открытых полей), `order` или `enableDataBinding` (см. параметры `/order` и `/enableDataBinding` в предыдущем разделе параметров файла XSD).</span><span class="sxs-lookup"><span data-stu-id="dd0b1-253">One of the following values: `none`, `properties` (generates properties instead of public fields), `order`, or `enableDataBinding` (see the `/order` and `/enableDataBinding` switches in the preceding XSD File Options section.</span></span>|

 <span data-ttu-id="dd0b1-254">Также предусмотрена возможность управления созданием кода `DataSet` с использованием элемента `<generateDataSet>`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-254">You can also control how `DataSet` code is generated by using the `<generateDataSet>` element.</span></span> <span data-ttu-id="dd0b1-255">Приведенный ниже XML-код указывает, что созданный код использует структуры `DataSet` (например, класс <xref:System.Data.DataTable>), чтобы создать код Visual Basic для указанного элемента.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-255">The following XML specifies that the generated code uses `DataSet` structures (such as the <xref:System.Data.DataTable> class) to create Visual Basic code for a specified element.</span></span> <span data-ttu-id="dd0b1-256">Созданные структуры DataSet поддерживают запросы LINQ.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-256">The generated DataSet structures will support LINQ queries.</span></span>

 ```xml
 <xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
     <generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>
     </generateDataSet>
 </xsd>
```

<span data-ttu-id="dd0b1-257">Параметры, которые можно задать для элемента `<generateDataSet>`, включают в себя следующие.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-257">Options you can set for the `<generateDataSet>` element include the following.</span></span>

|<span data-ttu-id="dd0b1-258">Элемент</span><span class="sxs-lookup"><span data-stu-id="dd0b1-258">Element</span></span>|<span data-ttu-id="dd0b1-259">Описание</span><span class="sxs-lookup"><span data-stu-id="dd0b1-259">Description</span></span>|
|-------------|-----------------|
|\<schema>|<span data-ttu-id="dd0b1-260">Определяет файл схемы XML, для которой создается код.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-260">Specifies an XML Schema file to generate code for.</span></span> <span data-ttu-id="dd0b1-261">С помощью нескольких элементов \<schema> можно задать несколько файлов схемы XML.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-261">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|

 <span data-ttu-id="dd0b1-262">В следующей таблице представлены атрибуты, которые можно использовать с элементом `<generateDataSet>`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-262">The following table shows the attributes that can be used with the `<generateDataSet>` element.</span></span>

|<span data-ttu-id="dd0b1-263">Атрибут</span><span class="sxs-lookup"><span data-stu-id="dd0b1-263">Attribute</span></span>|<span data-ttu-id="dd0b1-264">Описание</span><span class="sxs-lookup"><span data-stu-id="dd0b1-264">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="dd0b1-265">enableLinqDataSet</span><span class="sxs-lookup"><span data-stu-id="dd0b1-265">enableLinqDataSet</span></span>|<span data-ttu-id="dd0b1-266">Указывает, что созданный набор данных можно запросить с помощью LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-266">Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="dd0b1-267">Значением по умолчанию является false.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-267">The default value is false.</span></span>|
|<span data-ttu-id="dd0b1-268">язык</span><span class="sxs-lookup"><span data-stu-id="dd0b1-268">language</span></span>|<span data-ttu-id="dd0b1-269">Задает используемый язык программирования.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-269">Specifies the programming language to use.</span></span> <span data-ttu-id="dd0b1-270">Доступный выбор: `CS` (C#, по умолчанию), `VB` (Visual Basic), `JS` (JScript) или `VJS` (Visual J#).</span><span class="sxs-lookup"><span data-stu-id="dd0b1-270">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="dd0b1-271">Также можно указать полное имя класса, реализующего <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-271">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|
|<span data-ttu-id="dd0b1-272">namespace</span><span class="sxs-lookup"><span data-stu-id="dd0b1-272">namespace</span></span>|<span data-ttu-id="dd0b1-273">Задает пространство имен созданного кода.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-273">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="dd0b1-274">Пространство имен должно соответствовать стандартам CLR (например, отсутствие пробелов или обратной косой черты).</span><span class="sxs-lookup"><span data-stu-id="dd0b1-274">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|

 <span data-ttu-id="dd0b1-275">Существуют атрибуты, которые можно задать для элемента верхнего уровня `<xsd>`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-275">There are attributes that you can set on the top level `<xsd>` element.</span></span> <span data-ttu-id="dd0b1-276">Эти параметры можно использовать с любым из дочерних элементов (`<generateSchemas>`, `<generateClasses>` или `<generateDataSet>`).</span><span class="sxs-lookup"><span data-stu-id="dd0b1-276">These options can be used with any of the child elements (`<generateSchemas>`, `<generateClasses>` or `<generateDataSet>`).</span></span> <span data-ttu-id="dd0b1-277">Следующий код XML создает код для элемента с именем "IDItems" в выходном каталоге с именем "MyOutputDirectory".</span><span class="sxs-lookup"><span data-stu-id="dd0b1-277">The following XML code generates code for an element named "IDItems" in the output directory named "MyOutputDirectory".</span></span>

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>
<generateClasses>
    <element>IDItems</element>
</generateClasses>
</xsd>
```

<span data-ttu-id="dd0b1-278">В следующей таблице представлены атрибуты, которые также можно использовать с элементом `<xsd>`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-278">The following table shows the attributes that can also be used with the `<xsd>` element.</span></span>

|<span data-ttu-id="dd0b1-279">Атрибут</span><span class="sxs-lookup"><span data-stu-id="dd0b1-279">Attribute</span></span>|<span data-ttu-id="dd0b1-280">Описание</span><span class="sxs-lookup"><span data-stu-id="dd0b1-280">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="dd0b1-281">output</span><span class="sxs-lookup"><span data-stu-id="dd0b1-281">output</span></span>|<span data-ttu-id="dd0b1-282">Имя каталога, в который сохраняется созданная схема или файл кода.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-282">The name of a directory where the generated schema or code file will be placed.</span></span>|
|<span data-ttu-id="dd0b1-283">nologo</span><span class="sxs-lookup"><span data-stu-id="dd0b1-283">nologo</span></span>|<span data-ttu-id="dd0b1-284">Отключает баннер.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-284">Suppresses the banner.</span></span> <span data-ttu-id="dd0b1-285">Задайте `true` или `false`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-285">Set to `true` or `false`.</span></span>|
|<span data-ttu-id="dd0b1-286">help</span><span class="sxs-lookup"><span data-stu-id="dd0b1-286">help</span></span>|<span data-ttu-id="dd0b1-287">Отображает синтаксис команд и параметров программы.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-287">Displays command syntax and options for the tool.</span></span> <span data-ttu-id="dd0b1-288">Задайте `true` или `false`.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-288">Set to `true` or `false`.</span></span>|

## <a name="examples"></a><span data-ttu-id="dd0b1-289">Примеры</span><span class="sxs-lookup"><span data-stu-id="dd0b1-289">Examples</span></span>

 <span data-ttu-id="dd0b1-290">Следующая команда создает схему XML из `myFile.xdr` и сохраняет ее в текущий каталог.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-290">The following command generates an XML schema from `myFile.xdr` and saves it to the current directory.</span></span>

```console
xsd myFile.xdr
```

<span data-ttu-id="dd0b1-291">Следующая команда создает схему XML из `myFile.xml` и сохраняет ее в указанный каталог.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-291">The following command generates an XML schema from `myFile.xml` and saves it to the specified directory.</span></span>

```console
xsd myFile.xml /outputdir:myOutputDir
```

<span data-ttu-id="dd0b1-292">Следующая команда создает набор данных, соответствующий определенной схеме на языке C# и сохраняет его как `XSDSchemaFile.cs` в текущий каталог.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-292">The following command generates a data set that corresponds to the specified schema in the C# language and saves it as `XSDSchemaFile.cs` in the current directory.</span></span>

```console
xsd /dataset /language:CS XSDSchemaFile.xsd
```

<span data-ttu-id="dd0b1-293">Следующая команда создает схемы XML для всех типов в сборке `myAssembly.dll` и сохраняет их как `schema0.xsd` в текущий каталог.</span><span class="sxs-lookup"><span data-stu-id="dd0b1-293">The following command generates XML schemas for all types in the assembly `myAssembly.dll` and saves them as `schema0.xsd` in the current directory.</span></span>

```console
xsd myAssembly.dll
```

## <a name="see-also"></a><span data-ttu-id="dd0b1-294">См. также</span><span class="sxs-lookup"><span data-stu-id="dd0b1-294">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
- [<span data-ttu-id="dd0b1-295">Инструменты</span><span class="sxs-lookup"><span data-stu-id="dd0b1-295">Tools</span></span>](../../framework/tools/index.md)
- [<span data-ttu-id="dd0b1-296">Командные строки</span><span class="sxs-lookup"><span data-stu-id="dd0b1-296">Command Prompts</span></span>](../../framework/tools/developer-command-prompt-for-vs.md)
- [<span data-ttu-id="dd0b1-297">Общие сведения о LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="dd0b1-297">LINQ to DataSet Overview</span></span>](../../framework/data/adonet/linq-to-dataset-overview.md)
- [<span data-ttu-id="dd0b1-298">Запрос к типизированным объектам DataSet</span><span class="sxs-lookup"><span data-stu-id="dd0b1-298">Querying Typed DataSets</span></span>](../../framework/data/adonet/querying-typed-datasets.md)
- [<span data-ttu-id="dd0b1-299">Встроенный язык запросов LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="dd0b1-299">LINQ (Language-Integrated Query) (C#)</span></span>](../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="dd0b1-300">Встроенный язык запросов LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd0b1-300">LINQ (Language-Integrated Query) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)
