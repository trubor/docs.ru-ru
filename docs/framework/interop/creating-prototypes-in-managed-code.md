---
title: Создание прототипов в управляемом коде
description: Создайте прототипы в управляемом коде .NET для доступа к неуправляемым функциям и использования полей атрибутов, которые уточняют определение метода в управляемом коде.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- prototypes in managed code
- COM interop, DLL functions
- unmanaged functions
- platform invoke, creating prototypes
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, object fields
- DLL functions
- object fields in platform invoke
ms.assetid: ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d
ms.openlocfilehash: 4260bc8b3f9a2550faa28dd4d35842327b4e5935
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244110"
---
# <a name="creating-prototypes-in-managed-code"></a><span data-ttu-id="6732e-103">Создание прототипов в управляемом коде</span><span class="sxs-lookup"><span data-stu-id="6732e-103">Creating Prototypes in Managed Code</span></span>

<span data-ttu-id="6732e-104">В этом разделе описывается доступ к неуправляемым функциям и представлено несколько полей атрибутов, которые уточняют определение метода в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="6732e-104">This topic describes how to access unmanaged functions and introduces several attribute fields that annotate method definition in managed code.</span></span> <span data-ttu-id="6732e-105">Примеры, демонстрирующие создание объявлений на основе .NET, которые используются с вызовом неуправляемого кода, см. в разделе [Маршалинг данных при вызове неуправляемого кода](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="6732e-105">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
 <span data-ttu-id="6732e-106">Чтобы обратиться к неуправляемой функции DLL из управляемого кода, нужно знать ее имя и имя библиотеки DLL, которая ее экспортирует.</span><span class="sxs-lookup"><span data-stu-id="6732e-106">Before you can access an unmanaged DLL function from managed code, you need to know the name of the function and the name of the DLL that exports it.</span></span> <span data-ttu-id="6732e-107">Имея эту информацию, можно приступать к написанию управляемого определения для неуправляемой функции, реализованной в библиотеке DLL.</span><span class="sxs-lookup"><span data-stu-id="6732e-107">With this information, you can begin to write the managed definition for an unmanaged function that is implemented in a DLL.</span></span> <span data-ttu-id="6732e-108">Кроме того, можно настроить способ, которым вызов неуправляемого кода создает функцию и маршалирует данные в функцию и обратно.</span><span class="sxs-lookup"><span data-stu-id="6732e-108">Furthermore, you can adjust the way that platform invoke creates the function and marshals data to and from the function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6732e-109">Функции API Windows, которые распределяют строку и позволяют освободить строку с помощью такого метода, как `LocalFree`.</span><span class="sxs-lookup"><span data-stu-id="6732e-109">Windows API functions that allocate a string enable you to free the string by using a method such as `LocalFree`.</span></span> <span data-ttu-id="6732e-110">Вызов неуправляемого кода обрабатывает эти параметры иначе.</span><span class="sxs-lookup"><span data-stu-id="6732e-110">Platform invoke handles such parameters differently.</span></span> <span data-ttu-id="6732e-111">Для вызовов неуправляемого кода следует использовать параметр типа `IntPtr`, а не `String`.</span><span class="sxs-lookup"><span data-stu-id="6732e-111">For platform invoke calls, make the parameter an `IntPtr` type instead of a `String` type.</span></span> <span data-ttu-id="6732e-112">Чтобы вручную преобразовать тип в строку и вручную освободить его, можно использовать методы, предоставленные классом <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6732e-112">Use methods that are provided by the <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> class to convert the type to a string manually and free it manually.</span></span>  
  
## <a name="declaration-basics"></a><span data-ttu-id="6732e-113">Основы объявления</span><span class="sxs-lookup"><span data-stu-id="6732e-113">Declaration Basics</span></span>  

 <span data-ttu-id="6732e-114">Как показано в примерах ниже, управляемые определения неуправляемых функций зависят от используемого языка.</span><span class="sxs-lookup"><span data-stu-id="6732e-114">Managed definitions to unmanaged functions are language-dependent, as you can see in the following examples.</span></span> <span data-ttu-id="6732e-115">Более полные примеры кода представлены в разделе [Примеры вызовов неуправляемого кода](platform-invoke-examples.md).</span><span class="sxs-lookup"><span data-stu-id="6732e-115">For more complete code examples, see [Platform Invoke Examples](platform-invoke-examples.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 <span data-ttu-id="6732e-116">Для применения полей <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType> или <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> к объявлению Visual Basic необходимо использовать атрибут <xref:System.Runtime.InteropServices.DllImportAttribute> вместо оператора `Declare`.</span><span class="sxs-lookup"><span data-stu-id="6732e-116">To apply the <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType>, or <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> fields to a Visual Basic declaration, you must use the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute instead of the `Declare` statement.</span></span>  
  
```vb
Imports System.Runtime.InteropServices

Friend Class NativeMethods
    <DllImport("user32.dll", CharSet:=CharSet.Auto)>
    Friend Shared Function MessageBox(
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
    End Function
End Class
```
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("user32.dll")]
extern "C" int MessageBox(
    IntPtr hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="adjusting-the-definition"></a><span data-ttu-id="6732e-117">Настройка определения</span><span class="sxs-lookup"><span data-stu-id="6732e-117">Adjusting the Definition</span></span>  

 <span data-ttu-id="6732e-118">Поля атрибутов, заданные явно или неявно, определяют выполнение управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="6732e-118">Whether you set them explicitly or not, attribute fields are at work defining the behavior of managed code.</span></span> <span data-ttu-id="6732e-119">Вызов неуправляемого кода выполняется в соответствии с набором значений по умолчанию различных полей, хранящихся в сборке как метаданные.</span><span class="sxs-lookup"><span data-stu-id="6732e-119">Platform invoke operates according to the default values set on various fields that exist as metadata in an assembly.</span></span> <span data-ttu-id="6732e-120">Это поведение по умолчанию можно изменить, настроив значения одного или нескольких полей.</span><span class="sxs-lookup"><span data-stu-id="6732e-120">You can alter this default behavior by adjusting the values of one or more fields.</span></span> <span data-ttu-id="6732e-121">Во многих случаях для установки значения используется <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6732e-121">In many cases, you use the <xref:System.Runtime.InteropServices.DllImportAttribute> to set a value.</span></span>  
  
 <span data-ttu-id="6732e-122">Ниже приведен полный набор полей атрибутов, относящихся к вызову неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="6732e-122">The following table lists the complete set of attribute fields that pertain to platform invoke.</span></span> <span data-ttu-id="6732e-123">Для каждого поля в таблице указано значение по умолчанию и дана ссылка на инструкцию по использованию поля для определения неуправляемых функций DLL.</span><span class="sxs-lookup"><span data-stu-id="6732e-123">For each field, the table includes the default value and a link to information on how to use these fields to define unmanaged DLL functions.</span></span>  
  
|<span data-ttu-id="6732e-124">Поле</span><span class="sxs-lookup"><span data-stu-id="6732e-124">Field</span></span>|<span data-ttu-id="6732e-125">Описание</span><span class="sxs-lookup"><span data-stu-id="6732e-125">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|<span data-ttu-id="6732e-126">Включает или отключает наилучшее сопоставление.</span><span class="sxs-lookup"><span data-stu-id="6732e-126">Enables or disables best-fit mapping.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|<span data-ttu-id="6732e-127">Задает соглашение о вызовах, которое должно использоваться при передаче аргументов методов.</span><span class="sxs-lookup"><span data-stu-id="6732e-127">Specifies the calling convention to use in passing method arguments.</span></span> <span data-ttu-id="6732e-128">Значение по умолчанию — `WinAPI`, что соответствует режиму `__stdcall` для 32-разрядных платформ на базе процессора Intel.</span><span class="sxs-lookup"><span data-stu-id="6732e-128">The default is `WinAPI`, which corresponds to `__stdcall` for the 32-bit Intel-based platforms.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|<span data-ttu-id="6732e-129">Управляет декорированием имен и способом маршалинга строковых аргументов в функцию.</span><span class="sxs-lookup"><span data-stu-id="6732e-129">Controls name mangling and the way that string arguments should be marshaled to the function.</span></span> <span data-ttu-id="6732e-130">Значение по умолчанию — `CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="6732e-130">The default is `CharSet.Ansi`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|<span data-ttu-id="6732e-131">Указывает точку входа DLL для вызова.</span><span class="sxs-lookup"><span data-stu-id="6732e-131">Specifies the DLL entry point to be called.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|<span data-ttu-id="6732e-132">Определяет, должна ли изменяться точка входа в соответствии с кодировкой.</span><span class="sxs-lookup"><span data-stu-id="6732e-132">Controls whether an entry point should be modified to correspond to the character set.</span></span> <span data-ttu-id="6732e-133">Значение по умолчанию зависит от языка программирования.</span><span class="sxs-lookup"><span data-stu-id="6732e-133">The default value varies by programming language.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|<span data-ttu-id="6732e-134">Определяет, должна ли сигнатура управляемого метода преобразовываться в неуправляемую сигнатуру, которая возвращает значение HRESULT и имеет дополнительный аргумент [out, retval] для возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="6732e-134">Controls whether the managed method signature should be transformed into an unmanaged signature that returns an HRESULT and has an additional [out, retval] argument for the return value.</span></span><br /><br /> <span data-ttu-id="6732e-135">Значение по умолчанию — `true` (сигнатура не должна преобразовываться).</span><span class="sxs-lookup"><span data-stu-id="6732e-135">The default is `true` (the signature should not be transformed).</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|<span data-ttu-id="6732e-136">Позволяет вызывающему объекту использовать функцию интерфейса API `Marshal.GetLastWin32Error` для определения факта ошибки при выполнении метода.</span><span class="sxs-lookup"><span data-stu-id="6732e-136">Enables the caller to use the `Marshal.GetLastWin32Error` API function to determine whether an error occurred while executing the method.</span></span> <span data-ttu-id="6732e-137">В Visual Basic значение по умолчанию — `true`, а в C# и C++ — `false`.</span><span class="sxs-lookup"><span data-stu-id="6732e-137">In Visual Basic, the default is `true`; in C# and C++, the default is `false`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|<span data-ttu-id="6732e-138">Управляет возникновением исключения при появлении несопоставимого символа Юникода, который преобразуется в символ ANSI "?".</span><span class="sxs-lookup"><span data-stu-id="6732e-138">Controls throwing of an exception on an unmappable Unicode character that is converted to an ANSI "?" character.</span></span>|  
  
 <span data-ttu-id="6732e-139">Дополнительные справочные сведения см. в разделе <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6732e-139">For detailed reference information, see <xref:System.Runtime.InteropServices.DllImportAttribute>.</span></span>  
  
## <a name="platform-invoke-security-considerations"></a><span data-ttu-id="6732e-140">Вопросы безопасности при вызове неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="6732e-140">Platform invoke security considerations</span></span>  

 <span data-ttu-id="6732e-141">Члены `Assert`, `Deny` и `PermitOnly` перечисления <xref:System.Security.Permissions.SecurityAction> называются *модификаторами обхода стека*.</span><span class="sxs-lookup"><span data-stu-id="6732e-141">The `Assert`, `Deny`, and `PermitOnly` members of the <xref:System.Security.Permissions.SecurityAction> enumeration are referred to as *stack walk modifiers*.</span></span> <span data-ttu-id="6732e-142">Эти члены игнорируются, если они используются как декларативные атрибуты в объявлениях вызова неуправляемого кода и операторах COM языка IDL.</span><span class="sxs-lookup"><span data-stu-id="6732e-142">These members are ignored if they are used as declarative attributes on platform invoke declarations and COM Interface Definition Language (IDL) statements.</span></span>  
  
### <a name="platform-invoke-examples"></a><span data-ttu-id="6732e-143">Примеры вызовов неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="6732e-143">Platform Invoke Examples</span></span>  

 <span data-ttu-id="6732e-144">Примеры вызовов неуправляемого кода в этом разделе иллюстрируют использование атрибута `RegistryPermission` с модификаторами обхода стека.</span><span class="sxs-lookup"><span data-stu-id="6732e-144">The platform invoke samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="6732e-145">В приведенном ниже примере кода модификаторы <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny` и `PermitOnly` не учитываются.</span><span class="sxs-lookup"><span data-stu-id="6732e-145">In the following example, the <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`, and `PermitOnly` modifiers are ignored.</span></span>  
  
```csharp  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionAssert();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="6732e-146">Однако модификатор `Demand` в следующем примере принимается.</span><span class="sxs-lookup"><span data-stu-id="6732e-146">However, the `Demand` modifier in the following example is accepted.</span></span>  
  
```csharp
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="6732e-147">Модификаторы <xref:System.Security.Permissions.SecurityAction> действительно правильно работают, если они заданы для класса, содержащего (инкапсулирующего) вызов неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="6732e-147"><xref:System.Security.Permissions.SecurityAction> modifiers do work correctly if they are placed on a class that contains (wraps) the platform invoke call.</span></span>  
  
```cpp  
      [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
public ref class PInvokeWrapper  
{  
public:  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
};  
```  
  
```csharp  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
class PInvokeWrapper  
{  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
}  
```  
  
 <span data-ttu-id="6732e-148">Модификаторы <xref:System.Security.Permissions.SecurityAction> также правильно работают в сценарии с вложением, когда они задаются для объекта, выполняющего вызов неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="6732e-148"><xref:System.Security.Permissions.SecurityAction> modifiers also work correctly in a nested scenario where they are placed on the caller of the platform invoke call:</span></span>  
  
```cpp  
      {  
public ref class PInvokeWrapper  
public:  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
  
    [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
};  
```  
  
```csharp  
class PInvokeScenario  
{  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionInternal();  
  
    [RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
}  
```  
  
#### <a name="com-interop-examples"></a><span data-ttu-id="6732e-149">Примеры COM-взаимодействия</span><span class="sxs-lookup"><span data-stu-id="6732e-149">COM Interop Examples</span></span>  

 <span data-ttu-id="6732e-150">Примеры COM-взаимодействия в этом разделе иллюстрируют использование атрибута `RegistryPermission` с модификаторами обхода стека.</span><span class="sxs-lookup"><span data-stu-id="6732e-150">The COM interop samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="6732e-151">В приведенных ниже объявлениях интерфейса COM-взаимодействия модификаторы `Assert`, `Deny` и `PermitOnly` не учитываются по аналогии с примерами вызовов неуправляемого кода в предыдущем разделе.</span><span class="sxs-lookup"><span data-stu-id="6732e-151">The following COM interop interface declarations ignore the `Assert`, `Deny`, and `PermitOnly` modifiers, similarly to the platform invoke examples in the previous section.</span></span>  
  
```csharp
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDenyStubsItf  
{  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
 <span data-ttu-id="6732e-152">Кроме того, модификатор `Demand` недопустим в сценариях объявления интерфейса COM-взаимодействия, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="6732e-152">Additionally, the `Demand` modifier is not accepted in COM interop interface declaration scenarios, as shown in the following example.</span></span>  
  
```csharp  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDemandStubsItf  
{  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6732e-153">См. также</span><span class="sxs-lookup"><span data-stu-id="6732e-153">See also</span></span>

- [<span data-ttu-id="6732e-154">Использование неуправляемых функций DLL</span><span class="sxs-lookup"><span data-stu-id="6732e-154">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="6732e-155">Задание точки входа</span><span class="sxs-lookup"><span data-stu-id="6732e-155">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="6732e-156">Определение кодировки</span><span class="sxs-lookup"><span data-stu-id="6732e-156">Specifying a Character Set</span></span>](specifying-a-character-set.md)
- [<span data-ttu-id="6732e-157">Примеры вызовов неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="6732e-157">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- <span data-ttu-id="6732e-158">[Platform Invoke Security Considerations](/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100)) (Вопросы безопасности при вызове неуправляемого кода)</span><span class="sxs-lookup"><span data-stu-id="6732e-158">[Platform Invoke Security Considerations](/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span></span>
- [<span data-ttu-id="6732e-159">Идентификация функций в библиотеках DLL</span><span class="sxs-lookup"><span data-stu-id="6732e-159">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="6732e-160">Создание класса, содержащего функции DLL</span><span class="sxs-lookup"><span data-stu-id="6732e-160">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="6732e-161">Вызов функции DLL</span><span class="sxs-lookup"><span data-stu-id="6732e-161">Calling a DLL Function</span></span>](calling-a-dll-function.md)
