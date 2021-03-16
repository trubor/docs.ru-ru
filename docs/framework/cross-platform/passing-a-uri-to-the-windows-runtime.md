---
description: 'Дополнительные сведения: передача URI в среду выполнения Windows'
title: Передача URI в среду выполнения Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
ms.openlocfilehash: 918f8ea71f4b23aeaf2a1295f2edd043a73a95ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "102402274"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>Передача URI в среду выполнения Windows

Методы среды выполнения Windows принимают только абсолютные URI. Если передать относительный URI методу среды выполнения Windows, вызывается исключение <xref:System.ArgumentException>. Это происходит из-за того, что при использовании среды выполнения Windows в коде .NET Framework класс <xref:Windows.Foundation.Uri?displayProperty=nameWithType> отображается в Intellisense как <xref:System.Uri?displayProperty=nameWithType>. Класс <xref:System.Uri?displayProperty=nameWithType> допускает относительные URI, а класс <xref:Windows.Foundation.Uri?displayProperty=nameWithType> — нет. Это также справедливо для методов, доступных в компонентах среды выполнения Windows. Если компонент предоставляет метод, принимающий URI, сигнатура в коде содержит <xref:System.Uri?displayProperty=nameWithType>. Однако для пользователей вашего компонента сигнатура содержит <xref:Windows.Foundation.Uri?displayProperty=nameWithType>. URI, переданный вашему компоненту, должен быть абсолютным.  
  
В этом разделе показано, как определить абсолютный URI и как создать его при указании ссылки на ресурс в пакете приложения.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Определение и использование абсолютного URI  

Используйте свойство <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType>, чтобы убедиться, что URI является абсолютным, перед его передачей в среду выполнения Windows. Такой подход более эффективен, чем перехват и обработка исключения <xref:System.ArgumentException>.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Использование абсолютного URI для ресурса в пакете приложения  

Чтобы указать URI для ресурса в пакете приложения, можно использовать схему `ms-appx` или `ms-appx-web` для создания абсолютного URI.  
  
В следующем примере показано, как задать свойство <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> для элемента управления <xref:Windows.UI.Xaml.Controls.WebView> и свойство <xref:Windows.UI.Xaml.Controls.Image.Source%2A> для элемента управления <xref:Windows.UI.Xaml.Controls.Image>, указав ресурсы из папки Pages, с использованием как XAML, так и кода.  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
Дополнительные сведения об этих схемах см. в статье [Схемы URI](/windows/uwp/app-resources/uri-schemes) в Центре разработки для Windows.  
  
## <a name="see-also"></a>См. также

- [Поддержка платформы .NET Framework для приложений магазина Windows и среды выполнения Windows](support-for-windows-store-apps-and-windows-runtime.md)
