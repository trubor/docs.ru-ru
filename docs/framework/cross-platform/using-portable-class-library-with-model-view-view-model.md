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
# <a name="using-portable-class-library-with-model-view-view-model"></a>Использование переносимой библиотеки классов с шаблоном "модель-представление-модель представления"

Можно использовать [переносимую библиотеку классов](portable-class-library.md) .NET Framework для реализации шаблона MVVM (модель — представление — модель представления) и совместного использования сборок на нескольких платформах.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 MVVM — это шаблон приложения, который изолирует интерфейс пользователя от основной бизнес-логики. Можно реализовать классы модели и модели представления в проекте переносимой библиотеки классов с помощью Visual Studio 2012, а затем создавать представления с учетом особенностей разных платформ. Такой подход позволяет один раз определить модель данных и бизнес-логику и использовать этот код в приложениях .NET Framework, Silverlight, Windows Phone и магазина Windows 8.x, как показано на следующей иллюстрации.

 ![Совместное использование сборок MVVM на разных платформах с использованием переносимой библиотеки классов.](./media/using-portable-class-library-with-model-view-view-model/mvvm-share-assemblies-across-platforms.png)

 В этой статье не предоставляются общие сведения о шаблоне MVVM. Здесь содержатся сведения только о реализации MVVM на основе переносимой библиотеки классов. Дополнительные сведения о MVVM см. в [кратком руководстве по MVVM с использованием библиотеки Prism 5.0 для WPF](/previous-versions/msp-n-p/gg430857(v=pandp.40)).

## <a name="classes-that-support-mvvm"></a>Классы, которые поддерживают MVVM

 Если проект переносимой библиотеки классов предназначается для приложений .NET Framework 4.5, .NET для магазина Windows 8.x, Silverlight или Windows Phone 7.5, вам доступны следующие классы для реализации шаблона MVVM:

- Класс <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>

- Класс <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>

- Класс <xref:System.Collections.Specialized.INotifyCollectionChanged?displayProperty=nameWithType>

- Класс <xref:System.Collections.Specialized.NotifyCollectionChangedAction?displayProperty=nameWithType>

- Класс <xref:System.Collections.Specialized.NotifyCollectionChangedEventArgs?displayProperty=nameWithType>

- Класс <xref:System.Collections.Specialized.NotifyCollectionChangedEventHandler?displayProperty=nameWithType>

- Класс <xref:System.ComponentModel.DataErrorsChangedEventArgs?displayProperty=nameWithType>

- Класс <xref:System.ComponentModel.INotifyDataErrorInfo?displayProperty=nameWithType>

- Класс <xref:System.ComponentModel.INotifyPropertyChanged?displayProperty=nameWithType>

- Класс <xref:System.Windows.Input.ICommand?displayProperty=nameWithType>

- Все классы в пространстве имен <xref:System.ComponentModel.DataAnnotations?displayProperty=nameWithType>

## <a name="implementing-mvvm"></a>Реализация MVVM

 Для реализации MVVM модель и модель представления обычно создаются в проекте переносимой библиотеки классов, так как проект переносимой библиотеки классов не может ссылаться на непереносимый проект. Модель и модель представления могут находиться в одном проекте или в отдельных проектах. Если вы используете отдельные проекты, добавьте ссылку из проекта модели представления на проект модели.

 После компиляции проектов модели и модели представления вы включите ссылки на эти сборки в приложение, которое содержит представление. Если представление взаимодействует только с моделью представления, достаточно указать ссылку на сборку, содержащую модель представления.

### <a name="model"></a>Моделирование

 В следующем примере показан упрощенный класс модели, который может размещаться в проекте переносимой библиотеки классов.

 [!code-csharp[PortableClassLibraryMVVM#1](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customer.cs#1)]
 [!code-vb[PortableClassLibraryMVVM#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customer.vb#1)]

 В следующем примере показан простой способ заполнять, извлекать и обновлять данные в проекте переносимой библиотеки классов. В реальных приложениях данные извлекаются из внешнего источника, например из службы Windows Communication Foundation (WCF).

 [!code-csharp[PortableClassLibraryMVVM#2](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/customerrepository.cs#2)]
 [!code-vb[PortableClassLibraryMVVM#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerrepository.vb#2)]

### <a name="view-model"></a>Модель представления

 При реализации шаблона MVVM часто добавляется базовый класс для моделей представления. В следующем примере демонстрируется такой базовый класс.

 [!code-csharp[PortableClassLibraryMVVM#3](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/viewmodelbase.cs#3)]
 [!code-vb[PortableClassLibraryMVVM#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/viewmodelbase.vb#3)]

 С шаблоном MVVM часто используется реализация интерфейса <xref:System.Windows.Input.ICommand>. В следующем примере показана реализация интерфейса <xref:System.Windows.Input.ICommand>.

 [!code-csharp[PortableClassLibraryMVVM#4](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/relaycommand.cs#4)]
 [!code-vb[PortableClassLibraryMVVM#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/relaycommand.vb#4)]

 Ниже представлен упрощенный пример модели представления.

 [!code-csharp[PortableClassLibraryMVVM#5](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainpageviewmodel.cs#5)]
 [!code-vb[PortableClassLibraryMVVM#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/portableclasslibrarymvvm/vb/customerviewmodel.vb#5)]  
  
### <a name="view"></a>Представление  

 В приложениях .NET Framework 4.5, магазина Windows 8.x, Silverlight или Windows Phone 7.5 можно указать ссылки на сборку, которая содержит проекты модели и модели представления.  Затем вы создадите представление, которое взаимодействует с этой моделью представления. В следующем примере показано упрощенное приложение Windows Presentation Foundation (WPF), которое извлекает данные из модели представления и обновляет их. Аналогичные представления можно создать в приложениях Silverlight, Windows Phone или магазина Windows 8.x.  
  
 [!code-xaml[PortableClassLibraryMVVM#6](../../../samples/snippets/csharp/VS_Snippets_CLR/portableclasslibrarymvvm/cs/mainwindow.xaml#6)]  
  
## <a name="see-also"></a>См. также раздел

- [Переносимая библиотека классов](portable-class-library.md)
