---
title: Критическое изменение. PrincipalPermissionAttribute устарел и является ошибочным
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где конструктор PrincipalPermissionAttribute устарел и вызывает ошибку во время компиляции.
ms.date: 11/01/2020
ms.openlocfilehash: 7568883935633e98b884b553efccf50504448b77
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257236"
---
# <a name="principalpermissionattribute-is-obsolete-as-error"></a>PrincipalPermissionAttribute устарел и является ошибочным

Конструктор <xref:System.Security.Permissions.PrincipalPermissionAttribute> устарел и вызывает ошибку времени компиляции. Нельзя создать экземпляр этого атрибута или применить его к методу.

## <a name="change-description"></a>Описание изменений

В .NET Framework и .NET Core можно добавлять заметки к методам с помощью атрибута <xref:System.Security.Permissions.PrincipalPermissionAttribute>. Пример:

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

Начиная с .NET 5 к методу нельзя применить атрибут <xref:System.Security.Permissions.PrincipalPermissionAttribute>. Конструктор атрибута устарел и вызывает ошибку во время компиляции. В отличие от других устаревших предупреждений, эту ошибку нельзя обойти.

## <a name="reason-for-change"></a>Причина изменения

Тип <xref:System.Security.Permissions.PrincipalPermissionAttribute>, как и другие типы, являющиеся подклассом <xref:System.Security.Permissions.SecurityAttribute>, является частью инфраструктуры .NET по управлению доступом для кода (CAS). В .NET Framework 2.x-4.x среда выполнения применяет заметки <xref:System.Security.Permissions.PrincipalPermissionAttribute> к записи метода, даже если приложение выполняется с полным доверием. В .NET Core и .NET 5 и более поздних версий не поддерживаются атрибуты CAS, и среда выполнения их игнорирует.

Это различие в поведении .NET Framework по отношению к .NET Core и .NET 5 может привести к ситуации "ошибочного открытия", когда доступ должен быть заблокирован, а вместо этого он был разрешен. Чтобы не допустить ситуации "ошибочного открытия", больше нельзя применять этот атрибут в коде, предназначенном для .NET 5 и более поздних версий.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name=""></a><a id="permission-action">Рекомендуемое действие</a>

При возникновении ошибки устаревшего атрибута необходимо выполнить определенные действия.

- **При применении атрибута к методу действия MVC ASP.NET:**

  Рассмотрите возможность использования встроенной инфраструктуры авторизации ASP.NET. В следующем примере кода показано, как добавить к контроллеру атрибут <xref:System.Web.Mvc.AuthorizeAttribute>. Среда выполнения ASP.NET выполнит авторизацию пользователя перед выполнением действия.

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

  Дополнительные сведения см. в статьях [Авторизация на основе ролей в ASP.NET Core](/aspnet/core/security/authorization/roles) и [Общие сведения об авторизации в ASP.NET Core](/aspnet/core/security/authorization/introduction).

- **При применении атрибута к коду библиотеки вне контекста веб-приложения:**

  Выполните проверки вручную в начале метода. Это можно сделать с помощью метода <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType>.

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

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- Security

### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->
