---
description: 'Подробнее о следующем: Практическое руководство. Изменение пользовательских параметров в Visual Basic'
title: Практическое руководство. Изменение пользовательских параметров
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 3877c9fadbf1b5b79470dc9ad41fbaf8123e6770
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797865"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a><span data-ttu-id="c6af7-103">Практическое руководство. Изменение пользовательских параметров в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6af7-103">How to: Change User Settings in Visual Basic</span></span>

<span data-ttu-id="c6af7-104">Пользовательские параметры можно изменять, присваивая новое значение свойству объекта параметров `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="c6af7-104">You can change a user setting by assigning a new value to the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="c6af7-105">Объект `My.Settings` представляет каждый параметр в виде свойства.</span><span class="sxs-lookup"><span data-stu-id="c6af7-105">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="c6af7-106">Имя свойства совпадает с именем параметра, а тип свойства совпадает с типом параметра.</span><span class="sxs-lookup"><span data-stu-id="c6af7-106">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="c6af7-107">**Область** параметра определяет, доступно ли свойство только для чтения. Свойство для параметра с областью **Приложение** доступно только для чтения, а свойство для параметра с областью **Пользователь** доступно для чтения или записи.</span><span class="sxs-lookup"><span data-stu-id="c6af7-107">The setting's **Scope** determines if the property is read-only: The property for an **Application**-scope setting is read-only, while the property for a **User**-scope setting is read-write.</span></span> <span data-ttu-id="c6af7-108">Дополнительные сведения см. в разделе [Объект My.Settings](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="c6af7-108">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6af7-109">Значения параметров с областью пользователя можно изменять и сохранять во время выполнения, однако параметры с областью приложения доступны только для чтения и не могут быть изменены программным способом.</span><span class="sxs-lookup"><span data-stu-id="c6af7-109">Although you can change and save the values of user-scope settings at run time, application-scope settings are read-only and cannot be changed programmatically.</span></span> <span data-ttu-id="c6af7-110">Вы можете изменить параметры области приложения при создании приложения с помощью **конструктора проектов** или путем изменения файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="c6af7-110">You can change application-scope settings when you create the application by using the **Project Designer** or by editing the application's configuration file.</span></span> <span data-ttu-id="c6af7-111">Дополнительные сведения см. в разделе [Управление параметрами приложения (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c6af7-111">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6af7-112">Пример</span><span class="sxs-lookup"><span data-stu-id="c6af7-112">Example</span></span>  

 <span data-ttu-id="c6af7-113">В этом примере изменяется значение пользовательского параметра `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="c6af7-113">This example changes the value of the `Nickname` user setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 <span data-ttu-id="c6af7-114">Для надлежащего выполнения этого примера приложение должно иметь пользовательский параметр `Nickname` типа `String`.</span><span class="sxs-lookup"><span data-stu-id="c6af7-114">For this example to work, your application must have a `Nickname` user setting, of type `String`.</span></span>  
  
 <span data-ttu-id="c6af7-115">Приложение сохраняет пользовательские параметры при завершении работы.</span><span class="sxs-lookup"><span data-stu-id="c6af7-115">The application saves the user settings when the application shuts down.</span></span> <span data-ttu-id="c6af7-116">Чтобы сохранить параметры немедленно, вызовите метод `My.Settings.Save`.</span><span class="sxs-lookup"><span data-stu-id="c6af7-116">To save the settings immediately, call the `My.Settings.Save` method.</span></span> <span data-ttu-id="c6af7-117">Дополнительные сведения см. в разделе [Практическое руководство. Сохранение пользовательских параметров в Visual Basic](how-to-persist-user-settings.md).</span><span class="sxs-lookup"><span data-stu-id="c6af7-117">For more information, see [How to: Persist User Settings in Visual Basic](how-to-persist-user-settings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6af7-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c6af7-118">See also</span></span>

- [<span data-ttu-id="c6af7-119">Объект My.Settings</span><span class="sxs-lookup"><span data-stu-id="c6af7-119">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="c6af7-120">Практическое руководство. Чтение параметров приложения в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6af7-120">How to: Read Application Settings in Visual Basic</span></span>](how-to-read-application-settings.md)
- [<span data-ttu-id="c6af7-121">Практическое руководство. Сохранение пользовательских параметров в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6af7-121">How to: Persist User Settings in Visual Basic</span></span>](how-to-persist-user-settings.md)
- [<span data-ttu-id="c6af7-122">Практическое руководство. Создание таблицы свойств для пользовательских параметров в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6af7-122">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="c6af7-123">Управление параметрами приложения (.NET)</span><span class="sxs-lookup"><span data-stu-id="c6af7-123">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
