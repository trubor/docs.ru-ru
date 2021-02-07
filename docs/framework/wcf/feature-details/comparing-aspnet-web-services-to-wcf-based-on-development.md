---
description: 'Дополнительные сведения: сравнение веб-служб ASP.NET с WCF на основе разработки'
title: Сравнение веб-служб ASP.NET с веб-службами на основе WCF по процессу разработки
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: fa9db35070bdde32d509f0e9c25dbf179d64da32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743464"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="d367e-103">Сравнение веб-служб ASP.NET с веб-службами на основе WCF по процессу разработки</span><span class="sxs-lookup"><span data-stu-id="d367e-103">Comparing ASP.NET Web Services to WCF Based on Development</span></span>

<span data-ttu-id="d367e-104">Windows Communication Foundation (WCF) имеет режим совместимости ASP.NET, позволяющий программировать и настраивать приложения WCF, например веб-службы ASP.NET, и имитировать их поведение.</span><span class="sxs-lookup"><span data-stu-id="d367e-104">Windows Communication Foundation (WCF) has an ASP.NET compatibility mode option to enable WCF applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="d367e-105">В следующих разделах сравниваются веб-службы ASP.NET и WCF в зависимости от того, что требуется для разработки приложений с использованием обеих технологий.</span><span class="sxs-lookup"><span data-stu-id="d367e-105">The following sections compare ASP.NET Web services and WCF based on what is required to develop applications using both technologies.</span></span>

## <a name="data-representation"></a><span data-ttu-id="d367e-106">Представление данных</span><span class="sxs-lookup"><span data-stu-id="d367e-106">Data Representation</span></span>

<span data-ttu-id="d367e-107">Разработка веб-службы с помощью ASP.NET обычно начинается с определения сложных типов данных, которые будет использовать служба.</span><span class="sxs-lookup"><span data-stu-id="d367e-107">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="d367e-108">ASP.NET предполагает использование сериализатора <xref:System.Xml.Serialization.XmlSerializer> для преобразования представленных типами .NET Framework данных в XML для передачи службе или от службы и для преобразования полученных в виде XML данных в объекты .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d367e-108">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="d367e-109">Определение сложных типов данных, которые будет использовать служба ASP.NET, требует определения классов .NET Framework, которые <xref:System.Xml.Serialization.XmlSerializer> может сериализовать в XML и из XML.</span><span class="sxs-lookup"><span data-stu-id="d367e-109">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="d367e-110">Такие классы могут быть написаны вручную или сформированы из определений типов в схеме XML с помощью утилиты командной строки для поддержки схем XML/типов данных (xsd.exe).</span><span class="sxs-lookup"><span data-stu-id="d367e-110">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>

<span data-ttu-id="d367e-111">Ниже перечислены основные моменты, которые необходимо знать для определения классов .NET Framework, которые <xref:System.Xml.Serialization.XmlSerializer> сможет сериализовать в XML и из XML.</span><span class="sxs-lookup"><span data-stu-id="d367e-111">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>

- <span data-ttu-id="d367e-112">В XML преобразуются только открытые поля и свойства объектов .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d367e-112">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>

- <span data-ttu-id="d367e-113">Экземпляры классов коллекций могут быть сериализованы в XML только при условии реализации классами интерфейса <xref:System.Collections.IEnumerable> или <xref:System.Collections.ICollection>.</span><span class="sxs-lookup"><span data-stu-id="d367e-113">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>

- <span data-ttu-id="d367e-114">Классы, реализующие интерфейс <xref:System.Collections.IDictionary>, такие как <xref:System.Collections.Hashtable>, не могут быть сериализованы в XML.</span><span class="sxs-lookup"><span data-stu-id="d367e-114">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>

- <span data-ttu-id="d367e-115">Пространство имен <xref:System.Xml.Serialization> содержит огромное множество типов атрибутов, которые можно добавлять в классы .NET Framework и их члены для управления тем, как экземпляры класса будут представлены в XML.</span><span class="sxs-lookup"><span data-stu-id="d367e-115">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>

<span data-ttu-id="d367e-116">Разработка приложений WCF обычно начинается с определения сложных типов.</span><span class="sxs-lookup"><span data-stu-id="d367e-116">WCF application development usually also begins with the definition of complex types.</span></span> <span data-ttu-id="d367e-117">WCF может быть создана для использования тех же типов платформа .NET Framework, что и веб-службы ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d367e-117">WCF can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>

<span data-ttu-id="d367e-118">WCF <xref:System.Runtime.Serialization.DataContractAttribute> и <xref:System.Runtime.Serialization.DataMemberAttribute> может быть добавлена к типам платформа .NET Framework, чтобы указать, что экземпляры типа должны быть сериализованы в XML, а какие конкретные поля или свойства типа должны быть сериализованы, как показано в следующем образце кода.</span><span class="sxs-lookup"><span data-stu-id="d367e-118">The WCF<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>

```csharp
//Example One:
[DataContract]
public class LineItem
{
    [DataMember]
    public string ItemNumber;
    [DataMember]
    public decimal Quantity;
    [DataMember]
    public decimal UnitPrice;
}

//Example Two:
public class LineItem
{
    [DataMember]
    private string itemNumber;
    [DataMember]
    private decimal quantity;
    [DataMember]
    private decimal unitPrice;

    public string ItemNumber
    {
      get
      {
          return this.itemNumber;
      }

      set
      {
          this.itemNumber = value;
      }
    }

    public decimal Quantity
    {
        get
        {
            return this.quantity;
        }

        set
        {
            this.quantity = value;
        }
    }

    public decimal UnitPrice
    {
      get
      {
          return this.unitPrice;
      }

      set
      {
          this.unitPrice = value;
      }
    }
}

//Example Three:
public class LineItem
{
     private string itemNumber;
     private decimal quantity;
     private decimal unitPrice;

     [DataMember]
     public string ItemNumber
     {
       get
       {
          return this.itemNumber;
       }

       set
       {
           this.itemNumber = value;
       }
     }

     [DataMember]
     public decimal Quantity
     {
          get
          {
              return this.quantity;
          }

          set
          {
             this.quantity = value;
          }
     }

     [DataMember]
     public decimal UnitPrice
     {
          get
          {
              return this.unitPrice;
          }

          set
          {
              this.unitPrice = value;
          }
     }
}
```

<span data-ttu-id="d367e-119">Атрибут <xref:System.Runtime.Serialization.DataContractAttribute> означает, что ноль или более полей или свойств типа должны быть сериализованы, тогда как атрибут <xref:System.Runtime.Serialization.DataMemberAttribute> указывает, что определенное поле или свойство должно быть сериализовано.</span><span class="sxs-lookup"><span data-stu-id="d367e-119">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="d367e-120">Атрибут <xref:System.Runtime.Serialization.DataContractAttribute> может быть применен к классу или структуре.</span><span class="sxs-lookup"><span data-stu-id="d367e-120">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="d367e-121">Атрибут <xref:System.Runtime.Serialization.DataMemberAttribute> может быть применен к полю или свойству, причем поля и свойства, к которым применяется атрибут, могут быть как открытыми, так и закрытыми.</span><span class="sxs-lookup"><span data-stu-id="d367e-121">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="d367e-122">Экземпляры типов, к которым применен объект, <xref:System.Runtime.Serialization.DataContractAttribute> называются контрактами данных в WCF.</span><span class="sxs-lookup"><span data-stu-id="d367e-122">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in WCF.</span></span> <span data-ttu-id="d367e-123">Они сериализуются в XML с помощью сериализатора <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d367e-123">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

<span data-ttu-id="d367e-124">Ниже перечислены важные различия между использованием сериализатора <xref:System.Runtime.Serialization.DataContractSerializer> и использованием сериализатора <xref:System.Xml.Serialization.XmlSerializer> и различных атрибутов из пространства имен <xref:System.Xml.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="d367e-124">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>

- <span data-ttu-id="d367e-125">Сериализатор <xref:System.Xml.Serialization.XmlSerializer> и атрибуты из пространства имен <xref:System.Xml.Serialization> предназначены для того, чтобы разработчик мог сопоставлять типы .NET Framework с любым допустимым типом, определенным в схеме XML, и как таковые позволяют очень точно управлять тем, как тип будет представлен в XML.</span><span class="sxs-lookup"><span data-stu-id="d367e-125">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="d367e-126">Сериализатор <xref:System.Runtime.Serialization.DataContractSerializer> и атрибуты <xref:System.Runtime.Serialization.DataContractAttribute> и <xref:System.Runtime.Serialization.DataMemberAttribute> позволяют контролировать представление типа в XML в очень небольшой степени.</span><span class="sxs-lookup"><span data-stu-id="d367e-126">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="d367e-127">Можно указать только пространства имен и имена, используемые для представления типа и его полей или свойств в XML, а также последовательности, в которой поля и свойства будут идти в XML.</span><span class="sxs-lookup"><span data-stu-id="d367e-127">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>

  ```csharp
  [DataContract(
  Namespace="urn:Contoso:2006:January:29",
  Name="LineItem")]
  public class LineItem
  {
        [DataMember(Name="ItemNumber",IsRequired=true,Order=0)]
        public string itemNumber;
        [DataMember(Name="Quantity",IsRequired=false,Order = 1)]
        public decimal quantity;
        [DataMember(Name="Price",IsRequired=false,Order = 2)]
        public decimal unitPrice;
  }
  ```

  <span data-ttu-id="d367e-128">Все остальные аспекты структуры XML-данных, используемых для представления типа .NET, определяет <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d367e-128">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

- <span data-ttu-id="d367e-129">Благодаря ограниченности контроля разработчика над представлением типа в XML процесс сериализации с помощью <xref:System.Runtime.Serialization.DataContractSerializer> весьма предсказуем и, следовательно, его легче оптимизировать.</span><span class="sxs-lookup"><span data-stu-id="d367e-129">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="d367e-130">Практическое преимущество такого принципа работы <xref:System.Runtime.Serialization.DataContractSerializer> состоит в повышении производительности примерно на десять процентов.</span><span class="sxs-lookup"><span data-stu-id="d367e-130">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>

- <span data-ttu-id="d367e-131">Атрибуты, предназначенные для использования в сочетании с сериализатором <xref:System.Xml.Serialization.XmlSerializer>, не указывают, какие поля или свойства сериализуются в XML, тогда как атрибут <xref:System.Runtime.Serialization.DataMemberAttribute>, предназначенный для использования в сочетании с сериализатором <xref:System.Runtime.Serialization.DataContractSerializer>, явно показывает, какие поля или свойства сериализуются.</span><span class="sxs-lookup"><span data-stu-id="d367e-131">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="d367e-132">Следовательно, контракты данных представляют собой явные контракты о структуре данных, которые будет отправлять и получать приложение.</span><span class="sxs-lookup"><span data-stu-id="d367e-132">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>

- <span data-ttu-id="d367e-133">Сериализатор <xref:System.Xml.Serialization.XmlSerializer> может преобразовывать в XML только открытые члены объекта .NET; сериализатор <xref:System.Runtime.Serialization.DataContractSerializer> может преобразовывать в XML члены объектов независимо от модификаторов доступа этих членов.</span><span class="sxs-lookup"><span data-stu-id="d367e-133">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>

- <span data-ttu-id="d367e-134">Вследствие способности сериализовать в XML закрытые члены типов для сериализатора <xref:System.Runtime.Serialization.DataContractSerializer> характерно меньшее количество ограничений на типы .NET, которые он может сериализовать в XML.</span><span class="sxs-lookup"><span data-stu-id="d367e-134">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="d367e-135">В частности, он способен преобразовывать в XML такие типы, как <xref:System.Collections.Hashtable>, который реализует интерфейс <xref:System.Collections.IDictionary>.</span><span class="sxs-lookup"><span data-stu-id="d367e-135">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="d367e-136">Сериализатор <xref:System.Runtime.Serialization.DataContractSerializer> со значительно большей вероятностью сможет сериализовать в XML экземпляры любого уже существующего типа .NET без внесения в тип изменений или разработки для него оболочки.</span><span class="sxs-lookup"><span data-stu-id="d367e-136">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>

- <span data-ttu-id="d367e-137">Другим следствием способности сериализатора <xref:System.Runtime.Serialization.DataContractSerializer> получать доступ к закрытым членам типа является то, что ему требуется полное доверие, тогда как сериализатор <xref:System.Xml.Serialization.XmlSerializer> этого не требует.</span><span class="sxs-lookup"><span data-stu-id="d367e-137">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="d367e-138">Разрешение на доступ к коду полного доверия обеспечивает полный доступ ко всем ресурсам на компьютере, к которым можно получить доступ с помощью учетных данных, с которыми выполняется код.</span><span class="sxs-lookup"><span data-stu-id="d367e-138">The Full Trust code access permission gives complete access to all resources on a machine that can be accessed using the credentials under which the code is executing.</span></span> <span data-ttu-id="d367e-139">Этот параметр следует использовать с осторожностью, так как полностью доверенный код получает доступ ко всем ресурсам на компьютере.</span><span class="sxs-lookup"><span data-stu-id="d367e-139">This option should be used with care as fully trusted code accesses all resources on your machine.</span></span>

- <span data-ttu-id="d367e-140">Сериализатор <xref:System.Runtime.Serialization.DataContractSerializer> предусматривает некоторую поддержку управления версиями.</span><span class="sxs-lookup"><span data-stu-id="d367e-140">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>

  - <span data-ttu-id="d367e-141">Атрибут <xref:System.Runtime.Serialization.DataMemberAttribute> имеет свойство <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>, которому можно присваивать значение false для добавляемых в новые версии (т. е. отсутствовавших в предыдущих версиях) контракта данных членов, что позволяет приложениям с более новой версией контракта обрабатывать более ранние версии типа.</span><span class="sxs-lookup"><span data-stu-id="d367e-141">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>

  - <span data-ttu-id="d367e-142">Реализуя в контракте данных интерфейс <xref:System.Runtime.Serialization.IExtensibleDataObject>, разработчик может позволить сериализатору <xref:System.Runtime.Serialization.DataContractSerializer> передавать члены, определенные в более новых версиях контракта данных, через приложения с более ранними версиями контракта.</span><span class="sxs-lookup"><span data-stu-id="d367e-142">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>

<span data-ttu-id="d367e-143">Несмотря на все различия, XML-данные, в которые <xref:System.Xml.Serialization.XmlSerializer> сериализует тип, по умолчанию семантически идентичны XML-данным, в которые сериализует тип <xref:System.Runtime.Serialization.DataContractSerializer>, при условии, что пространство имен для XML определено явным образом.</span><span class="sxs-lookup"><span data-stu-id="d367e-143">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="d367e-144">Следующий класс, имеющий атрибуты для использования с обоими сериализаторами, преобразуется в семантически идентичный XML с помощью <xref:System.Xml.Serialization.XmlSerializer> и <xref:System.Runtime.Serialization.DataContractAttribute> :</span><span class="sxs-lookup"><span data-stu-id="d367e-144">The following class, which has attributes for use with both of the serializers, is translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>

```csharp
[Serializable]
[XmlRoot(Namespace="urn:Contoso:2006:January:29")]
[DataContract(Namespace="urn:Contoso:2006:January:29")]
public class LineItem
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}
```

<span data-ttu-id="d367e-145">Пакет средств разработки программного обеспечения (SDK) для Windows включает программу командной строки, которая называется [служебной программой для метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d367e-145">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="d367e-146">Как и средство xsd.exe, используемое с веб-службами ASP.NET, Svcutil.exe может формировать определения типов данных .NET из схемы XML.</span><span class="sxs-lookup"><span data-stu-id="d367e-146">Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="d367e-147">Типы являются контрактами данных, если сериализатор <xref:System.Runtime.Serialization.DataContractSerializer> способен выдать XML-данные в формате, определенном схемой XML; в противном случае они предназначены для сериализации с помощью <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d367e-147">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="d367e-148">Svcutil.exe также может формировать XML-схему из контрактов данных с помощью `dataContractOnly` переключателя.</span><span class="sxs-lookup"><span data-stu-id="d367e-148">Svcutil.exe can also generate an XML schema from data contracts by using its `dataContractOnly` switch.</span></span>

> [!NOTE]
> <span data-ttu-id="d367e-149">Несмотря на то, что ASP.NET веб-службы используют <xref:System.Xml.Serialization.XmlSerializer> , и режим СОВМЕСТИМОСТИ wcf ASP.NET делает службы WCF более сходными с поведением веб-служб ASP.NET, параметр совместимости ASP.NET не ограничивает один для использования <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="d367e-149">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and WCF ASP.NET compatibility mode makes WCF services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="d367e-150">Сериализатор <xref:System.Runtime.Serialization.DataContractSerializer> можно использовать и для служб, выполняемых в режиме совместимости с ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d367e-150">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>

## <a name="service-development"></a><span data-ttu-id="d367e-151">Разработка служб</span><span class="sxs-lookup"><span data-stu-id="d367e-151">Service Development</span></span>

<span data-ttu-id="d367e-152">Для разработки службы с использованием ASP.NET обычно требовалось добавлять атрибут <xref:System.Web.Services.WebService> в класс и атрибут <xref:System.Web.Services.WebMethodAttribute> во все методы этого класса, которые являются операциями службы:</span><span class="sxs-lookup"><span data-stu-id="d367e-152">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>

```csharp
[WebService]
public class Service : T:System.Web.Services.WebService
{
    [WebMethod]
    public string Echo(string input)
    {
       return input;
    }
}
```

<span data-ttu-id="d367e-153">В ASP.NET 2.0 появилась возможность добавления атрибутов <xref:System.Web.Services.WebService> и <xref:System.Web.Services.WebMethodAttribute> в интерфейс, а не в класс, и написания класса для реализации этого интерфейса:</span><span class="sxs-lookup"><span data-stu-id="d367e-153">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>

```csharp
[WebService]
public interface IEcho
{
    [WebMethod]
    string Echo(string input);
}

public class Service : IEcho
{

   public string Echo(string input)
   {
        return input;
    }
}
```

<span data-ttu-id="d367e-154">Этот вариант является предпочтительным, так как интерфейс с атрибутом <xref:System.Web.Services.WebService> составляет контракт для операций, выполняемых службой, доступный для повторного использования в различных классах, которые могут реализовывать этот же контракт другими способами.</span><span class="sxs-lookup"><span data-stu-id="d367e-154">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>

<span data-ttu-id="d367e-155">Служба WCF предоставляется путем определения одной или нескольких конечных точек WCF.</span><span class="sxs-lookup"><span data-stu-id="d367e-155">A WCF service is provided by defining one or more WCF endpoints.</span></span> <span data-ttu-id="d367e-156">Конечная точка определяется адресом, привязкой и контрактом службы.</span><span class="sxs-lookup"><span data-stu-id="d367e-156">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="d367e-157">Адрес определяет местонахождение службы.</span><span class="sxs-lookup"><span data-stu-id="d367e-157">The address defines where the service is located.</span></span> <span data-ttu-id="d367e-158">Привязка задает способ обмена данными со службой.</span><span class="sxs-lookup"><span data-stu-id="d367e-158">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="d367e-159">Контракт службы определяет операции, которые может выполнять служба.</span><span class="sxs-lookup"><span data-stu-id="d367e-159">The service contract defines the operations that the service can perform.</span></span>

<span data-ttu-id="d367e-160">Контракт службы обычно определяется в первую очередь, путем добавления атрибутов <xref:System.ServiceModel.ServiceContractAttribute> и <xref:System.ServiceModel.OperationContractAttribute> в интерфейс:</span><span class="sxs-lookup"><span data-stu-id="d367e-160">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>

```csharp
[ServiceContract]
public interface IEcho
{
     [OperationContract]
     string Echo(string input);
}
```

<span data-ttu-id="d367e-161"><xref:System.ServiceModel.ServiceContractAttribute>Указывает, что интерфейс определяет контракт службы WCF, а также <xref:System.ServiceModel.OperationContractAttribute> указывает, какие из методов интерфейса определяют операции контракта службы.</span><span class="sxs-lookup"><span data-stu-id="d367e-161">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a WCF service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>

<span data-ttu-id="d367e-162">После определения контракта службы он реализуется в классе - путем реализации в классе интерфейса, которым определяется контракт службы:</span><span class="sxs-lookup"><span data-stu-id="d367e-162">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>

```csharp
public class Service : IEcho
{
    public string Echo(string input)
    {
       return input;
    }
}
```

<span data-ttu-id="d367e-163">Класс, реализующий контракт службы, называется типом службы в WCF.</span><span class="sxs-lookup"><span data-stu-id="d367e-163">A class that implements a service contract is referred to as a service type in WCF.</span></span>

<span data-ttu-id="d367e-164">Следующий шаг - связать адрес и привязку с типом службы.</span><span class="sxs-lookup"><span data-stu-id="d367e-164">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="d367e-165">Это обычно делается в файле конфигурации путем непосредственного редактирования файла или с помощью редактора конфигурации, предоставленного в WCF.</span><span class="sxs-lookup"><span data-stu-id="d367e-165">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with WCF.</span></span> <span data-ttu-id="d367e-166">Ниже приведен пример файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="d367e-166">Here is an example of a configuration file.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
     <system.serviceModel>
      <services>
      <service name="Service ">
       <endpoint
        address="EchoService"
        binding="basicHttpBinding"
        contract="IEchoService "/>
      </service>
      </services>
     </system.serviceModel>
</configuration>
```

<span data-ttu-id="d367e-167">Привязка задает набор протоколов для обмена данными с приложением.</span><span class="sxs-lookup"><span data-stu-id="d367e-167">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="d367e-168">В следующей таблице перечислены предоставляемые системой привязки, соответствующие стандартным вариантам.</span><span class="sxs-lookup"><span data-stu-id="d367e-168">The following table lists the system-provided bindings that represent common options.</span></span>

|<span data-ttu-id="d367e-169">Имя</span><span class="sxs-lookup"><span data-stu-id="d367e-169">Name</span></span>|<span data-ttu-id="d367e-170">Назначение</span><span class="sxs-lookup"><span data-stu-id="d367e-170">Purpose</span></span>|
|----------|-------------|
|<span data-ttu-id="d367e-171">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d367e-171">BasicHttpBinding</span></span>|<span data-ttu-id="d367e-172">Взаимодействие с веб-службами и клиентами, поддерживающими спецификации WS-BasicProfile 1.1 и Basic Security Profile 1.0.</span><span class="sxs-lookup"><span data-stu-id="d367e-172">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|
|<span data-ttu-id="d367e-173">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d367e-173">WSHttpBinding</span></span>|<span data-ttu-id="d367e-174">Взаимодействие с веб-службами и клиентами, поддерживающими протоколы WS-\* через HTTP.</span><span class="sxs-lookup"><span data-stu-id="d367e-174">Interoperability with Web services and clients that support the WS-\* protocols over HTTP.</span></span>|
|<span data-ttu-id="d367e-175">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d367e-175">WSDualHttpBinding</span></span>|<span data-ttu-id="d367e-176">Дуплексная связь по протоколу HTTP, при которой получатель первоначального сообщения не отвечает непосредственно первоначальному отправителю, но может передавать любое количество ответов в течение некоторого периода времени, используя HTTP в соответствии с протоколами WS-\*.</span><span class="sxs-lookup"><span data-stu-id="d367e-176">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-\* protocols.</span></span>|
|<span data-ttu-id="d367e-177">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="d367e-177">WSFederationBinding</span></span>|<span data-ttu-id="d367e-178">Связь по протоколу HTTP, при которой доступом к ресурсам службы можно управлять на основе учетных данных, выданных явно идентифицированным поставщиком учетных данных.</span><span class="sxs-lookup"><span data-stu-id="d367e-178">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|
|<span data-ttu-id="d367e-179">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="d367e-179">NetTcpBinding</span></span>|<span data-ttu-id="d367e-180">Безопасная, надежная и высокопроизводительная связь между программными сущностями WCF по сети.</span><span class="sxs-lookup"><span data-stu-id="d367e-180">Secure, reliable, high-performance communication between WCF software entities across a network.</span></span>|
|<span data-ttu-id="d367e-181">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="d367e-181">NetNamedPipeBinding</span></span>|<span data-ttu-id="d367e-182">Безопасная, надежная и высокопроизводительная связь между сущностями программного обеспечения WCF на одном компьютере.</span><span class="sxs-lookup"><span data-stu-id="d367e-182">Secure, reliable, high-performance communication between WCF software entities on the same machine.</span></span>|
|<span data-ttu-id="d367e-183">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="d367e-183">NetMsmqBinding</span></span>|<span data-ttu-id="d367e-184">Взаимодействие между сущностями программного обеспечения WCF с помощью MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d367e-184">Communication between WCF software entities by using MSMQ.</span></span>|
|<span data-ttu-id="d367e-185">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="d367e-185">MsmqIntegrationBinding</span></span>|<span data-ttu-id="d367e-186">Обмен данными между программной сущностью WCF и другой сущностью программы с помощью MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d367e-186">Communication between a WCF software entity and another software entity by using MSMQ.</span></span>|
|<span data-ttu-id="d367e-187">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="d367e-187">NetPeerTcpBinding</span></span>|<span data-ttu-id="d367e-188">Взаимодействие между сущностями программного обеспечения WCF с помощью одноранговых сетей Windows.</span><span class="sxs-lookup"><span data-stu-id="d367e-188">Communication between WCF software entities by using Windows Peer-to-Peer Networking.</span></span>|

<span data-ttu-id="d367e-189">Предоставляемая системой привязка <xref:System.ServiceModel.BasicHttpBinding> включает набор протоколов, поддерживаемых веб-службами ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d367e-189">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>

<span data-ttu-id="d367e-190">Пользовательские привязки для приложений WCF легко определяются как коллекции классов элементов привязки, которые WCF использует для реализации отдельных протоколов.</span><span class="sxs-lookup"><span data-stu-id="d367e-190">Custom bindings for WCF applications are easily defined as collections of the binding element classes that WCF uses to implement individual protocols.</span></span> <span data-ttu-id="d367e-191">Можно писать новые элементы привязки для представления дополнительных протоколов.</span><span class="sxs-lookup"><span data-stu-id="d367e-191">New binding elements can be written to represent additional protocols.</span></span>

<span data-ttu-id="d367e-192">Внутреннее поведение типов служб можно корректировать, используя свойства семейства классов, называемых поведениями.</span><span class="sxs-lookup"><span data-stu-id="d367e-192">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="d367e-193">В следующем примере с помощью класса <xref:System.ServiceModel.ServiceBehaviorAttribute> указывается, что тип службы должен быть многопоточным.</span><span class="sxs-lookup"><span data-stu-id="d367e-193">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple)]
public class DerivativesCalculatorServiceType: IDerivativesCalculator
```

<span data-ttu-id="d367e-194">Некоторые поведения, такие как <xref:System.ServiceModel.ServiceBehaviorAttribute>, представляют собой атрибуты.</span><span class="sxs-lookup"><span data-stu-id="d367e-194">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="d367e-195">Другие, имеющие свойства, которые может потребоваться задавать администраторам, могут быть изменены в конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="d367e-195">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>

<span data-ttu-id="d367e-196">При программировании типов служб часто используется класс <xref:System.ServiceModel.OperationContext>.</span><span class="sxs-lookup"><span data-stu-id="d367e-196">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="d367e-197">Его статическое свойство <xref:System.ServiceModel.OperationContext.Current%2A> обеспечивает доступ к информации о контексте, в котором выполняется операция.</span><span class="sxs-lookup"><span data-stu-id="d367e-197">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="d367e-198"><xref:System.ServiceModel.OperationContext> аналогичен классам <xref:System.Web.HttpContext> и <xref:System.EnterpriseServices.ContextUtil>.</span><span class="sxs-lookup"><span data-stu-id="d367e-198"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>

## <a name="hosting"></a><span data-ttu-id="d367e-199">Hosting</span><span class="sxs-lookup"><span data-stu-id="d367e-199">Hosting</span></span>

<span data-ttu-id="d367e-200">Веб-службы ASP.NET компилируются в сборку библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="d367e-200">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="d367e-201">Формируется файл, называемый файлом службы, который имеет расширение ASMX и содержит директиву `@ WebService`. Эта директива идентифицирует класс, содержащий код для службы и сборку, в которой он находится.</span><span class="sxs-lookup"><span data-stu-id="d367e-201">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>

`<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>`

<span data-ttu-id="d367e-202">Файл службы копируется в корень приложения ASP.NET в службах IIS, а сборка копируется в подкаталог \bin этого корня приложения.</span><span class="sxs-lookup"><span data-stu-id="d367e-202">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="d367e-203">После этого приложение будет доступно по URL-адресу файла службы в корне приложения.</span><span class="sxs-lookup"><span data-stu-id="d367e-203">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>

<span data-ttu-id="d367e-204">Службы WCF могут быть размещены в IIS 5,1 или 6,0, службе активации Windows (WAS), входящей в состав IIS 7,0, и в любом приложении .NET.</span><span class="sxs-lookup"><span data-stu-id="d367e-204">WCF services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="d367e-205">Чтобы службу можно было разместить в IIS 5.1 или 6.0, в качестве транспортного протокола связи она должна использовать HTTP.</span><span class="sxs-lookup"><span data-stu-id="d367e-205">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>

<span data-ttu-id="d367e-206">Чтобы разместить службу в IIS 5.1, 6.0 или в WAS, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="d367e-206">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>

1. <span data-ttu-id="d367e-207">Скомпилируйте тип службы в сборку библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="d367e-207">Compile the service type into a class library assembly.</span></span>

2. <span data-ttu-id="d367e-208">Создайте файл службы с расширением SVC с директивой `@ ServiceHost` для идентификации типа службы:</span><span class="sxs-lookup"><span data-stu-id="d367e-208">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>

    `<%@ServiceHost language="c#" Service="MyService" %>`

3. <span data-ttu-id="d367e-209">Скопируйте файл службы в виртуальный каталог, а сборку в подкаталог \bin этого виртуального каталога.</span><span class="sxs-lookup"><span data-stu-id="d367e-209">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>

4. <span data-ttu-id="d367e-210">Скопируйте файл конфигурации в виртуальный каталог и назовите его Web.config.</span><span class="sxs-lookup"><span data-stu-id="d367e-210">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>

<span data-ttu-id="d367e-211">После этого приложение будет доступно по URL-адресу файла службы в корне приложения.</span><span class="sxs-lookup"><span data-stu-id="d367e-211">The application is then accessible by using the URL of the service file in the application root.</span></span>

<span data-ttu-id="d367e-212">Чтобы разместить службу WCF в приложении .NET, Скомпилируйте тип службы в сборку библиотеки классов, на которую ссылается приложение, и запрограммировать приложение для размещения службы с помощью <xref:System.ServiceModel.ServiceHost> класса.</span><span class="sxs-lookup"><span data-stu-id="d367e-212">To host a WCF service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="d367e-213">Ниже приведен простой пример требуемого программирования:</span><span class="sxs-lookup"><span data-stu-id="d367e-213">The following is an example of the basic programming required:</span></span>

```csharp
string httpBaseAddress = "http://www.contoso.com:8000/";
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";

Uri httpBaseAddressUri = new Uri(httpBaseAddress);
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);

Uri[] baseAddresses = new Uri[] {
 httpBaseAddressUri,
 tcpBaseAddressUri};

using(ServiceHost host = new ServiceHost(
typeof(Service), //"Service" is the name of the service type baseAddresses))
{
     host.Open();

     […] //Wait to receive messages
     host.Close();
}
```

<span data-ttu-id="d367e-214">В этом примере показано задание адресов для одного или нескольких транспортных протоколов при построении объекта <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="d367e-214">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="d367e-215">Эти адреса называются базовыми адресами.</span><span class="sxs-lookup"><span data-stu-id="d367e-215">These addresses are referred to as base addresses.</span></span>

<span data-ttu-id="d367e-216">Адрес, предоставленный для любой конечной точки службы WCF, является адресом относительно базового адреса узла конечной точки.</span><span class="sxs-lookup"><span data-stu-id="d367e-216">The address provided for any endpoint of a WCF service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="d367e-217">Узел размещения может иметь по одному базовому адресу для каждого транспортного протокола связи.</span><span class="sxs-lookup"><span data-stu-id="d367e-217">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="d367e-218">В приведенном выше примере файла конфигурации выбранная для конечной точки привязка <xref:System.ServiceModel.BasicHttpBinding> предполагает использование в качестве транспорта протокола HTTP, поэтому адрес конечной точки — `EchoService`— рассматривается относительно базового HTTP-адреса узла.</span><span class="sxs-lookup"><span data-stu-id="d367e-218">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="d367e-219">В случае размещения в предыдущем примере основным адресом HTTP является `http://www.contoso.com:8000/` .</span><span class="sxs-lookup"><span data-stu-id="d367e-219">In the case of the host in the preceding example, the HTTP base address is `http://www.contoso.com:8000/`.</span></span> <span data-ttu-id="d367e-220">Для службы, размещенной в IIS или WAS, базовый адрес - это URL-адрес файла службы для этой службы.</span><span class="sxs-lookup"><span data-stu-id="d367e-220">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>

<span data-ttu-id="d367e-221">Для использования параметра режима совместимости WCF ASP.NET можно использовать только службы, размещенные в IIS или WAS, которые настроены с протоколом HTTP в качестве транспортного протокола.</span><span class="sxs-lookup"><span data-stu-id="d367e-221">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use WCF ASP.NET compatibility mode option.</span></span> <span data-ttu-id="d367e-222">Для включения этого режима необходимо выполнить следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="d367e-222">Turning that option on requires the following steps.</span></span>

1. <span data-ttu-id="d367e-223">Программист должен добавить атрибут <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> в тип службы и указать, что режим совместимости с ASP.NET допускается либо требуется.</span><span class="sxs-lookup"><span data-stu-id="d367e-223">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>

    ```csharp
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(
          RequirementsMode=AspNetCompatibilityRequirementsMode.Require)]
    public class DerivativesCalculatorServiceType: IDerivativesCalculator
    ```

2. <span data-ttu-id="d367e-224">Администратор должен настроить приложение на использование режима совместимости с ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d367e-224">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>

    ```xml
    <configuration>
         <system.serviceModel>
          <services>
          […]
          </services>
          <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
        </system.serviceModel>
    </configuration>
    ```

    <span data-ttu-id="d367e-225">Приложения WCF также можно настроить на использование ASMX в качестве расширения для файлов служб, а не SVC.</span><span class="sxs-lookup"><span data-stu-id="d367e-225">WCF applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>

    ```xml
    <system.web>
         <compilation>
          <compilation debug="true">
          <buildProviders>
           <remove extension=".asmx"/>
           <add extension=".asmx"
            type="System.ServiceModel.ServiceBuildProvider,
            System.ServiceModel,
            Version=3.0.0.0,
            Culture=neutral,
            PublicKeyToken=b77a5c561934e089" />
          </buildProviders>
          </compilation>
         </compilation>
    </system.web>
    ```

    <span data-ttu-id="d367e-226">Этот параметр позволяет сохранить необходимость изменения клиентов, настроенных на использование URL-адресов файлов службы ASMX при изменении службы для использования WCF.</span><span class="sxs-lookup"><span data-stu-id="d367e-226">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use WCF.</span></span>

## <a name="client-development"></a><span data-ttu-id="d367e-227">Разработка клиентов</span><span class="sxs-lookup"><span data-stu-id="d367e-227">Client Development</span></span>

<span data-ttu-id="d367e-228">Клиенты для веб-служб ASP.NET формируются с помощью программы командной строки WSDL.exe, которая предоставляет URL-адрес ASMX-файла в качестве входных данных.</span><span class="sxs-lookup"><span data-stu-id="d367e-228">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="d367e-229">Соответствующий инструмент, предоставляемый WCF, — это [средство служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d367e-229">The corresponding tool provided by WCF is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="d367e-230">Он создает модуль кода с определением контракта службы и определением клиентского класса WCF.</span><span class="sxs-lookup"><span data-stu-id="d367e-230">It generates a code module with the definition of the service contract and the definition of a WCF client class.</span></span> <span data-ttu-id="d367e-231">Кроме того, она формирует файл конфигурации с адресом и привязкой службы.</span><span class="sxs-lookup"><span data-stu-id="d367e-231">It also generates a configuration file with the address and binding of the service.</span></span>

<span data-ttu-id="d367e-232">При программировании клиента удаленной службы обычно рекомендуется программировать в соответствии с асинхронной моделью.</span><span class="sxs-lookup"><span data-stu-id="d367e-232">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="d367e-233">Код, формируемый программой WSDL.exe, по умолчанию всегда предусматривает и синхронную, и асинхронную модели.</span><span class="sxs-lookup"><span data-stu-id="d367e-233">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="d367e-234">Код, создаваемый [служебной программой метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , может предоставляться для любого из этих шаблонов.</span><span class="sxs-lookup"><span data-stu-id="d367e-234">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="d367e-235">По умолчанию предусматривается синхронная модель.</span><span class="sxs-lookup"><span data-stu-id="d367e-235">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="d367e-236">При выполнении программы с переключателем `/async` сформированный код предусматривает асинхронную модель.</span><span class="sxs-lookup"><span data-stu-id="d367e-236">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>

<span data-ttu-id="d367e-237">Нет никакой гарантии, что имена в клиентских классах WCF, созданных ASP. Инструмент WSDL.exe NET по умолчанию соответствует именам в клиентских классах WCF, созданных средством Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="d367e-237">There is no guarantee that names in the WCF client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in WCF client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="d367e-238">В частности, имена свойств классов, которые должны сериализоваться с помощью сериализатора <xref:System.Xml.Serialization.XmlSerializer>, в формируемом программой Svcutil.exe коде по умолчанию получают суффикс "Property", который отсутствует в коде, формируемом WSDL.exe.</span><span class="sxs-lookup"><span data-stu-id="d367e-238">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>

## <a name="message-representation"></a><span data-ttu-id="d367e-239">Представление сообщений</span><span class="sxs-lookup"><span data-stu-id="d367e-239">Message Representation</span></span>

<span data-ttu-id="d367e-240">Заголовки сообщений SOAP, отправляемых и получаемых веб-службами ASP.NET, можно настроить.</span><span class="sxs-lookup"><span data-stu-id="d367e-240">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="d367e-241">Из класса <xref:System.Web.Services.Protocols.SoapHeader> наследуется класс для определения структуры заголовка, после чего применяется атрибут <xref:System.Web.Services.Protocols.SoapHeaderAttribute>, чтобы указать на присутствие заголовка.</span><span class="sxs-lookup"><span data-stu-id="d367e-241">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>

```csharp
public class SomeProtocol : SoapHeader
{
     public long CurrentValue;
     public long Total;
}

[WebService]
public interface IEcho
{
     SomeProtocol ProtocolHeader
     {
      get;
     set;
     }

     [WebMethod]
     [SoapHeader("ProtocolHeader")]
     string PlaceOrders(PurchaseOrderType order);
}

public class Service: WebService, IEcho
{
     private SomeProtocol protocolHeader;

     public SomeProtocol ProtocolHeader
     {
         get
         {
              return this.protocolHeader;
         }

         set
         {
              this.protocolHeader = value;
         }
     }

     string PlaceOrders(PurchaseOrderType order)
     {
         long currentValue = this.protocolHeader.CurrentValue;
     }
}
```

<span data-ttu-id="d367e-242">WCF предоставляет атрибуты,, <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.MessageHeaderAttribute> и <xref:System.ServiceModel.MessageBodyMemberAttribute> для описания структуры сообщений SOAP, отправленных и полученных службой.</span><span class="sxs-lookup"><span data-stu-id="d367e-242">The WCF provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>

```csharp
[DataContract]
public class SomeProtocol
{
     [DataMember]
     public long CurrentValue;
     [DataMember]
     public long Total;
}

[DataContract]
public class Item
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}

[MessageContract]
public class ItemMessage
{
     [MessageHeader]
     public SomeProtocol ProtocolHeader;
     [MessageBody]
     public Item Content;
}

[ServiceContract]
public interface IItemService
{
     [OperationContract]
     public void DeliverItem(ItemMessage itemMessage);
}
```

<span data-ttu-id="d367e-243">Этот синтаксис дает явное представление структуры сообщений, тогда как в веб-службе ASP.NET структура сообщений подразумевается в коде.</span><span class="sxs-lookup"><span data-stu-id="d367e-243">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="d367e-244">Кроме того, в синтаксисе ASP.NET заголовки сообщений представлены в виде свойств службы, например `ProtocolHeader` свойства в предыдущем примере, а в синтаксисе WCF они более точно представлены в виде свойств сообщений.</span><span class="sxs-lookup"><span data-stu-id="d367e-244">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in WCF syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="d367e-245">Кроме того, WCF позволяет добавлять заголовки сообщений в конфигурацию конечных точек.</span><span class="sxs-lookup"><span data-stu-id="d367e-245">Also, WCF allows message headers to be added to the configuration of endpoints.</span></span>

```xml
<service name="Service ">
     <endpoint
      address="EchoService"
      binding="basicHttpBinding"
      contract="IEchoService ">
      <headers>
      <dsig:X509Certificate
       xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">
       ...
      </dsig:X509Certificate>
      </headers>
     </endpoint>
</service>
```

<span data-ttu-id="d367e-246">Это позволяет обойтись без ссылок на заголовки инфраструктурных протоколов в коде клиента или службы: заголовки добавляются в сообщения в соответствии с тем, как настроена конечная точка.</span><span class="sxs-lookup"><span data-stu-id="d367e-246">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>

## <a name="service-description"></a><span data-ttu-id="d367e-247">Описание службы</span><span class="sxs-lookup"><span data-stu-id="d367e-247">Service Description</span></span>

<span data-ttu-id="d367e-248">При выдаче запроса HTTP-GET на ASMX-файл веб-службы ASP.NET с запросом "WSDL" ASP.NET формирует WSDL-код для описания службы.</span><span class="sxs-lookup"><span data-stu-id="d367e-248">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="d367e-249">Этот WSDL-код возвращается в качестве ответа на запрос HTTP-GET.</span><span class="sxs-lookup"><span data-stu-id="d367e-249">It returns that WSDL as the response to the request.</span></span>

<span data-ttu-id="d367e-250">В ASP.NET 2.0 появилась возможность проверять, совместима ли служба со спецификацией Basic Profile 1.1 Организации по обеспечению взаимодействия веб-служб (Web Services-Interoperability Organization, WS-I), и вставлять утверждение о совместимости службы в WSDL.</span><span class="sxs-lookup"><span data-stu-id="d367e-250">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="d367e-251">Это делается с помощью параметров `ConformsTo` и `EmitConformanceClaims` атрибута <xref:System.Web.Services.WebServiceBindingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d367e-251">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>

```csharp
[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(
     ConformsTo = WsiProfiles.BasicProfile1_1,
     EmitConformanceClaims=true)]
public interface IEcho
```

<span data-ttu-id="d367e-252">WSDL-код, формируемый ASP.NET для службы, можно настраивать.</span><span class="sxs-lookup"><span data-stu-id="d367e-252">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="d367e-253">Настройка производится путем создания класса, производного от <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension>, для добавления элементов в WSDL-код.</span><span class="sxs-lookup"><span data-stu-id="d367e-253">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>

<span data-ttu-id="d367e-254">Выдача HTTP-запроса GET с запросом WSDL для SVC-файла службы WCF с конечной точкой HTTP, размещенной в IIS 51, 6,0 или WAS, приводит к тому, что WCF отвечает на WSDL для описания службы.</span><span class="sxs-lookup"><span data-stu-id="d367e-254">Issuing an HTTP GET request with the query WSDL for the .svc file of a WCF service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes WCF to respond with WSDL to describe the service.</span></span> <span data-ttu-id="d367e-255">Передача запроса HTTP-GET с запросом «WSDL» на базовый HTTP-адрес службы, размещенной в приложении .NET, имеет тот же эффект, если параметр httpGetEnabled имеет значение true.</span><span class="sxs-lookup"><span data-stu-id="d367e-255">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>

<span data-ttu-id="d367e-256">Однако WCF также реагирует на запросы WS-MetadataExchange с WSDL, который создается для описания службы.</span><span class="sxs-lookup"><span data-stu-id="d367e-256">However, WCF also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="d367e-257">Веб-службы ASP.NET не располагают встроенной поддержкой запросов WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="d367e-257">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>

<span data-ttu-id="d367e-258">WSDL-код, создаваемый WCF, можно настроить с большой нагрузкой.</span><span class="sxs-lookup"><span data-stu-id="d367e-258">The WSDL that WCF generates can be extensively customized.</span></span> <span data-ttu-id="d367e-259">Класс <xref:System.ServiceModel.Description.ServiceMetadataBehavior> предоставляет некоторые средства для настройки WSDL-кода.</span><span class="sxs-lookup"><span data-stu-id="d367e-259">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="d367e-260">Кроме того, WCF можно настроить так, чтобы она не создавала WSDL, а использовала статический WSDL-файл по указанному URL.</span><span class="sxs-lookup"><span data-stu-id="d367e-260">The WCF can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>

```xml
<behaviors>
     <behavior name="DescriptionBehavior">
     <metadataPublishing
      enableMetadataExchange="true"
      enableGetWsdl="true"
      enableHelpPage="true"
      metadataLocation=
      "http://localhost/DerivativesCalculatorService/Service.WSDL"/>
     </behavior>
</behaviors>
```

## <a name="exception-handling"></a><span data-ttu-id="d367e-261">Обработка исключений</span><span class="sxs-lookup"><span data-stu-id="d367e-261">Exception Handling</span></span>

<span data-ttu-id="d367e-262">В веб-службах ASP.NET необработанные исключения возвращаются клиентам в виде ошибок SOAP.</span><span class="sxs-lookup"><span data-stu-id="d367e-262">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="d367e-263">Также можно явно вызывать исключения класса <xref:System.Web.Services.Protocols.SoapException>, что позволяет в большей степени контролировать содержимое ошибки SOAP, передаваемое клиенту.</span><span class="sxs-lookup"><span data-stu-id="d367e-263">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>

<span data-ttu-id="d367e-264">В службах WCF необработанные исключения не возвращаются клиентам в виде ошибок SOAP, чтобы предотвратить непреднамеренное предоставление конфиденциальной информации через исключения.</span><span class="sxs-lookup"><span data-stu-id="d367e-264">In WCF services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="d367e-265">Предусмотрен параметр конфигурации для возвращения необработанных исключений клиентам в целях отладки.</span><span class="sxs-lookup"><span data-stu-id="d367e-265">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>

<span data-ttu-id="d367e-266">Для возвращения ошибок SOAP клиентам можно вызывать исключения универсального типа - <xref:System.ServiceModel.FaultException%601> - используя в качестве универсального типа тип контракта данных.</span><span class="sxs-lookup"><span data-stu-id="d367e-266">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="d367e-267">Также можно добавлять в операции атрибуты <xref:System.ServiceModel.FaultContractAttribute> для указания того, какие ошибки могут быть выданы операцией.</span><span class="sxs-lookup"><span data-stu-id="d367e-267">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>

```csharp
[DataContract]
public class MathFault
{
     [DataMember]
     public string operation;
     [DataMember]
     public string problemType;
}

[ServiceContract]
public interface ICalculator
{
     [OperationContract]
     [FaultContract(typeof(MathFault))]
     int Divide(int n1, int n2);
}
```

<span data-ttu-id="d367e-268">В этом случае возможные ошибки объявляются в WSDL-коде для службы, что дает разработчикам клиентов возможность предвидеть, какие ошибки могут произойти в результате операции, и написать соответствующие инструкции catch.</span><span class="sxs-lookup"><span data-stu-id="d367e-268">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>

```csharp
try
{
     result = client.Divide(value1, value2);
}
catch (FaultException<MathFault> e)
{
 Console.WriteLine("FaultException<MathFault>: Math fault while doing "
  + e.Detail.operation
  + ". Problem: "
  + e.Detail.problemType);
}
```

## <a name="state-management"></a><span data-ttu-id="d367e-269">Управление состоянием</span><span class="sxs-lookup"><span data-stu-id="d367e-269">State Management</span></span>

<span data-ttu-id="d367e-270">Класс, используемый для реализации веб-службы ASP.NET, может наследоваться от класса <xref:System.Web.Services.WebService>.</span><span class="sxs-lookup"><span data-stu-id="d367e-270">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>

```csharp
public class Service : WebService, IEcho
{

 public string Echo(string input)
 {
  return input;
 }
}
```

<span data-ttu-id="d367e-271">В этом случае класс можно запрограммировать на использование свойства Context базового класса <xref:System.Web.Services.WebService> для доступа к объекту <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="d367e-271">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="d367e-272">Объект <xref:System.Web.HttpContext> можно использовать для обновления и извлечения информации о состоянии приложения (с помощью его свойства Application) и для обновления и извлечения информации о состоянии сеанса (с помощью его свойства Session).</span><span class="sxs-lookup"><span data-stu-id="d367e-272">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>

<span data-ttu-id="d367e-273">ASP.NET позволяет в значительной степени контролировать место фактического хранения информации о состоянии сеанса, для доступа к которой используется свойство Session объекта <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="d367e-273">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="d367e-274">Эта информация может храниться в файлах cookie, в базе данных, в памяти текущего сервера или в памяти указанного сервера.</span><span class="sxs-lookup"><span data-stu-id="d367e-274">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="d367e-275">Место хранения информации указывается в файле конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="d367e-275">The choice is made in the service’s configuration file.</span></span>

<span data-ttu-id="d367e-276">WCF предоставляет расширяемые объекты для управления состоянием.</span><span class="sxs-lookup"><span data-stu-id="d367e-276">The WCF provides extensible objects for state management.</span></span> <span data-ttu-id="d367e-277">Расширяемые объекты - это объекты, реализующие интерфейс <xref:System.ServiceModel.IExtensibleObject%601>.</span><span class="sxs-lookup"><span data-stu-id="d367e-277">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="d367e-278">Наиболее важными из расширяемых объектов являются <xref:System.ServiceModel.ServiceHostBase> и <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="d367e-278">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="d367e-279">`ServiceHostBase` позволяет сохранять состояние, к которому могут обращаться все экземпляры всех типов служб на одном и том же узле, тогда как `InstanceContext` позволяет сохранять состояние, к которому может обращаться любой код, выполняемый в одном экземпляре типа службы.</span><span class="sxs-lookup"><span data-stu-id="d367e-279">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>

<span data-ttu-id="d367e-280">Здесь тип службы, `TradingSystem` , имеет объект <xref:System.ServiceModel.ServiceBehaviorAttribute> , который указывает, что все вызовы из одного и того же экземпляра клиента WCF направляются на один и тот же экземпляр типа службы.</span><span class="sxs-lookup"><span data-stu-id="d367e-280">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same WCF client instance are routed to the same instance of the service type.</span></span>

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class TradingSystem: ITradingService
```

<span data-ttu-id="d367e-281">Класс, `DealData`, определяет состояние, к которому может обращаться любой код, выполняемый в одном и том же экземпляре типа службы.</span><span class="sxs-lookup"><span data-stu-id="d367e-281">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>

```csharp
internal class DealData: IExtension<InstanceContext>
{
 public string DealIdentifier = null;
 public Trade[] Trades = null;
}
```

<span data-ttu-id="d367e-282">В коде типа службы, реализующем одну из операций контракта службы, к состоянию текущего экземпляра типа службы добавляется объект состояния `DealData`.</span><span class="sxs-lookup"><span data-stu-id="d367e-282">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>

```csharp
string ITradingService.BeginDeal()
{
 string dealIdentifier = Guid.NewGuid().ToString();
 DealData state = new DealData(dealIdentifier);
 OperationContext.Current.InstanceContext.Extensions.Add(state);
 return dealIdentifier;
}
```

<span data-ttu-id="d367e-283">Этот объект состояния затем может быть извлечен и изменен кодом, реализующим другую операцию контракта службы.</span><span class="sxs-lookup"><span data-stu-id="d367e-283">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>

```csharp
void ITradingService.AddTrade(Trade trade)
{
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();
 dealData.AddTrade(trade);
}
```

<span data-ttu-id="d367e-284">В то время как ASP.NET предоставляет контроль над тем, где на самом деле хранится информация о состоянии в <xref:System.Web.HttpContext> классе, WCF, по крайней мере, в начальной версии, не предоставляет контроль над тем, где хранятся расширяемые объекты.</span><span class="sxs-lookup"><span data-stu-id="d367e-284">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, WCF, at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="d367e-285">Это является наиболее оптимальной причиной выбора режима совместимости ASP.NET для службы WCF.</span><span class="sxs-lookup"><span data-stu-id="d367e-285">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a WCF service.</span></span> <span data-ttu-id="d367e-286">Если настраиваемое управление состоянием является обязательным условием, выбор режима совместимости с ASP.NET позволяет использовать средства класса <xref:System.Web.HttpContext> в точности так, как они используются в ASP.NET, а также настраивать место хранения информации о состоянии с помощью класса <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="d367e-286">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>

## <a name="security"></a><span data-ttu-id="d367e-287">Безопасность</span><span class="sxs-lookup"><span data-stu-id="d367e-287">Security</span></span>

<span data-ttu-id="d367e-288">Для защиты веб-служб ASP.NET используются те же механизмы, что и для защиты любого приложения IIS.</span><span class="sxs-lookup"><span data-stu-id="d367e-288">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="d367e-289">Так как приложения WCF могут размещаться не только в службах IIS, но и в любом исполняемом файле .NET, варианты защиты приложений WCF должны быть сделаны независимыми от средств IIS.</span><span class="sxs-lookup"><span data-stu-id="d367e-289">Because WCF applications can be hosted not only within IIS but also within any .NET executable, the options for securing WCF applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="d367e-290">Однако средства, предоставляемые для веб-служб ASP.NET, также доступны для служб WCF, работающих в режиме совместимости ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d367e-290">However, the facilities provided for ASP.NET Web services are also available for WCF services running in ASP.NET compatibility mode.</span></span>

### <a name="security-authentication"></a><span data-ttu-id="d367e-291">Безопасность: проверка подлинности</span><span class="sxs-lookup"><span data-stu-id="d367e-291">Security: Authentication</span></span>

<span data-ttu-id="d367e-292">Службы IIS предоставляют средства для управления доступом к приложениям, позволяющие выбрать либо анонимный доступ, либо один из ряда режимов проверки подлинности: проверка подлинности Windows, дайджест-проверка подлинности, обычная проверка подлинности и проверка подлинности по паспорту .NET Passport.</span><span class="sxs-lookup"><span data-stu-id="d367e-292">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="d367e-293">Вариант с проверкой подлинности Windows можно использовать для управления доступом к веб-службам ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d367e-293">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="d367e-294">Однако, когда приложения WCF размещаются в службах IIS, службы IIS должны разрешать анонимный доступ к приложению, чтобы проверка подлинности могла управляться самой WCF, что поддерживает проверку подлинности Windows между различными параметрами.</span><span class="sxs-lookup"><span data-stu-id="d367e-294">However, when WCF applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by WCF itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="d367e-295">Другие встроенные средства включают маркеры имени пользователя, сертификаты X.509, маркеры SAML и карту CardSpace; также можно определять пользовательские механизмы проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="d367e-295">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>

### <a name="security-impersonation"></a><span data-ttu-id="d367e-296">Безопасность: олицетворение</span><span class="sxs-lookup"><span data-stu-id="d367e-296">Security: Impersonation</span></span>

<span data-ttu-id="d367e-297">ASP.NET предоставляет элемент удостоверения, посредством которого веб-служба ASP.NET может олицетворять определенного пользователя или любого пользователя, учетные данные которого переданы в текущем запросе.</span><span class="sxs-lookup"><span data-stu-id="d367e-297">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="d367e-298">Этот элемент можно использовать для настройки олицетворения в приложениях WCF, работающих в режиме совместимости ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d367e-298">That element can be used to configure impersonation in WCF applications running in ASP.NET compatibility mode.</span></span>

<span data-ttu-id="d367e-299">Система конфигурации WCF предоставляет свой собственный элемент Identity для обозначения конкретного пользователя для олицетворения.</span><span class="sxs-lookup"><span data-stu-id="d367e-299">The WCF configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="d367e-300">Кроме того, клиенты и службы WCF могут быть настроены независимо для олицетворения.</span><span class="sxs-lookup"><span data-stu-id="d367e-300">Also, WCF clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="d367e-301">Клиенты можно настроить на олицетворение текущего пользователя при передаче запросов.</span><span class="sxs-lookup"><span data-stu-id="d367e-301">Clients can be configured to impersonate the current user when they transmit requests.</span></span>

```xml
<behaviors>
     <behavior name="DerivativesCalculatorClientBehavior">
      <clientCredentials>
      <windows allowedImpersonationLevel="Impersonation"/>
      </clientCredentials>
     </behavior>
</behaviors>
```

<span data-ttu-id="d367e-302">Операции службы можно настроить на олицетворение любого пользователя, учетные данные которого переданы в текущем запросе.</span><span class="sxs-lookup"><span data-stu-id="d367e-302">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>

```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]
public void Receive(Message input)
```

### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="d367e-303">Безопасность: авторизация с использованием списков управления доступом</span><span class="sxs-lookup"><span data-stu-id="d367e-303">Security: Authorization using Access Control Lists</span></span>

<span data-ttu-id="d367e-304">Для ограничения доступа к ASMX-файлам можно использовать списки управления доступом (ACL).</span><span class="sxs-lookup"><span data-stu-id="d367e-304">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="d367e-305">Однако списки ACL для файлов WCF. svc игнорируются, за исключением режима совместимости ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d367e-305">However, ACLs on WCF .svc files are ignored except in ASP.NET compatibility mode.</span></span>

### <a name="security-role-based-authorization"></a><span data-ttu-id="d367e-306">Безопасность: авторизация на основе ролей</span><span class="sxs-lookup"><span data-stu-id="d367e-306">Security: Role-based Authorization</span></span>

<span data-ttu-id="d367e-307">Режим проверки подлинности Windows, предоставляемый службами IIS, можно использовать в сочетании с предусмотренным в языке конфигурации ASP.NET элементом авторизации для упрощения авторизации на основе ролей для веб-служб ASP.NET, основанных на группах Windows, которым назначены пользователи.</span><span class="sxs-lookup"><span data-stu-id="d367e-307">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="d367e-308">В ASP.NET 2.0 появился более общий механизм авторизации на основе ролей: поставщики ролей.</span><span class="sxs-lookup"><span data-stu-id="d367e-308">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>

<span data-ttu-id="d367e-309">Поставщики ролей - это классы, реализующие базовый интерфейс для отправки запросов о ролях, которым назначен пользователь, причем каждый поставщик ролей предназначен для извлечения этой информации из определенного источника.</span><span class="sxs-lookup"><span data-stu-id="d367e-309">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="d367e-310">ASP.NET 2.0 предоставляет поставщик ролей, который может извлекать назначения ролей из базы данных Microsoft SQL Server, и еще один поставщик, способный извлекать назначения ролей из диспетчера авторизации Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="d367e-310">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>

<span data-ttu-id="d367e-311">Механизм поставщика ролей можно фактически использовать независимо от ASP.NET в любом приложении .NET, включая приложение WCF.</span><span class="sxs-lookup"><span data-stu-id="d367e-311">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a WCF application.</span></span> <span data-ttu-id="d367e-312">В следующем примере конфигурации для приложения WCF показано, как использование поставщика ролей ASP.NET является параметром, выбранным с помощью <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> .</span><span class="sxs-lookup"><span data-stu-id="d367e-312">The following sample configuration for a WCF application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

```xml
<system.serviceModel>
     <services>
         <service name="Service.ResourceAccessServiceType"
             behaviorConfiguration="ServiceBehavior">
             <endpoint
              address="ResourceAccessService"
              binding="wsHttpBinding"
              contract="Service.IResourceAccessContract"/>
         </service>
     </services>
     <behaviors>
       <behavior name="ServiceBehavior">
       <serviceAuthorization principalPermissionMode="UseAspNetRoles"/>
      </behavior>
     </behaviors>
</system.serviceModel>
```

### <a name="security-claims-based-authorization"></a><span data-ttu-id="d367e-313">Безопасность: авторизация на основе утверждений</span><span class="sxs-lookup"><span data-stu-id="d367e-313">Security: Claims-based Authorization</span></span>

<span data-ttu-id="d367e-314">Одним из наиболее важных нововведений WCF является тщательная Поддержка авторизации доступа к защищенным ресурсам на основе заявок.</span><span class="sxs-lookup"><span data-stu-id="d367e-314">One of the most important innovations of WCF is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="d367e-315">Утверждения состоят из типа, права и значения. В качестве примера можно привести водительское удостоверение:</span><span class="sxs-lookup"><span data-stu-id="d367e-315">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="d367e-316">оно содержит ряд утверждений о своем предъявителе, одним из которых является дата рождения предъявителя.</span><span class="sxs-lookup"><span data-stu-id="d367e-316">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="d367e-317">Тип этого утверждения - дата рождения, а значение утверждения - дата рождения водителя.</span><span class="sxs-lookup"><span data-stu-id="d367e-317">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="d367e-318">Право, которое утверждение дает предъявителю, указывает, что предъявитель может делать со значением утверждения.</span><span class="sxs-lookup"><span data-stu-id="d367e-318">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="d367e-319">В случае утверждения даты рождения водителя право состоит во владении: эта дата рождения принадлежит водителю, однако он не может, например, изменять ее.</span><span class="sxs-lookup"><span data-stu-id="d367e-319">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="d367e-320">Авторизация на основе утверждений включает в себя авторизацию на основе ролей, поскольку роли являются одним из типов утверждений.</span><span class="sxs-lookup"><span data-stu-id="d367e-320">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>

<span data-ttu-id="d367e-321">Авторизация на основе утверждений осуществляется путем сравнения набора утверждений с требованиями доступа к операции и предоставления доступа к операции или отказа в доступе к операции в зависимости от результатов этого сравнения.</span><span class="sxs-lookup"><span data-stu-id="d367e-321">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="d367e-322">В WCF можно указать класс, который будет использоваться для выполнения авторизации на основе утверждений, путем присвоения значения `ServiceAuthorizationManager` свойству <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> .</span><span class="sxs-lookup"><span data-stu-id="d367e-322">In WCF, you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

```xml
<behaviors>
     <behavior name='ServiceBehavior'>
     <serviceAuthorization
     serviceAuthorizationManagerType=
                   'Service.AccessChecker, Service' />
     </behavior>
</behaviors>
```

<span data-ttu-id="d367e-323">Классы, используемые для выполнения авторизации на основе утверждений, должны быть производными от класса <xref:System.ServiceModel.ServiceAuthorizationManager>, в котором имеется только один метод для переопределения - `AccessCheck()`.</span><span class="sxs-lookup"><span data-stu-id="d367e-323">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> <span data-ttu-id="d367e-324">WCF вызывает этот метод каждый раз при вызове операции службы и предоставляет <xref:System.ServiceModel.OperationContext> объект, который имеет утверждения для пользователя в его `ServiceSecurityContext.AuthorizationContext` свойстве.</span><span class="sxs-lookup"><span data-stu-id="d367e-324">WCF calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> <span data-ttu-id="d367e-325">WCF выполняет сборку утверждений о пользователе из любого маркера безопасности, предоставленного пользователем для проверки подлинности, что оставляет за собой задачу оценки того, достаточно ли этих утверждений для рассматриваемой операции.</span><span class="sxs-lookup"><span data-stu-id="d367e-325">WCF does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>

<span data-ttu-id="d367e-326">WCF автоматически собирает утверждения из любого вида маркера безопасности, так как делает код для авторизации на основе утверждений полностью независимым от механизма проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="d367e-326">That WCF automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="d367e-327">В противоположность этому авторизация с использованием списков ACL или ролей в ASP.NET тесно связана с проверкой подлинности Windows.</span><span class="sxs-lookup"><span data-stu-id="d367e-327">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>

### <a name="security-confidentiality"></a><span data-ttu-id="d367e-328">Безопасность: конфиденциальность</span><span class="sxs-lookup"><span data-stu-id="d367e-328">Security: Confidentiality</span></span>

<span data-ttu-id="d367e-329">Конфиденциальность сообщений, отправляемых и принимаемых веб-службами ASP.NET, может быть обеспечена на уровне транспорта путем настройки приложения в IIS на использование протокола HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d367e-329">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="d367e-330">То же самое можно сделать для приложений WCF, размещенных в IIS.</span><span class="sxs-lookup"><span data-stu-id="d367e-330">The same can be done for WCF applications hosted within IIS.</span></span> <span data-ttu-id="d367e-331">Однако приложения WCF, размещенные за пределами служб IIS, также можно настроить для использования защищенного транспортного протокола.</span><span class="sxs-lookup"><span data-stu-id="d367e-331">However, WCF applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="d367e-332">Более важно, что приложения WCF также можно настроить для защиты сообщений перед их перепереносом с помощью протокола WS-Security.</span><span class="sxs-lookup"><span data-stu-id="d367e-332">More important, WCF applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="d367e-333">Защита только тела сообщения с использованием WS-Security позволяет передавать его с соблюдением конфиденциальности в пункт назначения через посредников.</span><span class="sxs-lookup"><span data-stu-id="d367e-333">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>

## <a name="globalization"></a><span data-ttu-id="d367e-334">Глобализация</span><span class="sxs-lookup"><span data-stu-id="d367e-334">Globalization</span></span>

<span data-ttu-id="d367e-335">Язык конфигурации ASP.NET позволяет задавать язык и региональные параметры для отдельных служб.</span><span class="sxs-lookup"><span data-stu-id="d367e-335">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="d367e-336">WCF не поддерживает этот параметр конфигурации, за исключением режима совместимости ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d367e-336">The WCF does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="d367e-337">Для локализации службы WCF, которая не использует режим совместимости ASP.NET, Скомпилируйте тип службы в сборках, зависящих от языка и региональных параметров, и разместите отдельные конечные точки, зависящие от языка и региональных параметров, для каждой сборки, зависящей от культуры.</span><span class="sxs-lookup"><span data-stu-id="d367e-337">To localize a WCF service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="d367e-338">См. также</span><span class="sxs-lookup"><span data-stu-id="d367e-338">See also</span></span>

- [<span data-ttu-id="d367e-339">Сравнение веб-служб ASP.NET с веб-службами на основе WCF по назначению и используемым стандартам</span><span class="sxs-lookup"><span data-stu-id="d367e-339">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
