---
description: 'Узнайте подробнее о: Практическое руководство. Запуск приложения и отправка ему нажатий клавиш (Visual Basic)'
title: Практическое руководство. Запуск приложения и отправка ему нажатий клавиш (Visual Basic)
ms.date: 10/23/2019
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: ea54b940b528e0833d9c7a6cbef67f65a4cb4f6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666463"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="7cdc0-103">Практическое руководство. Запуск приложения и отправка ему нажатий клавиш (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7cdc0-103">How to: start an application and send it keystrokes (Visual Basic)</span></span>

<span data-ttu-id="7cdc0-104">Этот пример использует метод <xref:Microsoft.VisualBasic.Interaction.Shell%2A> для запуска приложения "Блокнот", а затем распечатывает предложение, отправляя нажатия клавиш с помощью метода [My.Computer.Keyboard.SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A).</span><span class="sxs-lookup"><span data-stu-id="7cdc0-104">This example uses the <xref:Microsoft.VisualBasic.Interaction.Shell%2A> method to start the Notepad application and then prints a sentence by sending keystrokes using the [My.Computer.Keyboard.SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) method.</span></span>

## <a name="example"></a><span data-ttu-id="7cdc0-105">Пример</span><span class="sxs-lookup"><span data-stu-id="7cdc0-105">Example</span></span>

[!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]

## <a name="robust-programming"></a><span data-ttu-id="7cdc0-106">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="7cdc0-106">Robust programming</span></span>

<span data-ttu-id="7cdc0-107">Если приложение с запрошенным идентификатором процесса не найдено, возникает исключение <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="7cdc0-107">An <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7cdc0-108">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7cdc0-108">.NET Framework Security</span></span>

<span data-ttu-id="7cdc0-109">Вызов функции `Shell` требует полного доверия (класс <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="7cdc0-109">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="7cdc0-110">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7cdc0-110">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
