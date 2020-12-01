---
title: Устранение рисков. Новый 64-разрядный JIT-компилятор
description: Узнайте о новом 64-разрядном JIT-компиляторе, входящем в .NET Framework 4.6, и непредвиденном поведении или исключениях, которые могут возникать во время компиляции.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: 228c286f6c5620dc838df5002edc60863a0fe4e2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256603"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="241aa-103">Устранение рисков. Новый 64-разрядный JIT-компилятор</span><span class="sxs-lookup"><span data-stu-id="241aa-103">Mitigation: New 64-bit JIT Compiler</span></span>

<span data-ttu-id="241aa-104">Начиная с .NET Framework 4.6, среда выполнения включает в себя новый 64-разрядный JIT-компилятор.</span><span class="sxs-lookup"><span data-stu-id="241aa-104">Starting with .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="241aa-105">Это изменение не влияет на компиляцию с помощью 32-разрядного JIT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="241aa-105">This change does not affect compilation with the 32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="241aa-106">Непредвиденное поведение или исключения</span><span class="sxs-lookup"><span data-stu-id="241aa-106">Unexpected behavior or exceptions</span></span>  

 <span data-ttu-id="241aa-107">В некоторых случаях компиляция с помощью нового 64-разрядного JIT-компилятора приводит к исключению среды выполнения или к поведению, которое не наблюдается при выполнении кода, скомпилированного старым 64-разрядным JIT-компилятором.</span><span class="sxs-lookup"><span data-stu-id="241aa-107">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="241aa-108">Известные различия включают в себя следующее.</span><span class="sxs-lookup"><span data-stu-id="241aa-108">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="241aa-109">Все эти известные проблемы устранены в новом 64-разрядном компиляторе на платформе .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="241aa-109">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="241aa-110">Большинство проблем было также устранено в выпусках обновлений платформы .NET Framework 4.6 и 4.6.1, включенных в состав обновления Windows.</span><span class="sxs-lookup"><span data-stu-id="241aa-110">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="241aa-111">Эти проблемы можно устранить, обеспечив актуальность используемой версии Windows или обновив платформу до версии .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="241aa-111">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
- <span data-ttu-id="241aa-112">При определенных условиях операция распаковки может вызывать исключение <xref:System.NullReferenceException> в сборках выпусков с включенной оптимизацией.</span><span class="sxs-lookup"><span data-stu-id="241aa-112">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
- <span data-ttu-id="241aa-113">В некоторых случаях выполнение рабочего кода в большом теле метода может вызывать исключение <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="241aa-113">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
- <span data-ttu-id="241aa-114">При определенных условиях в сборках выпусков передаваемые методу структуры обрабатываются как ссылочные типы, а не типы значений.</span><span class="sxs-lookup"><span data-stu-id="241aa-114">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="241aa-115">Одним из проявлений этой проблемы является отображение отдельных элементов коллекции в непредвиденном порядке.</span><span class="sxs-lookup"><span data-stu-id="241aa-115">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
- <span data-ttu-id="241aa-116">При определенных условиях сравнение значений <xref:System.UInt16> с установленным старшим битом выполняется неверно, если включена оптимизация.</span><span class="sxs-lookup"><span data-stu-id="241aa-116">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
- <span data-ttu-id="241aa-117">При определенных условиях, особенно при инициализации значений массивов, инициализация памяти инструкцией <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL может инициализировать память неправильным значением.</span><span class="sxs-lookup"><span data-stu-id="241aa-117">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="241aa-118">Это может привести либо к необработанному исключению, либо к неправильным выходным данным.</span><span class="sxs-lookup"><span data-stu-id="241aa-118">This can result either in an unhandled exception or incorrect output.</span></span>  
  
- <span data-ttu-id="241aa-119">В некоторых редких случаях условная поразрядная проверка может возвращать неверное значение типа <xref:System.Boolean> или вызывать исключение, если включены оптимизации компилятора.</span><span class="sxs-lookup"><span data-stu-id="241aa-119">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
- <span data-ttu-id="241aa-120">При определенных условиях, если инструкция `if` используется для проверки условия перед входом в блок `try` и на выходе из блока `try`, и такое же условие вычисляется в блоке `catch` или `finally`, новый 64-разрядный JIT-компилятор удаляет условие `if` из блока `catch` или `finally` при оптимизации кода.</span><span class="sxs-lookup"><span data-stu-id="241aa-120">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="241aa-121">В результате код внутри инструкции `if` в блоке `catch` или `finally` выполняется безусловно.</span><span class="sxs-lookup"><span data-stu-id="241aa-121">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>

## <a name="mitigation-of-known-issues"></a><span data-ttu-id="241aa-122">Устранение известных проблем</span><span class="sxs-lookup"><span data-stu-id="241aa-122">Mitigation of known issues</span></span>  

 <span data-ttu-id="241aa-123">При возникновении перечисленных выше проблем их можно решить, выполнив одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="241aa-123">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
- <span data-ttu-id="241aa-124">Обновление до .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="241aa-124">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="241aa-125">Новый 64-разрядный компилятор, входящий в состав .NET Framework 4.6.2, устраняет все эти известные проблемы.</span><span class="sxs-lookup"><span data-stu-id="241aa-125">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
- <span data-ttu-id="241aa-126">Обновление Windows до актуального состояния при запуске Центра обновления Windows.</span><span class="sxs-lookup"><span data-stu-id="241aa-126">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="241aa-127">Обновления служб до .NET Framework 4.6 и 4.6.1 решают все эти проблемы, кроме исключения <xref:System.NullReferenceException> при распаковке-преобразовании.</span><span class="sxs-lookup"><span data-stu-id="241aa-127">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
- <span data-ttu-id="241aa-128">Компиляция с помощью старого 64-разрядного JIT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="241aa-128">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="241aa-129">Дополнительные сведения о том, как это сделать, см. в разделе [Устранение других проблем](#Other).</span><span class="sxs-lookup"><span data-stu-id="241aa-129">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>

## <a name="mitigation-of-other-issues"></a><span data-ttu-id="241aa-130">Устранение других проблем</span><span class="sxs-lookup"><span data-stu-id="241aa-130">Mitigation of other issues</span></span>  

 <span data-ttu-id="241aa-131">При возникновении любых других различий в поведении между кодом, скомпилированным с помощью старого и нового 64-разрядных JIT-компиляторов, или между отладочной и окончательной версиями приложения, которые обе скомпилированы новым 64-разрядным JIT-компилятором, можно выполнить следующие действия для компиляции приложения с помощью старого 64-разрядного JIT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="241aa-131">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
- <span data-ttu-id="241aa-132">Для каждого отдельного приложения можно добавить элемент [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) в файл конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="241aa-132">On a per-application basis, you can add the [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="241aa-133">Следующее действие отключает компиляцию с помощью нового 64-разрядного JIT-компилятора и вместо этого использует устаревший 64-разрядный JIT-компилятор.</span><span class="sxs-lookup"><span data-stu-id="241aa-133">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- <span data-ttu-id="241aa-134">Для каждого отдельного пользователя можно добавить значение `REG_DWORD` с именем `useLegacyJit` в раздел реестра `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework`.</span><span class="sxs-lookup"><span data-stu-id="241aa-134">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="241aa-135">Значение 1 включает устаревший 64-разрядный JIT-компилятор; значение 0 отключает его и включает новый 64-разрядный JIT-компилятор.</span><span class="sxs-lookup"><span data-stu-id="241aa-135">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
- <span data-ttu-id="241aa-136">Для каждого отдельного компьютера можно добавить значение `REG_DWORD` с именем `useLegacyJit` в раздел реестра `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework`.</span><span class="sxs-lookup"><span data-stu-id="241aa-136">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="241aa-137">Значение 1 включает устаревший 64-разрядный JIT-компилятор; значение 0 отключает его и включает новый 64-разрядный JIT-компилятор.</span><span class="sxs-lookup"><span data-stu-id="241aa-137">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="241aa-138">Можно также сообщить нам об обнаруженной проблеме, обратившись в службу [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span><span class="sxs-lookup"><span data-stu-id="241aa-138">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="241aa-139">См. также</span><span class="sxs-lookup"><span data-stu-id="241aa-139">See also</span></span>

- [<span data-ttu-id="241aa-140">Совместимость приложений</span><span class="sxs-lookup"><span data-stu-id="241aa-140">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="241aa-141">\<useLegacyJit> Элемент</span><span class="sxs-lookup"><span data-stu-id="241aa-141">\<useLegacyJit> Element</span></span>](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
