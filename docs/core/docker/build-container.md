---
title: Руководство "Контейнеризация приложений с помощью Docker"
description: Из этого руководства вы узнаете, как контейнеризировать приложение .NET Core с помощью Docker.
ms.date: 03/22/2021
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 0a64743046d31badb10b5240a172b6e47c76d3cc
ms.sourcegitcommit: 26721a2260deabb3318cc98af8619306711153cd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2021
ms.locfileid: "105027898"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Учебник. Контейнеризация приложения .NET Core

Из этого руководства вы узнаете, как контейнеризировать приложение .NET Core с помощью Docker. Контейнеры имеют множество функций и преимуществ, таких как неизменяемая инфраструктура, предоставление переносимой архитектуры и обеспечение масштабируемости. Этот образ можно использовать для создания контейнеров в вашей локальной среде разработки, частном или общедоступном облаке.

В этом учебнике рассмотрены следующие задачи.

> [!div class="checklist"]
>
> - создать и опубликовать простое приложение .NET Core;
> - создать и настроить Dockerfile для .NET Core;
> - Создание образа Docker
> - создать и запустить контейнер Docker.

Вы также узнаете о задачах сборки и развертывания контейнера Docker для приложения .NET Core. *Платформа Docker* использует *модуль Docker* для быстрой сборки и упаковки приложений в качестве *образов Docker*. Эти образы имеют формат *Dockerfile* и предназначены для развертывания и запуска в многоуровневом контейнере.

> [!NOTE]
> Это руководство **не** относится к приложениям ASP.NET Core. Если вы используете ASP.NET Core, см. руководство по [контейнеризации приложений ASP.NET Core](/aspnet/core/host-and-deploy/docker/building-net-docker-images).

## <a name="prerequisites"></a>Предварительные требования

Установите следующие необходимые компоненты:

- [Пакет SDK для .NET Core 5.0](https://dotnet.microsoft.com/download)\
Если у вас установлена платформа .NET Core, воспользуйтесь командой `dotnet --info`, чтобы определить версию пакета SDK.
- [Docker Community Edition](https://www.docker.com/products/docker-desktop).
- Временная рабочая папка для *Dockerfile* и примера приложения .NET Core. В этом руководстве в качестве рабочей папки используется имя *docker-working*.

## <a name="create-net-core-app"></a>Создание приложения .NET Core

Вам нужно создать приложение .NET Core для выполнения контейнера Docker. Откройте терминал, создайте рабочую папку, если вы еще этого не сделали, и войдите в нее. Выполните следующую команду в рабочей папке, чтобы создать проект во вложенной папке с именем *app*:

```dotnetcli
dotnet new console -o App -n NetCore.Docker
```

Дерево папок будет выглядеть следующим образом:

```
docker-working
    └──App
        ├──NetCore.Docker.csproj
        ├──Program.cs
        └──obj
            ├──NetCore.Docker.csproj.nuget.dgspec.json
            ├──NetCore.Docker.csproj.nuget.g.props
            ├──NetCore.Docker.csproj.nuget.g.targets
            ├──project.assets.json
            └──project.nuget.cache
```

Команда `dotnet new` создает папку с именем *App* и консольное приложение Hello World. Измените каталоги и перейдите в папку *App* из сеанса терминала. Используйте команду `dotnet run`, чтобы запустить приложение. Приложение запустится и выведет `Hello World!` под командой:

```dotnetcli
dotnet run
Hello World!
```

Шаблон по умолчанию создает приложение, которое выводит текст в терминал и затем завершает работу. В этом руководстве описано, как использовать приложение с бесконечным циклом выполнения. Откройте файл *Program.cs* в текстовом редакторе.

> [!TIP]
> Если вы используете Visual Studio Code, в предыдущем сеансе терминала введите следующую команду:
>
> ```console
> code .
> ```
>
> Откроется папка *App*, которая содержит проект в Visual Studio Code.

Файл *Program.cs* должен выглядеть как следующий фрагмент кода C#:

```csharp
using System;

namespace NetCore.Docker
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Замените его кодом, который считает числа каждую секунду:

```csharp
using System;
using System.Threading.Tasks;

namespace NetCore.Docker
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                Console.WriteLine($"Counter: {++counter}");
                await Task.Delay(1000);
            }
        }
    }
}
```

Сохраните файл и протестируйте программу еще раз с помощью команды `dotnet run`. Помните, что это приложение выполняется бесконечно. Остановите его с помощью команды отмены, нажав клавиши <kbd>CTRL+C</kbd>. Ниже представлен пример таких выходных данных:

```dotnetcli
dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

Если приложению передать число в командной строке, оно досчитает до такого числа и завершит работу. Введите команду `dotnet run -- 5`, чтобы приложение досчитало до пяти.

> [!IMPORTANT]
> Все параметры после `--` не передаются команде `dotnet run`, а передаются в приложение.

## <a name="publish-net-core-app"></a>Публикация приложения .NET Core

Прежде чем добавлять приложение .NET Core в образ Docker, его необходимо опубликовать. Рекомендуется, чтобы в контейнере была запущена опубликованная версия приложения. Чтобы опубликовать приложение, выполните следующую команду:

```dotnetcli
dotnet publish -c Release
```

Эта команда компилирует приложение и помещает результат в папку *publish*. Путь к папке *publish* из рабочей папки должен быть таким: `.\App\bin\Release\net5.0\publish\`

#### <a name="windows"></a>[Windows](#tab/windows)

Получите список файлов для папки publish из папки *App*, чтобы убедиться, что файл *NetCore.Docker.dll* создан.

```powershell
dir .\bin\Release\net5.0\publish\

    Directory: C:\Users\dapine\App\bin\Release\net5.0\publish

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        4/27/2020   8:27 AM            434 NetCore.Docker.deps.json
-a----        4/27/2020   8:27 AM           6144 NetCore.Docker.dll
-a----        4/27/2020   8:27 AM         171520 NetCore.Docker.exe
-a----        4/27/2020   8:27 AM            860 NetCore.Docker.pdb
-a----        4/27/2020   8:27 AM            154 NetCore.Docker.runtimeconfig.json
```

#### <a name="linux"></a>[Linux](#tab/linux)

Воспользуйтесь командой `ls`, чтобы получить список каталога и проверить, был ли создан файл *NetCore.Docker.dll*.

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/net5.0/publish
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
```

---

## <a name="create-the-dockerfile"></a>Создание файла Dockerfile

Файл *Dockerfile* используется командой `docker build` для создания образа контейнера. Это текстовый файл с именем *Dockerfile*, не имеющий расширения.

Создайте файл с именем *Dockerfile* в каталоге, содержащем файл *CSPROJ*, и откройте его в текстовом редакторе. В этом учебнике будет использоваться образ среды выполнения ASP.NET Core (который содержит образ среды выполнения .NET Core). Он подходит для консольного приложения .NET Core.

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:5.0
```

> [!NOTE]
> Образ среды выполнения ASP.NET Core используется намеренно, хотя может использоваться образ `mcr.microsoft.com/dotnet/runtime:5.0`.

Ключевое слово `FROM` требует полного имени образа контейнера Docker. Реестр контейнеров Microsoft (MCR, mcr.microsoft.com) представляет собой коллекцию Docker Hub, в которой размещены общедоступные контейнеры. Сегмент `dotnet/core` — это репозиторий контейнеров, а сегмент `aspnet` является именем образа контейнера. Образ помечается `5.0` для управления версиями. Таким образом, `mcr.microsoft.com/dotnet/aspnet:5.0` — это среда выполнения .NET Core 5.0. Убедитесь, что вызываете версию среды выполнения, которая соответствует версии среды выполнения, с которой работает пакет SDK. Например, приложение, созданное в предыдущем разделе, использовало пакет SDK для .NET Core 5.0, а базовый образ, указанный в *Dockerfile*, имеет тег **5.0.** .

Сохраните файл *Dockerfile*. Структура каталогов рабочей папки должна выглядеть следующим образом. Некоторые файлы и папки на более глубоком уровне были опущены для экономии места в статье:

```
docker-working
    └──App
        ├──Dockerfile
        ├──NetCore.Docker.csproj
        ├──Program.cs
        ├──bin
        │   └──Release
        │       └──net5.0
        │           └──publish
        │               ├──NetCore.Docker.deps.json
        │               ├──NetCore.Docker.exe
        │               ├──NetCore.Docker.dll
        │               ├──NetCore.Docker.pdb
        │               └──NetCore.Docker.runtimeconfig.json
        └──obj
            └──...
```

В терминале выполните следующую команду:

```console
docker build -t counter-image -f Dockerfile .
```

Docker обработает все строки файла *Dockerfile*. Символ `.` в команде `docker build` используется, чтобы выполнить с помощью Docker поиск файла *Dockerfile* в текущей папке. Эта команда создает образ и локальный репозиторий с именем **counter-image**, который указывает на такой образ. После завершения работы этой команды выполните команду `docker images`, чтобы просмотреть список установленных образов:

```console
docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              e6780479db63        4 days ago          190MB
mcr.microsoft.com/dotnet/aspnet         5.0                 e6780479db63        4 days ago          190MB
```

Обратите внимание, что два образа имеют одинаковое значение **IMAGE ID**. Это связано с тем, что единственная команда в файле *Dockerfile* создает новый образ на основе существующего. Добавим в файл *Dockerfile* еще три команды. Каждая команда создает новый уровень образа, а последняя команда представляет образ, на который указывает запись в репозитории **counter-image**.

```dockerfile
COPY bin/Release/net5.0/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

Команда `COPY` предписывает Docker скопировать указанную папку на вашем компьютере в папку в контейнере. В этом примере папка *publish* копируется в папку с именем *App* в контейнере.

Команда `WORKDIR` изменяет **текущий каталог** в контейнере на *App*.

Следующая команда `ENTRYPOINT` используется, чтобы настроить с помощью Docker контейнер для запуска в качестве исполняемого файла. При запуске контейнера выполняется команда `ENTRYPOINT`. После выполнения команды контейнер автоматически остановится.

> [!TIP]
> Для повышения безопасности вы можете отказаться от конвейера диагностики. Такой отказ позволяет контейнеру выполняться в режиме только для чтения. Для этого укажите переменную среды `COMPlus_EnableDiagnostics` как `0` (непосредственно перед шагом `ENTRYPOINT`).
>
> ```dockerfile
> ENV COMPlus_EnableDiagnostics=0
> ```

В окне терминала выполните команду `docker build -t counter-image -f Dockerfile .`, а после ее выполнения — команду `docker images`.

```console
docker build -t counter-image -f Dockerfile .
Sending build context to Docker daemon  1.117MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/aspnet:5.0
 ---> e6780479db63
Step 2/4 : COPY bin/Release/net5.0/publish/ App/
 ---> d1732740eed2
Step 3/4 : WORKDIR /App
 ---> Running in b1701a42f3ff
Removing intermediate container b1701a42f3ff
 ---> 919aab5b95e3
Step 4/4 : ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
 ---> Running in c12aebd26ced
Removing intermediate container c12aebd26ced
 ---> cd11c3df9b19
Successfully built cd11c3df9b19
Successfully tagged counter-image:latest

docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              cd11c3df9b19        41 seconds ago      190MB
mcr.microsoft.com/dotnet/aspnet         5.0                 e6780479db63        4 days ago          190MB
```

Каждая команда в файле *Dockerfile* создает уровень и экземпляр **IMAGE ID**. Последний экземпляр **IMAGE ID** (ваш идентификатор будет отличаться) имеет значение **cd11c3df9b19**. Теперь вы создадите контейнер на основе этого образа.

## <a name="create-a-container"></a>Создание контейнера

Теперь, когда у вас есть образ, содержащий приложение, вы можете создать контейнер. Контейнер можно создать двумя способами. Сначала создайте остановленный контейнер.

```console
docker create --name core-counter counter-image
0f281cb3af994fba5d962cc7d482828484ea14ead6bfe386a35e5088c0058851
```

Команда `docker create` выше создает контейнер на основе образа **counter-image**. В выходных данных этой команды присутствует **CONTAINER ID** (ваш идентификатор будет отличаться) созданного контейнера. Чтобы просмотреть список *всех* контейнеров, воспользуйтесь командой `docker ps -a`:

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED           STATUS     PORTS    NAMES
0f281cb3af99    counter-image    "dotnet NetCore.Dock…"    40 seconds ago    Created             core-counter
```

### <a name="manage-the-container"></a>Управление контейнером

Контейнер был создан с определенным именем `core-counter`. Для управления контейнером используется это имя. В следующем примере используется команда `docker start` для запуска контейнера, а затем — команда `docker ps` для отображения только запущенных контейнеров:

```console
docker start core-counter
core-counter

docker ps
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS          PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    2 minutes ago    Up 11 seconds            core-counter
```

Аналогично, команда `docker stop` останавливает контейнер. В следующем примере используется команда `docker stop` для остановки контейнера, а затем — команда `docker ps` для подтверждения того, что контейнеры не запущены:

```console
docker stop core-counter
core-counter

docker ps
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="connect-to-a-container"></a>Подключение к контейнеру

После запуска контейнера вы можете подключиться к нему, чтобы просмотреть выходные данные. С помощью команд `docker start` и `docker attach` запустите контейнер и просмотрите поток вывода. В этом примере команда, вызываемая нажатием клавиш <kbd>CTRL+C</kbd>, используется для отключения от запущенного контейнера. Нажатие клавиш завершает процесс в контейнере, если не указано иное, что приведет к остановке контейнера. Параметр `--sig-proxy=false` гарантирует, что команда, вызываемая нажатием клавиш <kbd>CTRL+C</kbd>, не остановит процесс в контейнере.

После отключения от контейнера снова подключитесь к нему, чтобы убедиться в том, что он продолжает работать и считать числа.

```console
docker start core-counter
core-counter

docker attach --sig-proxy=false core-counter
Counter: 7
Counter: 8
Counter: 9
^C

docker attach --sig-proxy=false core-counter
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a>Удаление контейнера

В рамках этого руководства предполагается, что вам не нужны контейнеры, которые запущены, но не выполняют полезные действия. Удалите созданный ранее контейнер. Если контейнер запущен, остановите его.

```console
docker stop core-counter
```

В примере ниже выводится список всех контейнеров, а затем используется команда `docker rm` для удаления контейнера. После этого выполняется повторная проверка наличия запущенных контейнеров.

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS                        PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    7 minutes ago    Exited (143) 20 seconds ago            core-counter

docker rm core-counter
core-counter

docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="single-run"></a>Однократный запуск

Docker предоставляет единую команду `docker run` для создания и запуска контейнера. Она исключает необходимость в поочередном выполнении команд `docker create` и `docker start`. Вы также можете настроить ее для автоматического удаления контейнера при его остановке. Например, команда `docker run -it --rm` выполняет две операции. Сначала она автоматически подключается к контейнеру с помощью текущего терминала, а потом, после завершения работы контейнера, удаляет его:

```console
docker run -it --rm counter-image
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

Контейнер также передает параметры в выполнение приложения .NET Core. Чтобы указать приложению .NET Core считать только до 3, передайте 3.

```console
docker run -it --rm counter-image 3
Counter: 1
Counter: 2
Counter: 3
```

Во время выполнения `docker run -it` команда, вызываемая нажатием клавиш <kbd>CTRL+C</kbd>, остановит процесс, запущенный в контейнере. А это, в свою очередь, приведет к остановке контейнера. Так как в команде указан параметр `--rm`, контейнер автоматически удалится после остановки процесса. Убедитесь, что он больше не существует:

```console
docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="change-the-entrypoint"></a>Изменение команды ENTRYPOINT

Команда `docker run` также позволяет изменить команду `ENTRYPOINT` из файла *Dockerfile* для запуска другой программы, но только для соответствующего контейнера. Например, воспользуйтесь указанной ниже командой, чтобы запустить `bash` или `cmd.exe`. При необходимости измените команду.

#### <a name="windows"></a>[Windows](#tab/windows)

В этом примере команда `ENTRYPOINT` изменена на `cmd.exe`. Нажав клавиши <kbd>CTRL+C</kbd>, вы можете завершить процесс и остановить контейнер.

```console
docker run -it --rm --entrypoint "cmd.exe" counter-image

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a>[Linux](#tab/linux)

В этом примере команда `ENTRYPOINT` изменена на `bash`. Команда `exit` позволяет завершить процесс и остановить контейнер.

```bash
docker run -it --rm --entrypoint "bash" counter-image
root@b735b9799abf:/App# ls
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.exe  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
root@b735b9799abf:/App# dotnet NetCore.Docker.dll 3
Counter: 1
Counter: 2
Counter: 3
root@b735b9799abf:/App# exit
exit
```

---

## <a name="essential-commands"></a>Основные команды

В Docker есть множество различных команд, которые создают контейнеры и образы, управляют ими, а также взаимодействуют с ними. Для управления контейнерами в основном используются такие команды Docker:

- [docker build](https://docs.docker.com/engine/reference/commandline/build/)
- [docker run](https://docs.docker.com/engine/reference/commandline/run/)
- [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
- [docker stop](https://docs.docker.com/engine/reference/commandline/stop/)
- [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
- [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
- [docker image](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>Очистка ресурсов

В этом учебнике описано, как создать контейнеры и образы. При желании эти ресурсы можно удалить. Ниже представлены команды, которые позволяют сделать следующее:

01. Вывести список всех контейнеров.

    ```console
    docker ps -a
    ```

02. Остановить запущенные контейнеры по имени.

    ```console
    docker stop counter-image
    ```

03. Удалить контейнер.

    ```console
    docker rm counter-image
    ```

Затем удалите все ненужные образы на компьютере. Удалите образ, созданный с помощью файла *Dockerfile*, а затем удалите образ .NET Core, на основе которого был создан файл *Dockerfile*. Вы можете использовать значение **IMAGE ID** или строку в формате **РЕПОЗИТОРИЙ:МЕТКА**.

```console
docker rmi counter-image:latest
docker rmi mcr.microsoft.com/dotnet/aspnet:5.0
```

С помощью команды `docker images` просмотрите список установленных образов.

> [!TIP]
> Файлы образов могут иметь большой размер. Как правило, удаляются временные контейнеры, созданные в ходе тестирования и разработки приложения. При этом рекомендуется оставить базовые образы с установленной средой выполнения, если на ее основе вы планируете создавать другие образы.

## <a name="next-steps"></a>Следующие шаги

- [Узнайте, как упаковать в контейнер приложение ASP.NET Core.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [Изучите руководство по микрослужбам ASP.NET Core.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [Узнайте больше о службах Azure, которые поддерживают контейнеры.](https://azure.microsoft.com/overview/containers/)
- [Ознакомьтесь с командами Dockerfile.](https://docs.docker.com/engine/reference/builder/)
- [Изучите инструменты Visual Studio для контейнеров](/visualstudio/containers/overview)
