---
description: 'Дополнительные сведения о: BC30830: операторы "Line" больше не поддерживаются'
title: Операторы Line больше не поддерживаются (ошибка компилятора Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 16696856cee365171000e7b0abc206c42d3f3174
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795876"
---
# <a name="bc30830-line-statements-are-no-longer-supported"></a><span data-ttu-id="12372-103">BC30830: операторы "Line" больше не поддерживаются</span><span class="sxs-lookup"><span data-stu-id="12372-103">BC30830: 'Line' statements are no longer supported</span></span>

<span data-ttu-id="12372-104">Операторы Line больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="12372-104">Line statements are no longer supported.</span></span> <span data-ttu-id="12372-105">Функциональные возможности файлового ввода-вывода доступны как `Microsoft.VisualBasic.FileSystem.LineInput` и графические функции доступны в виде `System.Drawing.Graphics.DrawLine` .</span><span class="sxs-lookup"><span data-stu-id="12372-105">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>

 <span data-ttu-id="12372-106">**Идентификатор ошибки:** BC30830</span><span class="sxs-lookup"><span data-stu-id="12372-106">**Error ID:** BC30830</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="12372-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="12372-107">To correct this error</span></span>

- <span data-ttu-id="12372-108">При выполнении доступа к файлу используйте `Microsoft.VisualBasic.FileSystem.LineInput` .</span><span class="sxs-lookup"><span data-stu-id="12372-108">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>

- <span data-ttu-id="12372-109">Если выполняется вывод графики, используйте `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="12372-109">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>

## <a name="see-also"></a><span data-ttu-id="12372-110">См. также</span><span class="sxs-lookup"><span data-stu-id="12372-110">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="12372-111">Доступ к файлам с помощью Visual Basic</span><span class="sxs-lookup"><span data-stu-id="12372-111">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
