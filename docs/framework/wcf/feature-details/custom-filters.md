---
description: 'Дополнительные сведения: настраиваемые фильтры'
title: Настраиваемые фильтры
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: 95a419823cf69575f951c0984e2136f9e7afca56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704983"
---
# <a name="custom-filters"></a><span data-ttu-id="ec3ed-103">Настраиваемые фильтры</span><span class="sxs-lookup"><span data-stu-id="ec3ed-103">Custom Filters</span></span>

<span data-ttu-id="ec3ed-104">Пользовательские фильтры позволяют определять логику сопоставления, которую невозможно определить с помощью фильтров системных сообщений.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-104">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="ec3ed-105">Например, можно создать пользовательский фильтр, который хэширует определенный элемент сообщений, а затем выполняет проверку значения, чтобы определить значение, которое возвращается фильтром (true или false).</span><span class="sxs-lookup"><span data-stu-id="ec3ed-105">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="ec3ed-106">Реализация</span><span class="sxs-lookup"><span data-stu-id="ec3ed-106">Implementation</span></span>  

 <span data-ttu-id="ec3ed-107">Пользовательский фильтр является реализацией абстрактного базового класса <xref:System.ServiceModel.Dispatcher.MessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-107">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="ec3ed-108">При реализации пользовательского фильтра конструктор может, если необходимо, принять один строковый параметр.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-108">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="ec3ed-109">Этот параметр содержит данные о конфигурации, которые передаются конструктору MessageFilter для предоставления значений и настроек, необходимых фильтру во время выполнения для сопоставления.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-109">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="ec3ed-110">Например, их можно использовать, чтобы указать значение, поиск которого в оцениваемом сообщении выполняет фильтр.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-110">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="ec3ed-111">В следующем примере показана базовая реализация настраиваемого фильтра сообщений, принимающего строковый параметр:</span><span class="sxs-lookup"><span data-stu-id="ec3ed-111">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
```csharp  
public class MyMessageFilter: MessageFilter  
{  
    string filterData;  
    public MyMessageFilter(string filterData)  
    {  
        if(string.IsNullOrEmpty(filterData)  
            throw new ArgumentNullException("filterData");  
        this.filterData=filterData;  
    }  
    public override bool Match(System.ServiceModel.Channels.Message message)  
    {  
        ...  
        return retValue;  
    }  
    public override bool Match(System.ServiceModel.Channels.MessageBuffer buffer)  
    {  
        ...  
        return retValue;  
    }  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="ec3ed-112">В реальной реализации метод Match содержит логику, которая проверит сообщение, чтобы определить, должен ли этот фильтр сообщений возвращать **значение true** или **false**.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-112">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="ec3ed-113">Производительность</span><span class="sxs-lookup"><span data-stu-id="ec3ed-113">Performance</span></span>  

 <span data-ttu-id="ec3ed-114">Реализуя пользовательский фильтр, важно принять во внимание максимальное время, которое может потребоваться фильтру для завершения обработки сообщения.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-114">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="ec3ed-115">Поскольку сообщение может обрабатываться несколькими фильтрами перед тем, как будет найдено совпадение, важно убедиться, что время ожидания клиентского запроса не завершится раньше, чем сообщение смогут обработать все фильтры.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-115">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="ec3ed-116">Вследствие этого пользовательский фильтр должен содержать только код, необходимый для обработки содержимого или атрибутов сообщения, чтобы определить его соответствие условиям фильтра.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-116">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="ec3ed-117">В целом, при реализации пользовательского фильтра следует избегать следующих действий.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-117">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
- <span data-ttu-id="ec3ed-118">Ввод-вывод, например сохранение данных на диск или в базу данных.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-118">IO, such as saving data to disk or to a database.</span></span>  
  
- <span data-ttu-id="ec3ed-119">Ненужная обработка, например циклический проход по многочисленным записям в документе.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-119">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
- <span data-ttu-id="ec3ed-120">Блокировка операций, например вызовы, которые предусматривают блокировку совместно используемых ресурсов или поиск по базе данных.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-120">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="ec3ed-121">Перед использованием пользовательского фильтра в рабочей среде следует провести тесты производительности для определения средней продолжительности времени, в течение которого фильтр обрабатывает сообщение.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-121">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="ec3ed-122">В сумме со средним временем обработки для других фильтров, используемых в таблице фильтров, это позволит достаточно точно определить максимальное значение времени ожидания, которое необходимо задать в клиентском приложении.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-122">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="ec3ed-123">Использование</span><span class="sxs-lookup"><span data-stu-id="ec3ed-123">Usage</span></span>  

 <span data-ttu-id="ec3ed-124">Чтобы использовать настраиваемый фильтр со службой маршрутизации, необходимо добавить его в таблицу фильтров, указав новую запись фильтра типа "Пользовательская", полное имя типа фильтра сообщений и имя сборки.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-124">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="ec3ed-125">Как и в случае с другими фильтрами MessageFilters, можно указать строковые данные filterData, передаваемые конструктору пользовательского фильтра.</span><span class="sxs-lookup"><span data-stu-id="ec3ed-125">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="ec3ed-126">В следующем примере показывается использование пользовательского фильтра при работе со службой маршрутизации:</span><span class="sxs-lookup"><span data-stu-id="ec3ed-126">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="CustomFilter1" filterType="Custom"
            customType="CustomAssembly.MyMessageFilter,
            CustomAssembly" filterData="custom data" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="CustomFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
RoutingConfiguration rc = new RoutingConfiguration();  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
rc.FilterTable.Add(new MyMessageFilter("CustomData"), endpointList);  
```
