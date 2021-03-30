---
title: Создание и использование асинхронных потоков
description: В этом расширенном руководстве показано, как создавать и использовать асинхронные потоки. Асинхронные потоки предоставляют более естественный способ работы с последовательностями данных, которые могут создаваться асинхронно.
ms.date: 02/10/2019
ms.technology: csharp-async
ms.custom: mvc
ms.openlocfilehash: 9218e11a066d1d6107e501d4c20079a642f927a3
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104878933"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Учебник. Создание и использование асинхронных потоков с использованием C# 8.0 и .NET Core 3.0

В C# 8.0 представлены **асинхронные потоки**, которые моделируют источник данных потоковой передачи. Потоки данных часто извлекают или создают элементы асинхронно. Асинхронные потоки полагаются на новые интерфейсы, появившиеся в .NET Standard 2.1. Эти интерфейсы поддерживаются в .NET Core 3.0 и более поздних версиях. Они предоставляют естественную модель программирования для асинхронных потоковых источников данных.

В этом руководстве вы узнаете, как:

> [!div class="checklist"]
>
> - Создать источник данных, который формирует последовательность элементов данных асинхронно.
> - Использовать этот источник данных асинхронно.
> - Поддержка отмены и перехваченных контекстов для асинхронных потоков.
> - Распознавать, когда новый интерфейс и источник данных предпочтительнее для более ранних синхронных последовательностей данных.

## <a name="prerequisites"></a>Предварительные требования

Вам нужно настроить свой компьютер для выполнения .NET Core, включая компилятор C# 8.0. Компилятор C# 8 доступен, начиная с [версии 16.3 Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) или [в пакете SDK .NET Core 3.0](https://dotnet.microsoft.com/download).

Чтобы вы могли получить доступ к конечной точке GraphQL GitHub, необходимо создать [маркер доступа GitHub](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token). Выберите следующие разрешения для маркеров доступа GitHub.

- repo:status
- public_repo

Храните маркер доступа в надежном месте, чтобы вы могли использовать его для получения доступа к конечной точке API GitHub.

> [!WARNING]
> Храните свой личный маркер доступа в безопасном месте. Любое программное обеспечение с вашим личным маркером доступа может выполнять вызовы API GitHub с помощью ваших прав доступа.

В этом руководстве предполагается, что вы знакомы с C# и .NET, включая Visual Studio или .NET Core CLI.

## <a name="run-the-starter-application"></a>Запуск начального приложения

Вы можете получить код для начального приложения, используемый в этом руководстве в репозитории [dotnet/docs](https://github.com/dotnet/docs) в папке [csharp/tutorials/AsyncStreams](https://github.com/dotnet/docs/tree/main/docs/csharp/tutorials/snippets/generate-consume-asynchronous-streams/start).

Начальное приложение представляет собой консольное приложение, которое использует интерфейс [GraphQL GitHub](https://developer.github.com/v4/) для получения последних проблем, написанных в репозитории [dotnet/docs](https://github.com/dotnet/docs). Начнем с просмотра следующего кода для метода `Main` начального приложения.

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetStarterAppMain" :::

Вы можете задать переменную среды `GitHubKey` личному маркеру доступа или заменить последний аргумент в вызове на `GetEnvVariable` с помощью личного маркера доступа. Не размещайте код доступа в исходном коде, если будете предоставлять общий доступ к источнику другим пользователям. Никогда не отправляйте коды доступа в репозиторий с общим исходным кодом.

После создания клиента GitHub код в `Main` создает объект отчета о ходе выполнения и маркер отмены. После создания этих объектов `Main` вызывает `runPagedQueryAsync`, чтобы получить более 250 недавно созданных проблем. Результаты отобразятся после выполнения этой задачи.

При запуске начального приложения вы можете обнаружить некоторые важные замечания о том, как будет выполняться приложение.  Вы увидите ход выполнения, передаваемый каждой странице, возвращенной с GitHub. Прежде чем GitHub вернет каждую новую страницу проблем, возникает заметная пауза. Наконец, проблемы отображаются только после того, как получены все 10 страниц с GitHub.

## <a name="examine-the-implementation"></a>Изучение реализации

Реализация показывает, почему возникло поведение, обсуждавшееся в предыдущем разделе. Изучите код для `runPagedQueryAsync`.

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetRunPagedQuery" :::

Давайте сконцентрируемся на алгоритме разбивки по страницам и асинхронной структуре предыдущего кода. (Дополнительные сведения об API GraphQL GitHub см. в [этой документации](https://developer.github.com/v4/guides/).) Метод `runPagedQueryAsync` перечисляет проблемы от самых последних до самых старых. Чтобы продолжить с предыдущей страницы, он запрашивает по 25 выпусков на страницу и проверяет структуру ответа `pageInfo`. Это следует за стандартной поддержкой страниц GraphQL для многостраничных ответов. Ответ включает в себя объект `pageInfo`, который содержит значение `hasPreviousPages` и `startCursor`, используемые для запроса предыдущей страницы. Проблемы в массиве `nodes`. Метод `runPagedQueryAsync` добавляет эти узлы в массив, который содержит результаты со всех страниц.

После получения и восстановления страницы результатов `runPagedQueryAsync` сообщает о ходе выполнения и проверяет наличие отмены. Если есть запрос на отмену, `runPagedQueryAsync` выдает <xref:System.OperationCanceledException>.

Существует несколько элементов в этом коде, которые можно улучшить. Самое главное, `runPagedQueryAsync` должен выделить хранилище для всех возвращенных проблем. Этот пример останавливается после нахождения 250 проблем, так как для извлечения всех открытых проблем потребуется гораздо больше памяти на их хранение. Протоколы для поддержки отчетов о ходе выполнения и отмены делают алгоритм более сложным для понимания при первом чтении. Задействовано больше типов и API. Вы должны отслеживать передачу данных с помощью <xref:System.Threading.CancellationTokenSource> и связанного с ним <xref:System.Threading.CancellationToken>, чтобы понять, где запрашивается отмена и где она предоставляется.

## <a name="async-streams-provide-a-better-way"></a>Предоставление лучшего способа асинхронных потоков

Асинхронные потоки и связанная языковая поддержка обращаются ко всем этим вопросам. Код, который формирует последовательность, теперь может использовать `yield return` для возврата элементов в методе, который был объявлен с помощью модификатора `async`. Вы можете применить асинхронный поток, используя цикл `await foreach`, аналогично любой последовательности с помощью цикла `foreach`.

Эти новые языковые функции зависят от трех новых интерфейсов, добавленных в .NET Standard 2.1 и реализованных в .NET Core 3.0.

- <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>
- <xref:System.IAsyncDisposable?displayProperty=nameWithType>

Большинство разработчиков C# должны знать об этих трех интерфейсах. Они ведут себя подобно своим синхронным аналогам.

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Один тип, который может быть незнаком, — <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>. Структура `ValueTask` предоставляет API, аналогичный классу <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>. `ValueTask` используется в этих интерфейсах по причинам производительности.

## <a name="convert-to-async-streams"></a>Преобразование в асинхронные потоки

Затем для создания асинхронного потока преобразуйте метод `runPagedQueryAsync`. Сначала измените подпись `runPagedQueryAsync`, чтобы вернуть `IAsyncEnumerable<JToken>`, затем удалите маркер отмены и объекты хода выполнения из списка параметров, как показано в следующем коде.

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetUpdateSignature" :::

В следующем коде показано, как начальный код обрабатывает каждую страницу для извлечения.

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetProcessPage" :::

Замените эти три строки следующим кодом.

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetYieldReturnPage" :::

Вы также можете удалить объявление `finalResults` ранее в этом методе и оператор `return`, следующий за измененным циклом.

Вы завершили изменения для создания асинхронного потока. Готовый метод должен иметь вид, аналогичный приведенному ниже коду:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateAsyncStream" :::

Затем измените код, который использует коллекцию, для асинхронного потока. Найдите следующий код в `Main`, который обрабатывает коллекцию проблем.

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetEnumerateOldStyle" :::

Замените код следующим циклом `await foreach`.

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateAsyncStream" :::

Новый интерфейс <xref:System.Collections.Generic.IAsyncEnumerator%601> является производным от <xref:System.IAsyncDisposable>. Это означает, что предыдущий цикл будет асинхронно удалять поток по завершении цикла. Цикл похож на следующий код:

```csharp
int num = 0;
var enumerator = runPagedQueryAsync(client, PagedIssueQuery, "docs").GetEnumeratorAsync();
try
{
    while (await enumerator.MoveNextAsync())
    {
        var issue = enumerator.Current;
        Console.WriteLine(issue);
        Console.WriteLine($"Received {++num} issues in total");
    }
} finally
{
    if (enumerator != null)
        await enumerator.DisposeAsync();
}
```

Элементы потока по умолчанию обрабатываются в захваченном контексте. Чтобы отключить захват контекста, используйте метод расширения <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType>. Дополнительные сведения о контекстах синхронизации и захвате текущего контекста см. в [статье](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md), посвященной использованию асинхронной модели на основе задач.

Асинхронные потоки поддерживают отмену, используя тот же протокол, что и другие методы `async`. Для поддержки отмены можно изменить сигнатуру для метода асинхронного итератора следующим образом:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateWithCancellation" :::

Атрибут <xref:System.Runtime.CompilerServices.EnumeratorCancellationAttribute?dipslayProperty=nameWithType> заставляет компилятор создать код для <xref:System.Collections.Generic.IAsyncEnumerator%601>, который делает токен, передаваемый `GetAsyncEnumerator`, видимым в тексте асинхронного итератора в виде аргумента. Внутри `runQueryAsync` можно проверить состояние маркера и отменить дальнейшую работу при необходимости.

Используйте другой метод расширения, <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.WithCancellation%2A>, чтобы передать токен отмены асинхронному потоку. Измените цикл, перечисляя проблемы следующим образом:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateWithCancellation" :::

Вы можете получить код для готового руководства из репозитория [dotnet/docs](https://github.com/dotnet/docs) в папке [csharp/tutorials/AsyncStreams](https://github.com/dotnet/docs/tree/main/docs/csharp/tutorials/snippets/generate-consume-asynchronous-streams/finished).

## <a name="run-the-finished-application"></a>Запуск готового приложения

Снова запустите приложение. Сравните его поведение с поведением начального приложения. Первая страница результатов перечисляется, как только она становится доступной. Поскольку каждую новую страницу запрашивают и извлекают, результаты следующей страницы быстро перечисляются, возникает пауза. Блок `try` / `catch` не требует обработки отмены. Вызывающий может прекратить перечисление коллекции. Отчет о ходе выполнения четко сформирован, так как асинхронный поток формирует результаты скачивания каждой страницы. Состояние каждой возвращенной проблемы включается в цикл `await foreach`. Для отслеживания хода выполнения объект обратного вызова не требуется.

Изучив код, вы увидите улучшения в использовании памяти. Вам больше не нужно выделять коллекцию для хранения всех результатов до их перечисления. Вызывающий может определить, как использовать результаты и нужен ли набор хранилищ.

Запустите начальное и готовое приложение, и вы увидите различия между реализациями самостоятельно. Вы можете удалить маркер доступа GitHub, созданный при начале работы с этим руководством, после завершения изучения. Если злоумышленник получил доступ к этому маркеру, ему удастся получить доступ к API GitHub с помощью ваших учетных данных.
