---
description: 'Узнайте подробнее о: Воспроизведение звуков (Visual Basic)'
title: Воспроизведение звуков
ms.date: 07/20/2015
helpviewer_keywords:
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
ms.openlocfilehash: 247af8274108ca8374cf87e53aa2aaad8e5e736c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641516"
---
# <a name="playing-sounds-visual-basic"></a><span data-ttu-id="a7717-103">Воспроизведение звуков (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7717-103">Playing Sounds (Visual Basic)</span></span>

<span data-ttu-id="a7717-104">Объект `My.Computer.Audio` предоставляет методы для воспроизведения звуков.</span><span class="sxs-lookup"><span data-stu-id="a7717-104">The `My.Computer.Audio` object provides methods for playing sounds.</span></span>  
  
## <a name="playing-sounds"></a><span data-ttu-id="a7717-105">Воспроизведение звуков</span><span class="sxs-lookup"><span data-stu-id="a7717-105">Playing Sounds</span></span>  

 <span data-ttu-id="a7717-106">Воспроизведение в фоновом режиме позволяет приложению выполнять другой код во время воспроизведения звуков.</span><span class="sxs-lookup"><span data-stu-id="a7717-106">Background playing lets the application execute other code while the sound plays.</span></span> <span data-ttu-id="a7717-107">Метод `My.Computer.Audio.Play` позволяет приложению воспроизводить только один фоновый звук за раз; когда приложение воспроизводит новый фоновый звук, оно останавливает воспроизведение предыдущего фонового звука.</span><span class="sxs-lookup"><span data-stu-id="a7717-107">The `My.Computer.Audio.Play` method allows the application to play only one background sound at a time; when the application plays a new background sound, it stops playing the previous background sound.</span></span> <span data-ttu-id="a7717-108">Вы также можете воспроизвести звук и дождаться его окончания.</span><span class="sxs-lookup"><span data-stu-id="a7717-108">You can also play a sound and wait for it to complete.</span></span>  
  
 <span data-ttu-id="a7717-109">В следующем примере метод `My.Computer.Audio.Play` воспроизводит звук.</span><span class="sxs-lookup"><span data-stu-id="a7717-109">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="a7717-110">Если `AudioPlayMode.WaitToComplete` указан, `My.Computer.Audio.Play` дожидается завершения звука, прежде чем выполнение вызывающего кода будет продолжено.</span><span class="sxs-lookup"><span data-stu-id="a7717-110">When `AudioPlayMode.WaitToComplete` is specified, `My.Computer.Audio.Play` waits until the sound completes before calling code continues.</span></span> <span data-ttu-id="a7717-111">Пользуясь этим примером, убедитесь в том, что имя файла ссылается на звуковой WAV-файл на вашем компьютере.</span><span class="sxs-lookup"><span data-stu-id="a7717-111">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer</span></span>  
  
 [!code-vb[VbVbalrMyComputer#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#15)]  
  
 <span data-ttu-id="a7717-112">В следующем примере метод `My.Computer.Audio.Play` воспроизводит звук.</span><span class="sxs-lookup"><span data-stu-id="a7717-112">In the following example, the `My.Computer.Audio.Play` method plays a sound.</span></span> <span data-ttu-id="a7717-113">Пользуясь этим примером, убедитесь в том, что ресурсы приложения включают звуковой WAV-файла с именем Waterfall.</span><span class="sxs-lookup"><span data-stu-id="a7717-113">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#16)]  
  
## <a name="playing-looping-sounds"></a><span data-ttu-id="a7717-114">Циклическое воспроизведение звука</span><span class="sxs-lookup"><span data-stu-id="a7717-114">Playing Looping Sounds</span></span>  

 <span data-ttu-id="a7717-115">В следующем примере метод `My.Computer.Audio.Play` воспроизводит заданный звук в фоновом режиме, если задан параметр `PlayMode.BackgroundLoop`.</span><span class="sxs-lookup"><span data-stu-id="a7717-115">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="a7717-116">Пользуясь этим примером, убедитесь в том, что имя файла ссылается на звуковой WAV-файл на вашем компьютере.</span><span class="sxs-lookup"><span data-stu-id="a7717-116">When using this example, you should ensure that the file name refers to a .wav sound file that is on your computer.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#11)]  
  
 <span data-ttu-id="a7717-117">В следующем примере метод `My.Computer.Audio.Play` воспроизводит заданный звук в фоновом режиме, если задан параметр `PlayMode.BackgroundLoop`.</span><span class="sxs-lookup"><span data-stu-id="a7717-117">In the following example, the `My.Computer.Audio.Play` method plays the specified sound in the background when `PlayMode.BackgroundLoop` is specified.</span></span> <span data-ttu-id="a7717-118">Пользуясь этим примером, убедитесь в том, что ресурсы приложения включают звуковой WAV-файла с именем Waterfall.</span><span class="sxs-lookup"><span data-stu-id="a7717-118">When using this example, you should ensure that the application resources include a .wav sound file that is named Waterfall.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#12)]  
  
 <span data-ttu-id="a7717-119">Код в приведенном выше примере также доступен как фрагмент кода IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="a7717-119">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="a7717-120">В средстве выбора фрагмента кода он расположен в разделе **Приложения Windows Forms > Звук**.</span><span class="sxs-lookup"><span data-stu-id="a7717-120">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="a7717-121">Дополнительные сведения см. в статье [Фрагменты кода](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="a7717-121">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
 <span data-ttu-id="a7717-122">Обычно циклическое воспроизведение звука в приложении в конечном итоге должно прекратиться.</span><span class="sxs-lookup"><span data-stu-id="a7717-122">In general, when an application plays a looping sound, it should eventually stop the sound.</span></span>  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a><span data-ttu-id="a7717-123">Остановка воспроизведения звуков в фоновом режиме</span><span class="sxs-lookup"><span data-stu-id="a7717-123">Stopping the Playing of Sounds in the Background</span></span>  

 <span data-ttu-id="a7717-124">Метод `My.Computer.Audio.Stop` позволяет остановить звук, который воспроизводится в приложении в фоновом режиме или циклически.</span><span class="sxs-lookup"><span data-stu-id="a7717-124">Use the `My.Computer.Audio.Stop` method to stop the application's currently playing background or looping sound.</span></span>  
  
 <span data-ttu-id="a7717-125">Обычно циклическое воспроизведение звука в приложении в какой-то момент должно быть остановлено.</span><span class="sxs-lookup"><span data-stu-id="a7717-125">In general, when an application plays a looping sound, it should stop the sound at some point.</span></span>  
  
 <span data-ttu-id="a7717-126">Код в следующем примере останавливает звук, который воспроизводится в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="a7717-126">The following example stops a sound that is playing in the background.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#18)]  
  
 <span data-ttu-id="a7717-127">Код в приведенном выше примере также доступен как фрагмент кода IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="a7717-127">The preceding code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="a7717-128">В средстве выбора фрагмента кода он расположен в разделе **Приложения Windows Forms > Звук**.</span><span class="sxs-lookup"><span data-stu-id="a7717-128">In the code snippet picker, it is located in **Windows Forms Applications > Sound**.</span></span> <span data-ttu-id="a7717-129">Дополнительные сведения см. в статье [Фрагменты кода](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="a7717-129">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="playing-system-sounds"></a><span data-ttu-id="a7717-130">Воспроизведение системных звуков</span><span class="sxs-lookup"><span data-stu-id="a7717-130">Playing System Sounds</span></span>  

 <span data-ttu-id="a7717-131">Метод `My.Computer.Audio.PlaySystemSound` позволяет воспроизвести указанный системный звук.</span><span class="sxs-lookup"><span data-stu-id="a7717-131">Use the `My.Computer.Audio.PlaySystemSound` method to play the specified system sound.</span></span>  
  
 <span data-ttu-id="a7717-132">Метод `My.Computer.Audio.PlaySystemSound` принимает в качестве параметра один из общих членов класса <xref:System.Media.SystemSound>.</span><span class="sxs-lookup"><span data-stu-id="a7717-132">The `My.Computer.Audio.PlaySystemSound` method takes as a parameter one of the shared members from the <xref:System.Media.SystemSound> class.</span></span> <span data-ttu-id="a7717-133">Системный звук <xref:System.Media.SystemSounds.Asterisk%2A> обычно обозначает ошибку.</span><span class="sxs-lookup"><span data-stu-id="a7717-133">The system sound <xref:System.Media.SystemSounds.Asterisk%2A> generally denotes errors.</span></span>  
  
 <span data-ttu-id="a7717-134">Код в следующем примере использует метод `My.Computer.Audio.PlaySystemSound` для воспроизведения системного звука.</span><span class="sxs-lookup"><span data-stu-id="a7717-134">The following example uses the `My.Computer.Audio.PlaySystemSound` method to play a system sound.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="a7717-135">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a7717-135">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Audio>
- <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>
- <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>
- <xref:Microsoft.VisualBasic.AudioPlayMode>
