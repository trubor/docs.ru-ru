---
title: Практическое руководство. Реализация и вызов пользовательского метода расширения (руководство по программированию на C#)
description: Узнайте, как реализовать методы расширения для любого типа .NET. Клиентский код может использовать ваши методы путем добавления ссылки на содержащую их библиотеку DLL и добавления директивы using.
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 4ae48a05d451a3276b3a0f2ee4d6c633ce7db306
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513018"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="725e7-104">Практическое руководство. Реализация и вызов пользовательского метода расширения (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="725e7-104">How to implement and call a custom extension method (C# Programming Guide)</span></span>

<span data-ttu-id="725e7-105">Этот раздел описывает, как реализовать свои методы расширения для любого типа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="725e7-105">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="725e7-106">Клиентский код может использовать методы расширения путем добавления ссылки на содержащую их библиотеку DLL и добавления директивы [using](../../language-reference/keywords/using-directive.md), которая указывает пространство имен, в котором определены методы расширения.</span><span class="sxs-lookup"><span data-stu-id="725e7-106">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="725e7-107">Определение и вызов метода расширения</span><span class="sxs-lookup"><span data-stu-id="725e7-107">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="725e7-108">Определите статический [класс](./static-classes-and-static-class-members.md), который будет содержать метод расширения.</span><span class="sxs-lookup"><span data-stu-id="725e7-108">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="725e7-109">Класс должен быть видимым для клиентского кода.</span><span class="sxs-lookup"><span data-stu-id="725e7-109">The class must be visible to client code.</span></span> <span data-ttu-id="725e7-110">Дополнительные сведения о правилах доступа см. в разделах [Модификаторы доступа](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="725e7-110">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="725e7-111">Реализуйте метод расширения как статический метод как минимум с тем же уровнем видимости, что и содержащий класс.</span><span class="sxs-lookup"><span data-stu-id="725e7-111">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="725e7-112">Первый параметр метода указывает тип, с которым работает метод. Ему должен предшествовать модификатор [this](../../language-reference/keywords/this.md).</span><span class="sxs-lookup"><span data-stu-id="725e7-112">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="725e7-113">В вызывающем коде добавьте директиву `using`, чтобы задать [пространство имен](../../language-reference/keywords/namespace.md), содержащее класс метода расширения.</span><span class="sxs-lookup"><span data-stu-id="725e7-113">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="725e7-114">Вызовите методы, как если бы они являлись методами экземпляра для типа.</span><span class="sxs-lookup"><span data-stu-id="725e7-114">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="725e7-115">Обратите внимание, что первый параметр не указан вызывающим кодом, поскольку он представляет тип, к которому применяется оператор, и компилятору уже известен тип объекта.</span><span class="sxs-lookup"><span data-stu-id="725e7-115">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="725e7-116">Вам необходимо предоставить аргументы только для параметров со 2 по `n`.</span><span class="sxs-lookup"><span data-stu-id="725e7-116">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="725e7-117">Пример</span><span class="sxs-lookup"><span data-stu-id="725e7-117">Example</span></span>  

 <span data-ttu-id="725e7-118">В приведенном ниже примере реализуется метод расширения с именем `WordCount` в классе `CustomExtensions.StringExtension`.</span><span class="sxs-lookup"><span data-stu-id="725e7-118">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="725e7-119">Метод работает с классом <xref:System.String> класса, который указан как первый параметр метода.</span><span class="sxs-lookup"><span data-stu-id="725e7-119">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="725e7-120">Пространство имен `CustomExtensions` импортируется в пространство имен приложения, и метод вызывается внутри метода `Main`.</span><span class="sxs-lookup"><span data-stu-id="725e7-120">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-security"></a><span data-ttu-id="725e7-121">Безопасность .NET</span><span class="sxs-lookup"><span data-stu-id="725e7-121">.NET Security</span></span>  

 <span data-ttu-id="725e7-122">Методы расширения не предоставляют определенных уязвимостей безопасности.</span><span class="sxs-lookup"><span data-stu-id="725e7-122">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="725e7-123">Они не могут использоваться для олицетворения существующих методов для типа, поскольку все конфликты имен разрешаются в пользу метода экземпляра или статического метода, определяемого самим типом.</span><span class="sxs-lookup"><span data-stu-id="725e7-123">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="725e7-124">Методы расширения не могут получить доступ к любым конфиденциальным данным в расширенном классе.</span><span class="sxs-lookup"><span data-stu-id="725e7-124">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="725e7-125">См. также</span><span class="sxs-lookup"><span data-stu-id="725e7-125">See also</span></span>

- [<span data-ttu-id="725e7-126">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="725e7-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="725e7-127">Методы расширения</span><span class="sxs-lookup"><span data-stu-id="725e7-127">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="725e7-128">Встроенный язык запросов LINQ</span><span class="sxs-lookup"><span data-stu-id="725e7-128">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="725e7-129">Статические классы и члены статических классов</span><span class="sxs-lookup"><span data-stu-id="725e7-129">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="725e7-130">protected</span><span class="sxs-lookup"><span data-stu-id="725e7-130">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="725e7-131">internal</span><span class="sxs-lookup"><span data-stu-id="725e7-131">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="725e7-132">public</span><span class="sxs-lookup"><span data-stu-id="725e7-132">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="725e7-133">this</span><span class="sxs-lookup"><span data-stu-id="725e7-133">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="725e7-134">namespace</span><span class="sxs-lookup"><span data-stu-id="725e7-134">namespace</span></span>](../../language-reference/keywords/namespace.md)
