---
description: 'Дополнительные сведения: замена объекта Principal'
title: Замена объекта Principal
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET], replacing principal objects
- security [.NET], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
ms.openlocfilehash: 3f413a3b0824cef9f28454bf109d40556f61c26b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684988"
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="bf91c-103">Замена объекта Principal</span><span class="sxs-lookup"><span data-stu-id="bf91c-103">Replacing a Principal Object</span></span>

<span data-ttu-id="bf91c-104">Приложения, предоставляющие службы проверки подлинности, должны иметь возможность заменять объект **Principal** (<xref:System.Security.Principal.IPrincipal>) для данного потока.</span><span class="sxs-lookup"><span data-stu-id="bf91c-104">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="bf91c-105">Более того, система безопасности должна защищать возможность замены объектов **Principal** , так как злонамеренно подключенный неправильный **Principal** является угрозой безопасности приложения, предоставляя неверное удостоверение или роль.</span><span class="sxs-lookup"><span data-stu-id="bf91c-105">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="bf91c-106">Таким образом, приложениям, которым требуется возможность замены объектов **Principal** , должен быть предоставлен объект <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> для элемента управления "Участник".</span><span class="sxs-lookup"><span data-stu-id="bf91c-106">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="bf91c-107">(Обратите внимание, что это разрешение не требуется для выполнения проверок безопасности на основе ролей или для создания объектов **Principal** .)</span><span class="sxs-lookup"><span data-stu-id="bf91c-107">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
<span data-ttu-id="bf91c-108">Текущий объект **Principal** можно заменить, выполнив следующие задачи.</span><span class="sxs-lookup"><span data-stu-id="bf91c-108">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="bf91c-109">Создайте замещающий объект **Principal** и связанный объект **Identity** (удостоверение).</span><span class="sxs-lookup"><span data-stu-id="bf91c-109">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2. <span data-ttu-id="bf91c-110">Подключите новый объект **Principal** к контексту вызова.</span><span class="sxs-lookup"><span data-stu-id="bf91c-110">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf91c-111">Пример</span><span class="sxs-lookup"><span data-stu-id="bf91c-111">Example</span></span>

<span data-ttu-id="bf91c-112">В следующем примере показывается, как создать универсальный объект Principal и использовать его для задания участника потока.</span><span class="sxs-lookup"><span data-stu-id="bf91c-112">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
[!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
[!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bf91c-113">См. также</span><span class="sxs-lookup"><span data-stu-id="bf91c-113">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [<span data-ttu-id="bf91c-114">Объекты Principal и Identity</span><span class="sxs-lookup"><span data-stu-id="bf91c-114">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="bf91c-115">Безопасность ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bf91c-115">ASP.NET Core Security</span></span>](/aspnet/core/security/)
