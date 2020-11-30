---
title: Извлечение информации, сохраненной в атрибуте
description: Узнайте, как извлекать сведения, хранящиеся в атрибутах, например для экземпляра атрибута, нескольких экземпляров в одной области или нескольких экземпляров в разных областях.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
ms.openlocfilehash: 6ba01fcd23e626354e5f9a2baa914815b61c8332
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701566"
---
# <a name="retrieving-information-stored-in-attributes"></a><span data-ttu-id="c945a-103">Извлечение информации, сохраненной в атрибуте</span><span class="sxs-lookup"><span data-stu-id="c945a-103">Retrieving Information Stored in Attributes</span></span>

<span data-ttu-id="c945a-104">Извлечение пользовательских атрибутов не представляет никакой сложности.</span><span class="sxs-lookup"><span data-stu-id="c945a-104">Retrieving a custom attribute is a simple process.</span></span> <span data-ttu-id="c945a-105">Сначала объявите экземпляр атрибута, который вам нужно получить.</span><span class="sxs-lookup"><span data-stu-id="c945a-105">First, declare an instance of the attribute you want to retrieve.</span></span> <span data-ttu-id="c945a-106">Затем вызовите метод <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>, чтобы инициализировать новый атрибут тем значением, которое вы хотите получить.</span><span class="sxs-lookup"><span data-stu-id="c945a-106">Then, use the <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> method to initialize the new attribute to the value of the attribute you want to retrieve.</span></span> <span data-ttu-id="c945a-107">После инициализации нового атрибута обращайтесь к его свойствам, чтобы получить значения.</span><span class="sxs-lookup"><span data-stu-id="c945a-107">Once the new attribute is initialized, you simply use its properties to get the values.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c945a-108">В этой статье объясняется, как можно получить настраиваемые атрибуты для кода, загруженного в контекст выполнения.</span><span class="sxs-lookup"><span data-stu-id="c945a-108">This topic describes how to retrieve attributes for code loaded into the execution context.</span></span> <span data-ttu-id="c945a-109">Чтобы получить атрибуты для кода, загруженного в контекст только для отражения, необходимо использовать класс <xref:System.Reflection.CustomAttributeData>, как показано в статье [Практическое руководство. Загрузка сборок в контекст, предназначенный только для отражения](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="c945a-109">To retrieve attributes for code loaded into the reflection-only context, you must use the <xref:System.Reflection.CustomAttributeData> class, as shown in [How to: Load Assemblies into the Reflection-Only Context](../../framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
 <span data-ttu-id="c945a-110">В этом разделе описываются следующие способы извлечения атрибутов.</span><span class="sxs-lookup"><span data-stu-id="c945a-110">This section describes the following ways to retrieve attributes:</span></span>  
  
- [<span data-ttu-id="c945a-111">Извлечение единственного экземпляра атрибута</span><span class="sxs-lookup"><span data-stu-id="c945a-111">Retrieving a single instance of an attribute</span></span>](#cpconretrievingsingleinstanceofattribute)  
  
- [<span data-ttu-id="c945a-112">Извлечение нескольких экземпляров атрибута, применяемых к одной области</span><span class="sxs-lookup"><span data-stu-id="c945a-112">Retrieving multiple instances of an attribute applied to the same scope</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [<span data-ttu-id="c945a-113">Извлечение нескольких экземпляров атрибута, применяемых к разным областям</span><span class="sxs-lookup"><span data-stu-id="c945a-113">Retrieving multiple instances of an attribute applied to different scopes</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>

## <a name="retrieving-a-single-instance-of-an-attribute"></a><span data-ttu-id="c945a-114">Извлечение единственного экземпляра атрибута</span><span class="sxs-lookup"><span data-stu-id="c945a-114">Retrieving a Single Instance of an Attribute</span></span>  

 <span data-ttu-id="c945a-115">В следующем примере атрибут `DeveloperAttribute` (который описан в предыдущем разделе) применяется к классу `MainApp` на уровне класса.</span><span class="sxs-lookup"><span data-stu-id="c945a-115">In the following example, the `DeveloperAttribute` (described in the previous section) is applied to the `MainApp` class on the class level.</span></span> <span data-ttu-id="c945a-116">Метод `GetAttribute` использует **GetCustomAttribute** для получения значений, хранящихся в `DeveloperAttribute` на уровне класса, а затем выводит их в консоль.</span><span class="sxs-lookup"><span data-stu-id="c945a-116">The `GetAttribute` method uses **GetCustomAttribute** to retrieve the values stored in `DeveloperAttribute` on the class level before displaying them to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 <span data-ttu-id="c945a-117">Эта программа при выполнении выводит следующий текст.</span><span class="sxs-lookup"><span data-stu-id="c945a-117">This program displays the following text when executed.</span></span>  
  
```console  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 <span data-ttu-id="c945a-118">Если атрибут не найден, метод **GetCustomAttribute** инициализирует атрибут `MyAttribute` значением NULL.</span><span class="sxs-lookup"><span data-stu-id="c945a-118">If the attribute is not found, the **GetCustomAttribute** method initializes `MyAttribute` to a null value.</span></span> <span data-ttu-id="c945a-119">Этот пример проверяет наличие такого экземпляра в `MyAttribute` и уведомляет пользователя, если атрибут не найден.</span><span class="sxs-lookup"><span data-stu-id="c945a-119">This example checks `MyAttribute` for such an instance and notifies the user if no attribute is found.</span></span> <span data-ttu-id="c945a-120">Если `DeveloperAttribute` не найден в области класса, на консоль выводится следующее сообщение.</span><span class="sxs-lookup"><span data-stu-id="c945a-120">If the `DeveloperAttribute` is not found in the class scope, the following message displays to the console.</span></span>  
  
```console  
The attribute was not found.
```  
  
 <span data-ttu-id="c945a-121">В этом примере предполагается, что определения атрибута находится в текущем пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="c945a-121">This example assumes that the attribute definition is in the current namespace.</span></span> <span data-ttu-id="c945a-122">Не забудьте импортировать пространство имен, в котором существует определение нужного атрибута, если это не текущее пространство имен.</span><span class="sxs-lookup"><span data-stu-id="c945a-122">Remember to import the namespace in which the attribute definition resides if it is not in the current namespace.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>

## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a><span data-ttu-id="c945a-123">Извлечение нескольких экземпляров атрибута, применяемых к одной области</span><span class="sxs-lookup"><span data-stu-id="c945a-123">Retrieving Multiple Instances of an Attribute Applied to the Same Scope</span></span>  

 <span data-ttu-id="c945a-124">В предыдущем примере класс и искомый атрибут передаются в <xref:System.Attribute.GetCustomAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="c945a-124">In the previous example, the class to inspect and the specific attribute to find are passed to <xref:System.Attribute.GetCustomAttribute%2A>.</span></span> <span data-ttu-id="c945a-125">Такой код будет работать правильно только в том случае, если на уровне класса применяется только один экземпляр нужного атрибута.</span><span class="sxs-lookup"><span data-stu-id="c945a-125">That code works well if only one instance of an attribute is applied on the class level.</span></span> <span data-ttu-id="c945a-126">Если же на одном уровне класса применяются несколько экземпляров атрибута, метод **GetCustomAttribute** не сможет извлечь все данные.</span><span class="sxs-lookup"><span data-stu-id="c945a-126">However, if multiple instances of an attribute are applied on the same class level, the **GetCustomAttribute** method does not retrieve all the information.</span></span> <span data-ttu-id="c945a-127">Если несколько экземпляров одного атрибута применяются к одной области, вы можете поместить все экземпляры этого атрибута в массив с помощью <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c945a-127">In cases where multiple instances of the same attribute are applied to the same scope, you can use <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> to place all instances of an attribute into an array.</span></span> <span data-ttu-id="c945a-128">Например, если на уровне класса применяются два вхождения `DeveloperAttribute`, метод `GetAttribute` можно изменить так, чтобы отобразить сведения из обоих атрибутов.</span><span class="sxs-lookup"><span data-stu-id="c945a-128">For example, if two instances of `DeveloperAttribute` are applied on the class level of the same class, the `GetAttribute` method can be modified to display the information found in both attributes.</span></span> <span data-ttu-id="c945a-129">Как вы помните, несколько атрибутов можно применить на одном уровне только в том случае, если в определении атрибута в <xref:System.AttributeUsageAttribute> свойство **AllowMultiple** имеет значение **true**.</span><span class="sxs-lookup"><span data-stu-id="c945a-129">Remember, to apply multiple attributes on the same level, the attribute must be defined with the **AllowMultiple** property set to **true** in the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="c945a-130">В следующем примере кода показано, как использовать метод **GetCustomAttributes** для создания массива, который ссылается на все экземпляры `DeveloperAttribute` в любом заданном классе.</span><span class="sxs-lookup"><span data-stu-id="c945a-130">The following code example shows how to use the **GetCustomAttributes** method to create an array that references all instances of `DeveloperAttribute` in any given class.</span></span> <span data-ttu-id="c945a-131">Создав массив, метод выводит в консоль значения всех атрибутов.</span><span class="sxs-lookup"><span data-stu-id="c945a-131">The values of all attributes are then displayed to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 <span data-ttu-id="c945a-132">Если атрибуты не найдены, код уведомляет об этом пользователя.</span><span class="sxs-lookup"><span data-stu-id="c945a-132">If no attributes are found, this code alerts the user.</span></span> <span data-ttu-id="c945a-133">В противном случае он выводит все сведения, содержащиеся в обоих экземплярах `DeveloperAttribute`.</span><span class="sxs-lookup"><span data-stu-id="c945a-133">Otherwise, the information contained in both instances of `DeveloperAttribute` is displayed.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>

## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a><span data-ttu-id="c945a-134">Извлечение нескольких экземпляров атрибута, применяемых к разным областям</span><span class="sxs-lookup"><span data-stu-id="c945a-134">Retrieving Multiple Instances of an Attribute Applied to Different Scopes</span></span>  

 <span data-ttu-id="c945a-135">Методы <xref:System.Attribute.GetCustomAttributes%2A> и <xref:System.Attribute.GetCustomAttribute%2A> не выполняют поиск по всему классу, чтобы вернуть все экземпляры атрибута в этом классе.</span><span class="sxs-lookup"><span data-stu-id="c945a-135">The <xref:System.Attribute.GetCustomAttributes%2A> and <xref:System.Attribute.GetCustomAttribute%2A> methods do not search an entire class and return all instances of an attribute in that class.</span></span> <span data-ttu-id="c945a-136">Вместо этого они проверяют только один заданный метод или член за один вызов.</span><span class="sxs-lookup"><span data-stu-id="c945a-136">Rather, they search only one specified method or member at a time.</span></span> <span data-ttu-id="c945a-137">Если у вас есть класс, в котором к каждому члену применен один и тот же атрибут, и вы хотите извлечь значения всех атрибутов, примененных к этим членам, к каждому методу и члену нужно обращаться по отдельности с помощью методов **GetCustomAttributes** и  **GetCustomAttribute**.</span><span class="sxs-lookup"><span data-stu-id="c945a-137">If you have a class with the same attribute applied to every member and you want to retrieve the values in all the attributes applied to those members, you must supply every method or member individually to **GetCustomAttributes** and **GetCustomAttribute**.</span></span>  
  
 <span data-ttu-id="c945a-138">Следующий пример кода принимает класс в качестве параметра и выполняет в нем поиск атрибута `DeveloperAttribute` (определенного ранее) на уровне класса и в каждом отдельном методе этого класса.</span><span class="sxs-lookup"><span data-stu-id="c945a-138">The following code example takes a class as a parameter and searches for the `DeveloperAttribute` (defined previously) on the class level and on every individual method of that class.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 <span data-ttu-id="c945a-139">Если на уровне методов и на уровне класса не обнаружен ни один экземпляр `DeveloperAttribute`, метод `GetAttribute` извещает пользователя о том, что атрибуты не найдены, а затем отображает имя метода и класса, в котором он искал атрибут.</span><span class="sxs-lookup"><span data-stu-id="c945a-139">If no instances of the `DeveloperAttribute` are found on the method level or class level, the `GetAttribute` method notifies the user that no attributes were found and displays the name of the method or class that does not contain the attribute.</span></span> <span data-ttu-id="c945a-140">Если атрибут успешно найден, метод выводит в консоль поля `Name`, `Level` и `Reviewed`.</span><span class="sxs-lookup"><span data-stu-id="c945a-140">If an attribute is found, the `Name`, `Level`, and `Reviewed` fields are displayed to the console.</span></span>  
  
 <span data-ttu-id="c945a-141">Вы можете использовать члены класса <xref:System.Type>, чтобы получить отдельные методы и члены переданного класса.</span><span class="sxs-lookup"><span data-stu-id="c945a-141">You can use the members of the <xref:System.Type> class to get the individual methods and members in the passed class.</span></span> <span data-ttu-id="c945a-142">Этот пример первым делом опрашивает объект **Type**, чтобы получить данные об атрибуте на уровне класса.</span><span class="sxs-lookup"><span data-stu-id="c945a-142">This example first queries the **Type** object to get attribute information for the class level.</span></span> <span data-ttu-id="c945a-143">После этого он выполняет <xref:System.Type.GetMethods%2A?displayProperty=nameWithType>, чтобы поместить экземпляры всех методов в массив объектов <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> и получить данные об атрибуте на уровне методов.</span><span class="sxs-lookup"><span data-stu-id="c945a-143">Next, it uses <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> to place instances of all methods into an array of <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objects to retrieve attribute information for the method level.</span></span> <span data-ttu-id="c945a-144">Вы также можете использовать метод <xref:System.Type.GetProperties%2A?displayProperty=nameWithType>, чтобы найти атрибуты на уровне свойств, или метод <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType>, чтобы найти атрибуты на уровне конструктора.</span><span class="sxs-lookup"><span data-stu-id="c945a-144">You can also use the <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> method to check for attributes on the property level or <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> to check for attributes on the constructor level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c945a-145">См. также</span><span class="sxs-lookup"><span data-stu-id="c945a-145">See also</span></span>

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c945a-146">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="c945a-146">Attributes</span></span>](index.md)
