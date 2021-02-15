---
description: 'Дополнительные сведения: Visual Basic соглашения о написании кода'
title: Соглашения о написании кода
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: 424871ab0e77629ded977bd0be768ed8736d1761
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460037"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="2df58-103">Соглашения о написании кода в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2df58-103">Visual Basic Coding Conventions</span></span>

<span data-ttu-id="2df58-104">Корпорация Майкрософт разрабатывает образцы и документацию, которые соответствуют рекомендациям, приведенным в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="2df58-104">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="2df58-105">Если следовать тем же соглашениям о написании кода, вы можете получить следующие преимущества:</span><span class="sxs-lookup"><span data-stu-id="2df58-105">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
- <span data-ttu-id="2df58-106">Ваш код будет иметь единообразный вид, чтобы читатели могли лучше сосредоточиться на содержимом, а не на макете.</span><span class="sxs-lookup"><span data-stu-id="2df58-106">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
- <span data-ttu-id="2df58-107">Читатели смогут быстрее понять код, так как они могут делать предположения на основе предыдущего опыта.</span><span class="sxs-lookup"><span data-stu-id="2df58-107">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="2df58-108">Вы можете легко копировать, изменять и обслуживать код.</span><span class="sxs-lookup"><span data-stu-id="2df58-108">You can copy, change, and maintain the code more easily.</span></span>  
  
- <span data-ttu-id="2df58-109">Вы сможете убедиться в том, что код демонстрирует "рекомендации" для Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2df58-109">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="2df58-110">Соглашения об именах</span><span class="sxs-lookup"><span data-stu-id="2df58-110">Naming Conventions</span></span>  
  
- <span data-ttu-id="2df58-111">Сведения о правилах именования см. в разделе [рекомендации по именованию](../../../standard/design-guidelines/naming-guidelines.md) .</span><span class="sxs-lookup"><span data-stu-id="2df58-111">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
- <span data-ttu-id="2df58-112">Не используйте "My" или "My" как часть имени переменной.</span><span class="sxs-lookup"><span data-stu-id="2df58-112">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="2df58-113">Такой подход создает путаницу с `My` объектами.</span><span class="sxs-lookup"><span data-stu-id="2df58-113">This practice creates confusion with the `My` objects.</span></span>  
  
- <span data-ttu-id="2df58-114">Не нужно изменять имена объектов в автоматически создаваемом коде, чтобы они соответствовали рекомендациям.</span><span class="sxs-lookup"><span data-stu-id="2df58-114">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="2df58-115">Соглашения о расположении</span><span class="sxs-lookup"><span data-stu-id="2df58-115">Layout Conventions</span></span>  
  
- <span data-ttu-id="2df58-116">Вставьте табуляцию в качестве пробелов и используйте интеллектуальные отступы с отступами в четырех пробелах.</span><span class="sxs-lookup"><span data-stu-id="2df58-116">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
- <span data-ttu-id="2df58-117">Чтобы переформатировать код в редакторе кода, используйте **достаточное переформатирование** .</span><span class="sxs-lookup"><span data-stu-id="2df58-117">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="2df58-118">Дополнительные сведения см. в разделе [Параметры, текстовый редактор, базовый (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2df58-118">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
- <span data-ttu-id="2df58-119">Используйте только один оператор в строке.</span><span class="sxs-lookup"><span data-stu-id="2df58-119">Use only one statement per line.</span></span> <span data-ttu-id="2df58-120">Не используйте Visual Basic символ разделителя строки (:).</span><span class="sxs-lookup"><span data-stu-id="2df58-120">Don't use the Visual Basic line separator character (:).</span></span>  
  
- <span data-ttu-id="2df58-121">Старайтесь не использовать явный символ продолжения строки "_" в пользу неявного продолжения строки везде, где это разрешено языком.</span><span class="sxs-lookup"><span data-stu-id="2df58-121">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
- <span data-ttu-id="2df58-122">Используйте только одно объявление в строке.</span><span class="sxs-lookup"><span data-stu-id="2df58-122">Use only one declaration per line.</span></span>  
  
- <span data-ttu-id="2df58-123">Если **Перечисление (переформатирование) кода** не приводит к автоматическому форматированию строк продолжения, следует вручную задать отступ для строк продолжения на одну позицию табуляции.</span><span class="sxs-lookup"><span data-stu-id="2df58-123">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="2df58-124">Однако всегда выровняйте элементы в списке по левому краю.</span><span class="sxs-lookup"><span data-stu-id="2df58-124">However, always left-align items in a list.</span></span>  
  
    ```vb  
    a As Integer,  
    b As Integer  
    ```  
  
- <span data-ttu-id="2df58-125">Добавьте хотя бы одну пустую строку между определениями методов и свойств.</span><span class="sxs-lookup"><span data-stu-id="2df58-125">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="2df58-126">Соглашения о комментариях</span><span class="sxs-lookup"><span data-stu-id="2df58-126">Commenting Conventions</span></span>  
  
- <span data-ttu-id="2df58-127">Заключите комментарии в отдельную строку, а не в конец строки кода.</span><span class="sxs-lookup"><span data-stu-id="2df58-127">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
- <span data-ttu-id="2df58-128">Начинать текст комментария с прописной буквы и заканчивать текст комментария точкой.</span><span class="sxs-lookup"><span data-stu-id="2df58-128">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
- <span data-ttu-id="2df58-129">Вставьте один пробел между разделителем комментария (') и текстом комментария.</span><span class="sxs-lookup"><span data-stu-id="2df58-129">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- <span data-ttu-id="2df58-130">Не заключайте комментарии в форматированные блоки звездочек.</span><span class="sxs-lookup"><span data-stu-id="2df58-130">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="2df58-131">Структура программы</span><span class="sxs-lookup"><span data-stu-id="2df58-131">Program Structure</span></span>  
  
- <span data-ttu-id="2df58-132">При использовании `Main` метода используйте конструкцию по умолчанию для новых консольных приложений и используйте `My` для аргументов командной строки.</span><span class="sxs-lookup"><span data-stu-id="2df58-132">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="2df58-133">Рекомендации по работе с языком</span><span class="sxs-lookup"><span data-stu-id="2df58-133">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="2df58-134">Тип данных String</span><span class="sxs-lookup"><span data-stu-id="2df58-134">String Data Type</span></span>  
  
- <span data-ttu-id="2df58-135">Для сцепления коротких строк рекомендуется использовать [интерполяцию строк](../language-features/strings/interpolated-strings.md), как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="2df58-135">Use [string interpolation](../language-features/strings/interpolated-strings.md) to concatenate short strings, as shown in the following code.</span></span>
  
     ```vb
     MsgBox($"hello{vbCrLf}goodbye")
     ```
  
- <span data-ttu-id="2df58-136">Чтобы добавить строки в циклы, используйте <xref:System.Text.StringBuilder> объект.</span><span class="sxs-lookup"><span data-stu-id="2df58-136">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="2df58-137">Ослабленные делегаты в обработчиках событий</span><span class="sxs-lookup"><span data-stu-id="2df58-137">Relaxed Delegates in Event Handlers</span></span>  

 <span data-ttu-id="2df58-138">Не следует явно уточнять аргументы (объект и EventArgs) обработчиками событий.</span><span class="sxs-lookup"><span data-stu-id="2df58-138">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="2df58-139">Если вы не используете аргументы события, передаваемые в событие (например, отправитель как объект, e как EventArgs), используйте ослабленные делегаты и оставьте аргументы событий в коде:</span><span class="sxs-lookup"><span data-stu-id="2df58-139">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="2df58-140">Беззнаковый тип данных</span><span class="sxs-lookup"><span data-stu-id="2df58-140">Unsigned Data Type</span></span>  
  
- <span data-ttu-id="2df58-141">Используйте `Integer` вместо неподписанных типов, за исключением тех случаев, когда они необходимы.</span><span class="sxs-lookup"><span data-stu-id="2df58-141">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="2df58-142">Массивы</span><span class="sxs-lookup"><span data-stu-id="2df58-142">Arrays</span></span>  
  
- <span data-ttu-id="2df58-143">Используйте короткий синтаксис при инициализации массивов в строке объявления.</span><span class="sxs-lookup"><span data-stu-id="2df58-143">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="2df58-144">Например, используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="2df58-144">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     <span data-ttu-id="2df58-145">Не используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="2df58-145">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- <span data-ttu-id="2df58-146">Установите обозначение массива на тип, а не на переменную.</span><span class="sxs-lookup"><span data-stu-id="2df58-146">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="2df58-147">Например, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="2df58-147">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     <span data-ttu-id="2df58-148">Не используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="2df58-148">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- <span data-ttu-id="2df58-149">Используйте синтаксис {} при объявлении и инициализации массивов базовых типов данных.</span><span class="sxs-lookup"><span data-stu-id="2df58-149">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="2df58-150">Например, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="2df58-150">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     <span data-ttu-id="2df58-151">Не используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="2df58-151">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="2df58-152">Использование ключевого слова WITH</span><span class="sxs-lookup"><span data-stu-id="2df58-152">Use the With Keyword</span></span>  

 <span data-ttu-id="2df58-153">При выполнении серии вызовов одного объекта рассмотрите возможность использования `With` ключевого слова:</span><span class="sxs-lookup"><span data-stu-id="2df58-153">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="2df58-154">Используйте параметр try... Перехватывать и использовать операторы при использовании обработки исключений</span><span class="sxs-lookup"><span data-stu-id="2df58-154">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  

 <span data-ttu-id="2df58-155">Не используйте `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="2df58-155">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="2df58-156">Использование ключевого слова IsNot</span><span class="sxs-lookup"><span data-stu-id="2df58-156">Use the IsNot Keyword</span></span>  

 <span data-ttu-id="2df58-157">Используйте `IsNot` ключевое слово вместо `Not...Is Nothing` .</span><span class="sxs-lookup"><span data-stu-id="2df58-157">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="2df58-158">Создать ключевое слово</span><span class="sxs-lookup"><span data-stu-id="2df58-158">New Keyword</span></span>  
  
- <span data-ttu-id="2df58-159">Используйте короткий экземпляр.</span><span class="sxs-lookup"><span data-stu-id="2df58-159">Use short instantiation.</span></span> <span data-ttu-id="2df58-160">Например, используйте следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="2df58-160">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     <span data-ttu-id="2df58-161">Предыдущая строка эквивалентна следующей:</span><span class="sxs-lookup"><span data-stu-id="2df58-161">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- <span data-ttu-id="2df58-162">Используйте инициализаторы объектов для новых объектов вместо конструктора без параметров:</span><span class="sxs-lookup"><span data-stu-id="2df58-162">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a><span data-ttu-id="2df58-163">Обработка событий</span><span class="sxs-lookup"><span data-stu-id="2df58-163">Event Handling</span></span>  
  
- <span data-ttu-id="2df58-164">Используйте `Handles` вместо `AddHandler` :</span><span class="sxs-lookup"><span data-stu-id="2df58-164">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- <span data-ttu-id="2df58-165">Используйте `AddressOf` и не создавайте делегата явным образом:</span><span class="sxs-lookup"><span data-stu-id="2df58-165">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- <span data-ttu-id="2df58-166">При определении события используйте короткий синтаксис и позвольте компилятору определить делегат:</span><span class="sxs-lookup"><span data-stu-id="2df58-166">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- <span data-ttu-id="2df58-167">Не следует проверять, имеет ли событие `Nothing` значение (null) перед вызовом `RaiseEvent` метода.</span><span class="sxs-lookup"><span data-stu-id="2df58-167">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="2df58-168">`RaiseEvent` проверяет `Nothing` перед тем, как он вызывает событие.</span><span class="sxs-lookup"><span data-stu-id="2df58-168">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="2df58-169">Использование общих членов</span><span class="sxs-lookup"><span data-stu-id="2df58-169">Using Shared Members</span></span>  

 <span data-ttu-id="2df58-170">Вызывайте `Shared` члены с помощью имени класса, а не из переменной экземпляра.</span><span class="sxs-lookup"><span data-stu-id="2df58-170">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="2df58-171">Использовать литералы XML</span><span class="sxs-lookup"><span data-stu-id="2df58-171">Use XML Literals</span></span>  

 <span data-ttu-id="2df58-172">XML-литералы упрощают наиболее распространенные задачи, возникающие при работе с XML (например, Загрузка, запрос и преобразование).</span><span class="sxs-lookup"><span data-stu-id="2df58-172">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="2df58-173">При разработке с использованием XML-кода следуйте приведенным ниже рекомендациям.</span><span class="sxs-lookup"><span data-stu-id="2df58-173">When you develop with XML, follow these guidelines:</span></span>  
  
- <span data-ttu-id="2df58-174">Используйте литералы XML для создания XML-документов и фрагментов вместо непосредственного вызова API XML.</span><span class="sxs-lookup"><span data-stu-id="2df58-174">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
- <span data-ttu-id="2df58-175">Импортируйте пространства имен XML на уровне файла или проекта, чтобы воспользоваться преимуществами оптимизации производительности для XML-литералов.</span><span class="sxs-lookup"><span data-stu-id="2df58-175">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
- <span data-ttu-id="2df58-176">Используйте свойства осей XML для доступа к элементам и атрибутам в XML-документе.</span><span class="sxs-lookup"><span data-stu-id="2df58-176">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
- <span data-ttu-id="2df58-177">Используйте внедренные выражения для включения значений и создания XML на основе существующих значений вместо использования вызовов API, таких как `Add` метод.</span><span class="sxs-lookup"><span data-stu-id="2df58-177">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a><span data-ttu-id="2df58-178">Запросы LINQ</span><span class="sxs-lookup"><span data-stu-id="2df58-178">LINQ Queries</span></span>  
  
- <span data-ttu-id="2df58-179">Используйте значимые имена для переменных запроса:</span><span class="sxs-lookup"><span data-stu-id="2df58-179">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- <span data-ttu-id="2df58-180">Укажите имена элементов в запросе, чтобы убедиться, что имена свойств анонимных типов правильно заменяются прописными буквами, используя регистр языка Pascal:</span><span class="sxs-lookup"><span data-stu-id="2df58-180">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- <span data-ttu-id="2df58-181">Переименуйте свойства, если имена свойств в результате могут быть неоднозначными.</span><span class="sxs-lookup"><span data-stu-id="2df58-181">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="2df58-182">Например, если запрос возвращает имя клиента и идентификатор заказа, переименуйте их вместо того, чтобы покинуть их как `Name` и `ID` в результате:</span><span class="sxs-lookup"><span data-stu-id="2df58-182">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- <span data-ttu-id="2df58-183">Используйте определение типа в объявлении переменных запроса и переменных диапазона:</span><span class="sxs-lookup"><span data-stu-id="2df58-183">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- <span data-ttu-id="2df58-184">Выровняйте предложения запроса в `From` операторе:</span><span class="sxs-lookup"><span data-stu-id="2df58-184">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- <span data-ttu-id="2df58-185">Используйте `Where` предложения перед другими предложениями запроса, чтобы последующие предложения запроса работали с отфильтрованным набором данных:</span><span class="sxs-lookup"><span data-stu-id="2df58-185">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- <span data-ttu-id="2df58-186">Используйте `Join` предложение для явного определения операции JOIN вместо использования `Where` предложения для неявного определения операции объединения:</span><span class="sxs-lookup"><span data-stu-id="2df58-186">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="2df58-187">См. также</span><span class="sxs-lookup"><span data-stu-id="2df58-187">See also</span></span>

- [<span data-ttu-id="2df58-188">Правила написания безопасного кода</span><span class="sxs-lookup"><span data-stu-id="2df58-188">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
