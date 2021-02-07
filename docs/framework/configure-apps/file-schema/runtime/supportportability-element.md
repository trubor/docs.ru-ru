---
description: 'Дополнительные сведения о: <supportPortability> element'
title: Элемент <supportPortability>
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
ms.openlocfilehash: 5a39f946d5b3841af5f4254cc2f70142aa6c013d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754515"
---
# <a name="supportportability-element"></a><span data-ttu-id="ad88d-103">Элемент \<supportPortability></span><span class="sxs-lookup"><span data-stu-id="ad88d-103">\<supportPortability> Element</span></span>

<span data-ttu-id="ad88d-104">Указывает, что приложение может ссылаться на ту же сборку в двух различных реализациях .NET Framework, отключая поведение по умолчанию, которое рассматривает сборки как эквивалент для переносимости приложения.</span><span class="sxs-lookup"><span data-stu-id="ad88d-104">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supportPortability>**  
  
## <a name="syntax"></a><span data-ttu-id="ad88d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ad88d-105">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad88d-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ad88d-106">Attributes and Elements</span></span>  

<span data-ttu-id="ad88d-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ad88d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad88d-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ad88d-108">Attributes</span></span>  
  
|<span data-ttu-id="ad88d-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ad88d-109">Attribute</span></span>|<span data-ttu-id="ad88d-110">Описание</span><span class="sxs-lookup"><span data-stu-id="ad88d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad88d-111">PKT</span><span class="sxs-lookup"><span data-stu-id="ad88d-111">PKT</span></span>|<span data-ttu-id="ad88d-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="ad88d-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="ad88d-113">Указывает токен открытого ключа для затронутой сборки в виде строки.</span><span class="sxs-lookup"><span data-stu-id="ad88d-113">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="ad88d-114">Включено</span><span class="sxs-lookup"><span data-stu-id="ad88d-114">enabled</span></span>|<span data-ttu-id="ad88d-115">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="ad88d-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ad88d-116">Указывает, должна ли быть включена поддержка переносимости между реализациями указанной платформа .NET Framework сборки.</span><span class="sxs-lookup"><span data-stu-id="ad88d-116">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ad88d-117">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="ad88d-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="ad88d-118">Значение</span><span class="sxs-lookup"><span data-stu-id="ad88d-118">Value</span></span>|<span data-ttu-id="ad88d-119">Описание</span><span class="sxs-lookup"><span data-stu-id="ad88d-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ad88d-120">Да</span><span class="sxs-lookup"><span data-stu-id="ad88d-120">true</span></span>|<span data-ttu-id="ad88d-121">Включить поддержку переносимости между реализациями указанной платформа .NET Framework сборки.</span><span class="sxs-lookup"><span data-stu-id="ad88d-121">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="ad88d-122">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ad88d-122">This is the default.</span></span>|  
|<span data-ttu-id="ad88d-123">false</span><span class="sxs-lookup"><span data-stu-id="ad88d-123">false</span></span>|<span data-ttu-id="ad88d-124">Отключение поддержки переносимости между реализациями указанной платформа .NET Framework сборки.</span><span class="sxs-lookup"><span data-stu-id="ad88d-124">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="ad88d-125">Это позволяет приложению иметь ссылки на несколько реализаций указанной сборки.</span><span class="sxs-lookup"><span data-stu-id="ad88d-125">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad88d-126">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ad88d-126">Child Elements</span></span>  

<span data-ttu-id="ad88d-127">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ad88d-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad88d-128">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ad88d-128">Parent Elements</span></span>  
  
|<span data-ttu-id="ad88d-129">Элемент</span><span class="sxs-lookup"><span data-stu-id="ad88d-129">Element</span></span>|<span data-ttu-id="ad88d-130">Описание</span><span class="sxs-lookup"><span data-stu-id="ad88d-130">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ad88d-131">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad88d-131">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ad88d-132">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="ad88d-132">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="ad88d-133">Содержит сведения о перенаправлении версии сборки и о расположениях сборок.</span><span class="sxs-lookup"><span data-stu-id="ad88d-133">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad88d-134">Remarks</span><span class="sxs-lookup"><span data-stu-id="ad88d-134">Remarks</span></span>  

<span data-ttu-id="ad88d-135">Начиная с платформа .NET Framework 4, поддержка предоставляется автоматически для приложений, которые могут использовать любую из двух реализаций платформа .NET Framework, например либо реализацию платформа .NET Framework, либо платформа .NET Framework для реализации Silverlight.</span><span class="sxs-lookup"><span data-stu-id="ad88d-135">Beginning with the .NET Framework 4, support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="ad88d-136">Две реализации конкретной платформа .NET Framework сборки считаются эквивалентными связывателем сборки.</span><span class="sxs-lookup"><span data-stu-id="ad88d-136">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="ad88d-137">В нескольких сценариях эта функция переносимости приложений вызывает проблемы.</span><span class="sxs-lookup"><span data-stu-id="ad88d-137">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="ad88d-138">В этих сценариях `<supportPortability>` элемент можно использовать для отключения функции.</span><span class="sxs-lookup"><span data-stu-id="ad88d-138">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
<span data-ttu-id="ad88d-139">Одним из таких сценариев является сборка, которая должна ссылаться как на реализацию платформа .NET Framework, так и на платформа .NET Framework для реализации в Silverlight конкретной ссылочной сборки.</span><span class="sxs-lookup"><span data-stu-id="ad88d-139">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="ad88d-140">Например, конструктору XAML, написанному на Windows Presentation Foundation (WPF), может потребоваться ссылка на реализацию WPF настольной системы, для пользовательского интерфейса конструктора и подмножество WPF, включенное в реализацию Silverlight.</span><span class="sxs-lookup"><span data-stu-id="ad88d-140">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="ad88d-141">По умолчанию отдельные ссылки вызывают ошибку компиляции, так как привязка сборки видит две эквивалентные сборки.</span><span class="sxs-lookup"><span data-stu-id="ad88d-141">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="ad88d-142">Этот элемент отключает поведение по умолчанию и обеспечивает успешную компиляцию.</span><span class="sxs-lookup"><span data-stu-id="ad88d-142">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ad88d-143">Чтобы компилятор мог передать информацию в логику привязки сборки среды CLR, необходимо использовать `/appconfig` параметр компилятора, чтобы указать расположение файла app.config, содержащего этот элемент.</span><span class="sxs-lookup"><span data-stu-id="ad88d-143">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad88d-144">Пример</span><span class="sxs-lookup"><span data-stu-id="ad88d-144">Example</span></span>  

<span data-ttu-id="ad88d-145">В следующем примере приложение включает ссылки на реализацию платформа .NET Framework и платформа .NET Framework для реализации Silverlight любой платформа .NET Framework сборки, которая существует в обеих реализациях.</span><span class="sxs-lookup"><span data-stu-id="ad88d-145">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="ad88d-146">`/appconfig`Для указания расположения этого файла app.config необходимо использовать параметр компилятора.</span><span class="sxs-lookup"><span data-stu-id="ad88d-146">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad88d-147">См. также</span><span class="sxs-lookup"><span data-stu-id="ad88d-147">See also</span></span>

- [<span data-ttu-id="ad88d-148">-appconfig (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="ad88d-148">-appconfig (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- <span data-ttu-id="ad88d-149">[Общие сведения об унификации сборок платформы .NET Framework](/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ad88d-149">[.NET Framework Assembly Unification Overview](/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span></span>
