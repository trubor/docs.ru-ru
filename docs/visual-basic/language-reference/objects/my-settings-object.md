---
description: 'Подробнее о: объект My. Settings'
title: Объект My.Settings
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 92323c5379d0c5a4dbf96cfdbe0becccc2bad7cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640606"
---
# <a name="mysettings-object"></a><span data-ttu-id="619b8-103">Объект My.Settings</span><span class="sxs-lookup"><span data-stu-id="619b8-103">My.Settings Object</span></span>

<span data-ttu-id="619b8-104">Предоставляет свойства и методы для доступа к параметрам приложения.</span><span class="sxs-lookup"><span data-stu-id="619b8-104">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="619b8-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="619b8-105">Remarks</span></span>  

 <span data-ttu-id="619b8-106">`My.Settings`Объект предоставляет доступ к параметрам приложения и позволяет динамически сохранять и извлекать параметры свойств и другие сведения для приложения.</span><span class="sxs-lookup"><span data-stu-id="619b8-106">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="619b8-107">Дополнительные сведения см. в разделе [Управление параметрами приложения (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="619b8-107">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="619b8-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="619b8-108">Properties</span></span>  

 <span data-ttu-id="619b8-109">Свойства объекта `My.Settings` обеспечивают доступ к параметрам приложения.</span><span class="sxs-lookup"><span data-stu-id="619b8-109">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="619b8-110">Чтобы добавить или удалить параметры, используйте **Конструктор параметров**.</span><span class="sxs-lookup"><span data-stu-id="619b8-110">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="619b8-111">Каждый параметр имеет **имя**, **Тип**, **область** и **значение**, и эти параметры определяют, как свойство для доступа к каждому параметру отображается в `My.Settings` объекте.</span><span class="sxs-lookup"><span data-stu-id="619b8-111">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="619b8-112">**Имя** определяет имя свойства.</span><span class="sxs-lookup"><span data-stu-id="619b8-112">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="619b8-113">**Тип** определяет тип свойства.</span><span class="sxs-lookup"><span data-stu-id="619b8-113">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="619b8-114">**Область** указывает, доступно ли свойство только для чтения.</span><span class="sxs-lookup"><span data-stu-id="619b8-114">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="619b8-115">Если значение — **Application**, свойство доступно только для чтения; Если значение — **User**, свойство доступно для чтения и записи.</span><span class="sxs-lookup"><span data-stu-id="619b8-115">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="619b8-116">**Значение** является значением свойства по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="619b8-116">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="619b8-117">Методы</span><span class="sxs-lookup"><span data-stu-id="619b8-117">Methods</span></span>  
  
|<span data-ttu-id="619b8-118">Метод</span><span class="sxs-lookup"><span data-stu-id="619b8-118">Method</span></span>|<span data-ttu-id="619b8-119">Описание</span><span class="sxs-lookup"><span data-stu-id="619b8-119">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="619b8-120">Перезагружает пользовательские параметры из последних сохраненных значений.</span><span class="sxs-lookup"><span data-stu-id="619b8-120">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="619b8-121">Сохраняет текущие параметры пользователя.</span><span class="sxs-lookup"><span data-stu-id="619b8-121">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="619b8-122">`My.Settings`Объект также предоставляет дополнительные свойства и методы, унаследованные от <xref:System.Configuration.ApplicationSettingsBase> класса.</span><span class="sxs-lookup"><span data-stu-id="619b8-122">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="619b8-123">Задания</span><span class="sxs-lookup"><span data-stu-id="619b8-123">Tasks</span></span>  

 <span data-ttu-id="619b8-124">В следующей таблице приведены примеры задач, включающих `My.Settings` объект.</span><span class="sxs-lookup"><span data-stu-id="619b8-124">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="619b8-125">Кому</span><span class="sxs-lookup"><span data-stu-id="619b8-125">To</span></span>|<span data-ttu-id="619b8-126">См.</span><span class="sxs-lookup"><span data-stu-id="619b8-126">See</span></span>|  
|---|---|  
|<span data-ttu-id="619b8-127">Чтение параметра приложения</span><span class="sxs-lookup"><span data-stu-id="619b8-127">Read an application setting</span></span>|[<span data-ttu-id="619b8-128">Практическое руководство. Чтение параметров приложения в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="619b8-128">How to: Read Application Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="619b8-129">Изменение параметров пользователя</span><span class="sxs-lookup"><span data-stu-id="619b8-129">Change a user setting</span></span>|[<span data-ttu-id="619b8-130">Практическое руководство. Изменение пользовательских параметров в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="619b8-130">How to: Change User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="619b8-131">Сохранить параметры пользователя</span><span class="sxs-lookup"><span data-stu-id="619b8-131">Persist user settings</span></span>|[<span data-ttu-id="619b8-132">Практическое руководство. Сохранение пользовательских параметров в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="619b8-132">How to: Persist User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="619b8-133">Создание сетки свойств для параметров пользователя</span><span class="sxs-lookup"><span data-stu-id="619b8-133">Create a property grid for user settings</span></span>|[<span data-ttu-id="619b8-134">Практическое руководство. Создание таблицы свойств для пользовательских параметров в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="619b8-134">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="619b8-135">Пример</span><span class="sxs-lookup"><span data-stu-id="619b8-135">Example</span></span>  

 <span data-ttu-id="619b8-136">В этом пример выводится значение параметра `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="619b8-136">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="619b8-137">Для надлежащего выполнения этого примера приложение должно иметь параметр `Nickname` типа `String`.</span><span class="sxs-lookup"><span data-stu-id="619b8-137">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="619b8-138">См. также</span><span class="sxs-lookup"><span data-stu-id="619b8-138">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="619b8-139">Практическое руководство. Чтение параметров приложения в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="619b8-139">How to: Read Application Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="619b8-140">Практическое руководство. Изменение пользовательских параметров в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="619b8-140">How to: Change User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="619b8-141">Практическое руководство. Сохранение пользовательских параметров в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="619b8-141">How to: Persist User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="619b8-142">Практическое руководство. Создание таблицы свойств для пользовательских параметров в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="619b8-142">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="619b8-143">Управление параметрами приложения (.NET)</span><span class="sxs-lookup"><span data-stu-id="619b8-143">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
