---
title: Практическое руководство. Использование компонентов, поддерживающих асинхронную модель, основанную на событиях
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET], asynchronous features
- components [.NET], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
ms.openlocfilehash: 36fe8015187833e03c4cc3fc1609ec647daf7278
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678003"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="48ac5-102">Практическое руководство. Использование компонентов, поддерживающих асинхронную модель, основанную на событиях</span><span class="sxs-lookup"><span data-stu-id="48ac5-102">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="48ac5-103">Многие компоненты предоставляют возможность выполнять работу асинхронно.</span><span class="sxs-lookup"><span data-stu-id="48ac5-103">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="48ac5-104">Например, компоненты <xref:System.Media.SoundPlayer> и <xref:System.Windows.Forms.PictureBox> позволяют загружать звуки и изображения в фоновом режиме, не прерывая работу основного потока.</span><span class="sxs-lookup"><span data-stu-id="48ac5-104">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="48ac5-105">Чтобы применить асинхронные методы для класса, поддерживающего [асинхронную модель на основе событий](event-based-asynchronous-pattern-overview.md), зачастую достаточно присоединить обработчик события к событию _имя_метода_**Completed** нужного компонента, как для любого другого события.</span><span class="sxs-lookup"><span data-stu-id="48ac5-105">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's _MethodName_**Completed** event, just as you would for any other event.</span></span> <span data-ttu-id="48ac5-106">При вызове метода _имя_метода_**Async** приложение будет работать без прерывания, пока не будет создано событие _имя_метода_**Completed**.</span><span class="sxs-lookup"><span data-stu-id="48ac5-106">When you call the _MethodName_**Async** method, your application will continue running without interruption until the _MethodName_**Completed** event is raised.</span></span> <span data-ttu-id="48ac5-107">В обработчике событий вы можете проверить параметр <xref:System.ComponentModel.AsyncCompletedEventArgs>, чтобы определить, была ли асинхронная операция выполнена успешно или отменена.</span><span class="sxs-lookup"><span data-stu-id="48ac5-107">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="48ac5-108">Дополнительные сведения об обработчиках событий см. в статье [Обзор обработчиков событий (Windows Forms)](/dotnet/desktop/winforms/event-handlers-overview-windows-forms).</span><span class="sxs-lookup"><span data-stu-id="48ac5-108">For more information about using event handlers, see [Event Handlers Overview](/dotnet/desktop/winforms/event-handlers-overview-windows-forms).</span></span>  
  
 <span data-ttu-id="48ac5-109">Следующая процедура демонстрирует, как использовать возможность асинхронной загрузки изображений в элементе управления <xref:System.Windows.Forms.PictureBox>.</span><span class="sxs-lookup"><span data-stu-id="48ac5-109">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="48ac5-110">Асинхронная загрузка изображений для элемента управления PictureBox</span><span class="sxs-lookup"><span data-stu-id="48ac5-110">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1. <span data-ttu-id="48ac5-111">Создайте в форме экземпляр компонента <xref:System.Windows.Forms.PictureBox>.</span><span class="sxs-lookup"><span data-stu-id="48ac5-111">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2. <span data-ttu-id="48ac5-112">Назначьте обработчик событий для события <xref:System.Windows.Forms.PictureBox.LoadCompleted>.</span><span class="sxs-lookup"><span data-stu-id="48ac5-112">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="48ac5-113">Проверьте в нем наличие ошибок, которые могли произойти во время асинхронной загрузки.</span><span class="sxs-lookup"><span data-stu-id="48ac5-113">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="48ac5-114">Также здесь нужно проверить, не запрошена ли отмена.</span><span class="sxs-lookup"><span data-stu-id="48ac5-114">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#5)]  
  
3. <span data-ttu-id="48ac5-115">Добавьте в форму две кнопки с именами `loadButton` и `cancelLoadButton`.</span><span class="sxs-lookup"><span data-stu-id="48ac5-115">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="48ac5-116">Добавьте обработчики событий <xref:System.Windows.Forms.Control.Click> для запуска и отмены загрузки.</span><span class="sxs-lookup"><span data-stu-id="48ac5-116">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#4)]  
  
4. <span data-ttu-id="48ac5-117">Запустите приложение.</span><span class="sxs-lookup"><span data-stu-id="48ac5-117">Run your application.</span></span>  
  
     <span data-ttu-id="48ac5-118">В процессе загрузки изображения вы сможете свободно перемещаться по форме, сворачивать ее и разворачивать.</span><span class="sxs-lookup"><span data-stu-id="48ac5-118">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48ac5-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="48ac5-119">See also</span></span>

- [<span data-ttu-id="48ac5-120">Практическое руководство. Фоновое выполнение операции</span><span class="sxs-lookup"><span data-stu-id="48ac5-120">How to: Run an Operation in the Background</span></span>](/dotnet/desktop/winforms/controls/how-to-run-an-operation-in-the-background)
- [<span data-ttu-id="48ac5-121">Обзор асинхронной модели, основанной на событиях</span><span class="sxs-lookup"><span data-stu-id="48ac5-121">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
