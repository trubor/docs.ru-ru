---
description: 'Дополнительные сведения: общие атрибуты (Visual Basic)'
title: Общие атрибуты
ms.date: 07/20/2015
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
ms.openlocfilehash: 875554b69a23640c2d67367c93b56c34c286df37
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437791"
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="82f9f-103">Common Attributes (Visual Basic) (Распространенные атрибуты (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="82f9f-103">Common Attributes (Visual Basic)</span></span>

<span data-ttu-id="82f9f-104">В этом разделе описываются атрибуты, наиболее часто используемые в Visual Basic программах.</span><span class="sxs-lookup"><span data-stu-id="82f9f-104">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>

- [<span data-ttu-id="82f9f-105">Глобальные атрибуты</span><span class="sxs-lookup"><span data-stu-id="82f9f-105">Global Attributes</span></span>](#Global)

- [<span data-ttu-id="82f9f-106">Устаревший атрибут</span><span class="sxs-lookup"><span data-stu-id="82f9f-106">Obsolete Attribute</span></span>](#Obsolete)

- [<span data-ttu-id="82f9f-107">Атрибут Conditional</span><span class="sxs-lookup"><span data-stu-id="82f9f-107">Conditional Attribute</span></span>](#Conditional)

- [<span data-ttu-id="82f9f-108">Атрибуты сведений о вызывающем объекте</span><span class="sxs-lookup"><span data-stu-id="82f9f-108">Caller Info Attributes</span></span>](#CallerInfo)

- [<span data-ttu-id="82f9f-109">Атрибуты Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82f9f-109">Visual Basic Attributes</span></span>](#VB)

## <a name="global-attributes"></a><a name="Global"></a> <span data-ttu-id="82f9f-110">Глобальные атрибуты</span><span class="sxs-lookup"><span data-stu-id="82f9f-110">Global Attributes</span></span>

<span data-ttu-id="82f9f-111">Большинство атрибутов применяется к определенным элементам языка, таким как классы или методы. Тем не менее некоторые атрибуты являются глобальными — они применяются ко всей сборке или модулю.</span><span class="sxs-lookup"><span data-stu-id="82f9f-111">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="82f9f-112">Например, атрибут <xref:System.Reflection.AssemblyVersionAttribute> можно использовать для встраивания сведений о версии в сборку, например следующим образом:</span><span class="sxs-lookup"><span data-stu-id="82f9f-112">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>

```vb
<Assembly: AssemblyVersion("1.0.0.0")>
```

<span data-ttu-id="82f9f-113">Глобальные атрибуты появляются в исходном коде после любых инструкций верхнего уровня `Imports` и перед любыми объявлениями типа, модуля или пространства имен.</span><span class="sxs-lookup"><span data-stu-id="82f9f-113">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="82f9f-114">Глобальные атрибуты могут содержаться в нескольких исходных файлах, однако эти файлы должны быть скомпилированы за один проход компиляции.</span><span class="sxs-lookup"><span data-stu-id="82f9f-114">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="82f9f-115">Для проектов Visual Basic глобальные атрибуты обычно помещаются в файл AssemblyInfo. vb (файл создается автоматически при создании проекта в Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="82f9f-115">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>

<span data-ttu-id="82f9f-116">Атрибуты сборки — это значения, которые предоставляют сведения о сборке.</span><span class="sxs-lookup"><span data-stu-id="82f9f-116">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="82f9f-117">Они делятся на следующие категории:</span><span class="sxs-lookup"><span data-stu-id="82f9f-117">They fall into the following categories:</span></span>

- <span data-ttu-id="82f9f-118">Атрибуты удостоверения сборки</span><span class="sxs-lookup"><span data-stu-id="82f9f-118">Assembly identity attributes</span></span>

- <span data-ttu-id="82f9f-119">Информационные атрибуты</span><span class="sxs-lookup"><span data-stu-id="82f9f-119">Informational attributes</span></span>

- <span data-ttu-id="82f9f-120">Атрибуты манифеста сборки</span><span class="sxs-lookup"><span data-stu-id="82f9f-120">Assembly manifest attributes</span></span>

### <a name="assembly-identity-attributes"></a><span data-ttu-id="82f9f-121">Атрибуты удостоверения сборки</span><span class="sxs-lookup"><span data-stu-id="82f9f-121">Assembly Identity Attributes</span></span>

<span data-ttu-id="82f9f-122">Три атрибута (со строгим именем, если оно применимо) определяют удостоверение сборки: имя, версию, язык и региональные параметры.</span><span class="sxs-lookup"><span data-stu-id="82f9f-122">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="82f9f-123">Эти атрибуты формируют полное имя сборки и являются обязательными при ссылке на нее в коде.</span><span class="sxs-lookup"><span data-stu-id="82f9f-123">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="82f9f-124">Атрибуты можно использовать для задания версии сборки и языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="82f9f-124">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="82f9f-125">Однако значение имени задается компилятором, в интегрированной среде разработки Visual Studio, в [диалоговом окне сведений о сборке](/visualstudio/ide/reference/assembly-information-dialog-box) или в компоновщике сборок (Al.exe) при создании сборки на основе файла, содержащего манифест сборки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-125">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="82f9f-126">Атрибут <xref:System.Reflection.AssemblyFlagsAttribute> указывает, могут ли сосуществовать несколько копий сборки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-126">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>

<span data-ttu-id="82f9f-127">В следующей таблице приведены атрибуты удостоверения.</span><span class="sxs-lookup"><span data-stu-id="82f9f-127">The following table shows the identity attributes.</span></span>

|<span data-ttu-id="82f9f-128">Атрибут</span><span class="sxs-lookup"><span data-stu-id="82f9f-128">Attribute</span></span>|<span data-ttu-id="82f9f-129">Назначение</span><span class="sxs-lookup"><span data-stu-id="82f9f-129">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="82f9f-130">Полностью описывает удостоверение сборки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-130">Fully describes the identity of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="82f9f-131">Задает версию сборки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-131">Specifies the version of an assembly.</span></span>|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="82f9f-132">Указывает, какой язык и региональные параметры поддерживает сборка.</span><span class="sxs-lookup"><span data-stu-id="82f9f-132">Specifies which culture the assembly supports.</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="82f9f-133">Указывает, поддерживает ли сборка параллельное выполнение на одном компьютере, в одном процессе или в одном домене приложения.</span><span class="sxs-lookup"><span data-stu-id="82f9f-133">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|

### <a name="informational-attributes"></a><span data-ttu-id="82f9f-134">Информационные атрибуты</span><span class="sxs-lookup"><span data-stu-id="82f9f-134">Informational Attributes</span></span>

<span data-ttu-id="82f9f-135">Информационные атрибуты можно использовать для предоставления дополнительных сведений о компании или продукте в сборке.</span><span class="sxs-lookup"><span data-stu-id="82f9f-135">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="82f9f-136">В следующей таблице показаны информационные атрибуты, определенные в пространстве имен <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="82f9f-136">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="82f9f-137">Атрибут</span><span class="sxs-lookup"><span data-stu-id="82f9f-137">Attribute</span></span>|<span data-ttu-id="82f9f-138">Назначение</span><span class="sxs-lookup"><span data-stu-id="82f9f-138">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="82f9f-139">Определяет настраиваемый атрибут, задающий имя продукта для манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-139">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="82f9f-140">Определяет настраиваемый атрибут, задающий товарный знак для манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-140">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="82f9f-141">Определяет настраиваемый атрибут, задающий информационную версию для манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-141">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="82f9f-142">Определяет настраиваемый атрибут, задающий название организации для манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-142">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="82f9f-143">Определяет настраиваемый атрибут, задающий уведомление об авторских правах для манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-143">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="82f9f-144">Дает компилятору указание использовать определенный номер версии для ресурса версии файла Win32.</span><span class="sxs-lookup"><span data-stu-id="82f9f-144">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="82f9f-145">Указывает, соответствует ли сборка спецификации CLS.</span><span class="sxs-lookup"><span data-stu-id="82f9f-145">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|

### <a name="assembly-manifest-attributes"></a><span data-ttu-id="82f9f-146">Атрибуты манифеста сборки</span><span class="sxs-lookup"><span data-stu-id="82f9f-146">Assembly Manifest Attributes</span></span>

<span data-ttu-id="82f9f-147">Атрибуты манифеста сборки можно использовать для предоставления сведений в манифесте сборки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-147">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="82f9f-148">К ним относится заголовок, описание, псевдоним по умолчанию и конфигурация.</span><span class="sxs-lookup"><span data-stu-id="82f9f-148">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="82f9f-149">В следующей таблице показаны атрибуты манифеста сборки, определенные в пространстве имен <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="82f9f-149">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>

|<span data-ttu-id="82f9f-150">Атрибут</span><span class="sxs-lookup"><span data-stu-id="82f9f-150">Attribute</span></span>|<span data-ttu-id="82f9f-151">Назначение</span><span class="sxs-lookup"><span data-stu-id="82f9f-151">Purpose</span></span>|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="82f9f-152">Определяет настраиваемый атрибут, задающий название сборки для манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-152">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="82f9f-153">Определяет настраиваемый атрибут, задающий описание сборки для манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-153">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="82f9f-154">Определяет настраиваемый атрибут, задающий конфигурацию сборки для манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-154">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="82f9f-155">Определяет понятный псевдоним по умолчанию для манифеста сборки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-155">Defines a friendly default alias for an assembly manifest</span></span>|

## <a name="obsolete-attribute"></a><a name="Obsolete"></a> <span data-ttu-id="82f9f-156">Устаревший атрибут</span><span class="sxs-lookup"><span data-stu-id="82f9f-156">Obsolete Attribute</span></span>

<span data-ttu-id="82f9f-157">Атрибут `Obsolete` помечает сущность программы как нерекомендуемую для использования.</span><span class="sxs-lookup"><span data-stu-id="82f9f-157">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="82f9f-158">Каждый случай использования сущности, помеченной как устаревшая, будет приводить к созданию предупреждения или сообщения об ошибке в зависимости от настройки атрибута.</span><span class="sxs-lookup"><span data-stu-id="82f9f-158">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="82f9f-159">Пример:</span><span class="sxs-lookup"><span data-stu-id="82f9f-159">For example:</span></span>

```vb
<System.Obsolete("use class B")>
Class A
    Sub Method()
    End Sub
End Class

Class B
    <System.Obsolete("use NewMethod", True)>
    Sub OldMethod()
    End Sub

    Sub NewMethod()
    End Sub
End Class
```

<span data-ttu-id="82f9f-160">В этом примере атрибут `Obsolete` применяется к классу `A` и к методу `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="82f9f-160">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="82f9f-161">Поскольку для второго аргумента конструктора атрибутов, примененного к `B.OldMethod`, задано значение `true`, этот метод будет вызывать ошибку компилятора, тогда как при использовании класса `A` будет просто создаваться предупреждение.</span><span class="sxs-lookup"><span data-stu-id="82f9f-161">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="82f9f-162">При этом вызов `B.NewMethod` не создает предупреждений или ошибок.</span><span class="sxs-lookup"><span data-stu-id="82f9f-162">Calling `B.NewMethod`, however, produces no warning or error.</span></span>

<span data-ttu-id="82f9f-163">Строка, предоставленная в качестве первого аргумента конструктору атрибута, будет отображаться как часть предупреждения или ошибки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-163">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="82f9f-164">Например, при использовании с предыдущими определениями следующий код создает два предупреждения и одну ошибку:</span><span class="sxs-lookup"><span data-stu-id="82f9f-164">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>

```vb
' Generates 2 warnings:
' Dim a As New A
' Generate no errors or warnings:

Dim b As New B
b.NewMethod()

' Generates an error, terminating compilation:
' b.OldMethod()
```

<span data-ttu-id="82f9f-165">Создается два предупреждения для класса `A`: одно для объявления ссылки на класс, а второе — для конструктора класса.</span><span class="sxs-lookup"><span data-stu-id="82f9f-165">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>

<span data-ttu-id="82f9f-166">Атрибут `Obsolete` может использоваться без аргументов, однако рекомендуется включать пояснение о том, почему соответствующий элемент является устаревшим и что следует использовать вместо него.</span><span class="sxs-lookup"><span data-stu-id="82f9f-166">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>

<span data-ttu-id="82f9f-167">Атрибут `Obsolete` является атрибутом однократного использования и может применяться к любой сущности, допускающей использование атрибутов.</span><span class="sxs-lookup"><span data-stu-id="82f9f-167">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="82f9f-168">`Obsolete` является псевдонимом для <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="82f9f-168">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>

## <a name="conditional-attribute"></a><a name="Conditional"></a> <span data-ttu-id="82f9f-169">Атрибут Conditional</span><span class="sxs-lookup"><span data-stu-id="82f9f-169">Conditional Attribute</span></span>

<span data-ttu-id="82f9f-170">Атрибут `Conditional` определяет зависимость выполнения метода от идентификатора предварительной обработки.</span><span class="sxs-lookup"><span data-stu-id="82f9f-170">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="82f9f-171">Атрибут `Conditional` является псевдонимом для <xref:System.Diagnostics.ConditionalAttribute> и может применяться к методу или классу атрибута.</span><span class="sxs-lookup"><span data-stu-id="82f9f-171">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>

<span data-ttu-id="82f9f-172">В этом примере атрибут `Conditional` применяется к методу для включения и отключения отображения диагностической информации для конкретной программы:</span><span class="sxs-lookup"><span data-stu-id="82f9f-172">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>

```vb
#Const TRACE_ON = True
Imports System.Diagnostics

Module TestConditionalAttribute
    Public Class Trace
        <Conditional("TRACE_ON")>
        Public Shared Sub Msg(ByVal msg As String)
            Console.WriteLine(msg)
        End Sub

    End Class

    Sub Main()
        Trace.Msg("Now in Main...")
        Console.WriteLine("Done.")
    End Sub
End Module
```

<span data-ttu-id="82f9f-173">Если идентификатор `TRACE_ON` не определен, выходные данные трассировки не отображаются.</span><span class="sxs-lookup"><span data-stu-id="82f9f-173">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>

<span data-ttu-id="82f9f-174">Атрибут `Conditional` часто используется с идентификатором `DEBUG` для включения функций трассировки и ведения журнала для отладочных сборок (но не сборок выпуска) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="82f9f-174">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>

```vb
<Conditional("DEBUG")>
Shared Sub DebugMethod()

End Sub
```

<span data-ttu-id="82f9f-175">Когда вызывается метод, помеченный как условный, наличие или отсутствие заданного символа предварительной обработки определяет, включается ли вызов или пропускается.</span><span class="sxs-lookup"><span data-stu-id="82f9f-175">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="82f9f-176">Если этот символ определен, вызов включается; в противном случае вызов пропускается.</span><span class="sxs-lookup"><span data-stu-id="82f9f-176">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="82f9f-177">Использование атрибута `Conditional` — это более понятная, элегантная и менее подверженная ошибкам альтернатива вложению методов в блоки `#if…#endif`, например следующим образом:</span><span class="sxs-lookup"><span data-stu-id="82f9f-177">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>

```vb
#If DEBUG Then
    Sub ConditionalMethod()
    End Sub
#End If
```

<span data-ttu-id="82f9f-178">Условный метод должен быть методом в объявлении класса или структуры и не должен возвращать значение.</span><span class="sxs-lookup"><span data-stu-id="82f9f-178">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>

### <a name="using-multiple-identifiers"></a><span data-ttu-id="82f9f-179">Использование нескольких идентификаторов</span><span class="sxs-lookup"><span data-stu-id="82f9f-179">Using Multiple Identifiers</span></span>

<span data-ttu-id="82f9f-180">Если метод содержит несколько атрибутов `Conditional`, вызов метода включается, если определен хотя бы один из условных символов (другими словами, символы логически связаны с помощью оператора ИЛИ).</span><span class="sxs-lookup"><span data-stu-id="82f9f-180">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="82f9f-181">В этом примере наличие `A` или `B` приведет к вызову метода:</span><span class="sxs-lookup"><span data-stu-id="82f9f-181">In this example, the presence of either `A` or `B` will result in a method call:</span></span>

```vb
<Conditional("A"), Conditional("B")>
Shared Sub DoIfAorB()

End Sub
```

<span data-ttu-id="82f9f-182">Для получения эффекта логического связывания символов с помощью оператора И можно определить последовательные условные методы.</span><span class="sxs-lookup"><span data-stu-id="82f9f-182">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="82f9f-183">Например, второй метод ниже будет выполняться, только если определены `A` и `B`:</span><span class="sxs-lookup"><span data-stu-id="82f9f-183">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>

```vb
<Conditional("A")>
Shared Sub DoIfA()
    DoIfAandB()
End Sub

<Conditional("B")>
Shared Sub DoIfAandB()
    ' Code to execute when both A and B are defined...
End Sub
```

### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="82f9f-184">Использование атрибута Conditional с классами атрибутов</span><span class="sxs-lookup"><span data-stu-id="82f9f-184">Using Conditional with Attribute Classes</span></span>

<span data-ttu-id="82f9f-185">Атрибут `Conditional` также может применяться к определению класса атрибута.</span><span class="sxs-lookup"><span data-stu-id="82f9f-185">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="82f9f-186">В этом примере настраиваемый атрибут `Documentation` добавит сведения в метаданные, только если задано значение DEBUG.</span><span class="sxs-lookup"><span data-stu-id="82f9f-186">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>

```vb
<Conditional("DEBUG")>
Public Class Documentation
    Inherits System.Attribute
    Private text As String
    Sub New(ByVal doc_text As String)
        text = doc_text
    End Sub
End Class

Class SampleClass
    ' This attribute will only be included if DEBUG is defined.
    <Documentation("This method displays an integer.")>
    Shared Sub DoWork(ByVal i As Integer)
        System.Console.WriteLine(i)
    End Sub
End Class
```

## <a name="caller-info-attributes"></a><a name="CallerInfo"></a> <span data-ttu-id="82f9f-187">Атрибуты сведений о вызывающем объекте</span><span class="sxs-lookup"><span data-stu-id="82f9f-187">Caller Info Attributes</span></span>

<span data-ttu-id="82f9f-188">С помощью информационных атрибутов вызывающего объекта можно получить сведения о вызывающем объекте метода.</span><span class="sxs-lookup"><span data-stu-id="82f9f-188">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="82f9f-189">Можно получить путь к файлу исходного кода, номер строки в исходном коде и имя вызывающего объекта.</span><span class="sxs-lookup"><span data-stu-id="82f9f-189">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>

<span data-ttu-id="82f9f-190">Для получения этих сведений используются атрибуты, которые применяются к необязательным параметрам.</span><span class="sxs-lookup"><span data-stu-id="82f9f-190">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="82f9f-191">Каждый необязательный параметр задает значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="82f9f-191">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="82f9f-192">В следующей таблице перечислены информационные атрибуты вызывающего объекта, которые определены в пространстве имен <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="82f9f-192">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="82f9f-193">Атрибут</span><span class="sxs-lookup"><span data-stu-id="82f9f-193">Attribute</span></span>|<span data-ttu-id="82f9f-194">Описание</span><span class="sxs-lookup"><span data-stu-id="82f9f-194">Description</span></span>|<span data-ttu-id="82f9f-195">Type</span><span class="sxs-lookup"><span data-stu-id="82f9f-195">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="82f9f-196">Полный путь исходного файла, содержащего вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="82f9f-196">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="82f9f-197">Это путь во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="82f9f-197">This is the path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="82f9f-198">Номер строки в исходном файле, из которого вызывается метод.</span><span class="sxs-lookup"><span data-stu-id="82f9f-198">Line number in the source file from which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="82f9f-199">Имя свойства или метода вызывающего объекта.</span><span class="sxs-lookup"><span data-stu-id="82f9f-199">Method name or property name of the caller.</span></span> <span data-ttu-id="82f9f-200">Дополнительные сведения см. в разделе [сведения о вызывающем объекте (Visual Basic)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="82f9f-200">For more information, see [Caller Information (Visual Basic)](../caller-information.md).</span></span>|`String`|

<span data-ttu-id="82f9f-201">Дополнительные сведения об атрибутах сведений о вызывающем объекте см. в разделе [сведения о вызывающем объекте (Visual Basic)](../caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="82f9f-201">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../caller-information.md).</span></span>

## <a name="visual-basic-attributes"></a><a name="VB"></a> <span data-ttu-id="82f9f-202">Атрибуты Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82f9f-202">Visual Basic Attributes</span></span>

<span data-ttu-id="82f9f-203">В следующей таблице перечислены атрибуты, характерные для Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="82f9f-203">The following table lists the attributes that are specific to Visual Basic.</span></span>

|<span data-ttu-id="82f9f-204">attribute</span><span class="sxs-lookup"><span data-stu-id="82f9f-204">Attribute</span></span>|<span data-ttu-id="82f9f-205">Назначение</span><span class="sxs-lookup"><span data-stu-id="82f9f-205">Purpose</span></span>|
|---------------|-------------|
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="82f9f-206">Указывает компилятору, что класс должен быть представлен в виде COM-объекта.</span><span class="sxs-lookup"><span data-stu-id="82f9f-206">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="82f9f-207">Разрешает доступ к членам модуля с использованием только квалификации, необходимой для модуля.</span><span class="sxs-lookup"><span data-stu-id="82f9f-207">Allows module members to be accessed using only the qualification needed for the module.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="82f9f-208">Задает размер строки фиксированной длины в структуре для использования с входными и выходными функциями файлов.</span><span class="sxs-lookup"><span data-stu-id="82f9f-208">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="82f9f-209">Задает размер фиксированного массива в структуре для использования с входными и выходными функциями файла.</span><span class="sxs-lookup"><span data-stu-id="82f9f-209">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|

### <a name="comclassattribute"></a><span data-ttu-id="82f9f-210">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="82f9f-210">COMClassAttribute</span></span>

<span data-ttu-id="82f9f-211">Используйте `COMClassAttribute` , чтобы упростить процесс создания COM-компонентов из Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="82f9f-211">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="82f9f-212">Объекты COM значительно отличаются от платформа .NET Framework сборок, и без `COMClassAttribute` них необходимо выполнить ряд действий по созданию COM-объекта из Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="82f9f-212">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="82f9f-213">Для классов, помеченных `COMClassAttribute` , компилятор выполняет многие из этих шагов автоматически.</span><span class="sxs-lookup"><span data-stu-id="82f9f-213">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>

### <a name="hidemodulenameattribute"></a><span data-ttu-id="82f9f-214">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="82f9f-214">HideModuleNameAttribute</span></span>

<span data-ttu-id="82f9f-215">Используйте `HideModuleNameAttribute` , чтобы разрешить доступ к членам модуля только с помощью квалификации, необходимой для модуля.</span><span class="sxs-lookup"><span data-stu-id="82f9f-215">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>

### <a name="vbfixedstringattribute"></a><span data-ttu-id="82f9f-216">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="82f9f-216">VBFixedStringAttribute</span></span>

<span data-ttu-id="82f9f-217">Используется `VBFixedStringAttribute` для принудительного Visual Basic создания строки фиксированной длины.</span><span class="sxs-lookup"><span data-stu-id="82f9f-217">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="82f9f-218">По умолчанию строки имеют переменную длину, и этот атрибут полезен при хранении строк в файлах.</span><span class="sxs-lookup"><span data-stu-id="82f9f-218">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="82f9f-219">Следующий код демонстрирует это:</span><span class="sxs-lookup"><span data-stu-id="82f9f-219">The following code demonstrates this:</span></span>

```vb
Structure Worker
    ' The runtime uses VBFixedString to determine
    ' if the field should be written out as a fixed size.
    <VBFixedString(10)> Public LastName As String
    <VBFixedString(7)> Public Title As String
    <VBFixedString(2)> Public Rank As String
End Structure
```

### <a name="vbfixedarrayattribute"></a><span data-ttu-id="82f9f-220">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="82f9f-220">VBFixedArrayAttribute</span></span>

<span data-ttu-id="82f9f-221">Используется `VBFixedArrayAttribute` для объявления массивов с фиксированным размером.</span><span class="sxs-lookup"><span data-stu-id="82f9f-221">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="82f9f-222">Как и в случае с Visual Basic строками, по умолчанию массивы имеют переменную длину.</span><span class="sxs-lookup"><span data-stu-id="82f9f-222">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="82f9f-223">Этот атрибут полезен при сериализации или записи данных в файлы.</span><span class="sxs-lookup"><span data-stu-id="82f9f-223">This attribute is useful when serializing or writing data to files.</span></span>

## <a name="see-also"></a><span data-ttu-id="82f9f-224">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="82f9f-224">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="82f9f-225">Руководство по программированию на Visual Basic</span><span class="sxs-lookup"><span data-stu-id="82f9f-225">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="82f9f-226">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="82f9f-226">Attributes</span></span>](../../../../standard/attributes/index.md)
- <span data-ttu-id="82f9f-227">[Reflection (Visual Basic)](../reflection.md) (Отражение (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="82f9f-227">[Reflection (Visual Basic)](../reflection.md)</span></span>
- <span data-ttu-id="82f9f-228">[Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md) (Обращение к атрибутам с помощью отражения (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="82f9f-228">[Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md)</span></span>
