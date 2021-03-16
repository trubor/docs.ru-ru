---
title: Критическое изменение. Максимальная длина текста NotifyIcon.Text увеличена
description: Сведения о критическом изменении в .NET 6, в результате которого увеличена максимальная длина текста для свойства NotifyIcon.Text.
ms.date: 01/19/2021
ms.openlocfilehash: f87b98dd852ce202689ae9360bee9b6cfbf01794
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255780"
---
# <a name="notifyicontext-maximum-text-length-increased"></a><span data-ttu-id="699dd-103">Максимальная длина текста NotifyIcon.Text увеличена</span><span class="sxs-lookup"><span data-stu-id="699dd-103">NotifyIcon.Text maximum text length increased</span></span>

<span data-ttu-id="699dd-104">Максимальная допустимая длина текста для свойства <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> увеличилась с 63 до 127 символов.</span><span class="sxs-lookup"><span data-stu-id="699dd-104">The maximum text length allowed for the <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> property increased from 63 to 127.</span></span>

## <a name="change-description"></a><span data-ttu-id="699dd-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="699dd-105">Change description</span></span>

<span data-ttu-id="699dd-106">В предыдущих версиях .NET максимальная допустимая длина для свойства <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> составляет 63 символа.</span><span class="sxs-lookup"><span data-stu-id="699dd-106">In previous .NET versions, the maximum text length allowed for the <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> property is 63 characters.</span></span> <span data-ttu-id="699dd-107">Начиная с .NET 6, максимальная допустимая длина текста составляет 127 символов.</span><span class="sxs-lookup"><span data-stu-id="699dd-107">Starting in .NET 6, the maximum allowed text length is 127 characters.</span></span> <span data-ttu-id="699dd-108">В любой версии при попытке задать значение, длина которого превышает ограничение, выдается <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="699dd-108">In any version, an <xref:System.ArgumentException> is thrown when you attempt to set a value that's longer than the limit.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="699dd-109">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="699dd-109">Reason for change</span></span>

<span data-ttu-id="699dd-110">Максимальная допустимая длина текста была увеличена в соответствии с [базовым API Windows](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080).</span><span class="sxs-lookup"><span data-stu-id="699dd-110">The maximum allowed text length was increased to be in line with the [underlying Windows API](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080).</span></span> <span data-ttu-id="699dd-111">API Windows был обновлен в Windows 2000, но по соображениям совместимости максимальный размер этого свойства не был обновлен на платформе .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="699dd-111">The Windows API was updated in Windows 2000, but due to compatibility reasons, the size limit for this property wasn't updated in .NET Framework.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="699dd-112">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="699dd-112">Version introduced</span></span>

<span data-ttu-id="699dd-113">.NET 6, предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="699dd-113">.NET 6 Preview 1</span></span>

## <a name="recommended-action"></a><span data-ttu-id="699dd-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="699dd-114">Recommended action</span></span>

<span data-ttu-id="699dd-115">Проверьте код и при необходимости ослабьте любые имеющиеся защитные проверки.</span><span class="sxs-lookup"><span data-stu-id="699dd-115">Review your code and relax any existing guard conditions, if necessary.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="699dd-116">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="699dd-116">Affected APIs</span></span>

<xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.NotifyIcon.Text`

### Category

Windows Forms

-->
