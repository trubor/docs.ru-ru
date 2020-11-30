---
title: Пользовательская сериализация
description: Пользовательская сериализация — это управление сериализацией и десериализацией типа. Управление сериализацией может обеспечить совместимость сериализации.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binary serialization, custom serialization
- custom serialization
- binary serialization, controlling
- OptionalFieldAttribute class, custom serialization
- ISerializable interface, custom serialization
- OnDeserializingAttribute class, custom serialization
- OnSerializedAttribute class, custom serialization
- serialization, custom serialization
- serialization, controlling
- OnDeserializedAttribute class, custom serialization
- OnSerializingAttribute class, custom serialization
ms.assetid: 12ed422d-5280-49b8-9b71-a2ed129c0384
ms.openlocfilehash: 4ca78c71f464a914c07583825d4a7027ebb11bf6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679043"
---
# <a name="custom-serialization"></a><span data-ttu-id="863d0-104">Пользовательская сериализация</span><span class="sxs-lookup"><span data-stu-id="863d0-104">Custom serialization</span></span>

<span data-ttu-id="863d0-105">Пользовательской сериализацией называется процесс управления сериализацией и десериализацией типа.</span><span class="sxs-lookup"><span data-stu-id="863d0-105">Custom serialization is the process of controlling the serialization and deserialization of a type.</span></span> <span data-ttu-id="863d0-106">Управление сериализацией позволяет обеспечить совместимость сериализации, в результате чего становится возможной сериализация и десериализация между различными версиями типа без нарушения основных функциональных возможностей типа.</span><span class="sxs-lookup"><span data-stu-id="863d0-106">By controlling serialization, it's possible to ensure serialization compatibility, which is the ability to serialize and deserialize between versions of a type without breaking the core functionality of the type.</span></span> <span data-ttu-id="863d0-107">Например, в первой версии типа может быть только два поля.</span><span class="sxs-lookup"><span data-stu-id="863d0-107">For example, in the first version of a type, there may be only two fields.</span></span> <span data-ttu-id="863d0-108">В следующей версии типа добавлено еще несколько полей.</span><span class="sxs-lookup"><span data-stu-id="863d0-108">In the next version of a type, several more fields are added.</span></span> <span data-ttu-id="863d0-109">Во второй версии приложения должна быть предусмотрена возможность сериализации и десериализации обоих типов.</span><span class="sxs-lookup"><span data-stu-id="863d0-109">Yet the second version of an application must be able to serialize and deserialize both types.</span></span> <span data-ttu-id="863d0-110">В следующих разделах объясняется, как управлять сериализацией.</span><span class="sxs-lookup"><span data-stu-id="863d0-110">The following sections describe how to control serialization.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
> <span data-ttu-id="863d0-111">В версиях до .NET Framework 4.0 сериализация пользовательских данных в сборке с частичным доверием выполнялась методом `GetObjectData`.</span><span class="sxs-lookup"><span data-stu-id="863d0-111">In versions previous to .NET Framework 4.0, serialization of custom user data in a partially trusted assembly was accomplished using `GetObjectData`.</span></span> <span data-ttu-id="863d0-112">Начиная с версии 4.0 этот метод помечен атрибутом <xref:System.Security.SecurityCriticalAttribute>, который запрещает выполнение в сборках с частичным доверием.</span><span class="sxs-lookup"><span data-stu-id="863d0-112">Starting with version 4.0, that method is marked with the <xref:System.Security.SecurityCriticalAttribute> attribute, which prevents execution in partially trusted assemblies.</span></span> <span data-ttu-id="863d0-113">Чтобы решить эту проблему, реализуйте интерфейс <xref:System.Runtime.Serialization.ISafeSerializationData>.</span><span class="sxs-lookup"><span data-stu-id="863d0-113">To work around this condition, implement the <xref:System.Runtime.Serialization.ISafeSerializationData> interface.</span></span>  
  
## <a name="running-custom-methods-during-and-after-serialization"></a><span data-ttu-id="863d0-114">Использование пользовательских методов во время сериализации и после нее</span><span class="sxs-lookup"><span data-stu-id="863d0-114">Running custom methods during and after serialization</span></span>

<span data-ttu-id="863d0-115">Для выполнения настраиваемых методов во время и после сериализации рекомендуем применять следующие атрибуты к методам, которые используются для исправления данных во время и после сериализации:</span><span class="sxs-lookup"><span data-stu-id="863d0-115">The recommended way to run custom methods during and after serialization is to apply the following attributes to methods that are used to correct data during and after serialization:</span></span>  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 <span data-ttu-id="863d0-116">Эти атрибуты обеспечивают использование типа на любом или на всех четырех этапах процесса сериализации и десериализации.</span><span class="sxs-lookup"><span data-stu-id="863d0-116">These attributes allow the type to participate in any one of, or all four of the phases, of the serialization and deserialization processes.</span></span> <span data-ttu-id="863d0-117">Атрибуты определяют методы типа, которые должны вызываться на каждом этапе.</span><span class="sxs-lookup"><span data-stu-id="863d0-117">The attributes specify the methods of the type that should be invoked during each phase.</span></span> <span data-ttu-id="863d0-118">Доступ методов к потоку сериализации отсутствует, однако можно изменить объект перед сериализацией и после нее или перед десериализацией и после нее.</span><span class="sxs-lookup"><span data-stu-id="863d0-118">The methods do not access the serialization stream but instead allow you to alter the object before and after serialization, or before and after deserialization.</span></span> <span data-ttu-id="863d0-119">Атрибуты можно применять на всех уровнях иерархии наследования типов, и каждый метод вызывается в иерархии от базового до самого дальнего в цепочке наследования.</span><span class="sxs-lookup"><span data-stu-id="863d0-119">The attributes can be applied at all levels of the type inheritance hierarchy, and each method is called in the hierarchy from the base to the most derived.</span></span> <span data-ttu-id="863d0-120">Этот механизм позволяет избежать усложненности и каких-либо проблем реализации интерфейса <xref:System.Runtime.Serialization.ISerializable>, передав процесс сериализации и десериализации самой дальней в цепочке наследования реализации.</span><span class="sxs-lookup"><span data-stu-id="863d0-120">This mechanism avoids the complexity and any resulting issues of implementing the <xref:System.Runtime.Serialization.ISerializable> interface by giving the responsibility for serialization and deserialization to the most derived implementation.</span></span> <span data-ttu-id="863d0-121">Кроме того, благодаря такому механизму модули форматирования могут игнорировать заполнение полей и извлечение данных из потока сериализации.</span><span class="sxs-lookup"><span data-stu-id="863d0-121">Additionally, this mechanism allows the formatters to ignore the population of fields and retrieval from the serialization stream.</span></span> <span data-ttu-id="863d0-122">Дополнительные сведения и примеры управления сериализацией и десериализацией см. по ссылкам выше.</span><span class="sxs-lookup"><span data-stu-id="863d0-122">For details and examples of controlling serialization and deserialization, click any of the previous links.</span></span>  
  
 <span data-ttu-id="863d0-123">Кроме того, при добавлении нового поля в существующий сериализуемый тип применяйте к полю атрибут <xref:System.Runtime.Serialization.OptionalFieldAttribute>.</span><span class="sxs-lookup"><span data-stu-id="863d0-123">In addition, when adding a new field to an existing serializable type, apply the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to the field.</span></span> <span data-ttu-id="863d0-124"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> и <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> игнорируют отсутствие поля, если обрабатывается поток без нового поля.</span><span class="sxs-lookup"><span data-stu-id="863d0-124">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignores the absence of the field when a stream that is missing the new field is processed.</span></span>  
  
## <a name="implementing-the-iserializable-interface"></a><span data-ttu-id="863d0-125">Реализация интерфейса ISerializable</span><span class="sxs-lookup"><span data-stu-id="863d0-125">Implementing the ISerializable interface</span></span>  

 <span data-ttu-id="863d0-126">Еще одним способом управления сериализацией является реализация для объекта интерфейса <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="863d0-126">The other way to control serialization is achieved by implementing the <xref:System.Runtime.Serialization.ISerializable> interface on an object.</span></span> <span data-ttu-id="863d0-127">Однако следует помнить, что метод, описанный в предыдущем разделе, замещает этот метод управления сериализацией.</span><span class="sxs-lookup"><span data-stu-id="863d0-127">Note, however, that the method in the previous section supersedes this method to control serialization.</span></span>  
  
 <span data-ttu-id="863d0-128">Кроме того, не следует использовать сериализацию по умолчанию для класса, который отмечен атрибутом [Serializable](xref:System.SerializableAttribute) и имеет декларативную или принудительную безопасность на уровне класса или конструкторов.</span><span class="sxs-lookup"><span data-stu-id="863d0-128">In addition, you should not use default serialization on a class that is marked with the [Serializable](xref:System.SerializableAttribute) attribute and has declarative or imperative security at the class level or on its constructors.</span></span> <span data-ttu-id="863d0-129">В таких случаях в классах всегда следует реализовывать интерфейс <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="863d0-129">Instead, these classes should always implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 <span data-ttu-id="863d0-130">Реализация <xref:System.Runtime.Serialization.ISerializable> включает реализацию метода `GetObjectData` и специального конструктора, который используется при десериализации объекта.</span><span class="sxs-lookup"><span data-stu-id="863d0-130">Implementing <xref:System.Runtime.Serialization.ISerializable> involves implementing the `GetObjectData` method and a special constructor that is used when the object is deserialized.</span></span> <span data-ttu-id="863d0-131">В следующем образце кода показано, как реализовать <xref:System.Runtime.Serialization.ISerializable> в классе `MyObject` на основе информации предыдущего раздела.</span><span class="sxs-lookup"><span data-stu-id="863d0-131">The following sample code shows how to implement <xref:System.Runtime.Serialization.ISerializable> on the `MyObject` class from a previous section.</span></span>  
  
```csharp
[Serializable]
public class MyObject : ISerializable
{
    public int n1;
    public int n2;
    public String str;

    public MyObject()
    {
    }

    protected MyObject(SerializationInfo info, StreamingContext context)
    {
      n1 = info.GetInt32("i");
      n2 = info.GetInt32("j");
      str = info.GetString("k");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public virtual void GetObjectData(SerializationInfo info, StreamingContext context)
    {
        info.AddValue("i", n1);
        info.AddValue("j", n2);
        info.AddValue("k", str);
    }
}
```

```vb
<Serializable()>  _
Public Class MyObject
    Implements ISerializable
    Public n1 As Integer
    Public n2 As Integer
    Public str As String

    Public Sub New()
    End Sub

    Protected Sub New(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        n1 = info.GetInt32("i")
        n2 = info.GetInt32("j")
        str = info.GetString("k")
    End Sub 'New

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overridable Sub GetObjectData(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        info.AddValue("i", n1)
        info.AddValue("j", n2)
        info.AddValue("k", str)
    End Sub
End Class
```  
  
 <span data-ttu-id="863d0-132">Если во время сериализации вызывается **GetObjectData**, следует указать информацию <xref:System.Runtime.Serialization.SerializationInfo>, которая предоставляется вместе с вызовом метода.</span><span class="sxs-lookup"><span data-stu-id="863d0-132">When **GetObjectData** is called during serialization, you are responsible for populating the <xref:System.Runtime.Serialization.SerializationInfo> provided with the method call.</span></span> <span data-ttu-id="863d0-133">Добавьте переменные, которые будут сериализованы как пары имен и значений.</span><span class="sxs-lookup"><span data-stu-id="863d0-133">Add the variables to be serialized as name and value pairs.</span></span> <span data-ttu-id="863d0-134">В качестве имени можно ввести любой текст.</span><span class="sxs-lookup"><span data-stu-id="863d0-134">Any text can be used as the name.</span></span> <span data-ttu-id="863d0-135">Переменные-члены, добавляемые в <xref:System.Runtime.Serialization.SerializationInfo> могут быть любыми при условии, что сериализуется достаточное количество данных для восстановления объекта при десериализации.</span><span class="sxs-lookup"><span data-stu-id="863d0-135">You have the freedom to decide which member variables are added to the <xref:System.Runtime.Serialization.SerializationInfo>, provided that sufficient data is serialized to restore the object during deserialization.</span></span> <span data-ttu-id="863d0-136">Производные классы должны вызывать метод **GetObjectData** для базового объекта, если в последнем реализован интерфейс <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="863d0-136">Derived classes should call the **GetObjectData** method on the base object if the latter implements <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
 <span data-ttu-id="863d0-137">Обратите внимание, что сериализация позволяет другому коду просматривать или изменять данные экземпляра объекта, не доступные в ином случае.</span><span class="sxs-lookup"><span data-stu-id="863d0-137">Note that serialization can allow other code to see or modify object instance data that is otherwise inaccessible.</span></span> <span data-ttu-id="863d0-138">Поэтому код, выполняющий сериализацию, требует разрешения [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) с установленным флагом <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter>.</span><span class="sxs-lookup"><span data-stu-id="863d0-138">Therefore, code that performs serialization requires the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="863d0-139">При политике безопасности по умолчанию такое разрешение не предоставляется коду, загруженному из Интернета или интрасети, и дается только коду на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="863d0-139">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span> <span data-ttu-id="863d0-140">Метод **GetObjectData** должен быть явно защищен посредством запроса либо [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) с установленным флагом <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter>, либо иных разрешений, которые предназначены специально для защиты закрытых данных.</span><span class="sxs-lookup"><span data-stu-id="863d0-140">The **GetObjectData** method must be explicitly protected either by demanding the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified or by demanding other permissions that specifically help protect private data.</span></span>  
  
 <span data-ttu-id="863d0-141">Если в закрытом поле хранятся конфиденциальные сведения, для их защиты следует запрашивать соответствующие разрешения для **GetObjectData**.</span><span class="sxs-lookup"><span data-stu-id="863d0-141">If a private field stores sensitive information, you should demand the appropriate permissions on **GetObjectData** to protect the data.</span></span> <span data-ttu-id="863d0-142">Помните, что код, которому предоставлены разрешения [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) с установленным флагом **SerializationFormatter**, может просматривать и изменять данные, которые хранятся в закрытых полях.</span><span class="sxs-lookup"><span data-stu-id="863d0-142">Remember that code that has been granted [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the **SerializationFormatter** flag specified can view and modify the data stored in private fields.</span></span> <span data-ttu-id="863d0-143">Злонамеренный вызывающий объект с предоставленными разрешениями [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) может просматривать такие данные, как местоположения скрытых каталогов или предоставленные разрешения, и использовать такую информацию для повышения уязвимости системы безопасности компьютера.</span><span class="sxs-lookup"><span data-stu-id="863d0-143">A malicious caller granted this [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) can view data such as hidden directory locations or granted permissions and use the data to exploit a security vulnerability on the computer.</span></span> <span data-ttu-id="863d0-144">Полный список устанавливаемых флагов разрешений безопасности представлен в перечислении [SecurityPermissionFlag Enumeration](xref:System.Security.Permissions.SecurityPermissionFlag).</span><span class="sxs-lookup"><span data-stu-id="863d0-144">For a complete list of the security permission flags you can specify, see the [SecurityPermissionFlag Enumeration](xref:System.Security.Permissions.SecurityPermissionFlag).</span></span>  
  
 <span data-ttu-id="863d0-145">Следует особо отметить, что при добавлении <xref:System.Runtime.Serialization.ISerializable> в класс следует реализовать и **GetObjectData**, и специальный конструктор.</span><span class="sxs-lookup"><span data-stu-id="863d0-145">It's important to stress that when <xref:System.Runtime.Serialization.ISerializable> is added to a class you must implement both **GetObjectData** and the special constructor.</span></span> <span data-ttu-id="863d0-146">Компилятор выдает предупреждение, если **GetObjectData** отсутствует.</span><span class="sxs-lookup"><span data-stu-id="863d0-146">The compiler warns you if **GetObjectData** is missing.</span></span> <span data-ttu-id="863d0-147">Но поскольку невозможно принудительно реализовать конструктор, при его отсутствии предупреждение не выводится, и при попытке десериализовать класс без конструктора создается исключение.</span><span class="sxs-lookup"><span data-stu-id="863d0-147">However, because it is impossible to enforce the implementation of a constructor, no warning is provided if the constructor is absent, and an exception is thrown when an attempt is made to deserialize a class without the constructor.</span></span>  
  
 <span data-ttu-id="863d0-148">В текущей разработке предусмотрена поддержка метода <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A>, чтобы избежать возможных проблем с безопасностью и управлением версиями.</span><span class="sxs-lookup"><span data-stu-id="863d0-148">The current design was favored above a <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> method to get around potential security and versioning problems.</span></span> <span data-ttu-id="863d0-149">Например, метод `SetObjectData` должен быть открытым, если он определяется как часть интерфейса. По этой причине пользователям следует написать код, чтобы метод **SetObjectData** не вызывался несколько раз.</span><span class="sxs-lookup"><span data-stu-id="863d0-149">For example, a `SetObjectData` method must be public if it is defined as part of an interface; thus users must write code to defend against having the **SetObjectData** method called multiple times.</span></span> <span data-ttu-id="863d0-150">Иначе вредоносное приложение, вызывающее метод **SetObjectData** для объекта в процессе выполнения операции, может стать причиной возникновения проблем.</span><span class="sxs-lookup"><span data-stu-id="863d0-150">Otherwise, a malicious application that calls the **SetObjectData** method on an object in the process of executing an operation can cause potential problems.</span></span>  
  
 <span data-ttu-id="863d0-151">Во время десериализации информация <xref:System.Runtime.Serialization.SerializationInfo> передается классу с помощью предусмотренного для этого конструктора.</span><span class="sxs-lookup"><span data-stu-id="863d0-151">During deserialization, <xref:System.Runtime.Serialization.SerializationInfo> is passed to the class using the constructor provided for this purpose.</span></span> <span data-ttu-id="863d0-152">При десериализации объекта все ограничения видимости, применимые к конструктору, игнорируются, поэтому класс можно отметить как открытый, защищенный, внутренний или закрытый.</span><span class="sxs-lookup"><span data-stu-id="863d0-152">Any visibility constraints placed on the constructor are ignored when the object is deserialized; so you can mark the class as public, protected, internal, or private.</span></span> <span data-ttu-id="863d0-153">Однако рекомендуется защищать конструктор, если только класс не запечатан. В этом случае конструктор следует отметить как закрытый.</span><span class="sxs-lookup"><span data-stu-id="863d0-153">However, it is a best practice to make the constructor protected unless the class is sealed, in which case the constructor should be marked private.</span></span> <span data-ttu-id="863d0-154">Кроме того, конструктор должен выполнять тщательную проверку входных данных.</span><span class="sxs-lookup"><span data-stu-id="863d0-154">The constructor should also perform thorough input validation.</span></span> <span data-ttu-id="863d0-155">Чтобы избежать неправильного использования вредоносным кодом, конструктор должен производить такие же проверки безопасности и наличия необходимых разрешений при попытках получить экземпляр подобного класса с помощью другого конструктора.</span><span class="sxs-lookup"><span data-stu-id="863d0-155">To avoid misuse by malicious code, the constructor should enforce the same security checks and permissions required to obtain an instance of the class using any other constructor.</span></span> <span data-ttu-id="863d0-156">При несоблюдении этой рекомендации вредоносный код может предварительно сериализовать объект, получить контроль над [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) с установленным флагом <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> и десериализовать объект на клиентском компьютере, обойдя любую защиту, которая была реализована во время построения стандартного экземпляра с использованием открытого конструктора.</span><span class="sxs-lookup"><span data-stu-id="863d0-156">If you do not follow this recommendation, malicious code can preserialize an object, obtain control with the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified and deserialize the object on a client computer bypassing any security that would have been applied during standard instance construction using a public constructor.</span></span>  
  
 <span data-ttu-id="863d0-157">Чтобы восстановить состояние объекта, необходимо всего лишь запросить значения переменных из <xref:System.Runtime.Serialization.SerializationInfo> по именам, использованным во время сериализации.</span><span class="sxs-lookup"><span data-stu-id="863d0-157">To restore the state of the object, simply retrieve the values of the variables from <xref:System.Runtime.Serialization.SerializationInfo> using the names used during serialization.</span></span> <span data-ttu-id="863d0-158">Если в базовом классе реализовано <xref:System.Runtime.Serialization.ISerializable>, следует вызвать базовый конструктор, чтобы базовый объект смог восстановить свои переменные.</span><span class="sxs-lookup"><span data-stu-id="863d0-158">If the base class implements <xref:System.Runtime.Serialization.ISerializable>, the base constructor should be called to allow the base object to restore its variables.</span></span>  
  
 <span data-ttu-id="863d0-159">При создании нового производного класса на основе класса с реализацией <xref:System.Runtime.Serialization.ISerializable> в производном классе должны быть реализованы как конструктор, так и метод **GetObjectData**, если имеются переменные, подлежащие сериализации.</span><span class="sxs-lookup"><span data-stu-id="863d0-159">When you derive a new class from one that implements <xref:System.Runtime.Serialization.ISerializable>, the derived class must implement both the constructor as well as the **GetObjectData** method if it has variables that need to be serialized.</span></span> <span data-ttu-id="863d0-160">В следующем примере показано, как это можно сделать с помощью рассмотренного ранее класса `MyObject`.</span><span class="sxs-lookup"><span data-stu-id="863d0-160">The following code example shows how this is done using the `MyObject` class shown previously.</span></span>  
  
```csharp
[Serializable]
public class ObjectTwo : MyObject
{
    public int num;

    public ObjectTwo()
      : base()
    {
    }

    protected ObjectTwo(SerializationInfo si, StreamingContext context)
      : base(si, context)
    {
        num = si.GetInt32("num");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public override void GetObjectData(SerializationInfo si, StreamingContext context)
    {
        base.GetObjectData(si,context);
        si.AddValue("num", num);
    }
}
```

```vb
<Serializable()>  _
Public Class ObjectTwo
    Inherits MyObject
    Public num As Integer

    Public Sub New()

    End Sub

    Protected Sub New(ByVal si As SerializationInfo, _
    ByVal context As StreamingContext)
        MyBase.New(si, context)
        num = si.GetInt32("num")
    End Sub

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overrides Sub GetObjectData(ByVal si As SerializationInfo, ByVal context As StreamingContext)
        MyBase.GetObjectData(si, context)
        si.AddValue("num", num)
    End Sub
End Class
```  
  
 <span data-ttu-id="863d0-161">Не забудьте вызвать базовый класс в конструкторе десериализации.</span><span class="sxs-lookup"><span data-stu-id="863d0-161">Don't forget to call the base class in the deserialization constructor.</span></span> <span data-ttu-id="863d0-162">Если этого не сделать, конструктор для базового класса никогда не вызывается, и после десериализации объект не является полностью построенным.</span><span class="sxs-lookup"><span data-stu-id="863d0-162">If this isn't done, the constructor on the base class is never called, and the object is not fully constructed after deserialization.</span></span>  
  
 <span data-ttu-id="863d0-163">Объекты воссоздаются изнутри, вызов методов во время десериализации может привести к нежелательным побочным эффектам, поскольку вызываемые объекты могут относиться к ссылкам на объекты, которые не были десериализованы на момент вызова.</span><span class="sxs-lookup"><span data-stu-id="863d0-163">Objects are reconstructed from the inside out; and calling methods during deserialization can have undesirable side effects, because the methods called might refer to object references that have not been deserialized by the time the call is made.</span></span> <span data-ttu-id="863d0-164">Если в десериализуемом классе реализовано <xref:System.Runtime.Serialization.IDeserializationCallback>, во время десериализации всего графа объекта автоматически вызывается метод <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A>.</span><span class="sxs-lookup"><span data-stu-id="863d0-164">If the class being deserialized implements the <xref:System.Runtime.Serialization.IDeserializationCallback>, the <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> method is automatically called when the entire object graph has been deserialized.</span></span> <span data-ttu-id="863d0-165">На этом этапе все дочерние объекты, на которые имеются ссылки, полностью восстановлены.</span><span class="sxs-lookup"><span data-stu-id="863d0-165">At this point, all the child objects referenced have been fully restored.</span></span> <span data-ttu-id="863d0-166">Типичным примером класса, который сложно десериализовать без использования прослушивателя событий, служит хэш-таблица.</span><span class="sxs-lookup"><span data-stu-id="863d0-166">A hash table is a typical example of a class that is difficult to deserialize without using the event listener.</span></span> <span data-ttu-id="863d0-167">Вызов пар "ключ-значение" во время десериализации не представляет сложности, однако добавление таких объектов обратно в хэш-таблицу может быть затруднительным, поскольку нет никаких гарантий, что производные на основе хэш-таблицы классы десериализованы.</span><span class="sxs-lookup"><span data-stu-id="863d0-167">It is easy to retrieve the key and value pairs during deserialization, but adding these objects back to the hash table can cause problems, because there is no guarantee that classes that derived from the hash table have been deserialized.</span></span> <span data-ttu-id="863d0-168">Поэтому на данном этапе не рекомендуется вызывать методы для хэш-таблицы.</span><span class="sxs-lookup"><span data-stu-id="863d0-168">Calling methods on a hash table at this stage is therefore not advisable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="863d0-169">См. также</span><span class="sxs-lookup"><span data-stu-id="863d0-169">See also</span></span>

- [<span data-ttu-id="863d0-170">Двоичная сериализация</span><span class="sxs-lookup"><span data-stu-id="863d0-170">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="863d0-171">Сериализация XML и SOAP</span><span class="sxs-lookup"><span data-stu-id="863d0-171">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="863d0-172">Безопасность и сериализация</span><span class="sxs-lookup"><span data-stu-id="863d0-172">Security and Serialization</span></span>](../../framework/misc/security-and-serialization.md)
