---
title: Рекомендации по внедрению зависимостей
description: Ознакомьтесь с рекомендациями по внедрению зависимостей и разработке приложений для .NET.
author: IEvangelist
ms.author: dapine
ms.date: 10/29/2020
ms.topic: guide
ms.openlocfilehash: 105536df873829dc79dcca1b86d080360e71303f
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2021
ms.locfileid: "102402147"
---
# <a name="dependency-injection-guidelines"></a>Рекомендации по внедрению зависимостей

В этой статье приведены общие рекомендации по внедрению зависимостей в приложениях .NET.

## <a name="design-services-for-dependency-injection"></a>Проектирование служб для внедрения зависимостей

При разработке служб для внедрения зависимостей придерживайтесь следующих рекомендаций:

- Избегайте статических классов и членов с отслеживанием состояния. Избегайте создания глобального состояния. Для этого проектируйте приложения для использования отдельных служб.
- Избегайте прямого создания экземпляров зависимых классов внутри служб. Прямое создание экземпляров обязывает использовать в коде определенную реализацию.
- Сделайте службы приложения небольшими, хорошо организованными и удобными в тестировании.

Если в классе много внедренных зависимостей, это может указывать на то, что у класса слишком много задач и он нарушает [принцип единственной обязанности](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility). Попробуйте выполнить рефакторинг класса и перенести часть его обязанностей в новые классы.

### <a name="disposal-of-services"></a>Удаление служб

Контейнер отвечает за очистку создаваемых типов и вызывает <xref:System.IDisposable.Dispose%2A> для экземпляров <xref:System.IDisposable>. Службы, разрешенные из контейнера, никогда не должны удаляться разработчиком. Если тип или фабрика зарегистрированы как одноэлементный объект, контейнер автоматически удалит одноэлементные объекты.

В следующем примере службы создаются контейнером службы и автоматически удаляются:

:::code language="csharp" source="snippets/configuration/console-di-disposable/TransientDisposable.cs":::

Предыдущий удаляемый объект должен иметь временное существование.

:::code language="csharp" source="snippets/configuration/console-di-disposable/ScopedDisposable.cs":::

Предыдущий удаляемый объект должен существовать в пределах заданной области.

:::code language="csharp" source="snippets/configuration/console-di-disposable/SingletonDisposable.cs":::

Предыдущий удаляемый объект должен существовать только в одном экземпляре.

:::code language="csharp" source="snippets/configuration/console-di-disposable/Program.cs" range="1-21,41-60" highlight="":::

Консоль отладки после выполнения отображает следующие выходные данные:

```console
Scope 1...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

Scope 2...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

info: Microsoft.Hosting.Lifetime[0]
      Application started.Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
     Hosting environment: Production
info: Microsoft.Hosting.Lifetime[0]
     Content root path: .\configuration\console-di-disposable\bin\Debug\net5.0
info: Microsoft.Hosting.Lifetime[0]
     Application is shutting down...
SingletonDisposable.Dispose()
```

### <a name="services-not-created-by-the-service-container"></a>Службы, не созданные контейнером службы

Рассмотрим следующий код.

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton(new ExampleService());

    // ...
}
```

В приведенном выше коде:

- Экземпляр `ExampleService` **не** создается контейнером службы.
- Платформа **не** удаляет службы автоматически.
- За удаление служб отвечает разработчик.

### <a name="idisposable-guidance-for-transient-and-shared-instances"></a>Руководство по применению временных и общих экземпляров IDisposable

#### <a name="transient-limited-lifetime"></a>Временный экземпляр, ограниченное время существования

**Сценарий**

Приложению требуется экземпляр <xref:System.IDisposable> с ограниченным временем существования для реализации любого из следующих сценариев:

- Экземпляр разрешается в корневой области (в корневом контейнере).
- Экземпляр должен быть удален до завершения области.

**Решение**

Используйте шаблон фабрики для создания экземпляра за пределами родительской области. В этом случае приложение обычно имеет метод `Create`, который непосредственно вызывает конструктор окончательного типа. Если окончательный тип имеет другие зависимости, фабрика позволяет:

- Получить <xref:System.IServiceProvider> в своем конструкторе.
- Используйте <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType>, чтобы создать экземпляр за пределами контейнера, используя контейнер для его зависимостей.

#### <a name="shared-instance-limited-lifetime"></a>Общий экземпляр, ограниченное время существования

**Сценарий**

Приложению требуется общий экземпляр <xref:System.IDisposable> в нескольких службах, но для экземпляра <xref:System.IDisposable> требуется ограниченное время существования.

**Решение**

Зарегистрируйте экземпляр с временем существования с заданной областью. Используйте <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> для создания нового <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>. Используйте <xref:System.IServiceProvider> области для получения необходимых служб. Удалите область, если она больше не нужна.

#### <a name="general-idisposable-guidelines"></a>Общие рекомендации для `IDisposable`

- Не регистрируйте экземпляры <xref:System.IDisposable> с временным временем существования. Вместо этого используйте шаблон фабрики.
- Не разрешайте экземпляры <xref:System.IDisposable> с временным временем существования или временем существования с заданной областью в корневую область. Единственное исключение — это когда приложение создает или повторно создает и удаляет <xref:System.IServiceProvider>, но это не является идеальным вариантом.
- Для получения зависимости <xref:System.IDisposable> через DI не требуется, чтобы получатель реализовывал сам интерфейс <xref:System.IDisposable>. Получатель зависимости <xref:System.IDisposable> не должен вызывать <xref:System.IDisposable.Dispose%2A> для этой зависимости.
- Области должны использоваться для управления временем существования служб. Области не являются иерархическими, и между ними нет специальной связи.

Дополнительные сведения об очистке ресурсов см. в статьях [Реализация метода `Dispose`](../../standard/garbage-collection/implementing-dispose.md)или [Реализация метода `DisposeAsync`](../../standard/garbage-collection/implementing-disposeasync.md). Кроме того, изучите сценарий [Удаляемые временные службы собираются контейнером](#disposable-transient-services-captured-by-container), так как он имеет отношение к очистке ресурсов.

## <a name="default-service-container-replacement"></a>Замена стандартного контейнера служб

Встроенный контейнер служб предназначен для удовлетворения потребностей платформы и большинства клиентских приложений. Мы рекомендуем использовать встроенный контейнер, если только не требуется конкретная функциональная возможность, которую он не поддерживает, например:

- Внедрение свойств
- Внедрение по имени
- Дочерние контейнеры
- Настраиваемое управление временем существования
- `Func<T>` поддерживает отложенную инициализацию
- Регистрация на основе соглашения

С приложениями ASP.NET Core можно использовать следующие сторонние контейнеры:

- [Autofac](https://autofac.readthedocs.io/en/latest/integration/aspnetcore.html);
- [DryIoc](https://www.nuget.org/packages/DryIoc.Microsoft.DependencyInjection);
- [Grace](https://www.nuget.org/packages/Grace.DependencyInjection.Extensions);
- [LightInject](https://github.com/seesharper/LightInject.Microsoft.DependencyInjection);
- [Lamar](https://jasperfx.github.io/lamar/);
- [Stashbox](https://github.com/z4kn4fein/stashbox-extensions-dependencyinjection);
- [Unity](https://www.nuget.org/packages/Unity.Microsoft.DependencyInjection)

## <a name="thread-safety"></a>Потокобезопасность

Создавайте потокобезопасные одноэлементные службы. Если одноэлементная служба имеет зависимость от временной службы, с учетом характера использования одноэлементной службой к этой временной службе также может предъявляться требование потокобезопасности.

Фабричный метод отдельной службы, например второй аргумент в [AddSingleton\<TService>(IServiceCollection, Func\<IServiceProvider,TService>)](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), не обязательно должен быть потокобезопасным. Как и конструктор типов (`static`), он гарантированно будет вызываться только один раз одним потоком.

## <a name="recommendations"></a>Рекомендации

- Разрешение служб на основе `async/await` и `Task` не поддерживается. Так как C# не поддерживает асинхронные конструкторы, следует использовать асинхронные методы после асинхронного разрешения службы.
- Не храните данные и конфигурацию непосредственно в контейнере служб. Например, обычно не следует добавлять корзину пользователя в контейнер служб. Конфигурация должна использовать шаблон параметров. Аналогичным образом, избегайте объектов "хранения данных", которые служат лишь для доступа к другому объекту. Лучше запросить фактический элемент через внедрение зависимостей.
- Избегайте статического доступа к службам. Например, не используйте везде [IApplicationBuilder.ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) в качестве статического поля или свойства.
- Обеспечьте высокую скорость и синхронизацию [фабрик DI](#async-di-factories-can-cause-deadlocks).
- Старайтесь не использовать [*шаблон обнаружения служб*](#scoped-service-as-singleton). Например, не вызывайте <xref:System.IServiceProvider.GetService%2A> для получения экземпляра службы, когда можно использовать внедрение зависимостей.
- Другой вариант указателя службы, позволяющий избежать этого, — внедрение фабрики, которая разрешает зависимости во время выполнения. Оба метода смешивают стратегии [инверсии управления](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion).
- Избегайте вызовов <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> в `ConfigureServices`. Вызов `BuildServiceProvider` обычно происходит, когда разработчику необходимо разрешить службу в `ConfigureServices`.
- [Контейнер собирает удаляемые временные службы](#disposable-transient-services-captured-by-container) для удаления. Это может привести к утечке памяти, если разрешение выполняется в контейнере верхнего уровня.
- Включите проверку области, чтобы убедиться, что в приложении нет отдельных объектов, записывающих службы с заданной областью. Дополнительные сведения см. в разделе [Проверка области](dependency-injection.md#scope-validation).

Как и с любыми рекомендациями, у вас могут возникнуть ситуации, когда нужно отступить от одного из правил. Исключения возникают редко, — как правило, это особые случаи, связанные с самой платформой.

Внедрение зависимостей является *альтернативой* для шаблонов доступа к статическим или глобальным объектам. Вы не сможете воспользоваться преимуществами внедрения зависимостей, если будете сочетать его с доступом к статическим объектам.

## <a name="example-anti-patterns"></a>Примеры антишаблонов

В дополнение к основным рекомендациям этой статьи мы рекомендуем изучить несколько антишаблонов, *которых **следует** избегать*. Некоторые из этих антишаблонов основаны на опыте, полученном при разработке самих сред выполнения.

> [!WARNING]
> Это примеры антишаблонов. *Не* копируйте этот код и ни в коем случае *не* используйте такие действия.

### <a name="disposable-transient-services-captured-by-container"></a>Контейнер собирает удаляемые временные службы

При регистрации *временных* служб, которые реализуют <xref:System.IDisposable>, по умолчанию контейнер внедрения будет удерживать эти ссылки, не избавляясь от них методом <xref:System.IDisposable.Dispose>, пока не будет удален сам контейнер — то есть когда остановится приложение, если ссылки были разрешены из контейнера, или будет удалена область действия, если они были разрешены из этой области. Это может привести к утечке памяти, если разрешение выполняется на уровне контейнера.

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="18-30":::

В предыдущем антишаблоне создаются и размещаются на корневом уровне экземпляры 1000 объектов `ExampleDisposable`. Они не будут удалены, пока существует экземпляр `serviceProvider`.

Дополнительные сведения об отладке утечек памяти см. в статье [Отладка утечки памяти в .NET Core](../diagnostics/debug-memory-leak.md).

### <a name="async-di-factories-can-cause-deadlocks"></a>Фабрики асинхронного внедрения могут вызвать взаимоблокировки

Термин "фабрики асинхронного внедрения" обозначает методы перегрузки, которые существуют при вызове `Add{LIFETIME}`. Некоторые перегрузки принимают `Func<IServiceProvider, T>`, где `T` обозначает регистрируемую службу, а параметр имеет имя `implementationFactory`. `implementationFactory` можно предоставить как лямбда-выражение, локальную функцию или метод. Если фабрика является асинхронной и используется <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType>, происходит взаимоблокировка.

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="32-45" highlight="4-8":::

В приведенном выше коде объект `implementationFactory` получает лямбда-выражение, в котором тело вызывает <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> для метода возврата `Task<Bar>`. Это ***вызывает взаимоблокировку***. Метод `GetBarAsync` эмулирует асинхронную работу с использованием <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType>, а затем вызывает <xref:Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService%60%601(System.IServiceProvider)>.

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="47-53":::

Дополнительные сведения об асинхронной работе см. в статье [Асинхронное программирование: важная информация и советы](../../csharp/async.md#important-info-and-advice). Дополнительные сведения об отладке взаимоблокировок см. в статье [Отладка взаимоблокировки в .NET Core](../diagnostics/debug-deadlock.md).

Когда при использовании этого антишаблона возникает взаимоблокировка, вы можете изучить два ожидающих потока в окне параллельных стеков Visual Studio. Дополнительные сведения см. в статье о [просмотре потоков и задач в окне "Параллельные стеки"](/visualstudio/debugger/using-the-parallel-stacks-window).

### <a name="captive-dependency"></a>Зависимость с захватом

Термин ["зависимость с захватом"](https://blog.ploeh.dk/2014/06/02/captive-dependency) был предложен [Марком Симаном](https://blog.ploeh.dk/about) (Mark Seeman) для обозначения ситуаций с неверной настройкой времени существования службы, когда более длительно выполняемая служба "захватывает" службы с более коротким временем существования.

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="55-65":::

В приведенном выше коде `Foo` регистрируется как служба с одним экземпляром, а для `Bar` ограничена область действия. На первый взгляд, все нормально. Но давайте рассмотрим реализацию `Foo`.

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Foo.cs" highlight="5":::

Объекту `Foo` требуется объект `Bar`, и возникает ошибка конфигурации, так как `Foo` работает с одним экземпляром, а `Bar` имеет ограниченную область действия. В таком варианте экземпляр `Foo` будет создан только один раз, и он будет удерживать `Bar` в течение всего времени существования, что превышает предполагаемое время существования для службы `Bar` с ограниченной областью действия. Мы рекомендуем проверить области, передав `validateScopes: true` в <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Boolean)>. При проверке областей вы получите сообщение <xref:System.InvalidOperationException>, похожее на строку "Не удается использовать службу "Bar" с заданной областью из службы "Foo" с одним экземпляром".

Дополнительные сведения см. в разделе [Проверка области](dependency-injection.md#scope-validation).

### <a name="scoped-service-as-singleton"></a>Выполнение в одном экземпляре службы с заданной областью

При использовании служб с заданной областью, если вы не создаете область или используете ее в существующей области, она становится службой с одним экземпляром.

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="68-82" highlight="13-14":::

В приведенном выше коде `Bar` извлекается в <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>, что является верным. Антишаблоном здесь будет извлечение `Bar` вне пределов области, и имя переменной `avoid` подсказывает нам, какой пример извлечения неправилен.

## <a name="see-also"></a>См. также раздел

- [Внедрение зависимостей в .NET](dependency-injection.md)
- [Руководство. Использование внедрения зависимостей в .NET](dependency-injection-usage.md)
