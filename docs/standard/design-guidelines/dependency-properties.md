---
description: 'Узнайте подробнее о: Свойства зависимостей'
title: Свойства зависимостей
ms.date: 10/22/2008
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: 78b141d6e8d1bb6bd5cf050a89aa67705111bae3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642309"
---
# <a name="dependency-properties"></a><span data-ttu-id="db7d7-103">Свойства зависимостей</span><span class="sxs-lookup"><span data-stu-id="db7d7-103">Dependency Properties</span></span>

<span data-ttu-id="db7d7-104">Свойство зависимостей — это обычное свойство, которое сохраняет свое значение в хранилище свойств, а не, например, в переменной типа (поле).</span><span class="sxs-lookup"><span data-stu-id="db7d7-104">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>

 <span data-ttu-id="db7d7-105">Присоединенное свойство зависимостей — это разновидность свойства зависимостей, смоделированная как статические методы Get и Set, представляющие свойства, которые описывают связь между объектами и их контейнерами (например, позицию объекта `Button` в контейнере `Panel`).</span><span class="sxs-lookup"><span data-stu-id="db7d7-105">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>

 <span data-ttu-id="db7d7-106">✔ СЛЕДУЕТ️ предоставить свойства зависимостей для поддержки таких функций WPF, как применение стилей, триггеры, привязка данных, анимации, динамические ресурсы и наследование.</span><span class="sxs-lookup"><span data-stu-id="db7d7-106">✔️ DO provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>

## <a name="dependency-property-design"></a><span data-ttu-id="db7d7-107">Разработка свойства зависимостей</span><span class="sxs-lookup"><span data-stu-id="db7d7-107">Dependency Property Design</span></span>

 <span data-ttu-id="db7d7-108">✔️ При реализации свойств зависимостей они ДОЛЖНЫ быть производными от <xref:System.Windows.DependencyObject> или одного из его подтипов.</span><span class="sxs-lookup"><span data-stu-id="db7d7-108">✔️ DO inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="db7d7-109">Тип обеспечивает очень эффективную реализацию хранилища свойств и автоматически поддерживает привязку данных WPF.</span><span class="sxs-lookup"><span data-stu-id="db7d7-109">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>

 <span data-ttu-id="db7d7-110">✔️ СЛЕДУЕТ️️ предоставить обычное свойство среды CLR и открытое статическое доступное только для чтения поле, в котором хранится экземпляр <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> для каждого свойства зависимостей.</span><span class="sxs-lookup"><span data-stu-id="db7d7-110">✔️ DO provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>

 <span data-ttu-id="db7d7-111">✔ СЛЕДУЕТ️ реализовать свойства зависимостей, вызывая методы экземпляра <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> и <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db7d7-111">✔️ DO implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="db7d7-112">✔ СЛЕДУЕТ️ назвать статическое поле свойства зависимостей, добавив суффикс Property к имени свойства.</span><span class="sxs-lookup"><span data-stu-id="db7d7-112">✔️ DO name the dependency property static field by suffixing the name of the property with "Property."</span></span>

 <span data-ttu-id="db7d7-113">❌ НЕ задавайте явным образом значения по умолчанию для свойств зависимостей в коде. Вместо этого задайте их в метаданных.</span><span class="sxs-lookup"><span data-stu-id="db7d7-113">❌ DO NOT set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>

 <span data-ttu-id="db7d7-114">Если вы явно задаете свойства по умолчанию, можно предотвратить задание этого свойства неявными средствами, такими как средство применения стилей.</span><span class="sxs-lookup"><span data-stu-id="db7d7-114">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>

 <span data-ttu-id="db7d7-115">❌ НЕ помещайте в методы доступа к свойствам код, отличный от стандартного кода для доступа к статическому полю.</span><span class="sxs-lookup"><span data-stu-id="db7d7-115">❌ DO NOT put code in the property accessors other than the standard code to access the static field.</span></span>

 <span data-ttu-id="db7d7-116">Этот код не будет выполняться, если свойство задано неявными средствами, например средством применения стилей, так как оно использует статическое поле напрямую.</span><span class="sxs-lookup"><span data-stu-id="db7d7-116">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>

 <span data-ttu-id="db7d7-117">❌ НЕ используйте свойства зависимостей для хранения защищенных данных.</span><span class="sxs-lookup"><span data-stu-id="db7d7-117">❌ DO NOT use dependency properties to store secure data.</span></span> <span data-ttu-id="db7d7-118">Вы даже можете получить открытый доступ к частным свойствам зависимостей.</span><span class="sxs-lookup"><span data-stu-id="db7d7-118">Even private dependency properties can be accessed publicly.</span></span>

## <a name="attached-dependency-property-design"></a><span data-ttu-id="db7d7-119">Разработка присоединенного свойства зависимостей</span><span class="sxs-lookup"><span data-stu-id="db7d7-119">Attached Dependency Property Design</span></span>

 <span data-ttu-id="db7d7-120">Свойства зависимостей, описанные в предыдущем разделе, представляют встроенные свойства объявляющего типа. Например, свойство `Text` является свойством `TextButton`, которое объявляет его.</span><span class="sxs-lookup"><span data-stu-id="db7d7-120">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="db7d7-121">Присоединенное свойство зависимостей — это особый вид свойства.</span><span class="sxs-lookup"><span data-stu-id="db7d7-121">A special kind of dependency property is the attached dependency property.</span></span>

 <span data-ttu-id="db7d7-122">Классическим примером присоединенного свойства является свойство <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db7d7-122">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="db7d7-123">Свойство представляет положение столбца кнопок (не сетки). Однако оно используется только в том случае, если сетка содержит кнопку. Поэтому оно присоединено к кнопкам с помощью сеток.</span><span class="sxs-lookup"><span data-stu-id="db7d7-123">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>

    <Button Grid.Column="0">Click</Button>
    <Button Grid.Column="1">Clack</Button>
</Grid>
```

 <span data-ttu-id="db7d7-124">Присоединенное свойство, как правило, идентично обычному свойству зависимости, за исключением того, что методы доступа представлены статическими методами Get и Set:</span><span class="sxs-lookup"><span data-stu-id="db7d7-124">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>

```csharp
public class Grid {

    public static int GetColumn(DependencyObject obj) {
        return (int)obj.GetValue(ColumnProperty);
    }

    public static void SetColumn(DependencyObject obj, int value) {
        obj.SetValue(ColumnProperty,value);
    }

    public static readonly DependencyProperty ColumnProperty =
        DependencyProperty.RegisterAttached(
            "Column",
            typeof(int),
            typeof(Grid)
    );
}
```

## <a name="dependency-property-validation"></a><span data-ttu-id="db7d7-125">Проверка свойства зависимостей</span><span class="sxs-lookup"><span data-stu-id="db7d7-125">Dependency Property Validation</span></span>

 <span data-ttu-id="db7d7-126">Свойства часто реализуют проверку.</span><span class="sxs-lookup"><span data-stu-id="db7d7-126">Properties often implement what is called validation.</span></span> <span data-ttu-id="db7d7-127">Логика проверки выполняется при попытке изменить значение свойства.</span><span class="sxs-lookup"><span data-stu-id="db7d7-127">Validation logic executes when an attempt is made to change the value of a property.</span></span>

 <span data-ttu-id="db7d7-128">К сожалению, методы доступа к свойствам зависимостей не могут содержать произвольный код проверки.</span><span class="sxs-lookup"><span data-stu-id="db7d7-128">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="db7d7-129">Вместо этого во время регистрации свойства необходимо указать логику проверки свойств зависимостей.</span><span class="sxs-lookup"><span data-stu-id="db7d7-129">Instead, dependency property validation logic needs to be specified during property registration.</span></span>

 <span data-ttu-id="db7d7-130">❌ НЕ помещайте логику проверки свойств зависимостей в методы доступа свойства.</span><span class="sxs-lookup"><span data-stu-id="db7d7-130">❌ DO NOT put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="db7d7-131">Вместо этого передайте обратный вызов проверки в метод `DependencyProperty.Register`.</span><span class="sxs-lookup"><span data-stu-id="db7d7-131">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>

## <a name="dependency-property-change-notifications"></a><span data-ttu-id="db7d7-132">Уведомления об изменении свойства зависимостей</span><span class="sxs-lookup"><span data-stu-id="db7d7-132">Dependency Property Change Notifications</span></span>

 <span data-ttu-id="db7d7-133">❌ НЕ реализуйте логику уведомления об изменении в методах доступа к свойствам зависимостей.</span><span class="sxs-lookup"><span data-stu-id="db7d7-133">❌ DO NOT implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="db7d7-134">Свойства зависимостей имеют встроенную функцию уведомлений об изменениях. Чтобы ее использовать, необходимо передать обратный вызов уведомления об изменении в <xref:System.Windows.PropertyMetadata>.</span><span class="sxs-lookup"><span data-stu-id="db7d7-134">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>

## <a name="dependency-property-value-coercion"></a><span data-ttu-id="db7d7-135">Приведение значения свойства зависимостей</span><span class="sxs-lookup"><span data-stu-id="db7d7-135">Dependency Property Value Coercion</span></span>

 <span data-ttu-id="db7d7-136">Если значение, переданное методу задания свойства, изменяется методом задания до фактического изменения хранилища свойств, выполняется приведение свойства.</span><span class="sxs-lookup"><span data-stu-id="db7d7-136">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>

 <span data-ttu-id="db7d7-137">❌ НЕ реализуйте логику приведения в методах доступа к свойствам зависимостей.</span><span class="sxs-lookup"><span data-stu-id="db7d7-137">❌ DO NOT implement coercion logic in dependency property accessors.</span></span>

 <span data-ttu-id="db7d7-138">Свойства зависимостей имеют встроенную функцию приведения, которую можно использовать путем предоставления `PropertyMetadata` обратного вызова приведения.</span><span class="sxs-lookup"><span data-stu-id="db7d7-138">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>

 <span data-ttu-id="db7d7-139">*Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*</span><span class="sxs-lookup"><span data-stu-id="db7d7-139">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="db7d7-140">*Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="db7d7-140">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="db7d7-141">См. также</span><span class="sxs-lookup"><span data-stu-id="db7d7-141">See also</span></span>

- [<span data-ttu-id="db7d7-142">Рекомендации по проектированию на основе Framework</span><span class="sxs-lookup"><span data-stu-id="db7d7-142">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="db7d7-143">Обычные шаблоны разработки</span><span class="sxs-lookup"><span data-stu-id="db7d7-143">Common Design Patterns</span></span>](common-design-patterns.md)
