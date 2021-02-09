---
description: 'Подробнее о следующем: Практическое руководство. Проверка состояния подключения в Visual Basic'
title: Практическое руководство. Проверка состояния подключения
ms.date: 07/20/2015
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
ms.openlocfilehash: c568e3be5d8fedb1ae12c748110b23218deaf069
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797748"
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="08c19-103">Практическое руководство. Проверка состояния подключения в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="08c19-103">How to: Check Connection Status in Visual Basic</span></span>

<span data-ttu-id="08c19-104">Свойство <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> можно использовать, чтобы проверить наличие на компьютере подключения к действующей сети или Интернету.</span><span class="sxs-lookup"><span data-stu-id="08c19-104">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="08c19-105">Проверка наличия на компьютере рабочего подключения</span><span class="sxs-lookup"><span data-stu-id="08c19-105">To check whether a computer has a working connection</span></span>  
  
- <span data-ttu-id="08c19-106">Определите, имеет ли свойство `IsAvailable` значение `True` или `False`.</span><span class="sxs-lookup"><span data-stu-id="08c19-106">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="08c19-107">Следующий код проверяет состояние свойства и сообщает его:</span><span class="sxs-lookup"><span data-stu-id="08c19-107">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#3)]  
  
     <span data-ttu-id="08c19-108">Этот пример кода также доступен в качестве фрагмента кода IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="08c19-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="08c19-109">В средстве выбора фрагмента кода он расположен в разделе **Связь и сеть**.</span><span class="sxs-lookup"><span data-stu-id="08c19-109">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="08c19-110">Дополнительные сведения см. в статье [Фрагменты кода](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="08c19-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c19-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="08c19-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable>
