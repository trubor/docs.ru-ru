---
title: Создание класса, содержащего функции DLL
description: Создайте управляемую оболочку класса в .NET для хранения функций DLL, которые помогают инкапсулировать функции платформы.
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
ms.openlocfilehash: c255efe4579635389ac62956cac9d1405bfb184c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271438"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="54e74-103">Создание класса, содержащего функции DLL</span><span class="sxs-lookup"><span data-stu-id="54e74-103">Creating a Class to Hold DLL Functions</span></span>

<span data-ttu-id="54e74-104">Упаковка часто используемых функций DLL в управляемый класс позволяет эффективно инкапсулировать функциональные возможности платформы.</span><span class="sxs-lookup"><span data-stu-id="54e74-104">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="54e74-105">Делать это в каждом случае необязательно, однако использование оболочки класса удобно, поскольку определение функций DLL может быть затруднительно и нередко приводит к ошибкам.</span><span class="sxs-lookup"><span data-stu-id="54e74-105">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="54e74-106">При программировании на языке Visual Basic или C# необходимо объявлять функции DLL в классе или модуле Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="54e74-106">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="54e74-107">В классе определяется статический метод для каждой функции DLL, которую требуется вызывать.</span><span class="sxs-lookup"><span data-stu-id="54e74-107">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="54e74-108">Определение может включать дополнительные сведения, в том числе кодировку или соглашение о вызовах, используемые при передаче аргументов метода. Если эти сведения не указаны, используются параметры по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="54e74-108">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="54e74-109">Полный список параметров объявления и их значений по умолчанию см. в разделе [Создание прототипов в управляемом коде](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="54e74-109">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="54e74-110">После упаковки вы можете вызывать методы для этого класса так же, как и статические методы для любого другого класса.</span><span class="sxs-lookup"><span data-stu-id="54e74-110">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="54e74-111">При вызове неуправляемого кода базовая экспортированная функция обрабатывается автоматически.</span><span class="sxs-lookup"><span data-stu-id="54e74-111">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="54e74-112">При разработке управляемого класса для вызова неуправляемого кода следует учитывать отношения между классами и функциями DLL.</span><span class="sxs-lookup"><span data-stu-id="54e74-112">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="54e74-113">Например, с их помощью можно выполнять следующее.</span><span class="sxs-lookup"><span data-stu-id="54e74-113">For example, you can:</span></span>  
  
- <span data-ttu-id="54e74-114">Объявлять функции DLL в существующем классе.</span><span class="sxs-lookup"><span data-stu-id="54e74-114">Declare DLL functions within an existing class.</span></span>  
  
- <span data-ttu-id="54e74-115">Создавать отдельный класс для каждой функции DLL, обеспечивая изоляцию и удобство поиска функций.</span><span class="sxs-lookup"><span data-stu-id="54e74-115">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
- <span data-ttu-id="54e74-116">Создавать один класс для набора связанных функций DLL, что позволяет упорядочивать их по логическим группам и снизить затраты на ресурсы.</span><span class="sxs-lookup"><span data-stu-id="54e74-116">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="54e74-117">Имена класса и его методов могут быть произвольными.</span><span class="sxs-lookup"><span data-stu-id="54e74-117">You can name the class and its methods as you please.</span></span> <span data-ttu-id="54e74-118">Примеры, демонстрирующие создание объявлений на основе .NET, которые используются с вызовом неуправляемого кода, см. в разделе [Маршалинг данных при вызове неуправляемого кода](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="54e74-118">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54e74-119">См. также</span><span class="sxs-lookup"><span data-stu-id="54e74-119">See also</span></span>

- [<span data-ttu-id="54e74-120">Использование неуправляемых функций DLL</span><span class="sxs-lookup"><span data-stu-id="54e74-120">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="54e74-121">Идентификация функций в библиотеках DLL</span><span class="sxs-lookup"><span data-stu-id="54e74-121">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="54e74-122">Создание прототипов в управляемом коде</span><span class="sxs-lookup"><span data-stu-id="54e74-122">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="54e74-123">Вызов функции DLL</span><span class="sxs-lookup"><span data-stu-id="54e74-123">Calling a DLL Function</span></span>](calling-a-dll-function.md)
