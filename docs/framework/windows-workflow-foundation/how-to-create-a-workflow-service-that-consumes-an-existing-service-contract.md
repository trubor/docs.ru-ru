---
description: Дополнительные сведения о том, как создать службу рабочего процесса, которая использует существующий контракт службы.
title: Практическое руководство. Создание службы рабочих процессов, использующей существующий контракт службы
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 0a31f0f4e205c72b857b59726437e896a7c68231
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631259"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="f1d7b-103">Практическое руководство. Создание службы рабочих процессов, использующей существующий контракт службы</span><span class="sxs-lookup"><span data-stu-id="f1d7b-103">How to: Create a workflow service that consumes an existing service contract</span></span>

<span data-ttu-id="f1d7b-104">Платформа .NET Framework 4,5 обеспечивает лучшую интеграцию между веб-службами и рабочими процессами в виде разработки рабочих процессов с помощью контрактов.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-104">.NET Framework 4.5 features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="f1d7b-105">Средство разработки рабочих процессов на основе контракта позволяет создать контракт в Code First.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-105">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="f1d7b-106">Затем это средство автоматически создает в области элементов шаблон действия для каждой операции в контракте.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-106">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1d7b-107">Этот раздел содержит пошаговые инструкции по созданию службы рабочих процессов на основе контракта.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-107">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="f1d7b-108">Дополнительные сведения о разработке службы рабочих процессов в первую очередь см. в разделе [разработка первой службы рабочих процессов](contract-first-workflow-service-development.md)на основе контрактов.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-108">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="f1d7b-109">Создание проекта рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="f1d7b-109">Creating the workflow project</span></span>  
  
1. <span data-ttu-id="f1d7b-110">В Visual Studio выберите последовательно **Файл** и **Создать проект**.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-110">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="f1d7b-111">Выберите узел **WCF** в узле **C#** в дереве **шаблонов** и выберите шаблон **приложение службы рабочего процесса WCF** .</span><span class="sxs-lookup"><span data-stu-id="f1d7b-111">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2. <span data-ttu-id="f1d7b-112">Присвойте новому проекту имя `ContractFirst` и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-112">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="f1d7b-113">Создание контракта службы</span><span class="sxs-lookup"><span data-stu-id="f1d7b-113">Creating the service contract</span></span>  
  
1. <span data-ttu-id="f1d7b-114">Щелкните правой кнопкой мыши проект в **Обозреватель решений** и выберите **Добавить**, **новый элемент...**.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-114">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="f1d7b-115">Выберите узел **кода** слева и шаблон **класса** справа.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-115">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="f1d7b-116">Присвойте новому классу имя `IBookService` и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-116">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2. <span data-ttu-id="f1d7b-117">В верхней части появившегося окна кода добавьте в `System.Servicemodel` инструкцию Using.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-117">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    ```  
  
3. <span data-ttu-id="f1d7b-118">Измените образец определения класса на следующее определение интерфейса.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-118">Change the sample class definition to the following interface definition.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. <span data-ttu-id="f1d7b-119">Постройте проект, нажав клавиши **CTRL + SHIFT + B**.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-119">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="f1d7b-120">Импорт контракта службы</span><span class="sxs-lookup"><span data-stu-id="f1d7b-120">Importing the service contract</span></span>  
  
1. <span data-ttu-id="f1d7b-121">Щелкните правой кнопкой мыши проект в **Обозреватель решений** и выберите пункт **Импорт контракта службы**.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-121">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="f1d7b-122">В разделе **\<Current Project>** откройте все подузлы и выберите **ибуксервице**.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-122">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="f1d7b-123">Нажмите кнопку **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-123">Click **OK**.</span></span>  
  
2. <span data-ttu-id="f1d7b-124">Откроется диалоговое окно с сообщением, что операция была завершена успешно, а созданные действия появятся в области элементов после сборки проекта.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-124">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="f1d7b-125">Нажмите кнопку **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-125">Click **OK**.</span></span>  
  
3. <span data-ttu-id="f1d7b-126">Постройте проект, нажав клавиши **CTRL + SHIFT + B**, чтобы импортированные действия отображались на панели элементов.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-126">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4. <span data-ttu-id="f1d7b-127">В **Обозреватель решений** откройте Service1. xamlx.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-127">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="f1d7b-128">Служба рабочего процесса появится в конструкторе.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-128">The workflow service will appear in the designer.</span></span>  
  
5. <span data-ttu-id="f1d7b-129">Выберите действие **последовательности** .</span><span class="sxs-lookup"><span data-stu-id="f1d7b-129">Select the **Sequence** activity.</span></span> <span data-ttu-id="f1d7b-130">В окно свойств щелкните **...**</span><span class="sxs-lookup"><span data-stu-id="f1d7b-130">In the Properties window, click the **…**</span></span> <span data-ttu-id="f1d7b-131">в свойстве **имплементедконтракт** .</span><span class="sxs-lookup"><span data-stu-id="f1d7b-131">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="f1d7b-132">В открывшемся окне **Редактор коллекции типов** щелкните раскрывающийся список **Тип** и выберите пункт **Обзор для типов...**</span><span class="sxs-lookup"><span data-stu-id="f1d7b-132">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="f1d7b-133">.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-133">entry.</span></span> <span data-ttu-id="f1d7b-134">В диалоговом окне **Обзор и выбор типа .NET** в разделе **\<Current Project>** откройте все подузлы и выберите **ибуксервице**.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-134">In the **Browse and Select a .NET Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="f1d7b-135">Нажмите кнопку **OK**.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-135">Click **OK**.</span></span> <span data-ttu-id="f1d7b-136">В диалоговом окне **Редактор коллекции типов** нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="f1d7b-136">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6. <span data-ttu-id="f1d7b-137">Выберите и удалите действия **действия ReceiveRequest** и **SendResponse** .</span><span class="sxs-lookup"><span data-stu-id="f1d7b-137">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7. <span data-ttu-id="f1d7b-138">Из панели элементов перетащите **Buy_ReceiveAndSendReply** и **Checkout_Receive** действие в действие **Последовательная служба** .</span><span class="sxs-lookup"><span data-stu-id="f1d7b-138">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
