---
description: 'Дополнительные сведения: указание Передача данных в контрактах служб'
title: Задание передачи данных в контрактах служб
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: 672d2127af95847c0a085a8ca1c358f2a8440dee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793432"
---
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="30350-103">Задание передачи данных в контрактах служб</span><span class="sxs-lookup"><span data-stu-id="30350-103">Specifying Data Transfer in Service Contracts</span></span>

<span data-ttu-id="30350-104">Windows Communication Foundation (WCF) можно рассматривать как инфраструктуру обмена сообщениями.</span><span class="sxs-lookup"><span data-stu-id="30350-104">The Windows Communication Foundation (WCF) can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="30350-105">Операции служб могут получать сообщения, обрабатывать их и отправлять.</span><span class="sxs-lookup"><span data-stu-id="30350-105">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="30350-106">Сообщения описываются с помощью контрактов операций.</span><span class="sxs-lookup"><span data-stu-id="30350-106">Messages are described using operation contracts.</span></span> <span data-ttu-id="30350-107">Например, рассмотрим следующий контракт:</span><span class="sxs-lookup"><span data-stu-id="30350-107">For example, consider the following contract.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(string fromCity, string toCity);  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
  
    <OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
End Interface  
```  
  
 <span data-ttu-id="30350-108">Операция `GetAirfare` принимает сообщение с информацией о `fromCity` и `toCity`, затем возвращает сообщение, содержащее число.</span><span class="sxs-lookup"><span data-stu-id="30350-108">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="30350-109">В этом разделе рассматриваются различные способы описания сообщений в контракте операции.</span><span class="sxs-lookup"><span data-stu-id="30350-109">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="30350-110">Описание сообщений с помощью параметров</span><span class="sxs-lookup"><span data-stu-id="30350-110">Describing Messages by Using Parameters</span></span>  

 <span data-ttu-id="30350-111">Простейший способ описания сообщений - с помощью списка параметров и возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="30350-111">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="30350-112">В приведенном выше примере строковые параметры `fromCity` и `toCity` используются для описания сообщения запроса, а возвращаемое значение типа "float" - для описания ответного сообщения.</span><span class="sxs-lookup"><span data-stu-id="30350-112">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="30350-113">Если возвращаемое значение само по себе недостаточно для описания ответного сообщения, можно использовать выходные параметры.</span><span class="sxs-lookup"><span data-stu-id="30350-113">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="30350-114">Например, следующая операция содержит строки `fromCity` и `toCity` в сообщении запроса и число с названием валюты в ответном сообщении:</span><span class="sxs-lookup"><span data-stu-id="30350-114">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="30350-115">Кроме того, используя ссылочные параметры, можно сделать параметр частью обоих сообщений (запроса и ответа).</span><span class="sxs-lookup"><span data-stu-id="30350-115">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="30350-116">Параметры должны принадлежать к сериализуемому типу (преобразуемому в XML).</span><span class="sxs-lookup"><span data-stu-id="30350-116">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="30350-117">По умолчанию в WCF для выполнения этого преобразования используется компонент, называемый <xref:System.Runtime.Serialization.DataContractSerializer> классом.</span><span class="sxs-lookup"><span data-stu-id="30350-117">By default, WCF uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="30350-118">Поддерживается большая часть типов-примитивов (таких как `int`, `string`, `float` и `DateTime`).</span><span class="sxs-lookup"><span data-stu-id="30350-118">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="30350-119">Как правило, пользовательские типы должны иметь контракт данных.</span><span class="sxs-lookup"><span data-stu-id="30350-119">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="30350-120">Дополнительные сведения см. [в разделе Использование контрактов данных](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="30350-120">For more information, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
```csharp
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
  
    [DataContract]  
    public class Itinerary  
    {  
        [DataMember]  
        public string fromCity;  
        [DataMember]  
        public string toCity;  
   }  
}  
```  
  
```vb  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
    <DataContract()>  
    Class Itinerary  
  
        <DataMember()>  
        Public fromCity As String  
        <DataMember()>  
        Public toCity As String  
    End Class  
End Interface  
```  
  
 <span data-ttu-id="30350-121">Иногда объект `DataContractSerializer` не подходит для сериализации конкретных типов.</span><span class="sxs-lookup"><span data-stu-id="30350-121">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> <span data-ttu-id="30350-122">WCF поддерживает альтернативный механизм сериализации, <xref:System.Xml.Serialization.XmlSerializer> который также можно использовать для сериализации параметров.</span><span class="sxs-lookup"><span data-stu-id="30350-122">WCF supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="30350-123">Сериализатор <xref:System.Xml.Serialization.XmlSerializer> позволяет более четко контролировать результирующий XML-код с помощью атрибутов, таких как `XmlAttributeAttribute`.</span><span class="sxs-lookup"><span data-stu-id="30350-123">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="30350-124">Чтобы перейти на использование сериализатора <xref:System.Xml.Serialization.XmlSerializer> для определенной операции или для всей службы, примените к ней атрибут <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="30350-124">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="30350-125">Пример:</span><span class="sxs-lookup"><span data-stu-id="30350-125">For example:</span></span>  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    [XmlSerializerFormat]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
}  
public class Itinerary  
{  
    public string fromCity;  
    public string toCity;  
    [XmlAttribute]  
    public bool isFirstClass;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    <XmlSerializerFormat>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
End Interface  
  
Class Itinerary  
  
    Public fromCity As String  
    Public toCity As String  
    <XmlSerializerFormat()>  
    Public isFirstClass As Boolean  
End Class  
```  
  
 <span data-ttu-id="30350-126">Дополнительные сведения см. [в разделе Использование класса XmlSerializer](using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="30350-126">For more information, see [Using the XmlSerializer Class](using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="30350-127">Следует помнить, что задавать использование модуля <xref:System.Xml.Serialization.XmlSerializer> вручную (как показано выше) не рекомендуется, если для этого нет определенных причин, рассмотренных в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="30350-127">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="30350-128">Изолировать имена параметров .NET от имен контрактов можно с помощью атрибута <xref:System.ServiceModel.MessageParameterAttribute>, а задать имя контракта - с помощью свойства `Name`.</span><span class="sxs-lookup"><span data-stu-id="30350-128">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="30350-129">Например, следующий контракт операции эквивалентен приведенному в первом примере этого раздела.</span><span class="sxs-lookup"><span data-stu-id="30350-129">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
```csharp  
[OperationContract]  
public float GetAirfare(  
    [MessageParameter(Name="fromCity")] string originCity,  
    [MessageParameter(Name="toCity")] string destinationCity);  
```  
  
```vb  
<OperationContract()>  
  Function GetAirfare(<MessageParameter(Name := "fromCity")> fromCity As String, <MessageParameter(Name := "toCity")> toCity As String) As Double  
```  
  
## <a name="describing-empty-messages"></a><span data-ttu-id="30350-130">Описание пустых сообщений</span><span class="sxs-lookup"><span data-stu-id="30350-130">Describing Empty Messages</span></span>  

 <span data-ttu-id="30350-131">Пустое сообщение запроса можно описать с помощью отсутствия входных и ссылочных параметров.</span><span class="sxs-lookup"><span data-stu-id="30350-131">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="30350-132">Например, в C#:</span><span class="sxs-lookup"><span data-stu-id="30350-132">For example, in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="30350-133">Например, в Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="30350-133">For example, in Visual Basic:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="30350-134">Пустое сообщение ответа можно описать, указав тип `void` для возвращаемого значения и отсутствие входных и ссылочных параметров.</span><span class="sxs-lookup"><span data-stu-id="30350-134">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="30350-135">Например, в</span><span class="sxs-lookup"><span data-stu-id="30350-135">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="30350-136">Это действие не является односторонней операцией, как например:</span><span class="sxs-lookup"><span data-stu-id="30350-136">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="30350-137">Операция `SetTemperatureStatus` возвращает пустое сообщение.</span><span class="sxs-lookup"><span data-stu-id="30350-137">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="30350-138">Вместо него она может вернуть ошибку, если возникнет проблема при обработке входного сообщения.</span><span class="sxs-lookup"><span data-stu-id="30350-138">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="30350-139">Операция `SetLightbulbStatus` не возвращает какое-либо значение.</span><span class="sxs-lookup"><span data-stu-id="30350-139">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="30350-140">Эта операция никоим образом не может сообщить об ошибке.</span><span class="sxs-lookup"><span data-stu-id="30350-140">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="30350-141">Описание сообщений с помощью контрактов сообщений</span><span class="sxs-lookup"><span data-stu-id="30350-141">Describing Messages by Using Message Contracts</span></span>  

 <span data-ttu-id="30350-142">Иногда имеет смысл представить все сообщение одним типом.</span><span class="sxs-lookup"><span data-stu-id="30350-142">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="30350-143">Хотя для этого можно использовать контракт данных, все же рекомендуется использовать контракт сообщений: это позволяет избежать чрезмерных уровней заключения в оболочку в результирующем XML-коде.</span><span class="sxs-lookup"><span data-stu-id="30350-143">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="30350-144">Кроме того, контракты сообщений обеспечивают более полное управление результирующими сообщениями.</span><span class="sxs-lookup"><span data-stu-id="30350-144">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="30350-145">Например, можно задать, какие именно сведения должны находиться в тексте сообщения и какие в заголовке.</span><span class="sxs-lookup"><span data-stu-id="30350-145">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="30350-146">В следующем примере показано использование контрактов сообщений.</span><span class="sxs-lookup"><span data-stu-id="30350-146">The following example shows the use of message contracts.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    GetAirfareResponse GetAirfare(GetAirfareRequest request);  
}  
  
[MessageContract]  
public class GetAirfareRequest  
{  
    [MessageHeader] public DateTime date;  
    [MessageBodyMember] public Itinerary itinerary;  
}  
  
[MessageContract]  
public class GetAirfareResponse  
{  
    [MessageBodyMember] public float airfare;  
    [MessageBodyMember] public string currency;  
}  
  
[DataContract]  
public class Itinerary  
{  
    [DataMember] public string fromCity;  
    [DataMember] public string toCity;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    Function GetAirfare(request As GetAirfareRequest) As GetAirfareResponse  
End Interface  
  
<MessageContract()>  
Public Class GetAirfareRequest  
    <MessageHeader()>
    Public Property date as DateTime  
    <MessageBodyMember()>  
    Public Property itinerary As Itinerary  
End Class  
  
<MessageContract()>  
Public Class GetAirfareResponse  
    <MessageBodyMember()>  
    Public Property airfare As Double  
    <MessageBodyMember()> Public Property currency As String  
End Class  
  
<DataContract()>  
Public Class Itinerary  
    <DataMember()> Public Property fromCity As String  
    <DataMember()> Public Property toCity As String  
End Class  
```  
  
 <span data-ttu-id="30350-147">Дополнительные сведения см. [в разделе Использование контрактов сообщений](using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="30350-147">For more information, see [Using Message Contracts](using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="30350-148">В приведенном выше примере класс <xref:System.Runtime.Serialization.DataContractSerializer> используется по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="30350-148">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="30350-149">Класс <xref:System.Xml.Serialization.XmlSerializer> также можно использовать с контрактами сообщений.</span><span class="sxs-lookup"><span data-stu-id="30350-149">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="30350-150">Для этого примените атрибут <xref:System.ServiceModel.XmlSerializerFormatAttribute> к операции или к контракту и используйте типы, совместимые с классом <xref:System.Xml.Serialization.XmlSerializer>, в заголовках сообщения и элементах тела сообщения.</span><span class="sxs-lookup"><span data-stu-id="30350-150">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="30350-151">Описание сообщений с помощью потоков</span><span class="sxs-lookup"><span data-stu-id="30350-151">Describing Messages by Using Streams</span></span>  

 <span data-ttu-id="30350-152">Еще один способ описания сообщений в операциях - использование класса <xref:System.IO.Stream> (или одного из производных от него классов) в контракте операции или в качестве элемента тела контракта сообщения (в этом случае он должен быть единственным элементом).</span><span class="sxs-lookup"><span data-stu-id="30350-152">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="30350-153">Для входящих сообщений необходимо использовать тип `Stream`: производные классы использовать не допускается.</span><span class="sxs-lookup"><span data-stu-id="30350-153">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="30350-154">Вместо вызова сериализатора WCF извлекает данные из потока и помещает их непосредственно в исходящее сообщение или получает данные из входящего сообщения и помещает их непосредственно в поток.</span><span class="sxs-lookup"><span data-stu-id="30350-154">Instead of invoking the serializer, WCF retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="30350-155">В следующем образце показано использование потоков.</span><span class="sxs-lookup"><span data-stu-id="30350-155">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="30350-156">Нельзя совмещать потоковые данные (`Stream`) с непотоковыми в одном теле сообщения.</span><span class="sxs-lookup"><span data-stu-id="30350-156">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="30350-157">Используйте контракт сообщения, чтобы поместить дополнительные данные в заголовок сообщения.</span><span class="sxs-lookup"><span data-stu-id="30350-157">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="30350-158">В следующем примере показано неправильное использование потоков при определении контракта операции.</span><span class="sxs-lookup"><span data-stu-id="30350-158">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
```csharp  
//Incorrect:  
// [OperationContract]  
// public void UploadFile (string fileName, Stream fileData);  
```  
  
```vb  
'Incorrect:  
    '<OperationContract()>  
    Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
```  
  
 <span data-ttu-id="30350-159">В следующем образце показано правильное использование потоков при определении контракта операции.</span><span class="sxs-lookup"><span data-stu-id="30350-159">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
```csharp  
[OperationContract]  
public void UploadFile (UploadFileMessage message);  
//code omitted  
[MessageContract]  
public class UploadFileMessage  
{  
    [MessageHeader] public string fileName;  
    [MessageBodyMember] public Stream fileData;  
}  
```  
  
```vb  
<OperationContract()>  
Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
'Code Omitted  
<MessageContract()>  
Public Class UploadFileMessage  
   <MessageHeader()>  
    Public Property fileName As String  
    <MessageBodyMember()>  
    Public Property fileData As Stream  
End Class  
```  
  
 <span data-ttu-id="30350-160">Дополнительные сведения см. в разделе [большие данные и потоковая передача](large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="30350-160">For more information, see [Large Data and Streaming](large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="30350-161">Использование класса сообщений</span><span class="sxs-lookup"><span data-stu-id="30350-161">Using the Message Class</span></span>  

 <span data-ttu-id="30350-162">Чтобы обеспечить полный программный контроль над получаемыми или отправляемыми сообщениями, можно использовать класс <xref:System.ServiceModel.Channels.Message> напрямую, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="30350-162">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="30350-163">Это расширенный сценарий, подробно описанный в разделе [использование класса Message](using-the-message-class.md).</span><span class="sxs-lookup"><span data-stu-id="30350-163">This is an advanced scenario, which is described in detail in [Using the Message Class](using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="30350-164">Описание сообщений об ошибках</span><span class="sxs-lookup"><span data-stu-id="30350-164">Describing Fault Messages</span></span>  

 <span data-ttu-id="30350-165">Помимо сообщений, описываемых возвращаемыми значениями и выходными или ссылочными параметрами, любая неодносторонняя операция может возвращать не менее двух возможных значений: нормальное ответное сообщение и сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="30350-165">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="30350-166">Рассмотрим следующий контракт операции.</span><span class="sxs-lookup"><span data-stu-id="30350-166">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="30350-167">Эта операция может возвращать либо нормальное сообщение, содержащее число `float`, либо сообщение об ошибке, содержащее код ошибки и ее описание.</span><span class="sxs-lookup"><span data-stu-id="30350-167">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="30350-168">Для этого следует предусмотреть вызов исключения <xref:System.ServiceModel.FaultException> при реализации службы.</span><span class="sxs-lookup"><span data-stu-id="30350-168">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="30350-169">Можно указать дополнительные сообщения об ошибках с помощью атрибута <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="30350-169">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="30350-170">Необходима возможность сериализации дополнительных ошибок с помощью кода <xref:System.Runtime.Serialization.DataContractSerializer>, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="30350-170">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
[FaultContract(typeof(ItineraryNotAvailableFault))]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
  
//code omitted  
  
[DataContract]  
public class ItineraryNotAvailableFault  
{  
    [DataMember]  
    public bool IsAlternativeDateAvailable;  
  
    [DataMember]  
    public DateTime alternativeSuggestedDate;  
}  
```  
  
```vb  
<OperationContract()>  
<FaultContract(GetType(ItineraryNotAvailableFault))>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime) As Double  
  
'Code Omitted  
<DataContract()>  
Public Class  
  <DataMember()>  
  Public Property IsAlternativeDateAvailable As Boolean  
  <DataMember()>  
  Public Property alternativeSuggestedDate As DateTime  
End Class  
```  
  
 <span data-ttu-id="30350-171">Эти дополнительные ошибки можно создать вызовом исключения <xref:System.ServiceModel.FaultException%601> с соответствующим типом данных контракта.</span><span class="sxs-lookup"><span data-stu-id="30350-171">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="30350-172">Дополнительные сведения см. в разделе [обработка исключений и ошибок](../extending/handling-exceptions-and-faults.md).</span><span class="sxs-lookup"><span data-stu-id="30350-172">For more information, see [Handling Exceptions and Faults](../extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="30350-173">Использовать класс <xref:System.Xml.Serialization.XmlSerializer> для описания ошибок не допускается.</span><span class="sxs-lookup"><span data-stu-id="30350-173">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="30350-174">Атрибут <xref:System.ServiceModel.XmlSerializerFormatAttribute> не влияет на контракты ошибок.</span><span class="sxs-lookup"><span data-stu-id="30350-174">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="30350-175">Использование производных типов</span><span class="sxs-lookup"><span data-stu-id="30350-175">Using Derived Types</span></span>  

 <span data-ttu-id="30350-176">Иногда имеет смысл использовать базовый тип в контракте операции или сообщения, а затем (при фактическом вызове операции) производный тип.</span><span class="sxs-lookup"><span data-stu-id="30350-176">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="30350-177">В этом случае необходимо использовать либо атрибут <xref:System.ServiceModel.ServiceKnownTypeAttribute>, либо некий альтернативный механизм, позволяющий использовать производные типы.</span><span class="sxs-lookup"><span data-stu-id="30350-177">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="30350-178">Рассмотрим следующую операцию.</span><span class="sxs-lookup"><span data-stu-id="30350-178">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="30350-179">Предположим, что два типа, `Book` и `Magazine`, унаследованы от `LibraryItem`.</span><span class="sxs-lookup"><span data-stu-id="30350-179">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="30350-180">Чтобы использовать их в операции `IsLibraryItemAvailable`, можно изменить ее следующим образом:</span><span class="sxs-lookup"><span data-stu-id="30350-180">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="30350-181">Или же можно воспользоваться атрибутом <xref:System.Runtime.Serialization.KnownTypeAttribute>, если атрибут по умолчанию <xref:System.Runtime.Serialization.DataContractSerializer> уже используется, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="30350-181">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
  
// code omitted
  
[DataContract]  
[KnownType(typeof(Book))]  
[KnownType(typeof(Magazine))]  
public class LibraryItem  
{  
    //code omitted  
}  
```  
  
```vb  
<OperationContract()>  
Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
  
'Code Omitted  
<DataContract()>  
<KnownType(GetType(Book))>  
<KnownType(GetType(Magazine))>  
Public Class LibraryItem  
  'Code Omitted  
End Class  
```  
  
 <span data-ttu-id="30350-182">Для этого примените атрибут <xref:System.Xml.Serialization.XmlIncludeAttribute> при использовании <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="30350-182">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="30350-183">Атрибут <xref:System.ServiceModel.ServiceKnownTypeAttribute> можно применить к операции или ко всей службе.</span><span class="sxs-lookup"><span data-stu-id="30350-183">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="30350-184">Он принимает либо тип, либо имя метода, при вызове которого возвращается список известных типов (подобно атрибуту <xref:System.Runtime.Serialization.KnownTypeAttribute>).</span><span class="sxs-lookup"><span data-stu-id="30350-184">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="30350-185">Дополнительные сведения см. в статье о [известных типах контрактов данных](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="30350-185">For more information, see [Data Contract Known Types](data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="30350-186">Указание назначения и стиля</span><span class="sxs-lookup"><span data-stu-id="30350-186">Specifying the Use and Style</span></span>  

 <span data-ttu-id="30350-187">Для описания служб с помощью языка WSDL наиболее часто используются следующие две службы: Document и RPC (удаленный вызов процедуры).</span><span class="sxs-lookup"><span data-stu-id="30350-187">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="30350-188">В стиле Document тело сообщения полностью описывается с помощью схемы, а в языке WSDL различные части тела сообщения описываются ссылками на элементы в этой схеме.</span><span class="sxs-lookup"><span data-stu-id="30350-188">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="30350-189">В стиле RPC код WSDL ссылается на тип схемы для каждой части сообщения, а не элемент.</span><span class="sxs-lookup"><span data-stu-id="30350-189">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="30350-190">В некоторых случаях необходимо выбрать один из этих типов вручную.</span><span class="sxs-lookup"><span data-stu-id="30350-190">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="30350-191">Для этого можно применить атрибут <xref:System.ServiceModel.DataContractFormatAttribute> и задать свойство `Style` (когда используется <xref:System.Runtime.Serialization.DataContractSerializer>) или задать `Style` атрибуту <xref:System.ServiceModel.XmlSerializerFormatAttribute> (когда используется <xref:System.Xml.Serialization.XmlSerializer>).</span><span class="sxs-lookup"><span data-stu-id="30350-191">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="30350-192">Кроме того, <xref:System.Xml.Serialization.XmlSerializer> поддерживает две формы сериализованного XML: `Literal` и `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="30350-192">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="30350-193">`Literal` - наиболее распространенная форма, а также единственная форма, которую поддерживает <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="30350-193">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="30350-194">`Encoded` - это форма из прежних версий, описанная в разделе 5 спецификации протокола SOAP. Не рекомендуется для использования в новых службах.</span><span class="sxs-lookup"><span data-stu-id="30350-194">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="30350-195">Чтобы перейти в режим `Encoded`, задайте свойству `Use` атрибута <xref:System.ServiceModel.XmlSerializerFormatAttribute> значение `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="30350-195">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="30350-196">В большинстве случаев лучше не изменять параметры по умолчанию для свойств `Style` и `Use`.</span><span class="sxs-lookup"><span data-stu-id="30350-196">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="30350-197">Управление процессом сериализации</span><span class="sxs-lookup"><span data-stu-id="30350-197">Controlling the Serialization Process</span></span>  

 <span data-ttu-id="30350-198">Сериализацию данных можно настраивать различными способами.</span><span class="sxs-lookup"><span data-stu-id="30350-198">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="30350-199">Изменение параметров сериализации для сервера</span><span class="sxs-lookup"><span data-stu-id="30350-199">Changing Server Serialization Settings</span></span>  

 <span data-ttu-id="30350-200">Если используется сериализатор по умолчанию <xref:System.Runtime.Serialization.DataContractSerializer>, можно управлять некоторыми аспектами процесса сериализации в службе путем применения к ней атрибута <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="30350-200">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="30350-201">В частности, с помощью свойства `MaxItemsInObjectGraph` можно задать максимальную квоту на количество объектов, десериализуемых с помощью <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="30350-201">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="30350-202">Можно использовать свойство `IgnoreExtensionDataObject` для отключения функции полной совместимости управления версиями.</span><span class="sxs-lookup"><span data-stu-id="30350-202">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="30350-203">Дополнительные сведения о квотах см. в разделе [Вопросы безопасности для данных](security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="30350-203">For more information about quotas, see [Security Considerations for Data](security-considerations-for-data.md).</span></span> <span data-ttu-id="30350-204">Дополнительные сведения о циклической активации см. в разделе [контракты данных с прямыми совместимостью](forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="30350-204">For more information about round-tripping, see [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md).</span></span>  
  
```csharp  
[ServiceBehavior(MaxItemsInObjectGraph=100000)]  
public class MyDataService:IDataService  
{  
    public DataPoint[] GetData()  
    {  
       // Implementation omitted  
    }  
}  
```  
  
```vb  
<ServiceBehavior(MaxItemsInObjectGraph:=100000)>  
Public Class MyDataService Implements IDataService  
  
    Function GetData() As DataPoint()  
         ‘ Implementation omitted  
    End Function  
End Interface  
```  
  
### <a name="serialization-behaviors"></a><span data-ttu-id="30350-205">Поведения сериализации</span><span class="sxs-lookup"><span data-stu-id="30350-205">Serialization Behaviors</span></span>  

 <span data-ttu-id="30350-206">В WCF доступны два поведения — <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> и <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> , которые автоматически подключаются в зависимости от того, какой сериализатор используется для определенной операции.</span><span class="sxs-lookup"><span data-stu-id="30350-206">Two behaviors are available in WCF, the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="30350-207">Поскольку эти поведения применяются автоматически, о них обычно можно не беспокоиться.</span><span class="sxs-lookup"><span data-stu-id="30350-207">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="30350-208">Впрочем, у поведения `DataContractSerializerOperationBehavior` имеются свойства `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject` и `DataContractSurrogate`, позволяющие настроить процесс сериализации.</span><span class="sxs-lookup"><span data-stu-id="30350-208">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="30350-209">Назначение первых двух из вышеперечисленных свойств аналогично рассмотренному в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="30350-209">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="30350-210">С помощью свойства `DataContractSurrogate` можно включить суррогаты контрактов данных - мощный механизм настройки и расширения процесса сериализации.</span><span class="sxs-lookup"><span data-stu-id="30350-210">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="30350-211">Дополнительные сведения см. в разделе [суррогаты контракта данных](../extending/data-contract-surrogates.md).</span><span class="sxs-lookup"><span data-stu-id="30350-211">For more information, see [Data Contract Surrogates](../extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="30350-212">С помощью поведения `DataContractSerializerOperationBehavior` можно настроить сериализацию как для клиента, так и для сервера.</span><span class="sxs-lookup"><span data-stu-id="30350-212">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="30350-213">В следующем примере показано, как увеличить квоту `MaxItemsInObjectGraph` для клиента.</span><span class="sxs-lookup"><span data-stu-id="30350-213">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
```csharp  
ChannelFactory<IDataService> factory = new ChannelFactory<IDataService>(binding, address);  
foreach (OperationDescription op in factory.Endpoint.Contract.Operations)  
{  
    DataContractSerializerOperationBehavior dataContractBehavior =  
                op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
    if (dataContractBehavior != null)  
    {  
        dataContractBehavior.MaxItemsInObjectGraph = 100000;  
    }  
}  
IDataService client = factory.CreateChannel();  
```  
  
```vb  
Dim factory As ChannelFactory(Of IDataService) = New ChannelFactory(Of IDataService)(binding, address)  
For Each op As OperationDescription In factory.Endpoint.Contract.Operations  
        Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
        If dataContractBehavior IsNot Nothing Then  
            dataContractBehavior.MaxItemsInObjectGraph = 100000  
        End If  
     Next  
    Dim client As IDataService = factory.CreateChannel  
```  
  
<span data-ttu-id="30350-214">Ниже приведен эквивалентный код службы в собственном размещении:</span><span class="sxs-lookup"><span data-stu-id="30350-214">The following is the equivalent code on the service, in the self-hosted case:</span></span>
  
```csharp  
ServiceHost serviceHost = new ServiceHost(typeof(IDataService))  
foreach (ServiceEndpoint ep in serviceHost.Description.Endpoints)  
{  
foreach (OperationDescription op in ep.Contract.Operations)  
{  
        DataContractSerializerOperationBehavior dataContractBehavior =  
           op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
        if (dataContractBehavior != null)  
        {  
            dataContractBehavior.MaxItemsInObjectGraph = 100000;  
        }  
}  
}  
serviceHost.Open();  
```  
  
```vb  
Dim serviceHost As ServiceHost = New ServiceHost(GetType(IDataService))  
        For Each ep As ServiceEndpoint In serviceHost.Description.Endpoints  
            For Each op As OperationDescription In ep.Contract.Operations  
                Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
  
                If dataContractBehavior IsNot Nothing Then  
                    dataContractBehavior.MaxItemsInObjectGraph = 100000  
                End If  
            Next  
        Next  
        serviceHost.Open()  
```  
  
 <span data-ttu-id="30350-215">Если клиент размещен в Интернете, необходимо создать новый класс, производный от `ServiceHost`, и подключить его с помощью фабрики узла служб.</span><span class="sxs-lookup"><span data-stu-id="30350-215">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="30350-216">Управление параметрами сериализации в конфигурации</span><span class="sxs-lookup"><span data-stu-id="30350-216">Controlling Serialization Settings in Configuration</span></span>  

 <span data-ttu-id="30350-217">Параметры `MaxItemsInObjectGraph` и `IgnoreExtensionDataObject` можно изменять с помощью конфигурации, используя конечную точку `dataContractSerializer` или поведение службы, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="30350-217">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="LargeQuotaBehavior">  
                    <dataContractSerializer  
                      maxItemsInObjectGraph="100000" />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <client>  
            <endpoint address="http://example.com/myservice"  
                  behaviorConfiguration="LargeQuotaBehavior"  
                binding="basicHttpBinding" bindingConfiguration=""
                            contract="IDataService"  
                name="" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="30350-218">Сериализация общих типов, сохранение графов объектов и пользовательские сериализаторы</span><span class="sxs-lookup"><span data-stu-id="30350-218">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  

 <span data-ttu-id="30350-219"><xref:System.Runtime.Serialization.DataContractSerializer> при сериализации использует имена контрактов данных, а не имена типов .NET.</span><span class="sxs-lookup"><span data-stu-id="30350-219">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="30350-220">Это соответствует принципам сервисноориентированной архитектуры и повышает степень гибкости, поскольку типы .NET могут изменяться, не затрагивая при этом сетевой контракт.</span><span class="sxs-lookup"><span data-stu-id="30350-220">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="30350-221">В редких случаях имеет смысл сериализовать имена типов .NET, обеспечив таким образом тесное соединение клиента и сервера (подобно технологии удаленного взаимодействия платформы .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="30350-221">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="30350-222">Это не рекомендуемый подход, за исключением редких случаев, которые обычно возникают при переходе на WCF из платформа .NET Framework удаленного взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="30350-222">This is not a recommended practice, except in rare cases that usually occur when migrating to WCF from .NET Framework remoting.</span></span> <span data-ttu-id="30350-223">В этом случае необходимо использовать класс <xref:System.Runtime.Serialization.NetDataContractSerializer> вместо класса <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="30350-223">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="30350-224"><xref:System.Runtime.Serialization.DataContractSerializer> обычно сериализует графы объектов как деревья объектов.</span><span class="sxs-lookup"><span data-stu-id="30350-224">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="30350-225">А именно, если один объект указан неоднократно, он сериализуется неоднократно.</span><span class="sxs-lookup"><span data-stu-id="30350-225">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="30350-226">Рассмотрим, к примеру, экземпляр класса `PurchaseOrder`, имеющий два поля типа Address с именами `billTo` и `shipTo`.</span><span class="sxs-lookup"><span data-stu-id="30350-226">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="30350-227">Если оба поля заданы одному и тому же экземпляру класса Address, после сериализации и десериализации получится два идентичных экземпляра этого класса.</span><span class="sxs-lookup"><span data-stu-id="30350-227">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="30350-228">Это происходит из-за отсутствия стандартного (и поддерживающего взаимодействие) способа представления графов объектов в XML (за исключением стандарта предыдущих версий с кодировкой SOAP, используемого в сериализаторе <xref:System.Xml.Serialization.XmlSerializer>, как указано в предыдущем разделе о `Style` и `Use`).</span><span class="sxs-lookup"><span data-stu-id="30350-228">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="30350-229">Сериализация графов объектов как деревьев имеет определенные преимущества: например, невозможность сериализации графов с циклическими ссылками.</span><span class="sxs-lookup"><span data-stu-id="30350-229">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="30350-230">Иногда требуется переключиться на истинную сериализацию графов объектов, даже несмотря на потерю возможностей взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="30350-230">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="30350-231">Это достигается с помощью сериализатора <xref:System.Runtime.Serialization.DataContractSerializer>, созданного с параметром `preserveObjectReferences`, имеющим значение `true`.</span><span class="sxs-lookup"><span data-stu-id="30350-231">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="30350-232">Иногда встроенных сериализаторов бывает недостаточно для прорабатываемого сценария.</span><span class="sxs-lookup"><span data-stu-id="30350-232">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="30350-233">В большинстве случаев все же сохраняется возможность использовать абстракцию <xref:System.Runtime.Serialization.XmlObjectSerializer>, от которой наследуются оба сериализатора (<xref:System.Runtime.Serialization.DataContractSerializer> и <xref:System.Runtime.Serialization.NetDataContractSerializer>).</span><span class="sxs-lookup"><span data-stu-id="30350-233">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="30350-234">Во всех трех предыдущих случаях (сохранение типов .NET, сохранение графов объектов и сериализация на базе пользовательского сериализатора `XmlObjectSerializer`) требуется подключить пользовательский сериализатор.</span><span class="sxs-lookup"><span data-stu-id="30350-234">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="30350-235">Для этого выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="30350-235">To do this, perform the following steps:</span></span>  
  
1. <span data-ttu-id="30350-236">Самостоятельно составьте код поведения, наследуемого от класса <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="30350-236">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2. <span data-ttu-id="30350-237">Переопределите два метода `CreateSerializer` так, чтобы они возвращали ваш сериализатор (либо <xref:System.Runtime.Serialization.NetDataContractSerializer>, т. е. сериализатор <xref:System.Runtime.Serialization.DataContractSerializer>, у которого для `preserveObjectReferences` задано значение `true`, либо полностью созданный вами сериализатор <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span><span class="sxs-lookup"><span data-stu-id="30350-237">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3. <span data-ttu-id="30350-238">Прежде чем открывать узел службы или создавать канал клиента, удалите существующее поведение <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> и подключите производный пользовательский класс, созданный на предыдущих этапах.</span><span class="sxs-lookup"><span data-stu-id="30350-238">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="30350-239">Дополнительные сведения о дополнительных понятиях сериализации см. в разделе [сериализация и десериализация](serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="30350-239">For more information about advanced serialization concepts, see [Serialization and Deserialization](serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30350-240">См. также</span><span class="sxs-lookup"><span data-stu-id="30350-240">See also</span></span>

- [<span data-ttu-id="30350-241">Использование класса XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="30350-241">Using the XmlSerializer Class</span></span>](using-the-xmlserializer-class.md)
- [<span data-ttu-id="30350-242">Практическое руководство. Включение потоковой передачи</span><span class="sxs-lookup"><span data-stu-id="30350-242">How to: Enable Streaming</span></span>](how-to-enable-streaming.md)
- [<span data-ttu-id="30350-243">Практическое руководство. Создание базового контракта данных для класса или структуры</span><span class="sxs-lookup"><span data-stu-id="30350-243">How to: Create a Basic Data Contract for a Class or Structure</span></span>](how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
