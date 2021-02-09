---
description: 'Подробнее о следующем: Практическое руководство. Чтение параметров приложения в Visual Basic'
title: Практическое руководство. Чтение параметров приложения
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 30b5a3b0cdf3565fc8c1f0dfa19e7717a714c350
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797826"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a><span data-ttu-id="dffe9-103">Практическое руководство. Чтение параметров приложения в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dffe9-103">How to: Read Application Settings in Visual Basic</span></span>

<span data-ttu-id="dffe9-104">Пользовательский параметр можно прочитать с помощью свойства объекта `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="dffe9-104">You can read a user setting by accessing the setting's property on the `My.Settings` object.</span></span>  
  
 <span data-ttu-id="dffe9-105">Объект `My.Settings` представляет каждый параметр в виде свойства.</span><span class="sxs-lookup"><span data-stu-id="dffe9-105">The `My.Settings` object exposes each setting as a property.</span></span> <span data-ttu-id="dffe9-106">Имя свойства совпадает с именем параметра, а тип свойства совпадает с типом параметра.</span><span class="sxs-lookup"><span data-stu-id="dffe9-106">The property name is the same as the setting name, and the property type is the same as the setting type.</span></span> <span data-ttu-id="dffe9-107">**Область** параметра определяет, доступно ли свойство только для чтения. Свойство для параметра с областью **Приложение** доступно только для чтения, а свойство для параметра с областью **Пользователь** доступно для чтения или записи.</span><span class="sxs-lookup"><span data-stu-id="dffe9-107">The setting's **Scope** indicates if the property is read-only; the property for an **Application** scope setting is read-only, while the property for a **User** scope setting is read-write.</span></span> <span data-ttu-id="dffe9-108">Дополнительные сведения см. в разделе [Объект My.Settings](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="dffe9-108">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dffe9-109">Пример</span><span class="sxs-lookup"><span data-stu-id="dffe9-109">Example</span></span>  

 <span data-ttu-id="dffe9-110">В этом пример выводится значение параметра `Nickname`.</span><span class="sxs-lookup"><span data-stu-id="dffe9-110">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="dffe9-111">Для надлежащего выполнения этого примера приложение должно иметь параметр `Nickname` типа `String`.</span><span class="sxs-lookup"><span data-stu-id="dffe9-111">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span> <span data-ttu-id="dffe9-112">Дополнительные сведения см. в разделе [Управление параметрами приложения (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="dffe9-112">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dffe9-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="dffe9-113">See also</span></span>

- [<span data-ttu-id="dffe9-114">Объект My.Settings</span><span class="sxs-lookup"><span data-stu-id="dffe9-114">My.Settings Object</span></span>](../../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="dffe9-115">Практическое руководство. Изменение пользовательских параметров в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dffe9-115">How to: Change User Settings in Visual Basic</span></span>](how-to-change-user-settings.md)
- [<span data-ttu-id="dffe9-116">Практическое руководство. Сохранение пользовательских параметров в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dffe9-116">How to: Persist User Settings in Visual Basic</span></span>](how-to-persist-user-settings.md)
- [<span data-ttu-id="dffe9-117">Практическое руководство. Создание таблицы свойств для пользовательских параметров в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dffe9-117">How to: Create Property Grids for User Settings in Visual Basic</span></span>](how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="dffe9-118">Управление параметрами приложения (.NET)</span><span class="sxs-lookup"><span data-stu-id="dffe9-118">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
