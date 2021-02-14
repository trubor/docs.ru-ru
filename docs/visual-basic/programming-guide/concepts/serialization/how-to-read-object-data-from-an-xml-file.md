---
description: Дополнительные сведения см. в статье как читать данные объекта из XML-файла (Visual Basic)
title: Практическое руководство. Чтение данных объекта из XML-файла
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: d281997a0dd96ad6263fe03cea84b3e84005a3ad
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486827"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="00b23-103">How to: Read Object Data from an XML File (Visual Basic) (Практическое руководство. Чтение данных объекта из XML-файла (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="00b23-103">How to: Read Object Data from an XML File (Visual Basic)</span></span>

<span data-ttu-id="00b23-104">В этом примере демонстрируется считывание данных объекта, которые ранее были записаны в XML-файл с помощью класса <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="00b23-104">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00b23-105">Пример</span><span class="sxs-lookup"><span data-stu-id="00b23-105">Example</span></span>  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="00b23-106">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="00b23-106">Compile the code</span></span>  

 <span data-ttu-id="00b23-107">Замените имя файла "c:\temp\SerializationOverview.xml" на имя файла, в котором содержатся сериализованные данные.</span><span class="sxs-lookup"><span data-stu-id="00b23-107">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="00b23-108">Дополнительные сведения о сериализации данных см. [в разделе инструкции. запись данных объекта в XML-файл (Visual Basic)](how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="00b23-108">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="00b23-109">У класса должен быть открытый конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="00b23-109">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="00b23-110">Десериализуются только открытые свойства и поля.</span><span class="sxs-lookup"><span data-stu-id="00b23-110">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="00b23-111">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="00b23-111">Robust Programming</span></span>  

 <span data-ttu-id="00b23-112">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="00b23-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="00b23-113">В сериализуемом классе нет открытого конструктора без параметров.</span><span class="sxs-lookup"><span data-stu-id="00b23-113">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="00b23-114">Данные в файле не являются данными из класса, который десериализуется.</span><span class="sxs-lookup"><span data-stu-id="00b23-114">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="00b23-115">Файл не существует (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="00b23-115">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="00b23-116">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="00b23-116">.NET Framework Security</span></span>  

 <span data-ttu-id="00b23-117">Всегда проверяйте входные данные и никогда не десериализуйте данные из непроверенных источников.</span><span class="sxs-lookup"><span data-stu-id="00b23-117">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="00b23-118">Созданный заново объект выполняется на локальном компьютере с разрешениями кода, который его десериализовал.</span><span class="sxs-lookup"><span data-stu-id="00b23-118">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="00b23-119">Следует проверять все входные данные перед использованием их в приложении.</span><span class="sxs-lookup"><span data-stu-id="00b23-119">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b23-120">См. также</span><span class="sxs-lookup"><span data-stu-id="00b23-120">See also</span></span>

- <xref:System.IO.StreamWriter>
- <span data-ttu-id="00b23-121">[How to: Write Object Data to an XML File (Visual Basic)](how-to-write-object-data-to-an-xml-file.md) (Практическое руководство. Запись данных объекта в XML-файл (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="00b23-121">[How to: Write Object Data to an XML File (Visual Basic)](how-to-write-object-data-to-an-xml-file.md)</span></span>
- [<span data-ttu-id="00b23-122">Сериализация (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00b23-122">Serialization (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="00b23-123">Руководство по программированию на Visual Basic</span><span class="sxs-lookup"><span data-stu-id="00b23-123">Visual Basic Programming Guide</span></span>](../../index.md)
