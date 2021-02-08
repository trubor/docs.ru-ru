---
description: 'Дополнительные сведения о: начальная форма не указана'
title: Начальная форма не указана
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 4b00890f07121ef55ce49978842010cc54aba29b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797189"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="baa04-103">Начальная форма не указана</span><span class="sxs-lookup"><span data-stu-id="baa04-103">A startup form has not been specified</span></span>

<span data-ttu-id="baa04-104">Приложение использует класс, <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> но не задает начальную форму.</span><span class="sxs-lookup"><span data-stu-id="baa04-104">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="baa04-105">Это может произойти, если в конструкторе проектов установлен флажок **Включить платформу приложений** , но не указана **Форма запуска** .</span><span class="sxs-lookup"><span data-stu-id="baa04-105">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="baa04-106">Дополнительные сведения см. в разделе [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="baa04-106">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="baa04-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="baa04-107">To correct this error</span></span>  
  
1. <span data-ttu-id="baa04-108">Укажите объект запуска для приложения.</span><span class="sxs-lookup"><span data-stu-id="baa04-108">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="baa04-109">Дополнительные сведения см. в разделе [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="baa04-109">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2. <span data-ttu-id="baa04-110">Переопределите <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> метод, чтобы задать <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> для свойства начальную форму.</span><span class="sxs-lookup"><span data-stu-id="baa04-110">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa04-111">См. также</span><span class="sxs-lookup"><span data-stu-id="baa04-111">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="baa04-112">Обзор модели приложения в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="baa04-112">Overview of the Visual Basic Application Model</span></span>](../../developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
