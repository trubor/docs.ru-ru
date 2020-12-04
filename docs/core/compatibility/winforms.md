---
title: Критические изменения в Windows Forms
description: Список критических изменений в Windows Forms для .NET Core 3.0 и 3.1.
ms.date: 09/08/2020
ms.openlocfilehash: b944f7eea89b61f41feb8eef99e949c2d6017960
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726435"
---
# <a name="breaking-changes-in-windows-forms-for-net-core-30-and-31"></a><span data-ttu-id="56bf2-103">Критические изменения в Windows Forms для .NET Core 3.0 и 3.1</span><span class="sxs-lookup"><span data-stu-id="56bf2-103">Breaking changes in Windows Forms for .NET Core 3.0 and 3.1</span></span>

<span data-ttu-id="56bf2-104">Поддержка Windows Forms была добавлена в .NET Core в версии 3.0.</span><span class="sxs-lookup"><span data-stu-id="56bf2-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="56bf2-105">В этой статье перечислены критические изменения для Windows Forms, сгруппированные по версии .NET, в которой они появились.</span><span class="sxs-lookup"><span data-stu-id="56bf2-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="56bf2-106">Если вы обновляете приложение Windows Forms с .NET Framework или с предыдущей версии .NET Core (3.0 или более поздней), эта статья для вас актуальна.</span><span class="sxs-lookup"><span data-stu-id="56bf2-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="56bf2-107">На этой странице описаны следующие критические изменения:</span><span class="sxs-lookup"><span data-stu-id="56bf2-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="56bf2-108">Критическое изменение</span><span class="sxs-lookup"><span data-stu-id="56bf2-108">Breaking change</span></span> | <span data-ttu-id="56bf2-109">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="56bf2-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="56bf2-110">Удаленные элементы управления</span><span class="sxs-lookup"><span data-stu-id="56bf2-110">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="56bf2-111">3.1</span><span class="sxs-lookup"><span data-stu-id="56bf2-111">3.1</span></span> |
| [<span data-ttu-id="56bf2-112">При отображении подсказки не возникает событие CellFormatting</span><span class="sxs-lookup"><span data-stu-id="56bf2-112">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="56bf2-113">3.1</span><span class="sxs-lookup"><span data-stu-id="56bf2-113">3.1</span></span> |
| [<span data-ttu-id="56bf2-114">Шрифт Control.DefaultFont изменен на Segoe UI 9 пт</span><span class="sxs-lookup"><span data-stu-id="56bf2-114">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="56bf2-115">3.0</span><span class="sxs-lookup"><span data-stu-id="56bf2-115">3.0</span></span> |
| [<span data-ttu-id="56bf2-116">Модернизация FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="56bf2-116">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="56bf2-117">3.0</span><span class="sxs-lookup"><span data-stu-id="56bf2-117">3.0</span></span> |
| [<span data-ttu-id="56bf2-118">Из некоторых типов Windows Forms удален атрибут SerializableAttribute</span><span class="sxs-lookup"><span data-stu-id="56bf2-118">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="56bf2-119">3.0</span><span class="sxs-lookup"><span data-stu-id="56bf2-119">3.0</span></span> |
| [<span data-ttu-id="56bf2-120">Параметр совместимости AllowUpdateChildControlIndexForTabControls не поддерживается</span><span class="sxs-lookup"><span data-stu-id="56bf2-120">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="56bf2-121">3.0</span><span class="sxs-lookup"><span data-stu-id="56bf2-121">3.0</span></span> |
| [<span data-ttu-id="56bf2-122">Параметр совместимости DomainUpDown.UseLegacyScrolling не поддерживается</span><span class="sxs-lookup"><span data-stu-id="56bf2-122">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="56bf2-123">3.0</span><span class="sxs-lookup"><span data-stu-id="56bf2-123">3.0</span></span> |
| [<span data-ttu-id="56bf2-124">Параметр совместимости DoNotLoadLatestRichEditControl не поддерживается</span><span class="sxs-lookup"><span data-stu-id="56bf2-124">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="56bf2-125">3.0</span><span class="sxs-lookup"><span data-stu-id="56bf2-125">3.0</span></span> |
| [<span data-ttu-id="56bf2-126">Параметр совместимости DoNotSupportSelectAllShortcutInMultilineTextBox не поддерживается</span><span class="sxs-lookup"><span data-stu-id="56bf2-126">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="56bf2-127">3.0</span><span class="sxs-lookup"><span data-stu-id="56bf2-127">3.0</span></span> |
| [<span data-ttu-id="56bf2-128">Параметр совместимости DontSupportReentrantFilterMessage не поддерживается</span><span class="sxs-lookup"><span data-stu-id="56bf2-128">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="56bf2-129">3.0</span><span class="sxs-lookup"><span data-stu-id="56bf2-129">3.0</span></span> |
| [<span data-ttu-id="56bf2-130">Параметр совместимости EnableVisualStyleValidation не поддерживается</span><span class="sxs-lookup"><span data-stu-id="56bf2-130">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="56bf2-131">3.0</span><span class="sxs-lookup"><span data-stu-id="56bf2-131">3.0</span></span> |
| [<span data-ttu-id="56bf2-132">Параметр совместимости UseLegacyContextMenuStripSourceControlValue не поддерживается</span><span class="sxs-lookup"><span data-stu-id="56bf2-132">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="56bf2-133">3.0</span><span class="sxs-lookup"><span data-stu-id="56bf2-133">3.0</span></span> |
| [<span data-ttu-id="56bf2-134">Параметр совместимости UseLegacyImages не поддерживается</span><span class="sxs-lookup"><span data-stu-id="56bf2-134">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="56bf2-135">3.0</span><span class="sxs-lookup"><span data-stu-id="56bf2-135">3.0</span></span> |

## <a name="net-core-31"></a><span data-ttu-id="56bf2-136">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="56bf2-136">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

<span data-ttu-id="56bf2-137">\*\*_</span><span class="sxs-lookup"><span data-stu-id="56bf2-137">\*\*_</span></span>

## <a name="net-core-30"></a><span data-ttu-id="56bf2-138">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="56bf2-138">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

_*_

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

_*_

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

<span data-ttu-id="56bf2-139">_\*\*</span><span class="sxs-lookup"><span data-stu-id="56bf2-139">_\*\*</span></span>

## <a name="see-also"></a><span data-ttu-id="56bf2-140">См. также</span><span class="sxs-lookup"><span data-stu-id="56bf2-140">See also</span></span>

- [<span data-ttu-id="56bf2-141">Перенос приложения Windows Forms в .NET Core</span><span class="sxs-lookup"><span data-stu-id="56bf2-141">Port a Windows Forms app to .NET Core</span></span>](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
