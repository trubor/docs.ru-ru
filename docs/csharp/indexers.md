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
# <a name="indexers"></a>Индексаторы

*Индексаторы* аналогичны свойствам. Во многих отношениях индексаторы основаны на тех же компонентах языка, что и [свойства](properties.md). Индексаторы обеспечивают поддержку *индексированных* свойств: свойств, на которые ссылаются с помощью одного или нескольких аргументов. Эти аргументы предоставляют индекс в определенную коллекцию значений.

## <a name="indexer-syntax"></a>Синтаксис индексаторов

Для обращения к индексатору используется имя переменной и квадратные скобки. Аргументы индексатора необходимо поместить в квадратные скобки:

```csharp
var item = someObject["key"];
someObject["AnotherKey"] = item;
```

Для объявления индексаторов используется ключевое слово `this` в качестве имени свойства, а аргументы объявляются в квадратных скобках. Это объявление соответствует примеру использования, показанному в предыдущем абзаце:

```csharp
public int this[string key]
{
    get { return storage.Find(key); }
    set { storage.SetAt(key, value); }
}
```

Наш первый пример помогает понять связь между синтаксисом свойств и индексаторов. Эта аналогия справедлива для большей части синтаксических правил для индексаторов. Индексаторы могут иметь любые допустимые модификаторы доступа (общедоступный, защищенный внутренний, защищенный, внутренний, закрытый или закрытый защищенный). Они могут быть запечатанными, виртуальными или абстрактными. Как и для свойств, вы можете указать разные модификаторы доступа для методов доступа set и get в индексаторе.
Можно также указать индексаторы только для чтения (опуская метод доступа set) или только для записи (опуская метод доступа get).

К индексаторам можно применять практически все возможности, предусмотренные для свойств. Единственное исключение из этого правила — *автоматически реализуемые свойства*. Компилятор не всегда может создать правильное хранилище для индексатора.

Наличие аргументов для ссылки на элемент в наборе элементов отличает индексаторы от свойств. Можно определить несколько индексаторов для типа, при условии что списки аргументов для каждого индексатора являются уникальными. Рассмотрим различные сценарии, в которых можно использовать один или несколько индексаторов в определении класса.

## <a name="scenarios"></a>Сценарии

Вам потребуется определить *индексаторы* в типе, если его API моделирует некоторую коллекцию, где определяются аргументы для этой коллекции. Индексаторы могут сопоставляться или не сопоставляться напрямую с типами коллекций, которые являются частью основной платформы .NET. Тип может иметь другие обязанности, помимо моделирования коллекции.
Индексаторы позволяют предоставить API, который соответствует абстракции данного типа, не раскрывая внутренних сведений о том, как хранятся или вычисляются значения этой абстракции.

Давайте рассмотрим некоторые распространенные сценарии использования *индексаторов*. Вы можете воспользоваться [папкой с примерами индексаторов](https://github.com/dotnet/samples/tree/main/csharp/indexers). Инструкции по загрузке см. в разделе [Просмотр и скачивание примеров](../samples-and-tutorials/index.md#view-and-download-samples).

### <a name="arrays-and-vectors"></a>Массивы и векторы

Один из наиболее распространенных сценариев для создания индексаторов — когда тип моделирует массив или вектор. Можно создать индексатор для моделирования упорядоченного набора данных.

Преимущество создания собственного индексатора заключается в том, что вы можете определить хранилище для этой коллекции в соответствии с потребностями. Представьте себе ситуацию, когда ваш тип моделирует исторические данные, которые слишком велики для загрузки в память за один раз. Вам потребуется загружать и выгружать разделы коллекции по мере использования. Следующий пример моделирует такое поведение. Он сообщает о том, сколько точек данных существует. Он создает страницы для хранения разделов данных по требованию. Он удаляет страницы из памяти, чтобы освободить место для страниц, которые требуются более поздним запросам.

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

Вы можете следовать этой идиоме проектирования для моделирования любых типов коллекций, если у вас имеются веские причины для того, чтобы не загружать весь набор данных в коллекции в память. Обратите внимание, что класс `Page` является закрытым вложенным классом, который не является частью открытого интерфейса. Эти подробности скрыты от пользователей этого класса.

### <a name="dictionaries"></a>Словари

Другим распространенным сценарием является необходимость моделирования словаря или карты. Этот сценарий подразумевает хранение в типе значений на основе ключа, как правило, текстовых ключей. В этом примере создается словарь, сопоставляющий аргументы командной строки с [лямбда-выражениями](delegates-overview.md), управляющими этими параметрами. В следующем примере показано два класса: класс `ArgsActions`, сопоставляющий параметр командной строки делегату `Action`, и `ArgsProcessor`, использующий `ArgsActions` для выполнения каждого объекта `Action` при обнаружении соответствующего параметра.

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

В этом примере коллекция `ArgsAction` точно соответствует базовой коллекции.
`get` определяет, настроен ли данный параметр. Если это так, он возвращает объект `Action`, связанный с этим параметром. В противном случае он возвращает объект `Action`, не выполняющий никаких действий. Открытый метод доступа не включает метод доступа `set`. Вместо этого в проекте используется открытый метод для задания параметров.

### <a name="multi-dimensional-maps"></a>Многомерные сопоставления

Можно создавать индексаторы, использующие несколько аргументов. Кроме того, эти аргументы не ограничиваются одним типом. Рассмотрим два примера.

В первом примере показан класс, который создает значения для множества Мандельброта. Дополнительные сведения о математических принципах этого множества см. в [этой статье](https://en.wikipedia.org/wiki/Mandelbrot_set).
Индексатор использует два значения double для определения точки на плоскости X и Y.
Метод доступа get вычисляет количество итераций до определения точки, не входящей в это множество. Если достигается максимальное количество итераций, точка находится в множестве и возвращается значение maxIterations класса. (Компьютер создает изображения на основе заданных цветов множества Мандельброта для числа итераций, необходимых для определения того, что точка находится за пределами множества.)

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

Множество Мандельброта определяет значения в каждой координате (x, y) для значений реальных чисел.
Это определяет словарь, который может содержать бесконечное количество значений. Таким образом, множество не основано на хранилище. Напротив, этот класс вычисляет значение для каждой точки, когда код вызывает метод доступа `get`. Базовое хранилище не используется.

Теперь рассмотрим один из последних примеров использования индексаторов, где индексатор принимает несколько аргументов разных типов. Рассмотрим программу, которая управляет историческими данными о температуре. Этот индексатор использует город и дату для задания или получения высоких и низких температур для этого расположения:

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

В этом примере создается индексатор, который сопоставляет данные о погоде по двум разным аргументам: городу (представленному `string`) и дате (представленной `DateTime`). Внутреннее хранилище использует два класса `Dictionary`, представляющие двухмерный словарь. Открытый API больше не представляет базовое хранилище. Вместо этого функции языка для индексаторов позволяют создать открытый интерфейс, который представляет абстракцию, несмотря на то, что базовое хранилище должно использовать разные базовые типы коллекции.

Этот код включает две части, которые могут быть незнакомы некоторым разработчикам. Эти две директивы `using`:

```csharp
using DateMeasurements = System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>;
using CityDataMeasurements = System.Collections.Generic.Dictionary<string, System.Collections.Generic.Dictionary<System.DateTime, IndexersSamples.Common.Measurements>>;
```

создают *псевдоним* сконструированного универсального типа. Эти операторы позволяют коду позднее использовать более описательные имена `DateMeasurements` и `CityDateMeasurements` вместо универсальной конструкции `Dictionary<DateTime, Measurements>` и `Dictionary<string, Dictionary<DateTime, Measurements> >`.
Эта конструкция требует использования полных имен типов в правой части равенства `=`.

Второй прием — отбросить части времени любого объекта `DateTime`, используемого для индексации в коллекции. .NET не включает тип "только дата".
Разработчики используют тип `DateTime`, однако использование свойства `Date` для проверки того, что любой объект `DateTime` принадлежит к заданной дате, равноценно.

## <a name="summing-up"></a>Заключение

Индексаторы следует создавать при наличии в вашем классе элемента, подобного свойству, если такое свойство представляет не одно значение, а коллекцию значений, где каждый отдельный элемент определяется набором аргументов. Эти аргументы могут однозначно определять, на какой элемент в коллекции необходимо ссылаться.
Индексаторы расширяют концепцию [свойств](properties.md), где член обрабатывается как элемент данных за пределами класса и как метод — в его пределах. Индексаторы позволяют аргументам находить в свойстве один элемент, который представляет набор элементов.
