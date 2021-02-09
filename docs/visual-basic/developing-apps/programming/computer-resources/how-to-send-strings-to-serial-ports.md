---
description: 'Подробнее о следующем: Практическое руководство. Отправка строк в последовательный порт в Visual Basic'
title: Практическое руководство. Отправка строк в последовательные порты
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: 66dedaab05090af2659701e57b37b4813447b8ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666489"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="84a85-103">Практическое руководство. Отправка строк в последовательный порт в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84a85-103">How to: Send Strings to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="84a85-104">В этом разделе описывается, как использовать `My.Computer.Ports` для отправки строк в последовательные порты компьютера в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="84a85-104">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84a85-105">Пример</span><span class="sxs-lookup"><span data-stu-id="84a85-105">Example</span></span>  

 <span data-ttu-id="84a85-106">Этот пример кода отправляет строку в последовательный порт COM1.</span><span class="sxs-lookup"><span data-stu-id="84a85-106">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="84a85-107">Возможно, на вашем компьютере потребуется использовать другой последовательный порт.</span><span class="sxs-lookup"><span data-stu-id="84a85-107">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="84a85-108">Воспользуйтесь методом `My.Computer.Ports.OpenSerialPort`, чтобы получить ссылку на порт.</span><span class="sxs-lookup"><span data-stu-id="84a85-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="84a85-109">Для получения дополнительной информации см. <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="84a85-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="84a85-110">Блок `Using` позволяет приложению закрыть последовательный порт даже в том случае, если он создает исключение.</span><span class="sxs-lookup"><span data-stu-id="84a85-110">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="84a85-111">В блоке `Try...Catch...Finally` должен отображаться весь код, управляющий последовательным портом.</span><span class="sxs-lookup"><span data-stu-id="84a85-111">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="84a85-112">Метод <xref:System.IO.Ports.SerialPort.WriteLine%2A> отправляет данные в последовательный порт.</span><span class="sxs-lookup"><span data-stu-id="84a85-112">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="84a85-113">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="84a85-113">Compiling the Code</span></span>  
  
- <span data-ttu-id="84a85-114">В этом примере предполагается, что компьютер использует `COM1`.</span><span class="sxs-lookup"><span data-stu-id="84a85-114">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="84a85-115">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="84a85-115">Robust Programming</span></span>  

 <span data-ttu-id="84a85-116">В этом примере предполагается, что компьютер использует `COM1`. Для большей гибкости код должен позволять пользователю выбирать нужный последовательный порт из списка доступных портов.</span><span class="sxs-lookup"><span data-stu-id="84a85-116">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="84a85-117">Дополнительные сведения см. в разделе [Практическое руководство. Отображение доступных последовательных портов](how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="84a85-117">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="84a85-118">В этом примере блок `Using` позволяет сделать так, чтобы приложение закрыло порт, даже если он создает исключение.</span><span class="sxs-lookup"><span data-stu-id="84a85-118">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="84a85-119">Дополнительные сведения см. в разделе [Оператор using](../../../language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="84a85-119">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84a85-120">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="84a85-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="84a85-121">Практическое руководство. Дозвон при помощи модема, подключенного к последовательному порту компьютера</span><span class="sxs-lookup"><span data-stu-id="84a85-121">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="84a85-122">Практическое руководство. Отображение доступных последовательных портов</span><span class="sxs-lookup"><span data-stu-id="84a85-122">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
