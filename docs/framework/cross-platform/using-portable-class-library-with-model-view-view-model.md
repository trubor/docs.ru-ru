---
description: Узнайте об использовании переносимой библиотеки классов с шаблоном "модель — представление — модель представления"
title: Использование переносимой библиотеки классов с шаблоном "модель-представление-модель представления"
ms.date: 07/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Portable Class Library [.NET Framework], and MVVM
- MVVM, and Portable Class Library
ms.assetid: 41a0b9f8-15a2-431a-bc35-e310b2953b03
ms.openlocfilehash: 4eea099aaa515c2b7d9874fd6c6d5c4132c5e7a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "102402262"
---
# <a name="using-portable-class-library-with-model-view-view-model"></a><span data-ttu-id="3fc51-103">Использование переносимой библиотеки классов с шаблоном "модель-представление-модель представления"</span><span class="sxs-lookup"><span data-stu-id="3fc51-103">Using Portable Class Library with Model-View-View Model</span></span>

<span data-ttu-id="3fc51-104">Можно использовать [переносимую библиотеку классов](portable-class-library.md) .NET Framework для реализации шаблона MVVM (модель — представление — модель представления) и совместного использования сборок на нескольких платформах.</span><span class="sxs-lookup"><span data-stu-id="3fc51-104">You can use the .NET Framework [Portable Class Library](portable-class-library.md) to implement the Model-View-View Model (MVVM) pattern and share assemblies across multiple platforms.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 <span data-ttu-id="3fc51-105">MVVM — это шаблон приложения, который изолирует интерфейс пользователя от основной бизнес-логики.</span><span class="sxs-lookup"><span data-stu-id="3fc51-105">MVVM is an application pattern that isolates the user interface from the underlying business logic.</span></span> <span data-ttu-id="3fc51-106">Можно реализовать классы модели и модели представления в проекте переносимой библиотеки классов с помощью Visual Studio 2012, а затем создавать представления с учетом особенностей разных платформ.</span><span class="sxs-lookup"><span data-stu-id="3fc51-106">You can implement the model and view model classes in a Portable Class Library project in Visual Studio 2012, and then create views that are customized for different platforms.</span></span> <span data-ttu-id="3fc51-107">Такой подход позволяет один раз определить модель данных и бизнес-логику и использовать этот код в приложениях .NET Framework, Silverlight, Windows Phone и магазина Windows 8.x, как показано на следующей иллюстрации.</span><span class="sxs-lookup"><span data-stu-id="3fc51-107">This approach enables you to write the data model and business logic only once, and use that code from .NET Framework, Silverlight, Windows Phone, and Windows 8.x Store apps, as shown in the following illustration.</span></span>

 ![Совместное использование сборок MVVM на разных платформах с использованием переносимой библиотеки классов.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 <span data-ttu-id="3fc51-109">В этой статье не предоставляются общие сведения о шаблоне MVVM.</span><span class="sxs-lookup"><span data-stu-id="3fc51-109">This topic does not provide general information about the MVVM pattern.</span></span> <span data-ttu-id="3fc51-110">Здесь содержатся сведения только о реализации MVVM на основе переносимой библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="3fc51-110">It only provides information about how to use Portable Class Library to implement MVVM.</span></span> <span data-ttu-id="3fc51-111">Дополнительные сведения о MVVM см. в [кратком руководстве по MVVM с использованием библиотеки Prism 5.0 для WPF](/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span><span class="sxs-lookup"><span data-stu-id="3fc51-111">For more information about MVVM, see the [MVVM Quickstart Using the Prism Library 5.0 for WPF](/previous-versions/msp-n-p/gg430857(v=pandp.40)).</span></span>

## <a name="classes-that-support-mvvm"></a><span data-ttu-id="3fc51-112">Классы, которые поддерживают MVVM</span><span class="sxs-lookup"><span data-stu-id="3fc51-112">Classes That Support MVVM</span></span>

 <span data-ttu-id="3fc51-113">Если проект переносимой библиотеки классов предназначается для приложений .NET Framework 4.5, .NET для магазина Windows 8.x, Silverlight или Windows Phone 7.5, вам доступны следующие классы для реализации шаблона MVVM:</span><span class="sxs-lookup"><span data-stu-id="3fc51-113">When you target the .NET Framework 4.5, .NET for Windows 8.x Store apps, Silverlight, or Windows Phone 7.5 for your Portable Class Library project, the following classes are available for implementing the MVVM pattern:</span></span>

- <span data-ttu-id="3fc51-114">Класс <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3fc51-114"><xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="3fc51-115">Класс <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3fc51-115"><xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="3fc51-116">Класс <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3fc51-116"><xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="3fc51-117">Класс <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3fc51-117"><xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="3fc51-118">Класс <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3fc51-118"><xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="3fc51-119">Класс <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3fc51-119"><xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="3fc51-120">Класс <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3fc51-120"><xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="3fc51-121">Класс <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3fc51-121"><xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="3fc51-122">Класс <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3fc51-122"><xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="3fc51-123">Класс <xref:System.Windows.Input.ICommand?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3fc51-123"><xref:System.Windows.Input.ICommand?displayProperty=nameWithType> class</span></span>

- <span data-ttu-id="3fc51-124">Все классы в пространстве имен <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3fc51-124">All classes in the <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType> namespace</span></span>

## <a name="implementing-mvvm"></a><span data-ttu-id="3fc51-125">Реализация MVVM</span><span class="sxs-lookup"><span data-stu-id="3fc51-125">Implementing MVVM</span></span>

 <span data-ttu-id="3fc51-126">Для реализации MVVM модель и модель представления обычно создаются в проекте переносимой библиотеки классов, так как проект переносимой библиотеки классов не может ссылаться на непереносимый проект.</span><span class="sxs-lookup"><span data-stu-id="3fc51-126">To implement MVVM, you typically create both the model and the view model in a Portable Class Library project, because a Portable Class Library project cannot reference a non-portable project.</span></span> <span data-ttu-id="3fc51-127">Модель и модель представления могут находиться в одном проекте или в отдельных проектах.</span><span class="sxs-lookup"><span data-stu-id="3fc51-127">The model and view model can be in the same project or in separate projects.</span></span> <span data-ttu-id="3fc51-128">Если вы используете отдельные проекты, добавьте ссылку из проекта модели представления на проект модели.</span><span class="sxs-lookup"><span data-stu-id="3fc51-128">If you use separate projects, add a reference from the view model project to the model project.</span></span>

 <span data-ttu-id="3fc51-129">После компиляции проектов модели и модели представления вы включите ссылки на эти сборки в приложение, которое содержит представление.</span><span class="sxs-lookup"><span data-stu-id="3fc51-129">After you compile the model and view model projects, you reference those assemblies in the app that contains the view.</span></span> <span data-ttu-id="3fc51-130">Если представление взаимодействует только с моделью представления, достаточно указать ссылку на сборку, содержащую модель представления.</span><span class="sxs-lookup"><span data-stu-id="3fc51-130">If the view interacts only with the view model, you only have to reference the assembly that contains the view model.</span></span>

### <a name="model"></a><span data-ttu-id="3fc51-131">Моделирование</span><span class="sxs-lookup"><span data-stu-id="3fc51-131">Model</span></span>

 <span data-ttu-id="3fc51-132">В следующем примере показан упрощенный класс модели, который может размещаться в проекте переносимой библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="3fc51-132">The following example shows a simplified model class that could reside in a Portable Class Library project.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 <span data-ttu-id="3fc51-133">В следующем примере показан простой способ заполнять, извлекать и обновлять данные в проекте переносимой библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="3fc51-133">The following example shows a simple way to populate, retrieve, and update the data in a Portable Class Library project.</span></span> <span data-ttu-id="3fc51-134">В реальных приложениях данные извлекаются из внешнего источника, например из службы Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3fc51-134">In a real app, you would retrieve the data from a source such as a Windows Communication Foundation (WCF) service.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a><span data-ttu-id="3fc51-135">Модель представления</span><span class="sxs-lookup"><span data-stu-id="3fc51-135">View Model</span></span>

 <span data-ttu-id="3fc51-136">При реализации шаблона MVVM часто добавляется базовый класс для моделей представления.</span><span class="sxs-lookup"><span data-stu-id="3fc51-136">A base class for view models is frequently added when implementing the MVVM pattern.</span></span> <span data-ttu-id="3fc51-137">В следующем примере демонстрируется такой базовый класс.</span><span class="sxs-lookup"><span data-stu-id="3fc51-137">The following example shows a base class.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 <span data-ttu-id="3fc51-138">С шаблоном MVVM часто используется реализация интерфейса <xref:System.Windows.Input.ICommand>.</span><span class="sxs-lookup"><span data-stu-id="3fc51-138">An implementation of the <xref:System.Windows.Input.ICommand> interface is frequently used with the MVVM pattern.</span></span> <span data-ttu-id="3fc51-139">В следующем примере показана реализация интерфейса <xref:System.Windows.Input.ICommand>.</span><span class="sxs-lookup"><span data-stu-id="3fc51-139">The following example shows an implementation of the <xref:System.Windows.Input.ICommand> interface.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 <span data-ttu-id="3fc51-140">Ниже представлен упрощенный пример модели представления.</span><span class="sxs-lookup"><span data-stu-id="3fc51-140">The following example shows a simplified view model.</span></span>

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a><span data-ttu-id="3fc51-141">Представление</span><span class="sxs-lookup"><span data-stu-id="3fc51-141">View</span></span>  

 <span data-ttu-id="3fc51-142">В приложениях .NET Framework 4.5, магазина Windows 8.x, Silverlight или Windows Phone 7.5 можно указать ссылки на сборку, которая содержит проекты модели и модели представления.</span><span class="sxs-lookup"><span data-stu-id="3fc51-142">From a .NET Framework 4.5 app, Windows 8.x Store app, Silverlight-based app, or Windows Phone 7.5 app, you can reference the assembly that contains the model and view model projects.</span></span>  <span data-ttu-id="3fc51-143">Затем вы создадите представление, которое взаимодействует с этой моделью представления.</span><span class="sxs-lookup"><span data-stu-id="3fc51-143">You then create a view that interacts with the view model.</span></span> <span data-ttu-id="3fc51-144">В следующем примере показано упрощенное приложение Windows Presentation Foundation (WPF), которое извлекает данные из модели представления и обновляет их.</span><span class="sxs-lookup"><span data-stu-id="3fc51-144">The following example shows a simplified Windows Presentation Foundation (WPF) app that retrieves and updates data from the view model.</span></span> <span data-ttu-id="3fc51-145">Аналогичные представления можно создать в приложениях Silverlight, Windows Phone или магазина Windows 8.x.</span><span class="sxs-lookup"><span data-stu-id="3fc51-145">You could create similar views in Silverlight, Windows Phone, or Windows 8.x Store apps.</span></span>  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a><span data-ttu-id="3fc51-146">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3fc51-146">See also</span></span>

- [<span data-ttu-id="3fc51-147">Переносимая библиотека классов</span><span class="sxs-lookup"><span data-stu-id="3fc51-147">Portable Class Library</span></span>](portable-class-library.md)
