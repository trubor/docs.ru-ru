---
title: Kubernetes-gRPC для разработчиков WCF
description: Запуск ASP.NET Core gRPC Services в кластере Kubernetes.
ms.date: 12/15/2020
ms.openlocfilehash: 0b457d6fa982b5f5b983194d4aedbff0eb782f36
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938067"
---
# <a name="kubernetes"></a><span data-ttu-id="894ca-103">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="894ca-103">Kubernetes</span></span>

<span data-ttu-id="894ca-104">Хотя контейнеры можно запускать вручную на узлах DOCKER, для надежных рабочих систем лучше использовать механизм оркестрации контейнеров для управления несколькими экземплярами, работающими на нескольких серверах в кластере.</span><span class="sxs-lookup"><span data-stu-id="894ca-104">Although it's possible to run containers manually on Docker hosts, for reliable production systems it's better to use a container orchestration engine to manage multiple instances running across several servers in a cluster.</span></span> <span data-ttu-id="894ca-105">Доступны различные механизмы оркестрации контейнеров, в том числе Kubernetes, Docker Swarm и Apache Mesos.</span><span class="sxs-lookup"><span data-stu-id="894ca-105">There are various container orchestration engines available, including Kubernetes, Docker Swarm, and Apache Mesos.</span></span> <span data-ttu-id="894ca-106">Но из этих ядер Kubernetes далеко и далеко не самый широко используемый, поэтому он будет посвящен этой главе.</span><span class="sxs-lookup"><span data-stu-id="894ca-106">But of these engines, Kubernetes is far and away the most widely used, so it will be the focus of this chapter.</span></span>

<span data-ttu-id="894ca-107">Kubernetes включает следующие функциональные возможности:</span><span class="sxs-lookup"><span data-stu-id="894ca-107">Kubernetes includes the following functionality:</span></span>

- <span data-ttu-id="894ca-108">**Планирование** запускает контейнеры на нескольких узлах в кластере, обеспечивая сбалансированное использование доступного ресурса, поддержание работоспособности контейнеров при сбоях и обработку последовательных обновлений для новых версий образов или новых конфигураций.</span><span class="sxs-lookup"><span data-stu-id="894ca-108">**Scheduling** runs containers on multiple nodes within a cluster, ensuring balanced usage of the available resource, keeping containers running if there are outages, and handling rolling updates to new versions of images or new configurations.</span></span>
- <span data-ttu-id="894ca-109">**Проверки работоспособности** отслеживают контейнеры, чтобы обеспечить непрерывную работу службы.</span><span class="sxs-lookup"><span data-stu-id="894ca-109">**Health checks** monitor containers to ensure continued service.</span></span>
- <span data-ttu-id="894ca-110">**Обнаружение службы DNS &** обрабатывает маршрутизацию между службами в кластере.</span><span class="sxs-lookup"><span data-stu-id="894ca-110">**DNS & service discovery** handles routing between services within a cluster.</span></span>
- <span data-ttu-id="894ca-111">Входящий трафик **предоставляет доступ к** выбранным службам извне и обычно обеспечивает балансировку нагрузки между экземплярами этих служб.</span><span class="sxs-lookup"><span data-stu-id="894ca-111">**Ingress** exposes selected services externally and generally provides load-balancing across instances of those services.</span></span>
- <span data-ttu-id="894ca-112">**Управление ресурсами** подключает внешние ресурсы, например хранилище, к контейнерам.</span><span class="sxs-lookup"><span data-stu-id="894ca-112">**Resource management** attaches external resources like storage to containers.</span></span>

<span data-ttu-id="894ca-113">В этой главе подробно описано, как развернуть службу ASP.NET Core gRPC и веб-сайт, который использует эту службу в кластере Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="894ca-113">This chapter will detail how to deploy an ASP.NET Core gRPC service and a website that consumes the service into a Kubernetes cluster.</span></span> <span data-ttu-id="894ca-114">Пример используемого приложения доступен в репозитории [DotNet-Architecture/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) на сайте GitHub.</span><span class="sxs-lookup"><span data-stu-id="894ca-114">The sample application used is available in the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="kubernetes-terminology"></a><span data-ttu-id="894ca-115">Терминология Kubernetes</span><span class="sxs-lookup"><span data-stu-id="894ca-115">Kubernetes terminology</span></span>

<span data-ttu-id="894ca-116">Kubernetes использует *конфигурацию требуемого состояния*. API используется для *описания таких объектов*, как модули Pod, *развертывания* и *службы*, и *плоскость управления* требует реализации требуемого состояния на всех *узлах* *кластера*.</span><span class="sxs-lookup"><span data-stu-id="894ca-116">Kubernetes uses *desired state configuration*: the API is used to describe objects like *Pods*, *Deployments*, and *Services*, and the *Control Plane* takes care of implementing the desired state across all the *nodes* in a *cluster*.</span></span> <span data-ttu-id="894ca-117">В кластере Kubernetes имеется *главный* узел, на котором работает *API Kubernetes*, который можно взаимодействовать программно или с помощью `kubectl` программы командной строки.</span><span class="sxs-lookup"><span data-stu-id="894ca-117">A Kubernetes cluster has a *Master* node that runs the *Kubernetes API*, which you can communicate with programmatically or by using the `kubectl` command-line tool.</span></span> <span data-ttu-id="894ca-118">`kubectl` может создавать объекты и управлять ими с помощью аргументов командной строки, но лучше подходит для файлов YAML, содержащих данные объявления для объектов Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="894ca-118">`kubectl` can create and manage objects through command-line arguments, but it works best with YAML files that contain declaration data for Kubernetes objects.</span></span>

### <a name="kubernetes-yaml-files"></a><span data-ttu-id="894ca-119">Файлы YAML Kubernetes</span><span class="sxs-lookup"><span data-stu-id="894ca-119">Kubernetes YAML files</span></span>

<span data-ttu-id="894ca-120">Каждый файл YAML Kubernetes будет иметь по крайней мере три свойства верхнего уровня:</span><span class="sxs-lookup"><span data-stu-id="894ca-120">Every Kubernetes YAML file will have at least three top-level properties:</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

<span data-ttu-id="894ca-121">`apiVersion`Свойство используется для указания версии (и API), для которой предназначен файл.</span><span class="sxs-lookup"><span data-stu-id="894ca-121">The `apiVersion` property is used to specify which version (and which API) the file is intended for.</span></span> <span data-ttu-id="894ca-122">`kind`Свойство определяет тип объекта, представляемого YAML.</span><span class="sxs-lookup"><span data-stu-id="894ca-122">The `kind` property specifies the kind of object the YAML represents.</span></span> <span data-ttu-id="894ca-123">`metadata`Свойство содержит такие свойства объектов `name` , как, `namespace` и `labels` .</span><span class="sxs-lookup"><span data-stu-id="894ca-123">The `metadata` property contains object properties like `name`, `namespace`, and `labels`.</span></span>

<span data-ttu-id="894ca-124">В большинстве файлов YAML Kubernetes также есть `spec` раздел, описывающий ресурсы и конфигурацию, необходимые для создания объекта.</span><span class="sxs-lookup"><span data-stu-id="894ca-124">Most Kubernetes YAML files will also have a `spec` section that describes the resources and configuration necessary to create the object.</span></span>

### <a name="pods"></a><span data-ttu-id="894ca-125">Модули pod</span><span class="sxs-lookup"><span data-stu-id="894ca-125">Pods</span></span>

<span data-ttu-id="894ca-126">Модули Pod являются основными единицами выполнения в Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="894ca-126">Pods are the basic units of execution in Kubernetes.</span></span> <span data-ttu-id="894ca-127">Они могут запускать несколько контейнеров, но они также используются для выполнения отдельных контейнеров.</span><span class="sxs-lookup"><span data-stu-id="894ca-127">They can run multiple containers, but they're also used to run single containers.</span></span> <span data-ttu-id="894ca-128">Модуль также включает все ресурсы хранилища, необходимые контейнерам, и сетевой IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="894ca-128">The pod also includes any storage resources required by the containers, and the network IP address.</span></span>

### <a name="services"></a><span data-ttu-id="894ca-129">Службы</span><span class="sxs-lookup"><span data-stu-id="894ca-129">Services</span></span>

<span data-ttu-id="894ca-130">Службы являются мета-объектами, описывающими Pod (или наборы модулей), и предоставляют способ доступа к ним в кластере, например для сопоставления имени службы с набором IP-адресов Pod с помощью службы DNS кластера.</span><span class="sxs-lookup"><span data-stu-id="894ca-130">Services are meta-objects that describe Pods (or sets of Pods) and provide a way to access them within the cluster, such as mapping a service name to a set of pod IP addresses by using the cluster DNS service.</span></span>

### <a name="deployments"></a><span data-ttu-id="894ca-131">Развернутые приложения</span><span class="sxs-lookup"><span data-stu-id="894ca-131">Deployments</span></span>

<span data-ttu-id="894ca-132">Развертывания — это объекты *требуемого состояния* для модулей Pod.</span><span class="sxs-lookup"><span data-stu-id="894ca-132">Deployments are the *desired state* objects for Pods.</span></span> <span data-ttu-id="894ca-133">Если вы создаете модуль Pod вручную, он не будет перезапущен после завершения его работы.</span><span class="sxs-lookup"><span data-stu-id="894ca-133">If you create a pod manually, it won't be restarted when it terminates.</span></span> <span data-ttu-id="894ca-134">Развертывания используются для информирования кластера о том, какие модули, и сколько реплик этих модулей следует запускать в настоящее время.</span><span class="sxs-lookup"><span data-stu-id="894ca-134">Deployments are used to tell the cluster which Pods, and how many replicas of those Pods, should be running at the present time.</span></span>

### <a name="other-objects"></a><span data-ttu-id="894ca-135">Другие объекты</span><span class="sxs-lookup"><span data-stu-id="894ca-135">Other objects</span></span>

<span data-ttu-id="894ca-136">Модули Pod, службы и развертывания — это всего три основных типа объектов.</span><span class="sxs-lookup"><span data-stu-id="894ca-136">Pods, Services, and Deployments are just three of the most basic object types.</span></span> <span data-ttu-id="894ca-137">Существуют десятки других типов объектов, управляемых кластерами Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="894ca-137">There are dozens of other object types that are managed by Kubernetes clusters.</span></span> <span data-ttu-id="894ca-138">Дополнительные сведения см. в документации по [основным понятиям Kubernetes](https://kubernetes.io/docs/concepts/) .</span><span class="sxs-lookup"><span data-stu-id="894ca-138">For more information, see the [Kubernetes Concepts](https://kubernetes.io/docs/concepts/) documentation.</span></span>

### <a name="namespaces"></a><span data-ttu-id="894ca-139">Пространства имен</span><span class="sxs-lookup"><span data-stu-id="894ca-139">Namespaces</span></span>

<span data-ttu-id="894ca-140">Кластеры Kubernetes предназначены для масштабирования до сотен или тысяч узлов и для запуска аналогичного числа служб.</span><span class="sxs-lookup"><span data-stu-id="894ca-140">Kubernetes clusters are designed to scale to hundreds or thousands of nodes and to run similar numbers of services.</span></span> <span data-ttu-id="894ca-141">Чтобы избежать конфликта между именами объектов, пространства имен используются для группирования объектов вместе в составе более крупных приложений.</span><span class="sxs-lookup"><span data-stu-id="894ca-141">To avoid clashes between object names, namespaces are used to group objects together as part of larger applications.</span></span> <span data-ttu-id="894ca-142">Собственные службы Kubernetes выполняются в `default` пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="894ca-142">Kubernetes's own services run in a `default` namespace.</span></span> <span data-ttu-id="894ca-143">Все объекты пользователя должны создаваться в собственных пространствах имен, чтобы избежать возможных конфликт с объектами по умолчанию или другими клиентами в кластере.</span><span class="sxs-lookup"><span data-stu-id="894ca-143">All user objects should be created in their own namespaces to avoid potential clashes with default objects or other tenants in the cluster.</span></span>

## <a name="get-started-with-kubernetes"></a><span data-ttu-id="894ca-144">Начало работы с Kubernetes</span><span class="sxs-lookup"><span data-stu-id="894ca-144">Get started with Kubernetes</span></span>

<span data-ttu-id="894ca-145">Если вы используете DOCKER Desktop для Windows или DOCKER Desktop для Mac, Kubernetes уже доступен.</span><span class="sxs-lookup"><span data-stu-id="894ca-145">If you're running Docker Desktop for Windows or Docker Desktop for Mac, Kubernetes is already available.</span></span> <span data-ttu-id="894ca-146">Просто включите его в разделе **Kubernetes** окна **Параметры** :</span><span class="sxs-lookup"><span data-stu-id="894ca-146">Just enable it in the **Kubernetes** section of the **Settings** window:</span></span>

![Включение Kubernetes в DOCKER Desktop](media/kubernetes/enable-kubernetes-docker-desktop-v2.png)

<span data-ttu-id="894ca-148">Чтобы запустить локальный кластер Kubernetes в Linux, рассмотрите возможность [minikube](https://github.com/kubernetes/minikube)или [MicroK8s](https://microk8s.io/) , если дистрибутив Linux поддерживает [привязку](https://snapcraft.io/).</span><span class="sxs-lookup"><span data-stu-id="894ca-148">To run a local Kubernetes cluster on Linux, consider [minikube](https://github.com/kubernetes/minikube), or [MicroK8s](https://microk8s.io/) if your Linux distribution supports [snaps](https://snapcraft.io/).</span></span>

<span data-ttu-id="894ca-149">Чтобы убедиться, что кластер работает и доступен, выполните `kubectl version` команду:</span><span class="sxs-lookup"><span data-stu-id="894ca-149">To confirm that your cluster is running and accessible, run the `kubectl version` command:</span></span>

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:50:19Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:41:49Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"linux/amd64"}
```

<span data-ttu-id="894ca-150">В этом примере как CLI, так `kubectl` и сервер Kubernetes работают под управлением версии 1.14.6.</span><span class="sxs-lookup"><span data-stu-id="894ca-150">In this example, both the `kubectl` CLI and the Kubernetes server are running version 1.14.6.</span></span> <span data-ttu-id="894ca-151">Каждая версия должна `kubectl` поддерживать предыдущую и следующую версии сервера, поэтому `kubectl` 1,14 должна работать с серверными версиями 1,13 и 1,15.</span><span class="sxs-lookup"><span data-stu-id="894ca-151">Each version of `kubectl` is supposed to support the previous and next version of the server, so `kubectl` 1.14 should work with server versions 1.13 and 1.15 as well.</span></span>

## <a name="run-services-on-kubernetes"></a><span data-ttu-id="894ca-152">Запуск служб на Kubernetes</span><span class="sxs-lookup"><span data-stu-id="894ca-152">Run services on Kubernetes</span></span>

<span data-ttu-id="894ca-153">Пример приложения содержит `kube` каталог, содержащий три файла YAML.</span><span class="sxs-lookup"><span data-stu-id="894ca-153">The sample application has a `kube` directory that contains three YAML files.</span></span> <span data-ttu-id="894ca-154">`namespace.yml`Файл объявляет пользовательское пространство имен: `stocks` .</span><span class="sxs-lookup"><span data-stu-id="894ca-154">The `namespace.yml` file declares a custom namespace: `stocks`.</span></span> <span data-ttu-id="894ca-155">`stockdata.yml`Файл объявляет развертывание и службу для приложения gRPC, а `stockweb.yml` файл объявляет развертывание и службу для веб-приложения ASP.NET Core 5,0 MVC, которое использует службу gRPC.</span><span class="sxs-lookup"><span data-stu-id="894ca-155">The `stockdata.yml` file declares the Deployment and the Service for the gRPC application, and the `stockweb.yml` file declares the Deployment and Service for an ASP.NET Core 5.0 MVC web application that consumes the gRPC service.</span></span>

<span data-ttu-id="894ca-156">Чтобы использовать `YAML` файл с `kubectl` , выполните `apply -f` команду:</span><span class="sxs-lookup"><span data-stu-id="894ca-156">To use a `YAML` file with `kubectl`, run the `apply -f` command:</span></span>

```console
kubectl apply -f object.yml
```

<span data-ttu-id="894ca-157">`apply`Команда проверит допустимость файла YAML и отобразит все ошибки, полученные от API, но не ждет, пока все объекты, объявленные в файле, не будут созданы, так как этот шаг может занять некоторое время.</span><span class="sxs-lookup"><span data-stu-id="894ca-157">The `apply` command will check the validity of the YAML file and display any errors received from the API, but doesn't wait until all the objects declared in the file have been created because this step can take some time.</span></span> <span data-ttu-id="894ca-158">Используйте `kubectl get` команду с соответствующими типами объектов для проверки создания объекта в кластере.</span><span class="sxs-lookup"><span data-stu-id="894ca-158">Use the `kubectl get` command with the relevant object types to check on object creation in the cluster.</span></span>

### <a name="the-namespace-declaration"></a><span data-ttu-id="894ca-159">Объявление пространства имен</span><span class="sxs-lookup"><span data-stu-id="894ca-159">The namespace declaration</span></span>

<span data-ttu-id="894ca-160">Объявление пространства имен является простым и требует только присваивания `name` :</span><span class="sxs-lookup"><span data-stu-id="894ca-160">Namespace declaration is simple and requires only assigning a `name`:</span></span>

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

<span data-ttu-id="894ca-161">Используйте `kubectl` , чтобы применить `namespace.yml` файл и убедиться, что пространство имен успешно создано:</span><span class="sxs-lookup"><span data-stu-id="894ca-161">Use `kubectl` to apply the `namespace.yml` file and to confirm the namespace is created successfully:</span></span>

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a><span data-ttu-id="894ca-162">Приложение Стоккдата</span><span class="sxs-lookup"><span data-stu-id="894ca-162">The StockData application</span></span>

<span data-ttu-id="894ca-163">В `stockdata.yml` файле объявляются два объекта: развертывание и служба.</span><span class="sxs-lookup"><span data-stu-id="894ca-163">The `stockdata.yml` file declares two objects: a Deployment and a Service.</span></span>

#### <a name="the-stockdata-deployment"></a><span data-ttu-id="894ca-164">Развертывание Стоккдата</span><span class="sxs-lookup"><span data-stu-id="894ca-164">The StockData Deployment</span></span>

<span data-ttu-id="894ca-165">Часть развертывания файла YAML предоставляет `spec` для самого развертывания, включая необходимое количество реплик, а также `template` для создания объектов Pod и управления ими при развертывании.</span><span class="sxs-lookup"><span data-stu-id="894ca-165">The Deployment part of the YAML file provides the `spec` for the deployment itself, including the number of replicas required, and a `template` for the Pod objects to be created and managed by the deployment.</span></span> <span data-ttu-id="894ca-166">Обратите внимание, что объекты развертывания управляются `apps` API, как указано в `apiVersion` , а не в основном API Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="894ca-166">Note that Deployment objects are managed by the `apps` API, as specified in `apiVersion`, rather than the main Kubernetes API.</span></span>

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
  replicas: 1
  template:
    metadata:
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

<span data-ttu-id="894ca-167">`spec.selector`Свойство используется для сопоставления выполняющихся модулей Pod с развертыванием.</span><span class="sxs-lookup"><span data-stu-id="894ca-167">The `spec.selector` property is used to match running Pods to the Deployment.</span></span> <span data-ttu-id="894ca-168">`metadata.labels`Свойство Pod должно соответствовать `matchLabels` свойству, иначе вызов API завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="894ca-168">The Pod's `metadata.labels` property must match the `matchLabels` property or the API call will fail.</span></span>

<span data-ttu-id="894ca-169">В `template.spec` разделе объявляется контейнер для выполнения.</span><span class="sxs-lookup"><span data-stu-id="894ca-169">The `template.spec` section declares the container to be run.</span></span> <span data-ttu-id="894ca-170">При работе с локальным кластером Kubernetes, например, предоставленным с помощью DOCKER Desktop, можно указать образы, которые были собраны локально, если у них есть тег версии.</span><span class="sxs-lookup"><span data-stu-id="894ca-170">When you're working with a local Kubernetes cluster, such as the one provided by Docker Desktop, you can specify images that were built locally as long as they have a version tag.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="894ca-171">По умолчанию Kubernetes всегда проверяет и пытается извлечь новый образ.</span><span class="sxs-lookup"><span data-stu-id="894ca-171">By default, Kubernetes will always check for and try to pull a new image.</span></span> <span data-ttu-id="894ca-172">Если образ не удается найти ни в одном из известных репозиториев, создание Pod завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="894ca-172">If it can't find the image in any of its known repositories, the Pod creation will fail.</span></span> <span data-ttu-id="894ca-173">Для работы с локальными образами задайте для параметра значение `imagePullPolicy` `Never` .</span><span class="sxs-lookup"><span data-stu-id="894ca-173">To work with local images, set the `imagePullPolicy` to `Never`.</span></span>

<span data-ttu-id="894ca-174">`ports`Свойство указывает, какие порты контейнера должны быть опубликованы в модуле Pod.</span><span class="sxs-lookup"><span data-stu-id="894ca-174">The `ports` property specifies which container ports should be published on the Pod.</span></span> <span data-ttu-id="894ca-175">`stockservice`Образ запускает службу на стандартном HTTP-порте, поэтому порт 80 публикуется.</span><span class="sxs-lookup"><span data-stu-id="894ca-175">The `stockservice` image runs the service on the standard HTTP port, so port 80 is published.</span></span>

<span data-ttu-id="894ca-176">`resources`Раздел применяет ограничения ресурсов к контейнеру, выполняющемуся в модуле Pod.</span><span class="sxs-lookup"><span data-stu-id="894ca-176">The `resources` section applies resource limits to the container running within the Pod.</span></span> <span data-ttu-id="894ca-177">Это хороший подход, так как он предотвращает использование всеми доступными ЦП или памяти на узле отдельным модулем.</span><span class="sxs-lookup"><span data-stu-id="894ca-177">This is a good practice because it prevents an individual Pod from consuming all the available CPU or memory on a node.</span></span>

> [!NOTE]
> <span data-ttu-id="894ca-178">ASP.NET Core 5,0 оптимизирована и настроена для работы в контейнерах с ограниченными ресурсами.</span><span class="sxs-lookup"><span data-stu-id="894ca-178">ASP.NET Core 5.0 has been optimized and tuned to run in resource-limited containers.</span></span> <span data-ttu-id="894ca-179">`dotnet/core/aspnet`Образ DOCKER задает переменную среды, чтобы указать `dotnet` среде выполнения, что она находится в контейнере.</span><span class="sxs-lookup"><span data-stu-id="894ca-179">The `dotnet/core/aspnet` Docker image sets an environment variable to tell the `dotnet` runtime that it's in a container.</span></span>

#### <a name="the-stockdata-service"></a><span data-ttu-id="894ca-180">Служба Стоккдата</span><span class="sxs-lookup"><span data-stu-id="894ca-180">The StockData Service</span></span>

<span data-ttu-id="894ca-181">Часть службы файла YAML объявляет службу, которая предоставляет доступ к модулям Pod в кластере.</span><span class="sxs-lookup"><span data-stu-id="894ca-181">The Service part of the YAML file declares the service that provides access to the Pods within the cluster.</span></span>

```yaml
apiVersion: v1
kind: Service
metadata:
  name: stockdata
  namespace: stocks
spec:
  ports:
  - port: 80
  selector:
    run: stockdata
```

<span data-ttu-id="894ca-182">Служба `spec` использует `selector` свойство для сопоставления с выполнением `Pods` , в данном случае поиск модулей Pod с меткой `run: stockdata` .</span><span class="sxs-lookup"><span data-stu-id="894ca-182">The Service `spec` uses the `selector` property to match running `Pods`, in this case looking for Pods that have a label `run: stockdata`.</span></span> <span data-ttu-id="894ca-183">Указанный параметр `port` в соответствующих модулях Pod публикуется с помощью именованной службы.</span><span class="sxs-lookup"><span data-stu-id="894ca-183">The specified `port` on matching Pods is published by the named service.</span></span> <span data-ttu-id="894ca-184">Другие модули, выполняющиеся в `stocks` пространстве имен, могут обращаться к HTTP через эту службу, используя в `http://stockdata` качестве адреса.</span><span class="sxs-lookup"><span data-stu-id="894ca-184">Other Pods running in the `stocks` namespace can access HTTP on this service by using `http://stockdata` as the address.</span></span> <span data-ttu-id="894ca-185">Для модулей Pod, выполняющихся в других пространствах имен, можно использовать `http://stockdata.stocks` имя узла.</span><span class="sxs-lookup"><span data-stu-id="894ca-185">Pods running in other namespaces can use the `http://stockdata.stocks` host name.</span></span> <span data-ttu-id="894ca-186">Управлять доступом к службам между пространствами имен можно с помощью [политик сети](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span><span class="sxs-lookup"><span data-stu-id="894ca-186">You can control cross-namespace service access by using [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/).</span></span>

#### <a name="deploy-the-stockdata-application"></a><span data-ttu-id="894ca-187">Развертывание приложения Стоккдата</span><span class="sxs-lookup"><span data-stu-id="894ca-187">Deploy the StockData application</span></span>

<span data-ttu-id="894ca-188">Используйте `kubectl` , чтобы применить `stockdata.yml` файл и убедиться, что развертывание и служба созданы:</span><span class="sxs-lookup"><span data-stu-id="894ca-188">Use `kubectl` to apply the `stockdata.yml` file and confirm that the Deployment and Service were created:</span></span>

```console
> kubectl apply -f .\stockdata.yml
deployment.apps/stockdata created
service/stockdata created

> kubectl get deployment stockdata --namespace stocks
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
stockdata   1/1     1            1           17s

> kubectl get service stockdata --namespace stocks
NAME        TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
stockdata   ClusterIP   10.97.132.103   <none>        80/TCP    33s
```

### <a name="the-stockweb-application"></a><span data-ttu-id="894ca-189">Приложение Стокквеб</span><span class="sxs-lookup"><span data-stu-id="894ca-189">The StockWeb application</span></span>

<span data-ttu-id="894ca-190">`stockweb.yml`Файл объявляет развертывание и службу для приложения MVC.</span><span class="sxs-lookup"><span data-stu-id="894ca-190">The `stockweb.yml` file declares the Deployment and Service for the MVC application.</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockweb
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockweb
  replicas: 1
  template:
    metadata:
      labels:
        run: stockweb
    spec:
      containers:
      - name: stockweb
        image: stockweb:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
        env:
        - name: StockData__Address
          value: "http://stockdata"
        - name: DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT
          value: "true"

---

apiVersion: v1
kind: Service
metadata:
  name: stockweb
  namespace: stocks
spec:
  type: NodePort
  ports:
  - port: 80
  selector:
    run: stockweb
```

#### <a name="environment-variables"></a><span data-ttu-id="894ca-191">Переменные среды</span><span class="sxs-lookup"><span data-stu-id="894ca-191">Environment variables</span></span>

<span data-ttu-id="894ca-192">В `env` разделе объекта развертывания указываются переменные среды, которые должны быть заданы в контейнере, где выполняются `stockweb:1.0.0` образы.</span><span class="sxs-lookup"><span data-stu-id="894ca-192">The `env` section of the Deployment object specifies environment variables to be set in the container that's running the `stockweb:1.0.0` images.</span></span>

<span data-ttu-id="894ca-193">**`StockData__Address`** Переменная среды будет сопоставлена с `StockData:Address` параметром конфигурации благодаря поставщику конфигурации EnvironmentVariables.</span><span class="sxs-lookup"><span data-stu-id="894ca-193">The **`StockData__Address`** environment variable will map to the `StockData:Address` configuration setting thanks to the EnvironmentVariables configuration provider.</span></span> <span data-ttu-id="894ca-194">Этот параметр использует двойные подчеркивания между именами, чтобы разделить разделы.</span><span class="sxs-lookup"><span data-stu-id="894ca-194">This setting uses double underscores between names to separate sections.</span></span> <span data-ttu-id="894ca-195">Адрес использует имя службы `stockdata` службы, которое выполняется в том же пространстве имен Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="894ca-195">The address uses the service name of the `stockdata` Service, which is running in the same Kubernetes namespace.</span></span>

<span data-ttu-id="894ca-196">**`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** Переменная среды задает <xref:System.AppContext> параметр, который включает незашифрованные соединения HTTP/2 для <xref:System.Net.Http.HttpClient> .</span><span class="sxs-lookup"><span data-stu-id="894ca-196">The **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** environment variable sets an <xref:System.AppContext> switch that enables unencrypted HTTP/2 connections for <xref:System.Net.Http.HttpClient>.</span></span> <span data-ttu-id="894ca-197">Эта переменная среды выполняет те же действия, что и установка переключателя в коде, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="894ca-197">This environment variable does the same thing as setting the switch in code, as shown here:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="894ca-198">Если для параметра используется переменная среды, контекст можно легко изменить в зависимости от контекста, в котором выполняется приложение.</span><span class="sxs-lookup"><span data-stu-id="894ca-198">If you use an environment variable for the switch, you can easily change the context depending on the context in which the application is running.</span></span>

#### <a name="service-types"></a><span data-ttu-id="894ca-199">Типы услуг</span><span class="sxs-lookup"><span data-stu-id="894ca-199">Service types</span></span>

<span data-ttu-id="894ca-200">`type: NodePort`Свойство используется, чтобы сделать веб-приложение доступным извне кластера.</span><span class="sxs-lookup"><span data-stu-id="894ca-200">The `type: NodePort` property is used to make the web application accessible from outside the cluster.</span></span> <span data-ttu-id="894ca-201">Этот тип свойства приводит к тому, что Kubernetes публикует порт 80 в службе на произвольный порт в внешних сетевых сокетах кластера.</span><span class="sxs-lookup"><span data-stu-id="894ca-201">This property type causes Kubernetes to publish port 80 on the Service to an arbitrary port on the cluster's external network sockets.</span></span> <span data-ttu-id="894ca-202">Назначенный порт можно найти с помощью `kubectl get service` команды.</span><span class="sxs-lookup"><span data-stu-id="894ca-202">You can find the assigned port by using the `kubectl get service` command.</span></span>

<span data-ttu-id="894ca-203">`stockdata`Служба не должна быть доступна извне кластера, поэтому она использует тип по умолчанию, `ClusterIP` .</span><span class="sxs-lookup"><span data-stu-id="894ca-203">The `stockdata` Service shouldn't be accessible from outside the cluster, so it uses the default type, `ClusterIP`.</span></span>

<span data-ttu-id="894ca-204">В рабочих системах, скорее всего, будет использоваться интегрированная подсистема балансировки нагрузки для предоставления доступа к общедоступным приложениям внешним потребителям.</span><span class="sxs-lookup"><span data-stu-id="894ca-204">Production systems will most likely use an integrated load balancer to expose public applications to external consumers.</span></span> <span data-ttu-id="894ca-205">Службы, предоставляемые таким образом, должны использовать `LoadBalancer` тип.</span><span class="sxs-lookup"><span data-stu-id="894ca-205">Services exposed in this way should use the `LoadBalancer` type.</span></span>

<span data-ttu-id="894ca-206">Дополнительные сведения о типах служб см. в документации по [службам Kubernetes Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) .</span><span class="sxs-lookup"><span data-stu-id="894ca-206">For more information on Service types, see the [Kubernetes Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) documentation.</span></span>

#### <a name="deploy-the-stockweb-application"></a><span data-ttu-id="894ca-207">Развертывание приложения Стокквеб</span><span class="sxs-lookup"><span data-stu-id="894ca-207">Deploy the StockWeb application</span></span>

<span data-ttu-id="894ca-208">Используйте `kubectl` , чтобы применить `stockweb.yml` файл и убедиться, что развертывание и служба созданы:</span><span class="sxs-lookup"><span data-stu-id="894ca-208">Use `kubectl` to apply the `stockweb.yml` file and confirm that the Deployment and Service were created:</span></span>

```console
> kubectl apply -f .\stockweb.yml
deployment.apps/stockweb created
service/stockweb created

> kubectl get deployment stockweb --namespace stocks
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
stockweb   1/1     1            1           8s

> kubectl get service stockweb --namespace stocks
NAME       TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
stockweb   NodePort   10.106.141.5   <none>        80:32564/TCP   13s
```

<span data-ttu-id="894ca-209">Выходные данные `get service` команды показывают, что HTTP-порт был опубликован для порта `32564` внешней сети.</span><span class="sxs-lookup"><span data-stu-id="894ca-209">The output of the `get service` command shows that the HTTP port has been published to port `32564` on the external network.</span></span> <span data-ttu-id="894ca-210">Для приложения DOCKER Desktop этот IP-адрес будет иметь значение localhost.</span><span class="sxs-lookup"><span data-stu-id="894ca-210">For Docker Desktop, this IP address will be localhost.</span></span> <span data-ttu-id="894ca-211">Доступ к приложению можно получить, перейдя по адресу `http://localhost:32564` .</span><span class="sxs-lookup"><span data-stu-id="894ca-211">You can access the application by browsing to `http://localhost:32564`.</span></span>

### <a name="test-the-application"></a><span data-ttu-id="894ca-212">Тестирование приложения</span><span class="sxs-lookup"><span data-stu-id="894ca-212">Test the application</span></span>

<span data-ttu-id="894ca-213">В приложении Стокквеб отображается список акций НАСДАК, полученных из простой службы "запрос-ответ".</span><span class="sxs-lookup"><span data-stu-id="894ca-213">The StockWeb application displays a list of NASDAQ stocks that are retrieved from a simple request-reply service.</span></span> <span data-ttu-id="894ca-214">В этой демонстрации каждая строка также показывает уникальный идентификатор экземпляра службы, который его вернул.</span><span class="sxs-lookup"><span data-stu-id="894ca-214">For this demonstration, each line also shows the unique ID of the Service instance that returned it.</span></span>

![Снимок экрана Стокквеб](media/kubernetes/stockweb-screenshot.png)

<span data-ttu-id="894ca-216">Если количество реплик `stockdata` службы увеличилось, можно ожидать, что значение **сервера** изменится с line на Line, но на самом деле все записи 100 всегда возвращаются из одного и того же экземпляра.</span><span class="sxs-lookup"><span data-stu-id="894ca-216">If the number of replicas of the `stockdata` Service were increased, you might expect the **Server** value to change from line to line, but in fact all 100 records are always returned from the same instance.</span></span> <span data-ttu-id="894ca-217">Если страница обновляется каждые несколько секунд, идентификатор сервера остается прежним.</span><span class="sxs-lookup"><span data-stu-id="894ca-217">If you refresh the page every few seconds, the server ID remains the same.</span></span> <span data-ttu-id="894ca-218">Почему это происходит?</span><span class="sxs-lookup"><span data-stu-id="894ca-218">Why does this happen?</span></span> <span data-ttu-id="894ca-219">Здесь можно воспроизвести два фактора.</span><span class="sxs-lookup"><span data-stu-id="894ca-219">There are two factors at play here.</span></span>

<span data-ttu-id="894ca-220">Во-первых, система обнаружения службы Kubernetes по умолчанию использует балансировку нагрузки с циклическим перебором.</span><span class="sxs-lookup"><span data-stu-id="894ca-220">First, the Kubernetes Service discovery system uses round-robin load balancing by default.</span></span> <span data-ttu-id="894ca-221">При первом запросе DNS-сервера он вернет первый соответствующий IP-адрес для службы.</span><span class="sxs-lookup"><span data-stu-id="894ca-221">The first time the DNS server is queried, it will return the first matching IP address for the Service.</span></span> <span data-ttu-id="894ca-222">В следующий раз он вернет следующий IP-адрес в списке и т. д. до конца.</span><span class="sxs-lookup"><span data-stu-id="894ca-222">The next time, it will return the next IP address in the list, and so on, until the end.</span></span> <span data-ttu-id="894ca-223">На этом этапе он вернется к началу.</span><span class="sxs-lookup"><span data-stu-id="894ca-223">At that point, it loops back to the start.</span></span>

<span data-ttu-id="894ca-224">Во-вторых, объект, `HttpClient` используемый для клиента gRPC приложения стокквеб, создается и управляется [ASP.NET Core хттпклиентфактори](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), а один экземпляр этого клиента используется для каждого вызова страницы.</span><span class="sxs-lookup"><span data-stu-id="894ca-224">Second, the `HttpClient` used for the StockWeb application's gRPC client is created and managed by the [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md), and a single instance of this client is used for every call to the page.</span></span> <span data-ttu-id="894ca-225">Клиент выполняет только один поиск DNS, поэтому все запросы направляются на один и тот же IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="894ca-225">The client only does one DNS lookup, so all requests are routed to the same IP address.</span></span> <span data-ttu-id="894ca-226">И поскольку `HttpClientHandler` кэшируется в целях повышения производительности, несколько запросов в быстром выполнении будут  использовать один и тот же IP-адрес, пока не истечет кэшированный DNS-элемент или не будет удален экземпляр обработчика по некоторой причине.</span><span class="sxs-lookup"><span data-stu-id="894ca-226">And because the `HttpClientHandler` is cached for performance reasons, multiple requests in quick succession will *all* use the same IP address, until the cached DNS entry expires or the handler instance is disposed for some reason.</span></span>

<span data-ttu-id="894ca-227">В результате запросы по умолчанию к службе gRPC не сбалансированы по всем экземплярам этой службы в кластере.</span><span class="sxs-lookup"><span data-stu-id="894ca-227">The result is that by default requests to a gRPC Service aren't balanced across all instances of that Service in the cluster.</span></span> <span data-ttu-id="894ca-228">Разные потребители будут использовать разные экземпляры, но это не гарантирует хорошее распределение запросов или сбалансированное использование ресурсов.</span><span class="sxs-lookup"><span data-stu-id="894ca-228">Different consumers will use different instances, but that doesn't guarantee a good distribution of requests or a balanced use of resources.</span></span>

<span data-ttu-id="894ca-229">Следующая глава, « [сети службы](service-mesh.md)», будет решать эту проблему.</span><span class="sxs-lookup"><span data-stu-id="894ca-229">The next chapter, [Service meshes](service-mesh.md), will address this problem.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="894ca-230">[Назад](docker.md)
>[Вперед](service-mesh.md)</span><span class="sxs-lookup"><span data-stu-id="894ca-230">[Previous](docker.md)
[Next](service-mesh.md)</span></span>
