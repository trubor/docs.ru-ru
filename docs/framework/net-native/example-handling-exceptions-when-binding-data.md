---
description: 'Дополнительные сведения: пример: обработка исключений при привязке данных'
title: Пример. Обработка исключений при привязке данных
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
ms.openlocfilehash: 434520e42afa3e1ab7c453c3ddf41863ceb62eb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747898"
---
# <a name="example-handling-exceptions-when-binding-data"></a><span data-ttu-id="6aef4-103">Пример. Обработка исключений при привязке данных</span><span class="sxs-lookup"><span data-stu-id="6aef4-103">Example: Handling Exceptions When Binding Data</span></span>

> [!NOTE]
> <span data-ttu-id="6aef4-104">В этом разделе рассматривается предварительная версия программного обеспечения для разработчиков машинного кода .NET.</span><span class="sxs-lookup"><span data-stu-id="6aef4-104">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="6aef4-105">Предварительную версию можно скачать на [веб-сайте Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (требуется регистрация).</span><span class="sxs-lookup"><span data-stu-id="6aef4-105">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="6aef4-106">В следующем примере показано, как разрешить исключение [MissingMetadataException](missingmetadataexception-class-net-native.md) , возникающее, когда приложение, скомпилированное с помощью цепочки инструментов .NET Native, пытается привязать данные.</span><span class="sxs-lookup"><span data-stu-id="6aef4-106">The following example shows how to resolve a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception that is thrown when an app compiled with the .NET Native tool chain tries to bind data.</span></span> <span data-ttu-id="6aef4-107">Сведения об исключении:</span><span class="sxs-lookup"><span data-stu-id="6aef4-107">Here’s the exception information:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:
App.ViewModels.MainPageVM  
```  
  
 <span data-ttu-id="6aef4-108">Ниже приведен связанный стек вызова:</span><span class="sxs-lookup"><span data-stu-id="6aef4-108">Here's the associated call stack:</span></span>  
  
```output
Reflection::Execution::ReflectionDomainSetupImplementation.CreateNonInvokabilityException+0x238  
Reflection::Core::ReflectionDomain.CreateNonInvokabilityException+0x2e  
Reflection::Core::Execution::ExecutionEnvironment.+0x316  
System::Reflection::Runtime::PropertyInfos::RuntimePropertyInfo.GetValue+0x1cb  
System::Reflection::PropertyInfo.GetValue+0x22  
System::Runtime::InteropServices::WindowsRuntime::CustomPropertyImpl.GetValue+0x42  
App!$66_Interop::McgNative.Func_IInspectable_IInspectable+0x158  
App!$66_Interop::McgNative::__vtable_Windows_UI_Xaml_Data__ICustomProperty.GetValue__STUB+0x46  
Windows_UI_Xaml!DirectUI::PropertyProviderPropertyAccess::GetValue+0x3f
Windows_UI_Xaml!DirectUI::PropertyAccessPathStep::GetValue+0x31
Windows_UI_Xaml!DirectUI::PropertyPathListener::ConnectPathStep+0x113  
```  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="6aef4-109">Что делало приложение?</span><span class="sxs-lookup"><span data-stu-id="6aef4-109">What was the app doing?</span></span>  

 <span data-ttu-id="6aef4-110">В базе стека кадры из <xref:Windows.UI.Xaml?displayProperty=nameWithType> пространства имен указывают, что обработчик визуализации XAML запущен.</span><span class="sxs-lookup"><span data-stu-id="6aef4-110">At the base of the stack, frames from the <xref:Windows.UI.Xaml?displayProperty=nameWithType> namespace indicate that the XAML rendering engine was running.</span></span>   <span data-ttu-id="6aef4-111">Использование метода <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType>указывает на поиск на основе отражения значения свойства типа, метаданные которого были удалены.</span><span class="sxs-lookup"><span data-stu-id="6aef4-111">The use of the <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> method indicates a reflection-based lookup of a property’s value on the type whose metadata was removed.</span></span>  
  
 <span data-ttu-id="6aef4-112">На первом шаге предоставления директивы метаданных следовало бы добавить метаданные `serialize` для типа, чтобы его свойства стали доступны:</span><span class="sxs-lookup"><span data-stu-id="6aef4-112">The first step in providing a metadata directive would be to add `serialize` metadata for the type so that its properties are all accessible:</span></span>  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="6aef4-113">Это изолированный случай?</span><span class="sxs-lookup"><span data-stu-id="6aef4-113">Is this an isolated case?</span></span>  

 <span data-ttu-id="6aef4-114">В этом сценарии, если привязка данных имеет неполные метаданные для одной модели `ViewModel`, это может быть справедливо и для других.</span><span class="sxs-lookup"><span data-stu-id="6aef4-114">In this scenario, if data binding has incomplete metadata for one `ViewModel`, it may for others, too.</span></span>  <span data-ttu-id="6aef4-115">Если код структурирован таким образом, что все модели просмотра приложения находятся в пространстве имен `App.ViewModels`, можно использовать более общую директиву среды выполнения:</span><span class="sxs-lookup"><span data-stu-id="6aef4-115">If the code is structured in a way that the app’s view models are all in the `App.ViewModels` namespace, you could use a more general runtime directive:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a><span data-ttu-id="6aef4-116">Можно переписать код, чтобы не использовать отражение?</span><span class="sxs-lookup"><span data-stu-id="6aef4-116">Could the code be rewritten to not use reflection?</span></span>  

 <span data-ttu-id="6aef4-117">Так как привязки данных интенсивно использует отражение, изменение кода, чтобы избежать отражения невозможно.</span><span class="sxs-lookup"><span data-stu-id="6aef4-117">Because data binding is reflection-intensive, changing the code to avoid reflection isn’t feasible.</span></span>  
  
 <span data-ttu-id="6aef4-118">Однако, существуют способы задания `ViewModel` странице XAML таким образом, чтобы цепочка инструментов могла связать привязки свойства с нужным типом во время компиляции и сохранить метаданные без использования директивы среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="6aef4-118">However, there are ways to specify the `ViewModel` to the XAML page so that the tool chain can associate property bindings with the correct type at compile time and keep the metadata without using a runtime directive.</span></span>  <span data-ttu-id="6aef4-119">Например, атрибут можно применить <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> к свойствам.</span><span class="sxs-lookup"><span data-stu-id="6aef4-119">For example, you could apply the <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> attribute on properties.</span></span> <span data-ttu-id="6aef4-120">Это вынуждает компилятор XAML создать необходимые таблицы подстановок и избежать использования директивы среды выполнения в файле Default.rd.xml.</span><span class="sxs-lookup"><span data-stu-id="6aef4-120">This causes the XAML compiler to generate the required lookup information and avoids requiring a runtime directive in the Default.rd.xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aef4-121">См. также</span><span class="sxs-lookup"><span data-stu-id="6aef4-121">See also</span></span>

- [<span data-ttu-id="6aef4-122">Начало работы</span><span class="sxs-lookup"><span data-stu-id="6aef4-122">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="6aef4-123">Пример. Устранение неполадок динамического программирования</span><span class="sxs-lookup"><span data-stu-id="6aef4-123">Example: Troubleshooting Dynamic Programming</span></span>](example-troubleshooting-dynamic-programming.md)
