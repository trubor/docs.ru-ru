---
title: Средство анализа композиции (Mefx)
description: Сведения о средстве анализа композиции (Mefx), которое анализирует файлы DLL и EXE, содержащие части Managed Extensibility Framework (MEF), в .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- Composition Analysis Tool [MEF]
- MEF, Composition Analysis Tool
- Mefx [MEF], Composition Analysis Tool
ms.assetid: c48a7f93-83bb-4a06-aea0-d8e7bd1502ad
ms.openlocfilehash: d3f3a282cfa9274a1939d312987dd58b24eab2af
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255797"
---
# <a name="composition-analysis-tool-mefx"></a><span data-ttu-id="0681e-103">Средство анализа композиции (Mefx)</span><span class="sxs-lookup"><span data-stu-id="0681e-103">Composition Analysis Tool (Mefx)</span></span>

<span data-ttu-id="0681e-104">Средство анализа композиции (Mefx) — это приложение командной строки, анализирующее файлы библиотеки (.dll) и приложений (.exe) с частями Managed Extensibility Framework (MEF).</span><span class="sxs-lookup"><span data-stu-id="0681e-104">The Composition Analysis Tool (Mefx) is a command-line application that analyzes library (.dll) and application (.exe) files containing Managed Extensibility Framework (MEF) parts.</span></span> <span data-ttu-id="0681e-105">Основное назначение Mefx — предоставить разработчикам способ диагностики ошибок композиции в приложениях MEF, не добавляя громоздкий код трассировки в само приложение.</span><span class="sxs-lookup"><span data-stu-id="0681e-105">The primary purpose of Mefx is to provide developers a way to diagnose composition failures in their MEF applications without the requirement to add cumbersome tracing code to the application itself.</span></span> <span data-ttu-id="0681e-106">Это средство также помогает понять части из сторонней библиотеки.</span><span class="sxs-lookup"><span data-stu-id="0681e-106">It can also be useful to help understand parts from a library provided by a third party.</span></span> <span data-ttu-id="0681e-107">В этом разделе описывается использование Mefx, содержится справочная информация по его синтаксису.</span><span class="sxs-lookup"><span data-stu-id="0681e-107">This topic describes how to use Mefx and provides a reference for its syntax.</span></span>  
  
<a name="getting_mefx"></a>

## <a name="getting-mefx"></a><span data-ttu-id="0681e-108">Получение Mefx</span><span class="sxs-lookup"><span data-stu-id="0681e-108">Getting Mefx</span></span>  

 <span data-ttu-id="0681e-109">Средство Mefx доступно в GitHub по следующей ссылке: [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span><span class="sxs-lookup"><span data-stu-id="0681e-109">Mefx is available on GitHub at [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef/releases/tag/4.0).</span></span> <span data-ttu-id="0681e-110">Просто загрузите и распакуйте средство.</span><span class="sxs-lookup"><span data-stu-id="0681e-110">Simply download and unzip the tool.</span></span>  
  
<a name="basic_syntax"></a>

## <a name="basic-syntax"></a><span data-ttu-id="0681e-111">Базовый синтаксис</span><span class="sxs-lookup"><span data-stu-id="0681e-111">Basic Syntax</span></span>  

 <span data-ttu-id="0681e-112">Mefx вызывается из командной строки в следующем формате.</span><span class="sxs-lookup"><span data-stu-id="0681e-112">Mefx is invoked from the command line in the following format:</span></span>  
  
```console
mefx [files and directories] [action] [options]  
```  
  
 <span data-ttu-id="0681e-113">Первый набор аргументов обозначает файлы и каталоги, из которых требуется загрузить части для анализа.</span><span class="sxs-lookup"><span data-stu-id="0681e-113">The first set of arguments specify the files and directories from which to load parts for analysis.</span></span> <span data-ttu-id="0681e-114">Укажите файл с переключателем `/file:` и каталог с переключателем `/directory:` .</span><span class="sxs-lookup"><span data-stu-id="0681e-114">Specify a file with the `/file:` switch, and a directory with the `/directory:` switch.</span></span> <span data-ttu-id="0681e-115">Можно указать несколько файлов или каталогов, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="0681e-115">You can specify multiple files or directories, as shown in the following example:</span></span>  
  
```console  
mefx /file:MyAddIn.dll /directory:Program\AddIns [action...]  
```  
  
> [!NOTE]
> <span data-ttu-id="0681e-116">Каждый файл .dll или .exe следует загружать только один раз.</span><span class="sxs-lookup"><span data-stu-id="0681e-116">Each .dll or .exe should only be loaded one time.</span></span> <span data-ttu-id="0681e-117">Если файл загружается несколько раз, средство может вернуть неправильные данные.</span><span class="sxs-lookup"><span data-stu-id="0681e-117">If a file is loaded multiple times, the tool may return incorrect information.</span></span>  
  
 <span data-ttu-id="0681e-118">После списка файлов и каталогов необходимо указать команду и параметры для этой команды.</span><span class="sxs-lookup"><span data-stu-id="0681e-118">After the list of files and directories, you must specify a command, and any options for that command.</span></span>  
  
<a name="listing_available_parts"></a>

## <a name="listing-available-parts"></a><span data-ttu-id="0681e-119">Составление списка доступных частей</span><span class="sxs-lookup"><span data-stu-id="0681e-119">Listing Available Parts</span></span>  

 <span data-ttu-id="0681e-120">Используйте действие `/parts` , чтобы составить список всех частей, объявленных в загруженных файлах.</span><span class="sxs-lookup"><span data-stu-id="0681e-120">Use the `/parts` action to list all the parts declared in the files loaded.</span></span> <span data-ttu-id="0681e-121">Результатом является простой список имен частей.</span><span class="sxs-lookup"><span data-stu-id="0681e-121">The result is a simple list of part names.</span></span>  
  
```console
mefx /file:MyAddIn.dll /parts  
MyAddIn.AddIn  
MyAddIn.MemberPart  
```  
  
 <span data-ttu-id="0681e-122">Для получения дополнительных сведений о частях воспользуйтесь параметром `/verbose` .</span><span class="sxs-lookup"><span data-stu-id="0681e-122">For more information about the parts, use the `/verbose` option.</span></span> <span data-ttu-id="0681e-123">Это позволит вывести дополнительные сведения обо всех доступных частях.</span><span class="sxs-lookup"><span data-stu-id="0681e-123">This will output more information for all available parts.</span></span> <span data-ttu-id="0681e-124">Для получения дополнительной информации об определенной части воспользуйтесь действием `/type` , а не `/parts`.</span><span class="sxs-lookup"><span data-stu-id="0681e-124">To get more information about a single part, use the `/type` action instead of `/parts`.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /type:MyAddIn.AddIn /verbose  
[Part] MyAddIn.MemberPart from: AssemblyCatalog (Assembly=" MyAddIn, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] MyAddIn.MemberPart (ContractName=" MyAddIn.MemberPart")  
```  
  
<a name="listing_imports_and_exports"></a>

## <a name="listing-imports-and-exports"></a><span data-ttu-id="0681e-125">Составление списка импортируемых и экспортируемых элементов</span><span class="sxs-lookup"><span data-stu-id="0681e-125">Listing Imports and Exports</span></span>  

 <span data-ttu-id="0681e-126">Действия `/imports` и `/exports` позволяют перечислить все импортируемые и экспортируемые части соответственно.</span><span class="sxs-lookup"><span data-stu-id="0681e-126">The `/imports` and `/exports` actions will list all the imported parts and all the exported parts, respectively.</span></span> <span data-ttu-id="0681e-127">Также можно составить список частей, импортирующих или экспортирующих определенный тип, воспользовавшись действиями `/importers` или `/exporters` .</span><span class="sxs-lookup"><span data-stu-id="0681e-127">You can also list the parts that import or export a particular type by using the `/importers` or `/exporters` actions.</span></span>  
  
```console  
mefx /file:MyAddIn.dll /importers:MyAddin.MemberPart  
MyAddin.AddIn  
```  
  
 <span data-ttu-id="0681e-128">К этим действиям также можно применить параметр `/verbose` .</span><span class="sxs-lookup"><span data-stu-id="0681e-128">You can also apply the `/verbose` option to these actions.</span></span>  
  
<a name="finding_rejected_parts"></a>

## <a name="finding-rejected-parts"></a><span data-ttu-id="0681e-129">Поиск отклоненных частей</span><span class="sxs-lookup"><span data-stu-id="0681e-129">Finding Rejected Parts</span></span>  

 <span data-ttu-id="0681e-130">После загрузки доступных частей Mefx с помощью модуля композиции MEF составляет из них композицию.</span><span class="sxs-lookup"><span data-stu-id="0681e-130">Once it has loaded the available parts, Mefx uses the MEF composition engine to compose them.</span></span> <span data-ttu-id="0681e-131">Части, которые не удается включить в композицию, называются *отклоненными*.</span><span class="sxs-lookup"><span data-stu-id="0681e-131">Parts that cannot be successfully composed are referred to as *rejected*.</span></span> <span data-ttu-id="0681e-132">Чтобы составить список всех отклоненных частей, воспользуйтесь действием `/rejected` .</span><span class="sxs-lookup"><span data-stu-id="0681e-132">To list all the rejected parts, use the `/rejected` action.</span></span>  
  
 <span data-ttu-id="0681e-133">Для печати подробных сведений об отклоненных частях можно воспользоваться параметром `/verbose` и действием `/rejected` .</span><span class="sxs-lookup"><span data-stu-id="0681e-133">You can use the `/verbose` option with the `/rejected` action to print detailed information about rejected parts.</span></span> <span data-ttu-id="0681e-134">В следующем примере библиотека DLL `ClassLibrary1` содержит часть `AddIn` , которая импортирует части `MemberPart` и `ChainOne` .</span><span class="sxs-lookup"><span data-stu-id="0681e-134">In the following example, the `ClassLibrary1` DLL contains the `AddIn` part, which imports the `MemberPart` and `ChainOne` parts.</span></span> <span data-ttu-id="0681e-135">`ChainOne` импортирует `ChainTwo`, но `ChainTwo` не существует.</span><span class="sxs-lookup"><span data-stu-id="0681e-135">`ChainOne` imports `ChainTwo`, but `ChainTwo` does not exist.</span></span> <span data-ttu-id="0681e-136">Это означает, что `ChainOne` отклоняется, в результате чего отклоняется также и часть `AddIn` .</span><span class="sxs-lookup"><span data-stu-id="0681e-136">This means that `ChainOne` is rejected, which causes `AddIn` to be rejected.</span></span>  
  
```console  
mefx /file:ClassLibrary1.dll /rejected /verbose  
```  
  
 <span data-ttu-id="0681e-137">Ниже показаны полные выходные данные предыдущей команды.</span><span class="sxs-lookup"><span data-stu-id="0681e-137">The following shows the complete output of the previous command:</span></span>  
  
```output
[Part] ClassLibrary1.AddIn from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Export] ClassLibrary1.AddIn (ContractName="ClassLibrary1.AddIn")  
  [Import] ClassLibrary1.AddIn.memberPart (ContractName="ClassLibrary1.MemberPart")  
    [SatisfiedBy] ClassLibrary1.MemberPart (ContractName="ClassLibrary1.MemberPart") from: ClassLibrary1.MemberPart from: AssemblyCatalog (Assembly="ClassLibrar  
y1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Import] ClassLibrary1.AddIn.chain (ContractName="ClassLibrary1.ChainOne")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainOne") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainOne".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
    [Unsuitable] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
from: ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
      [Because] PartDefinitionIsRejected, The part providing the export is rejected because of other issues.  
  
[Part] ClassLibrary1.ChainOne from: AssemblyCatalog (Assembly="ClassLibrary1, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null")  
  [Primary Rejection]  
  [Export] ClassLibrary1.ChainOne (ContractName="ClassLibrary1.ChainOne")  
  [Import] ClassLibrary1.ChainOne.chain (ContractName="ClassLibrary1.ChainTwo")  
    [Exception] System.ComponentModel.Composition.ImportCardinalityMismatchException: No valid exports were found that match the constraint '((exportDefinition.ContractName == "ClassLibrary1.ChainTwo") AndAlso (exportDefinition.Metadata.ContainsKey("ExportTypeIdentity") AndAlso "ClassLibrary1.ChainTwo".Equals(exportDefinition.Metadata.get_Item("ExportTypeIdentity"))))', invalid exports may have been rejected.  
   at System.ComponentModel.Composition.Hosting.ExportProvider.GetExports(ImportDefinition definition, AtomicComposition atomicComposition)  
   at Microsoft.ComponentModel.Composition.Diagnostics.CompositionInfo.AnalyzeImportDefinition(ExportProvider host, IEnumerable`1 availableParts, ImportDefinition id)  
```  
  
 <span data-ttu-id="0681e-138">Интересные сведения содержатся в результатах `[Exception]` и `[Unsuitable]` .</span><span class="sxs-lookup"><span data-stu-id="0681e-138">The interesting information is contained in the `[Exception]` and `[Unsuitable]` results.</span></span> <span data-ttu-id="0681e-139">Результат `[Exception]` предоставляет сведения о том, почему часть была отклонена.</span><span class="sxs-lookup"><span data-stu-id="0681e-139">The `[Exception]` result provides information about why a part was rejected.</span></span> <span data-ttu-id="0681e-140">Результат `[Unsuitable]` показывает, почему подходящую по остальным параметрам часть невозможно использовать для заполнения импорта. В данном случае причина в том, что сама эта часть была отклонена из-за отсутствующих импортируемых элементов.</span><span class="sxs-lookup"><span data-stu-id="0681e-140">The `[Unsuitable]` result indicates why an otherwise-matching part could not be used to fill an import; in this case, because that part was itself rejected for missing imports.</span></span>  
  
<a name="analyzing_primary_causes"></a>

## <a name="analyzing-primary-causes"></a><span data-ttu-id="0681e-141">Анализ основных причин</span><span class="sxs-lookup"><span data-stu-id="0681e-141">Analyzing Primary Causes</span></span>  

 <span data-ttu-id="0681e-142">Если несколько частей связаны в длинную цепочку зависимостей, проблема с частью в нижней области может стать причиной отклонения всей цепочки.</span><span class="sxs-lookup"><span data-stu-id="0681e-142">If several parts are linked in a long dependency chain, a problem involving a part near the bottom may cause the entire chain to be rejected.</span></span> <span data-ttu-id="0681e-143">Диагностировать эти проблемы может быть сложно, потому что причина сбоя не всегда очевидна.</span><span class="sxs-lookup"><span data-stu-id="0681e-143">Diagnosing these problems can be difficult because the root cause of the failure is not always obvious.</span></span> <span data-ttu-id="0681e-144">Чтобы упростить проблему, можно использовать действие `/causes` , которое пытается найти причину любого каскадного отклонения.</span><span class="sxs-lookup"><span data-stu-id="0681e-144">To help with the problem, you can use the `/causes` action, which attempts to find the root cause of any cascading rejection.</span></span>  
  
 <span data-ttu-id="0681e-145">Если бы в предыдущем примере использовалось действие `/causes` , удалось бы вывести только информацию для части `ChainOne`, незаполненный импорт которой является основной причиной отклонения `AddIn`.</span><span class="sxs-lookup"><span data-stu-id="0681e-145">Using the `/causes` action on the previous example would list only information for `ChainOne`, whose unfilled import is the root cause of the rejection of `AddIn`.</span></span> <span data-ttu-id="0681e-146">Действие `/causes` можно использовать в обычном режиме и с параметрами `/verbose` .</span><span class="sxs-lookup"><span data-stu-id="0681e-146">The `/causes` action can be used in both normal and `/verbose` options.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0681e-147">В большинстве случаев Mefx сможет диагностировать основную причину каскадного сбоя.</span><span class="sxs-lookup"><span data-stu-id="0681e-147">In most cases, Mefx will be able to diagnose the root cause of a cascading failure.</span></span> <span data-ttu-id="0681e-148">Однако в тех случаях, когда части программным способом добавляются в контейнер, Mefx не сможет диагностировать причину проблемы, если задействованы иерархические контейнеры или пользовательские реализации `ExportProvider` .</span><span class="sxs-lookup"><span data-stu-id="0681e-148">However, in cases where parts are added programmatically to a container, cases involving hierarchical containers, or cases involving custom `ExportProvider` implementations, Mefx will not be able to diagnose the cause.</span></span> <span data-ttu-id="0681e-149">В общем случае вышеописанных случаев следует по возможности избегать, поскольку сбои, как правило, сложно диагностировать.</span><span class="sxs-lookup"><span data-stu-id="0681e-149">In general, the previously described cases should be avoided where possible, as failures are generally difficult to diagnose.</span></span>  
  
<a name="white_lists"></a>

## <a name="white-lists"></a><span data-ttu-id="0681e-150">Белые списки</span><span class="sxs-lookup"><span data-stu-id="0681e-150">White Lists</span></span>  

 <span data-ttu-id="0681e-151">Параметр `/whitelist` позволяет задать текстовый файл с перечислением частей, которые, как ожидается, будут отклонены.</span><span class="sxs-lookup"><span data-stu-id="0681e-151">The `/whitelist` option enables you to specify a text file that lists parts that are expected to be rejected.</span></span> <span data-ttu-id="0681e-152">Непредвиденные отклонения будут помечены.</span><span class="sxs-lookup"><span data-stu-id="0681e-152">Unexpected rejections will then be flagged.</span></span> <span data-ttu-id="0681e-153">Это может быть полезным при анализе неполной библиотеки или вложенной библиотеки, в которой отсутствуют некоторые зависимости.</span><span class="sxs-lookup"><span data-stu-id="0681e-153">This can be useful when you analyze an incomplete library, or a sub-library that is missing some dependencies.</span></span> <span data-ttu-id="0681e-154">Параметр `/whitelist` можно применить к действиям `/rejected` или `/causes` .</span><span class="sxs-lookup"><span data-stu-id="0681e-154">The `/whitelist` option can be applied to the `/rejected` or `/causes` actions.</span></span>  
  
 <span data-ttu-id="0681e-155">Рассмотрим файл с именем test.txt, который содержит текст ClassLibrary1.ChainOne.</span><span class="sxs-lookup"><span data-stu-id="0681e-155">Consider a file named test.txt that contains the text "ClassLibrary1.ChainOne".</span></span> <span data-ttu-id="0681e-156">При запуске действия `/rejected` с параметром `/whitelist` в предыдущем примере будут получены следующие выходные данные.</span><span class="sxs-lookup"><span data-stu-id="0681e-156">If you run the `/rejected` action with the `/whitelist` option on the previous example, it will produce the following output:</span></span>  
  
```console
mefx /file:ClassLibrary1.dll /rejected /whitelist:test.txt  
[Unexpected] ClassLibrary1.AddIn  
ClassLibrary1.ChainOne  
```
