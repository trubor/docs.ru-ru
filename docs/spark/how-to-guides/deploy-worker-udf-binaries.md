---
title: Развертывание рабочей роли и двоичных файлов пользовательских функций .NET для Apache Spark
description: Узнайте, как развернуть рабочую роль и двоичные файлы пользовательских функций .NET для Apache Spark.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: d3e86d22a308c7124812f2c11742c2e18803b13d
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875542"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>Развертывание рабочей роли и двоичных файлов пользовательских функций .NET для Apache Spark

В этом руководстве приводятся общие инструкции по развертыванию рабочей роли и двоичных файлов пользовательских функций .NET для Apache Spark. Вы узнаете, какие переменные среды следует настроить, а также ознакомитесь с некоторыми часто используемыми параметрами для запуска приложений с помощью `spark-submit`.

## <a name="configurations"></a>Конфигурации

В конфигурациях приводятся общие переменные среды и параметры для развертывания рабочей роли и двоичных файлов пользовательских функций .NET для Apache Spark.

### <a name="environment-variables"></a>Переменные среды

При развертывании рабочих ролей и создании пользовательских функций может потребоваться задать ряд стандартных переменных среды.

| Переменная среды         | Описание
| :--------------------------- | :----------
| DOTNET_WORKER_DIR            | Путь к месту создания двоичного файла <code>Microsoft.Spark.Worker</code>.</br>Он используется драйвером Spark и будет передан в исполнители Spark. Если эта переменная не задана, исполнители Spark будут выполнять поиск по пути, указанному в переменной среды <code>PATH</code>.</br>_Пример: "C:\bin\Microsoft.Spark.Worker"_
| DOTNET_ASSEMBLY_SEARCH_PATHS | Разделенные запятыми пути, по которому <code>Microsoft.Spark.Worker</code> будет загружать сборки.</br>Обратите внимание, что, если путь начинается с символа ".", в начало будет добавлен рабочий каталог. В **режиме YARN** символ "." представляет рабочий каталог контейнера.</br>_Пример: "C:\Users\\&lt;имя пользователя&gt;\\&lt;mysparkapp&gt;\bin\Debug\\&lt;версия dotnet&gt;"_
| DOTNET_WORKER_DEBUG          | Если нужно <a href="https://github.com/dotnet/spark/blob/main/docs/developer-guide.md#debugging-user-defined-function-udf">выполнить отладку пользовательской функции</a>, присвойте этой переменной среды значение <code>1</code> перед выполнением <code>spark-submit</code>.

### <a name="parameter-options"></a>Параметры

После [упаковки](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies) приложения Spark его можно запустить с помощью `spark-submit`. В таблице ниже представлены некоторые часто используемые параметры.

| имени параметра        | Описание
| :---------------------| :----------
| --class               | Точка входа для приложения.</br>_Пример: org.apache.spark.deploy.dotnet.DotnetRunner_
| --master              | <a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">Главный URL-адрес</a> кластера.</br>_Пример: yarn_
| --deploy-mode         | Указывает, следует ли развернуть драйвер в рабочих узлах (<code>cluster</code>) или локально в качестве внешнего клиента (<code>client</code>).</br>По умолчанию: <code>client</code>
| --conf                | Произвольное свойство конфигурации Spark в формате <code>key=value</code>.</br>_Пример: spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=.\worker\Microsoft.Spark.Worker_
| --files               | Разделенный запятыми список файлов, которые следует поместить в рабочий каталог каждого исполнителя.<br/><ul><li>Обратите внимание, что этот параметр применим только в режиме YARN.</li><li>Он поддерживает указание имен файлов с помощью символа #, как в Hadoop.</br></ul>_Пример: <code>myLocalSparkApp.dll#appSeen.dll</code>. При работе в режиме YARN приложение должно использовать имя в виде <code>appSeen.dll</code> для ссылки на <code>myLocalSparkApp.dll</code>._</li>
| --archives          | Разделенный запятыми список архивов, которые следует извлечь в рабочий каталог каждого исполнителя.</br><ul><li>Обратите внимание, что этот параметр применим только в режиме YARN.</li><li>Он поддерживает указание имен файлов с помощью символа #, как в Hadoop.</br></ul>_Пример: <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code>. В этом примере ZIP-файл копируется и извлекается в папку <code>worker</code>._</li>
| application-jar       | Путь к упакованному JAR-файлу, содержащему приложение и все зависимости.</br>_Пример: hdfs://&lt;путь к файлу jar&gt;/microsoft-spark-&lt;версия&gt;.jar_
| application-arguments | Аргументы, передаваемые методу main основного класса, если таковые имеются.</br>_Пример: hdfs://&lt;путь к приложению&gt;/&lt;приложение&gt;.zip &lt;имя приложения&gt; &lt;аргументы приложения&gt;_

> [!NOTE]
> При запуске приложений с помощью `spark-submit` укажите все параметры `--options` перед `application-jar`, иначе они будут проигнорированы. Дополнительные сведения см. в [описании параметров `spark-submit`](https://spark.apache.org/docs/latest/submitting-applications.html) и [подробной статье о запуске Spark в режиме YARN](https://spark.apache.org/docs/latest/running-on-yarn.html).

## <a name="frequently-asked-questions"></a>Вопросы и ответы

### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>При запуске приложения Spark с пользовательскими функциями возникает ошибка FileNotFoundException. Что следует делать?

> **Ошибка:** [Error] [TaskRunner] [0] Произошел сбой ProcessStream() со следующим исключением. System.IO.FileNotFoundException: файл сборки "mySparkApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" не найден: "mySparkApp.dll"

**Ответ.** Проверьте, правильно ли задана переменная среды `DOTNET_ASSEMBLY_SEARCH_PATHS`. Она должна содержать путь к файлу `mySparkApp.dll`.

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>Почему после обновления версии .NET для Apache Spark и сброса переменной среды `DOTNET_WORKER_DIR` по-прежнему происходит указанная ниже ошибка `IOException`?

> **Ошибка:** Утеряна задача 0.0 на этапе 11.0 (TID 24, localhost, драйвер исполнителя): java.io.IOException: Не удается запустить программу Microsoft.Spark.Worker.exe: CreateProcess error=2. Система не может найти указанный файл.

**Ответ.** Сначала попробуйте перезапустить окно PowerShell (или другие командные окна), чтобы получить последние значения переменных среды. Затем запустите программу.

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>После отправки приложения Spark происходит ошибка `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'`.

> **Ошибка:** [Error] [TaskRunner] [0] Произошел сбой ProcessStream() со следующим исключением. System.TypeLoadException: не удалось загрузить тип System.Runtime.Remoting.Contexts.Context из сборки "mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=...".

**Ответ.** Проверьте используемую версию `Microsoft.Spark.Worker`. Имеются две версии: **.NET Framework 4.6.1** и **.NET Core 3.1.x**. В этом случае следует использовать `Microsoft.Spark.Worker.net461.win-x64-<version>` (которую можно скачать [здесь](https://github.com/dotnet/spark/releases)), так как тип `System.Runtime.Remoting.Contexts.Context` предназначен только для .NET Framework.

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>Как запустить приложение Spark с пользовательскими функциями в режиме YARN? Какие переменные среды и параметры следует использовать?

**Ответ.** Для запуска приложения Spark в режиме YARN переменные среды следует указывать в виде `spark.yarn.appMasterEnv.[EnvironmentVariableName]`. Ниже приведен пример использования `spark-submit`.

```powershell
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master yarn \
--deploy-mode cluster \
--conf spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=./worker/Microsoft.Spark.Worker-<version> \
--conf spark.yarn.appMasterEnv.DOTNET_ASSEMBLY_SEARCH_PATHS=./udfs \
--archives hdfs://<path to your files>/Microsoft.Spark.Worker.net461.win-x64-<version>.zip#worker,hdfs://<path to your files>/mySparkApp.zip#udfs \
hdfs://<path to jar file>/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar \
hdfs://<path to your files>/mySparkApp.zip mySparkApp
```

## <a name="next-steps"></a>Следующие шаги

* [Начало работы с .NET для Apache Spark](../tutorials/get-started.md)
* [Отладка приложения .NET для Apache Spark в Windows](debug.md)
