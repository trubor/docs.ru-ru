---
description: 'Узнайте подробнее о: Доступ к формам приложения (Visual Basic)'
title: Доступ к формам приложения
ms.date: 07/20/2015
helpviewer_keywords:
- forms [Visual Basic], communicating between
- application forms [Visual Basic], accessing
- forms [Visual Basic], accessing one from another
- My.Forms object
- forms [Visual Basic], accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
ms.openlocfilehash: dae73700434f9cdbb145ebea605c87c33f7c0c73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797904"
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="3b8ce-103">Доступ к формам приложения (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b8ce-103">Accessing Application Forms (Visual Basic)</span></span>

<span data-ttu-id="3b8ce-104">Объект `My.Forms` предоставляет простой способ доступа к экземпляру каждой формы Windows, объявленной в проекте приложения.</span><span class="sxs-lookup"><span data-stu-id="3b8ce-104">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="3b8ce-105">Для доступа к экрану-заставке и основной форме приложения, а также для получения списка открытых форм приложения можно также использовать свойства объекта `My.Application`.</span><span class="sxs-lookup"><span data-stu-id="3b8ce-105">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="3b8ce-106">Задачи</span><span class="sxs-lookup"><span data-stu-id="3b8ce-106">Tasks</span></span>  

 <span data-ttu-id="3b8ce-107">Приведенная ниже таблица содержит примеры, показывающие, как получить доступ к формам приложения.</span><span class="sxs-lookup"><span data-stu-id="3b8ce-107">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="3b8ce-108">Кому</span><span class="sxs-lookup"><span data-stu-id="3b8ce-108">To</span></span>|<span data-ttu-id="3b8ce-109">См.</span><span class="sxs-lookup"><span data-stu-id="3b8ce-109">See</span></span>|  
|---|---|  
|<span data-ttu-id="3b8ce-110">Доступ к одной форме приложения из другой</span><span class="sxs-lookup"><span data-stu-id="3b8ce-110">Access one form from another form in an application.</span></span>|[<span data-ttu-id="3b8ce-111">Объект My.Forms</span><span class="sxs-lookup"><span data-stu-id="3b8ce-111">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="3b8ce-112">Отображение заголовков всех открытых форм приложения</span><span class="sxs-lookup"><span data-stu-id="3b8ce-112">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="3b8ce-113">Обновление данных о состоянии на экране-заставке при запуске приложения</span><span class="sxs-lookup"><span data-stu-id="3b8ce-113">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="3b8ce-114">См. также</span><span class="sxs-lookup"><span data-stu-id="3b8ce-114">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>
- [<span data-ttu-id="3b8ce-115">Объект My.Forms</span><span class="sxs-lookup"><span data-stu-id="3b8ce-115">My.Forms Object</span></span>](../../language-reference/objects/my-forms-object.md)
