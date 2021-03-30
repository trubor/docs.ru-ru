---
title: Стандартные счетчики событий в .NET
description: Сведения о счетчиках событий, публикуемых в библиотеках и среде выполнения .NET.
ms.topic: reference
ms.date: 12/17/2020
ms.openlocfilehash: aad4fa8b33ebf0dcb7803c77b11fb99a6b6d7b83
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872838"
---
# <a name="well-known-eventcounters-in-net"></a>Стандартные счетчики событий в .NET

В библиотеках и среде выполнения .NET реализовано и опубликовано несколько объектов [`EventCounter`](./event-counters.md), которые можно использовать для выявления и диагностики различных проблем с производительностью. В этом документе приводятся справочные сведения о поставщиках, которые можно использовать для отслеживания этих объектов `EventCounters`, а также их описание.

## <a name="systemruntime-counters"></a>Счетчики "System.Runtime"

Следующие счетчики публикуются как часть среды выполнения .NET (CoreCLR) и поддерживаются в [`RuntimeEventSource.cs`](https://github.com/dotnet/runtime/blob/main/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs).

| Счетчик | Описание |
|--|--|
| :::no-loc text="% Time in GC since last GC"::: (`time-in-gc`) | Процент времени в сборке мусора с момента последнего сборки мусора |
| :::no-loc text="Allocation Rate"::: (`alloc-rate`) | Количество выделенных байтов за интервал обновления |
| :::no-loc text="CPU Usage"::: (`cpu-usage`) | Процент использования ЦП процессом относительно всех ресурсов ЦП системы |
| :::no-loc text="Exception Count"::: (`exception-count`) | Количество произошедших исключений |
| :::no-loc text="GC Heap Size"::: (`gc-heap-size`) | Количество байтов, которое должно быть выделено на основе <xref:System.GC.GetTotalMemory(System.Boolean)?displayProperty=nameWithType> |
| :::no-loc text="Gen 0 GC Count"::: (`gen-0-gc-count`) | Количество сборок мусора для поколения 0 за интервал обновления |
| :::no-loc text="Gen 0 Size"::: (`gen-0-size`) | Количество байтов для сборки мусора поколения 0 |
| :::no-loc text="Gen 1 GC Count"::: (`gen-1-gc-count`) | Количество сборок мусора для поколения 1 за интервал обновления |
| :::no-loc text="Gen 1 Size"::: (`gen-1-size`) | Количество байтов для сборки мусора поколения 1 |
| :::no-loc text="Gen 2 GC Count"::: (`gen-2-gc-count`) | Количество сборок мусора для поколения 2 за интервал обновления |
| :::no-loc text="Gen 2 Size"::: (`gen-2-size`) | Количество байтов для сборки мусора поколения 2 |
| :::no-loc text="LOH Size"::: (`loh-size`) | Количество байтов для кучи больших объектов |
| :::no-loc text="POH Size"::: (`poh-size`) | Количество байтов для кучи закрепленных объектов (доступно в .NET 5 и более поздних версиях) |
| :::no-loc text="GC Fragmentation"::: (`gc-fragmentation`) | Фрагментация кучи сборки мусора (доступно в .NET 5 и более поздних версиях) |
| :::no-loc text="Monitor Lock Contention Count"::: (`monitor-lock-contention-count`) | Значение, указывающее, сколько раз возникало состязание при попытке установить блокировку монитора на основе <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> |
| :::no-loc text="Number of Active Timers"::: (`active-timer-count`) | Количество активных в данных момент экземпляров <xref:System.Threading.Timer> на основе <xref:System.Threading.Timer.ActiveCount?displayProperty=nameWithType> |
| :::no-loc text="Number of Assemblies Loaded"::: (`assembly-count`) | Количество экземпляров <xref:System.Reflection.Assembly>, загруженных в процесс в определенный момент времени |
| :::no-loc text="ThreadPool Completed Work Item Count"::: (`threadpool-completed-items-count`) | Количество рабочих элементов, обработанных на данный момент в <xref:System.Threading.ThreadPool> |
| :::no-loc text="ThreadPool Queue Length"::: (`threadpool-queue-length`) | Количество рабочих элементов, находящихся в настоящее время в очереди на обработку в <xref:System.Threading.ThreadPool> |
| :::no-loc text="ThreadPool Thread Count"::: (`threadpool-thread-count`) | Текущее количество потоков пула потоков в <xref:System.Threading.ThreadPool> на основе <xref:System.Threading.ThreadPool.ThreadCount?displayProperty=nameWithType> |
| :::no-loc text="Working Set"::: (`working-set`) | Объем физической памяти, сопоставленной контексту процесса, в определенный момент времени на основе <xref:System.Environment.WorkingSet?displayProperty=nameWithType> |
| :::no-loc text="IL Bytes Jitted"::: (`il-bytes-jitted`) | Общий размер IL, скомпилированных JIT-компилятором, в байтах (доступно в .NET 5 и более поздних версиях) |
| :::no-loc text="Method Jitted Count"::: (`method-jitted-count`) | Общее число методов, скомпилированных JIT-компилятором (доступно в .NET 5 и более поздних версиях) |

## <a name="microsoftaspnetcorehosting-counters"></a>Счетчики "Microsoft.AspNetCore.Hosting"

Следующие счетчики публикуются как часть [ASP.NET Core](/aspnet/core) и поддерживаются в [`HostingEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/main/src/Hosting/Hosting/src/Internal/HostingEventSource.cs).

| Счетчик | Описание |
|--|--|
| :::no-loc text="Current Requests"::: (`current-requests`) | Общее количество запросов, которые были запущены, но еще не остановлены |
| :::no-loc text="Failed Requests"::: (`failed-requests`) | Общее число неудачных запросов, произошедших за время существования приложения |
| :::no-loc text="Request Rate"::: (`requests-per-second`) | Количество выполняемых запросов за интервал обновления |
| :::no-loc text="Total Requests"::: (`total-requests`) | Общее число запросов, произошедших за время существования приложения |

## <a name="microsoftaspnetcorehttpconnections-counters"></a>Счетчики "Microsoft.AspNetCore.Http.Connections"

Следующие счетчики публикуются как часть [ASP.NET Core SignalR](/aspnet/core/signalr/introduction) и поддерживаются в [`HttpConnectionsEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/main/src/SignalR/common/Http.Connections/src/Internal/HttpConnectionsEventSource.cs).

| Счетчик | Описание |
|--|--|
| :::no-loc text="Average Connection Duration"::: (`connections-duration`) | Средняя продолжительность подключения в миллисекундах |
| :::no-loc text="Current Connections"::: (`current-connections`) | Количество активных подключений, которые были запущены, но еще не остановлены |
| :::no-loc text="Total Connections Started"::: (`connections-started`) | Общее число запущенных подключений |
| :::no-loc text="Total Connections Stopped"::: (`connections-stopped`) | Общее число остановленных подключений |
| :::no-loc text="Total Connections Timed Out"::: (`connections-timed-out`) | Общее число подключений, для которых истекло время ожидания |

## <a name="microsoft-aspnetcore-server-kestrel-counters"></a>Счетчики "Microsoft-AspNetCore-Server-Kestrel"

Следующие счетчики публикуются как часть [веб-сервера Kestrel ASP.NET Core](/aspnet/core/fundamentals/servers/kestrel) и поддерживаются в [`KestrelEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/main/src/Servers/Kestrel/Core/src/Internal/Infrastructure/KestrelEventSource.cs).

| Счетчик | Описание |
|--|--|
| :::no-loc text="Connection Queue Length"::: (`connection-queue-length`) | Текущая длина очереди подключения |
| :::no-loc text="Connection Rate"::: (`connections-per-second`) | Количество подключений к веб-серверу за интервал обновления |
| :::no-loc text="Current Connections"::: (`current-connections`) | Текущее количество активных подключений к веб-серверу |
| :::no-loc text="Current TLS Handshakes"::: (`current-tls-handshakes`) | Текущее количество подтверждений TLS |
| :::no-loc text="Current Upgraded Requests (WebSockets)"::: (`current-upgraded-requests`) | Текущее количество обновленных запросов (WebSockets) |
| :::no-loc text="Failed TLS Handshakes"::: (`failed-tls-handshakes`) | Общее число неудачных подтверждений TLS |
| :::no-loc text="Request Queue Length"::: (`request-queue-length`) | Текущая длина очереди запросов |
| :::no-loc text="TLS Handshake Rate"::: (`tls-handshakes-per-second`) | Количество подтверждений TLS за интервал обновления |
| :::no-loc text="Total Connections"::: (`total-connections`) | Общее число подключений к веб-серверу |
| :::no-loc text="Total TLS Handshakes"::: (`total-tls-handshakes`) | Общее число подтверждений TLS на веб-сервере |

## <a name="systemnethttp-counters"></a>Счетчики "System.Net.Http"

Следующие счетчики публикуются в стеке HTTP.  Они доступны только в .NET 5 и более поздних версий.

| Счетчик | Описание |
|--|--|
| :::no-loc text="Requests Started"::: (`requests-started`) | Количество запросов, запущенных с момента запуска процесса |
| :::no-loc text="Requests Started Rate"::: (`requests-started-rate`) | Количество запущенных запросов за интервал обновления |
| :::no-loc text="Requests Failed"::: (`requests-failed`) | Количество завершившихся сбоем запросов с момента запуска процесса |
| :::no-loc text="Requests Failed Rate"::: (`requests-failed-rate`) | Количество завершившихся сбоем запросов за интервал обновления |
| :::no-loc text="Current Requests"::: (`current-requests`) | Текущее количество HTTP-запросов, которые были запущены, но еще не завершились успехом или сбоем |
| :::no-loc text="Current HTTP 1.1 Connections"::: (`http11-connections-current-total`) | Текущее количество соединений HTTP 1.1, которые были запущены, но еще не завершились успехом или сбоем |
| :::no-loc text="Current HTTP 2.0 Connections"::: (`http20-connections-current-total`) | Текущее количество соединений HTTP 2.0, которые были запущены, но еще не завершились успехом или сбоем |
| :::no-loc text="HTTP 1.1 Requests Queue Duration"::: (`http11-requests-queue-duration`) | Средняя продолжительность пребывания запросов HTTP 1.1 в очереди запросов |
| :::no-loc text="HTTP 2.0 Requests Queue Duration"::: (`http20-requests-queue-duration`) | Средняя продолжительность пребывания запросов HTTP 2.0 в очереди запросов |

## <a name="systemnetnameresolution-counters"></a>Счетчики "System.Net.NameResolution"

Следующие счетчики используются для отслеживания метрик, связанных с поиском DNS. Они доступны только в .NET 5 и более поздних версий.

| Счетчик | Описание |
|--|--|
| :::no-loc text="DNS Lookups Requested"::: (`dns-lookups-requested`) | Количество запросов на поиск DNS, запущенных с момента запуска процесса |
| :::no-loc text="Average DNS Lookup Duration"::: (`dns-lookups-duration`) | Средняя продолжительность поиска DNS |

## <a name="systemnetsecurity-counters"></a>Счетчики "System.Net.Security"

Следующие счетчики используются для отслеживания метрик, связанных с протоколом TLS.  Они доступны только в .NET 5 и более поздних версий.

| Счетчик | Описание |
|--|--|
| :::no-loc text="TLS handshakes completed"::: (`tls-handshake-rate`) | Количество подтверждений TLS, завершенных за интервал обновления |
| :::no-loc text="Total TLS handshakes completed"::: (`total-tls-handshakes`) | Общее количество подтверждений TLS, завершенных с момента запуска процесса |
| :::no-loc text="Current TLS handshakes"::: (`current-tls-handshakes`) | Текущее количество соединений подтверждений TLS, которые были запущены, но еще не завершились |
| :::no-loc text="Total TLS handshakes failed"::: (`failed-tls-handshakes`) | Общее количество подтверждений TLS, завершившихся сбоем с момента запуска процесса |
| :::no-loc text="All TLS Sessions Active"::: (`all-tls-sessions-open`) | Количество активных сеансов TLS любой версии |
| :::no-loc text="TLS 1.0 Sessions Active"::: (`tls10-sessions-open`) | Количество активных сеансов TLS 1.0 |
| :::no-loc text="TLS 1.1 Sessions Active"::: (`tls11-sessions-open`) | Количество активных сеансов TLS 1.1 |
| :::no-loc text="TLS 1.2 Sessions Active"::: (`tls12-sessions-open`) | Количество активных сеансов TLS 1.2 |
| :::no-loc text="TLS 1.3 Sessions Active"::: (`tls13-sessions-open`) | Количество активных сеансов TLS 1.3 |
| :::no-loc text="TLS Handshake Duration"::: (`all-tls-handshake-duration`) | Средняя продолжительность всех подтверждений TLS |
| :::no-loc text="TLS 1.0 Handshake Duration"::: (`tls10-handshake-duration`) | Средняя продолжительность подтверждений TLS 1.0 |
| :::no-loc text="TLS 1.1 Handshake Duration"::: (`tls11-handshake-duration`) | Средняя продолжительность подтверждений TLS 1.1 |
| :::no-loc text="TLS 1.2 Handshake Duration"::: (`tls12-handshake-duration`) | Средняя продолжительность подтверждений TLS 1.2 |
| :::no-loc text="TLS 1.3 Handshake Duration"::: (`tls13-handshake-duration`) | Средняя продолжительность подтверждений TLS 1.3 |

## <a name="systemnetsockets-counters-available-on-net-5-and-later-versions"></a>Счетчики "System.Net.Sockets" (доступны в .NET 5 и более поздних версий)

Следующие счетчики используются для отслеживания метрик, связанных с <xref:System.Net.Sockets.Socket>.

| Счетчик | Описание |
|--|--|
| :::no-loc text="Outgoing Connections Established"::: (`outgoing-connections-established`) | Общее количество исходящих соединений, установленных с момента запуска процесса |
| :::no-loc text="Incoming Connections Established"::: (`incoming-connections-established`) | Общее количество входящих соединений, установленных с момента запуска процесса |
| :::no-loc text="Bytes Received"::: (`bytes-received`) | Общее количество байтов, полученных с момента запуска процесса |
| :::no-loc text="Bytes Sent"::: (`bytes-sent`) | Общее количество байтов, отправленных с момента запуска процесса |
| :::no-loc text="Datagrams Received"::: (`datagrams-received`) | Общее количество датаграмм, полученных с момента запуска процесса |
| :::no-loc text="Datagrams Sent"::: (`datagrams-sent`) | Общее количество датаграмм, отправленных с момента запуска процесса |
