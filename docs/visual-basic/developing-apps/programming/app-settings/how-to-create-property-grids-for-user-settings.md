---
description: 'Подробнее о следующем: Практическое руководство. Создание таблицы свойств для пользовательских параметров в Visual Basic'
title: Практическое руководство. Создание таблицы свойств для пользовательских параметров
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: 19523f712207cac225ccf68e02e338a9e76fe358
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797852"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a><span data-ttu-id="60c35-103">Практическое руководство. Создание таблицы свойств для пользовательских параметров в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60c35-103">How to: Create Property Grids for User Settings in Visual Basic</span></span>

<span data-ttu-id="60c35-104">Вы можете создать таблицу свойств для параметров пользователя, заполнив элемент управления <xref:System.Windows.Forms.PropertyGrid> свойствами параметров пользователей для объекта `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="60c35-104">You can create a property grid for user settings by populating a <xref:System.Windows.Forms.PropertyGrid> control with the user setting properties of the `My.Settings` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60c35-105">Для надлежащего выполнения этого примера для приложения необходимо настроить пользовательские параметры.</span><span class="sxs-lookup"><span data-stu-id="60c35-105">In order for this example to work, your application must have its user settings configured.</span></span> <span data-ttu-id="60c35-106">Дополнительные сведения см. в разделе [Управление параметрами приложения (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="60c35-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="60c35-107">Объект `My.Settings` представляет каждый параметр в виде свойства.</span><span class="sxs-lookup"><span data-stu-id="60c35-107">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="60c35-108">Имя свойства совпадает с именем параметра, а тип свойства совпадает с типом параметра.</span><span class="sxs-lookup"><span data-stu-id="60c35-108">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="60c35-109">**Область** параметра определяет, доступно ли свойство только для чтения. Свойство для параметра с областью **Приложение** доступно только для чтения, а свойство для параметра с областью **Пользователь** доступно для чтения или записи.</span><span class="sxs-lookup"><span data-stu-id="60c35-109">The setting's **Scope** determines if the property is read-only; the property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="60c35-110">Дополнительные сведения см. в разделе [Объект My.Settings](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="60c35-110">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60c35-111">Невозможно изменить или сохранить значения параметров области определения приложения во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="60c35-111">You cannot change or save the values of application-scope settings at run time.</span></span> <span data-ttu-id="60c35-112">Параметры области определения приложения можно изменить только при создании приложения (с помощью **конструктора проектов**) или путем изменения файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="60c35-112">Application-scope settings can be changed only when creating the application (through the **Project Designer**) or by editing the application's configuration file.</span></span> <span data-ttu-id="60c35-113">Дополнительные сведения см. в разделе [Управление параметрами приложения (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="60c35-113">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
 <span data-ttu-id="60c35-114">В этом примере элемент управления <xref:System.Windows.Forms.PropertyGrid> используется для доступа к свойствам параметров пользователей объекта `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="60c35-114">This example uses a <xref:System.Windows.Forms.PropertyGrid> control to access the user-setting properties of the `My.Settings` object.</span></span> <span data-ttu-id="60c35-115">По умолчанию <xref:System.Windows.Forms.PropertyGrid> отображает все свойства объекта `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="60c35-115">By default, the <xref:System.Windows.Forms.PropertyGrid> shows all the properties of the `My.Settings` object.</span></span> <span data-ttu-id="60c35-116">Однако свойства параметров пользователей имеют атрибут <xref:System.Configuration.UserScopedSettingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="60c35-116">However, the user-setting properties have the <xref:System.Configuration.UserScopedSettingAttribute> attribute.</span></span> <span data-ttu-id="60c35-117">В данном примере для свойства <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> объекта <xref:System.Windows.Forms.PropertyGrid> устанавливается значение <xref:System.Configuration.UserScopedSettingAttribute>, чтобы отображать только свойства параметров пользователей.</span><span class="sxs-lookup"><span data-stu-id="60c35-117">This example sets the <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> property of the <xref:System.Windows.Forms.PropertyGrid> to <xref:System.Configuration.UserScopedSettingAttribute> to display only the user-setting properties.</span></span>  
  
### <a name="to-add-a-user-setting-property-grid"></a><span data-ttu-id="60c35-118">Добавление таблицы свойств параметров пользователей</span><span class="sxs-lookup"><span data-stu-id="60c35-118">To add a user setting property grid</span></span>  
  
1. <span data-ttu-id="60c35-119">Добавьте элемент управления **PropertyGrid** из **панели элементов** в область конструктора для вашего приложения (здесь предполагается приложение `Form1`).</span><span class="sxs-lookup"><span data-stu-id="60c35-119">Add the **PropertyGrid** control from the **Toolbox** to the design surface for your application, assumed here to be `Form1`.</span></span>  
  
     <span data-ttu-id="60c35-120">Имя по умолчанию элемента управления таблицы свойств — `PropertyGrid1`.</span><span class="sxs-lookup"><span data-stu-id="60c35-120">The default name of the property-grid control is `PropertyGrid1`.</span></span>  
  
2. <span data-ttu-id="60c35-121">Дважды щелкните область конструктора для `Form1`, чтобы открыть код обработчика событий загрузки формы.</span><span class="sxs-lookup"><span data-stu-id="60c35-121">Double-click the design surface for `Form1` to open the code for the form-load event handler.</span></span>  
  
3. <span data-ttu-id="60c35-122">Задайте объект `My.Settings` в качестве выделенного объекта для таблицы свойств.</span><span class="sxs-lookup"><span data-stu-id="60c35-122">Set the `My.Settings` object as the selected object for the property grid.</span></span>  
  
     [!code-vb[VbVbalrMyResources#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#11)]  
  
4. <span data-ttu-id="60c35-123">Настройте таблицу свойств для отображения только параметров пользователей.</span><span class="sxs-lookup"><span data-stu-id="60c35-123">Configure the property grid to show only the user settings.</span></span>  
  
     [!code-vb[VbVbalrMyResources#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#12)]  
  
    > [!NOTE]
    > <span data-ttu-id="60c35-124">Чтобы отобразить только параметры области определения приложения, используйте атрибут <xref:System.Configuration.ApplicationScopedSettingAttribute> вместо <xref:System.Configuration.UserScopedSettingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="60c35-124">To show only the application-scope settings, use the <xref:System.Configuration.ApplicationScopedSettingAttribute> attribute instead of  <xref:System.Configuration.UserScopedSettingAttribute>.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="60c35-125">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="60c35-125">Robust Programming</span></span>  

 <span data-ttu-id="60c35-126">Приложение сохраняет пользовательские параметры при завершении работы.</span><span class="sxs-lookup"><span data-stu-id="60c35-126">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="60c35-127">Чтобы сохранить параметры немедленно, вызовите метод `My.Settings.Save`.</span><span class="sxs-lookup"><span data-stu-id="60c35-127">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="60c35-128">Дополнительные сведения см. в разделе [Практическое руководство. Сохранение пользовательских параметров в Visual Basic](how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="60c35-128">For more information, see [How to: Persist User Settings in Visual Basic](how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c35-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="60c35-129">See also</span></span>

- [<span data-ttu-id="60c35-130">Объект My.Settings</span><span class="sxs-lookup"><span data-stu-id="60c35-130">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="60c35-131">Практическое руководство. Чтение параметров приложения в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60c35-131">How to: Read Application Settings in Visual Basic</span></span>](how-to-read-application-settings.md)
- [<span data-ttu-id="60c35-132">Практическое руководство. Изменение пользовательских параметров в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60c35-132">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="60c35-133">Практическое руководство. Сохранение пользовательских параметров в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60c35-133">How to: Persist User Settings in Visual Basic</span></span>](how-to-persist-user-settings.md)
- [<span data-ttu-id="60c35-134">Управление параметрами приложения (.NET)</span><span class="sxs-lookup"><span data-stu-id="60c35-134">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
