---
title: Ведение журнала с высокой производительностью в .NET
author: IEvangelist
description: Сведения о том, как использовать LoggerMessage для создания кэшируемых делегатов, которым нужно меньше выделений объектов в сценариях высокопроизводительного ведения журналов.
ms.author: dapine
ms.date: 01/04/2021
ms.openlocfilehash: 0031ff7a9f70cb0cf724fdf6dfa4fbe0a44af7c1
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2021
ms.locfileid: "102402135"
---
# <a name="high-performance-logging-in-net"></a>Ведение журнала с высокой производительностью в .NET

Класс <xref:Microsoft.Extensions.Logging.LoggerMessage> предоставляет функциональные возможности для создания кэшируемых делегатов, которым нужно меньше выделений объектов и вычислительных ресурсов, чем [методам расширения для средства ведения журнала](xref:Microsoft.Extensions.Logging.LoggerExtensions), таким как <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> и <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A>. Для сценариев высокопроизводительного ведения журналов используйте шаблон <xref:Microsoft.Extensions.Logging.LoggerMessage>.

<xref:Microsoft.Extensions.Logging.LoggerMessage> предоставляет следующие преимущества производительности по сравнению с методами расширения для средства ведения журнала:

- Методы расширения для средства ведения журнала требуют "упаковку-преобразование" типов значений, таких как `int`, в `object`. Шаблон <xref:Microsoft.Extensions.Logging.LoggerMessage> позволяет избежать упаковки-преобразования за счет статических полей <xref:System.Action> и методов расширения со строго типизированными параметрами.
- Методы расширения для средства ведения журнала должны анализировать шаблон сообщения (именованную строку формата) при каждой записи сообщения журнала. <xref:Microsoft.Extensions.Logging.LoggerMessage> требует анализировать шаблон всего один раз — при определении сообщения.

В этом примере приложения демонстрируются возможности <xref:Microsoft.Extensions.Logging.LoggerMessage> с рабочей службой для обработки приоритетной очереди. Это приложение обрабатывает рабочие элементы в порядке приоритета. По мере выполнения этих операций создаются сообщения журнала с помощью шаблона <xref:Microsoft.Extensions.Logging.LoggerMessage>.

## <a name="define-a-logger-message"></a>Определение сообщения средства ведения журнала

Примените [Define(LogLevel, EventId, String)](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A), чтобы создать делегат <xref:System.Action> для сохранения сообщения в журнал. Перегрузки <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> позволяют передать до шести параметров типа в именованную строку формата (шаблон).

Строка, предоставляемая методу <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A>, является шаблоном, а не интерполированной строкой. Заполнители заполняются в том порядке, в котором указаны типы. Имена заполнителей в шаблоне должны быть описательными и согласованными между разными шаблонами. Они выступают в качестве имен свойств в структурированных данных журнала. Мы рекомендуем использовать [стиль Pascal ](../../standard/design-guidelines/capitalization-conventions.md) для имен заполнителей. Например, `{Item}`, `{DateTime}`.

Каждое сообщение журнала является <xref:System.Action>, хранящимся в статическом поле, созданном [LoggerMessage.Define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A). Следующий пример приложения создает поле для описания сообщения журнала при обработке рабочих элементов.

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingField":::

Для <xref:System.Action> укажите:

- уровень ведения журнала;
- уникальный идентификатор события (<xref:Microsoft.Extensions.Logging.EventId>) с именем статического метода расширения;
- шаблон сообщения (именованная строка формата).

При выведении рабочих элементов из очереди для обработки приложение рабочей службы устанавливает следующие параметры:

- уровень ведения журнала — <xref:Microsoft.Extensions.Logging.LogLevel.Critical?displayProperty=nameWithType>;
- идентификатор события — `13` с именем метода `FailedToProcessWorkItem`;
- шаблон сообщения (именованная строка формата) — строка.

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingAssignment":::

Структурированные хранилища для ведения журнала могут использовать имя события, когда оно предоставляется вместе с идентификатором события, для улучшения ведения журнала. Например, [Serilog](https://github.com/serilog/serilog-extensions-logging) использует имя события.

<xref:System.Action> вызывается с помощью строго типизированного метода расширения. Метод `PriorityItemProcessed` записывает сообщение каждый раз, когда обрабатывается рабочий элемент. Метод `FailedToProcessWorkItem`, в свою очередь, вызывается только при возникновении исключения.

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="15-18":::

Изучите выходные данные консоли приложения:

```console
crit: WorkerServiceOptions.Example.Worker[13]
      Epic failure processing item!
      System.Exception: Failed to verify communications.
         at WorkerServiceOptions.Example.Worker.ExecuteAsync(CancellationToken stoppingToken) in
         ..\Worker.cs:line 27
```

Чтобы передать параметры в сообщение журнала, определите до шести типов при создании статического поля. Пример приложения регистрирует сведения о рабочем элементе при обработке элементов, определяя тип `WorkItem` для поля <xref:System.Action>.

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemField":::

Шаблон сообщения журнала делегата получает его значения заполнителей из предоставленных типов. Этот пример приложения определяет делегат для добавления рабочего элемента, где используется параметр элемента `WorkItem`.

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemAssignment":::

Статический метод расширения `PriorityItemProcessed`, который используется для сохранения в журнал сообщения об обработке рабочего элемента, получает рабочий элемент в качестве значения аргумента и передает его делегату <xref:System.Action>.

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemMethod":::

В методе `ExecuteAsync` рабочей службы вызывается `PriorityItemProcessed` для записи сообщения в журнал.

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="12":::

Изучите выходные данные консоли приложения:

```console
info: WorkerServiceOptions.Example.Worker[1]
      Processing priority item: Priority-Extreme (50db062a-9732-4418-936d-110549ad79e4): 'Verify communications'
```

## <a name="define-logger-message-scope"></a>Определение области сообщения средства ведения журнала

Метод [DefineScope(String)](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A) создает делегат <xref:System.Func%601> для определения [области журнала](logging.md#log-scopes). Перегрузки <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> позволяют передать до трех параметров типа в именованную строку формата (шаблон).

Как и в случае с методом <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A>, строка, предоставляемая методу <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A>, является шаблоном, а не интерполированной строкой. Заполнители заполняются в том порядке, в котором указаны типы. Имена заполнителей в шаблоне должны быть описательными и согласованными между разными шаблонами. Они выступают в качестве имен свойств в структурированных данных журнала. Мы рекомендуем использовать [стиль Pascal ](../../standard/design-guidelines/capitalization-conventions.md) для имен заполнителей. Например, `{Item}`, `{DateTime}`.

Определите [область журнала](logging.md#log-scopes), чтобы применить последовательность сообщений журнала с помощью метода <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A>. Включите `IncludeScopes` в раздел средства ведения журнала консоли в файле *appsettings.json*:

:::code language="json" source="snippets/configuration/worker-service-options/appsettings.json" highlight="3-5":::

Для создания области журнала добавьте поле, содержащее делегат <xref:System.Func%601> для области. Пример приложения создает поле `_processingWorkScope` (*Internal/LoggerExtensions.cs*):

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkField":::

Используйте <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> для создания делегата. Можно указать до трех типов для использования в качестве аргументов шаблона при вызове делегата. Этот пример приложения использует шаблон сообщения, который содержит дату и время начала обработки.

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkAssignment":::

Предоставьте статический метод расширения для сообщения журнала. Включите любые параметры типа для именованных свойств, отображаемых в шаблоне сообщений. Этот пример приложения принимает `DateTime` в качестве настраиваемой метки времени для сохранения в журнал и возвращает `_processingWorkScope`.

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkMethod":::

Область создает оболочку для вызовов расширения ведения журнала в блоке [using](../../csharp/language-reference/keywords/using-statement.md).

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="4":::

Изучите сообщения журнала в выходных данных консоли приложения: Следующий результат демонстрирует упорядочение сообщений журнала по приоритету, с указанием сообщения об области журнала.

```console
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Extreme (f5090ede-a337-4041-b914-f6bc0db5ae64): 'Verify communications'
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: ..\worker-service-options
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-High (496d440f-2007-4391-b179-09d75ab52373): 'Validate collection'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (dea9e3f4-d7df-46d2-b7cd-5e0232eb98a5): 'Propagate selections'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (089d7f0d-da72-4b55-92fe-57b147838056): 'Enter pooling [contention]'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Low (6e68c4be-089f-4450-9080-1ea63fcbb686): 'Health check network'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (6f324134-6bb6-455f-81d4-553ab307c421): 'Ping weather service'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (37bf736c-7a26-4a2a-9e56-e89bcf3b8f35): 'Set process state'
```

## <a name="see-also"></a>См. также раздел

- [Ведение журнала в .NET](logging.md)
