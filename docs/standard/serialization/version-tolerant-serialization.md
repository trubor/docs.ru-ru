---
title: Независимая от версий сериализация
description: Сведения о независимой от версий сериализации (набор функций, которые упрощают изменение сериализуемых типов).
ms.date: 08/08/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- version tolerant serialization
- serialization, custom serialization
- serialization, version tolerant
- serialization, controlling
- versions and serialization
- BinaryFormatter class, samples
- serialization, attributes
ms.assetid: bea0ffe3-2708-4a16-ac7d-e586ed6b8e8d
ms.openlocfilehash: 26612c5b0591efa61fcd476733aee2b219d67c62
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96438158"
---
# <a name="version-tolerant-serialization"></a><span data-ttu-id="2a6d5-103">Независимая от версий сериализация</span><span class="sxs-lookup"><span data-stu-id="2a6d5-103">Version tolerant serialization</span></span>

<span data-ttu-id="2a6d5-104">В последних версиях .NET Framework создание сериализуемых типов, которые можно повторно использовать от одной версии приложения к другой, было проблематичным.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-104">In the earliest versions of .NET Framework, creating serializable types that would be reusable from one version of an application to the next was problematic.</span></span> <span data-ttu-id="2a6d5-105">Если тип был изменен путем добавления дополнительных полей, возникала следующая проблема:</span><span class="sxs-lookup"><span data-stu-id="2a6d5-105">If a type was modified by adding extra fields, the following problems would occur:</span></span>

- <span data-ttu-id="2a6d5-106">Приложения старых версий выдадут исключения при запросе десериализации новых версий старого типа.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-106">Older versions of an application would throw exceptions when asked to deserialize new versions of the old type.</span></span>
- <span data-ttu-id="2a6d5-107">Приложения более новых версий выдадут исключения при десериализации старых версий типа с отсутствующими данными.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-107">Newer versions of an application would throw exceptions when deserializing older versions of a type with missing data.</span></span>

<span data-ttu-id="2a6d5-108">Независимая от версий сериализация (VTS) является набором функций, которые со временем упрощают изменение сериализуемых типов.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-108">Version Tolerant Serialization (VTS) is a set of features that makes it easier, over time, to modify serializable types.</span></span> <span data-ttu-id="2a6d5-109">В частности, функции VTS доступны для классов, к которым применен атрибут <xref:System.SerializableAttribute>, включая универсальные типы.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-109">Specifically, the VTS features are enabled for classes to which the <xref:System.SerializableAttribute> attribute has been applied, including generic types.</span></span> <span data-ttu-id="2a6d5-110">VTS позволяет добавлять новые поля для таких классов, не нарушая совместимости с другими версиями типа.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-110">VTS makes it possible to add new fields to those classes without breaking compatibility with other versions of the type.</span></span>

<span data-ttu-id="2a6d5-111">Функции VTS доступны при использовании <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-111">The VTS features are enabled when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="2a6d5-112">Кроме того, при использовании <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> доступны все функции, за исключением допустимости лишних данных.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-112">Additionally, all features except extraneous data tolerance are also enabled when using the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="2a6d5-113">Дополнительные сведения об использовании этих классов для сериализации см. в разделе [Двоичная сериализация](binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="2a6d5-113">For more information about using these classes for serialization, see [Binary Serialization](binary-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a><span data-ttu-id="2a6d5-114">Список функций</span><span class="sxs-lookup"><span data-stu-id="2a6d5-114">Feature list</span></span>

<span data-ttu-id="2a6d5-115">Набор функций включает в себя следующие:</span><span class="sxs-lookup"><span data-stu-id="2a6d5-115">The set of features includes the following:</span></span>

- <span data-ttu-id="2a6d5-116">Допустимость лишних или непредвиденных данных.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-116">Tolerance of extraneous or unexpected data.</span></span> <span data-ttu-id="2a6d5-117">Это позволяет новым версиям типа отправлять данные в старые версии.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-117">This enables newer versions of the type to send data to older versions.</span></span>
- <span data-ttu-id="2a6d5-118">Допустимость отсутствующих необязательных данных.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-118">Tolerance of missing optional data.</span></span> <span data-ttu-id="2a6d5-119">Это позволяет старым версиям отправлять данные в новые версии.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-119">This enables older versions to send data to newer versions.</span></span>
- <span data-ttu-id="2a6d5-120">Обратные вызовы сериализации.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-120">Serialization callbacks.</span></span> <span data-ttu-id="2a6d5-121">Это обеспечивает интеллектуальную настройку значения по умолчанию в случае отсутствия данных.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-121">This enables intelligent default value setting in cases where data is missing.</span></span>

<span data-ttu-id="2a6d5-122">Кроме того, существует функция объявления при добавлении нового необязательного поля.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-122">In addition, there is a feature for declaring when a new optional field has been added.</span></span> <span data-ttu-id="2a6d5-123">Это свойство <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> атрибута <xref:System.Runtime.Serialization.OptionalFieldAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-123">This is the <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> property of the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute.</span></span>

<span data-ttu-id="2a6d5-124">Эти функции подробно описаны в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-124">These features are discussed in greater detail in the following sections.</span></span>

### <a name="tolerance-of-extraneous-or-unexpected-data"></a><span data-ttu-id="2a6d5-125">Допустимость лишних или непредвиденных данных</span><span class="sxs-lookup"><span data-stu-id="2a6d5-125">Tolerance of extraneous or unexpected data</span></span>

<span data-ttu-id="2a6d5-126">В прошлом при десериализации наличие каких-либо лишних или непредвиденных данных приводило к выводу исключения.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-126">In the past, during deserialization, any extraneous or unexpected data caused exceptions to be thrown.</span></span> <span data-ttu-id="2a6d5-127">С использованием VTS в такой же ситуации какие-либо лишние или непредвиденные данные игнорируются, и исключения не выводятся.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-127">With VTS, in the same situation, any extraneous or unexpected data is ignored instead of causing exceptions to be thrown.</span></span> <span data-ttu-id="2a6d5-128">Благодаря этому приложения, использующие более новые версии типа (т.е. версию с большим числом полей), могут отправлять информацию в приложения, ожидающие старые версии этого же типа.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-128">This enables applications that use newer versions of a type (that is, a version that includes more fields) to send information to applications that expect older versions of the same type.</span></span>

<span data-ttu-id="2a6d5-129">В следующем примере дополнительные данные в `CountryField` версии 2.0 класса `Address` игнорируются, когда более старое приложение десериализует новую версию.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-129">In the following example, the extra data contained in the `CountryField` of version 2.0 of the `Address` class is ignored when an older application deserializes the newer version.</span></span>

```csharp  
// Version 1 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
}  
// Version 2.0 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    // The older application ignores this data.  
    public string CountryField;  
}  
```  
  
```vb  
' Version 1 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
End Class  
  
' Version 2.0 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
    ' The older application ignores this data.  
    Public CountryField As String  
End Class  
```  

### <a name="tolerance-of-missing-data"></a><span data-ttu-id="2a6d5-130">Допустимость отсутствующих данных</span><span class="sxs-lookup"><span data-stu-id="2a6d5-130">Tolerance of missing data</span></span>

<span data-ttu-id="2a6d5-131">Поля можно отметить как необязательные, применив к ним атрибут <xref:System.Runtime.Serialization.OptionalFieldAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-131">Fields can be marked as optional by applying the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to them.</span></span> <span data-ttu-id="2a6d5-132">При отсутствии во время десериализации необязательных данных модуль сериализации игнорирует такое отсутствие и не выводит исключение.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-132">During deserialization, if the optional data is missing, the serialization engine ignores the absence and does not throw an exception.</span></span> <span data-ttu-id="2a6d5-133">Поэтому приложения, ожидающие старые версии типа, могут отправлять данные в приложения, ожидающие новые версии этого же типа.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-133">Thus, applications that expect older versions of a type can send data to applications that expect newer versions of the same type.</span></span>

<span data-ttu-id="2a6d5-134">В следующем примере показана версия 2.0 класса `Address` с полем `CountryField`, отмеченным как необязательное.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-134">The following example shows version 2.0 of the `Address` class with the `CountryField` field marked as optional.</span></span> <span data-ttu-id="2a6d5-135">Если приложение более старой версии отправляет версию 1 в новое приложение, ожидающее версии 2.0, отсутствие данных игнорируется.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-135">If an older application sends version 1 to a newer application that expects version 2.0, the absence of the data is ignored.</span></span>

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;

    [OptionalField]
    public string CountryField;
}
```

```vb
<Serializable> _
Public Class Address
    Public Street As String
    Public City As String

    <OptionalField> _
    Public CountryField As String
End Class
```
  
### <a name="serialization-callbacks"></a><span data-ttu-id="2a6d5-136">Обратные вызовы сериализации</span><span class="sxs-lookup"><span data-stu-id="2a6d5-136">Serialization callbacks</span></span>

<span data-ttu-id="2a6d5-137">Обратные вызовы сериализации являются механизмом, который предоставляет обработчики для процесса сериализации и десериализации в четырех точках.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-137">Serialization callbacks are a mechanism that provides hooks into the serialization/deserialization process at four points.</span></span>

|<span data-ttu-id="2a6d5-138">Атрибут</span><span class="sxs-lookup"><span data-stu-id="2a6d5-138">Attribute</span></span>|<span data-ttu-id="2a6d5-139">Когда вызывается связанный метод</span><span class="sxs-lookup"><span data-stu-id="2a6d5-139">When the Associated Method is Called</span></span>|<span data-ttu-id="2a6d5-140">Типичные случаи использования</span><span class="sxs-lookup"><span data-stu-id="2a6d5-140">Typical Use</span></span>|
|---------------|------------------------------------------|-----------------|
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="2a6d5-141">Перед десериализацией.\*</span><span class="sxs-lookup"><span data-stu-id="2a6d5-141">Before deserialization.\*</span></span>|<span data-ttu-id="2a6d5-142">Инициализация значений по умолчанию для необязательных полей.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-142">Initialize default values for optional fields.</span></span>|
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="2a6d5-143">После десериализации.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-143">After deserialization.</span></span>|<span data-ttu-id="2a6d5-144">Исправление значений необязательных полей на основании содержимого других полей.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-144">Fix optional field values based on contents of other fields.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="2a6d5-145">Перед сериализацией.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-145">Before serialization.</span></span>|<span data-ttu-id="2a6d5-146">Подготовка к сериализации.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-146">Prepare for serialization.</span></span> <span data-ttu-id="2a6d5-147">Например, создание структур необязательных данных.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-147">For example, create optional data structures.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="2a6d5-148">После сериализации.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-148">After serialization.</span></span>|<span data-ttu-id="2a6d5-149">Регистрация событий сериализации в журнале.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-149">Log serialization events.</span></span>|

 <span data-ttu-id="2a6d5-150">\* Этот обратный вызов осуществляется перед конструктором десериализации, если таковой имеется.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-150">\* This callback is invoked before the deserialization constructor, if one is present.</span></span>

#### <a name="using-callbacks"></a><span data-ttu-id="2a6d5-151">Использование обратных вызовов</span><span class="sxs-lookup"><span data-stu-id="2a6d5-151">Using callbacks</span></span>

<span data-ttu-id="2a6d5-152">Чтобы использовать обратные вызовы, примените соответствующий атрибут к методу, который принимает параметр <xref:System.Runtime.Serialization.StreamingContext>.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-152">To use callbacks, apply the appropriate attribute to a method that accepts a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span> <span data-ttu-id="2a6d5-153">Для каждого из этих атрибутов можно отметить только один метод для класса.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-153">Only one method per class can be marked with each of these attributes.</span></span> <span data-ttu-id="2a6d5-154">Пример:</span><span class="sxs-lookup"><span data-stu-id="2a6d5-154">For example:</span></span>

```csharp
[OnDeserializing]
private void SetCountryRegionDefault(StreamingContext sc)
{
    CountryField = "Japan";
}
```

```vb
<OnDeserializing>
Private Sub SetCountryRegionDefault(sc As StreamingContext)
    CountryField = "Japan"
End Sub
```

<span data-ttu-id="2a6d5-155">Эти методы предназначены для управления версиями.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-155">The intended use of these methods is for versioning.</span></span> <span data-ttu-id="2a6d5-156">Во время десериализации возможна неправильная инициализация необязательного поля, если данные для него отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-156">During deserialization, an optional field may not be correctly initialized if the data for the field is missing.</span></span> <span data-ttu-id="2a6d5-157">Это можно исправить, создав метод, который назначает правильное значение, а затем применяет к методу атрибут **OnDeserializingAttribute** или **OnDeserializedAttribute**.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-157">This can be corrected by creating the method that assigns the correct value, then applying either the **OnDeserializingAttribute** or **OnDeserializedAttribute** attribute to the method.</span></span>

<span data-ttu-id="2a6d5-158">В следующем примере показан метод в контексте типа.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-158">The following example shows the method in the context of a type.</span></span> <span data-ttu-id="2a6d5-159">Если приложение более ранней версии отправляет экземпляр класса `Address` в приложение более поздней версии, данные поля `CountryField` будут отсутствовать.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-159">If an earlier version of an application sends an instance of the `Address` class to a later version of the application, the `CountryField` field data will be missing.</span></span> <span data-ttu-id="2a6d5-160">Но после десериализации полю будет присвоено значение по умолчанию "Japan".</span><span class="sxs-lookup"><span data-stu-id="2a6d5-160">But after deserialization, the field will be set to a default value "Japan".</span></span>

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;
    [OptionalField]
    public string CountryField;

    [OnDeserializing]
    private void SetCountryRegionDefault(StreamingContext sc)
    {
        CountryField = "Japan";
    }
}
```

```vb
<Serializable> _
Public Class Address
    Public Street As String
    Public City As String
    <OptionalField> _
    Public CountryField As String

    <OnDeserializing> _
    Private Sub SetCountryRegionDefault(sc As StreamingContext)
        CountryField = "Japan"
    End Sub
End Class
```

## <a name="the-versionadded-property"></a><span data-ttu-id="2a6d5-161">Свойство VersionAdded</span><span class="sxs-lookup"><span data-stu-id="2a6d5-161">The VersionAdded property</span></span>

<span data-ttu-id="2a6d5-162">**OptionalFieldAttribute** имеет свойство **VersionAdded**.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-162">The **OptionalFieldAttribute** has the **VersionAdded** property.</span></span> <span data-ttu-id="2a6d5-163">Свойство содержит сведения о том, какую версию типа добавило указанное поле.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-163">The property indicates which version of a type a given field has been added.</span></span> <span data-ttu-id="2a6d5-164">Увеличение должно осуществляться точно по одному (начиная с 2) при каждом изменении типа, см. следующий пример:</span><span class="sxs-lookup"><span data-stu-id="2a6d5-164">It should be incremented by exactly one (starting at 2) every time the type is modified, as shown in the following example:</span></span>

```csharp
// Version 1.0
[Serializable]
public class Person
{
    public string FullName;
}

// Version 2.0
[Serializable]
public class Person
{
    public string FullName;

    [OptionalField(VersionAdded = 2)]
    public string NickName;
    [OptionalField(VersionAdded = 2)]
    public DateTime BirthDate;
}

// Version 3.0
[Serializable]
public class Person
{
    public string FullName;

    [OptionalField(VersionAdded=2)]
    public string NickName;
    [OptionalField(VersionAdded=2)]
    public DateTime BirthDate;

    [OptionalField(VersionAdded=3)]
    public int Weight;
}
```

```vb
' Version 1.0
<Serializable> _
Public Class Person
    Public FullName
End Class

' Version 2.0
<Serializable> _
Public Class Person
    Public FullName As String

    <OptionalField(VersionAdded := 2)> _
    Public NickName As String
    <OptionalField(VersionAdded := 2)> _
    Public BirthDate As DateTime
End Class

' Version 3.0
<Serializable> _
Public Class Person
    Public FullName As String

    <OptionalField(VersionAdded := 2)> _
    Public NickName As String
    <OptionalField(VersionAdded := 2)> _
    Public BirthDate As DateTime

    <OptionalField(VersionAdded := 3)> _
    Public Weight As Integer
End Class
```

## <a name="serializationbinder"></a><span data-ttu-id="2a6d5-165">SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="2a6d5-165">SerializationBinder</span></span>

<span data-ttu-id="2a6d5-166">Некоторым пользователям может понадобиться выбирать классы для сериализации и десериализации, поскольку на сервере и клиенте требуются разные версии класса.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-166">Some users may need to control which class to serialize and deserialize because a different version of the class is required on the server and client.</span></span> <span data-ttu-id="2a6d5-167">Класс <xref:System.Runtime.Serialization.SerializationBinder> является абстрактным классом, который используется для управления фактическими типами, применяемыми при сериализации и десериализации.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-167"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="2a6d5-168">Чтобы использовать этот класс, создайте класс, производный от <xref:System.Runtime.Serialization.SerializationBinder>, и переопределите методы <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> и <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-168">To use this class, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> methods.</span></span> <span data-ttu-id="2a6d5-169">Дополнительные сведения см. в разделе [Управление сериализацией и десериализацией с помощью SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span><span class="sxs-lookup"><span data-stu-id="2a6d5-169">For more information, see [Controlling Serialization and Deserialization with SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span></span>

## <a name="best-practices"></a><span data-ttu-id="2a6d5-170">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="2a6d5-170">Best practices</span></span>

<span data-ttu-id="2a6d5-171">Чтобы обеспечить правильное управление версиями, соблюдайте следующие правила при изменении типа от версии к версии:</span><span class="sxs-lookup"><span data-stu-id="2a6d5-171">To ensure proper versioning behavior, follow these rules when modifying a type from version to version:</span></span>

- <span data-ttu-id="2a6d5-172">Никогда не удаляйте сериализованное поле.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-172">Never remove a serialized field.</span></span>
- <span data-ttu-id="2a6d5-173">Никогда не применяйте атрибут <xref:System.NonSerializedAttribute> к полю, если атрибут не был применен к полю в предыдущей версии.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-173">Never apply the <xref:System.NonSerializedAttribute> attribute to a field if the attribute was not applied to the field in the previous version.</span></span>
- <span data-ttu-id="2a6d5-174">Никогда не изменяйте имя или тип сериализованного поля.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-174">Never change the name or the type of a serialized field.</span></span>
- <span data-ttu-id="2a6d5-175">При добавлении нового сериализованного поля применяйте атрибут **OptionalFieldAttribute**.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-175">When adding a new serialized field, apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="2a6d5-176">При удалении атрибута **NonSerializedAttribute** из поля (которое было несериализуемым в предыдущей версии) примените атрибут **OptionalFieldAttribute**.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-176">When removing a **NonSerializedAttribute** attribute from a field (that was not serializable in a previous version), apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="2a6d5-177">Для всех необязательных полей присвойте значимые значения по умолчанию с помощью обратных вызовов сериализации, если 0 или **null** приемлемы в качестве значений по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-177">For all optional fields, set meaningful defaults using the serialization callbacks unless 0 or **null** as defaults are acceptable.</span></span>

<span data-ttu-id="2a6d5-178">Чтобы гарантировать совместимость типа с будущими модулями сериализации, соблюдайте следующие правила:</span><span class="sxs-lookup"><span data-stu-id="2a6d5-178">To ensure that a type will be compatible with future serialization engines, follow these guidelines:</span></span>

- <span data-ttu-id="2a6d5-179">Всегда правильно задавайте свойство **VersionAdded** для атрибута **OptionalFieldAttribute**.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-179">Always set the **VersionAdded** property on the **OptionalFieldAttribute** attribute correctly.</span></span>
- <span data-ttu-id="2a6d5-180">Избегайте ветвления версий.</span><span class="sxs-lookup"><span data-stu-id="2a6d5-180">Avoid branched versioning.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a6d5-181">См. также</span><span class="sxs-lookup"><span data-stu-id="2a6d5-181">See also</span></span>

- <xref:System.SerializableAttribute>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- <xref:System.NonSerializedAttribute>
- [<span data-ttu-id="2a6d5-182">Двоичная сериализация</span><span class="sxs-lookup"><span data-stu-id="2a6d5-182">Binary Serialization</span></span>](binary-serialization.md)
