---
title: Руководство по программированию на C#. Статические конструкторы
description: Статический конструктор в C# инициализирует статические данные или выполняет действие, выполняемое только один раз перед созданием первого экземпляра или ссылки на статические члены.
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: c224f96091e8fd5c51139757002ec8a67461a508
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898740"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="36d73-103">Статические конструкторы (Руководство по программированию в C#)</span><span class="sxs-lookup"><span data-stu-id="36d73-103">Static Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="36d73-104">Статический конструктор используется для инициализации любых [статических](../../language-reference/keywords/static.md) данных или для выполнения определенного действия, которое требуется выполнить только один раз.</span><span class="sxs-lookup"><span data-stu-id="36d73-104">A static constructor is used to initialize any [static](../../language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="36d73-105">Он вызывается автоматически перед созданием первого экземпляра или ссылкой на какие-либо статические члены.</span><span class="sxs-lookup"><span data-stu-id="36d73-105">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[SimpleClass#1](snippets/static-constructors/Program.cs#1)]

## <a name="remarks"></a><span data-ttu-id="36d73-106">Примечания</span><span class="sxs-lookup"><span data-stu-id="36d73-106">Remarks</span></span>

<span data-ttu-id="36d73-107">Статические конструкторы обладают следующими свойствами.</span><span class="sxs-lookup"><span data-stu-id="36d73-107">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="36d73-108">Статический конструктор не принимает модификаторы доступа и не имеет параметров.</span><span class="sxs-lookup"><span data-stu-id="36d73-108">A static constructor does not take access modifiers or have parameters.</span></span>  

- <span data-ttu-id="36d73-109">Класс или структура могут иметь только один статический конструктор.</span><span class="sxs-lookup"><span data-stu-id="36d73-109">A class or struct can only have one static constructor.</span></span>

- <span data-ttu-id="36d73-110">Статические конструкторы не могут быть унаследованы или перегружены.</span><span class="sxs-lookup"><span data-stu-id="36d73-110">Static constructors cannot be inherited or overloaded.</span></span>

- <span data-ttu-id="36d73-111">Статический конструктор нельзя вызывать напрямую. Он предназначен только для вызова из общеязыковой среды выполнения (CLR).</span><span class="sxs-lookup"><span data-stu-id="36d73-111">A static constructor cannot be called directly and is only meant to be called by the common language runtime (CLR).</span></span> <span data-ttu-id="36d73-112">Он запускается автоматически.</span><span class="sxs-lookup"><span data-stu-id="36d73-112">It is invoked automatically.</span></span>

- <span data-ttu-id="36d73-113">Пользователь не управляет временем, в течение которого статический конструктор выполняется в программе.</span><span class="sxs-lookup"><span data-stu-id="36d73-113">The user has no control on when the static constructor is executed in the program.</span></span>
  
- <span data-ttu-id="36d73-114">Статический конструктор вызывается автоматически для инициализации [класса](../../language-reference/keywords/class.md) перед созданием первого экземпляра типа или ссылкой на какие-либо статические члены.</span><span class="sxs-lookup"><span data-stu-id="36d73-114">A static constructor is called automatically to initialize the [class](../../language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span> <span data-ttu-id="36d73-115">Статический конструктор выполняется раньше, чем конструктор экземпляра.</span><span class="sxs-lookup"><span data-stu-id="36d73-115">A static constructor will run before an instance constructor.</span></span> <span data-ttu-id="36d73-116">Статический конструктор типа вызывается при вызове статического метода, назначенного делегату или событию, а не при его назначении.</span><span class="sxs-lookup"><span data-stu-id="36d73-116">A type's static constructor is called when a static method assigned to an event or a delegate is invoked and not when it is assigned.</span></span> <span data-ttu-id="36d73-117">Если в классе со статическим конструктором существуют переменные инициализаторы статических полей, они поочередно выполняются в том порядке, в котором включены в объявление класса, и сразу после этого выполняется статический конструктор.</span><span class="sxs-lookup"><span data-stu-id="36d73-117">If static field variable initializers are present in the class of the static constructor, they will be executed in the textual order in which they appear in the class declaration immediately prior to the execution of the static constructor.</span></span>

- <span data-ttu-id="36d73-118">Если вы не предоставили статический конструктор для инициализации статических полей, все статические поля инициализируются значениями по умолчанию, которые указаны в разделе [Значения по умолчанию типов C#](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="36d73-118">If you don't provide a static constructor to initialize static fields, all static fields are initialized to their default value as listed in [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span>
  
- <span data-ttu-id="36d73-119">Если статический конструктор инициирует исключение, среда выполнения не вызывает его во второй раз, и тип остается неинициализированным на время существования домена приложения, в котором выполняется программа.</span><span class="sxs-lookup"><span data-stu-id="36d73-119">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span> <span data-ttu-id="36d73-120">Чаще всего исключение <xref:System.TypeInitializationException> вызывается, когда статический конструктор не может создать экземпляр типа или в статическом конструкторе создается необработанное исключение.</span><span class="sxs-lookup"><span data-stu-id="36d73-120">Most commonly, a <xref:System.TypeInitializationException> exception is thrown when a static constructor is unable to instantiate a type or for an unhandled exception occurring within a static constructor.</span></span> <span data-ttu-id="36d73-121">Для устранения неполадок с неявными статическими конструкторами, которые не определены в исходном коде, может потребоваться проверка кода на промежуточном языке (IL).</span><span class="sxs-lookup"><span data-stu-id="36d73-121">For implicit static constructors that are not explicitly defined in source code, troubleshooting may require inspection of the intermediate language (IL) code.</span></span>

- <span data-ttu-id="36d73-122">Наличие статического конструктора не позволяет добавлять атрибут типа <xref:System.Reflection.TypeAttributes.BeforeFieldInit>.</span><span class="sxs-lookup"><span data-stu-id="36d73-122">The presence of a static constructor prevents the addition of the <xref:System.Reflection.TypeAttributes.BeforeFieldInit> type attribute.</span></span> <span data-ttu-id="36d73-123">Это ограничивает возможности оптимизации во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="36d73-123">This limits runtime optimization.</span></span>

- <span data-ttu-id="36d73-124">Поле, объявленное как `static readonly`, может быть присвоено только при его объявлении или в статическом конструкторе.</span><span class="sxs-lookup"><span data-stu-id="36d73-124">A field declared as `static readonly` may only be assigned as part of its declaration or in a static constructor.</span></span> <span data-ttu-id="36d73-125">Если явный статический конструктор не является обязательным, инициализируйте статические поля в объявлении, а не через статический конструктор, чтобы сохранить больше возможностей для оптимизации в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="36d73-125">When an explicit static constructor is not required, initialize static fields at declaration, rather than through a static constructor for better runtime optimization.</span></span>

> [!Note]
> <span data-ttu-id="36d73-126">Наличие явного статического конструктора следует документировать, несмотря на отсутствие прямого доступа к нему, поскольку это важно для устранения неполадок с исключениями при инициализации.</span><span class="sxs-lookup"><span data-stu-id="36d73-126">Though not directly accessible, the presence of an explicit static constructor should be documented to assist with troubleshooting initialization exceptions.</span></span>

### <a name="usage"></a><span data-ttu-id="36d73-127">Использование</span><span class="sxs-lookup"><span data-stu-id="36d73-127">Usage</span></span>

- <span data-ttu-id="36d73-128">Типичным использованием статических конструкторов является случай, когда класс использует файл журнала и конструктор применяется для добавления записей в этот файл.</span><span class="sxs-lookup"><span data-stu-id="36d73-128">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
- <span data-ttu-id="36d73-129">Статические конструкторы также полезны при создании классов-оболочек для неуправляемого кода, когда конструктор может вызвать метод `LoadLibrary`.</span><span class="sxs-lookup"><span data-stu-id="36d73-129">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  

- <span data-ttu-id="36d73-130">Статические конструкторы очень удобны для применения в среде выполнения проверок параметра типа, которые невозможно проверить с помощью ограничений во время компиляции (ограничения параметров типа).</span><span class="sxs-lookup"><span data-stu-id="36d73-130">Static constructors are also a convenient place to enforce run-time checks on the type parameter that cannot be checked at compile time via constraints (Type parameter constraints).</span></span>

## <a name="example"></a><span data-ttu-id="36d73-131">Пример</span><span class="sxs-lookup"><span data-stu-id="36d73-131">Example</span></span>

 <span data-ttu-id="36d73-132">В этом примере класс `Bus` имеет статический конструктор.</span><span class="sxs-lookup"><span data-stu-id="36d73-132">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="36d73-133">При создании первого экземпляра класса `Bus` (`bus1`) для инициализации класса вызывается статический конструктор.</span><span class="sxs-lookup"><span data-stu-id="36d73-133">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="36d73-134">В выходных данных этого примера можно увидеть, что статический конструктор выполняется только один раз, несмотря на то, что создается два экземпляра класса `Bus`. Кроме того, этот конструктор вызывается до выполнения конструктора экземпляра.</span><span class="sxs-lookup"><span data-stu-id="36d73-134">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[BusSample#2](snippets/static-constructors/Program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="36d73-135">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="36d73-135">C# language specification</span></span>

<span data-ttu-id="36d73-136">Дополнительные сведения см. в разделе [Статические конструктор](~/_csharplang/spec/classes.md#static-constructors) в [спецификации языка C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="36d73-136">For more information, see the [Static constructors](~/_csharplang/spec/classes.md#static-constructors) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="36d73-137">См. также</span><span class="sxs-lookup"><span data-stu-id="36d73-137">See also</span></span>

- [<span data-ttu-id="36d73-138">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="36d73-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="36d73-139">Классы и структуры</span><span class="sxs-lookup"><span data-stu-id="36d73-139">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="36d73-140">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="36d73-140">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="36d73-141">Статические классы и члены статических классов</span><span class="sxs-lookup"><span data-stu-id="36d73-141">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="36d73-142">Методы завершения</span><span class="sxs-lookup"><span data-stu-id="36d73-142">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="36d73-143">Рекомендации по разработке конструкторов</span><span class="sxs-lookup"><span data-stu-id="36d73-143">Constructor Design Guidelines</span></span>](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [<span data-ttu-id="36d73-144">Предупреждение о безопасности CA2121. Статические конструкторы должны быть частными</span><span class="sxs-lookup"><span data-stu-id="36d73-144">Security Warning - CA2121: Static constructors should be private</span></span>](/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
