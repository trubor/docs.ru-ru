---
description: 'Дополнительные сведения: объект My. WebService'
title: Объект My.WebServices
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: e8d7ef8b349fef6d69b92d9df4a23222bd3c912e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640541"
---
# <a name="mywebservices-object"></a><span data-ttu-id="7797d-103">Объект My.WebServices</span><span class="sxs-lookup"><span data-stu-id="7797d-103">My.WebServices Object</span></span>

<span data-ttu-id="7797d-104">Предоставляет свойства для создания и доступа к одному экземпляру каждой веб-службы XML, на которую ссылается текущий проект.</span><span class="sxs-lookup"><span data-stu-id="7797d-104">Provides properties for creating and accessing a single instance of each XML Web service referenced by the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7797d-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="7797d-105">Remarks</span></span>  

 <span data-ttu-id="7797d-106">Объект `My.WebServices` предоставляет экземпляр каждой веб-службы, на которую ссылается текущий проект.</span><span class="sxs-lookup"><span data-stu-id="7797d-106">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="7797d-107">Каждый экземпляр создается по запросу.</span><span class="sxs-lookup"><span data-stu-id="7797d-107">Each instance is instantiated on demand.</span></span> <span data-ttu-id="7797d-108">Доступ к этим веб-службам можно получить через свойства объекта `My.WebServices`.</span><span class="sxs-lookup"><span data-stu-id="7797d-108">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="7797d-109">Имя свойства совпадает с именем веб-службы, к которой обращается свойство.</span><span class="sxs-lookup"><span data-stu-id="7797d-109">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="7797d-110">Любой класс, наследуемый от <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>, является веб-службой.</span><span class="sxs-lookup"><span data-stu-id="7797d-110">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span> <span data-ttu-id="7797d-111">Сведения о добавлении веб-служб в проект см. в разделе [доступ к веб-службам приложений](../../developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="7797d-111">For information about adding Web services to a project, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="7797d-112">`My.WebServices`Объект предоставляет только веб-службы, связанные с текущим проектом.</span><span class="sxs-lookup"><span data-stu-id="7797d-112">The `My.WebServices` object exposes only the Web services associated with the current project.</span></span> <span data-ttu-id="7797d-113">Он не предоставляет доступ к веб-службам, объявленным в упоминаемых в них библиотеках DLL.</span><span class="sxs-lookup"><span data-stu-id="7797d-113">It does not provide access to Web services declared in referenced DLLs.</span></span> <span data-ttu-id="7797d-114">Для доступа к веб-службе, предоставляемой библиотекой DLL, необходимо использовать полное имя веб-службы в формате *dllname*. *WebServiceName*.</span><span class="sxs-lookup"><span data-stu-id="7797d-114">To access a Web service that a DLL provides, you must use the qualified name of the Web service, in the form *DllName*.*WebServiceName*.</span></span> <span data-ttu-id="7797d-115">Дополнительные сведения см. в разделе [доступ к веб-службам приложений](../../developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="7797d-115">For more information, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="7797d-116">Объект и его свойства недоступны для веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="7797d-116">The object and its properties are not available for Web applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7797d-117">Свойства</span><span class="sxs-lookup"><span data-stu-id="7797d-117">Properties</span></span>  

 <span data-ttu-id="7797d-118">Каждое свойство `My.WebServices` объекта предоставляет доступ к экземпляру веб-службы, на которую ссылается текущий проект.</span><span class="sxs-lookup"><span data-stu-id="7797d-118">Each property of the `My.WebServices` object provides access to an instance of a Web service referenced by the current project.</span></span> <span data-ttu-id="7797d-119">Имя свойства совпадает с именем веб-службы, к которой обращается свойство, а тип свойства совпадает с типом веб-службы.</span><span class="sxs-lookup"><span data-stu-id="7797d-119">The name of the property is the same as the name of the Web service that the property accesses, and the property type is the same as the Web service's type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7797d-120">При конфликте имен имя свойства для доступа к веб-службе — *RootNamespace* _ *Namespace* \_ *ServiceName*.</span><span class="sxs-lookup"><span data-stu-id="7797d-120">If there is a name collision, the property name for accessing a Web service is *RootNamespace* _ *Namespace*\_*ServiceName*.</span></span> <span data-ttu-id="7797d-121">Например, рассмотрим две веб-службы с именем `Service1` .</span><span class="sxs-lookup"><span data-stu-id="7797d-121">For example, consider two Web services named `Service1`.</span></span> <span data-ttu-id="7797d-122">Если одна из этих служб находится в корневом пространстве имен `WindowsApplication1` и в пространстве имен `Namespace1` , доступ к этой службе будет осуществляться с помощью `My.WebServices.WindowsApplication1_Namespace1_Service1` .</span><span class="sxs-lookup"><span data-stu-id="7797d-122">If one of these services is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that service by using `My.WebServices.WindowsApplication1_Namespace1_Service1`.</span></span>  
  
 <span data-ttu-id="7797d-123">При первом доступе к одному из `My.WebServices` свойств объекта он создает новый экземпляр веб-службы и сохраняет его.</span><span class="sxs-lookup"><span data-stu-id="7797d-123">When you first access one of the `My.WebServices` object's properties, it creates a new instance of the Web service and stores it.</span></span> <span data-ttu-id="7797d-124">Последующие обращения к этому свойству возвращают этот экземпляр веб-службы.</span><span class="sxs-lookup"><span data-stu-id="7797d-124">Subsequent accesses of that property return that instance of the Web service.</span></span>  
  
 <span data-ttu-id="7797d-125">Вы можете удалить веб-службу, назначив ей `Nothing` свойство для этой веб-службы.</span><span class="sxs-lookup"><span data-stu-id="7797d-125">You can dispose of a Web service by assigning `Nothing` to the property for that Web service.</span></span> <span data-ttu-id="7797d-126">Метод задания свойства присваивает `Nothing` хранимому значению.</span><span class="sxs-lookup"><span data-stu-id="7797d-126">The property setter assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="7797d-127">Если присвоить значение, отличное от `Nothing` свойства, метод задания выдаст <xref:System.ArgumentException> исключение.</span><span class="sxs-lookup"><span data-stu-id="7797d-127">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="7797d-128">Можно проверить `My.WebServices` , сохраняет ли свойство объекта экземпляр веб-службы с помощью `Is` `IsNot` оператора или.</span><span class="sxs-lookup"><span data-stu-id="7797d-128">You can test whether a property of the `My.WebServices` object stores an instance of the Web service by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="7797d-129">С помощью этих операторов можно проверить, имеет ли свойство значение `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="7797d-129">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7797d-130">Как правило, `Is` `IsNot` оператор или должен считывать значение свойства для выполнения сравнения.</span><span class="sxs-lookup"><span data-stu-id="7797d-130">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="7797d-131">Однако если текущее свойство хранится `Nothing` , свойство создает новый экземпляр веб-службы, а затем возвращает этот экземпляр.</span><span class="sxs-lookup"><span data-stu-id="7797d-131">However, if the property currently stores `Nothing`, the property creates a new instance of the Web service and then returns that instance.</span></span> <span data-ttu-id="7797d-132">Однако компилятор Visual Basic обрабатывает свойства `My.WebServices` объекта особым образом и позволяет `Is` `IsNot` оператору или проверить состояние свойства без изменения его значения.</span><span class="sxs-lookup"><span data-stu-id="7797d-132">However, the Visual Basic compiler treats the properties of the `My.WebServices` object specially, and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7797d-133">Пример</span><span class="sxs-lookup"><span data-stu-id="7797d-133">Example</span></span>  

 <span data-ttu-id="7797d-134">В этом примере вызывается `FahrenheitToCelsius` метод `TemperatureConverter` веб-службы XML и возвращается результат.</span><span class="sxs-lookup"><span data-stu-id="7797d-134">This example calls the `FahrenheitToCelsius` method of the `TemperatureConverter` XML Web service, and returns the result.</span></span>  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 <span data-ttu-id="7797d-135">Чтобы этот пример работал, проект должен ссылаться на веб-службу с именем `Converter` , и эта веб-служба должна предоставлять `ConvertTemperature` метод.</span><span class="sxs-lookup"><span data-stu-id="7797d-135">For this example to work, your project must reference a Web service named `Converter`, and that Web service must expose the `ConvertTemperature` method.</span></span> <span data-ttu-id="7797d-136">Дополнительные сведения см. в разделе [доступ к веб-службам приложений](../../developing-apps/programming/accessing-application-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="7797d-136">For more information, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="7797d-137">Этот код не работает в проекте веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="7797d-137">This code does not work in a Web application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7797d-138">Требования</span><span class="sxs-lookup"><span data-stu-id="7797d-138">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="7797d-139">Доступность по типу проекта</span><span class="sxs-lookup"><span data-stu-id="7797d-139">Availability by Project Type</span></span>  
  
|<span data-ttu-id="7797d-140">Тип проекта</span><span class="sxs-lookup"><span data-stu-id="7797d-140">Project type</span></span>|<span data-ttu-id="7797d-141">Доступно</span><span class="sxs-lookup"><span data-stu-id="7797d-141">Available</span></span>|  
|---|---|  
|<span data-ttu-id="7797d-142">Приложение Windows</span><span class="sxs-lookup"><span data-stu-id="7797d-142">Windows Application</span></span>|<span data-ttu-id="7797d-143">**Да**</span><span class="sxs-lookup"><span data-stu-id="7797d-143">**Yes**</span></span>|  
|<span data-ttu-id="7797d-144">Библиотека классов</span><span class="sxs-lookup"><span data-stu-id="7797d-144">Class Library</span></span>|<span data-ttu-id="7797d-145">**Да**</span><span class="sxs-lookup"><span data-stu-id="7797d-145">**Yes**</span></span>|  
|<span data-ttu-id="7797d-146">Консольное приложение</span><span class="sxs-lookup"><span data-stu-id="7797d-146">Console Application</span></span>|<span data-ttu-id="7797d-147">**Да**</span><span class="sxs-lookup"><span data-stu-id="7797d-147">**Yes**</span></span>|  
|<span data-ttu-id="7797d-148">Библиотека элементов управления Windows</span><span class="sxs-lookup"><span data-stu-id="7797d-148">Windows Control Library</span></span>|<span data-ttu-id="7797d-149">**Да**</span><span class="sxs-lookup"><span data-stu-id="7797d-149">**Yes**</span></span>|  
|<span data-ttu-id="7797d-150">Библиотека веб-элементов управления</span><span class="sxs-lookup"><span data-stu-id="7797d-150">Web Control Library</span></span>|<span data-ttu-id="7797d-151">**Да**</span><span class="sxs-lookup"><span data-stu-id="7797d-151">**Yes**</span></span>|  
|<span data-ttu-id="7797d-152">Службы Windows</span><span class="sxs-lookup"><span data-stu-id="7797d-152">Windows Service</span></span>|<span data-ttu-id="7797d-153">**Да**</span><span class="sxs-lookup"><span data-stu-id="7797d-153">**Yes**</span></span>|  
|<span data-ttu-id="7797d-154">Веб-сайт</span><span class="sxs-lookup"><span data-stu-id="7797d-154">Web Site</span></span>|<span data-ttu-id="7797d-155">Нет</span><span class="sxs-lookup"><span data-stu-id="7797d-155">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7797d-156">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7797d-156">See also</span></span>

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [<span data-ttu-id="7797d-157">Доступ к веб-службам приложения</span><span class="sxs-lookup"><span data-stu-id="7797d-157">Accessing Application Web Services</span></span>](../../developing-apps/programming/accessing-application-web-services.md)
