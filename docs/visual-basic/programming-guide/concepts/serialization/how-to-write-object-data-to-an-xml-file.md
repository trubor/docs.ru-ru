---
description: Дополнительные сведения см. в статье как записывать данные объекта в XML-файл (Visual Basic).
title: Практическое руководство. Запись данных объекта в XML-файл
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: c6935fa97ed8813528630f5794e0a8e3e7e77b4d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486840"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="01072-103">How to: Write Object Data to an XML File (Visual Basic) (Практическое руководство. Запись данных объекта в XML-файл (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="01072-103">How to: Write Object Data to an XML File (Visual Basic)</span></span>

<span data-ttu-id="01072-104">Показывает, как записать объект из класса в XML-файл с помощью класса <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="01072-104">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01072-105">Пример</span><span class="sxs-lookup"><span data-stu-id="01072-105">Example</span></span>  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="01072-106">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="01072-106">Compile the code</span></span>  

 <span data-ttu-id="01072-107">У класса должен быть открытый конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="01072-107">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="01072-108">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="01072-108">Robust Programming</span></span>  

 <span data-ttu-id="01072-109">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="01072-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="01072-110">В сериализуемом классе нет открытого конструктора без параметров.</span><span class="sxs-lookup"><span data-stu-id="01072-110">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="01072-111">Файл существует и является файлом только для чтения (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="01072-111">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="01072-112">Слишком длинный путь (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="01072-112">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="01072-113">Диск заполнен (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="01072-113">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="01072-114">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="01072-114">.NET Framework Security</span></span>  

 <span data-ttu-id="01072-115">В этом примере создается файл (если файл отсутствует).</span><span class="sxs-lookup"><span data-stu-id="01072-115">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="01072-116">Если приложению требуется создать файл, оно должно иметь доступ к каталогу для создания файлов (`Create`).</span><span class="sxs-lookup"><span data-stu-id="01072-116">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="01072-117">Если файл уже существует, то приложению достаточно иметь лишь доступ для записи файлов (`Write`), т. е. меньшие привилегии.</span><span class="sxs-lookup"><span data-stu-id="01072-117">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="01072-118">Безопаснее создавать файл во время развертывания, если это возможно, а также предоставлять доступ `Read` к отдельному файлу вместо доступа `Create` к папке.</span><span class="sxs-lookup"><span data-stu-id="01072-118">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01072-119">См. также</span><span class="sxs-lookup"><span data-stu-id="01072-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- <span data-ttu-id="01072-120">[How to: Read Object Data from an XML File (Visual Basic)](how-to-read-object-data-from-an-xml-file.md) (Практическое руководство. Чтение данных объекта из XML-файла (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="01072-120">[How to: Read Object Data from an XML File (Visual Basic)](how-to-read-object-data-from-an-xml-file.md)</span></span>
- [<span data-ttu-id="01072-121">Сериализация (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01072-121">Serialization (Visual Basic)</span></span>](index.md)
