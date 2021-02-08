---
description: Дополнительные сведения см. в статье как создать службу, возвращающую произвольные данные с помощью модели программирования WCF Web HTTP.
title: Практическое руководство. Как создать службу, возвращающую произвольные данные, с использованием модели программирования WCF Web HTTP
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: aeb03e0dad6c63c463db419027f5556922b2f160
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793536"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a><span data-ttu-id="ff507-103">Практическое руководство. Как создать службу, возвращающую произвольные данные, с использованием модели программирования WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="ff507-103">How to: Create a Service That Returns Arbitrary Data Using The WCF Web HTTP Programming Model</span></span>

<span data-ttu-id="ff507-104">Иногда разработчики должны полностью управлять тем, как данные возвращаются из операции службы.</span><span class="sxs-lookup"><span data-stu-id="ff507-104">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="ff507-105">Так происходит, когда операция службы должна возвращать данные в формате, не поддерживаемом WCF.</span><span class="sxs-lookup"><span data-stu-id="ff507-105">This is the case when a service operation must return data in a format not supported by WCF.</span></span> <span data-ttu-id="ff507-106">В этом разделе обсуждается использование модели программирования WCF WEB HTTP для создания такой службы.</span><span class="sxs-lookup"><span data-stu-id="ff507-106">This topic discusses using the WCF WEB HTTP Programming Model to create such a service.</span></span> <span data-ttu-id="ff507-107">В этой службе имеется одна операция, которая возвращает поток.</span><span class="sxs-lookup"><span data-stu-id="ff507-107">This service has one operation that returns a stream.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="ff507-108">Реализация контракта службы</span><span class="sxs-lookup"><span data-stu-id="ff507-108">To implement the service contract</span></span>  
  
1. <span data-ttu-id="ff507-109">Определите контракт службы.</span><span class="sxs-lookup"><span data-stu-id="ff507-109">Define the service contract.</span></span> <span data-ttu-id="ff507-110">Контракт называется `IImageServer` и в нем имеется один метод под названием `GetImage`, который возвращает поток <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="ff507-110">The contract is called `IImageServer` and has one method called `GetImage` that returns a <xref:System.IO.Stream>.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     <span data-ttu-id="ff507-111">Поскольку метод возвращает <xref:System.IO.Stream> , WCF предполагает, что операция имеет полный контроль над байтами, возвращаемыми операцией службы, и не применяет форматирование к возвращаемым данным.</span><span class="sxs-lookup"><span data-stu-id="ff507-111">Because the method returns a <xref:System.IO.Stream>, WCF assumes that the operation has complete control over the bytes that are returned from the service operation and it applies no formatting to the data that is returned.</span></span>  
  
2. <span data-ttu-id="ff507-112">Реализуйте контракт службы.</span><span class="sxs-lookup"><span data-stu-id="ff507-112">Implement the service contract.</span></span> <span data-ttu-id="ff507-113">В контракте есть только одна операция (`GetImage`).</span><span class="sxs-lookup"><span data-stu-id="ff507-113">The contract has only one operation (`GetImage`).</span></span> <span data-ttu-id="ff507-114">Этот метод создает растровое изображение и сохраняет его в потоке <xref:System.IO.MemoryStream> в формате JPG.</span><span class="sxs-lookup"><span data-stu-id="ff507-114">This method generates a bitmap and then save it to a <xref:System.IO.MemoryStream> in .jpg format.</span></span> <span data-ttu-id="ff507-115">Операция затем возвращает этот поток вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="ff507-115">The operation then returns that stream to the caller.</span></span>  
  
    ```csharp
    public class Service : IImageServer
    {
        public Stream GetImage(int width, int height)
        {
            Bitmap bitmap = new Bitmap(width, height);
            for (int i = 0; i < bitmap.Width; i++)
            {
                for (int j = 0; j < bitmap.Height; j++)
                {
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);
                }
            }
            MemoryStream ms = new MemoryStream();
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);
            ms.Position = 0;
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";
            return ms;
        }
    }
    ```  
  
     <span data-ttu-id="ff507-116">Взгляните на последнюю строку кода: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span><span class="sxs-lookup"><span data-stu-id="ff507-116">Notice the second to last line of code: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span></span>  
  
     <span data-ttu-id="ff507-117">При этом задается заголовок типа содержимого `"image/jpeg"` .</span><span class="sxs-lookup"><span data-stu-id="ff507-117">This sets the content type header to `"image/jpeg"`.</span></span> <span data-ttu-id="ff507-118">Хотя в этом образце показано, как вернуть JPG-файл, данный образец можно изменить для возврата любого типа необходимых данных в любом формате.</span><span class="sxs-lookup"><span data-stu-id="ff507-118">Although this sample shows how to return a .jpg file, it can be modified to return any type of data that is required, in any format.</span></span> <span data-ttu-id="ff507-119">Операция должна получить или создать данные и затем записать их в поток.</span><span class="sxs-lookup"><span data-stu-id="ff507-119">The operation must retrieve or generate the data and then write it to a stream.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="ff507-120">Размещение службы</span><span class="sxs-lookup"><span data-stu-id="ff507-120">To host the service</span></span>  
  
1. <span data-ttu-id="ff507-121">Создайте консольное приложение для размещения службы.</span><span class="sxs-lookup"><span data-stu-id="ff507-121">Create a console application to host the service.</span></span>  
  
    ```csharp
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }
    }  
    ```  
  
2. <span data-ttu-id="ff507-122">Создайте переменную для хранения базового адреса службы в методе `Main`.</span><span class="sxs-lookup"><span data-stu-id="ff507-122">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="ff507-123">Создайте экземпляр <xref:System.ServiceModel.ServiceHost> для службы, задав класс службы и базовый адрес.</span><span class="sxs-lookup"><span data-stu-id="ff507-123">Create a <xref:System.ServiceModel.ServiceHost> instance for the service specifying the service class and the base address.</span></span>  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="ff507-124">Добавьте конечную точку, используя <xref:System.ServiceModel.WebHttpBinding> и <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="ff507-124">Add an endpoint using the <xref:System.ServiceModel.WebHttpBinding> and the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="ff507-125">Откройте узел службы.</span><span class="sxs-lookup"><span data-stu-id="ff507-125">Open the service host.</span></span>  
  
    ```csharp  
    host.Open();  
    ```  
  
6. <span data-ttu-id="ff507-126">Подождите, пока пользователь нажмет клавишу ВВОД, чтобы завершить работу службы.</span><span class="sxs-lookup"><span data-stu-id="ff507-126">Wait until the user presses ENTER to terminate the service.</span></span>  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a><span data-ttu-id="ff507-127">Вызов необработанной службы с помощью Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="ff507-127">To call the raw service using Internet Explorer</span></span>  
  
1. <span data-ttu-id="ff507-128">Запустите службу. От службы должно появиться следующее сообщение:</span><span class="sxs-lookup"><span data-stu-id="ff507-128">Run the service, you should see the following output from the service.</span></span> `Service is running Press ENTER to close the host`  
  
2. <span data-ttu-id="ff507-129">Откройте Internet Explorer и введите `http://localhost:8000/Service/GetImage?width=50&height=40`. Должен появиться желтый прямоугольник с синей диагональной линией, проходящей через центр.</span><span class="sxs-lookup"><span data-stu-id="ff507-129">Open Internet Explorer and type in `http://localhost:8000/Service/GetImage?width=50&height=40` you should see a yellow rectangle with a blue diagonal line through the center.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff507-130">Пример</span><span class="sxs-lookup"><span data-stu-id="ff507-130">Example</span></span>  

 <span data-ttu-id="ff507-131">Ниже приведен полный листинг кода для данного раздела.</span><span class="sxs-lookup"><span data-stu-id="ff507-131">The following is a complete listing of the code for this topic.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Drawing;  
  
namespace RawImageService  
{  
    // Define the service contract  
    [ServiceContract]  
    public interface IImageServer  
    {  
        [WebGet]  
        Stream GetImage(int width, int height);  
    }  
  
    // implement the service contract  
    public class Service : IImageServer  
    {  
        public Stream GetImage(int width, int height)  
        {  
            // Although this method returns a jpeg, it can be  
            // modified to return any data you want within the stream  
            Bitmap bitmap = new Bitmap(width, height);  
            for (int i = 0; i < bitmap.Width; i++)  
            {  
                for (int j = 0; j < bitmap.Height; j++)  
                {  
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                }  
            }  
            MemoryStream ms = new MemoryStream();  
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
            ms.Position = 0;  
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
            return ms;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Service is running");  
            Console.Write("Press ENTER to close the host");  
            Console.ReadLine();  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ff507-132">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="ff507-132">Compiling the Code</span></span>  
  
- <span data-ttu-id="ff507-133">При компиляции образец кода обращается к файлам System.ServiceModel.dll и System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="ff507-133">When compiling the sample code reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff507-134">См. также</span><span class="sxs-lookup"><span data-stu-id="ff507-134">See also</span></span>

- [<span data-ttu-id="ff507-135">Модель веб-программирования HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="ff507-135">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
