---
title: Практическое руководство. Создание подписанных дружественных сборок
description: В этом руководстве демонстрируется использование дружественных сборок со сборками, имеющими строгие имена, а также приводятся сведения о безопасности .NET.
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 4c441501ae0f939f69ac863a990d6e392bd35fc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734274"
---
# <a name="how-to-create-signed-friend-assemblies"></a><span data-ttu-id="d050f-104">Практическое руководство. Создание подписанных дружественных сборок</span><span class="sxs-lookup"><span data-stu-id="d050f-104">How to: Create signed friend assemblies</span></span>

<span data-ttu-id="d050f-105">В этом примере демонстрируется использование дружественных сборок со сборками, имеющими строгие имена.</span><span class="sxs-lookup"><span data-stu-id="d050f-105">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="d050f-106">Обе сборки должны иметь строгое имя.</span><span class="sxs-lookup"><span data-stu-id="d050f-106">Both assemblies must be strong named.</span></span> <span data-ttu-id="d050f-107">Хотя обе сборки в этом примере используют одинаковые ключи, вы можете использовать для двух сборок разные ключи.</span><span class="sxs-lookup"><span data-stu-id="d050f-107">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="d050f-108">Создание подписанной и дружественной сборки</span><span class="sxs-lookup"><span data-stu-id="d050f-108">Create a signed assembly and a friend assembly</span></span>  
  
1. <span data-ttu-id="d050f-109">Откройте окно командной строки.</span><span class="sxs-lookup"><span data-stu-id="d050f-109">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="d050f-110">Используйте следующую последовательность команд в средстве задания строгих имен для формирования файла ключа и отображения его открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="d050f-110">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="d050f-111">Дополнительные сведения см. в разделе [Sn.exe (средство строгих имен)](../../framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="d050f-111">For more information, see [Sn.exe (Strong Name tool)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
    1. <span data-ttu-id="d050f-112">Создайте ключ строгого имени для этого примера и сохраните его в файле *FriendAssemblies.snk*:</span><span class="sxs-lookup"><span data-stu-id="d050f-112">Generate a strong-name key for this example and store it in the file *FriendAssemblies.snk*:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2. <span data-ttu-id="d050f-113">Извлеките открытый ключ из *FriendAssemblies.snk* и поместите его в файл *FriendAssemblies.publickey*:</span><span class="sxs-lookup"><span data-stu-id="d050f-113">Extract the public key from *FriendAssemblies.snk* and put it into *FriendAssemblies.publickey*:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. <span data-ttu-id="d050f-114">Выведите на экран открытый ключ, хранящийся в файле *FriendAssemblies.publickey*:</span><span class="sxs-lookup"><span data-stu-id="d050f-114">Display the public key stored in the file *FriendAssemblies.publickey*:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. <span data-ttu-id="d050f-115">Создайте файл C# или Visual Basic с именем *friend_signed_A*, содержащий приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="d050f-115">Create a C# or Visual Basic file named *friend_signed_A* that contains the following code.</span></span> <span data-ttu-id="d050f-116">Атрибут <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> используется в коде для объявления *friend_signed_B* в качестве дружественной сборки.</span><span class="sxs-lookup"><span data-stu-id="d050f-116">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare *friend_signed_B* as a friend assembly.</span></span>  

   <span data-ttu-id="d050f-117">Средство задания строгих имен создает новый открытый ключ при каждом запуске.</span><span class="sxs-lookup"><span data-stu-id="d050f-117">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="d050f-118">Таким образом, необходимо заменить открытый ключ в следующем коде только что созданным открытым ключом, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d050f-118">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  

   ```csharp  
   // friend_signed_A.cs  
   // Compile with:
   // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   using System.Runtime.CompilerServices;  

   [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
   class Class1  
   {  
       public void Test()  
       {  
           System.Console.WriteLine("Class1.Test");  
           System.Console.ReadLine();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_A.vb  
   ' Compile with:
   ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   Imports System.Runtime.CompilerServices  

   <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>
   Public Class Class1  
       Public Sub Test()  
           System.Console.WriteLine("Class1.Test")  
           System.Console.ReadLine()  
       End Sub  
   End Class  
   ```  

4. <span data-ttu-id="d050f-119">Скомпилируйте и подпишите сборку *friend_signed_A* с помощью приведенной ниже команды.</span><span class="sxs-lookup"><span data-stu-id="d050f-119">Compile and sign *friend_signed_A* by using the following command.</span></span>  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. <span data-ttu-id="d050f-120">Создайте файл C# или Visual Basic с именем *friend_signed_B*, содержащий приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="d050f-120">Create a C# or Visual Basic file named *friend_signed_B* that contains the following code.</span></span> <span data-ttu-id="d050f-121">Так как сборка *friend_signed_A* указывает сборку *friend_signed_B* в качестве дружественной, код в сборке *friend_signed_B* может обращаться к типам и членам `internal` (C#) или `Friend` (Visual Basic) в сборке *friend_signed_A*.</span><span class="sxs-lookup"><span data-stu-id="d050f-121">Because *friend_signed_A* specifies *friend_signed_B* as a friend assembly, the code in *friend_signed_B* can access `internal` (C#) or `Friend` (Visual Basic) types and members from *friend_signed_A*.</span></span> <span data-ttu-id="d050f-122">Файл содержит следующий код.</span><span class="sxs-lookup"><span data-stu-id="d050f-122">The file contains the following code.</span></span>  

   ```csharp  
   // friend_signed_B.cs  
   // Compile with:
   // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   public class Program  
   {  
       static void Main()  
       {  
           Class1 inst = new Class1();  
           inst.Test();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_B.vb  
   ' Compile with:
   ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   Module Sample  
       Public Sub Main()  
           Dim inst As New Class1  
           inst.Test()  
       End Sub  
   End Module  
   ```  

6. <span data-ttu-id="d050f-123">Откомпилируйте и подпишите сборку *friend_signed_B* с помощью приведенной ниже команды.</span><span class="sxs-lookup"><span data-stu-id="d050f-123">Compile and sign *friend_signed_B* by using the following command.</span></span>  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   <span data-ttu-id="d050f-124">Имя сборки, созданной компилятором, должно соответствовать имени дружественной сборки, передаваемой атрибуту <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d050f-124">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="d050f-125">Необходимо явно указать имя выходной сборки (*EXE* или *DLL*) с помощью параметра компилятора `-out`.</span><span class="sxs-lookup"><span data-stu-id="d050f-125">You must explicitly specify the name of the output assembly (*.exe* or *.dll*) by using the `-out` compiler option.</span></span> <span data-ttu-id="d050f-126">Дополнительные сведения см. в разделе [-out (параметры компилятора C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) или [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="d050f-126">For more information, see [-out (C# compiler options)](../../csharp/language-reference/compiler-options/out-compiler-option.md) or [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).</span></span>  

7. <span data-ttu-id="d050f-127">Запустите файл *friend_signed_B.exe*.</span><span class="sxs-lookup"><span data-stu-id="d050f-127">Run the *friend_signed_B.exe* file.</span></span>  

   <span data-ttu-id="d050f-128">Программа выводит строку **Class1.Test**.</span><span class="sxs-lookup"><span data-stu-id="d050f-128">The program outputs the string **Class1.Test**.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="d050f-129">Безопасность в .NET</span><span class="sxs-lookup"><span data-stu-id="d050f-129">.NET security</span></span>  

 <span data-ttu-id="d050f-130">Между атрибутом <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> и классом <xref:System.Security.Permissions.StrongNameIdentityPermission> существует определенное сходство.</span><span class="sxs-lookup"><span data-stu-id="d050f-130">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="d050f-131">Основное отличие заключается в том, что для выполнения <xref:System.Security.Permissions.StrongNameIdentityPermission> в определенном разделе кода могут потребоваться разрешения системы безопасности, тогда как атрибут <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> определяет видимость членов и типов `internal` (C#) или `Friend` (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d050f-131">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `internal` (C#) or `Friend` (Visual Basic) types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d050f-132">См. также</span><span class="sxs-lookup"><span data-stu-id="d050f-132">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="d050f-133">Сборки в .NET</span><span class="sxs-lookup"><span data-stu-id="d050f-133">Assemblies in .NET</span></span>](index.md)
- [<span data-ttu-id="d050f-134">Дружественные сборки</span><span class="sxs-lookup"><span data-stu-id="d050f-134">Friend assemblies</span></span>](friend.md)
- [<span data-ttu-id="d050f-135">Практическое руководство. Создание неподписанных дружественных сборок</span><span class="sxs-lookup"><span data-stu-id="d050f-135">How to: Create unsigned friend assemblies</span></span>](create-unsigned-friend.md)
- [<span data-ttu-id="d050f-136">-keyfile (C#)</span><span class="sxs-lookup"><span data-stu-id="d050f-136">-keyfile (C#)</span></span>](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [<span data-ttu-id="d050f-137">-keyfile (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d050f-137">-keyfile (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="d050f-138">Sn.exe (средство строгих имен)</span><span class="sxs-lookup"><span data-stu-id="d050f-138">Sn.exe (Strong Name tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="d050f-139">Создание и использование сборок со строгими именами</span><span class="sxs-lookup"><span data-stu-id="d050f-139">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="d050f-140">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="d050f-140">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d050f-141">Основные понятия программирования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d050f-141">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
