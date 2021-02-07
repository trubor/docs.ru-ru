---
description: 'Дополнительные сведения: типичные шаги для использования LINQ to SQL'
title: Стандартная последовательность действий при использовании LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: eb35b983471db8926646418352b01e1186e235e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680971"
---
# <a name="typical-steps-for-using-linq-to-sql"></a><span data-ttu-id="78a54-103">Стандартная последовательность действий при использовании LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="78a54-103">Typical Steps for Using LINQ to SQL</span></span>

<span data-ttu-id="78a54-104">Чтобы реализовать приложение [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], выполните действия, описанные в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="78a54-104">To implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application, you follow the steps described later in this topic.</span></span> <span data-ttu-id="78a54-105">Обратите внимание, что многие их этих действий являются необязательными.</span><span class="sxs-lookup"><span data-stu-id="78a54-105">Note that many steps are optional.</span></span> <span data-ttu-id="78a54-106">В большинстве случаев можно использовать объектную модель в состоянии, установленном по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="78a54-106">It is very possible that you can use your object model in its default state.</span></span>  
  
 <span data-ttu-id="78a54-107">Для действительно быстрого запуска используйте реляционный конструктор объектов, чтобы создать объектную модель и начать кодирование запросов.</span><span class="sxs-lookup"><span data-stu-id="78a54-107">For a really fast start, use the Object Relational Designer to create your object model and start coding your queries.</span></span>  
  
## <a name="creating-the-object-model"></a><span data-ttu-id="78a54-108">Создание модели объектов</span><span class="sxs-lookup"><span data-stu-id="78a54-108">Creating the Object Model</span></span>  

 <span data-ttu-id="78a54-109">Первый шаг состоит в создании модели объектов на основе метаданных существующей реляционной базы данных.</span><span class="sxs-lookup"><span data-stu-id="78a54-109">The first step is to create an object model from the metadata of an existing relational database.</span></span> <span data-ttu-id="78a54-110">Объектная модель представляет базу данных в соответствии с языком программирования, выбранным разработчиком.</span><span class="sxs-lookup"><span data-stu-id="78a54-110">The object model represents the database according to the programming language of the developer.</span></span> <span data-ttu-id="78a54-111">Дополнительные сведения см. [в разделе Объектная модель LINQ to SQL](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="78a54-111">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
### <a name="1-select-a-tool-to-create-the-model"></a><span data-ttu-id="78a54-112">1. Выберите инструмент, чтобы создать модель.</span><span class="sxs-lookup"><span data-stu-id="78a54-112">1. Select a tool to create the model.</span></span>  

 <span data-ttu-id="78a54-113">Для создания модели предусмотрено три средства.</span><span class="sxs-lookup"><span data-stu-id="78a54-113">Three tools are available for creating the model.</span></span>  
  
- <span data-ttu-id="78a54-114">реляционный конструктор объектов</span><span class="sxs-lookup"><span data-stu-id="78a54-114">The Object Relational Designer</span></span>  
  
     <span data-ttu-id="78a54-115">Этот конструктор предоставляет многофункциональный пользовательский интерфейс для создания объектной модели из существующей базы данных.</span><span class="sxs-lookup"><span data-stu-id="78a54-115">This designer provides a rich user interface for creating an object model from an existing database.</span></span> <span data-ttu-id="78a54-116">Это средство является частью интегрированной среды разработки Visual Studio и лучше всего подходит для небольших или средних баз данных.</span><span class="sxs-lookup"><span data-stu-id="78a54-116">This tool is part of the Visual Studio IDE, and is best suited to small or medium databases.</span></span>  
  
- <span data-ttu-id="78a54-117">Средство создания кода SQLMetal</span><span class="sxs-lookup"><span data-stu-id="78a54-117">The SQLMetal code-generation tool</span></span>  
  
     <span data-ttu-id="78a54-118">Эта служебная программа командной строки немного отличается от набора параметров конструктора O/R.</span><span class="sxs-lookup"><span data-stu-id="78a54-118">This command-line utility provides a slightly different set of options from the O/R Designer.</span></span> <span data-ttu-id="78a54-119">Данное средство лучше всего подходит для моделирования больших баз данных.</span><span class="sxs-lookup"><span data-stu-id="78a54-119">Modeling large databases is best done by using this tool.</span></span> <span data-ttu-id="78a54-120">Дополнительные сведения см. в разделе [SQLMetal.exe (средство создания кода)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="78a54-120">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
- <span data-ttu-id="78a54-121">Редактор кода</span><span class="sxs-lookup"><span data-stu-id="78a54-121">A code editor</span></span>  
  
     <span data-ttu-id="78a54-122">Вы можете написать собственный код с помощью редактора кода Visual Studio или другого редактора.</span><span class="sxs-lookup"><span data-stu-id="78a54-122">You can write your own code by using either the Visual Studio code editor or another editor.</span></span> <span data-ttu-id="78a54-123">Не рекомендуется применять этот подход, который может быть подвержен ошибкам, если имеется база данных и может использовать конструктор O/R или средство SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="78a54-123">We do not recommend this approach, which can be prone to errors, when you have an existing database and can use either the O/R Designer or the SQLMetal tool.</span></span> <span data-ttu-id="78a54-124">Однако редактор кода становится ценным инструментом, когда требуется уточнить или изменить код, уже созданный с помощью других средств.</span><span class="sxs-lookup"><span data-stu-id="78a54-124">However, the code editor can be valuable for refining or modifying code you have already generated by using other tools.</span></span> <span data-ttu-id="78a54-125">Дополнительные сведения см. в разделе [инструкции. Настройка классов сущностей с помощью редактора кода](how-to-customize-entity-classes-by-using-the-code-editor.md).</span><span class="sxs-lookup"><span data-stu-id="78a54-125">For more information, see [How to: Customize Entity Classes by Using the Code Editor](how-to-customize-entity-classes-by-using-the-code-editor.md).</span></span>  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a><span data-ttu-id="78a54-126">2. Выберите тип кода, который необходимо создать.</span><span class="sxs-lookup"><span data-stu-id="78a54-126">2. Select the kind of code you want to generate.</span></span>  
  
- <span data-ttu-id="78a54-127">Файл исходного кода C# или Visual Basic для сопоставления на основе атрибутов.</span><span class="sxs-lookup"><span data-stu-id="78a54-127">A C# or Visual Basic source code file for attribute-based mapping.</span></span>  
  
     <span data-ttu-id="78a54-128">Затем вы включите этот файл кода в проект Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78a54-128">You then include this code file in your Visual Studio project.</span></span> <span data-ttu-id="78a54-129">Дополнительные сведения см. в разделе [сопоставление на основе атрибутов](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="78a54-129">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="78a54-130">XML-файл для внешнего сопоставления.</span><span class="sxs-lookup"><span data-stu-id="78a54-130">An XML file for external mapping.</span></span>  
  
     <span data-ttu-id="78a54-131">С помощью этого метода метаданные для сопоставления можно хранить на пределами кода приложения.</span><span class="sxs-lookup"><span data-stu-id="78a54-131">By using this approach, you can keep the mapping metadata out of your application code.</span></span> <span data-ttu-id="78a54-132">Дополнительные сведения см. в разделе [внешнее сопоставление](external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="78a54-132">For more information, see [External Mapping](external-mapping.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="78a54-133">Конструктор O/R не поддерживает создание файлов внешнего сопоставления.</span><span class="sxs-lookup"><span data-stu-id="78a54-133">The O/R Designer does not support the generation of external mapping files.</span></span> <span data-ttu-id="78a54-134">Для реализации этой возможности необходимо использовать программу SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="78a54-134">You must use the SQLMetal tool to implement this feature.</span></span>  
  
- <span data-ttu-id="78a54-135">Файл DBML, который можно изменить перед созданием окончательного файла с исходным кодом.</span><span class="sxs-lookup"><span data-stu-id="78a54-135">A DBML file, which you can modify before generating a final code file.</span></span>  
  
     <span data-ttu-id="78a54-136">Данная возможность является дополнительной.</span><span class="sxs-lookup"><span data-stu-id="78a54-136">This is an advanced feature.</span></span>  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a><span data-ttu-id="78a54-137">3. Уточните файл кода в соответствии с потребностями приложения.</span><span class="sxs-lookup"><span data-stu-id="78a54-137">3. Refine the code file to reflect the needs of your application.</span></span>  

 <span data-ttu-id="78a54-138">Для этой цели можно использовать конструктор O/R или редактор кода.</span><span class="sxs-lookup"><span data-stu-id="78a54-138">For this purpose, you can use either the O/R Designer or the code editor.</span></span>  
  
## <a name="using-the-object-model"></a><span data-ttu-id="78a54-139">Использование модели объектов</span><span class="sxs-lookup"><span data-stu-id="78a54-139">Using the Object Model</span></span>  

 <span data-ttu-id="78a54-140">На следующем рисунке показана связь между разработчиком и данными в двухуровневом сценарии.</span><span class="sxs-lookup"><span data-stu-id="78a54-140">The following illustration shows the relationship between the developer and the data in a two-tier scenario.</span></span> <span data-ttu-id="78a54-141">Сведения о других сценариях см. [в разделе N-Tiered and Remote Applications with LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="78a54-141">For other scenarios, see [N-Tier and Remote Applications with LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md).</span></span>  
  
 ![Снимок экрана, на котором показана объектная модель LINQ.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 <span data-ttu-id="78a54-143">После создания объектной модели описание запросов на получение сведений и управление данными осуществляется в рамках этой модели.</span><span class="sxs-lookup"><span data-stu-id="78a54-143">Now that you have the object model, you describe information requests and manipulate data within that model.</span></span> <span data-ttu-id="78a54-144">Все операции выполняются в терминах объектов и свойство объектной модели, а не в терминах строк и столбцов базы данных.</span><span class="sxs-lookup"><span data-stu-id="78a54-144">You think in terms of the objects and properties in your object model and not in terms of the rows and columns of the database.</span></span> <span data-ttu-id="78a54-145">Работа непосредственно с базой данных не осуществляется.</span><span class="sxs-lookup"><span data-stu-id="78a54-145">You do not deal directly with the database.</span></span>  
  
 <span data-ttu-id="78a54-146">Когда вы указываете, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] как выполнить запрос, который вы описывали, или вызвать `SubmitChanges()` для данных, которыми вы управляете, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] взаимодействует с базой данных на языке базы данных.</span><span class="sxs-lookup"><span data-stu-id="78a54-146">When you instruct [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to either execute a query that you have described or call `SubmitChanges()` on data that you have manipulated, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] communicates with the database in the language of the database.</span></span>  
  
 <span data-ttu-id="78a54-147">Ниже представлены типичные действия, выполняемые при использовании созданной объектной модели.</span><span class="sxs-lookup"><span data-stu-id="78a54-147">The following represents typical steps for using the object model that you have created.</span></span>  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a><span data-ttu-id="78a54-148">1. Создание запросов для получения сведений из базы данных.</span><span class="sxs-lookup"><span data-stu-id="78a54-148">1. Create queries to retrieve information from the database.</span></span>  

 <span data-ttu-id="78a54-149">Дополнительные сведения см. в разделе [Основные понятия запросов](query-concepts.md) и [примеры запросов](query-examples.md).</span><span class="sxs-lookup"><span data-stu-id="78a54-149">For more information, see [Query Concepts](query-concepts.md) and [Query Examples](query-examples.md).</span></span>  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a><span data-ttu-id="78a54-150">2. Переопределите поведение по умолчанию для операций вставки, обновления и удаления.</span><span class="sxs-lookup"><span data-stu-id="78a54-150">2. Override default behaviors for Insert, Update, and Delete.</span></span>  

 <span data-ttu-id="78a54-151">Это необязательный шаг.</span><span class="sxs-lookup"><span data-stu-id="78a54-151">This step is optional.</span></span> <span data-ttu-id="78a54-152">Дополнительные сведения см. в разделе [Настройка операций вставки, обновления и удаления](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="78a54-152">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a><span data-ttu-id="78a54-153">3. Задайте соответствующие параметры для обнаружения конфликтов параллелизма и отчетов.</span><span class="sxs-lookup"><span data-stu-id="78a54-153">3. Set appropriate options to detect and report concurrency conflicts.</span></span>  

 <span data-ttu-id="78a54-154">Можно использовать параметры обработки конфликтов параллелизма, установленные в модели по умолчанию, или изменить их в соответствии с текущими потребностями.</span><span class="sxs-lookup"><span data-stu-id="78a54-154">You can leave your model with its default values for handling concurrency conflicts, or you can change it to suit your purposes.</span></span> <span data-ttu-id="78a54-155">Дополнительные сведения см. [в разделе как указать элементы, проверяемые на наличие конфликтов параллелизма](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) , и [как указать, когда создаются исключения параллелизма](how-to-specify-when-concurrency-exceptions-are-thrown.md).</span><span class="sxs-lookup"><span data-stu-id="78a54-155">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) and [How to: Specify When Concurrency Exceptions are Thrown](how-to-specify-when-concurrency-exceptions-are-thrown.md).</span></span>  
  
### <a name="4-establish-an-inheritance-hierarchy"></a><span data-ttu-id="78a54-156">4. Установите иерархию наследования.</span><span class="sxs-lookup"><span data-stu-id="78a54-156">4. Establish an inheritance hierarchy.</span></span>  

 <span data-ttu-id="78a54-157">Это необязательный шаг.</span><span class="sxs-lookup"><span data-stu-id="78a54-157">This step is optional.</span></span> <span data-ttu-id="78a54-158">Дополнительные сведения см. в разделе [Поддержка наследования](inheritance-support.md).</span><span class="sxs-lookup"><span data-stu-id="78a54-158">For more information, see [Inheritance Support](inheritance-support.md).</span></span>  
  
### <a name="5-provide-an-appropriate-user-interface"></a><span data-ttu-id="78a54-159">5. Укажите соответствующий пользовательский интерфейс.</span><span class="sxs-lookup"><span data-stu-id="78a54-159">5. Provide an appropriate user interface.</span></span>  

 <span data-ttu-id="78a54-160">Этот шаг необязателен. Его выполнение зависит от способа использования приложения.</span><span class="sxs-lookup"><span data-stu-id="78a54-160">This step is optional, and depends on how your application will be used.</span></span>  
  
### <a name="6-debug-and-test-your-application"></a><span data-ttu-id="78a54-161">6. Отладка и тестирование приложения.</span><span class="sxs-lookup"><span data-stu-id="78a54-161">6. Debug and test your application.</span></span>  

 <span data-ttu-id="78a54-162">Дополнительные сведения см. в разделе [Поддержка отладки](debugging-support.md).</span><span class="sxs-lookup"><span data-stu-id="78a54-162">For more information, see [Debugging Support](debugging-support.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78a54-163">См. также</span><span class="sxs-lookup"><span data-stu-id="78a54-163">See also</span></span>

- [<span data-ttu-id="78a54-164">Начало работы</span><span class="sxs-lookup"><span data-stu-id="78a54-164">Getting Started</span></span>](getting-started.md)
- [<span data-ttu-id="78a54-165">Создание модели объектов</span><span class="sxs-lookup"><span data-stu-id="78a54-165">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="78a54-166">Хранимые процедуры</span><span class="sxs-lookup"><span data-stu-id="78a54-166">Stored Procedures</span></span>](stored-procedures.md)
