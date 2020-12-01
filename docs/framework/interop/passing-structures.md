---
title: Передача структур
description: Получите представление о том, как передавать структуры и классы в неуправляемые функции. Узнайте об атрибуте StructLayoutAttribute, который используется для определения форматированных типов.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
ms.openlocfilehash: ece5db8fdf803ce2f450ebeaaad66a379cfbf992
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268915"
---
# <a name="passing-structures"></a><span data-ttu-id="df217-104">Передача структур</span><span class="sxs-lookup"><span data-stu-id="df217-104">Passing Structures</span></span>

<span data-ttu-id="df217-105">В качестве параметров во многие неуправляемые функции должны передаваться члены, структуры (определяемые пользователем типы в Visual Basic) или члены классов, которые определяются в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="df217-105">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="df217-106">При передаче структур или классов в неуправляемый код посредством вызовов неуправляемого кода необходимо указать дополнительную информацию для сохранения исходного размещения и выравнивания.</span><span class="sxs-lookup"><span data-stu-id="df217-106">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="df217-107">В этом разделе описывается атрибут <xref:System.Runtime.InteropServices.StructLayoutAttribute>, который используется для определения форматированных типов.</span><span class="sxs-lookup"><span data-stu-id="df217-107">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="df217-108">Для управляемых структур и классов можно выбрать любое из нескольких предсказуемых поведений размещения в перечислении **LayoutKind**.</span><span class="sxs-lookup"><span data-stu-id="df217-108">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="df217-109">Представленные в этом разделе понятия приводятся с учетом важного различия между структурами и типами классов.</span><span class="sxs-lookup"><span data-stu-id="df217-109">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="df217-110">Структуры представляют собой типы значений, а классы — ссылочные типы. В классах всегда реализуется как минимум один уровень косвенного обращения к памяти (указатель на значение).</span><span class="sxs-lookup"><span data-stu-id="df217-110">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="df217-111">Это важное отличие, поскольку неуправляемые функции часто используют косвенное обращение, как показано в сигнатурах в первом столбце в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="df217-111">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="df217-112">Управляемые структуры и объявления классов в оставшихся столбцах демонстрируют, в какой степени можно изменить уровень косвенного обращения в объявлении. Объявления предоставляются как для Visual Basic, так и для Visual C#.</span><span class="sxs-lookup"><span data-stu-id="df217-112">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="df217-113">Неуправляемая сигнатура</span><span class="sxs-lookup"><span data-stu-id="df217-113">Unmanaged signature</span></span>|<span data-ttu-id="df217-114">Управляемое объявление:</span><span class="sxs-lookup"><span data-stu-id="df217-114">Managed declaration:</span></span> <br /><span data-ttu-id="df217-115">без косвенного обращения</span><span class="sxs-lookup"><span data-stu-id="df217-115">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="df217-116">Управляемое объявление:</span><span class="sxs-lookup"><span data-stu-id="df217-116">Managed declaration:</span></span> <br /><span data-ttu-id="df217-117">один уровень косвенного обращения</span><span class="sxs-lookup"><span data-stu-id="df217-117">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="df217-118">Требуется ноль уровней косвенного обращения.</span><span class="sxs-lookup"><span data-stu-id="df217-118">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="df217-119">Добавляет ноль уровней косвенного обращения.</span><span class="sxs-lookup"><span data-stu-id="df217-119">Adds zero levels of indirection.</span></span>|<span data-ttu-id="df217-120">Невозможно, поскольку один уровень косвенного обращения уже существует.</span><span class="sxs-lookup"><span data-stu-id="df217-120">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="df217-121">Требуется один уровень косвенного обращения.</span><span class="sxs-lookup"><span data-stu-id="df217-121">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="df217-122">Добавляет один уровень косвенного обращения.</span><span class="sxs-lookup"><span data-stu-id="df217-122">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="df217-123">Добавляет ноль уровней косвенного обращения.</span><span class="sxs-lookup"><span data-stu-id="df217-123">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="df217-124">Требуется два уровня косвенного обращения.</span><span class="sxs-lookup"><span data-stu-id="df217-124">Demands two levels of indirection.</span></span>|<span data-ttu-id="df217-125">Невозможно, поскольку нельзя использовать **ByRef** **ByRef** или `ref` `ref`.</span><span class="sxs-lookup"><span data-stu-id="df217-125">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="df217-126">Добавляет один уровень косвенного обращения.</span><span class="sxs-lookup"><span data-stu-id="df217-126">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="df217-127">В этой таблице описываются следующие рекомендации по объявлению вызовов неуправляемого кода:</span><span class="sxs-lookup"><span data-stu-id="df217-127">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
- <span data-ttu-id="df217-128">Если неуправляемая функция не требует косвенного обращения, используйте структуру, передаваемую по значению.</span><span class="sxs-lookup"><span data-stu-id="df217-128">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
- <span data-ttu-id="df217-129">Если неуправляемая функция требует один уровень косвенного обращения, используйте передаваемую по ссылке структуру или передаваемый по значению класс.</span><span class="sxs-lookup"><span data-stu-id="df217-129">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
- <span data-ttu-id="df217-130">Если неуправляемая функция требует два уровня косвенного обращения, используйте класс, передаваемый по ссылке.</span><span class="sxs-lookup"><span data-stu-id="df217-130">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="df217-131">Объявление и передача структур</span><span class="sxs-lookup"><span data-stu-id="df217-131">Declaring and Passing Structures</span></span>  

 <span data-ttu-id="df217-132">В следующем примере демонстрируется, как определить структуры `Point` и `Rect` в управляемом коде и передать типы в качестве параметров в функцию **PtInRect** в файле User32.dll.</span><span class="sxs-lookup"><span data-stu-id="df217-132">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="df217-133">Функция **PtInRect** имеет следующую неуправляемую сигнатуру:</span><span class="sxs-lookup"><span data-stu-id="df217-133">**PtInRect** has the following unmanaged signature:</span></span>  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="df217-134">Обратите внимание, что структуру Rect необходимо передавать по ссылке, поскольку функция принимает указатель на тип RECT.</span><span class="sxs-lookup"><span data-stu-id="df217-134">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
    Public x As Integer  
    Public y As Integer  
End Structure  
  
Public Structure <StructLayout(LayoutKind.Explicit)> Rect  
    <FieldOffset(0)> Public left As Integer  
    <FieldOffset(4)> Public top As Integer  
    <FieldOffset(8)> Public right As Integer  
    <FieldOffset(12)> Public bottom As Integer  
End Structure  
  
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "user32.dll" (
        ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
    public int x;  
    public int y;  
}
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
    [FieldOffset(0)] public int left;  
    [FieldOffset(4)] public int top;  
    [FieldOffset(8)] public int right;  
    [FieldOffset(12)] public int bottom;  
}
  
internal static class NativeMethods
{  
    [DllImport("User32.dll")]  
    internal static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="df217-135">Объявление и передача классов</span><span class="sxs-lookup"><span data-stu-id="df217-135">Declaring and Passing Classes</span></span>  

 <span data-ttu-id="df217-136">Члены класса можно передавать в неуправляемую функцию DLL при условии, что класс имеет фиксированное размещение членов.</span><span class="sxs-lookup"><span data-stu-id="df217-136">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="df217-137">В следующем примере демонстрируется, как передать члены класса `MySystemTime`, которые определяются последовательно, в функцию **GetSystemTime** в файле User32.dll.</span><span class="sxs-lookup"><span data-stu-id="df217-137">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="df217-138">Функция **GetSystemTime** имеет следующую неуправляемую сигнатуру:</span><span class="sxs-lookup"><span data-stu-id="df217-138">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="df217-139">В отличие от типов значений, классы всегда имеют как минимум один уровень косвенного обращения.</span><span class="sxs-lookup"><span data-stu-id="df217-139">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Class MySystemTime  
    Public wYear As Short  
    Public wMonth As Short  
    Public wDayOfWeek As Short
    Public wDay As Short  
    Public wHour As Short  
    Public wMinute As Short  
    Public wSecond As Short  
    Public wMiliseconds As Short  
End Class  
  
Friend Class NativeMethods  
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        sysTime As MySystemTime)  
    Friend Declare Auto Function MessageBox Lib "User32.dll" (
        hWnd As IntPtr, lpText As String, lpCaption As String, uType As UInteger) As Integer  
End Class  
  
Public Class TestPlatformInvoke
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        NativeMethods.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)
    End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class MySystemTime {  
    public ushort wYear;
    public ushort wMonth;  
    public ushort wDayOfWeek;
    public ushort wDay;
    public ushort wHour;
    public ushort wMinute;
    public ushort wSecond;
    public ushort wMilliseconds;
}  
internal static class NativeMethods
{  
    [DllImport("Kernel32.dll")]  
    internal static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet = CharSet.Auto)]  
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        NativeMethods.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="df217-140">См. также</span><span class="sxs-lookup"><span data-stu-id="df217-140">See also</span></span>

- [<span data-ttu-id="df217-141">Вызов функции DLL</span><span class="sxs-lookup"><span data-stu-id="df217-141">Calling a DLL Function</span></span>](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
