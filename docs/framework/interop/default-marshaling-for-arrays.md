---
title: Маршалинг по умолчанию для массивов
description: Сведения о стандартном маршалинге для массивов. Узнайте об управляемых массивах, неуправляемых массивах, передаче параметров массива в код .NET и передаче массивов в COM.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
ms.openlocfilehash: b6a675bbbfb974d78539d02b31b500b03a2ac8f4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256667"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="25fec-104">Маршалинг по умолчанию для массивов</span><span class="sxs-lookup"><span data-stu-id="25fec-104">Default Marshaling for Arrays</span></span>

<span data-ttu-id="25fec-105">Если приложение полностью состоит из управляемого кода, общеязыковая среда выполнения (CLR) передает типы массивов в качестве параметров ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="25fec-105">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="25fec-106">В отличие от этого, маршалер взаимодействия по умолчанию передает массив в качестве параметров ввода.</span><span class="sxs-lookup"><span data-stu-id="25fec-106">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="25fec-107">В рамках [оптимизации закрепления](copying-and-pinning.md) непреобразуемый массив может выступать в качестве параметра ввода-вывода при взаимодействии с объектами в том же подразделении.</span><span class="sxs-lookup"><span data-stu-id="25fec-107">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="25fec-108">Тем не менее при последующем экспорте кода в библиотеку типов, используемую для создания учетной записи посредника между компьютерами, если эта библиотека используется для маршалинга вызовов между подразделениями, вызовы могут получать фактические характеристики параметра ввода.</span><span class="sxs-lookup"><span data-stu-id="25fec-108">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="25fec-109">Массивы имеют сложную структуру, поэтому для проведения различий между управляемыми и неуправляемыми массивами требуется больше информации, чем для других преобразуемых типов.</span><span class="sxs-lookup"><span data-stu-id="25fec-109">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span>  
  
## <a name="managed-arrays"></a><span data-ttu-id="25fec-110">Управляемые массивы</span><span class="sxs-lookup"><span data-stu-id="25fec-110">Managed Arrays</span></span>  

 <span data-ttu-id="25fec-111">Управляемые массивы могут иметь разные типы, однако базовым для всех этих типов является класс <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="25fec-111">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="25fec-112">Класс **System.Array** имеет свойства, определяющие ранг, длину, нижнюю и верхнюю границы массива, а также методы доступа, сортировки, поиска, копирования и создания массивов.</span><span class="sxs-lookup"><span data-stu-id="25fec-112">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="25fec-113">Эти типы массивов являются динамическими и не имеют соответствующих статических типов в библиотеке базовых классов.</span><span class="sxs-lookup"><span data-stu-id="25fec-113">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="25fec-114">В качестве уникального типа массива удобно рассматривать сочетание типа элементов и ранга.</span><span class="sxs-lookup"><span data-stu-id="25fec-114">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="25fec-115">Соответственно, тип одномерного массива целых чисел отличается от типа одномерного массива чисел типа double.</span><span class="sxs-lookup"><span data-stu-id="25fec-115">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="25fec-116">Аналогичным образом, его тип будет отличаться от типа двухмерного массива целых чисел.</span><span class="sxs-lookup"><span data-stu-id="25fec-116">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="25fec-117">При сравнении типов не учитываются границы массивов.</span><span class="sxs-lookup"><span data-stu-id="25fec-117">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="25fec-118">Как показано в следующей таблице, любой экземпляр управляемого массива должен иметь заданные тип элементов, ранг и нижнюю границу.</span><span class="sxs-lookup"><span data-stu-id="25fec-118">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="25fec-119">Тип управляемого массива</span><span class="sxs-lookup"><span data-stu-id="25fec-119">Managed array type</span></span>|<span data-ttu-id="25fec-120">Тип элемента</span><span class="sxs-lookup"><span data-stu-id="25fec-120">Element type</span></span>|<span data-ttu-id="25fec-121">Ранг</span><span class="sxs-lookup"><span data-stu-id="25fec-121">Rank</span></span>|<span data-ttu-id="25fec-122">Нижняя граница</span><span class="sxs-lookup"><span data-stu-id="25fec-122">Lower bound</span></span>|<span data-ttu-id="25fec-123">Нотация сигнатуры</span><span class="sxs-lookup"><span data-stu-id="25fec-123">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="25fec-124">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="25fec-124">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="25fec-125">Задается по типу.</span><span class="sxs-lookup"><span data-stu-id="25fec-125">Specified by type.</span></span>|<span data-ttu-id="25fec-126">Задается по рангу.</span><span class="sxs-lookup"><span data-stu-id="25fec-126">Specified by rank.</span></span>|<span data-ttu-id="25fec-127">При необходимости задается границами.</span><span class="sxs-lookup"><span data-stu-id="25fec-127">Optionally specified by bounds.</span></span>|<span data-ttu-id="25fec-128">*тип* **[** *n*,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="25fec-128">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="25fec-129">**ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="25fec-129">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="25fec-130">Неизвестно</span><span class="sxs-lookup"><span data-stu-id="25fec-130">Unknown</span></span>|<span data-ttu-id="25fec-131">Неизвестно</span><span class="sxs-lookup"><span data-stu-id="25fec-131">Unknown</span></span>|<span data-ttu-id="25fec-132">Неизвестно</span><span class="sxs-lookup"><span data-stu-id="25fec-132">Unknown</span></span>|<span data-ttu-id="25fec-133">**System.Array**</span><span class="sxs-lookup"><span data-stu-id="25fec-133">**System.Array**</span></span>|  
|<span data-ttu-id="25fec-134">**ELEMENT_TYPE_SZARRAY**</span><span class="sxs-lookup"><span data-stu-id="25fec-134">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="25fec-135">Задается по типу.</span><span class="sxs-lookup"><span data-stu-id="25fec-135">Specified by type.</span></span>|<span data-ttu-id="25fec-136">1</span><span class="sxs-lookup"><span data-stu-id="25fec-136">1</span></span>|<span data-ttu-id="25fec-137">0</span><span class="sxs-lookup"><span data-stu-id="25fec-137">0</span></span>|<span data-ttu-id="25fec-138">*тип* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="25fec-138">*type* **[** *n* **]**</span></span>|  
  
## <a name="unmanaged-arrays"></a><span data-ttu-id="25fec-139">Неуправляемые массивы</span><span class="sxs-lookup"><span data-stu-id="25fec-139">Unmanaged Arrays</span></span>  

 <span data-ttu-id="25fec-140">Неуправляемыми могут быть безопасные массивы в стиле COM или массивы в стиле C фиксированной или переменной длины.</span><span class="sxs-lookup"><span data-stu-id="25fec-140">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="25fec-141">Безопасный массив — это описывающий сам себя массив, передающий тип, ранг и границы соответствующего массива данных.</span><span class="sxs-lookup"><span data-stu-id="25fec-141">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="25fec-142">Массивы в стиле C — это одномерные типизированные массивы с фиксированной нижней границей, равной 0.</span><span class="sxs-lookup"><span data-stu-id="25fec-142">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="25fec-143">Служба маршалинга обеспечивает ограниченную поддержку обоих типов массивов.</span><span class="sxs-lookup"><span data-stu-id="25fec-143">The marshaling service has limited support for both types of arrays.</span></span>  
  
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="25fec-144">Передача параметров массива в код .NET</span><span class="sxs-lookup"><span data-stu-id="25fec-144">Passing Array Parameters to .NET Code</span></span>  

 <span data-ttu-id="25fec-145">Массивы в стиле языка C и безопасные массивы могут передаваться в код .NET из неуправляемого кода в виде безопасных массивов или массивов в стиле C.</span><span class="sxs-lookup"><span data-stu-id="25fec-145">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="25fec-146">В следующей таблице показаны значения неуправляемого типа и соответствующих импортируемых типов.</span><span class="sxs-lookup"><span data-stu-id="25fec-146">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="25fec-147">Неуправляемый тип</span><span class="sxs-lookup"><span data-stu-id="25fec-147">Unmanaged type</span></span>|<span data-ttu-id="25fec-148">Импортируемый тип</span><span class="sxs-lookup"><span data-stu-id="25fec-148">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="25fec-149">**SafeArray(** *Тип* **)**</span><span class="sxs-lookup"><span data-stu-id="25fec-149">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="25fec-150">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="25fec-150">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="25fec-151">Ранг = 1, нижняя граница = 0.</span><span class="sxs-lookup"><span data-stu-id="25fec-151">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="25fec-152">Размер известен только в том случае, если он предоставлен в управляемой сигнатуре.</span><span class="sxs-lookup"><span data-stu-id="25fec-152">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="25fec-153">Безопасные массивы, ранг которых не равен 1, а нижняя граница не равна 0, не поддерживают маршалинг в виде **SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="25fec-153">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="25fec-154">*Type*  **[]**</span><span class="sxs-lookup"><span data-stu-id="25fec-154">*Type*  **[]**</span></span>|<span data-ttu-id="25fec-155">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="25fec-155">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="25fec-156">Ранг = 1, нижняя граница = 0.</span><span class="sxs-lookup"><span data-stu-id="25fec-156">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="25fec-157">Размер известен только в том случае, если он предоставлен в управляемой сигнатуре.</span><span class="sxs-lookup"><span data-stu-id="25fec-157">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="25fec-158">Безопасные массивы</span><span class="sxs-lookup"><span data-stu-id="25fec-158">Safe Arrays</span></span>  

 <span data-ttu-id="25fec-159">При импорте безопасного массива из библиотеки типов в сборку .NET он преобразуется в одномерный массив известного типа (например, **int**).</span><span class="sxs-lookup"><span data-stu-id="25fec-159">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="25fec-160">К элементам массива применяются те же правила преобразования типов, что и к параметрам.</span><span class="sxs-lookup"><span data-stu-id="25fec-160">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="25fec-161">Например, безопасный массив типов **BSTR** преобразуется в управляемый массив строк, а безопасный массив вариантов — в управляемый массив объектов.</span><span class="sxs-lookup"><span data-stu-id="25fec-161">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="25fec-162">Тип элементов **SAFEARRAY** получается из библиотеки типов и сохраняется в значении **SAFEARRAY** перечисления <xref:System.Runtime.InteropServices.UnmanagedType>.</span><span class="sxs-lookup"><span data-stu-id="25fec-162">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="25fec-163">Поскольку ранг и границы безопасного массива нельзя определить из библиотеки типов, предполагается, что ранг равен 1, а нижняя граница — 0.</span><span class="sxs-lookup"><span data-stu-id="25fec-163">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="25fec-164">Ранг и границы должны быть определены в управляемой сигнатуре, которая создается с помощью [программы импорта библиотек типов (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="25fec-164">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="25fec-165">Если ранг, переданный в метод во время выполнения, отличается, возникает исключение <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException>.</span><span class="sxs-lookup"><span data-stu-id="25fec-165">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="25fec-166">Если тип массива, переданный во время выполнения, отличается, возникает исключение <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException>.</span><span class="sxs-lookup"><span data-stu-id="25fec-166">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="25fec-167">В следующем примере показано применение безопасных массивов в управляемом и неуправляемом коде.</span><span class="sxs-lookup"><span data-stu-id="25fec-167">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="25fec-168">**Неуправляемая сигнатура**</span><span class="sxs-lookup"><span data-stu-id="25fec-168">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="25fec-169">**Управляемая сигнатура**</span><span class="sxs-lookup"><span data-stu-id="25fec-169">**Managed signature**</span></span>  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_I4)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_DATE)> _
   ar() As DateTime)  
Sub New3(ByRef <MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_BSTR)> _
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_I4)] int[] ar) ;  
void New2([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_DATE)]
   DateTime[] ar);  
void New3([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_BSTR)]
   ref String[] ar);  
```  
  
 <span data-ttu-id="25fec-170">Многомерные массивы или безопасные массивы с отличной от нуля границей могут маршалироваться в управляемый код, если сигнатура метода, создаваемая с помощью программы Tlbimp.exe, изменяется, указывая на тип элементов **ELEMENT_TYPE_ARRAY** вместо **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="25fec-170">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="25fec-171">Кроме того, можно использовать параметр **/sysarray** с программой Tlbimp.exe для импорта всех массивов в качестве объектов <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="25fec-171">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="25fec-172">Если передаваемый массив заведомо является многомерным, можно изменить код MSIL, создаваемый программой Tlbimp.exe, а затем повторно скомпилировать его.</span><span class="sxs-lookup"><span data-stu-id="25fec-172">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="25fec-173">Дополнительные сведения об изменении кода MSIL см. в разделе [Настройка вызываемых оболочек времени выполнения](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="25fec-173">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="25fec-174">Массивы в стиле C</span><span class="sxs-lookup"><span data-stu-id="25fec-174">C-Style Arrays</span></span>  

 <span data-ttu-id="25fec-175">При импорте массива в стиле C из библиотеки типов в сборку .NET массив преобразуется в **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="25fec-175">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="25fec-176">Тип элемента массива определяется из библиотеки типов и сохраняется во время импорта.</span><span class="sxs-lookup"><span data-stu-id="25fec-176">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="25fec-177">К элементам массива применяются те же правила преобразования, что и к параметрам.</span><span class="sxs-lookup"><span data-stu-id="25fec-177">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="25fec-178">Например, массив типов **LPStr** преобразуется в массив типов **String**.</span><span class="sxs-lookup"><span data-stu-id="25fec-178">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="25fec-179">Программа Tlbimp.exe получает тип элементов массива и применяет к параметру атрибут <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="25fec-179">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="25fec-180">Ранг массива принимается равным 1.</span><span class="sxs-lookup"><span data-stu-id="25fec-180">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="25fec-181">Если ранг больше 1, массив маршалируется как одномерный массив в развертывании по столбцам.</span><span class="sxs-lookup"><span data-stu-id="25fec-181">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="25fec-182">Нижняя граница всегда равна 0.</span><span class="sxs-lookup"><span data-stu-id="25fec-182">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="25fec-183">Библиотеки типов могут содержать массивы фиксированной или переменной длины.</span><span class="sxs-lookup"><span data-stu-id="25fec-183">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="25fec-184">Поскольку в библиотеках типов содержится недостаточно информации для маршалинга массивов переменной длины, программа Tlbimp.exe может импортировать из них только массивы фиксированной длины.</span><span class="sxs-lookup"><span data-stu-id="25fec-184">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="25fec-185">Для массивов фиксированной длины размер импортируется из библиотеки типов и сохраняется в атрибуте **MarshalAsAttribute**, который применяется к параметру.</span><span class="sxs-lookup"><span data-stu-id="25fec-185">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="25fec-186">Библиотеки типов, содержащие массивы переменной длины, необходимо определять вручную, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="25fec-186">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="25fec-187">**Неуправляемая сигнатура**</span><span class="sxs-lookup"><span data-stu-id="25fec-187">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="25fec-188">**Управляемая сигнатура**</span><span class="sxs-lookup"><span data-stu-id="25fec-188">**Managed signature**</span></span>  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.LPArray, SizeConst=10)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, SizeConst=200)> _  
   ar() As Double)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)> _  
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.LPArray, SizeConst=10)] int[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray, SizeConst=200)] double[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray,
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)] String[] ar);  
```  
  
 <span data-ttu-id="25fec-189">Несмотря на то, что с помощью атрибутов **size_is** или **length_is** массива в исходном коде на языке IDL можно передать сведения о размере клиенту, компилятор MIDL не передает эту информацию в библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="25fec-189">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="25fec-190">Не зная размера, служба маршалинга взаимодействия не может маршалировать элементы массива.</span><span class="sxs-lookup"><span data-stu-id="25fec-190">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="25fec-191">Таким образом, массивы переменной длины импортируются в виде ссылочных аргументов.</span><span class="sxs-lookup"><span data-stu-id="25fec-191">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="25fec-192">Пример:</span><span class="sxs-lookup"><span data-stu-id="25fec-192">For example:</span></span>  
  
 <span data-ttu-id="25fec-193">**Неуправляемая сигнатура**</span><span class="sxs-lookup"><span data-stu-id="25fec-193">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="25fec-194">**Управляемая сигнатура**</span><span class="sxs-lookup"><span data-stu-id="25fec-194">**Managed signature**</span></span>  
  
```vb  
Sub New1(ByRef ar As Integer)  
Sub New2(ByRef ar As Double)  
Sub New3(ByRef ar As String)  
```  
  
```csharp  
void New1(ref int ar);
void New2(ref double ar);
void New3(ref String ar);
```  
  
 <span data-ttu-id="25fec-195">Чтобы предоставить размер массива маршалеру, можно изменить код на языке MSIL, создаваемый программой Tlbimp.exe, после чего повторно скомпилировать его.</span><span class="sxs-lookup"><span data-stu-id="25fec-195">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="25fec-196">Дополнительные сведения об изменении кода MSIL см. в разделе [Настройка вызываемых оболочек времени выполнения](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="25fec-196">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span> <span data-ttu-id="25fec-197">Чтобы указать число элементов в массиве, примените тип <xref:System.Runtime.InteropServices.MarshalAsAttribute> к параметру массива в определении управляемого метода одним из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="25fec-197">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
- <span data-ttu-id="25fec-198">Определите еще один параметр, который содержит число элементов в массиве.</span><span class="sxs-lookup"><span data-stu-id="25fec-198">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="25fec-199">Параметры определяются по позиции, начиная с первого, который получает номер 0.</span><span class="sxs-lookup"><span data-stu-id="25fec-199">The parameters are identified by position, starting with the first parameter as number 0.</span></span>
  
    ```vb  
    Sub [New](ElemCnt As Integer, _  
       \<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       int ElemCnt,
       [MarshalAs(UnmanagedType.LPArray, SizeParamIndex=0)] int[] ar );  
    ```  
  
- <span data-ttu-id="25fec-200">Определите размер массива в виде константы.</span><span class="sxs-lookup"><span data-stu-id="25fec-200">Define the size of the array as a constant.</span></span> <span data-ttu-id="25fec-201">Пример:</span><span class="sxs-lookup"><span data-stu-id="25fec-201">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="25fec-202">При маршалинге массивов из неуправляемого в управляемый код маршалер проверяет связанный с параметром атрибут **MarshalAsAttribute**, чтобы определить размер массива.</span><span class="sxs-lookup"><span data-stu-id="25fec-202">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="25fec-203">Если размер массива не указан, выполняется маршалинг только одного элемента.</span><span class="sxs-lookup"><span data-stu-id="25fec-203">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25fec-204">Атрибут **MarshalAsAttribute** не учитывается при маршалинге управляемых массивов в неуправляемый код.</span><span class="sxs-lookup"><span data-stu-id="25fec-204">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="25fec-205">В этом направлении размер массива определяется с помощью проверки.</span><span class="sxs-lookup"><span data-stu-id="25fec-205">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="25fec-206">Маршалинг подмножества управляемого массива невозможен.</span><span class="sxs-lookup"><span data-stu-id="25fec-206">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="25fec-207">Маршалер взаимодействия использует методы **CoTaskMemAlloc** и **CoTaskMemFree** для выделения и высвобождения памяти.</span><span class="sxs-lookup"><span data-stu-id="25fec-207">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="25fec-208">Эти методы также необходимо использовать при выделении памяти в неуправляемом коде.</span><span class="sxs-lookup"><span data-stu-id="25fec-208">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
## <a name="passing-arrays-to-com"></a><span data-ttu-id="25fec-209">Передача массивов в COM</span><span class="sxs-lookup"><span data-stu-id="25fec-209">Passing Arrays to COM</span></span>  

 <span data-ttu-id="25fec-210">Все типы управляемых массивов можно передавать в неуправляемый код из управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="25fec-210">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="25fec-211">В зависимости от управляемого типа и примененных к нему атрибутов, доступ к массиву осуществляется как к безопасному массиву или как к массиву в стиле C, как показано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="25fec-211">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="25fec-212">Тип управляемого массива</span><span class="sxs-lookup"><span data-stu-id="25fec-212">Managed array type</span></span>|<span data-ttu-id="25fec-213">Экспортируется как</span><span class="sxs-lookup"><span data-stu-id="25fec-213">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="25fec-214">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span><span class="sxs-lookup"><span data-stu-id="25fec-214">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="25fec-215"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *тип* **)**</span><span class="sxs-lookup"><span data-stu-id="25fec-215"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="25fec-216">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="25fec-216">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="25fec-217">Тип предоставляется в сигнатуре.</span><span class="sxs-lookup"><span data-stu-id="25fec-217">Type is provided in the signature.</span></span> <span data-ttu-id="25fec-218">Ранг всегда равен 1, а нижняя граница всегда — 0.</span><span class="sxs-lookup"><span data-stu-id="25fec-218">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="25fec-219">Размер всегда известен во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="25fec-219">Size is always known at run time.</span></span>|  
|<span data-ttu-id="25fec-220">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>** [ **\<** *bounds* **>** ]</span><span class="sxs-lookup"><span data-stu-id="25fec-220">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="25fec-221">**UnmanagedType.SafeArray(** *тип* **)**</span><span class="sxs-lookup"><span data-stu-id="25fec-221">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="25fec-222">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="25fec-222">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="25fec-223">Тип, ранг и границы предоставляются в сигнатуре.</span><span class="sxs-lookup"><span data-stu-id="25fec-223">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="25fec-224">Размер всегда известен во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="25fec-224">Size is always known at run time.</span></span>|  
|<span data-ttu-id="25fec-225">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>\*\*</span><span class="sxs-lookup"><span data-stu-id="25fec-225">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>\*\*</span></span>|<span data-ttu-id="25fec-226">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="25fec-226">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="25fec-227">**UnmanagedType.SafeArray(** *тип* **)**</span><span class="sxs-lookup"><span data-stu-id="25fec-227">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="25fec-228">Тип, ранг, границы и размер всегда известны во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="25fec-228">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="25fec-229">В OLE-автоматизации существует ограничение в отношении массивов структур, которые содержат LPSTR или LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="25fec-229">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="25fec-230">Таким образом, поля **String** должны маршалироваться как **UnmanagedType.BSTR**.</span><span class="sxs-lookup"><span data-stu-id="25fec-230">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="25fec-231">В противном случае будет создаваться исключение.</span><span class="sxs-lookup"><span data-stu-id="25fec-231">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="element_type_szarray"></a><span data-ttu-id="25fec-232">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="25fec-232">ELEMENT_TYPE_SZARRAY</span></span>  

 <span data-ttu-id="25fec-233">При экспорте метода, содержащего параметр **ELEMENT_TYPE_SZARRAY** (одномерный массив), из сборки .NET в библиотеку типов параметр массива преобразуется в массив **SAFEARRAY** заданного типа.</span><span class="sxs-lookup"><span data-stu-id="25fec-233">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="25fec-234">Те же правила преобразования применяются к типам элементов массива.</span><span class="sxs-lookup"><span data-stu-id="25fec-234">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="25fec-235">Содержимое управляемого массива автоматически копируется из управляемой памяти в **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="25fec-235">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="25fec-236">Пример:</span><span class="sxs-lookup"><span data-stu-id="25fec-236">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="25fec-237">Управляемая сигнатура</span><span class="sxs-lookup"><span data-stu-id="25fec-237">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="25fec-238">Неуправляемая сигнатура</span><span class="sxs-lookup"><span data-stu-id="25fec-238">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="25fec-239">Ранг безопасных массивов всегда равен 1, а нижняя граница —0.</span><span class="sxs-lookup"><span data-stu-id="25fec-239">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="25fec-240">Размер определяется во время выполнения на основе размера передаваемого управляемого массива.</span><span class="sxs-lookup"><span data-stu-id="25fec-240">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="25fec-241">Массив также может маршалироваться как массив в стиле C с помощью атрибута <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="25fec-241">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="25fec-242">Пример:</span><span class="sxs-lookup"><span data-stu-id="25fec-242">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="25fec-243">Управляемая сигнатура</span><span class="sxs-lookup"><span data-stu-id="25fec-243">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As Long, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]
   long [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]
   String [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, ArraySubType=
   UnmanagedType.LPStr, SizeParamIndex=1)]
   String [] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="25fec-244">Неуправляемая сигнатура</span><span class="sxs-lookup"><span data-stu-id="25fec-244">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(BSTR ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="25fec-245">Несмотря на то, что маршалеру известна длина, необходимая для маршалинга массива, длина массива обычно передается вызываемому объекту в отдельном аргументе.</span><span class="sxs-lookup"><span data-stu-id="25fec-245">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="element_type_array"></a><span data-ttu-id="25fec-246">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="25fec-246">ELEMENT_TYPE_ARRAY</span></span>  

 <span data-ttu-id="25fec-247">При экспорте метода, содержащего параметр **ELEMENT_TYPE_ARRAY**, из сборки .NET в библиотеку типов параметр массива преобразуется в массив **SAFEARRAY** заданного типа.</span><span class="sxs-lookup"><span data-stu-id="25fec-247">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="25fec-248">Содержимое управляемого массива автоматически копируется из управляемой памяти в **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="25fec-248">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="25fec-249">Пример:</span><span class="sxs-lookup"><span data-stu-id="25fec-249">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="25fec-250">Управляемая сигнатура</span><span class="sxs-lookup"><span data-stu-id="25fec-250">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="25fec-251">Неуправляемая сигнатура</span><span class="sxs-lookup"><span data-stu-id="25fec-251">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="25fec-252">Ранг, размер и границы безопасного массива определяются во время выполнения на основе характеристик управляемого массива.</span><span class="sxs-lookup"><span data-stu-id="25fec-252">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="25fec-253">Массив также может маршалироваться как массив в стиле C с помощью атрибута <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="25fec-253">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="25fec-254">Пример:</span><span class="sxs-lookup"><span data-stu-id="25fec-254">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="25fec-255">Управляемая сигнатура</span><span class="sxs-lookup"><span data-stu-id="25fec-255">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex:=1)> _  
   ar(,) As Long, size As Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, _  
   ArraySubType:=UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar(,) As String, size As Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex=1)]
   long [,] ar, int size );  
void New([MarshalAs(UnmanagedType.LPARRAY,
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex=1)]
   String [,] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="25fec-256">Неуправляемая сигнатура</span><span class="sxs-lookup"><span data-stu-id="25fec-256">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="25fec-257">Вложенные массивы не поддерживают маршалирование.</span><span class="sxs-lookup"><span data-stu-id="25fec-257">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="25fec-258">Например, при экспорте с использованием [программы экспорта библиотеки типов (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) следующая сигнатура приводит к возникновению ошибки.</span><span class="sxs-lookup"><span data-stu-id="25fec-258">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="25fec-259">Управляемая сигнатура</span><span class="sxs-lookup"><span data-stu-id="25fec-259">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a><span data-ttu-id="25fec-260">ELEMENT_TYPE_CLASS \<System.Array></span><span class="sxs-lookup"><span data-stu-id="25fec-260">ELEMENT_TYPE_CLASS \<System.Array></span></span>  

 <span data-ttu-id="25fec-261">При экспорте метода, содержащего параметр <xref:System.Array?displayProperty=nameWithType>, из сборки .NET в библиотеку типов параметр массива преобразуется в интерфейс **_Array**.</span><span class="sxs-lookup"><span data-stu-id="25fec-261">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="25fec-262">Содержимое этого управляемого массива доступно только через методы и свойства интерфейса **_Array**.</span><span class="sxs-lookup"><span data-stu-id="25fec-262">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="25fec-263">Массив **System.Array** также может маршалироваться как **SAFEARRAY** с помощью атрибута <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="25fec-263">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="25fec-264">При маршалинге безопасного массива его элементы маршалируются как варианты.</span><span class="sxs-lookup"><span data-stu-id="25fec-264">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="25fec-265">Пример:</span><span class="sxs-lookup"><span data-stu-id="25fec-265">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="25fec-266">Управляемая сигнатура</span><span class="sxs-lookup"><span data-stu-id="25fec-266">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="25fec-267">Неуправляемая сигнатура</span><span class="sxs-lookup"><span data-stu-id="25fec-267">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] _Array *ar);
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="25fec-268">Массивы внутри структур</span><span class="sxs-lookup"><span data-stu-id="25fec-268">Arrays within Structures</span></span>  

 <span data-ttu-id="25fec-269">Неуправляемые структуры могут содержать вложенные массивы.</span><span class="sxs-lookup"><span data-stu-id="25fec-269">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="25fec-270">По умолчанию эти вложенные поля массива маршалируются как SAFEARRAY.</span><span class="sxs-lookup"><span data-stu-id="25fec-270">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="25fec-271">В следующем примере `s1` — это вложенный массив, который выделяется непосредственно в структуре.</span><span class="sxs-lookup"><span data-stu-id="25fec-271">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="25fec-272">Неуправляемое представление</span><span class="sxs-lookup"><span data-stu-id="25fec-272">Unmanaged representation</span></span>  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="25fec-273">Массивы могут маршалироваться как <xref:System.Runtime.InteropServices.UnmanagedType>, для чего необходимо установить поле <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="25fec-273">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="25fec-274">Размер может задаваться только в виде константы.</span><span class="sxs-lookup"><span data-stu-id="25fec-274">The size can be set only as a constant.</span></span> <span data-ttu-id="25fec-275">В коде ниже показаны соответствующие управляемые определения `MyStruct`.</span><span class="sxs-lookup"><span data-stu-id="25fec-275">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
```vb  
Public Structure <StructLayout(LayoutKind.Sequential)> MyStruct  
   Public <MarshalAs(UnmanagedType.ByValArray, SizeConst := 128)> _  
     s1() As Short  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MyStruct {  
   [MarshalAs(UnmanagedType.ByValArray, SizeConst=128)] public short[] s1;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="25fec-276">См. также</span><span class="sxs-lookup"><span data-stu-id="25fec-276">See also</span></span>

- [<span data-ttu-id="25fec-277">Характеристики маршалинга по умолчанию</span><span class="sxs-lookup"><span data-stu-id="25fec-277">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="25fec-278">Преобразуемые и непреобразуемые типы</span><span class="sxs-lookup"><span data-stu-id="25fec-278">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="25fec-279">[Directional Attributes](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100)) (Атрибуты направления)</span><span class="sxs-lookup"><span data-stu-id="25fec-279">[Directional Attributes](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="25fec-280">Копирование и закрепление</span><span class="sxs-lookup"><span data-stu-id="25fec-280">Copying and Pinning</span></span>](copying-and-pinning.md)
