---
description: 'Подробнее о следующем: Практическое руководство. Отображение доступных последовательных портов в Visual Basic'
title: Практическое руководство. Отображение доступных последовательных портов
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: 7fdbd5577ca40d1a900bc9442cb4bfeedae82c64
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494575"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="a6e6b-103">Практическое руководство. Отображение доступных последовательных портов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a6e6b-103">How to: Show Available Serial Ports in Visual Basic</span></span>

<span data-ttu-id="a6e6b-104">В этом разделе описывается использование объекта `My.Computer.Ports` для отображения доступных последовательных портов компьютера в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a6e6b-104">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="a6e6b-105">Чтобы дать пользователю возможность выбрать используемый порт, имена последовательных портов отображаются в элементе управления <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="a6e6b-105">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6e6b-106">Пример</span><span class="sxs-lookup"><span data-stu-id="a6e6b-106">Example</span></span>  

 <span data-ttu-id="a6e6b-107">В этом примере циклически перебираются все строки, которые возвращает свойство `My.Computer.Ports.SerialPortNames`.</span><span class="sxs-lookup"><span data-stu-id="a6e6b-107">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="a6e6b-108">Эти строки представляют собой имена доступных последовательных портов на компьютере.</span><span class="sxs-lookup"><span data-stu-id="a6e6b-108">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="a6e6b-109">Как правило, пользователь выбирает, какой последовательный порт приложение должно использовать из списка доступных портов.</span><span class="sxs-lookup"><span data-stu-id="a6e6b-109">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="a6e6b-110">В этом примере имена последовательных портов хранятся в элементе управления <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="a6e6b-110">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="a6e6b-111">Дополнительные сведения см. в разделе [Элемент управления ListBox](/dotnet/desktop/winforms/controls/listbox-control-windows-forms).</span><span class="sxs-lookup"><span data-stu-id="a6e6b-111">For more information, see [ListBox Control](/dotnet/desktop/winforms/controls/listbox-control-windows-forms).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="a6e6b-112">Этот пример кода также доступен в качестве фрагмента кода IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="a6e6b-112">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="a6e6b-113">В средстве выбора фрагмента кода он расположен в разделе **Связь и сеть**.</span><span class="sxs-lookup"><span data-stu-id="a6e6b-113">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="a6e6b-114">Дополнительные сведения см. в статье [Фрагменты кода](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="a6e6b-114">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a6e6b-115">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="a6e6b-115">Compiling the Code</span></span>  

 <span data-ttu-id="a6e6b-116">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="a6e6b-116">This example requires:</span></span>  
  
- <span data-ttu-id="a6e6b-117">Ссылка проекта на System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="a6e6b-117">A project reference to System.Windows.Forms.dll.</span></span>  
  
- <span data-ttu-id="a6e6b-118">Доступ к членам пространства имен <xref:System.Windows.Forms>.</span><span class="sxs-lookup"><span data-stu-id="a6e6b-118">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="a6e6b-119">Добавьте оператор `Imports`, если в коде не используются полные имена членов.</span><span class="sxs-lookup"><span data-stu-id="a6e6b-119">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="a6e6b-120">Дополнительные сведения см. в статье [Оператор Imports (пространство имен .NET и тип)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="a6e6b-120">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
- <span data-ttu-id="a6e6b-121">Ваша форма должна включать элемент управления <xref:System.Windows.Forms.ListBox> с именем `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="a6e6b-121">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a6e6b-122">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="a6e6b-122">Robust Programming</span></span>  

 <span data-ttu-id="a6e6b-123">Необязательно использовать элемент управления <xref:System.Windows.Forms.ListBox> для отображения имен доступных последовательных портов.</span><span class="sxs-lookup"><span data-stu-id="a6e6b-123">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="a6e6b-124">Вместо него можно использовать <xref:System.Windows.Forms.ComboBox> или другой элемент управления.</span><span class="sxs-lookup"><span data-stu-id="a6e6b-124">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="a6e6b-125">Если приложение не требует реакции от пользователя, можно использовать для отображения информации элемент управления <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="a6e6b-125">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a6e6b-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a6e6b-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="a6e6b-127">Практическое руководство. Дозвон при помощи модема, подключенного к последовательному порту компьютера</span><span class="sxs-lookup"><span data-stu-id="a6e6b-127">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="a6e6b-128">Практическое руководство. Отправка строк в последовательные порты</span><span class="sxs-lookup"><span data-stu-id="a6e6b-128">How to: Send Strings to Serial Ports</span></span>](how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="a6e6b-129">Практическое руководство. Получение строк из последовательных портов</span><span class="sxs-lookup"><span data-stu-id="a6e6b-129">How to: Receive Strings From Serial Ports</span></span>](how-to-receive-strings-from-serial-ports.md)
