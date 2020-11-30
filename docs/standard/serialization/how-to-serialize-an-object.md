---
title: Практическое руководство. Сериализация объекта
description: 'В этой статье показано, как сериализовать объект. Выберите формат передачи для хранения потока XML: в виде потока или в виде файла.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: ce8510a987f75ed4110a44ffa9f2ac813d36a5be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678900"
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="b36cc-104">Практическое руководство. Сериализация объекта</span><span class="sxs-lookup"><span data-stu-id="b36cc-104">How to: Serialize an Object</span></span>

<span data-ttu-id="b36cc-105">Для сериализации объекта сначала следует создать сериализуемый объект и задать открытые свойства и поля.</span><span class="sxs-lookup"><span data-stu-id="b36cc-105">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="b36cc-106">Для этого необходимо выбрать формат передачи, в котором будет храниться поток XML: поток или файл.</span><span class="sxs-lookup"><span data-stu-id="b36cc-106">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="b36cc-107">Например, если поток XML должен храниться в неизменном виде, создайте объект <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="b36cc-107">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b36cc-108">Дополнительные примеры XML-сериализации см. в разделе [Примеры сериализации XML](examples-of-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="b36cc-108">For more examples of XML serialization, see [Examples of XML Serialization](examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="b36cc-109">Сериализация объекта</span><span class="sxs-lookup"><span data-stu-id="b36cc-109">To serialize an object</span></span>  
  
1. <span data-ttu-id="b36cc-110">Создайте объект и задайте его открытые поля и свойства.</span><span class="sxs-lookup"><span data-stu-id="b36cc-110">Create the object and set its public fields and properties.</span></span>  
  
2. <span data-ttu-id="b36cc-111">Постройте <xref:System.Xml.Serialization.XmlSerializer> с использованием типа объекта.</span><span class="sxs-lookup"><span data-stu-id="b36cc-111">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="b36cc-112">Дополнительные сведения см. в разделе конструкторов класса <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b36cc-112">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3. <span data-ttu-id="b36cc-113">Вызовите метод <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A>, чтобы создать либо поток XML, либо файловое представление открытых свойств и полей объекта.</span><span class="sxs-lookup"><span data-stu-id="b36cc-113">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="b36cc-114">В следующем примере создается файл.</span><span class="sxs-lookup"><span data-stu-id="b36cc-114">The following example creates a file.</span></span>  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b36cc-115">См. также</span><span class="sxs-lookup"><span data-stu-id="b36cc-115">See also</span></span>

- [<span data-ttu-id="b36cc-116">Введение в сериализацию XML</span><span class="sxs-lookup"><span data-stu-id="b36cc-116">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="b36cc-117">Практическое руководство. Десериализация объекта</span><span class="sxs-lookup"><span data-stu-id="b36cc-117">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
