---
description: 'Дополнительные сведения: действия доступа к базе данных'
title: Действия доступа к базе данных
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: 421da4a55997dac62ccc5c598bc401a20711ec61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792548"
---
# <a name="database-access-activities"></a><span data-ttu-id="1acee-103">Действия доступа к базе данных</span><span class="sxs-lookup"><span data-stu-id="1acee-103">Database Access Activities</span></span>

<span data-ttu-id="1acee-104">Действия доступа к базе данных позволяют обращаться к базе данных из рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="1acee-104">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="1acee-105">Эти действия позволяют обращаться к базам данных для получения или изменения информации и использовать [ADO.NET](../../data/adonet/index.md) для доступа к базе данных.</span><span class="sxs-lookup"><span data-stu-id="1acee-105">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1acee-106">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="1acee-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1acee-107">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="1acee-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="1acee-108">Если этот каталог не существует, перейдите на страницу (страница загрузки), чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="1acee-108">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1acee-109">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="1acee-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="1acee-110">Действия базы данных</span><span class="sxs-lookup"><span data-stu-id="1acee-110">Database Activities</span></span>

<span data-ttu-id="1acee-111">В следующих разделах приведен список действий, входящих в этот образец.</span><span class="sxs-lookup"><span data-stu-id="1acee-111">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="1acee-112">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="1acee-112">DbUpdate</span></span>

<span data-ttu-id="1acee-113">Выполняет SQL-запрос, который реализует изменение в базе данных (вставку, обновление, удаление или иные изменения).</span><span class="sxs-lookup"><span data-stu-id="1acee-113">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

<span data-ttu-id="1acee-114">Этот класс выполняет работу асинхронно (он является производным от класса <xref:System.Activities.AsyncCodeActivity> и использует его возможности для асинхронной работы).</span><span class="sxs-lookup"><span data-stu-id="1acee-114">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="1acee-115">Чтобы настроить сведения о соединении, можно задать неизменяемое имя поставщика (`ProviderName`) и строку соединения (`ConnectionString`) или использовать имя конфигурации строки соединения (`ConfigFileSectionName`) из файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="1acee-115">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="1acee-116">Запрос для выполнения настраивается в свойстве `Sql`, а параметры передаются через коллекцию `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="1acee-116">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="1acee-117">После выполнения `DbUpdate` количество измененных записей возвращается в свойстве `AffectedRecords`.</span><span class="sxs-lookup"><span data-stu-id="1acee-117">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

```csharp
Public class DbUpdate: AsyncCodeActivity
{
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [DependsOn("Parameters")]
    public OutArgument<int> AffectedRecords { get; set; }
}
```

|<span data-ttu-id="1acee-118">Аргумент</span><span class="sxs-lookup"><span data-stu-id="1acee-118">Argument</span></span>|<span data-ttu-id="1acee-119">Описание</span><span class="sxs-lookup"><span data-stu-id="1acee-119">Description</span></span>|
|-|-|
|<span data-ttu-id="1acee-120">ProviderName</span><span class="sxs-lookup"><span data-stu-id="1acee-120">ProviderName</span></span>|<span data-ttu-id="1acee-121">Неизменяемое имя поставщика ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="1acee-121">ADO.NET provider invariant name.</span></span> <span data-ttu-id="1acee-122">Если этот аргумент задан, то необходимо задать и аргумент `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="1acee-122">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="1acee-123">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="1acee-123">ConnectionString</span></span>|<span data-ttu-id="1acee-124">Строка соединения для подключения к базе данных.</span><span class="sxs-lookup"><span data-stu-id="1acee-124">Connection string to connect to the database.</span></span> <span data-ttu-id="1acee-125">Если этот аргумент задан, то необходимо задать и аргумент `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="1acee-125">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="1acee-126">ConfigName</span><span class="sxs-lookup"><span data-stu-id="1acee-126">ConfigName</span></span>|<span data-ttu-id="1acee-127">Имя раздела файла конфигурации, в котором хранятся сведения о соединении.</span><span class="sxs-lookup"><span data-stu-id="1acee-127">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="1acee-128">Если этот аргумент задан, то аргументы `ProviderName` и `ConnectionString` не требуются.</span><span class="sxs-lookup"><span data-stu-id="1acee-128">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="1acee-129">CommandType</span><span class="sxs-lookup"><span data-stu-id="1acee-129">CommandType</span></span>|<span data-ttu-id="1acee-130">Тип выполняемой команды <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="1acee-130">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="1acee-131">SQL</span><span class="sxs-lookup"><span data-stu-id="1acee-131">Sql</span></span>|<span data-ttu-id="1acee-132">Команда SQL для выполнения.</span><span class="sxs-lookup"><span data-stu-id="1acee-132">The SQL command to be executed.</span></span>|
|<span data-ttu-id="1acee-133">Параметры</span><span class="sxs-lookup"><span data-stu-id="1acee-133">Parameters</span></span>|<span data-ttu-id="1acee-134">Коллекция параметров SQL-запроса.</span><span class="sxs-lookup"><span data-stu-id="1acee-134">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="1acee-135">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="1acee-135">AffectedRecords</span></span>|<span data-ttu-id="1acee-136">Количество записей, на которые повлияла последняя операция.</span><span class="sxs-lookup"><span data-stu-id="1acee-136">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="1acee-137">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="1acee-137">DbQueryScalar</span></span>

<span data-ttu-id="1acee-138">Выполняет запрос, возвращающий единичное значение данные из базы данных.</span><span class="sxs-lookup"><span data-stu-id="1acee-138">Executes a query that retrieves a single value from the database.</span></span>

<span data-ttu-id="1acee-139">Этот класс выполняет работу асинхронно (он является производным от класса <xref:System.Activities.AsyncCodeActivity%601> и использует его возможности для асинхронной работы).</span><span class="sxs-lookup"><span data-stu-id="1acee-139">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="1acee-140">Чтобы настроить сведения о соединении, можно задать неизменяемое имя поставщика (`ProviderName`) и строку соединения (`ConnectionString`) или использовать имя конфигурации строки соединения (`ConfigFileSectionName`) из файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="1acee-140">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="1acee-141">Запрос для выполнения настраивается в свойстве `Sql`, а параметры передаются через коллекцию `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="1acee-141">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="1acee-142">После `DbQueryScalar` выполнения, скаляр возвращается в `Result out` аргументе (типа `TResult` , который определен в базовом классе <xref:System.Activities.AsyncCodeActivity%601> ).</span><span class="sxs-lookup"><span data-stu-id="1acee-142">After `DbQueryScalar` is executed, the scalar is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```csharp
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="1acee-143">Аргумент</span><span class="sxs-lookup"><span data-stu-id="1acee-143">Argument</span></span>|<span data-ttu-id="1acee-144">Описание</span><span class="sxs-lookup"><span data-stu-id="1acee-144">Description</span></span>|
|-|-|
|<span data-ttu-id="1acee-145">ProviderName</span><span class="sxs-lookup"><span data-stu-id="1acee-145">ProviderName</span></span>|<span data-ttu-id="1acee-146">Неизменяемое имя поставщика ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="1acee-146">ADO.NET provider invariant name.</span></span> <span data-ttu-id="1acee-147">Если этот аргумент задан, то необходимо задать и аргумент `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="1acee-147">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="1acee-148">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="1acee-148">ConnectionString</span></span>|<span data-ttu-id="1acee-149">Строка соединения для подключения к базе данных.</span><span class="sxs-lookup"><span data-stu-id="1acee-149">Connection string to connect to the database.</span></span> <span data-ttu-id="1acee-150">Если этот аргумент задан, то необходимо задать и аргумент `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="1acee-150">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="1acee-151">ConfigName</span><span class="sxs-lookup"><span data-stu-id="1acee-151">ConfigName</span></span>|<span data-ttu-id="1acee-152">Имя раздела файла конфигурации, в котором хранятся сведения о соединении.</span><span class="sxs-lookup"><span data-stu-id="1acee-152">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="1acee-153">Если этот аргумент задан, то аргументы `ProviderName` и `ConnectionString` не требуются.</span><span class="sxs-lookup"><span data-stu-id="1acee-153">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="1acee-154">CommandType</span><span class="sxs-lookup"><span data-stu-id="1acee-154">CommandType</span></span>|<span data-ttu-id="1acee-155">Тип выполняемой команды <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="1acee-155">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="1acee-156">SQL</span><span class="sxs-lookup"><span data-stu-id="1acee-156">Sql</span></span>|<span data-ttu-id="1acee-157">Команда SQL для выполнения.</span><span class="sxs-lookup"><span data-stu-id="1acee-157">The SQL command to be executed.</span></span>|
|<span data-ttu-id="1acee-158">Параметры</span><span class="sxs-lookup"><span data-stu-id="1acee-158">Parameters</span></span>|<span data-ttu-id="1acee-159">Коллекция параметров SQL-запроса.</span><span class="sxs-lookup"><span data-stu-id="1acee-159">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="1acee-160">Результат</span><span class="sxs-lookup"><span data-stu-id="1acee-160">Result</span></span>|<span data-ttu-id="1acee-161">Скаляр, полученный после выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="1acee-161">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="1acee-162">Этот аргумент имеет тип `TResult`.</span><span class="sxs-lookup"><span data-stu-id="1acee-162">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="1acee-163">DbQuery</span><span class="sxs-lookup"><span data-stu-id="1acee-163">DbQuery</span></span>

<span data-ttu-id="1acee-164">Выполняет запрос, который возвращает список объектов.</span><span class="sxs-lookup"><span data-stu-id="1acee-164">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="1acee-165">После выполнения запроса выполняется функция сопоставления (она может быть <xref:System.Func%601> < `DbDataReader` , `TResult`> или <xref:System.Activities.ActivityFunc%601> < `DbDataReader` , `TResult`>).</span><span class="sxs-lookup"><span data-stu-id="1acee-165">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="1acee-166">Эта функция сопоставления получает запись в `DbDataReader` и сопоставляет ее возвращаемому объекту.</span><span class="sxs-lookup"><span data-stu-id="1acee-166">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

<span data-ttu-id="1acee-167">Чтобы настроить сведения о соединении, можно задать неизменяемое имя поставщика (`ProviderName`) и строку соединения (`ConnectionString`) или использовать имя конфигурации строки соединения (`ConfigFileSectionName`) из файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="1acee-167">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="1acee-168">Запрос для выполнения настраивается в свойстве `Sql`, а параметры передаются через коллекцию `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="1acee-168">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="1acee-169">Результаты SQL-запроса извлекаются с использованием `DbDataReader`.</span><span class="sxs-lookup"><span data-stu-id="1acee-169">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="1acee-170">Действие выполняет перебор по `DbDataReader` и сопоставляет строки в `DbDataReader` с экземпляром `TResult`.</span><span class="sxs-lookup"><span data-stu-id="1acee-170">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="1acee-171">Пользователь `DbQuery` должен предоставить код сопоставления, и это можно сделать двумя способами: с помощью <xref:System.Func%601> < `DbDataReader` , `TResult`> или <xref:System.Activities.ActivityFunc%601> < `DbDataReader` `TResult`>.</span><span class="sxs-lookup"><span data-stu-id="1acee-171">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="1acee-172">В первом случае сопоставление совершается на одном шаге выполнения.</span><span class="sxs-lookup"><span data-stu-id="1acee-172">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="1acee-173">Поэтому этот способ быстрее, но сериализация в XAML невозможна.</span><span class="sxs-lookup"><span data-stu-id="1acee-173">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="1acee-174">Во втором случае сопоставление выполняется в несколько шагов.</span><span class="sxs-lookup"><span data-stu-id="1acee-174">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="1acee-175">Поэтому может потребоваться больше времени, зато возможны сериализация в XAML и декларативное авторство (любое существующее действие может участвовать в сопоставлении).</span><span class="sxs-lookup"><span data-stu-id="1acee-175">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

```csharp
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [OverloadGroup("DirectMapping")]
    [DefaultValue(null)]
    public Func<DbDataReader, TResult> Mapper { get; set; }

    [OverloadGroup("MultiplePulseMapping")]
    [DefaultValue(null)]
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }
}
```

|<span data-ttu-id="1acee-176">Аргумент</span><span class="sxs-lookup"><span data-stu-id="1acee-176">Argument</span></span>|<span data-ttu-id="1acee-177">Описание</span><span class="sxs-lookup"><span data-stu-id="1acee-177">Description</span></span>|
|-|-|
|<span data-ttu-id="1acee-178">ProviderName</span><span class="sxs-lookup"><span data-stu-id="1acee-178">ProviderName</span></span>|<span data-ttu-id="1acee-179">Неизменяемое имя поставщика ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="1acee-179">ADO.NET provider invariant name.</span></span> <span data-ttu-id="1acee-180">Если этот аргумент задан, то необходимо задать и аргумент `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="1acee-180">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="1acee-181">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="1acee-181">ConnectionString</span></span>|<span data-ttu-id="1acee-182">Строка соединения для подключения к базе данных.</span><span class="sxs-lookup"><span data-stu-id="1acee-182">Connection string to connect to the database.</span></span> <span data-ttu-id="1acee-183">Если этот аргумент задан, то необходимо задать и аргумент `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="1acee-183">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="1acee-184">ConfigName</span><span class="sxs-lookup"><span data-stu-id="1acee-184">ConfigName</span></span>|<span data-ttu-id="1acee-185">Имя раздела файла конфигурации, в котором хранятся сведения о соединении.</span><span class="sxs-lookup"><span data-stu-id="1acee-185">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="1acee-186">Если этот аргумент задан, то аргументы `ProviderName` и `ConnectionString` не требуются.</span><span class="sxs-lookup"><span data-stu-id="1acee-186">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="1acee-187">CommandType</span><span class="sxs-lookup"><span data-stu-id="1acee-187">CommandType</span></span>|<span data-ttu-id="1acee-188">Тип выполняемой команды <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="1acee-188">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="1acee-189">SQL</span><span class="sxs-lookup"><span data-stu-id="1acee-189">Sql</span></span>|<span data-ttu-id="1acee-190">Команда SQL для выполнения.</span><span class="sxs-lookup"><span data-stu-id="1acee-190">The SQL command to be executed.</span></span>|
|<span data-ttu-id="1acee-191">Параметры</span><span class="sxs-lookup"><span data-stu-id="1acee-191">Parameters</span></span>|<span data-ttu-id="1acee-192">Коллекция параметров SQL-запроса.</span><span class="sxs-lookup"><span data-stu-id="1acee-192">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="1acee-193">Сопоставитель</span><span class="sxs-lookup"><span data-stu-id="1acee-193">Mapper</span></span>|<span data-ttu-id="1acee-194">Функция сопоставления ( <xref:System.Func%601> < `DbDataReader` , `TResult`>), которая принимает запись в `DataReader` полученном виде в результате выполнения запроса и возвращает экземпляр объекта типа `TResult` , добавляемого в `Result` коллекцию.</span><span class="sxs-lookup"><span data-stu-id="1acee-194">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="1acee-195">В этом случае сопоставление совершается на одном шаге выполнения, но декларативное авторство с использованием конструктора невозможно.</span><span class="sxs-lookup"><span data-stu-id="1acee-195">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="1acee-196">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="1acee-196">MapperFunc</span></span>|<span data-ttu-id="1acee-197">Функция сопоставления ( <xref:System.Activities.ActivityFunc%601> < `DbDataReader` , `TResult`>), которая принимает запись в `DataReader` полученном виде в результате выполнения запроса и возвращает экземпляр объекта типа `TResult` , добавляемого в `Result` коллекцию.</span><span class="sxs-lookup"><span data-stu-id="1acee-197">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="1acee-198">В этом случае сопоставление совершается в несколько шагов выполнения.</span><span class="sxs-lookup"><span data-stu-id="1acee-198">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="1acee-199">Для этой функции возможны сериализация в XAML и декларативное авторство (любое существующее действие может участвовать в сопоставлении).</span><span class="sxs-lookup"><span data-stu-id="1acee-199">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="1acee-200">Результат</span><span class="sxs-lookup"><span data-stu-id="1acee-200">Result</span></span>|<span data-ttu-id="1acee-201">Список объектов, полученный в результате выполнения запроса и выполнения функции сопоставления для каждой записи в `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="1acee-201">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="1acee-202">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="1acee-202">DbQueryDataSet</span></span>

<span data-ttu-id="1acee-203">Выполняет запрос, который возвращает <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="1acee-203">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="1acee-204">Этот класс выполняет работу асинхронно.</span><span class="sxs-lookup"><span data-stu-id="1acee-204">This class performs its work asynchronously.</span></span> <span data-ttu-id="1acee-205">Он является производным от <xref:System.Activities.AsyncCodeActivity> < `TResult`> и использует его асинхронные возможности.</span><span class="sxs-lookup"><span data-stu-id="1acee-205">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

<span data-ttu-id="1acee-206">Чтобы настроить сведения о соединении, можно задать неизменяемое имя поставщика (`ProviderName`) и строку соединения (`ConnectionString`) или использовать имя конфигурации строки соединения (`ConfigFileSectionName`) из файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="1acee-206">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="1acee-207">Запрос для выполнения настраивается в свойстве `Sql`, а параметры передаются через коллекцию `Parameters`.</span><span class="sxs-lookup"><span data-stu-id="1acee-207">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="1acee-208">После `DbQueryDataSet` выполнения объект `DataSet` возвращается в `Result out` аргументе (типа `TResult` , который определен в базовом классе <xref:System.Activities.AsyncCodeActivity%601> ).</span><span class="sxs-lookup"><span data-stu-id="1acee-208">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```csharp
public class DbQueryDataSet : AsyncCodeActivity<DataSet>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="1acee-209">Аргумент</span><span class="sxs-lookup"><span data-stu-id="1acee-209">Argument</span></span>|<span data-ttu-id="1acee-210">Описание</span><span class="sxs-lookup"><span data-stu-id="1acee-210">Description</span></span>|
|-|-|
|<span data-ttu-id="1acee-211">ProviderName</span><span class="sxs-lookup"><span data-stu-id="1acee-211">ProviderName</span></span>|<span data-ttu-id="1acee-212">Неизменяемое имя поставщика ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="1acee-212">ADO.NET provider invariant name.</span></span> <span data-ttu-id="1acee-213">Если этот аргумент задан, то необходимо задать и аргумент `ConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="1acee-213">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="1acee-214">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="1acee-214">ConnectionString</span></span>|<span data-ttu-id="1acee-215">Строка соединения для подключения к базе данных.</span><span class="sxs-lookup"><span data-stu-id="1acee-215">Connection string to connect to the database.</span></span> <span data-ttu-id="1acee-216">Если этот аргумент задан, то необходимо задать и аргумент `ProviderName`.</span><span class="sxs-lookup"><span data-stu-id="1acee-216">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="1acee-217">ConfigName</span><span class="sxs-lookup"><span data-stu-id="1acee-217">ConfigName</span></span>|<span data-ttu-id="1acee-218">Имя раздела файла конфигурации, в котором хранятся сведения о соединении.</span><span class="sxs-lookup"><span data-stu-id="1acee-218">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="1acee-219">Если этот аргумент задан, то аргументы `ProviderName` и `ConnectionString` не требуются.</span><span class="sxs-lookup"><span data-stu-id="1acee-219">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="1acee-220">CommandType</span><span class="sxs-lookup"><span data-stu-id="1acee-220">CommandType</span></span>|<span data-ttu-id="1acee-221">Тип выполняемой команды <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="1acee-221">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="1acee-222">SQL</span><span class="sxs-lookup"><span data-stu-id="1acee-222">Sql</span></span>|<span data-ttu-id="1acee-223">Команда SQL для выполнения.</span><span class="sxs-lookup"><span data-stu-id="1acee-223">The SQL command to be executed.</span></span>|
|<span data-ttu-id="1acee-224">Параметры</span><span class="sxs-lookup"><span data-stu-id="1acee-224">Parameters</span></span>|<span data-ttu-id="1acee-225">Коллекция параметров SQL-запроса.</span><span class="sxs-lookup"><span data-stu-id="1acee-225">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="1acee-226">Результат</span><span class="sxs-lookup"><span data-stu-id="1acee-226">Result</span></span>|<span data-ttu-id="1acee-227"><xref:System.Data.DataSet>, полученный после выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="1acee-227"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="1acee-228">Настройка сведений о соединении</span><span class="sxs-lookup"><span data-stu-id="1acee-228">Configuring Connection Information</span></span>

<span data-ttu-id="1acee-229">Все DbActivities используют одни и те же параметры конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1acee-229">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="1acee-230">Их можно настроить двумя способами.</span><span class="sxs-lookup"><span data-stu-id="1acee-230">They can be configured in two ways:</span></span>

- <span data-ttu-id="1acee-231">`ConnectionString + InvariantName`: Укажите неизменяемое имя поставщика ADO.NET и строку соединения.</span><span class="sxs-lookup"><span data-stu-id="1acee-231">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<DateTime>()
  {
      ProviderName = "System.Data.SqlClient",
      ConnectionString = @"Data Source=.\SQLExpress;
                            Initial Catalog=DbActivitiesSample;
                            Integrated Security=True",
      Sql = "SELECT GetDate()"
  };
  ```

- <span data-ttu-id="1acee-232">`ConfigName`: Укажите имя раздела конфигурации, в котором содержатся сведения о соединении.</span><span class="sxs-lookup"><span data-stu-id="1acee-232">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>

  ```xml
  <connectionStrings>
      <add name="DbActivitiesSample"
            providerName="System.Data.SqlClient"
            connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
    </connectionStrings>
  ```

- <span data-ttu-id="1acee-233">В действии:</span><span class="sxs-lookup"><span data-stu-id="1acee-233">In the activity:</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<int>()
  {
      ConfigName = "DbActivitiesSample",
      Sql = "SELECT COUNT(*) FROM Roles"
  };
  ```

## <a name="running-this-sample"></a><span data-ttu-id="1acee-234">Выполнение образца</span><span class="sxs-lookup"><span data-stu-id="1acee-234">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="1acee-235">Инструкции по установке</span><span class="sxs-lookup"><span data-stu-id="1acee-235">Setup instructions</span></span>

<span data-ttu-id="1acee-236">Этот образец использует базу данных.</span><span class="sxs-lookup"><span data-stu-id="1acee-236">This sample uses a database.</span></span> <span data-ttu-id="1acee-237">Вместе с образцом предоставляется скрипт установки и загрузки (Setup.cmd).</span><span class="sxs-lookup"><span data-stu-id="1acee-237">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="1acee-238">Этот файл необходимо выполнить из командной строки.</span><span class="sxs-lookup"><span data-stu-id="1acee-238">You must execute that file using the command prompt.</span></span>

<span data-ttu-id="1acee-239">Скрипт Setup.cmd вызывает файл скрипта CreateDb.sql, который содержит команды SQL и выполняет следующие операции.</span><span class="sxs-lookup"><span data-stu-id="1acee-239">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

- <span data-ttu-id="1acee-240">Создает базу данных под именем DbActivitiesSample.</span><span class="sxs-lookup"><span data-stu-id="1acee-240">Creates a database called DbActivitiesSample.</span></span>

- <span data-ttu-id="1acee-241">Создает таблицу Roles.</span><span class="sxs-lookup"><span data-stu-id="1acee-241">Creates the Roles table.</span></span>

- <span data-ttu-id="1acee-242">Создает таблицу Employees.</span><span class="sxs-lookup"><span data-stu-id="1acee-242">Creates Employees table.</span></span>

- <span data-ttu-id="1acee-243">Вставляет 3 записи в таблицу Roles.</span><span class="sxs-lookup"><span data-stu-id="1acee-243">Inserts three records into the Roles table.</span></span>

- <span data-ttu-id="1acee-244">Вставляет двенадцать записей в таблицу Employees.</span><span class="sxs-lookup"><span data-stu-id="1acee-244">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="1acee-245">Запуск команды Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="1acee-245">To run Setup.cmd</span></span>

1. <span data-ttu-id="1acee-246">Откройте командную строку.</span><span class="sxs-lookup"><span data-stu-id="1acee-246">Open a command prompt.</span></span>

2. <span data-ttu-id="1acee-247">Перейдите в папку образца DbActivities.</span><span class="sxs-lookup"><span data-stu-id="1acee-247">Go to the DbActivities sample folder.</span></span>

3. <span data-ttu-id="1acee-248">Введите "Setup. cmd" и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="1acee-248">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1acee-249">Скрипт Setup.cmd пытается установить образец базы данных на экземпляр SQLExpress на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="1acee-249">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="1acee-250">Если образец необходимо установить на другом экземпляре сервера SQL, измените Setup.cmd, указав другое имя экземпляра.</span><span class="sxs-lookup"><span data-stu-id="1acee-250">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="1acee-251">Удаление образца базы данных</span><span class="sxs-lookup"><span data-stu-id="1acee-251">To uninstall the sample database</span></span>

1. <span data-ttu-id="1acee-252">Выполните в командной строке файл Cleanup.cmd из папки образца.</span><span class="sxs-lookup"><span data-stu-id="1acee-252">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="1acee-253">Выполнение образца</span><span class="sxs-lookup"><span data-stu-id="1acee-253">To run the sample</span></span>

1. <span data-ttu-id="1acee-254">Открытие решения в Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="1acee-254">Open the solution in Visual Studio 2010</span></span>

2. <span data-ttu-id="1acee-255">Для компиляции решения нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="1acee-255">To compile the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="1acee-256">Чтобы запустить образец без отладки, нажмите сочетание клавиш CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="1acee-256">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1acee-257">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="1acee-257">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1acee-258">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="1acee-258">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="1acee-259">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="1acee-259">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1acee-260">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="1acee-260">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
