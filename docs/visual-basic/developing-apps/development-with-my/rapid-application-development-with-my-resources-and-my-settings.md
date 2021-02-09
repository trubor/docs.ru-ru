---
description: 'Узнайте подробнее о: Быстрая разработка приложений с использованием My.Resources и My.Settings (Visual Basic)'
title: Быстрая разработка приложений с использованием My.Resources и My.Settings
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 38846b3a6ac273306f588ad8b043d7f35f7230a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797930"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a><span data-ttu-id="5e8f4-103">Быстрая разработка приложений с использованием My.Resources и My.Settings (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e8f4-103">Rapid Application Development with My.Resources and My.Settings (Visual Basic)</span></span>

<span data-ttu-id="5e8f4-104">Объект `My.Resources` предоставляет доступ к ресурсам приложения и позволяет динамически получать ресурсы для приложения.</span><span class="sxs-lookup"><span data-stu-id="5e8f4-104">The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.</span></span>  
  
## <a name="retrieving-resources"></a><span data-ttu-id="5e8f4-105">Извлечение ресурсов</span><span class="sxs-lookup"><span data-stu-id="5e8f4-105">Retrieving Resources</span></span>  

 <span data-ttu-id="5e8f4-106">С помощью объекта `My.Resources` можно получить ряд ресурсов, включая аудиофайлы, значки, изображения и строки.</span><span class="sxs-lookup"><span data-stu-id="5e8f4-106">A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object.</span></span> <span data-ttu-id="5e8f4-107">Например, можно получить доступ к файлам ресурсов, относящимся к языку и региональным параметрам приложения.</span><span class="sxs-lookup"><span data-stu-id="5e8f4-107">For example, you can access the application's culture-specific resource files.</span></span> <span data-ttu-id="5e8f4-108">В следующем примере значку с именем `Form1Icon`, хранимому в файле ресурсов приложения, задается значок формы.</span><span class="sxs-lookup"><span data-stu-id="5e8f4-108">The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.</span></span>  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 <span data-ttu-id="5e8f4-109">Объект `My.Resources` предоставляет только глобальные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="5e8f4-109">The `My.Resources` object exposes only global resources.</span></span> <span data-ttu-id="5e8f4-110">Он не предоставляет доступ к файлам ресурсов, связанным с формами.</span><span class="sxs-lookup"><span data-stu-id="5e8f4-110">It does not provide access to resource files associated with forms.</span></span> <span data-ttu-id="5e8f4-111">Обращайтесь к ресурсам формы из самой формы.</span><span class="sxs-lookup"><span data-stu-id="5e8f4-111">Access the form resources from the form.</span></span>  
  
 <span data-ttu-id="5e8f4-112">Аналогичным образом объект `My.Settings` предоставляет доступ к параметрам приложения, позволяя динамически сохранять и извлекать параметры свойств и другие сведения для приложения.</span><span class="sxs-lookup"><span data-stu-id="5e8f4-112">Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="5e8f4-113">См. сведения о [My.Resources Object](../../language-reference/objects/my-resources-object.md) и [My.Settings Object](../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="5e8f4-113">For more information, see [My.Resources Object](../../language-reference/objects/my-resources-object.md) and [My.Settings Object](../../language-reference/objects/my-settings-object.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e8f4-114">См. также</span><span class="sxs-lookup"><span data-stu-id="5e8f4-114">See also</span></span>

- [<span data-ttu-id="5e8f4-115">Объект My.Resources</span><span class="sxs-lookup"><span data-stu-id="5e8f4-115">My.Resources Object</span></span>](../../language-reference/objects/my-resources-object.md)
- [<span data-ttu-id="5e8f4-116">Объект My.Settings</span><span class="sxs-lookup"><span data-stu-id="5e8f4-116">My.Settings Object</span></span>](../../language-reference/objects/my-settings-object.md)
- [<span data-ttu-id="5e8f4-117">Доступ к параметрам приложения</span><span class="sxs-lookup"><span data-stu-id="5e8f4-117">Accessing Application Settings</span></span>](../programming/app-settings/index.md)
