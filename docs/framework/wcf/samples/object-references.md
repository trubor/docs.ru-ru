---
description: 'Дополнительные сведения: ссылки на объекты'
title: Ссылки на объекты
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: ae76cf13b4ccbbde2ad6d5022248bbcfeb263879
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732414"
---
# <a name="object-references"></a><span data-ttu-id="d499a-103">Ссылки на объекты</span><span class="sxs-lookup"><span data-stu-id="d499a-103">Object References</span></span>

<span data-ttu-id="d499a-104">В данном образце показано, как передать объекты по ссылкам между сервером и клиентом.</span><span class="sxs-lookup"><span data-stu-id="d499a-104">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="d499a-105">В этом примере используются смоделированные *социальные сети*.</span><span class="sxs-lookup"><span data-stu-id="d499a-105">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="d499a-106">Социальная сеть состоит из класса `Person`, содержащего список друзей, в котором каждый друг является экземпляром класса `Person` с собственным списком друзей.</span><span class="sxs-lookup"><span data-stu-id="d499a-106">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="d499a-107">Таким образом создается граф объектов.</span><span class="sxs-lookup"><span data-stu-id="d499a-107">This creates a graph of objects.</span></span> <span data-ttu-id="d499a-108">Служба предоставляет операции для этих социальных сетей.</span><span class="sxs-lookup"><span data-stu-id="d499a-108">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="d499a-109">В этом образце служба размещается в службах IIS, а клиентом является консольное приложение (EXE).</span><span class="sxs-lookup"><span data-stu-id="d499a-109">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d499a-110">Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="d499a-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="d499a-111">Служба</span><span class="sxs-lookup"><span data-stu-id="d499a-111">Service</span></span>  

 <span data-ttu-id="d499a-112">К классу `Person` применен атрибут<xref:System.Runtime.Serialization.DataContractAttribute>. Полю <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> присвоено значение `true`, объявляющее его ссылочным типом.</span><span class="sxs-lookup"><span data-stu-id="d499a-112">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="d499a-113">Ко всем свойствам применяется атрибут <xref:System.Runtime.Serialization.DataMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d499a-113">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
```csharp
[DataContract(IsReference=true)]  
public class Person  
{  
    string name;  
    string location;  
    string gender;  
    int age;  
    List<Person> friends;  
    [DataMember()]  
    public string Name  
    {  
        get { return name; }  
        set { name = value; }  
    }  
    [DataMember()]  
    public string Location  
    {  
        get { return location; }  
        set { location = value; }  
    }  
    [DataMember()]  
    public string Gender  
    {  
        get { return gender; }  
        set { gender = value; }  
    }  
…  
}  
```  
  
 <span data-ttu-id="d499a-114">Операция `GetPeopleInNetwork` принимает параметр типа `Person` и возвращает всех людей в сети; то есть всех людей в списке `friends`, друзей друзей и так далее без повторений.</span><span class="sxs-lookup"><span data-stu-id="d499a-114">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="d499a-115">Операция `GetMutualFriends` принимает параметр типа `Person` и возвращает всех друзей в списке, которые также имеют этого человека в их списке `friends`.</span><span class="sxs-lookup"><span data-stu-id="d499a-115">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
```csharp
public List<Person> GetMutualFriends(Person p)  
{  
    List<Person> mutual = new List<Person>();  
    foreach (Person friend in p.Friends)  
    {  
        if (friend.Friends.Contains(p))  
            mutual.Add(friend);  
    }  
    return mutual;  
}  
```  
  
 <span data-ttu-id="d499a-116">Операция `GetCommonFriends` принимает список типа `Person`.</span><span class="sxs-lookup"><span data-stu-id="d499a-116">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="d499a-117">Предполагается, что в списке присутствует два объекта `Person`.</span><span class="sxs-lookup"><span data-stu-id="d499a-117">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="d499a-118">Операция возвращает список объектов `Person`, находящихся в списках `friends` обоих объектов `Person`, в списке ввода.</span><span class="sxs-lookup"><span data-stu-id="d499a-118">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
```csharp
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a><span data-ttu-id="d499a-119">Клиент</span><span class="sxs-lookup"><span data-stu-id="d499a-119">Client</span></span>  

 <span data-ttu-id="d499a-120">Прокси клиента создается с помощью функции **Добавление ссылки на службу** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d499a-120">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="d499a-121">Создается социальная сеть, состоящая из пяти объектов `Person`.</span><span class="sxs-lookup"><span data-stu-id="d499a-121">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="d499a-122">Клиент вызывает каждый из трех методов службы.</span><span class="sxs-lookup"><span data-stu-id="d499a-122">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d499a-123">Настройка, сборка и выполнение образца</span><span class="sxs-lookup"><span data-stu-id="d499a-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d499a-124">Убедитесь, что вы выполнили [однократную процедуру настройки для Windows Communication Foundation примеров](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d499a-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d499a-125">Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d499a-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d499a-126">Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d499a-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d499a-127">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="d499a-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d499a-128">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="d499a-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d499a-129">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="d499a-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d499a-130">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="d499a-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="d499a-131">См. также</span><span class="sxs-lookup"><span data-stu-id="d499a-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="d499a-132">Справочные сведения о взаимодействии объектов</span><span class="sxs-lookup"><span data-stu-id="d499a-132">Interoperable Object References</span></span>](../feature-details/interoperable-object-references.md)
