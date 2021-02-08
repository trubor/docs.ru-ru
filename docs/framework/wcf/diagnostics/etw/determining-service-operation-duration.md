---
description: 'Дополнительные сведения: Определение длительности операции службы'
title: Определение продолжительности выполнения для операции службы
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: e9dd9ee4113ee4b4521afb6dfaf6a913e72ea5d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798814"
---
# <a name="determining-service-operation-duration"></a><span data-ttu-id="f5e57-103">Определение продолжительности выполнения для операции службы</span><span class="sxs-lookup"><span data-stu-id="f5e57-103">Determining service operation duration</span></span>

<span data-ttu-id="f5e57-104">Если аналитическая трассировка включена в приложении Windows Communication Foundation (WCF), длительность выполнения операции службы может быть легко определена с помощью проверки журнала событий.</span><span class="sxs-lookup"><span data-stu-id="f5e57-104">If analytic tracing is enabled in a Windows Communication Foundation (WCF) application, the duration of execution for a service operation can easily be determined by examining the event log.</span></span>  <span data-ttu-id="f5e57-105">В этом разделе показано, как определить время, затраченное на выполнение операции службы.</span><span class="sxs-lookup"><span data-stu-id="f5e57-105">This topic demonstrates how to determine the amount of time a service operation takes to complete.</span></span>  
  
### <a name="determining-service-operation-execution-duration"></a><span data-ttu-id="f5e57-106">Определение продолжительности выполнения для операции службы</span><span class="sxs-lookup"><span data-stu-id="f5e57-106">Determining service operation execution duration</span></span>  
  
1. <span data-ttu-id="f5e57-107">Откройте Просмотр событий, нажав кнопку **Пуск**, **выполните** и введите `eventvwr.exe` .</span><span class="sxs-lookup"><span data-stu-id="f5e57-107">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2. <span data-ttu-id="f5e57-108">Если вы не включили аналитическую трассировку, разверните узел **журналы приложений и служб**, **Microsoft**, **Windows**, **сервер приложений — приложения**.</span><span class="sxs-lookup"><span data-stu-id="f5e57-108">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="f5e57-109">Выберите **вид**, **Показать журналы аналитики и отладки**.</span><span class="sxs-lookup"><span data-stu-id="f5e57-109">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="f5e57-110">Щелкните правой кнопкой мыши **аналитика** и выберите **Включить журнал**.</span><span class="sxs-lookup"><span data-stu-id="f5e57-110">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="f5e57-111">Оставьте окно просмотра событий открытым, чтобы можно было просмотреть трассировки после выполнения операции службы.</span><span class="sxs-lookup"><span data-stu-id="f5e57-111">Leave Event Viewer open so that traces can be viewed after the service operation is run.</span></span>  
  
3. <span data-ttu-id="f5e57-112">Затем откройте приложение WCF, которое включает проект службы и клиентский проект, взаимодействующий с этой службой.</span><span class="sxs-lookup"><span data-stu-id="f5e57-112">Next, open a WCF application that includes a service project and a client project that interacts with that service.</span></span>  <span data-ttu-id="f5e57-113">Такое приложение можно создать, следуя [Начало работы руководстве](../../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f5e57-113">You can create such an application by following the [Getting Started Tutorial](../../getting-started-tutorial.md).</span></span>  <span data-ttu-id="f5e57-114">Если установлены образцы WCF, можно открыть [Начало работы](../../samples/getting-started-sample.md), содержащий завершенный проект, созданный в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="f5e57-114">If you have the WCF samples installed, you can open the [Getting Started](../../samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4. <span data-ttu-id="f5e57-115">Выполните серверное приложение, нажав клавишу **F5**.</span><span class="sxs-lookup"><span data-stu-id="f5e57-115">Execute the server application by pressing **F5**.</span></span> <span data-ttu-id="f5e57-116">Выполните клиентское приложение, щелкнув правой кнопкой мыши **клиентский** проект и выбрав **Отладка**, **запустить новый экземпляр**.</span><span class="sxs-lookup"><span data-stu-id="f5e57-116">Execute the client application by right-clicking on the **Client** project and selecting **Debug**, **Start New Instance**.</span></span>  
  
5. <span data-ttu-id="f5e57-117">В окне просмотра событий обновите аналитический журнал и отсортируйте события по идентификатору события.</span><span class="sxs-lookup"><span data-stu-id="f5e57-117">In Event Viewer, refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="f5e57-118">Найдите события с ИД события [214-оператионкомплетед](214-operationcompleted.md).</span><span class="sxs-lookup"><span data-stu-id="f5e57-118">Look for events with Event ID [214 - OperationCompleted](214-operationcompleted.md).</span></span>  <span data-ttu-id="f5e57-119">В этих событиях показано, какие операции выполнены, и указана продолжительность операции.</span><span class="sxs-lookup"><span data-stu-id="f5e57-119">These events will show which operations have completed, and what the duration of the operation was.</span></span>  <span data-ttu-id="f5e57-120">В следующем событии показана продолжительность операции Add.</span><span class="sxs-lookup"><span data-stu-id="f5e57-120">The following event shows the duration of an Add operation.</span></span>  
  
    ```output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
