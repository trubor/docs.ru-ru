---
description: 'Дополнительные сведения о: BC42033: неправильное значение контрольной суммы, нешестнадцатеричные цифры или нечетное число шестнадцатеричных цифр'
title: Неверное значение контрольной суммы, не шестнадцатеричные цифры или нечетное число шестнадцатеричных цифр
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: 051ee0e8ec8b87be4d5feeac8298c0e7a71baea7
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103885"
---
# <a name="bc42033-bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a><span data-ttu-id="8550e-103">BC42033: неправильное значение контрольной суммы, нешестнадцатеричные цифры или нечетное число шестнадцатеричных цифр</span><span class="sxs-lookup"><span data-stu-id="8550e-103">BC42033: Bad checksum value, non hex digits or odd number of hex digits</span></span>

<span data-ttu-id="8550e-104">Значение контрольной суммы содержит недопустимые шестнадцатеричные цифры или содержит нечетное число цифр.</span><span class="sxs-lookup"><span data-stu-id="8550e-104">A checksum value contains invalid hexadecimal digits or has an odd number of digits.</span></span>

 <span data-ttu-id="8550e-105">Когда среда ASP.NET создает исходный файл Visual Basic (с расширением VB), она вычисляет контрольную сумму и помещает ее в скрытый исходный файл под идентификатором `#externalchecksum`.</span><span class="sxs-lookup"><span data-stu-id="8550e-105">When ASP.NET generates a Visual Basic source file (extension .vb), it calculates a checksum and places it in a hidden source file identified by `#externalchecksum`.</span></span> <span data-ttu-id="8550e-106">Это также может сделать и пользователь, создающий файл VB, однако лучше оставить выполнение этого процесса внутренним механизмам.</span><span class="sxs-lookup"><span data-stu-id="8550e-106">It is possible for a user generating a .vb file to do this also, but this process is best left to internal use.</span></span>

 <span data-ttu-id="8550e-107">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="8550e-107">By default, this message is a warning.</span></span> <span data-ttu-id="8550e-108">Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8550e-108">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="8550e-109">**Идентификатор ошибки:** BC42033</span><span class="sxs-lookup"><span data-stu-id="8550e-109">**Error ID:** BC42033</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8550e-110">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="8550e-110">To correct this error</span></span>

1. <span data-ttu-id="8550e-111">Если ASP.NET создает исходный файл Visual Basic, перезапустите сборку проекта.</span><span class="sxs-lookup"><span data-stu-id="8550e-111">If ASP.NET is generating the Visual Basic source file, restart the project build.</span></span>

2. <span data-ttu-id="8550e-112">Если предупреждение продолжает выводиться после перезапуска, переустановите ASP.NET и повторите попытку сборки.</span><span class="sxs-lookup"><span data-stu-id="8550e-112">If this warning persists after restarting, reinstall ASP.NET and try the build again.</span></span>

3. <span data-ttu-id="8550e-113">Если предупреждение не пропадает или вы не используете ASP.NET, соберите сведения об условиях ее возникновения и уведомите службу технической поддержки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="8550e-113">If the warning still persists, or if you are not using ASP.NET, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="8550e-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8550e-114">See also</span></span>

- [<span data-ttu-id="8550e-115">Обзор ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8550e-115">ASP.NET Overview</span></span>](/aspnet/overview)
- [<span data-ttu-id="8550e-116">Параметры обратной связи Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8550e-116">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
