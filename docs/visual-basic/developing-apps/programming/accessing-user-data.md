---
description: 'Узнайте подробнее о: Доступ к пользователя (Visual Basic)'
title: Доступ к данным пользователя
ms.date: 07/20/2015
helpviewer_keywords:
- domain names [Visual Basic], retrieving
- data [Visual Basic], accessing user data
- My.User object [Visual Basic], tasks
- user data [Visual Basic], domain
- user names [Visual Basic], retrieving
- user data [Visual Basic], accessing
- login names [Visual Basic]
- examples [Visual Basic], accessing user data
ms.assetid: 32492a15-ee59-4a63-a1f1-9b24cc13140a
ms.openlocfilehash: 4f7f7a8cb121b74a2680f29c0aa14491f6e38434
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797878"
---
# <a name="accessing-user-data-visual-basic"></a><span data-ttu-id="9bd6c-103">Доступ к пользователя (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bd6c-103">Accessing User Data (Visual Basic)</span></span>

<span data-ttu-id="9bd6c-104">В этом разделе рассматриваются вопросы, связанные с объектом `My.User` и задачами, которые можно выполнять с его помощью.</span><span class="sxs-lookup"><span data-stu-id="9bd6c-104">This section contains topics dealing with the `My.User` object and tasks that you can accomplish with it.</span></span>  
  
 <span data-ttu-id="9bd6c-105">Объект `My.User` предоставляет доступ к сведениям о вошедшем в систему пользователе, возвращая объект, реализующий интерфейс <xref:System.Security.Principal.IPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="9bd6c-105">The `My.User` object provides access to information about the logged-on user by returning an object that implements the <xref:System.Security.Principal.IPrincipal> interface.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="9bd6c-106">Задачи</span><span class="sxs-lookup"><span data-stu-id="9bd6c-106">Tasks</span></span>  
  
|<span data-ttu-id="9bd6c-107">Кому</span><span class="sxs-lookup"><span data-stu-id="9bd6c-107">To</span></span>|<span data-ttu-id="9bd6c-108">См.</span><span class="sxs-lookup"><span data-stu-id="9bd6c-108">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="9bd6c-109">Получение имени входа пользователя</span><span class="sxs-lookup"><span data-stu-id="9bd6c-109">Get the user's login name</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.Name%2A>|  
|<span data-ttu-id="9bd6c-110">Получение имени домена пользователя, если приложение использует проверку подлинности Windows</span><span class="sxs-lookup"><span data-stu-id="9bd6c-110">Get the user's domain name, if the application uses Windows authentication</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.CurrentPrincipal>|  
|<span data-ttu-id="9bd6c-111">Определение роли пользователя</span><span class="sxs-lookup"><span data-stu-id="9bd6c-111">Determine the user's role</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="9bd6c-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9bd6c-112">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.User>
