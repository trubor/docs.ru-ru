---
title: Практическое руководство. Определение того, является ли файл сборкой
description: В этой статье показано, как вручную или программным способом определить, является ли файл сборкой .NET.
ms.date: 08/19/2019
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
dev_langs:
- csharp
- vb
ms.openlocfilehash: b78acaad31996f8fc2b965f51f541e99aeceb111
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731505"
---
# <a name="how-to-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="522b1-103">Практическое руководство. Определение того, является ли файл сборкой</span><span class="sxs-lookup"><span data-stu-id="522b1-103">How to: Determine if a file is an assembly</span></span>

<span data-ttu-id="522b1-104">Файл является сборкой только в том случае, если он является управляемым и содержит запись сборки в своих метаданных.</span><span class="sxs-lookup"><span data-stu-id="522b1-104">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="522b1-105">Дополнительные сведения о сборках и метаданных см. в разделе [Манифест сборки](manifest.md).</span><span class="sxs-lookup"><span data-stu-id="522b1-105">For more information on assemblies and metadata, see [Assembly manifest](manifest.md).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="522b1-106">Как вручную определить, является ли файл сборкой</span><span class="sxs-lookup"><span data-stu-id="522b1-106">How to manually determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="522b1-107">Запустите [Ildasm.exe (дизассемблер IL)](../../framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="522b1-107">Start the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md).</span></span>  
  
2. <span data-ttu-id="522b1-108">Загрузите файл, который нужно протестировать.</span><span class="sxs-lookup"><span data-stu-id="522b1-108">Load the file you want to test.</span></span>  
  
3. <span data-ttu-id="522b1-109">Если программа **ILDASM** сообщает, что файл не является переносимым исполняемым файлом (PE), то он не является сборкой.</span><span class="sxs-lookup"><span data-stu-id="522b1-109">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="522b1-110">Дополнительные сведения см. в разделе [Практическое руководство. Просмотр содержимого сборки](view-contents.md).</span><span class="sxs-lookup"><span data-stu-id="522b1-110">For more information, see the topic [How to: View assembly contents](view-contents.md).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="522b1-111">Как программно определить, является ли файл сборкой</span><span class="sxs-lookup"><span data-stu-id="522b1-111">How to programmatically determine if a file is an assembly</span></span>  
  
1. <span data-ttu-id="522b1-112">Вызовите метод <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType>, указав полный путь к файлу и имя файла, который вы тестируете.</span><span class="sxs-lookup"><span data-stu-id="522b1-112">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method, passing the full file path and name of the file you are testing.</span></span>  
  
2. <span data-ttu-id="522b1-113">Если возникает исключение <xref:System.BadImageFormatException>, значит файл не является сборкой.</span><span class="sxs-lookup"><span data-stu-id="522b1-113">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="522b1-114">Пример</span><span class="sxs-lookup"><span data-stu-id="522b1-114">Example</span></span>  

<span data-ttu-id="522b1-115">Этот пример кода проверяет, является ли библиотека DLL сборкой.</span><span class="sxs-lookup"><span data-stu-id="522b1-115">This example tests a DLL to see if it is an assembly.</span></span>  

```csharp
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  

```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```

<span data-ttu-id="522b1-116">Метод <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> загружает тестовый файл и освобождает его после того, как информация будет прочитана.</span><span class="sxs-lookup"><span data-stu-id="522b1-116">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="522b1-117">См. также</span><span class="sxs-lookup"><span data-stu-id="522b1-117">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="522b1-118">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="522b1-118">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="522b1-119">Основные понятия программирования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="522b1-119">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="522b1-120">Сборки в .NET</span><span class="sxs-lookup"><span data-stu-id="522b1-120">Assemblies in .NET</span></span>](index.md)
