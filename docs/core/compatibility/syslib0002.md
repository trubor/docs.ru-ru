---
title: Ошибка SYSLIB0002
description: Сведения об устаревших элементах, которые приводят к появлению ошибки во время компиляции SYSLIB0002.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 36ecde3c52845a6594c4d04e167df48142038654
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437503"
---
# <a name="syslib0002-principalpermissionattribute-is-obsolete"></a><span data-ttu-id="64116-103">SYSLIB0002. PrincipalPermissionAttribute устарел</span><span class="sxs-lookup"><span data-stu-id="64116-103">SYSLIB0002: PrincipalPermissionAttribute is obsolete</span></span>

<span data-ttu-id="64116-104">Начиная с версии .NET 5.0, конструктор <xref:System.Security.Permissions.PrincipalPermissionAttribute> является устаревшим и вызывает ошибку времени компиляции `SYSLIB0002`.</span><span class="sxs-lookup"><span data-stu-id="64116-104">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces compile-time error `SYSLIB0002`, starting in .NET 5.0.</span></span> <span data-ttu-id="64116-105">Нельзя создать экземпляр этого атрибута или применить его к методу.</span><span class="sxs-lookup"><span data-stu-id="64116-105">You cannot instantiate this attribute or apply it to a method.</span></span>

<span data-ttu-id="64116-106">В отличие от других устаревших предупреждений, эту ошибку нельзя обойти.</span><span class="sxs-lookup"><span data-stu-id="64116-106">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="64116-107">Обходные пути</span><span class="sxs-lookup"><span data-stu-id="64116-107">Workarounds</span></span>

- <span data-ttu-id="64116-108">При применении атрибута к методу действия MVC ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="64116-108">If you're applying the attribute to an ASP.NET MVC action method:</span></span>

  <span data-ttu-id="64116-109">Рассмотрите возможность использования встроенной инфраструктуры авторизации ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="64116-109">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="64116-110">В следующем примере кода показано, как добавить к контроллеру атрибут <xref:System.Web.Mvc.AuthorizeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="64116-110">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="64116-111">Среда выполнения ASP.NET выполнит авторизацию пользователя перед выполнением действия.</span><span class="sxs-lookup"><span data-stu-id="64116-111">The ASP.NET runtime will authorize the user before performing the action.</span></span>

  ```csharp
  using Microsoft.AspNetCore.Authorization;

  namespace MySampleApp
  {
      [Authorize(Roles = "Administrator")]
      public class AdministrationController : Controller
      {
          public ActionResult MyAction()
          {
              // This code won't run unless the current user
              // is in the 'Administrator' role.
          }
      }
  }
  ```

  <span data-ttu-id="64116-112">Дополнительные сведения см. в статьях [Авторизация на основе ролей в ASP.NET Core](/aspnet/core/security/authorization/roles) и [Общие сведения об авторизации в ASP.NET Core](/aspnet/core/security/authorization/introduction).</span><span class="sxs-lookup"><span data-stu-id="64116-112">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="64116-113">При применении атрибута к коду библиотеки вне контекста веб-приложения:</span><span class="sxs-lookup"><span data-stu-id="64116-113">If you're applying the attribute to library code outside the context of a web app:</span></span>

  <span data-ttu-id="64116-114">Выполните проверки вручную в начале метода, вызвав метод <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="64116-114">Perform the checks manually at the beginning of your method by calling the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

  ```csharp
  using System.Threading;

  void DoSomething()
  {
      if (Thread.CurrentPrincipal == null
          || !Thread.CurrentPrincipal.IsInRole("Administrators"))
      {
          throw new Exception("User is anonymous or isn't an admin.");
      }

      // Code that should run only when user is an administrator.
  }
  ```

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="64116-115">См. также</span><span class="sxs-lookup"><span data-stu-id="64116-115">See also</span></span>

- [<span data-ttu-id="64116-116">PrincipalPermissionAttribute устарел и является ошибочным</span><span class="sxs-lookup"><span data-stu-id="64116-116">PrincipalPermissionAttribute is obsolete as error</span></span>](core-libraries/5.0/principalpermissionattribute-obsolete.md)
