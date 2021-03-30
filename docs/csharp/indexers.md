---
title: Индексаторы
description: Сведения об индексаторах в C# и о том, как с их помощью реализуются индексируемые свойства, на которые можно ссылаться с использованием одного или нескольких аргументов.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 0e9496da-e766-45a9-b92b-91820d4a350e
ms.openlocfilehash: 2efd8735587c35be8e89dba7499a0a661796067d
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875789"
---
# <a name="indexers"></a><span data-ttu-id="8f6ba-103">Индексаторы</span><span class="sxs-lookup"><span data-stu-id="8f6ba-103">Indexers</span></span>

<span data-ttu-id="8f6ba-104">*Индексаторы* аналогичны свойствам.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-104">*Indexers* are similar to properties.</span></span> <span data-ttu-id="8f6ba-105">Во многих отношениях индексаторы основаны на тех же компонентах языка, что и [свойства](properties.md).</span><span class="sxs-lookup"><span data-stu-id="8f6ba-105">In many ways indexers build on the same language features as [properties](properties.md).</span></span> <span data-ttu-id="8f6ba-106">Индексаторы обеспечивают поддержку *индексированных* свойств: свойств, на которые ссылаются с помощью одного или нескольких аргументов.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-106">Indexers enable *indexed* properties: properties referenced using one or more arguments.</span></span> <span data-ttu-id="8f6ba-107">Эти аргументы предоставляют индекс в определенную коллекцию значений.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-107">Those arguments provide an index into some collection of values.</span></span>

## <a name="indexer-syntax"></a><span data-ttu-id="8f6ba-108">Синтаксис индексаторов</span><span class="sxs-lookup"><span data-stu-id="8f6ba-108">Indexer Syntax</span></span>

<span data-ttu-id="8f6ba-109">Для обращения к индексатору используется имя переменной и квадратные скобки.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-109">You access an indexer through a variable name and square brackets.</span></span> <span data-ttu-id="8f6ba-110">Аргументы индексатора необходимо поместить в квадратные скобки:</span><span class="sxs-lookup"><span data-stu-id="8f6ba-110">You place the indexer arguments inside the brackets:</span></span>

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

<span data-ttu-id="8f6ba-111">Для объявления индексаторов используется ключевое слово `this` в качестве имени свойства, а аргументы объявляются в квадратных скобках.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-111">You declare indexers using the `this` keyword as the property name, and declaring the arguments within square brackets.</span></span> <span data-ttu-id="8f6ba-112">Это объявление соответствует примеру использования, показанному в предыдущем абзаце:</span><span class="sxs-lookup"><span data-stu-id="8f6ba-112">This declaration would match the usage shown in the previous paragraph:</span></span>

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

<span data-ttu-id="8f6ba-113">Наш первый пример помогает понять связь между синтаксисом свойств и индексаторов.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-113">From this initial example, you can see the relationship between the syntax for properties and for indexers.</span></span> <span data-ttu-id="8f6ba-114">Эта аналогия справедлива для большей части синтаксических правил для индексаторов.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-114">This analogy carries through most of the syntax rules for indexers.</span></span> <span data-ttu-id="8f6ba-115">Индексаторы могут иметь любые допустимые модификаторы доступа (общедоступный, защищенный внутренний, защищенный, внутренний, закрытый или закрытый защищенный).</span><span class="sxs-lookup"><span data-stu-id="8f6ba-115">Indexers can have any valid access modifiers (public, protected internal, protected, internal, private or private protected).</span></span> <span data-ttu-id="8f6ba-116">Они могут быть запечатанными, виртуальными или абстрактными.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-116">They may be sealed, virtual, or abstract.</span></span> <span data-ttu-id="8f6ba-117">Как и для свойств, вы можете указать разные модификаторы доступа для методов доступа set и get в индексаторе.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-117">As with properties, you can specify different access modifiers for the get and set accessors in an indexer.</span></span>
<span data-ttu-id="8f6ba-118">Можно также указать индексаторы только для чтения (опуская метод доступа set) или только для записи (опуская метод доступа get).</span><span class="sxs-lookup"><span data-stu-id="8f6ba-118">You may also specify read-only indexers (by omitting the set accessor), or write-only indexers (by omitting the get accessor).</span></span>

<span data-ttu-id="8f6ba-119">К индексаторам можно применять практически все возможности, предусмотренные для свойств.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-119">You can apply almost everything you learn from working with properties to indexers.</span></span> <span data-ttu-id="8f6ba-120">Единственное исключение из этого правила — *автоматически реализуемые свойства*.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-120">The only exception to that rule is *auto implemented properties*.</span></span> <span data-ttu-id="8f6ba-121">Компилятор не всегда может создать правильное хранилище для индексатора.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-121">The compiler cannot always generate the correct storage for an indexer.</span></span>

<span data-ttu-id="8f6ba-122">Наличие аргументов для ссылки на элемент в наборе элементов отличает индексаторы от свойств.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-122">The presence of arguments to reference an item in a set of items distinguishes indexers from properties.</span></span> <span data-ttu-id="8f6ba-123">Можно определить несколько индексаторов для типа, при условии что списки аргументов для каждого индексатора являются уникальными.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-123">You may define multiple indexers on a type, as long as the argument lists for each indexer is unique.</span></span> <span data-ttu-id="8f6ba-124">Рассмотрим различные сценарии, в которых можно использовать один или несколько индексаторов в определении класса.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-124">Let's explore different scenarios where you might use one or more indexers in a class definition.</span></span>

## <a name="scenarios"></a><span data-ttu-id="8f6ba-125">Сценарии</span><span class="sxs-lookup"><span data-stu-id="8f6ba-125">Scenarios</span></span>

<span data-ttu-id="8f6ba-126">Вам потребуется определить *индексаторы* в типе, если его API моделирует некоторую коллекцию, где определяются аргументы для этой коллекции.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-126">You would define *indexers* in your type when its API models some collection where you define the arguments to that collection.</span></span> <span data-ttu-id="8f6ba-127">Индексаторы могут сопоставляться или не сопоставляться напрямую с типами коллекций, которые являются частью основной платформы .NET.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-127">Your indexers may or may not map directly to the collection types that are part of the .NET core framework.</span></span> <span data-ttu-id="8f6ba-128">Тип может иметь другие обязанности, помимо моделирования коллекции.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-128">Your type may have other responsibilities in addition to modeling a collection.</span></span>
<span data-ttu-id="8f6ba-129">Индексаторы позволяют предоставить API, который соответствует абстракции данного типа, не раскрывая внутренних сведений о том, как хранятся или вычисляются значения этой абстракции.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-129">Indexers enable you to provide the API that matches your type's abstraction without exposing the inner details of how the values for that abstraction are stored or computed.</span></span>

<span data-ttu-id="8f6ba-130">Давайте рассмотрим некоторые распространенные сценарии использования *индексаторов*.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-130">Let's walk through some of the common scenarios for using *indexers*.</span></span> <span data-ttu-id="8f6ba-131">Вы можете воспользоваться [папкой с примерами индексаторов](https://github.com/dotnet/samples/tree/main/csharp/indexers).</span><span class="sxs-lookup"><span data-stu-id="8f6ba-131">You can access the [sample folder for indexers](https://github.com/dotnet/samples/tree/main/csharp/indexers).</span></span> <span data-ttu-id="8f6ba-132">Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="8f6ba-132">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

### <a name="arrays-and-vectors"></a><span data-ttu-id="8f6ba-133">Массивы и векторы</span><span class="sxs-lookup"><span data-stu-id="8f6ba-133">Arrays and Vectors</span></span>

<span data-ttu-id="8f6ba-134">Один из наиболее распространенных сценариев для создания индексаторов — когда тип моделирует массив или вектор.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-134">One of the most common scenarios for creating indexers is when your type models an array, or a vector.</span></span> <span data-ttu-id="8f6ba-135">Можно создать индексатор для моделирования упорядоченного набора данных.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-135">You can create an indexer to model an ordered list of data.</span></span>

<span data-ttu-id="8f6ba-136">Преимущество создания собственного индексатора заключается в том, что вы можете определить хранилище для этой коллекции в соответствии с потребностями.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-136">The advantage of creating your own indexer is that you can define the storage for that collection to suit your needs.</span></span> <span data-ttu-id="8f6ba-137">Представьте себе ситуацию, когда ваш тип моделирует исторические данные, которые слишком велики для загрузки в память за один раз.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-137">Imagine a scenario where your type models historical data that is too large to load into memory at once.</span></span> <span data-ttu-id="8f6ba-138">Вам потребуется загружать и выгружать разделы коллекции по мере использования.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-138">You need to load and unload sections of the collection based on usage.</span></span> <span data-ttu-id="8f6ba-139">Следующий пример моделирует такое поведение.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-139">The example following models this behavior.</span></span> <span data-ttu-id="8f6ba-140">Он сообщает о том, сколько точек данных существует.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-140">It reports on how many data points exist.</span></span> <span data-ttu-id="8f6ba-141">Он создает страницы для хранения разделов данных по требованию.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-141">It creates pages to hold sections of the data on demand.</span></span> <span data-ttu-id="8f6ba-142">Он удаляет страницы из памяти, чтобы освободить место для страниц, которые требуются более поздним запросам.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-142">It removes pages from memory to make room for pages needed by more recent requests.</span></span>

```csharp
public class DataSamples
{
    private class Page
    {
        private readonly List<Measurements> pageData = new List<Measurements>();
        private readonly int startingIndex;
        private readonly int length;
        private bool dirty;
        private DateTime lastAccess;

        public Page(int startingIndex, int length)
        {
            this.startingIndex = startingIndex;
            this.length = length;
            lastAccess = DateTime.Now;

            // This stays as random stuff:
            var generator = new Random();
            for(int i=0; i < length; i++)
            {
                var m = new Measurements
                {
                    HiTemp = generator.Next(50, 95),
                    LoTemp = generator.Next(12, 49),
                    AirPressure = 28.0 + generator.NextDouble() * 4
                };
                pageData.Add(m);
            }
        }
        public bool HasItem(int index) =>
            ((index >= startingIndex) &&
            (index < startingIndex + length));

        public Measurements this[int index]
        {
            get
            {
                lastAccess = DateTime.Now;
                return pageData[index - startingIndex];
            }
            set
            {
                pageData[index - startingIndex] = value;
                dirty = true;
                lastAccess = DateTime.Now;
            }
        }

        public bool Dirty => dirty;
        public DateTime LastAccess => lastAccess;
    }

    private readonly int totalSize;
    private readonly List<Page> pagesInMemory = new List<Page>();

    public DataSamples(int totalSize)
    {
        this.totalSize = totalSize;
    }

    public Measurements this[int index]
    {
        get
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");

            var page = updateCachedPagesForAccess(index);
            return page[index];
        }
        set
        {
            if (index < 0)
                throw new IndexOutOfRangeException("Cannot index less than 0");
            if (index >= totalSize)
                throw new IndexOutOfRangeException("Cannot index past the end of storage");
            var page = updateCachedPagesForAccess(index);

            page[index] = value;
        }
    }

    private Page updateCachedPagesForAccess(int index)
    {
        foreach (var p in pagesInMemory)
        {
            if (p.HasItem(index))
            {
                return p;
            }
        }
        var startingIndex = (index / 1000) * 1000;
        var newPage = new Page(startingIndex, 1000);
        addPageToCache(newPage);
        return newPage;
    }

    private void addPageToCache(Page p)
    {
        if (pagesInMemory.Count > 4)
        {
            // remove oldest non-dirty page:
            var oldest = pagesInMemory
                .Where(page => !page.Dirty)
                .OrderBy(page => page.LastAccess)
                .FirstOrDefault();
            // Note that this may keep more than 5 pages in memory
            // if too much is dirty
            if (oldest != null)
                pagesInMemory.Remove(oldest);
        }
        pagesInMemory.Add(p);
    }
}
```

<span data-ttu-id="8f6ba-143">Вы можете следовать этой идиоме проектирования для моделирования любых типов коллекций, если у вас имеются веские причины для того, чтобы не загружать весь набор данных в коллекции в память.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-143">You can follow this design idiom to model any sort of collection where there are good reasons not to load the entire set of data into an in- memory collection.</span></span> <span data-ttu-id="8f6ba-144">Обратите внимание, что класс `Page` является закрытым вложенным классом, который не является частью открытого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-144">Notice that the `Page` class is a private nested class that is not part of the public interface.</span></span> <span data-ttu-id="8f6ba-145">Эти подробности скрыты от пользователей этого класса.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-145">Those details are hidden from any users of this class.</span></span>

### <a name="dictionaries"></a><span data-ttu-id="8f6ba-146">Словари</span><span class="sxs-lookup"><span data-stu-id="8f6ba-146">Dictionaries</span></span>

<span data-ttu-id="8f6ba-147">Другим распространенным сценарием является необходимость моделирования словаря или карты.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-147">Another common scenario is when you need to model a dictionary or a map.</span></span> <span data-ttu-id="8f6ba-148">Этот сценарий подразумевает хранение в типе значений на основе ключа, как правило, текстовых ключей.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-148">This scenario is when your type stores values based on key, typically text keys.</span></span> <span data-ttu-id="8f6ba-149">В этом примере создается словарь, сопоставляющий аргументы командной строки с [лямбда-выражениями](delegates-overview.md), управляющими этими параметрами.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-149">This example creates a dictionary that maps command line arguments to [lambda expressions](delegates-overview.md) that manage those options.</span></span> <span data-ttu-id="8f6ba-150">В следующем примере показано два класса: класс `ArgsActions`, сопоставляющий параметр командной строки делегату `Action`, и `ArgsProcessor`, использующий `ArgsActions` для выполнения каждого объекта `Action` при обнаружении соответствующего параметра.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-150">The following example shows two classes: an `ArgsActions` class that maps a command line option to an `Action` delegate, and an `ArgsProcessor` that uses the `ArgsActions` to execute each `Action` when it encounters that option.</span></span>

```csharp
public class ArgsProcessor
{
    private readonly ArgsActions actions;

    public ArgsProcessor(ArgsActions actions)
    {
        this.actions = actions;
    }

    public void Process(string[] args)
    {
        foreach(var arg in args)
        {
            actions[arg]?.Invoke();
        }
    }

}
public class ArgsActions
{
    readonly private Dictionary<string, Action> argsActions = new Dictionary<string, Action>();

    public Action this[string s]
    {
        get
        {
            Action action;
            Action defaultAction = () => {} ;
            return argsActions.TryGetValue(s, out action) ? action : defaultAction;
        }
    }

    public void SetOption(string s, Action a)
    {
        argsActions[s] = a;
    }
}
```

<span data-ttu-id="8f6ba-151">В этом примере коллекция `ArgsAction` точно соответствует базовой коллекции.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-151">In this example, the `ArgsAction` collection maps closely to the underlying collection.</span></span>
<span data-ttu-id="8f6ba-152">`get` определяет, настроен ли данный параметр.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-152">The `get` determines if a given option has been configured.</span></span> <span data-ttu-id="8f6ba-153">Если это так, он возвращает объект `Action`, связанный с этим параметром.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-153">If so, it returns the `Action` associated with that option.</span></span> <span data-ttu-id="8f6ba-154">В противном случае он возвращает объект `Action`, не выполняющий никаких действий.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-154">If not, it returns an `Action` that does nothing.</span></span> <span data-ttu-id="8f6ba-155">Открытый метод доступа не включает метод доступа `set`.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-155">The public accessor does not include a `set` accessor.</span></span> <span data-ttu-id="8f6ba-156">Вместо этого в проекте используется открытый метод для задания параметров.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-156">Rather, the design using a public method for setting options.</span></span>

### <a name="multi-dimensional-maps"></a><span data-ttu-id="8f6ba-157">Многомерные сопоставления</span><span class="sxs-lookup"><span data-stu-id="8f6ba-157">Multi-Dimensional Maps</span></span>

<span data-ttu-id="8f6ba-158">Можно создавать индексаторы, использующие несколько аргументов.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-158">You can create indexers that use multiple arguments.</span></span> <span data-ttu-id="8f6ba-159">Кроме того, эти аргументы не ограничиваются одним типом.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-159">In addition, those arguments are not constrained to be the same type.</span></span> <span data-ttu-id="8f6ba-160">Рассмотрим два примера.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-160">Let's look at two examples.</span></span>

<span data-ttu-id="8f6ba-161">В первом примере показан класс, который создает значения для множества Мандельброта.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-161">The first example shows a class that generates values for a Mandelbrot set.</span></span> <span data-ttu-id="8f6ba-162">Дополнительные сведения о математических принципах этого множества см. в [этой статье](https://en.wikipedia.org/wiki/Mandelbrot_set).</span><span class="sxs-lookup"><span data-stu-id="8f6ba-162">For more information on the mathematics behind the set, read [this article](https://en.wikipedia.org/wiki/Mandelbrot_set).</span></span>
<span data-ttu-id="8f6ba-163">Индексатор использует два значения double для определения точки на плоскости X и Y.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-163">The indexer uses two doubles to define a point in the X, Y plane.</span></span>
<span data-ttu-id="8f6ba-164">Метод доступа get вычисляет количество итераций до определения точки, не входящей в это множество.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-164">The get accessor computes the number of iterations until a point is determined to be not in the set.</span></span> <span data-ttu-id="8f6ba-165">Если достигается максимальное количество итераций, точка находится в множестве и возвращается значение maxIterations класса.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-165">If the maximum iterations is reached, the point is in the set, and the class's maxIterations value is returned.</span></span> <span data-ttu-id="8f6ba-166">(Компьютер создает изображения на основе заданных цветов множества Мандельброта для числа итераций, необходимых для определения того, что точка находится за пределами множества.)</span><span class="sxs-lookup"><span data-stu-id="8f6ba-166">(The computer generated images popularized for the Mandelbrot set define colors for the number of iterations necessary to determine that a point is outside the set.</span></span>

```csharp
public class Mandelbrot
{
    readonly private int maxIterations;

    public Mandelbrot(int maxIterations)
    {
        this.maxIterations = maxIterations;
    }

    public int this [double x, double y]
    {
        get
        {
            var iterations = 0;
            var x0 = x;
            var y0 = y;

            while ((x*x + y * y < 4) &&
                (iterations < maxIterations))
            {
                var newX = x * x - y * y + x0;
                y = 2 * x * y + y0;
                x = newX;
                iterations++;
            }
            return iterations;
        }
    }
}
```

<span data-ttu-id="8f6ba-167">Множество Мандельброта определяет значения в каждой координате (x, y) для значений реальных чисел.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-167">The Mandelbrot Set defines values at every (x,y) coordinate for real number values.</span></span>
<span data-ttu-id="8f6ba-168">Это определяет словарь, который может содержать бесконечное количество значений.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-168">That defines a dictionary that could contain an infinite number of values.</span></span> <span data-ttu-id="8f6ba-169">Таким образом, множество не основано на хранилище.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-169">Therefore, there is no storage behind the set.</span></span> <span data-ttu-id="8f6ba-170">Напротив, этот класс вычисляет значение для каждой точки, когда код вызывает метод доступа `get`.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-170">Instead, this class computes the value for each point when code calls the `get` accessor.</span></span> <span data-ttu-id="8f6ba-171">Базовое хранилище не используется.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-171">There's no underlying storage used.</span></span>

<span data-ttu-id="8f6ba-172">Теперь рассмотрим один из последних примеров использования индексаторов, где индексатор принимает несколько аргументов разных типов.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-172">Let's examine one last use of indexers, where the indexer takes multiple arguments of different types.</span></span> <span data-ttu-id="8f6ba-173">Рассмотрим программу, которая управляет историческими данными о температуре.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-173">Consider a program that manages historical temperature data.</span></span> <span data-ttu-id="8f6ba-174">Этот индексатор использует город и дату для задания или получения высоких и низких температур для этого расположения:</span><span class="sxs-lookup"><span data-stu-id="8f6ba-174">This indexer uses a city and a date to set or get the high and low temperatures for that location:</span></span>

```csharp
using DateMeasurements =
    System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements =
    System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;

public class HistoricalWeatherData
{
    readonly CityDataMeasurements storage = new CityDataMeasurements();

    public Measurements this[string city, DateTime date]
    {
        get
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
                throw new ArgumentOutOfRangeException(nameof(city), "City not found");

            // strip out any time portion:
            var index = date.Date;
            var measure = default(Measurements);
            if (cityData.TryGetValue(index, out measure))
                return measure;
            throw new ArgumentOutOfRangeException(nameof(date), "Date not found");
        }
        set
        {
            var cityData = default(DateMeasurements);

            if (!storage.TryGetValue(city, out cityData))
            {
                cityData = new DateMeasurements();
                storage.Add(city, cityData);
            }

            // Strip out any time portion:
            var index = date.Date;
            cityData[index] = value;
        }
    }
}
```

<span data-ttu-id="8f6ba-175">В этом примере создается индексатор, который сопоставляет данные о погоде по двум разным аргументам: городу (представленному `string`) и дате (представленной `DateTime`).</span><span class="sxs-lookup"><span data-stu-id="8f6ba-175">This example creates an indexer that maps weather data on two different arguments: a city (represented by a `string`) and a date (represented by a `DateTime`).</span></span> <span data-ttu-id="8f6ba-176">Внутреннее хранилище использует два класса `Dictionary`, представляющие двухмерный словарь.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-176">The internal storage uses two `Dictionary` classes to represent the two-dimensional dictionary.</span></span> <span data-ttu-id="8f6ba-177">Открытый API больше не представляет базовое хранилище.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-177">The public API no longer represents the underlying storage.</span></span> <span data-ttu-id="8f6ba-178">Вместо этого функции языка для индексаторов позволяют создать открытый интерфейс, который представляет абстракцию, несмотря на то, что базовое хранилище должно использовать разные базовые типы коллекции.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-178">Rather, the language features of indexers enables you to create a public interface that represents your abstraction, even though the underlying storage must use different core collection types.</span></span>

<span data-ttu-id="8f6ba-179">Этот код включает две части, которые могут быть незнакомы некоторым разработчикам.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-179">There are two parts of this code that may be unfamiliar to some developers.</span></span> <span data-ttu-id="8f6ba-180">Эти две директивы `using`:</span><span class="sxs-lookup"><span data-stu-id="8f6ba-180">These two `using` directives:</span></span>

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

<span data-ttu-id="8f6ba-181">создают *псевдоним* сконструированного универсального типа.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-181">create an *alias* for a constructed generic type.</span></span> <span data-ttu-id="8f6ba-182">Эти операторы позволяют коду позднее использовать более описательные имена `DateMeasurements` и `CityDateMeasurements` вместо универсальной конструкции `Dictionary<DateTime, Measurements>` и `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-182">Those statements enable the code later to use the more descriptive `DateMeasurements` and `CityDateMeasurements` names instead of the generic construction of `Dictionary<DateTime, Measurements>` and `Dictionary<string, Dictionary<DateTime, Measurements> >`.</span></span>
<span data-ttu-id="8f6ba-183">Эта конструкция требует использования полных имен типов в правой части равенства `=`.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-183">This construct does require using the fully qualified type names on the right side of the `=` sign.</span></span>

<span data-ttu-id="8f6ba-184">Второй прием — отбросить части времени любого объекта `DateTime`, используемого для индексации в коллекции.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-184">The second technique is to strip off the time portions of any `DateTime` object used to index into the collections.</span></span> <span data-ttu-id="8f6ba-185">.NET не включает тип "только дата".</span><span class="sxs-lookup"><span data-stu-id="8f6ba-185">.NET doesn't include a date-only type.</span></span>
<span data-ttu-id="8f6ba-186">Разработчики используют тип `DateTime`, однако использование свойства `Date` для проверки того, что любой объект `DateTime` принадлежит к заданной дате, равноценно.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-186">Developers use the `DateTime` type, but use the `Date` property to ensure that any `DateTime` object from that day are equal.</span></span>

## <a name="summing-up"></a><span data-ttu-id="8f6ba-187">Заключение</span><span class="sxs-lookup"><span data-stu-id="8f6ba-187">Summing Up</span></span>

<span data-ttu-id="8f6ba-188">Индексаторы следует создавать при наличии в вашем классе элемента, подобного свойству, если такое свойство представляет не одно значение, а коллекцию значений, где каждый отдельный элемент определяется набором аргументов.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-188">You should create indexers anytime you have a property-like element in your class where that property represents not a single value, but rather a collection of values where each individual item is identified by a set of arguments.</span></span> <span data-ttu-id="8f6ba-189">Эти аргументы могут однозначно определять, на какой элемент в коллекции необходимо ссылаться.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-189">Those arguments can uniquely identify which item in the collection should be referenced.</span></span>
<span data-ttu-id="8f6ba-190">Индексаторы расширяют концепцию [свойств](properties.md), где член обрабатывается как элемент данных за пределами класса и как метод — в его пределах.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-190">Indexers extend the concept of [properties](properties.md), where a member is treated like a data item from outside the class, but like a method on the inside.</span></span> <span data-ttu-id="8f6ba-191">Индексаторы позволяют аргументам находить в свойстве один элемент, который представляет набор элементов.</span><span class="sxs-lookup"><span data-stu-id="8f6ba-191">Indexers allow arguments to find a single item in a property that represents a set of items.</span></span>
