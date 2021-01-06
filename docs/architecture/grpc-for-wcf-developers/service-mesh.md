---
title: Сети службы — gRPC для разработчиков WCF
description: Использование сети службы для маршрутизации и балансировки запросов к gRPC службам в кластере Kubernetes.
ms.date: 12/15/2020
ms.openlocfilehash: a1c72a4facf1c133af912bbee242328653a051b6
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938134"
---
# <a name="service-meshes"></a><span data-ttu-id="3510d-103">Слои взаимодействия служб</span><span class="sxs-lookup"><span data-stu-id="3510d-103">Service meshes</span></span>

<span data-ttu-id="3510d-104">Сетка служб — это компонент инфраструктуры, который принимает Управление запросами службы маршрутизации в сети.</span><span class="sxs-lookup"><span data-stu-id="3510d-104">A service mesh is an infrastructure component that takes control of routing service requests within a network.</span></span> <span data-ttu-id="3510d-105">Сети служб могут обслуживать все виды сетевых проблем в кластере Kubernetes, в том числе:</span><span class="sxs-lookup"><span data-stu-id="3510d-105">Service meshes can handle all kinds of network-level concerns within a Kubernetes cluster, including:</span></span>

- <span data-ttu-id="3510d-106">обнаружение служб;</span><span class="sxs-lookup"><span data-stu-id="3510d-106">Service discovery</span></span>
- <span data-ttu-id="3510d-107">Балансировка нагрузки</span><span class="sxs-lookup"><span data-stu-id="3510d-107">Load balancing</span></span>
- <span data-ttu-id="3510d-108">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="3510d-108">Fault tolerance</span></span>
- <span data-ttu-id="3510d-109">Шифрование</span><span class="sxs-lookup"><span data-stu-id="3510d-109">Encryption</span></span>
- <span data-ttu-id="3510d-110">Наблюдение</span><span class="sxs-lookup"><span data-stu-id="3510d-110">Monitoring</span></span>

<span data-ttu-id="3510d-111">Сети службы Kubernetes работают путем добавления дополнительного контейнера, именуемого *прокси-сервером расширения*, в каждый модуль, входящий в эту сеть.</span><span class="sxs-lookup"><span data-stu-id="3510d-111">Kubernetes service meshes work by adding an extra container, called a *sidecar proxy*, to each pod included in the mesh.</span></span> <span data-ttu-id="3510d-112">Прокси-сервер обрабатывает все входящие и исходящие сетевые запросы.</span><span class="sxs-lookup"><span data-stu-id="3510d-112">The proxy takes over handling all inbound and outbound network requests.</span></span> <span data-ttu-id="3510d-113">После этого настройку и управление сетями можно настроить отдельно от контейнеров приложений.</span><span class="sxs-lookup"><span data-stu-id="3510d-113">You can then keep the configuration and management of networking matters separate from the application containers.</span></span> <span data-ttu-id="3510d-114">Во многих случаях это разделение не требует внесения изменений в код приложения.</span><span class="sxs-lookup"><span data-stu-id="3510d-114">In many cases, this separation doesn't require any changes to the application code.</span></span>

<span data-ttu-id="3510d-115">В примере, приведенном в [предыдущей главе](kubernetes.md#test-the-application), запросы gRPC из веб-приложения были направлены на один экземпляр службы gRPC.</span><span class="sxs-lookup"><span data-stu-id="3510d-115">In the [previous chapter's example](kubernetes.md#test-the-application), the gRPC requests from the web application were all routed to a single instance of the gRPC service.</span></span> <span data-ttu-id="3510d-116">Это происходит потому, что имя узла службы разрешается в IP-адрес, а этот IP-адрес кэшируется в течение времени существования `HttpClientHandler` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="3510d-116">This happens because the service's host name is resolved to an IP address, and that IP address is cached for the lifetime of the `HttpClientHandler` instance.</span></span> <span data-ttu-id="3510d-117">Это поведение можно обойти, обрабатывая поиск DNS вручную или создав несколько клиентов.</span><span class="sxs-lookup"><span data-stu-id="3510d-117">It might be possible to work around this behavior by handling DNS lookups manually or creating multiple clients.</span></span> <span data-ttu-id="3510d-118">Но это решение усложняет код приложения без добавления ценности бизнеса или клиента.</span><span class="sxs-lookup"><span data-stu-id="3510d-118">But this workaround would complicate the application code without adding any business or customer value.</span></span>

<span data-ttu-id="3510d-119">При использовании сетки службы запросы из контейнера приложения отправляются на прокси-сервер расширения.</span><span class="sxs-lookup"><span data-stu-id="3510d-119">When you use a service mesh, the requests from the application container are sent to the sidecar proxy.</span></span> <span data-ttu-id="3510d-120">Прокси-сервер расширения может затем распределять их по всем экземплярам другой службы.</span><span class="sxs-lookup"><span data-stu-id="3510d-120">The sidecar proxy can then distribute them intelligently across all instances of the other service.</span></span> <span data-ttu-id="3510d-121">Сетка также может:</span><span class="sxs-lookup"><span data-stu-id="3510d-121">The mesh can also:</span></span>

- <span data-ttu-id="3510d-122">Беспрепятственное реагирование на сбои отдельных экземпляров службы.</span><span class="sxs-lookup"><span data-stu-id="3510d-122">Respond seamlessly to failures of individual instances of a service.</span></span>
- <span data-ttu-id="3510d-123">Обрабатывает семантику повторных попыток для вызовов или истечения времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="3510d-123">Handle retry semantics for failed calls or timeouts.</span></span>
- <span data-ttu-id="3510d-124">Перенаправление невыполненных запросов на альтернативный экземпляр без возврата в клиентское приложение.</span><span class="sxs-lookup"><span data-stu-id="3510d-124">Reroute failed requests to an alternate instance without returning to the client application.</span></span>

<span data-ttu-id="3510d-125">На следующем снимке экрана показано приложение Стокквеб, работающее с сеткой службы Linkerd.</span><span class="sxs-lookup"><span data-stu-id="3510d-125">The following screenshot shows the StockWeb application running with the Linkerd service mesh.</span></span> <span data-ttu-id="3510d-126">В коде приложения нет изменений, а образ DOCKER не используется.</span><span class="sxs-lookup"><span data-stu-id="3510d-126">There are no changes to the application code, and the Docker image isn't being used.</span></span> <span data-ttu-id="3510d-127">Единственным необходимым изменением было Добавление заметки к развертыванию в файлах YAML для `stockdata` `stockweb` служб и.</span><span class="sxs-lookup"><span data-stu-id="3510d-127">The only change required was the addition of an annotation to the deployment in the YAML files for the `stockdata` and `stockweb` services.</span></span>

![Стокквеб с сетчатой службой](media/service-mesh/stockweb-servicemesh-screenshot.png)

<span data-ttu-id="3510d-129">Из столбца **сервера** можно увидеть, что запросы из приложения стокквеб были направлены в обе реплики службы стоккдата, несмотря на то, что исходит от одного `HttpClient` экземпляра в коде приложения.</span><span class="sxs-lookup"><span data-stu-id="3510d-129">You can see from the **Server** column that the requests from the StockWeb application have been routed to both replicas of the StockData service, despite originating from a single `HttpClient` instance in the application code.</span></span> <span data-ttu-id="3510d-130">На самом деле, если вы просматриваете код, вы увидите, что все 100 запросов к службе Стоккдата создаются одновременно с использованием того же `HttpClient` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="3510d-130">In fact, if you review the code, you'll see that all 100 requests to the StockData service are made simultaneously by using the same `HttpClient` instance.</span></span> <span data-ttu-id="3510d-131">При использовании сетки службы эти запросы будут сбалансированы по тем множеству, что доступны многие экземпляры служб.</span><span class="sxs-lookup"><span data-stu-id="3510d-131">With the service mesh, those requests will be balanced across however many service instances are available.</span></span>

<span data-ttu-id="3510d-132">Сети служб применяются только к трафику в кластере.</span><span class="sxs-lookup"><span data-stu-id="3510d-132">Service meshes apply only to traffic within a cluster.</span></span> <span data-ttu-id="3510d-133">Сведения о внешних клиентах см. в следующей главе [Балансировка нагрузки](load-balancing.md).</span><span class="sxs-lookup"><span data-stu-id="3510d-133">For external clients, see the next chapter, [Load Balancing](load-balancing.md).</span></span>

## <a name="service-mesh-options"></a><span data-ttu-id="3510d-134">Параметры сетки служб</span><span class="sxs-lookup"><span data-stu-id="3510d-134">Service mesh options</span></span>

<span data-ttu-id="3510d-135">В настоящее время существует три реализации универсальной сетки служб для использования с Kubernetes: [Istio](https://istio.io), [Linkerd](https://linkerd.io)и [Consul Connect](https://consul.io/mesh.html).</span><span class="sxs-lookup"><span data-stu-id="3510d-135">Three general-purpose service mesh implementations are currently available for use with Kubernetes: [Istio](https://istio.io), [Linkerd](https://linkerd.io), and [Consul Connect](https://consul.io/mesh.html).</span></span> <span data-ttu-id="3510d-136">Все три предоставляют маршрутизацию запросов и прокси-серверы, шифрование трафика, устойчивость, аутентификацию между узлами и управление трафиком.</span><span class="sxs-lookup"><span data-stu-id="3510d-136">All three provide request routing/proxying, traffic encryption, resilience, host-to-host authentication, and traffic control.</span></span>

<span data-ttu-id="3510d-137">Выбор сетки служб зависит от нескольких факторов:</span><span class="sxs-lookup"><span data-stu-id="3510d-137">Choosing a service mesh depends on multiple factors:</span></span>

- <span data-ttu-id="3510d-138">Конкретные требования Организации к затратам, соответствию требованиям, платным тарифным планам и т. д.</span><span class="sxs-lookup"><span data-stu-id="3510d-138">The organization's specific requirements around costs, compliance, paid support plans, and so on.</span></span>
- <span data-ttu-id="3510d-139">Характер кластера, его размер, количество развернутых служб и объем трафика в сети кластера.</span><span class="sxs-lookup"><span data-stu-id="3510d-139">The nature of the cluster, its size, the number of services deployed, and the volume of traffic within the cluster network.</span></span>
- <span data-ttu-id="3510d-140">Простота развертывания и управления сеткой и ее использование со службами.</span><span class="sxs-lookup"><span data-stu-id="3510d-140">Ease of deploying and managing the mesh and using it with services.</span></span>

## <a name="example-add-linkerd-to-a-deployment"></a><span data-ttu-id="3510d-141">Пример. Добавление Linkerd в развертывание</span><span class="sxs-lookup"><span data-stu-id="3510d-141">Example: Add Linkerd to a deployment</span></span>

<span data-ttu-id="3510d-142">В этом примере вы узнаете, как использовать сетку службы Linkerd с приложением *стокккубе* из [предыдущего раздела](kubernetes.md).</span><span class="sxs-lookup"><span data-stu-id="3510d-142">In this example, you'll learn how to use the Linkerd service mesh with the *StockKube* application from [the previous section](kubernetes.md).</span></span>
<span data-ttu-id="3510d-143">Чтобы выполнить этот пример, необходимо [установить интерфейс командной строки Linkerd](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span><span class="sxs-lookup"><span data-stu-id="3510d-143">To follow this example, you'll need to [install the Linkerd CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span></span> <span data-ttu-id="3510d-144">Вы можете скачать двоичные файлы Windows из раздела, содержащего выпуски GitHub.</span><span class="sxs-lookup"><span data-stu-id="3510d-144">You can download Windows binaries from the section that lists GitHub releases.</span></span> <span data-ttu-id="3510d-145">Обязательно используйте последний *стабильный* выпуск, а не один из выпусков.</span><span class="sxs-lookup"><span data-stu-id="3510d-145">Be sure to use the most recent *stable* release and not one of the edge releases.</span></span>

<span data-ttu-id="3510d-146">После установки Linkerd CLI [Начало работы](https://linkerd.io/2/getting-started/index.html) следуйте инструкциям по установке компонентов Linkerd в кластере Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="3510d-146">With the Linkerd CLI installed, follow the [Getting Started](https://linkerd.io/2/getting-started/index.html) instructions to install the Linkerd components on your Kubernetes cluster.</span></span> <span data-ttu-id="3510d-147">Эти инструкции просты, и установка на локальном экземпляре Kubernetes займет всего несколько минут.</span><span class="sxs-lookup"><span data-stu-id="3510d-147">The instructions are straightforward, and the installation should take only a couple of minutes on a local Kubernetes instance.</span></span>

### <a name="add-linkerd-to-kubernetes-deployments"></a><span data-ttu-id="3510d-148">Добавление Linkerd в развертывания Kubernetes</span><span class="sxs-lookup"><span data-stu-id="3510d-148">Add Linkerd to Kubernetes deployments</span></span>

<span data-ttu-id="3510d-149">Интерфейс командной строки Linkerd предоставляет `inject` команду для добавления необходимых разделов и свойств в файлы Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="3510d-149">The Linkerd CLI provides an `inject` command to add the necessary sections and properties to Kubernetes files.</span></span> <span data-ttu-id="3510d-150">Можно выполнить команду и записать выходные данные в новый файл.</span><span class="sxs-lookup"><span data-stu-id="3510d-150">You can run the command and write the output to a new file.</span></span>

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

<span data-ttu-id="3510d-151">Вы можете просмотреть новые файлы, чтобы узнать, какие изменения были сделаны.</span><span class="sxs-lookup"><span data-stu-id="3510d-151">You can inspect the new files to see what changes have been made.</span></span> <span data-ttu-id="3510d-152">Для объектов развертывания добавляется заметка метаданных, указывающая Linkerd вставить в модуль расширения контейнер прокси-сервера при его создании.</span><span class="sxs-lookup"><span data-stu-id="3510d-152">For deployment objects, a metadata annotation is added to tell Linkerd to inject a sidecar proxy container into the pod when it's created.</span></span>

<span data-ttu-id="3510d-153">Также можно передать выходные данные `linkerd inject` команды `kubectl` непосредственно.</span><span class="sxs-lookup"><span data-stu-id="3510d-153">It's also possible to pipe the output of the `linkerd inject` command to `kubectl` directly.</span></span> <span data-ttu-id="3510d-154">Следующие команды будут работать в PowerShell или в любой оболочке Linux.</span><span class="sxs-lookup"><span data-stu-id="3510d-154">The following commands will work in PowerShell or any Linux shell.</span></span>

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a><span data-ttu-id="3510d-155">Проверка служб на панели мониторинга Linkerd</span><span class="sxs-lookup"><span data-stu-id="3510d-155">Inspect services in the Linkerd dashboard</span></span>

<span data-ttu-id="3510d-156">Откройте панель мониторинга Linkerd с помощью `linkerd` интерфейса командной строки.</span><span class="sxs-lookup"><span data-stu-id="3510d-156">Open the Linkerd dashboard by using the `linkerd` CLI.</span></span>

```console
linkerd dashboard
```

<span data-ttu-id="3510d-157">На панели мониторинга содержатся подробные сведения обо всех службах, подключенных к сети.</span><span class="sxs-lookup"><span data-stu-id="3510d-157">The dashboard provides detailed information about all services that are connected to the mesh.</span></span>

![Панель мониторинга Linkerd, показывающая приложения Стокккубе](media/service-mesh/linkerd-screenshot.png)

<span data-ttu-id="3510d-159">Если вы увеличите число реплик службы Стоккдата gRPC, как показано в следующем примере, и обновите страницу Стокквеб в браузере, вы увидите сочетание идентификаторов в столбце **сервер** .</span><span class="sxs-lookup"><span data-stu-id="3510d-159">If you increase the number of replicas of the StockData gRPC service as shown in the following example, and refresh the StockWeb page in the browser, you should see a mix of IDs in the **Server** column.</span></span> <span data-ttu-id="3510d-160">Этот набор указывает, что все доступные экземпляры обслуживают запросы.</span><span class="sxs-lookup"><span data-stu-id="3510d-160">This mix indicates that all the available instances are serving requests.</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockdata
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockdata
  replicas: 2 # Increase the target number of instances
  template:
    metadata:
      annotations:
        linkerd.io/inject: enabled
      creationTimestamp: null
      labels:
        run: stockdata
    spec:
      containers:
      - name: stockdata
        image: stockdata:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
```

>[!div class="step-by-step"]
><span data-ttu-id="3510d-161">[Назад](kubernetes.md)
>[Вперед](load-balancing.md)</span><span class="sxs-lookup"><span data-stu-id="3510d-161">[Previous](kubernetes.md)
[Next](load-balancing.md)</span></span>
