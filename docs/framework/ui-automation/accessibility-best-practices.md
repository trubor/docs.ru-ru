---
title: Рекомендации по специальным возможностям
description: Ознакомьтесь с рекомендациями по специальным возможностям в .NET. Изучите программный доступ, параметры пользователя, визуальный дизайн пользовательского интерфейса, навигацию и интерфейсы мультимодальный.
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: e2a540678b9f802a3b06a5f3091a7bde33d99739
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/02/2021
ms.locfileid: "99427013"
---
# <a name="accessibility-best-practices"></a><span data-ttu-id="3afef-104">Рекомендации по специальным возможностям</span><span class="sxs-lookup"><span data-stu-id="3afef-104">Accessibility best practices</span></span>

> [!NOTE]
> <span data-ttu-id="3afef-105">Эта статья предназначена для платформа .NET Framework разработчиков, желающих использовать управляемые классы автоматизации пользовательского интерфейса, определенные в <xref:System.Windows.Automation> пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="3afef-105">This article is intended for .NET Framework developers who want to use the managed UI Automation classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="3afef-106">Последние сведения об автоматизации пользовательского интерфейса см. в разделе [API автоматизации Windows: Модель автоматизации пользовательского интерфейса](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="3afef-106">For the latest information about UI Automation, see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>

<span data-ttu-id="3afef-107">Реализация следующих рекомендаций в элементах управления или приложениях повысит их доступность для пользователей, использующих вспомогательные технологические устройства.</span><span class="sxs-lookup"><span data-stu-id="3afef-107">Implementing the following best practices in controls or applications will improve their accessibility for people who use assistive technology devices.</span></span> <span data-ttu-id="3afef-108">Многие из этих рекомендаций сосредоточены на хорошем проектировании пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="3afef-108">Many of these best practices focus on good user interface (UI) design.</span></span> <span data-ttu-id="3afef-109">Каждая рекомендация включает сведения о реализации для элементов управления Windows Presentation Foundation (WPF) или приложений.</span><span class="sxs-lookup"><span data-stu-id="3afef-109">Each best practice includes implementation information for Windows Presentation Foundation (WPF) controls or applications.</span></span> <span data-ttu-id="3afef-110">Во многих случаях работа по обеспечению соответствия рекомендациям уже включена в элементы управления WPF.</span><span class="sxs-lookup"><span data-stu-id="3afef-110">In many cases, the work to meet these best practices is already included in WPF controls.</span></span>

<a name="Programmatic_Access"></a>

## <a name="programmatic-access"></a><span data-ttu-id="3afef-111">Программный доступ</span><span class="sxs-lookup"><span data-stu-id="3afef-111">Programmatic Access</span></span>

<span data-ttu-id="3afef-112">Программный доступ предполагает, что все элементы пользовательского интерфейса помечены, значения свойств предоставляются, а соответствующие события вызываются.</span><span class="sxs-lookup"><span data-stu-id="3afef-112">Programmatic access involves ensuring that all UI elements are labeled, property values are exposed, and appropriate events are raised.</span></span> <span data-ttu-id="3afef-113">Для стандартных элементов управления WPF большая часть этой работы уже выполнена с помощью <xref:System.Windows.Automation.Peers.AutomationPeer> .</span><span class="sxs-lookup"><span data-stu-id="3afef-113">For standard WPF controls, most of this work is already done through <xref:System.Windows.Automation.Peers.AutomationPeer>.</span></span> <span data-ttu-id="3afef-114">Пользовательские элементы управления требуют дополнительной работы, чтобы обеспечить правильную реализацию программного доступа.</span><span class="sxs-lookup"><span data-stu-id="3afef-114">Custom controls require additional work to ensure that programmatic access is correctly implemented.</span></span>

<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>

### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a><span data-ttu-id="3afef-115">Включение программного доступа ко всем элементам и тексту пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="3afef-115">Enable Programmatic Access to all UI Elements and Text</span></span>

<span data-ttu-id="3afef-116">Элементы ПОЛЬЗОВАТЕЛЬСКОГО интерфейса должны включать программный доступ.</span><span class="sxs-lookup"><span data-stu-id="3afef-116">User interface (UI) elements should enable programmatic access.</span></span> <span data-ttu-id="3afef-117">Если пользовательский интерфейс является стандартным элементом управления WPF, поддержка программного доступа включается в элемент управления.</span><span class="sxs-lookup"><span data-stu-id="3afef-117">If the UI is a standard WPF control, support for programmatic access is included in the control.</span></span> <span data-ttu-id="3afef-118">Если это пользовательский элемент управления, т. е. элемент управления, являющийся подклассом стандартного элемента управления или элемента управления Control, то вы должны проверить в реализации <xref:System.Windows.Automation.Peers.AutomationPeer> области, которые, возможно, необходимо изменить.</span><span class="sxs-lookup"><span data-stu-id="3afef-118">If the control is a custom control – a control that has been subclassed from a common control or a control that has been subclassed from Control – then you must check the <xref:System.Windows.Automation.Peers.AutomationPeer> implementation for areas that may need modification.</span></span>

<span data-ttu-id="3afef-119">Эта рекомендация позволяет поставщикам вспомогательных технологий обнаруживать элементы пользовательского интерфейса вашего продукта и управлять ими.</span><span class="sxs-lookup"><span data-stu-id="3afef-119">Following this best practice allows assistive technology vendors to identify and manipulate elements of your product's UI.</span></span>

<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>

### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a><span data-ttu-id="3afef-120">Поместите имена, заголовки и описания в объекты пользовательского интерфейса, фреймы и страницы</span><span class="sxs-lookup"><span data-stu-id="3afef-120">Place Names, Titles, and Descriptions on UI Objects, Frames, and Pages</span></span>

<span data-ttu-id="3afef-121">Вспомогательные технологии, особенно средства чтения с экрана, используют заголовок, чтобы определить расположение фрейма, объекта или страницы в схеме навигации.</span><span class="sxs-lookup"><span data-stu-id="3afef-121">Assistive technologies, especially screen readers, use the title to understand the location of the frame, object, or page in the navigation scheme.</span></span> <span data-ttu-id="3afef-122">Поэтому заголовок должен быть описательным.</span><span class="sxs-lookup"><span data-stu-id="3afef-122">Therefore, the title must be descriptive.</span></span> <span data-ttu-id="3afef-123">Например, заголовок веб-страницы «Веб-страница Майкрософт» бесполезен, если пользователь углубился в некую конкретную область.</span><span class="sxs-lookup"><span data-stu-id="3afef-123">For example, a Web page title of "Microsoft Web Page" is useless if the user has navigated deeply into some particular area.</span></span> <span data-ttu-id="3afef-124">Описательное название важно для пользователей с нарушением зрения, которые зависят от средств чтения с экрана.</span><span class="sxs-lookup"><span data-stu-id="3afef-124">A descriptive title is critical for users who are blind and depend on screen readers.</span></span> <span data-ttu-id="3afef-125">Аналогично, для элементов управления WPF <xref:System.Windows.Automation.AutomationProperties.NameProperty> и <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> важны для вспомогательных устройств.</span><span class="sxs-lookup"><span data-stu-id="3afef-125">Similarly, for WPF controls, <xref:System.Windows.Automation.AutomationProperties.NameProperty> and <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> are important for assistive technology devices.</span></span>

<span data-ttu-id="3afef-126">Следуя этой рекомендации, вы можете использовать специальные технологии для обнаружения и управления пользовательским интерфейсом в примерах элементов управления и приложений.</span><span class="sxs-lookup"><span data-stu-id="3afef-126">Following this best practice allows assistive technologies to identify and manipulate UI in sample controls and applications.</span></span>

<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>

### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a><span data-ttu-id="3afef-127">Обеспечение инициации программных событий всеми действиями в пользовательском интерфейсе</span><span class="sxs-lookup"><span data-stu-id="3afef-127">Ensure Programmatic Events Are Triggered by All UI Activities</span></span>

<span data-ttu-id="3afef-128">Благодаря этой рекомендации вспомогательные технологии могут прослушивать изменения в пользовательском интерфейсе и уведомлять пользователя об этих изменениях.</span><span class="sxs-lookup"><span data-stu-id="3afef-128">Following this best practice allows assistive technologies to listen for changes in the UI and notify the user about these changes.</span></span>

<a name="User_Settings"></a>

## <a name="user-settings"></a><span data-ttu-id="3afef-129">Параметры пользователя</span><span class="sxs-lookup"><span data-stu-id="3afef-129">User Settings</span></span>

<span data-ttu-id="3afef-130">Рекомендации в этом разделе предназначены для того, чтобы элементы управления или приложения не переопределяли параметры пользователя.</span><span class="sxs-lookup"><span data-stu-id="3afef-130">The best practice in this section ensures that controls or applications do not override user settings.</span></span>

<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>

### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a><span data-ttu-id="3afef-131">Поддержка всех системных параметров и отсутствие помех со стороны функций специальных возможностей</span><span class="sxs-lookup"><span data-stu-id="3afef-131">Respect All System-Wide Settings and Do Not Interfere with Accessibility Functions</span></span>

<span data-ttu-id="3afef-132">Пользователи могут использовать панель управления для установки некоторых системных флагов; другие флаги можно установить программными средствами.</span><span class="sxs-lookup"><span data-stu-id="3afef-132">Users can use the Control Panel to set some system-wide flags; other flags can be set programmatically.</span></span> <span data-ttu-id="3afef-133">Эти параметры не должны изменяться элементами управления или приложениями.</span><span class="sxs-lookup"><span data-stu-id="3afef-133">These settings should not be changed by controls or applications.</span></span> <span data-ttu-id="3afef-134">Кроме того, приложения должны поддерживать параметры специальных возможностей базовой операционной системы.</span><span class="sxs-lookup"><span data-stu-id="3afef-134">Also, applications must support the accessibility settings of their host operating system.</span></span>

<span data-ttu-id="3afef-135">Следование этой рекомендации дает пользователям возможность устанавливать параметры специальных возможностей и знать, что эти параметры не будут изменены приложениями.</span><span class="sxs-lookup"><span data-stu-id="3afef-135">Following this best practice allows users to set accessibility settings and know that those settings will not be changed by applications.</span></span>

<a name="Visual_UI_Design"></a>

## <a name="visual-ui-design"></a><span data-ttu-id="3afef-136">Визуальная структура пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="3afef-136">Visual UI Design</span></span>

<span data-ttu-id="3afef-137">Рекомендации в этом разделе гарантируют, что элементы управления и приложения используют цвета и изображения эффективно и могут использоваться специальными технологиями.</span><span class="sxs-lookup"><span data-stu-id="3afef-137">Best Practices in this section ensure that controls or applications use color and images effectively and are able to be used by Assistive technologies.</span></span>

<a name="Don_t_Hard_Code_Colors"></a>

### <a name="dont-hard-code-colors"></a><span data-ttu-id="3afef-138">Не используйте жестко закодированные цвета</span><span class="sxs-lookup"><span data-stu-id="3afef-138">Don't Hard-Code Colors</span></span>

<span data-ttu-id="3afef-139">Люди, плохо различающие цвета, имеющие ослабленное зрение или использующие черно-белый экран, не смогут использовать приложения с жестко закодированными цветами.</span><span class="sxs-lookup"><span data-stu-id="3afef-139">People who are color blind, have low vision, or are using a black and white screen might not be able to use applications with hard-coded colors.</span></span>

<span data-ttu-id="3afef-140">Следование этой рекомендации обеспечивает пользователям возможность настройки цветов в зависимости от конкретных требований.</span><span class="sxs-lookup"><span data-stu-id="3afef-140">Following this best practice allows users to adjust color combinations based on individual needs.</span></span>

<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>

### <a name="support-high-contrast-and-all-system-display-attributes"></a><span data-ttu-id="3afef-141">Поддержка высокой контрастности и всех атрибутов отображения системы</span><span class="sxs-lookup"><span data-stu-id="3afef-141">Support High Contrast and all System Display Attributes</span></span>

<span data-ttu-id="3afef-142">Приложения не должны нарушать или отключать выбранные пользователем системные параметры контрастности, цвета и другие системные параметры и атрибуты отображения.</span><span class="sxs-lookup"><span data-stu-id="3afef-142">Applications should not disrupt or disable user-selected, system-wide contrast settings, color selections, or other system-wide display settings and attributes.</span></span> <span data-ttu-id="3afef-143">Системные параметры, установленные пользователем, повышают доступность приложений, поэтому приложения не должны отключать или игнорировать их.</span><span class="sxs-lookup"><span data-stu-id="3afef-143">System-wide settings adopted by a user enhance the accessibility of applications, so they should not be disabled or disregarded by applications.</span></span> <span data-ttu-id="3afef-144">Необходимо использовать правильную комбинацию цветов переднего плана и фона, чтобы обеспечить нужную контрастность.</span><span class="sxs-lookup"><span data-stu-id="3afef-144">Color should be used in their correct foreground-on-background combination to provide proper contrast.</span></span> <span data-ttu-id="3afef-145">Не смешивать несвязанные цвета и не используйте обратные цвета.</span><span class="sxs-lookup"><span data-stu-id="3afef-145">Don't mix unrelated colors, and don't reverse colors.</span></span>

<span data-ttu-id="3afef-146">Многим пользователям требуются определенные комбинации высокой контрастности, такие как белый текст на черном фоне.</span><span class="sxs-lookup"><span data-stu-id="3afef-146">Many users require specific high-contrast combinations, such as white text on a black background.</span></span> <span data-ttu-id="3afef-147">Отображение в обратном порядке, т. е. черный текст на белом фоне, приводит к растеканию фона по переднему плану и может затруднить чтение для некоторых пользователей.</span><span class="sxs-lookup"><span data-stu-id="3afef-147">Drawing these reversed, as black text on a white background causes the background to bleed over the foreground and can make reading difficult for some users.</span></span>

<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>

### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a><span data-ttu-id="3afef-148">Обеспечение правильного масштабирования всего пользовательского интерфейса при любом значении DPI</span><span class="sxs-lookup"><span data-stu-id="3afef-148">Ensure All UI Correctly Scales by Any DPI Setting</span></span>

<span data-ttu-id="3afef-149">Убедитесь, что весь пользовательский интерфейс может правильно масштабироваться в соответствии с параметром "количество точек на дюйм" (DPI).</span><span class="sxs-lookup"><span data-stu-id="3afef-149">Ensure that all UI can correctly scale by any dots per inch (dpi) setting.</span></span> <span data-ttu-id="3afef-150">Кроме того, убедитесь, что элементы пользовательского интерфейса помещаются на экране 1024 x 768 с 120 точек на дюйм (DPI).</span><span class="sxs-lookup"><span data-stu-id="3afef-150">Also, ensure that UI elements fit in a screen of 1024 x 768 with 120 dots per inch (dpi).</span></span>

<a name="Navigation"></a>

## <a name="navigation"></a><span data-ttu-id="3afef-151">Навигация</span><span class="sxs-lookup"><span data-stu-id="3afef-151">Navigation</span></span>

<span data-ttu-id="3afef-152">Рекомендации в этом разделе предназначены для того, чтобы обеспечить разрешение навигации для элементов управления и приложений.</span><span class="sxs-lookup"><span data-stu-id="3afef-152">Best Practices in this section ensure that navigation has been addressed for controls and applications.</span></span>

<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>

### <a name="provide-keyboard-interface-for-all-ui-elements"></a><span data-ttu-id="3afef-153">Предоставление интерфейса клавиатуры для всех элементов пользовательского интерфейса</span><span class="sxs-lookup"><span data-stu-id="3afef-153">Provide Keyboard Interface for All UI Elements</span></span>

<span data-ttu-id="3afef-154">Позиции табуляции, особенно при тщательном планировании, предоставляют пользователям другой способ навигации по пользовательскому интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="3afef-154">Tab stops, especially when carefully planned, give users another way to navigate the UI.</span></span>

<span data-ttu-id="3afef-155">Приложения должны предоставить следующие интерфейсы клавиатуры:</span><span class="sxs-lookup"><span data-stu-id="3afef-155">Applications should provide the following keyboard interfaces:</span></span>

- <span data-ttu-id="3afef-156">позиции табуляции для всех элементов управления, с которыми может взаимодействовать пользователь, таких как кнопки, ссылки или списки;</span><span class="sxs-lookup"><span data-stu-id="3afef-156">tab stops for all controls that the user can interact with, such as buttons, links, or list boxes</span></span>
- <span data-ttu-id="3afef-157">логическую последовательность перехода.</span><span class="sxs-lookup"><span data-stu-id="3afef-157">logical tab order</span></span>

<a name="Show_the_Keyboard_Focus"></a>

### <a name="show-the-keyboard-focus"></a><span data-ttu-id="3afef-158">Отображение фокуса клавиатуры</span><span class="sxs-lookup"><span data-stu-id="3afef-158">Show the Keyboard Focus</span></span>

<span data-ttu-id="3afef-159">Пользователи должны знать, в каком объекте находится фокус клавиатуры, чтобы можно было предвидеть результат нажатия клавиш.</span><span class="sxs-lookup"><span data-stu-id="3afef-159">Users need to know which object has the keyboard focus so that they can anticipate the effect of their keystrokes.</span></span> <span data-ttu-id="3afef-160">Чтобы выделить фокус клавиатуры, используйте цвета, шрифты или элементы графики, такие как прямоугольники или увеличение.</span><span class="sxs-lookup"><span data-stu-id="3afef-160">To highlight the keyboard focus, use colors, fonts, or graphics such as rectangles or magnification.</span></span> <span data-ttu-id="3afef-161">Чтобы воспроизвести выделить фокус клавиатуры, измените громкость, тон или тональность.</span><span class="sxs-lookup"><span data-stu-id="3afef-161">To audibly highlight the keyboard focus, change the volume, pitch, or tonal quality.</span></span>

<span data-ttu-id="3afef-162">Чтобы избежать путаницы, приложения должны скрывать все визуальные указатели фокуса и затенять выбранные элементы, расположенные в неактивных окнах (или областях).</span><span class="sxs-lookup"><span data-stu-id="3afef-162">To avoid confusion, applications should hide all visual focus indicators and dim selections that are located in inactive windows (or panes).</span></span>

<span data-ttu-id="3afef-163">Приложения должны выполнять с фокусом клавиатуры следующее:</span><span class="sxs-lookup"><span data-stu-id="3afef-163">Applications should do the following with keyboard focus:</span></span>

- <span data-ttu-id="3afef-164">один элемент всегда должен иметь фокус клавиатуры;</span><span class="sxs-lookup"><span data-stu-id="3afef-164">one item should always have keyboard focus</span></span>
- <span data-ttu-id="3afef-165">фокус клавиатуры должен быть видимым и очевидным;</span><span class="sxs-lookup"><span data-stu-id="3afef-165">keyboard focus should be visible and obvious</span></span>
- <span data-ttu-id="3afef-166">выбранные объекты или элементы с фокусом должны быть визуально выделены.</span><span class="sxs-lookup"><span data-stu-id="3afef-166">selections and/or focused items should be visually highlighted</span></span>

<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>

### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a><span data-ttu-id="3afef-167">Поддержка стандартов навигации и высокоэффективных навигационных схем</span><span class="sxs-lookup"><span data-stu-id="3afef-167">Support Navigation Standards and Powerful Navigation Schemes</span></span>

<span data-ttu-id="3afef-168">Различные аспекты навигации с помощью клавиатуры предоставляют пользователям различные способы перемещения по пользовательскому интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="3afef-168">Different aspects of keyboard navigation provide different ways for users to navigate the UI.</span></span>

<span data-ttu-id="3afef-169">Приложения должны предоставить следующие интерфейсы клавиатуры:</span><span class="sxs-lookup"><span data-stu-id="3afef-169">Applications should provide the following keyboard interfaces:</span></span>

- <span data-ttu-id="3afef-170">сочетания клавиш и клавиши доступа с подчеркиванием для всех команд, меню и элементов управления</span><span class="sxs-lookup"><span data-stu-id="3afef-170">shortcut keys and underlined access keys for all commands, menus, and controls</span></span>
- <span data-ttu-id="3afef-171">сочетания клавиш для важных ссылок;</span><span class="sxs-lookup"><span data-stu-id="3afef-171">keyboard shortcuts to important links</span></span>
- <span data-ttu-id="3afef-172">клавиши доступа для всех элементов меню, сочетания клавиш для всех кнопок, сочетания клавиш для всех команд.</span><span class="sxs-lookup"><span data-stu-id="3afef-172">all menu items have an access key; all buttons have accelerator keys, all commands have an accelerator key.</span></span>

<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>

### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a><span data-ttu-id="3afef-173">Не допускайте взаимодействие положения указателя мыши с навигацией с помощью клавиатуры</span><span class="sxs-lookup"><span data-stu-id="3afef-173">Do Not Let Mouse Location Interfere with Keyboard Navigation</span></span>

<span data-ttu-id="3afef-174">Положение указателя мыши не должно взаимодействовать с навигацией с помощью клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="3afef-174">Mouse location should not interfere with keyboard navigation.</span></span> <span data-ttu-id="3afef-175">Например, если мышь размещается в каком-то месте и пользователь перемещается по клавиатуре, щелчок мыши не должен происходить, если пользователь не инициировал его.</span><span class="sxs-lookup"><span data-stu-id="3afef-175">For example, if the mouse is positioned some place and the user is navigating with the keyboard, a mouse click should not happen unless initiated by the user.</span></span>

<a name="Multimodal_Interface"></a>

## <a name="multimodal-interface"></a><span data-ttu-id="3afef-176">Мультимодальный интерфейс</span><span class="sxs-lookup"><span data-stu-id="3afef-176">Multimodal Interface</span></span>

<span data-ttu-id="3afef-177">Рекомендации в этом разделе гарантируют, что пользовательский интерфейс приложения включает альтернативные варианты для визуальных элементов.</span><span class="sxs-lookup"><span data-stu-id="3afef-177">Best Practices in this section ensure that application UI includes alternatives for visual elements.</span></span>

<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>

### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a><span data-ttu-id="3afef-178">Предоставление выбираемых пользователем эквивалентов для нетекстовых элементов</span><span class="sxs-lookup"><span data-stu-id="3afef-178">Provide User-Selectable Equivalents for Non-Text Elements</span></span>

<span data-ttu-id="3afef-179">Для каждого нетекстового элемента предоставьте выбираемый пользователем эквивалент для текста, записей разговоров или звуковых описаний, например замещающий текст, подписи или визуальную обратную связь.</span><span class="sxs-lookup"><span data-stu-id="3afef-179">For each non-text element, provide a user-selectable equivalent for text, transcripts, or audio descriptions, such as alt text, captions, or visual feedback.</span></span>

<!-- markdownlint-disable DOCSMD011 -->
<span data-ttu-id="3afef-180">Нетекстовые элементы охватывают широкий спектр элементов пользовательского интерфейса, включая изображения, области карты изображений, анимацию, апплеты, кадры, сценарии, графические кнопки, звуки, автономные аудио-файлы и видео.</span><span class="sxs-lookup"><span data-stu-id="3afef-180">Non-text elements cover a wide range of UI elements including: images, image map regions, animations, applets, frames, scripts, graphical buttons, sounds, stand-alone audio files, and video.</span></span> <span data-ttu-id="3afef-181">Нетекстовые элементы важны, если они содержат визуальные сведения, речь или общие звуковые данные, к которым пользователю требуется доступ, чтобы понять содержимое пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="3afef-181">Non-text elements are important when they contain visual information, speech, or general audio information that the user needs access to in order to understand the content of the UI.</span></span>

<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>

### <a name="use-color-but-also-provide-alternatives-to-color"></a><span data-ttu-id="3afef-182">Используйте цвет, но также предоставьте альтернативы цвета</span><span class="sxs-lookup"><span data-stu-id="3afef-182">Use Color but Also Provide Alternatives to Color</span></span>

<span data-ttu-id="3afef-183">Используйте цвет для улучшения, выделения или повторения сведений, отображаемых другими средствами, но не передавайте сведения только с помощью цвета.</span><span class="sxs-lookup"><span data-stu-id="3afef-183">Use color to enhance, emphasize, or reiterate information shown by other means, but do not communicate information by using color alone.</span></span> <span data-ttu-id="3afef-184">Пользователям, плохо различающим цвета или использующим монохромный дисплей, требуются альтернативы цвету.</span><span class="sxs-lookup"><span data-stu-id="3afef-184">Users who are color blind or have a monochrome display need alternatives to color.</span></span>

<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>

### <a name="use-standard-input-apis-with-device-independent-calls"></a><span data-ttu-id="3afef-185">Используйте стандартные API ввода с аппаратно-независимыми вызовами</span><span class="sxs-lookup"><span data-stu-id="3afef-185">Use Standard Input APIs with Device-Independent Calls</span></span>

<span data-ttu-id="3afef-186">Аппаратно-независимые вызовы гарантируют равенство функций клавиатуры и мыши, а также предоставляют вспомогательные технологии с необходимыми сведениями о пользовательском интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="3afef-186">Device-independent calls ensure keyboard and mouse feature equality, while providing assistive technology with needed information about the UI.</span></span>

## <a name="see-also"></a><span data-ttu-id="3afef-187">См. также статью</span><span class="sxs-lookup"><span data-stu-id="3afef-187">See also</span></span>

- <xref:System.Windows.Automation.Peers>
- <span data-ttu-id="3afef-188">[Пример пользовательского элемента управления NumericUpDown с темой и поддержкой модели автоматизации пользовательского интерфейса](</previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90)>)</span><span class="sxs-lookup"><span data-stu-id="3afef-188">[NumericUpDown Custom Control with Theme and UI Automation Support Sample](</previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90)>)</span></span>
- [<span data-ttu-id="3afef-189">Рекомендации по проектированию пользовательского интерфейса клавиатуры</span><span class="sxs-lookup"><span data-stu-id="3afef-189">Guidelines for Keyboard User Interface Design</span></span>](/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
