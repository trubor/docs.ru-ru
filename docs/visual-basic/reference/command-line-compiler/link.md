---
description: 'Дополнительные сведения: -link (Visual Basic)'
title: -link
ms.date: 03/10/2018
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
ms.openlocfilehash: 31d98d2c0fb0cbd8e8baff82869501a7ff0ea270
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475140"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="f04bb-103">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f04bb-103">-link (Visual Basic)</span></span>

<span data-ttu-id="f04bb-104">Дает компилятору указание сделать всю информацию о типах COM из указанных сборок доступной компилируемому проекту.</span><span class="sxs-lookup"><span data-stu-id="f04bb-104">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f04bb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f04bb-105">Syntax</span></span>  
  
```console  
-link:fileList  
```

<span data-ttu-id="f04bb-106">or</span><span class="sxs-lookup"><span data-stu-id="f04bb-106">or</span></span>  

```console
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="f04bb-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="f04bb-107">Arguments</span></span>  
  
|<span data-ttu-id="f04bb-108">Термин</span><span class="sxs-lookup"><span data-stu-id="f04bb-108">Term</span></span>|<span data-ttu-id="f04bb-109">Определение</span><span class="sxs-lookup"><span data-stu-id="f04bb-109">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="f04bb-110">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="f04bb-110">Required.</span></span> <span data-ttu-id="f04bb-111">Список всех имен файлов сборки, разделенных запятыми.</span><span class="sxs-lookup"><span data-stu-id="f04bb-111">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="f04bb-112">Если имя файла содержит пробел, заключите его в кавычки.</span><span class="sxs-lookup"><span data-stu-id="f04bb-112">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f04bb-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="f04bb-113">Remarks</span></span>  

 <span data-ttu-id="f04bb-114">Параметр `-link` позволяет развернуть приложение, содержащее внедренные сведения о типе.</span><span class="sxs-lookup"><span data-stu-id="f04bb-114">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="f04bb-115">После этого приложение может использовать типы из сборки среды выполнения, реализующей информацию о внедренных типах, без ссылки на эту сборку.</span><span class="sxs-lookup"><span data-stu-id="f04bb-115">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="f04bb-116">Если опубликовано несколько версий сборки среды выполнения, приложение, содержащее сведения о внедренных типах, может работать с различными версиями без перекомпиляции.</span><span class="sxs-lookup"><span data-stu-id="f04bb-116">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="f04bb-117">Пример см. в разделе [Пошаговое руководство. внедрению типов из управляемых сборок](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="f04bb-117">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>  
  
 <span data-ttu-id="f04bb-118">Параметр `-link` особенно полезен при работе с COM-взаимодействием.</span><span class="sxs-lookup"><span data-stu-id="f04bb-118">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="f04bb-119">COM-типы внедряются для того, чтобы приложению не требовалась основная сборка взаимодействия (PIA) на целевом компьютере.</span><span class="sxs-lookup"><span data-stu-id="f04bb-119">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="f04bb-120">Параметр `-link` предписывает компилятору внедрить сведения о COM-типах из указанной сборки взаимодействия в полученный скомпилированный код.</span><span class="sxs-lookup"><span data-stu-id="f04bb-120">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="f04bb-121">COM-тип определяется значением CLSID (GUID).</span><span class="sxs-lookup"><span data-stu-id="f04bb-121">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="f04bb-122">Это позволяет запускать приложение на целевом компьютере, где установлены те же COM-типы с такими же значениями CLSID.</span><span class="sxs-lookup"><span data-stu-id="f04bb-122">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="f04bb-123">В качестве примера можно привести приложения, автоматизирующие Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="f04bb-123">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="f04bb-124">Поскольку в приложениях типа Office значение CLSID обычно не зависит от версии, ваше приложение сможет использовать COM-типы по ссылке до тех пора, пока на целевом компьютере установлена платформа .NET Framework 4 или более поздней версии, а приложение работает с методами, свойствами или событиями, включенными в эти COM-типы.</span><span class="sxs-lookup"><span data-stu-id="f04bb-124">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="f04bb-125">Параметр `-link` внедряет только интерфейсы, структуры и делегаты.</span><span class="sxs-lookup"><span data-stu-id="f04bb-125">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="f04bb-126">Внедрение COM-классов не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="f04bb-126">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f04bb-127">Если в коде создается экземпляр внедренного COM-типа, его следует создавать, используя соответствующий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="f04bb-127">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="f04bb-128">При попытке создать экземпляр внедренного COM-типа с помощью компонентного класса возникнет ошибка.</span><span class="sxs-lookup"><span data-stu-id="f04bb-128">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="f04bb-129">Чтобы задать параметр `-link` в Visual Studio, добавьте ссылку на сборку и задайте для свойства `Embed Interop Types` значение **true**.</span><span class="sxs-lookup"><span data-stu-id="f04bb-129">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="f04bb-130">По умолчанию для свойства `Embed Interop Types` задается значение **false**.</span><span class="sxs-lookup"><span data-stu-id="f04bb-130">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="f04bb-131">Ссылаясь на COM-сборку (сборку A), которая, в свою очередь, ссылается на другую COM-сборку (сборку Б), необходимо также добавить ссылку на сборку Б, если выполняется любое из следующих условий:</span><span class="sxs-lookup"><span data-stu-id="f04bb-131">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="f04bb-132">Тип из сборки A наследуется из типа или реализует интерфейс сборки Б.</span><span class="sxs-lookup"><span data-stu-id="f04bb-132">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="f04bb-133">Вызывается поле, свойство, событие или метод, имеющий тип возвращаемого значения или тип параметра из сборки Б.</span><span class="sxs-lookup"><span data-stu-id="f04bb-133">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="f04bb-134">Для указания каталога, в котором находятся одна или несколько ссылок на сборки, используется параметр [-libpath](libpath.md).</span><span class="sxs-lookup"><span data-stu-id="f04bb-134">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="f04bb-135">Как и параметр компилятора [-reference](reference.md), параметр компилятора `-link` использует файл ответов Vbc.rsp, который ссылается на часто используемые сборки .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f04bb-135">Like the [-reference](reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="f04bb-136">Если вы не хотите, чтобы компилятор использовал файл Vbc.rsp, примените параметр компилятора [-noconfig](noconfig.md).</span><span class="sxs-lookup"><span data-stu-id="f04bb-136">Use the [-noconfig](noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="f04bb-137">Краткой формой `-link` является `-l`.</span><span class="sxs-lookup"><span data-stu-id="f04bb-137">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="f04bb-138">Универсальные и внедренные типы</span><span class="sxs-lookup"><span data-stu-id="f04bb-138">Generics and Embedded Types</span></span>  

 <span data-ttu-id="f04bb-139">В следующих разделах описаны ограничения на использование универсальных типов в приложениях с внедренными типами взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="f04bb-139">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="f04bb-140">Универсальные интерфейсы</span><span class="sxs-lookup"><span data-stu-id="f04bb-140">Generic Interfaces</span></span>  

 <span data-ttu-id="f04bb-141">Использовать универсальные интерфейсы, внедренные из сборки взаимодействия, нельзя.</span><span class="sxs-lookup"><span data-stu-id="f04bb-141">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="f04bb-142">Эти действия показаны в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="f04bb-142">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="f04bb-143">Типы с универсальными параметрами</span><span class="sxs-lookup"><span data-stu-id="f04bb-143">Types That Have Generic Parameters</span></span>  

 <span data-ttu-id="f04bb-144">Типы с универсальным параметром, тип которого внедрен из сборки взаимодействия, нельзя использовать, если он относится к внешней сборке.</span><span class="sxs-lookup"><span data-stu-id="f04bb-144">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="f04bb-145">Это ограничение не относится к интерфейсам.</span><span class="sxs-lookup"><span data-stu-id="f04bb-145">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="f04bb-146">Например, рассмотрим интерфейс <xref:Microsoft.Office.Interop.Excel.Range>, который определен в сборке <xref:Microsoft.Office.Interop.Excel>.</span><span class="sxs-lookup"><span data-stu-id="f04bb-146">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="f04bb-147">Если библиотека содержит внедренные типы взаимодействия из сборки <xref:Microsoft.Office.Interop.Excel> и предоставляет метод, возвращающий универсальный тип с параметром, типом которого является интерфейс <xref:Microsoft.Office.Interop.Excel.Range>, этот метод должен возвращать универсальный интерфейс, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="f04bb-147">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 <span data-ttu-id="f04bb-148">В следующем примере клиентский код может вызывать метод, возвращающий универсальный интерфейс <xref:System.Collections.IList> без ошибок.</span><span class="sxs-lookup"><span data-stu-id="f04bb-148">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="f04bb-149">Пример</span><span class="sxs-lookup"><span data-stu-id="f04bb-149">Example</span></span>  

 <span data-ttu-id="f04bb-150">Следующая команда компилирует исходный файл `OfficeApp.vb`, ссылочные сборки из `COMData1.dll` и `COMData2.dll`, а также создает файл `OfficeApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="f04bb-150">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f04bb-151">См. также</span><span class="sxs-lookup"><span data-stu-id="f04bb-151">See also</span></span>

- [<span data-ttu-id="f04bb-152">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="f04bb-152">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="f04bb-153">Пошаговое руководство: внедрение типов из управляемых сборок</span><span class="sxs-lookup"><span data-stu-id="f04bb-153">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="f04bb-154">-reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f04bb-154">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="f04bb-155">-noconfig</span><span class="sxs-lookup"><span data-stu-id="f04bb-155">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="f04bb-156">-libpath</span><span class="sxs-lookup"><span data-stu-id="f04bb-156">-libpath</span></span>](libpath.md)
- [<span data-ttu-id="f04bb-157">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="f04bb-157">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="f04bb-158">Знакомство с COM-взаимодействием</span><span class="sxs-lookup"><span data-stu-id="f04bb-158">Introduction to COM Interop</span></span>](../../programming-guide/com-interop/introduction-to-com-interop.md)
