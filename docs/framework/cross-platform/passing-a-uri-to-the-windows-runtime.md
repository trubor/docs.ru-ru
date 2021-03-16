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
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="65e70-103">Передача URI в среду выполнения Windows</span><span class="sxs-lookup"><span data-stu-id="65e70-103">Passing a URI to the Windows Runtime</span></span>

<span data-ttu-id="65e70-104">Методы среды выполнения Windows принимают только абсолютные URI.</span><span class="sxs-lookup"><span data-stu-id="65e70-104">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="65e70-105">Если передать относительный URI методу среды выполнения Windows, вызывается исключение <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="65e70-105">If you pass a relative URI to a Windows Runtime method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="65e70-106">Это происходит из-за того, что при использовании среды выполнения Windows в коде .NET Framework класс <xref:Windows.Foundation.Uri?displayProperty=nameWithType> отображается в Intellisense как <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65e70-106">Here's why: When you use the Windows Runtime in .NET Framework code, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="65e70-107">Класс <xref:System.Uri?displayProperty=nameWithType> допускает относительные URI, а класс <xref:Windows.Foundation.Uri?displayProperty=nameWithType> — нет.</span><span class="sxs-lookup"><span data-stu-id="65e70-107">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class does not.</span></span> <span data-ttu-id="65e70-108">Это также справедливо для методов, доступных в компонентах среды выполнения Windows.</span><span class="sxs-lookup"><span data-stu-id="65e70-108">This is also true for methods you expose in Windows Runtime Components.</span></span> <span data-ttu-id="65e70-109">Если компонент предоставляет метод, принимающий URI, сигнатура в коде содержит <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65e70-109">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="65e70-110">Однако для пользователей вашего компонента сигнатура содержит <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65e70-110">However, to users of your component, the signature includes <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="65e70-111">URI, переданный вашему компоненту, должен быть абсолютным.</span><span class="sxs-lookup"><span data-stu-id="65e70-111">A URI that is passed to your component must be an absolute URI.</span></span>  
  
<span data-ttu-id="65e70-112">В этом разделе показано, как определить абсолютный URI и как создать его при указании ссылки на ресурс в пакете приложения.</span><span class="sxs-lookup"><span data-stu-id="65e70-112">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="65e70-113">Определение и использование абсолютного URI</span><span class="sxs-lookup"><span data-stu-id="65e70-113">Detecting and using an absolute URI</span></span>  

<span data-ttu-id="65e70-114">Используйте свойство <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType>, чтобы убедиться, что URI является абсолютным, перед его передачей в среду выполнения Windows.</span><span class="sxs-lookup"><span data-stu-id="65e70-114">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the Windows Runtime.</span></span> <span data-ttu-id="65e70-115">Такой подход более эффективен, чем перехват и обработка исключения <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="65e70-115">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="65e70-116">Использование абсолютного URI для ресурса в пакете приложения</span><span class="sxs-lookup"><span data-stu-id="65e70-116">Using an absolute URI for a resource in the app package</span></span>  

<span data-ttu-id="65e70-117">Чтобы указать URI для ресурса в пакете приложения, можно использовать схему `ms-appx` или `ms-appx-web` для создания абсолютного URI.</span><span class="sxs-lookup"><span data-stu-id="65e70-117">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
<span data-ttu-id="65e70-118">В следующем примере показано, как задать свойство <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> для элемента управления <xref:Windows.UI.Xaml.Controls.WebView> и свойство <xref:Windows.UI.Xaml.Controls.Image.Source%2A> для элемента управления <xref:Windows.UI.Xaml.Controls.Image>, указав ресурсы из папки Pages, с использованием как XAML, так и кода.</span><span class="sxs-lookup"><span data-stu-id="65e70-118">The following example shows how to set the <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> property for a <xref:Windows.UI.Xaml.Controls.WebView> control and the <xref:Windows.UI.Xaml.Controls.Image.Source%2A> property for an <xref:Windows.UI.Xaml.Controls.Image> control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
<span data-ttu-id="65e70-119">Дополнительные сведения об этих схемах см. в статье [Схемы URI](/windows/uwp/app-resources/uri-schemes) в Центре разработки для Windows.</span><span class="sxs-lookup"><span data-stu-id="65e70-119">For more information about these schemes, see [URI schemes](/windows/uwp/app-resources/uri-schemes) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65e70-120">См. также</span><span class="sxs-lookup"><span data-stu-id="65e70-120">See also</span></span>

- [<span data-ttu-id="65e70-121">Поддержка платформы .NET Framework для приложений магазина Windows и среды выполнения Windows</span><span class="sxs-lookup"><span data-stu-id="65e70-121">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](support-for-windows-store-apps-and-windows-runtime.md)
