---
title: Использование неуправляемых функций DLL
description: Использование неуправляемых функций DLL с помощью службы вызова неуправляемого кода, которая позволяет управляемому коду вызывать неуправляемые функции, реализованные в библиотеках DLL.
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- platform invoke, about platform invoke
- DLL functions, consuming unmanaged
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke
- DLL functions
ms.assetid: eca7606e-ebfb-4f47-b8d9-289903fdc045
ms.openlocfilehash: ea4008db59e580fc9d68135618f292496e96fce9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96282942"
---
# <a name="consuming-unmanaged-dll-functions"></a><span data-ttu-id="0760a-103">Использование неуправляемых функций DLL</span><span class="sxs-lookup"><span data-stu-id="0760a-103">Consuming Unmanaged DLL Functions</span></span>

<span data-ttu-id="0760a-104">Вызов неуправляемого кода — это служба, позволяющая управляемому коду вызывать неуправляемые функции, реализованные в библиотеках динамической компоновки (DLL), например функции библиотек API Windows.</span><span class="sxs-lookup"><span data-stu-id="0760a-104">Platform invoke is a service that enables managed code to call unmanaged functions implemented in dynamic link libraries (DLLs), such as those in the Windows API.</span></span> <span data-ttu-id="0760a-105">Он обнаруживает и вызывает экспортированную функцию и при необходимости маршалирует ее аргументы (целые числа, строки, массивы, структуры и так далее) через границы взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="0760a-105">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="0760a-106">В этом разделе описаны задачи, связанные с использованием неуправляемых функций DLL, и предоставляются дополнительные сведения о вызове неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="0760a-106">This section introduces tasks associated with consuming unmanaged DLL functions and provides more information about platform invoke.</span></span> <span data-ttu-id="0760a-107">Кроме того, раздел содержит общие сведения и ссылки на дополнительную информацию и примеры.</span><span class="sxs-lookup"><span data-stu-id="0760a-107">In addition to the following tasks, there are general considerations and a link providing additional information and examples.</span></span>  
  
#### <a name="to-consume-exported-dll-functions"></a><span data-ttu-id="0760a-108">Использование экспортированных функций DLL</span><span class="sxs-lookup"><span data-stu-id="0760a-108">To consume exported DLL functions</span></span>  
  
1. <span data-ttu-id="0760a-109">[Идентификация функций в библиотеках DLL](identifying-functions-in-dlls.md).</span><span class="sxs-lookup"><span data-stu-id="0760a-109">[Identify functions in DLLs](identifying-functions-in-dlls.md).</span></span>  
  
     <span data-ttu-id="0760a-110">Как минимум, необходимо указать имя функции и имя библиотеки DLL, содержащей ее.</span><span class="sxs-lookup"><span data-stu-id="0760a-110">Minimally, you must specify the name of the function and name of the DLL that contains it.</span></span>  
  
2. <span data-ttu-id="0760a-111">[Создание класса, содержащего функции DLL](creating-a-class-to-hold-dll-functions.md).</span><span class="sxs-lookup"><span data-stu-id="0760a-111">[Create a class to hold DLL functions](creating-a-class-to-hold-dll-functions.md).</span></span>  
  
     <span data-ttu-id="0760a-112">Можно использовать существующий класс, создать отдельный класс для каждой неуправляемой функции или создать один класс, содержащий набор связанных неуправляемых функций.</span><span class="sxs-lookup"><span data-stu-id="0760a-112">You can use an existing class, create an individual class for each unmanaged function, or create one class that contains a set of related unmanaged functions.</span></span>  
  
3. <span data-ttu-id="0760a-113">[Создание прототипов в управляемом коде](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="0760a-113">[Create prototypes in managed code](creating-prototypes-in-managed-code.md).</span></span>  
  
     <span data-ttu-id="0760a-114">[Visual Basic] Используйте оператор **Declare** с ключевыми словами **Function** и **Lib**.</span><span class="sxs-lookup"><span data-stu-id="0760a-114">[Visual Basic] Use the **Declare** statement with the **Function** and **Lib** keywords.</span></span> <span data-ttu-id="0760a-115">В редких случаях можно использовать атрибут **DllImportAttribute** с ключевыми словами **Shared Function**.</span><span class="sxs-lookup"><span data-stu-id="0760a-115">In some rare cases, you can use the **DllImportAttribute** with the **Shared Function** keywords.</span></span> <span data-ttu-id="0760a-116">Такие случаи рассматриваются далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="0760a-116">These cases are explained later in this section.</span></span>  
  
     <span data-ttu-id="0760a-117">[C#] Используйте атрибут **DllImportAttribute** для идентификации библиотеки DLL и функции.</span><span class="sxs-lookup"><span data-stu-id="0760a-117">[C#] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="0760a-118">Пометьте метод модификаторами **static** и **extern**.</span><span class="sxs-lookup"><span data-stu-id="0760a-118">Mark the method with the **static** and **extern** modifiers.</span></span>  
  
     <span data-ttu-id="0760a-119">[C++] Используйте атрибут **DllImportAttribute** для идентификации библиотеки DLL и функции.</span><span class="sxs-lookup"><span data-stu-id="0760a-119">[C++] Use the **DllImportAttribute** to identify the DLL and function.</span></span> <span data-ttu-id="0760a-120">Пометьте метод или функцию оболочки модификатором **extern "C"** .</span><span class="sxs-lookup"><span data-stu-id="0760a-120">Mark the wrapper method or function with **extern "C"**.</span></span>  
  
4. <span data-ttu-id="0760a-121">[Вызов функции DLL](calling-a-dll-function.md).</span><span class="sxs-lookup"><span data-stu-id="0760a-121">[Call a DLL function](calling-a-dll-function.md).</span></span>  
  
     <span data-ttu-id="0760a-122">Вызовите метод управляемого класса так же, как и любой другой управляемый метод.</span><span class="sxs-lookup"><span data-stu-id="0760a-122">Call the method on your managed class as you would any other managed method.</span></span> <span data-ttu-id="0760a-123">[Передача структур](passing-structures.md) и [реализация функций обратного вызова](callback-functions.md) представляют собой особые случаи.</span><span class="sxs-lookup"><span data-stu-id="0760a-123">[Passing structures](passing-structures.md) and [implementing callback functions](callback-functions.md) are special cases.</span></span>  
  
 <span data-ttu-id="0760a-124">Примеры, демонстрирующие создание объявлений на основе .NET, которые используются с вызовом неуправляемого кода, см. в разделе [Маршалинг данных при вызове неуправляемого кода](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="0760a-124">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="a-closer-look-at-platform-invoke"></a><span data-ttu-id="0760a-125">Подробный обзор вызова неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="0760a-125">A closer look at platform invoke</span></span>  

 <span data-ttu-id="0760a-126">Вызов неуправляемого кода использует метаданные для нахождения экспортированных функций и маршалинга их аргументов во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="0760a-126">Platform invoke relies on metadata to locate exported functions and marshal their arguments at run time.</span></span> <span data-ttu-id="0760a-127">Данный процесс показан на следующем рисунке.</span><span class="sxs-lookup"><span data-stu-id="0760a-127">The following illustration shows this process.</span></span>  
  
 ![Схема, показывающая вызов неуправляемого кода.](./media/consuming-unmanaged-dll-functions/platform-invoke-call.gif)  
  
 <span data-ttu-id="0760a-129">Когда неуправляемый код вызывает неуправляемую функцию, то он выполняет следующую последовательность действий:</span><span class="sxs-lookup"><span data-stu-id="0760a-129">When platform invoke calls an unmanaged function, it performs the following sequence of actions:</span></span>  
  
1. <span data-ttu-id="0760a-130">Определяет библиотеку DLL, содержащую функцию.</span><span class="sxs-lookup"><span data-stu-id="0760a-130">Locates the DLL containing the function.</span></span>  
  
2. <span data-ttu-id="0760a-131">Загружает библиотеку DLL в память.</span><span class="sxs-lookup"><span data-stu-id="0760a-131">Loads the DLL into memory.</span></span>  
  
3. <span data-ttu-id="0760a-132">Находит адрес функции в памяти и помещает ее аргументы в стек, выполнив по необходимости маршалинг данных.</span><span class="sxs-lookup"><span data-stu-id="0760a-132">Locates the address of the function in memory and pushes its arguments onto the stack, marshaling data as required.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0760a-133">Поиск и загрузка библиотеки DLL, а также определение адреса функции в памяти выполняются только при первом вызове функции.</span><span class="sxs-lookup"><span data-stu-id="0760a-133">Locating and loading the DLL, and locating the address of the function in memory occur only on the first call to the function.</span></span>  
  
4. <span data-ttu-id="0760a-134">Передает управление неуправляемой функции.</span><span class="sxs-lookup"><span data-stu-id="0760a-134">Transfers control to the unmanaged function.</span></span>  
  
 <span data-ttu-id="0760a-135">Вызов неуправляемого кода вызывает исключения, создаваемые неуправляемой функцией для управляемого вызывающего объекта.</span><span class="sxs-lookup"><span data-stu-id="0760a-135">Platform invoke throws exceptions generated by the unmanaged function to the managed caller.</span></span>

## <a name="see-also"></a><span data-ttu-id="0760a-136">См. также</span><span class="sxs-lookup"><span data-stu-id="0760a-136">See also</span></span>

- [<span data-ttu-id="0760a-137">Взаимодействие с неуправляемым кодом</span><span class="sxs-lookup"><span data-stu-id="0760a-137">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="0760a-138">Примеры вызовов неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="0760a-138">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="0760a-139">Маршалинг взаимодействия</span><span class="sxs-lookup"><span data-stu-id="0760a-139">Interop Marshaling</span></span>](interop-marshaling.md)
