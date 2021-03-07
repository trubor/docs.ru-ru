---
title: Стандартный блок управления состоянием ДАПР
description: Описание стандартного блока управления состоянием, его функций, преимуществ и способов его применения.
author: amolenk
ms.date: 02/07/2021
ms.reviewer: robvet
ms.openlocfilehash: 05daf18ece1da377f3d5d6a91c4839f196f14f80
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401835"
---
# <a name="the-dapr-state-management-building-block"></a><span data-ttu-id="701f4-103">Стандартный блок управления состоянием ДАПР</span><span class="sxs-lookup"><span data-stu-id="701f4-103">The Dapr state management building block</span></span>

<span data-ttu-id="701f4-104">Распределенные приложения состоят из независимых служб.</span><span class="sxs-lookup"><span data-stu-id="701f4-104">Distributed applications are composed of independent services.</span></span> <span data-ttu-id="701f4-105">Хотя каждая служба не имеет отслеживания состояния, некоторые службы должны относить состояние для выполнения бизнес-операций.</span><span class="sxs-lookup"><span data-stu-id="701f4-105">While each service should be stateless, some services must track state to complete business operations.</span></span> <span data-ttu-id="701f4-106">Рассмотрим службу корзины покупок для сайта электронной коммерции.</span><span class="sxs-lookup"><span data-stu-id="701f4-106">Consider a shopping basket service for an e-Commerce site.</span></span> <span data-ttu-id="701f4-107">Если служба не может контролировать состояние, клиент может выпустить содержимое корзины покупок, открывая веб-сайт, что приведет к потере продаж и неудовлетворенному обслуживанию клиентов.</span><span class="sxs-lookup"><span data-stu-id="701f4-107">If the service can't track state, the customer could loose the shopping basket content by leaving the website, resulting in a lost sale and an unhappy customer experience.</span></span> <span data-ttu-id="701f4-108">В этих сценариях состояние должно сохраняться в распределенном хранилище состояний.</span><span class="sxs-lookup"><span data-stu-id="701f4-108">For these scenarios, state needs to be persisted to a distributed state store.</span></span> <span data-ttu-id="701f4-109">[Стандартный блок управления состоянием ДАПР](https://docs.dapr.io/developing-applications/building-blocks/state-management/) упрощает отслеживание состояния и предлагает расширенные функции в различных хранилищах данных.</span><span class="sxs-lookup"><span data-stu-id="701f4-109">The [Dapr state management building block](https://docs.dapr.io/developing-applications/building-blocks/state-management/) simplifies state tracking and offers advanced features across various data stores.</span></span>

<span data-ttu-id="701f4-110">Чтобы испытать Стандартный блок управления состоянием, ознакомьтесь с [примером приложения счетчика в главе 3](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="701f4-110">To try out the state management building block, have a look at the [counter application sample in chapter 3](getting-started.md).</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="701f4-111">Решение</span><span class="sxs-lookup"><span data-stu-id="701f4-111">What it solves</span></span>

<span data-ttu-id="701f4-112">Отслеживание состояния в распределенном приложении может быть непростой задачей.</span><span class="sxs-lookup"><span data-stu-id="701f4-112">Tracking state in a distributed application can be challenging.</span></span> <span data-ttu-id="701f4-113">Пример:</span><span class="sxs-lookup"><span data-stu-id="701f4-113">For example:</span></span>

- <span data-ttu-id="701f4-114">Приложению могут потребоваться различные типы хранилищ данных.</span><span class="sxs-lookup"><span data-stu-id="701f4-114">The application may require different types of data stores.</span></span>
- <span data-ttu-id="701f4-115">Для доступа к данным и их обновления могут потребоваться различные уровни согласованности.</span><span class="sxs-lookup"><span data-stu-id="701f4-115">Different consistency levels may be required for accessing and updating data.</span></span>
- <span data-ttu-id="701f4-116">Несколько пользователей могут обновлять данные одновременно, что требует разрешения конфликтов.</span><span class="sxs-lookup"><span data-stu-id="701f4-116">Multiple users may update data at the same time, requiring  conflict resolution.</span></span>
- <span data-ttu-id="701f4-117">Службы должны повторить все кратковременные [временные ошибки](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) , возникающие при взаимодействии с хранилищем данных.</span><span class="sxs-lookup"><span data-stu-id="701f4-117">Services must retry any short-lived [transient errors](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) that  occur while interacting with the data store.</span></span>

<span data-ttu-id="701f4-118">Стандартный блок управления состоянием ДАПР решает эти проблемы.</span><span class="sxs-lookup"><span data-stu-id="701f4-118">The Dapr state management building block addresses these challenges.</span></span> <span data-ttu-id="701f4-119">Он упрощает отслеживание состояния без зависимостей или курс обучения по сторонним пакетам SDK хранилища.</span><span class="sxs-lookup"><span data-stu-id="701f4-119">It streamlines tracking state without dependencies or a learning curve on third-party storage SDKs.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="701f4-120">ДАПР State Management предлагает API " [ключ — значение](/azure/architecture/guide/technology-choices/data-store-overview#keyvalue-stores) ".</span><span class="sxs-lookup"><span data-stu-id="701f4-120">Dapr state management offers a [key/value](/azure/architecture/guide/technology-choices/data-store-overview#keyvalue-stores) API.</span></span> <span data-ttu-id="701f4-121">Эта функция не поддерживает хранилище реляционных данных или диаграмм.</span><span class="sxs-lookup"><span data-stu-id="701f4-121">The feature doesn't support relational or graph data storage.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="701f4-122">Принцип работы</span><span class="sxs-lookup"><span data-stu-id="701f4-122">How it works</span></span>

<span data-ttu-id="701f4-123">Приложение взаимодействует с ДАПР расширения для хранения и извлечения данных о ключе и значении.</span><span class="sxs-lookup"><span data-stu-id="701f4-123">The application interacts with a Dapr sidecar to store and retrieve key/value data.</span></span> <span data-ttu-id="701f4-124">Внутри расширения API использует настраиваемый компонент хранилища состояний для сохранения данных.</span><span class="sxs-lookup"><span data-stu-id="701f4-124">Under the hood, the sidecar API consumes a configurable state store component to persist data.</span></span> <span data-ttu-id="701f4-125">Разработчики могут выбирать из растущего набора [поддерживаемых хранилищ состояний](https://docs.dapr.io/operations/components/setup-state-store/supported-state-stores/) , включающих Azure Cosmos DB, SQL Server и Cassandra.</span><span class="sxs-lookup"><span data-stu-id="701f4-125">Developers can choose from a growing collection of [supported state stores](https://docs.dapr.io/operations/components/setup-state-store/supported-state-stores/) that include Azure Cosmos DB, SQL Server, and Cassandra.</span></span>

<span data-ttu-id="701f4-126">API можно вызывать с помощью HTTP или gRPC.</span><span class="sxs-lookup"><span data-stu-id="701f4-126">The API can be called with either HTTP or gRPC.</span></span> <span data-ttu-id="701f4-127">Используйте следующий URL-адрес для вызова API HTTP:</span><span class="sxs-lookup"><span data-stu-id="701f4-127">Use the following URL to call the HTTP API:</span></span>

```http
http://localhost:<dapr-port>/v1.0/state/<store-name>/
```

- <span data-ttu-id="701f4-128">`<dapr-port>`— HTTP-порт, прослушиваемый ДАПР.</span><span class="sxs-lookup"><span data-stu-id="701f4-128">`<dapr-port>`: the HTTP port that Dapr listens on.</span></span>
- <span data-ttu-id="701f4-129">`<store-name>`: имя используемого компонента хранилища состояний.</span><span class="sxs-lookup"><span data-stu-id="701f4-129">`<store-name>`: the name of the state store component to use.</span></span>

<span data-ttu-id="701f4-130">На рис. 5-1 показано, как служба корзины покупок с ДАПР сохраняет пару "ключ-значение" с помощью компонента хранилища состояний ДАПР с именем `statestore` .</span><span class="sxs-lookup"><span data-stu-id="701f4-130">Figure 5-1 shows how a Dapr-enabled shopping basket service stores a key/value pair using the Dapr state store component named `statestore`.</span></span>

![Схема хранения пары "ключ-значение" в хранилище состояний ДАПР.](media/state-management/state-management-flow.png)

<span data-ttu-id="701f4-132">**Рис. 5-1**.</span><span class="sxs-lookup"><span data-stu-id="701f4-132">**Figure 5-1**.</span></span> <span data-ttu-id="701f4-133">Сохранение пары "ключ-значение" в хранилище состояний ДАПР.</span><span class="sxs-lookup"><span data-stu-id="701f4-133">Storing a key/value pair in a Dapr state store.</span></span>

<span data-ttu-id="701f4-134">Обратите внимание на шаги, описанные на предыдущем рисунке.</span><span class="sxs-lookup"><span data-stu-id="701f4-134">Note the steps in the previous figure:</span></span>

1. <span data-ttu-id="701f4-135">Служба корзины вызывает API управления состоянием на ДАПР расширения.</span><span class="sxs-lookup"><span data-stu-id="701f4-135">The basket service calls the state management API on the Dapr sidecar.</span></span> <span data-ttu-id="701f4-136">Текст запроса заключает в себя массив JSON, который может содержать несколько пар "ключ-значение".</span><span class="sxs-lookup"><span data-stu-id="701f4-136">The body of the request encloses a JSON array that can contain multiple key/value pairs.</span></span>
1. <span data-ttu-id="701f4-137">ДАПР расширения определяет хранилище состояний на основе файла конфигурации компонента.</span><span class="sxs-lookup"><span data-stu-id="701f4-137">The Dapr sidecar determines the state store based on the component configuration file.</span></span> <span data-ttu-id="701f4-138">В данном случае это хранилище состояний кэша Redis.</span><span class="sxs-lookup"><span data-stu-id="701f4-138">In this case, it's a Redis cache state store.</span></span>
1. <span data-ttu-id="701f4-139">Расширения сохраняет данные в кэш Redis.</span><span class="sxs-lookup"><span data-stu-id="701f4-139">The sidecar persists the data to the Redis cache.</span></span>

<span data-ttu-id="701f4-140">Получение сохраненных данных является аналогичным вызовом API.</span><span class="sxs-lookup"><span data-stu-id="701f4-140">Retrieving the stored data is a similar API call.</span></span> <span data-ttu-id="701f4-141">В приведенном ниже примере для получения данных с помощью вызова API ДАПР расширения используется команда с *фигурой* .</span><span class="sxs-lookup"><span data-stu-id="701f4-141">In the example below, a *curl* command retrieves the data by calling the Dapr sidecar API:</span></span>

```console
curl http://localhost:3500/v1.0/state/statestore/basket1
```

<span data-ttu-id="701f4-142">Команда возвращает сохраненное состояние в тексте ответа:</span><span class="sxs-lookup"><span data-stu-id="701f4-142">The command returns the stored state in the response body:</span></span>

```json
{
  "items": [
    {
      "itemId": "DaprHoodie",
      "quantity": 1
    }
  ],
  "customerId": 1
}
```

<span data-ttu-id="701f4-143">В следующих разделах объясняется, как использовать расширенные возможности стандартного блока управления состоянием.</span><span class="sxs-lookup"><span data-stu-id="701f4-143">The following sections explain how to use the more advanced features of the state management building block.</span></span>

### <a name="consistency"></a><span data-ttu-id="701f4-144">Согласованность</span><span class="sxs-lookup"><span data-stu-id="701f4-144">Consistency</span></span>

<span data-ttu-id="701f4-145">[Cap Теорема](https://en.wikipedia.org/wiki/CAP_theorem) — это набор принципов, применяемых к распределенным системам, в которых хранится состояние.</span><span class="sxs-lookup"><span data-stu-id="701f4-145">The [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem) is a set of principles that apply to distributed systems that store state.</span></span> <span data-ttu-id="701f4-146">На рис. 5-2 показаны три свойства теоремаа CAP.</span><span class="sxs-lookup"><span data-stu-id="701f4-146">Figure 5-2 shows the three properties of the CAP theorem.</span></span>

![ОГРАНИЧЕНИЕ теорема.](media/state-management/cap-theorem.png)

<span data-ttu-id="701f4-148">**Рис. 5-2**.</span><span class="sxs-lookup"><span data-stu-id="701f4-148">**Figure 5-2**.</span></span> <span data-ttu-id="701f4-149">ОГРАНИЧЕНИЕ теорема.</span><span class="sxs-lookup"><span data-stu-id="701f4-149">The CAP theorem.</span></span>

<span data-ttu-id="701f4-150">Теорема указывает, что распределенные системы данных предлагают компромисс между согласованностью, доступностью и отклонением секций.</span><span class="sxs-lookup"><span data-stu-id="701f4-150">The theorem states that distributed data systems offer a trade-off between consistency, availability, and partition tolerance.</span></span> <span data-ttu-id="701f4-151">И все хранилища данных могут *гарантировать только два из трех свойств*:</span><span class="sxs-lookup"><span data-stu-id="701f4-151">And, that any datastore can only *guarantee two of the three properties*:</span></span>

- <span data-ttu-id="701f4-152">*Согласованность* (**C**).</span><span class="sxs-lookup"><span data-stu-id="701f4-152">*Consistency* (**C**).</span></span> <span data-ttu-id="701f4-153">Каждый узел в кластере отвечает последним данным, даже если система должна блокировать запрос до тех пор, пока все реплики не будут обновлены.</span><span class="sxs-lookup"><span data-stu-id="701f4-153">Every node in the cluster responds with the most recent data, even if the system must block the request until all replicas update.</span></span> <span data-ttu-id="701f4-154">Если вы запрашиваете "последовательную систему" для обновляемого элемента, вы не получите ответ, пока все реплики не будут успешно обновлены.</span><span class="sxs-lookup"><span data-stu-id="701f4-154">If you query a "consistent system" for an item that is currently updating, you won't get a response until all replicas successfully update.</span></span> <span data-ttu-id="701f4-155">Однако вы всегда получаете самые актуальные данные.</span><span class="sxs-lookup"><span data-stu-id="701f4-155">However, you'll always receive the most current data.</span></span>

- <span data-ttu-id="701f4-156">*Доступность* (**а**).</span><span class="sxs-lookup"><span data-stu-id="701f4-156">*Availability* (**A**).</span></span> <span data-ttu-id="701f4-157">Каждый узел возвращает немедленный ответ, даже если этот ответ не является самыми последними данными.</span><span class="sxs-lookup"><span data-stu-id="701f4-157">Every node returns an immediate response, even if that response isn't the most recent data.</span></span> <span data-ttu-id="701f4-158">Если вы запрашиваете доступную систему для обновляемого элемента, вы получите наилучший ответ, который может предоставить служба.</span><span class="sxs-lookup"><span data-stu-id="701f4-158">If you query an "available system" for an item that is updating, you'll get the best possible answer the service can provide at that moment.</span></span>

- <span data-ttu-id="701f4-159">*Допуск секции* (**P**).</span><span class="sxs-lookup"><span data-stu-id="701f4-159">*Partition Tolerance* (**P**).</span></span> <span data-ttu-id="701f4-160">Гарантирует, что система продолжит работать, даже если реплицированный узел данных завершается сбоем или теряет связь с другими реплицируемыми узлами данных.</span><span class="sxs-lookup"><span data-stu-id="701f4-160">Guarantees the system continues to operate even if a replicated data node fails or loses connectivity with other replicated data nodes.</span></span>

<span data-ttu-id="701f4-161">Распределенные приложения должны поддерживать свойство **P** .</span><span class="sxs-lookup"><span data-stu-id="701f4-161">Distributed applications must handle the **P** property.</span></span> <span data-ttu-id="701f4-162">Так как службы обмениваются данными друг с другом с помощью сетевых вызовов, произойдет перерыв в работе сети (**P**).</span><span class="sxs-lookup"><span data-stu-id="701f4-162">As services communicate among each other with network calls, network disruptions (**P**) will occur.</span></span> <span data-ttu-id="701f4-163">Учитывая это, распределенные приложения должны быть либо **ТД** , либо **CP**.</span><span class="sxs-lookup"><span data-stu-id="701f4-163">With that in mind, distributed applications must either be **AP** or **CP**.</span></span>

<span data-ttu-id="701f4-164">Приложения **AP** выбирают доступность при согласованности.</span><span class="sxs-lookup"><span data-stu-id="701f4-164">**AP** applications choose availability over consistency.</span></span> <span data-ttu-id="701f4-165">ДАПР поддерживает этот вариант и имеет **окончательную стратегию согласованности** .</span><span class="sxs-lookup"><span data-stu-id="701f4-165">Dapr supports this choice with its **eventual consistency** strategy.</span></span> <span data-ttu-id="701f4-166">Рассмотрим базовое хранилище данных, например Azure CosmosDB, которое хранит избыточные данные на нескольких репликах.</span><span class="sxs-lookup"><span data-stu-id="701f4-166">Consider an underlying data store, such as Azure CosmosDB, which stores redundant data on multiple replicas.</span></span> <span data-ttu-id="701f4-167">При окончательной согласованности хранилище состояний записывает обновление в одну реплику и завершает запрос записи с клиентом.</span><span class="sxs-lookup"><span data-stu-id="701f4-167">With eventual consistency, the state store writes the update to one replica and completes the write request with the client.</span></span> <span data-ttu-id="701f4-168">По истечении этого времени хранилище будет асинхронно обновлять свои реплики.</span><span class="sxs-lookup"><span data-stu-id="701f4-168">After this time, the store will asynchronously update its replicas.</span></span> <span data-ttu-id="701f4-169">Запросы на чтение могут возвращать данные из любой реплики, включая реплики, которые еще не получили Последнее обновление.</span><span class="sxs-lookup"><span data-stu-id="701f4-169">Read requests can return data from any of the replicas, including those replicas that haven't yet received the latest update.</span></span>

<span data-ttu-id="701f4-170">Приложения **CP** выбирают согласованность по доступности.</span><span class="sxs-lookup"><span data-stu-id="701f4-170">**CP** applications choose consistency over availability.</span></span> <span data-ttu-id="701f4-171">ДАПР поддерживает этот вариант со стратегией **строгой согласованности** .</span><span class="sxs-lookup"><span data-stu-id="701f4-171">Dapr supports this choice with its **strong consistency** strategy.</span></span> <span data-ttu-id="701f4-172">В этом случае хранилище состояний будет синхронно обновлять *все* (или, в некоторых случаях, *кворум* ) обязательные реплики *перед* завершением запроса на запись.</span><span class="sxs-lookup"><span data-stu-id="701f4-172">In this scenario, the state store will synchronously update *all* (or, in some cases, a *quorum* of) required replicas *before* completing the write request.</span></span> <span data-ttu-id="701f4-173">Операции чтения возвращают актуальные данные для всех реплик.</span><span class="sxs-lookup"><span data-stu-id="701f4-173">Read operations will return the most up-to-date data consistently across replicas.</span></span>

<span data-ttu-id="701f4-174">Уровень согласованности для операции состояния задается путем присоединения к операции указания *согласованности* .</span><span class="sxs-lookup"><span data-stu-id="701f4-174">The consistency level for a state operation is specified by attaching a *consistency hint* to the operation.</span></span> <span data-ttu-id="701f4-175">В следующей *фигурной* команде запись `Hello=World` пары "ключ-значение" записывается в хранилище состояний с помощью подсказки строгой согласованности:</span><span class="sxs-lookup"><span data-stu-id="701f4-175">The following *curl* command writes a `Hello=World` key/value pair to a state store using a strong consistency hint:</span></span>

```console
curl -X POST http://localhost:3500/v1.0/state/<store-name> \
  -H "Content-Type: application/json" \
  -d '[
        {
          "key": "Hello",
          "value": "World",
          "options": {
            "consistency": "strong"
          }
        }
      ]'
```

> [!IMPORTANT]
> <span data-ttu-id="701f4-176">Компонент хранилища состояний ДАПР позволяет выполнить подсказку согласованности, присоединенную к операции.</span><span class="sxs-lookup"><span data-stu-id="701f4-176">It is up to the Dapr state store component to fulfill the consistency hint attached to the operation.</span></span> <span data-ttu-id="701f4-177">Не все хранилища данных поддерживают оба уровня согласованности.</span><span class="sxs-lookup"><span data-stu-id="701f4-177">Not all data stores support both consistency levels.</span></span> <span data-ttu-id="701f4-178">Если подсказка о согласованности не задана, поведение по умолчанию — в **конечном итоге**.</span><span class="sxs-lookup"><span data-stu-id="701f4-178">If no consistency hint is set, the default behavior is **eventual**.</span></span>

### <a name="concurrency"></a><span data-ttu-id="701f4-179">Параллелизм</span><span class="sxs-lookup"><span data-stu-id="701f4-179">Concurrency</span></span>

<span data-ttu-id="701f4-180">В приложении с несколькими пользователями существует вероятность того, что несколько пользователей будут одновременно обновлять одни и те же данные (одновременно).</span><span class="sxs-lookup"><span data-stu-id="701f4-180">In a multi-user application, there's a chance that multiple users will update the same data concurrently (at the same time).</span></span> <span data-ttu-id="701f4-181">ДАПР поддерживает управление оптимистичным параллелизмом (OCC) для управления конфликтами.</span><span class="sxs-lookup"><span data-stu-id="701f4-181">Dapr supports optimistic concurrency control (OCC) to manage conflicts.</span></span> <span data-ttu-id="701f4-182">OCC основан на предположении, что конфликты обновления встречаются редко, так как пользователи работают с различными частями данных.</span><span class="sxs-lookup"><span data-stu-id="701f4-182">OCC is based on an assumption that update conflicts are uncommon because users work on different parts of the data.</span></span> <span data-ttu-id="701f4-183">Более эффективно предположить, что обновление будет выполняться, и повторить попытку, если это не так.</span><span class="sxs-lookup"><span data-stu-id="701f4-183">It's more efficient to assume an update will succeed and retry if it doesn't.</span></span> <span data-ttu-id="701f4-184">Альтернатива, реализация пессимистической блокировки может повлиять на производительность с долговременной блокировкой, вызывающей состязание за использование данных.</span><span class="sxs-lookup"><span data-stu-id="701f4-184">The alternative, implementing pessimistic locking, can affect performance with long-running locking causing data contention.</span></span>

<span data-ttu-id="701f4-185">ДАПР поддерживает управление оптимистичным параллелизмом (OCC) с помощью тегов ETag.</span><span class="sxs-lookup"><span data-stu-id="701f4-185">Dapr supports optimistic concurrency control (OCC) using ETags.</span></span> <span data-ttu-id="701f4-186">ETag — это значение, связанное с определенной версией хранимой пары "ключ-значение".</span><span class="sxs-lookup"><span data-stu-id="701f4-186">An ETag is a value associated with a specific version of a stored key/value pair.</span></span> <span data-ttu-id="701f4-187">Каждый раз при обновлении пары "ключ-значение" значение ETag также обновляется.</span><span class="sxs-lookup"><span data-stu-id="701f4-187">Each time a key/value pair updates, the ETag value updates as well.</span></span> <span data-ttu-id="701f4-188">Когда клиент получает пару "ключ-значение", ответ включает текущее значение ETag.</span><span class="sxs-lookup"><span data-stu-id="701f4-188">When a client retrieves a key/value pair, the response includes the current ETag value.</span></span> <span data-ttu-id="701f4-189">Когда клиент обновляет или удаляет пару "ключ-значение", он должен отправить значение ETag обратно в тексте запроса.</span><span class="sxs-lookup"><span data-stu-id="701f4-189">When a client updates or deletes a key/value pair, it must send that ETag value back in the request body.</span></span> <span data-ttu-id="701f4-190">Если другой клиент обновил данные, Теги ETag не будут совпадать, и запрос завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="701f4-190">If another client has updated the data in the meantime, the ETags won't match and the request will fail.</span></span> <span data-ttu-id="701f4-191">На этом этапе клиент должен получить обновленные данные, внести изменения еще раз и повторно отправить обновление.</span><span class="sxs-lookup"><span data-stu-id="701f4-191">At this point, the client must retrieve the updated data, make the change again, and resubmit the update.</span></span> <span data-ttu-id="701f4-192">Эта стратегия называется **первой записью WINS**.</span><span class="sxs-lookup"><span data-stu-id="701f4-192">This strategy is called **first-write-wins**.</span></span>

<span data-ttu-id="701f4-193">ДАПР также поддерживает стратегию **последней записи в службу WINS** .</span><span class="sxs-lookup"><span data-stu-id="701f4-193">Dapr also supports a **last-write-wins** strategy.</span></span> <span data-ttu-id="701f4-194">При таком подходе клиент не присоединяет ETag к запросу записи.</span><span class="sxs-lookup"><span data-stu-id="701f4-194">With this approach, the client doesn't attach an ETag to the write request.</span></span> <span data-ttu-id="701f4-195">Компонент хранилища состояний всегда будет разрешать обновление, даже если базовое значение было изменено во время сеанса.</span><span class="sxs-lookup"><span data-stu-id="701f4-195">The state store component will always allow the update, even if the underlying value has changed during the session.</span></span> <span data-ttu-id="701f4-196">Последняя запись — WINS полезна для сценариев записи с высокой пропускной способностью с низким состязанием за данные.</span><span class="sxs-lookup"><span data-stu-id="701f4-196">Last-write-wins is useful for high-throughput write scenarios with low data contention.</span></span> <span data-ttu-id="701f4-197">Кроме того, можно допустить случайное обновление пользователя.</span><span class="sxs-lookup"><span data-stu-id="701f4-197">As well, overwriting an occasional user update can be tolerated.</span></span>

### <a name="transactions"></a><span data-ttu-id="701f4-198">Transactions</span><span class="sxs-lookup"><span data-stu-id="701f4-198">Transactions</span></span>

<span data-ttu-id="701f4-199">ДАПР может записывать *многоэлементные изменения* в хранилище данных в виде одной операции, реализованной в виде транзакции.</span><span class="sxs-lookup"><span data-stu-id="701f4-199">Dapr can write *multi-item changes* to a data store as a single operation implemented as a transaction.</span></span> <span data-ttu-id="701f4-200">Эта функция доступна только для хранилищ данных, поддерживающих транзакции [ACID](https://en.wikipedia.org/wiki/ACID) .</span><span class="sxs-lookup"><span data-stu-id="701f4-200">This functionality is only available for data stores that support [ACID](https://en.wikipedia.org/wiki/ACID) transactions.</span></span> <span data-ttu-id="701f4-201">На момент написания этой статьи в эти магазины входят Redis, MongoDB, PostgreSQL, SQL Server и Azure CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="701f4-201">At the time of this writing, these stores include Redis, MongoDB, PostgreSQL, SQL Server, and Azure CosmosDB.</span></span>

<span data-ttu-id="701f4-202">В приведенном ниже примере операция с несколькими элементами отправляется в хранилище состояний в одной транзакции.</span><span class="sxs-lookup"><span data-stu-id="701f4-202">In the example below, a multi-item operation is sent to the state store in a single transaction.</span></span> <span data-ttu-id="701f4-203">Для фиксации транзакции должны быть выполнены все операции.</span><span class="sxs-lookup"><span data-stu-id="701f4-203">All operations must succeed for the transaction to commit.</span></span> <span data-ttu-id="701f4-204">При сбое одной или нескольких операций выполняется откат всей транзакции.</span><span class="sxs-lookup"><span data-stu-id="701f4-204">If one or more of the operations fail, the entire transaction rolls back.</span></span>

```console
curl -X POST http://localhost:3500/v1.0/state/<store-name>/transaction \
  -H "Content-Type: application/json" \
  -d '{
        "operations": [
          {
            "operation": "upsert",
            "request": { "key": "Key1", "value": "Value1"
            }
          },
          {
            "operation": "delete",
            "request": { "key": "Key2" }
          }
        ]
      }'
```

<span data-ttu-id="701f4-205">Для хранилищ данных, которые не поддерживают транзакции, несколько ключей по-прежнему можно отправить как один запрос.</span><span class="sxs-lookup"><span data-stu-id="701f4-205">For data stores that don't support transactions, multiple keys can still be sent as a single request.</span></span> <span data-ttu-id="701f4-206">В следующем примере показана операция **групповой** записи:</span><span class="sxs-lookup"><span data-stu-id="701f4-206">The following example shows a **bulk** write operation:</span></span>

```console
curl -X POST http://localhost:3500/v1.0/state/<store-name> \
  -H "Content-Type: application/json" \
  -d '[
        { "key": "Key1", "value": "Value1" },
        { "key": "Key2", "value": "Value2" }
      ]'
```

<span data-ttu-id="701f4-207">Для выполнения операций с массовыми операциями ДАПР будет отправлять каждую пару "ключ-значение" как отдельный запрос к хранилищу данных.</span><span class="sxs-lookup"><span data-stu-id="701f4-207">For bulk operations, Dapr will submit each key/value pair update as a separate request to the data store.</span></span>

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="701f4-208">Использование пакета SDK для ДАПР .NET</span><span class="sxs-lookup"><span data-stu-id="701f4-208">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="701f4-209">Пакет SDK для ДАПР для .NET обеспечивает поддержку платформы .NET Core для конкретного языка.</span><span class="sxs-lookup"><span data-stu-id="701f4-209">The Dapr .NET SDK provides language-specific support for .NET Core platform.</span></span> <span data-ttu-id="701f4-210">`DaprClient`Для чтения и записи данных разработчики могут использовать класс, представленный в [главе 3](getting-started.md) .</span><span class="sxs-lookup"><span data-stu-id="701f4-210">Developers can use the `DaprClient` class introduced in [chapter 3](getting-started.md) to read and write data.</span></span> <span data-ttu-id="701f4-211">В следующем примере показано, как использовать `DaprClient.GetStateAsync<TValue>` метод для чтения данных из хранилища состояний.</span><span class="sxs-lookup"><span data-stu-id="701f4-211">The following example shows how to use the `DaprClient.GetStateAsync<TValue>` method to read data from a state store.</span></span> <span data-ttu-id="701f4-212">Метод принимает имя хранилища, `statestore` и ключ, `AMS` в качестве параметров:</span><span class="sxs-lookup"><span data-stu-id="701f4-212">The method expects the store name, `statestore`, and key, `AMS`, as parameters:</span></span>

```csharp
var weatherForecast = await daprClient.GetStateAsync<WeatherForecast>("statestore", "AMS");
```

<span data-ttu-id="701f4-213">Если хранилище состояний не содержит данных для ключа `AMS` , результатом будет `default(WeatherForecast)` .</span><span class="sxs-lookup"><span data-stu-id="701f4-213">If the state store contains no data for key `AMS`, the result will be `default(WeatherForecast)`.</span></span>

<span data-ttu-id="701f4-214">Чтобы записать данные в хранилище данных, используйте `DaprClient.SaveStateAsync<TValue>` метод:</span><span class="sxs-lookup"><span data-stu-id="701f4-214">To write data to the data store, use the `DaprClient.SaveStateAsync<TValue>` method:</span></span>

```csharp
daprClient.SaveStateAsync("statestore", "AMS", weatherForecast);
```

<span data-ttu-id="701f4-215">В примере используется стратегия **Last-Write-WINS** , так как значение ETag не передается в компонент хранилища состояний.</span><span class="sxs-lookup"><span data-stu-id="701f4-215">The example uses the **last-write-wins** strategy as an ETag value isn't passed to the state store component.</span></span> <span data-ttu-id="701f4-216">Чтобы использовать управление оптимистичным параллелизмом (OCC) с стратегией с **первой записью WINS** , сначала извлеките текущий ETag с помощью `DaprClient.GetStateAndETagAsync` метода.</span><span class="sxs-lookup"><span data-stu-id="701f4-216">To use optimistic concurrency control (OCC) with a **first-write-wins** strategy, first retrieve the current ETag using the `DaprClient.GetStateAndETagAsync` method.</span></span> <span data-ttu-id="701f4-217">Затем запишите обновленное значение и передайте полученный ETag с помощью `DaprClient.TrySaveStateAsync` метода.</span><span class="sxs-lookup"><span data-stu-id="701f4-217">Then write the updated value and pass along the retrieved ETag using the `DaprClient.TrySaveStateAsync` method.</span></span>

```csharp
var (weatherForecast, etag) = await daprClient.GetStateAndETagAsync<WeatherForecast>("statestore", city);

// ... make some changes to the retrieved weather forecast

var result = await daprClient.TrySaveStateAsync("statestore", city, weatherForecast, etag);
```

<span data-ttu-id="701f4-218">`DaprClient.TrySaveStateAsync`Метод завершается ошибкой, если данные (и связанные с ними ETag) были изменены в хранилище состояний после извлечения данных.</span><span class="sxs-lookup"><span data-stu-id="701f4-218">The `DaprClient.TrySaveStateAsync` method fails when the data (and associated ETag) has been changed in the state store after the data was retrieved.</span></span> <span data-ttu-id="701f4-219">Метод возвращает логическое значение, указывающее, был ли вызов успешной.</span><span class="sxs-lookup"><span data-stu-id="701f4-219">The method returns a boolean value to indicate whether the call succeeded.</span></span> <span data-ttu-id="701f4-220">Стратегия обработки сбоя заключается в том, чтобы просто перезагрузить обновленные данные из хранилища состояний, внести изменения еще раз и повторно отправить обновление.</span><span class="sxs-lookup"><span data-stu-id="701f4-220">A strategy to handle the failure is to simply reload the updated data from the state store, make the change again, and resubmit the update.</span></span>

<span data-ttu-id="701f4-221">Если вы всегда хотите, чтобы запись была выполнена, независимо от других изменений данных, используйте стратегию **последней записи и WINS** .</span><span class="sxs-lookup"><span data-stu-id="701f4-221">If you always want a write to succeed regardless of other changes to the data, use the **last-write-wins** strategy.</span></span>

<span data-ttu-id="701f4-222">Пакет SDK предоставляет другие методы для получения данных в пакетном режиме, удаления данных и выполнения транзакций.</span><span class="sxs-lookup"><span data-stu-id="701f4-222">The SDK provides other methods to retrieve data in bulk, delete data, and execute transactions.</span></span> <span data-ttu-id="701f4-223">Дополнительные сведения см. в [репозитории SDK для .NET ДАПР](https://github.com/dapr/dotnet-sdk).</span><span class="sxs-lookup"><span data-stu-id="701f4-223">For more information, see the [Dapr .NET SDK repository](https://github.com/dapr/dotnet-sdk).</span></span>

### <a name="aspnet-core-integration"></a><span data-ttu-id="701f4-224">Интеграция ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="701f4-224">ASP.NET Core integration</span></span>

<span data-ttu-id="701f4-225">ДАПР также поддерживает ASP.NET Core, кросс-платформенную платформу для создания современных облачных веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="701f4-225">Dapr also supports ASP.NET Core, a cross-platform framework for building modern cloud-based web applications.</span></span> <span data-ttu-id="701f4-226">Пакет SDK для ДАПР интегрирует возможности управления состоянием непосредственно в возможности [привязки модели ASP.NET Core](/aspnet/core/mvc/models/model-binding) .</span><span class="sxs-lookup"><span data-stu-id="701f4-226">The Dapr SDK integrates state management capabilities directly into the [ASP.NET Core model binding](/aspnet/core/mvc/models/model-binding) capabilities.</span></span> <span data-ttu-id="701f4-227">Конфигурация проста.</span><span class="sxs-lookup"><span data-stu-id="701f4-227">Configuration is simple.</span></span> <span data-ttu-id="701f4-228">Добавьте, добавив `IMVCBuilder.AddDapr` `.AddDapr` метод расширения в `Startup.cs` класс, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="701f4-228">Add the `IMVCBuilder.AddDapr` by appending the `.AddDapr` extension method in your `Startup.cs` class as shown in the next example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers().AddDapr();
}
```

<span data-ttu-id="701f4-229">После настройки ДАПР может внедрить пару "ключ-значение" непосредственно в действие контроллера с помощью атрибута ASP.NET Core `FromState` .</span><span class="sxs-lookup"><span data-stu-id="701f4-229">Once configured, Dapr can inject a key/value pair directly into a controller action using the ASP.NET Core `FromState` attribute.</span></span> <span data-ttu-id="701f4-230">Обращение к `DaprClient` объекту больше не требуется.</span><span class="sxs-lookup"><span data-stu-id="701f4-230">Referencing the `DaprClient` object is no longer necessary.</span></span> <span data-ttu-id="701f4-231">В следующем примере показан веб-API, который возвращает прогноз погоды для данного города:</span><span class="sxs-lookup"><span data-stu-id="701f4-231">The next example shows a Web API that returns the weather forecast for a given city:</span></span>

```csharp
[HttpGet("{city}")]
public ActionResult<WeatherForecast> Get([FromState("statestore", "city")] StateEntry<WeatherForecast> forecast)
{
    if (forecast.Value == null)
    {
      return NotFound();
    }

    return forecast.Value;
}
```

<span data-ttu-id="701f4-232">В этом примере контроллер загружает прогноз погоды с помощью `FromState` атрибута.</span><span class="sxs-lookup"><span data-stu-id="701f4-232">In the example, the controller loads the weather forecast using the `FromState` attribute.</span></span> <span data-ttu-id="701f4-233">Первый параметр атрибута — это хранилище состояний, `statestore` .</span><span class="sxs-lookup"><span data-stu-id="701f4-233">The first attribute parameter is the state store, `statestore`.</span></span> <span data-ttu-id="701f4-234">Вторым параметром атрибута `city` является имя переменной [шаблона маршрута](/aspnet/core/mvc/controllers/routing#route-templates) для получения ключа состояния.</span><span class="sxs-lookup"><span data-stu-id="701f4-234">The second attribute parameter, `city`, is the name of the [route template](/aspnet/core/mvc/controllers/routing#route-templates) variable to get the state key.</span></span> <span data-ttu-id="701f4-235">Если опустить второй параметр, `forecast` для поиска переменной шаблона маршрута используется имя параметра привязанного метода ().</span><span class="sxs-lookup"><span data-stu-id="701f4-235">If you omit the second parameter, the name of the bound method parameter (`forecast`) is used to look up the route template variable.</span></span>

<span data-ttu-id="701f4-236">`StateEntry`Класс содержит свойства для всей информации, полученной для одной пары «ключ-значение `StoreName` »:, `Key` , `Value` и `ETag` .</span><span class="sxs-lookup"><span data-stu-id="701f4-236">The `StateEntry` class contains properties for all the information that is retrieved for a single key/value pair: `StoreName`, `Key`, `Value`, and `ETag`.</span></span> <span data-ttu-id="701f4-237">ETag полезен для реализации стратегии управления оптимистичным параллелизмом (OCC).</span><span class="sxs-lookup"><span data-stu-id="701f4-237">The ETag is useful for implementing optimistic concurrency control (OCC) strategy.</span></span> <span data-ttu-id="701f4-238">Класс также предоставляет методы для удаления или обновления полученных данных типа "ключ-значение" без необходимости использования `DaprClient` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="701f4-238">The class also provides methods to delete or update retrieved key/value data without requiring a `DaprClient` instance.</span></span> <span data-ttu-id="701f4-239">В следующем примере `TrySaveAsync` метод используется для обновления полученного прогноза погоды с помощью OCC.</span><span class="sxs-lookup"><span data-stu-id="701f4-239">In the next example, the `TrySaveAsync` method is used to update the retrieved weather forecast using OCC.</span></span>

```csharp
[HttpPut("{city}")]
public async Task Put(WeatherForecast updatedForecast, [FromState("statestore", "city")] StateEntry<WeatherForecast> currentForecast)
{
    // update cached current forecast with updated forecast passed into service endpoint
    currentForecast.Value = updatedForecast;

    // update state store
    var success = await currentForecast.TrySaveAsync();

    // ... check result
}
```

## <a name="state-store-components"></a><span data-ttu-id="701f4-240">Компоненты хранилища состояний</span><span class="sxs-lookup"><span data-stu-id="701f4-240">State store components</span></span>

<span data-ttu-id="701f4-241">На момент написания этой статьи ДАПР обеспечивает поддержку следующих транзакционных хранилищ состояний:</span><span class="sxs-lookup"><span data-stu-id="701f4-241">At the time of this writing, Dapr provides support for the following transactional state stores:</span></span>

- <span data-ttu-id="701f4-242">Azure CosmosDB</span><span class="sxs-lookup"><span data-stu-id="701f4-242">Azure CosmosDB</span></span>
- <span data-ttu-id="701f4-243">Azure SQL Server;</span><span class="sxs-lookup"><span data-stu-id="701f4-243">Azure SQL Server</span></span>
- <span data-ttu-id="701f4-244">MongoDB</span><span class="sxs-lookup"><span data-stu-id="701f4-244">MongoDB</span></span>
- <span data-ttu-id="701f4-245">PostgreSQL</span><span class="sxs-lookup"><span data-stu-id="701f4-245">PostgreSQL</span></span>
- <span data-ttu-id="701f4-246">Redis</span><span class="sxs-lookup"><span data-stu-id="701f4-246">Redis</span></span>

<span data-ttu-id="701f4-247">ДАПР также включает поддержку хранилищ состояний, поддерживающих операции CRUD, но не транзакционные возможности:</span><span class="sxs-lookup"><span data-stu-id="701f4-247">Dapr also includes support for state stores that support CRUD operations, but not transactional capabilities:</span></span>

- <span data-ttu-id="701f4-248">аероспике</span><span class="sxs-lookup"><span data-stu-id="701f4-248">Aerospike</span></span>
- <span data-ttu-id="701f4-249">Хранилище BLOB-объектов Azure</span><span class="sxs-lookup"><span data-stu-id="701f4-249">Azure Blob Storage</span></span>
- <span data-ttu-id="701f4-250">Хранилище таблиц Azure</span><span class="sxs-lookup"><span data-stu-id="701f4-250">Azure Table Storage</span></span>
- <span data-ttu-id="701f4-251">Cassandra</span><span class="sxs-lookup"><span data-stu-id="701f4-251">Cassandra</span></span>
- <span data-ttu-id="701f4-252">клаудстате</span><span class="sxs-lookup"><span data-stu-id="701f4-252">Cloudstate</span></span>
- <span data-ttu-id="701f4-253">Couchbase</span><span class="sxs-lookup"><span data-stu-id="701f4-253">Couchbase</span></span>
- <span data-ttu-id="701f4-254">etcd</span><span class="sxs-lookup"><span data-stu-id="701f4-254">etcd</span></span>
- <span data-ttu-id="701f4-255">Google Cloud Фиресторе</span><span class="sxs-lookup"><span data-stu-id="701f4-255">Google Cloud Firestore</span></span>
- <span data-ttu-id="701f4-256">Hashicorp Consul</span><span class="sxs-lookup"><span data-stu-id="701f4-256">Hashicorp Consul</span></span>
- <span data-ttu-id="701f4-257">хазелкаст</span><span class="sxs-lookup"><span data-stu-id="701f4-257">Hazelcast</span></span>
- <span data-ttu-id="701f4-258">Memcached</span><span class="sxs-lookup"><span data-stu-id="701f4-258">Memcached</span></span>
- <span data-ttu-id="701f4-259">Zookeeper</span><span class="sxs-lookup"><span data-stu-id="701f4-259">Zookeeper</span></span>

### <a name="configuration"></a><span data-ttu-id="701f4-260">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="701f4-260">Configuration</span></span>

<span data-ttu-id="701f4-261">При инициализации для локальной, автономной разработки ДАПР регистрирует Redis в качестве хранилища состояний по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="701f4-261">When initialized for local, self-hosted development, Dapr registers Redis as the default state store.</span></span> <span data-ttu-id="701f4-262">Ниже приведен пример конфигурации хранилища состояний по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="701f4-262">Here's an example of the default state store configuration.</span></span> <span data-ttu-id="701f4-263">Запишите имя по умолчанию `statestore` :</span><span class="sxs-lookup"><span data-stu-id="701f4-263">Note the default name, `statestore`:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

 > [!NOTE]
 > <span data-ttu-id="701f4-264">Многие хранилища состояний могут быть зарегистрированы в одном приложении с разными именами.</span><span class="sxs-lookup"><span data-stu-id="701f4-264">Many state stores can be registered to a single application each with a different name.</span></span>

<span data-ttu-id="701f4-265">Хранилище состояний Redis требует `redisHost` , `redisPassword` чтобы метаданные подключались к экземпляру Redis.</span><span class="sxs-lookup"><span data-stu-id="701f4-265">The Redis state store requires `redisHost` and `redisPassword` metadata to connect to the Redis instance.</span></span> <span data-ttu-id="701f4-266">В приведенном выше примере пароль Redis (по умолчанию это пустая строка) хранится в виде простой строки.</span><span class="sxs-lookup"><span data-stu-id="701f4-266">In the example above, the Redis password (which is an empty string by default) is stored as a plain string.</span></span> <span data-ttu-id="701f4-267">Рекомендуется избегать строк с четким текстом и всегда использовать секретные ссылки.</span><span class="sxs-lookup"><span data-stu-id="701f4-267">The best practice is to avoid clear-text strings and always use secret references.</span></span> <span data-ttu-id="701f4-268">Дополнительные сведения об управлении секретами см. в [главе 10](secrets.md).</span><span class="sxs-lookup"><span data-stu-id="701f4-268">To learn more about secret management, see [chapter 10](secrets.md).</span></span>

<span data-ttu-id="701f4-269">Другое поле метаданных `actorStateStore` указывает, может ли хранилище состояний использоваться стандартным блоком субъектов.</span><span class="sxs-lookup"><span data-stu-id="701f4-269">The other metadata field, `actorStateStore`, indicates whether the state store can be consumed by the actors building block.</span></span>

### <a name="key-prefix-strategies"></a><span data-ttu-id="701f4-270">Стратегии префиксов ключей</span><span class="sxs-lookup"><span data-stu-id="701f4-270">Key prefix strategies</span></span>

<span data-ttu-id="701f4-271">Компоненты хранилища состояний позволяют различным стратегиям хранить пары "ключ-значение" в базовом хранилище.</span><span class="sxs-lookup"><span data-stu-id="701f4-271">State store components enable different strategies to store key/value pairs in the underlying store.</span></span> <span data-ttu-id="701f4-272">Взпомните предыдущий пример службы корзины покупок, в которой хранятся товары, которые клиент хочет приобрести:</span><span class="sxs-lookup"><span data-stu-id="701f4-272">Recall the earlier example of a shopping basket service storing items a customer wishes to purchase:</span></span>

```console
curl -X POST http://localhost:3500/v1.0/state/statestore \
  -H "Content-Type: application/json" \
  -d '[{
        "key": "basket1",
        "value": {
          "customerId": 1,
          "items": [
            { "itemId": "DaprHoodie", "quantity": 1 }
          ]
        }
     }]'
```

<span data-ttu-id="701f4-273">С помощью средства консоли Redis просмотрите кэш Redis, чтобы увидеть, как компонент хранилища состояний Redis сохраняет данные.</span><span class="sxs-lookup"><span data-stu-id="701f4-273">Using the Redis Console tool, look inside the Redis cache to see how the Redis state store component persisted the data:</span></span>

```
127.0.0.1:6379> KEYS *
1) "basketservice||basket1"

127.0.0.1:6379> HGETALL basketservice||basket1
1) "data"
2) "{\"items\":[{\"itemId\":\"DaprHoodie\",\"quantity\":1}],\"customerId\":1}"
3) "version"
4) "1"
```

<span data-ttu-id="701f4-274">Выходные данные показывают полный **ключ** Redis для данных в виде `basketservice||basket1` .</span><span class="sxs-lookup"><span data-stu-id="701f4-274">The output shows the full Redis **key** for the data as `basketservice||basket1`.</span></span> <span data-ttu-id="701f4-275">По умолчанию ДАПР использует `application id` экземпляр ДАПР ( `basketservice` ) в качестве префикса для ключа.</span><span class="sxs-lookup"><span data-stu-id="701f4-275">By default, Dapr uses the `application id` of the Dapr instance (`basketservice`) as a prefix for the key.</span></span> <span data-ttu-id="701f4-276">Это соглашение об именовании позволяет нескольким экземплярам ДАПР совместно использовать одно и то же хранилище данных без конфликтов имен ключей.</span><span class="sxs-lookup"><span data-stu-id="701f4-276">This naming convention enables multiple Dapr instances to share the same data store without key name collisions.</span></span> <span data-ttu-id="701f4-277">Для разработчика важно всегда указывать то же самое `application id` при запуске приложения с помощью ДАПР.</span><span class="sxs-lookup"><span data-stu-id="701f4-277">For the developer, it's critical always to specify the same `application id` when running the application with Dapr.</span></span> <span data-ttu-id="701f4-278">Если этот параметр опущен, ДАПР создаст уникальный идентификатор приложения.</span><span class="sxs-lookup"><span data-stu-id="701f4-278">If omitted, Dapr will generate a unique application ID.</span></span> <span data-ttu-id="701f4-279">В случае `application id` изменения приложение больше не сможет получить доступ к состоянию, сохраненному с помощью предыдущего префикса ключа.</span><span class="sxs-lookup"><span data-stu-id="701f4-279">If the `application id` changes, the application can no longer access the state stored with the previous key prefix.</span></span>

<span data-ttu-id="701f4-280">С другой стороны, можно настроить *постоянное значение* для префикса ключа в `keyPrefix` поле метаданных в файле компонента хранилища состояний.</span><span class="sxs-lookup"><span data-stu-id="701f4-280">That said, it's possible to configure a *constant value* for the key prefix in the `keyPrefix` metadata field in the state store component file.</span></span> <span data-ttu-id="701f4-281">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="701f4-281">Consider the following example:</span></span>

```yaml
spec:
  metadata:
  - name: keyPrefix
  - value: MyPrefix
```

<span data-ttu-id="701f4-282">Префикс константного ключа обеспечивает доступ к хранилищу состояний в нескольких приложениях ДАПР.</span><span class="sxs-lookup"><span data-stu-id="701f4-282">A constant key prefix enables the state store to be accessed across multiple Dapr applications.</span></span> <span data-ttu-id="701f4-283">Более того, установка параметра `keyPrefix` позволяет `none` полностью опустить префикс.</span><span class="sxs-lookup"><span data-stu-id="701f4-283">What's more, setting the `keyPrefix` to `none` omits the prefix completely.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="701f4-284">Эталонное приложение: Ешопондапр</span><span class="sxs-lookup"><span data-stu-id="701f4-284">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="701f4-285">Эта книга содержит Справочное приложение `eShopOnDapr` .</span><span class="sxs-lookup"><span data-stu-id="701f4-285">This book includes a reference application entitled `eShopOnDapr`.</span></span> <span data-ttu-id="701f4-286">Она моделируется на основе более раннего справочного приложения по микрослужбам Майкрософт, `eShopOnContainers` .</span><span class="sxs-lookup"><span data-stu-id="701f4-286">It's modeled from an earlier Microsoft microservices reference application, `eShopOnContainers`.</span></span>

<span data-ttu-id="701f4-287">Исходная архитектура [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) использовала `IBasketRepository` интерфейс для чтения и записи данных для службы корзины.</span><span class="sxs-lookup"><span data-stu-id="701f4-287">The original [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) architecture used an `IBasketRepository` interface to read and write data for the basket service.</span></span> <span data-ttu-id="701f4-288">`RedisBasketRepository`Класс предоставил реализацию, используя Redis в качестве базового хранилища данных:</span><span class="sxs-lookup"><span data-stu-id="701f4-288">The `RedisBasketRepository` class provided the implementation using Redis as the underlying data store:</span></span>

```csharp
public class RedisBasketRepository : IBasketRepository
{
    private readonly ConnectionMultiplexer _redis;
    private readonly IDatabase _database;

    public RedisBasketRepository(ConnectionMultiplexer redis)
    {
        _redis = redis;
        _database = redis.GetDatabase();
    }

    public async Task<CustomerBasket> GetBasketAsync(string customerId)
    {
        var data = await _database.StringGetAsync(customerId);

        if (data.IsNullOrEmpty)
        {
            return null;
        }

        return JsonConvert.DeserializeObject<CustomerBasket>(data);
    }

    // ...
}
```

<span data-ttu-id="701f4-289">В этом коде используется сторонний `StackExchange.Redis` пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="701f4-289">This code uses the third-party `StackExchange.Redis` NuGet package.</span></span> <span data-ttu-id="701f4-290">Чтобы загрузить корзину покупок для данного клиента, необходимо выполнить следующие действия.</span><span class="sxs-lookup"><span data-stu-id="701f4-290">The following steps are required to load the shopping basket for a given customer:</span></span>

1. <span data-ttu-id="701f4-291">Вставьте в `ConnectionMultiplexer` конструктор.</span><span class="sxs-lookup"><span data-stu-id="701f4-291">Inject a `ConnectionMultiplexer` into the constructor.</span></span> <span data-ttu-id="701f4-292">`ConnectionMultiplexer`Регистрируется с помощью платформы внедрения зависимостей в `Startup.cs` файле:</span><span class="sxs-lookup"><span data-stu-id="701f4-292">The `ConnectionMultiplexer` is registered with the dependency injection framework in the `Startup.cs` file:</span></span>

   ```csharp
   services.AddSingleton<ConnectionMultiplexer>(sp =>
   {
       var settings = sp.GetRequiredService<IOptions<BasketSettings>>().Value;
       var configuration = ConfigurationOptions.Parse(settings.ConnectionString, true);
       configuration.ResolveDns = true;
       return ConnectionMultiplexer.Connect(configuration);
   });
   ```

1. <span data-ttu-id="701f4-293">Используйте `ConnectionMultiplexer` для создания `IDatabase` экземпляра в каждом использующем классе.</span><span class="sxs-lookup"><span data-stu-id="701f4-293">Use the `ConnectionMultiplexer` to create an `IDatabase` instance in each consuming class.</span></span>

1. <span data-ttu-id="701f4-294">Используйте `IDatabase` экземпляр для выполнения вызова Стрингжет Redis с помощью указанного в `customerId` качестве ключа.</span><span class="sxs-lookup"><span data-stu-id="701f4-294">Use the `IDatabase` instance to execute a Redis StringGet call using the given `customerId` as the key.</span></span>

1. <span data-ttu-id="701f4-295">Проверьте, загружены ли данные из Redis. Если нет, возвращается значение `null` .</span><span class="sxs-lookup"><span data-stu-id="701f4-295">Check if data is loaded from Redis; if not, return `null`.</span></span>

1. <span data-ttu-id="701f4-296">Десериализация данных из Redis в `CustomerBasket` объект и возврат результата.</span><span class="sxs-lookup"><span data-stu-id="701f4-296">Deserialize the data from Redis to a `CustomerBasket` object and return the result.</span></span>

<span data-ttu-id="701f4-297">В обновленном эталонном приложении [ешопондапр](https://github.com/dotnet-architecture/eShopOnDapr) новый `DaprBasketRepository` класс заменяет `RedisBasketRepository` класс:</span><span class="sxs-lookup"><span data-stu-id="701f4-297">In the updated [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr) reference application, a new `DaprBasketRepository` class replaces the `RedisBasketRepository` class:</span></span>

```csharp
public class DaprBasketRepository : IBasketRepository
{
    private const string StoreName = "eshop-basket-statestore";

    private readonly DaprClient _daprClient;

    public DaprBasketRepository(DaprClient daprClient)
    {
        _daprClient = daprClient ?? throw new ArgumentNullException(nameof(daprClient));;
    }

    public async Task<CustomerBasket> GetBasketAsync(string customerId)
    {
        return await _daprClient.GetStateAsync<CustomerBasket>(StoreName, customerId);
    }

    // ...
}
```

<span data-ttu-id="701f4-298">Обновленный код использует пакет SDK для .NET ДАПР для чтения и записи данных с помощью стандартного блока управления состоянием.</span><span class="sxs-lookup"><span data-stu-id="701f4-298">The updated code uses the Dapr .NET SDK to read and write data using the state management building block.</span></span> <span data-ttu-id="701f4-299">Новые шаги по загрузке корзины для клиента значительно упрощены:</span><span class="sxs-lookup"><span data-stu-id="701f4-299">The new steps to load the basket for a customer are dramatically simplified:</span></span>

1. <span data-ttu-id="701f4-300">Вставьте в `DaprClient` конструктор.</span><span class="sxs-lookup"><span data-stu-id="701f4-300">Inject a `DaprClient` into the constructor.</span></span> <span data-ttu-id="701f4-301">`DaprClient`Регистрируется в файле в инфраструктуре внедрения зависимостей `Startup.cs` .</span><span class="sxs-lookup"><span data-stu-id="701f4-301">The `DaprClient` is registered with the dependency injection framework in the `Startup.cs` file.</span></span>
1. <span data-ttu-id="701f4-302">Используйте `DaprClient.GetStateAsync` метод, чтобы загрузить элементы корзины покупок клиента из настроенного хранилища состояний и вернуть результат.</span><span class="sxs-lookup"><span data-stu-id="701f4-302">Use the `DaprClient.GetStateAsync` method to load the customer's shopping basket items from the configured state store and return the result.</span></span>

<span data-ttu-id="701f4-303">Обновленная реализация по-прежнему использует Redis в качестве базового хранилища данных.</span><span class="sxs-lookup"><span data-stu-id="701f4-303">The updated implementation still uses Redis as the underlying data store.</span></span> <span data-ttu-id="701f4-304">Но ДАПР абстрагирует `StackExchange.Redis` ссылки и сложность приложения.</span><span class="sxs-lookup"><span data-stu-id="701f4-304">But, Dapr abstracts the `StackExchange.Redis` references and complexity from the application.</span></span> <span data-ttu-id="701f4-305">Требуется файл конфигурации ДАПР:</span><span class="sxs-lookup"><span data-stu-id="701f4-305">A Dapr configuration file is all that's needed:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    secretKeyRef:
      name: redisPassword
auth:
  secretStore: eshop-secretstore
```

<span data-ttu-id="701f4-306">Реализация ДАПР также упрощает изменение базового хранилища данных.</span><span class="sxs-lookup"><span data-stu-id="701f4-306">The Dapr implementation also simplifies changing the underlying data store.</span></span> <span data-ttu-id="701f4-307">Например, для переключения на хранилище таблиц Azure требуется только изменение содержимого файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="701f4-307">For example, switching to Azure Table Storage requires only changing the contents of the configuration file.</span></span> <span data-ttu-id="701f4-308">Изменения кода не требуются.</span><span class="sxs-lookup"><span data-stu-id="701f4-308">No code changes are necessary.</span></span>

## <a name="summary"></a><span data-ttu-id="701f4-309">Итоги</span><span class="sxs-lookup"><span data-stu-id="701f4-309">Summary</span></span>

<span data-ttu-id="701f4-310">Стандартный блок управления состоянием ДАПР предоставляет API для хранения данных ключа и значения в различных хранилищах данных.</span><span class="sxs-lookup"><span data-stu-id="701f4-310">The Dapr state management building block offers an API for storing key/value data across various data stores.</span></span> <span data-ttu-id="701f4-311">API обеспечивает поддержку следующих функций:</span><span class="sxs-lookup"><span data-stu-id="701f4-311">The API provides support for:</span></span>

- <span data-ttu-id="701f4-312">Массовые операции</span><span class="sxs-lookup"><span data-stu-id="701f4-312">Bulk operations</span></span>
- <span data-ttu-id="701f4-313">Строгая и окончательная согласованность</span><span class="sxs-lookup"><span data-stu-id="701f4-313">Strong and eventual consistency</span></span>
- <span data-ttu-id="701f4-314">Управление оптимистическим параллелизмом</span><span class="sxs-lookup"><span data-stu-id="701f4-314">Optimistic concurrency control</span></span>
- <span data-ttu-id="701f4-315">Транзакции для нескольких элементов</span><span class="sxs-lookup"><span data-stu-id="701f4-315">Multi-item transactions</span></span>

<span data-ttu-id="701f4-316">Пакет SDK для .NET предоставляет поддержку для конкретного языка для .NET Core и ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="701f4-316">The .NET SDK provides language-specific support for .NET Core and ASP.NET Core.</span></span> <span data-ttu-id="701f4-317">Интеграция привязки модели упрощает доступ и обновление состояния из методов действий контроллера ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="701f4-317">Model binding integration simplifies accessing and updating state from ASP.NET Core controller action methods.</span></span>

<span data-ttu-id="701f4-318">В приложении Ешопондапр Reference преимущества перехода на управление состоянием ДАПР очевидны:</span><span class="sxs-lookup"><span data-stu-id="701f4-318">In the eShopOnDapr reference application, the benefits to moving to Dapr state management are clear:</span></span>

1. <span data-ttu-id="701f4-319">В новой реализации используется меньше строк кода.</span><span class="sxs-lookup"><span data-stu-id="701f4-319">The new implementation uses fewer lines of code.</span></span>
1. <span data-ttu-id="701f4-320">Он абстрагирует сложность API стороннего разработчика `StackExchange.Redis` .</span><span class="sxs-lookup"><span data-stu-id="701f4-320">It abstracts away the complexity of the third-party `StackExchange.Redis` API.</span></span>
1. <span data-ttu-id="701f4-321">Замена базового кэша Redis другим типом хранилища данных теперь требует только внесения изменений в файл конфигурации хранилища состояний.</span><span class="sxs-lookup"><span data-stu-id="701f4-321">Replacing the underlying Redis cache with a different type of data store now only requires changes to the state store configuration file.</span></span>

### <a name="references"></a><span data-ttu-id="701f4-322">Ссылки</span><span class="sxs-lookup"><span data-stu-id="701f4-322">References</span></span>

- [<span data-ttu-id="701f4-323">ДАПР поддерживаемые хранилища состояний</span><span class="sxs-lookup"><span data-stu-id="701f4-323">Dapr supported state stores</span></span>](https://docs.dapr.io/operations/components/setup-state-store/supported-state-stores/)

> [!div class="step-by-step"]
> <span data-ttu-id="701f4-324">[Назад](reference-application.md)
> [Вперед](service-invocation.md)</span><span class="sxs-lookup"><span data-stu-id="701f4-324">[Previous](reference-application.md)
[Next](service-invocation.md)</span></span>
