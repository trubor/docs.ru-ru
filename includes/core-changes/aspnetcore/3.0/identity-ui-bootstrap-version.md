---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032793"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="01822-101">Удостоверение. Изменение версии Bootstrap пользовательского интерфейса по умолчанию</span><span class="sxs-lookup"><span data-stu-id="01822-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="01822-102">Начиная с ASP.NET Core 3.0, пользовательский интерфейс удостоверений по умолчанию использует Bootstrap версии 4.</span><span class="sxs-lookup"><span data-stu-id="01822-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="01822-103">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="01822-103">Version introduced</span></span>

<span data-ttu-id="01822-104">3.0</span><span class="sxs-lookup"><span data-stu-id="01822-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="01822-105">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="01822-105">Old behavior</span></span>

<span data-ttu-id="01822-106">Вызов метода `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` был таким же, как и `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`.</span><span class="sxs-lookup"><span data-stu-id="01822-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="01822-107">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="01822-107">New behavior</span></span>

<span data-ttu-id="01822-108">Вызов метода `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` такой же, как и `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`.</span><span class="sxs-lookup"><span data-stu-id="01822-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="01822-109">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="01822-109">Reason for change</span></span>

<span data-ttu-id="01822-110">Выпуск Bootstrap версии 4 соответствует временному интервалу для ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="01822-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="01822-111">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="01822-111">Recommended action</span></span>

<span data-ttu-id="01822-112">Это изменение затронет вас, если вы используете пользовательский интерфейс удостоверений по умолчанию и добавили его в `Startup.ConfigureServices`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="01822-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="01822-113">Выполните одно из указанных ниже действий.</span><span class="sxs-lookup"><span data-stu-id="01822-113">Take one of the following actions:</span></span>

- <span data-ttu-id="01822-114">перенесите приложение для использования Bootstrap 4, следуя [инструкциям по переносу](https://getbootstrap.com/docs/4.0/migration);</span><span class="sxs-lookup"><span data-stu-id="01822-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="01822-115">обновите `Startup.ConfigureServices` для принудительного использования Bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="01822-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="01822-116">Пример:</span><span class="sxs-lookup"><span data-stu-id="01822-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="01822-117">Категория</span><span class="sxs-lookup"><span data-stu-id="01822-117">Category</span></span>

<span data-ttu-id="01822-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="01822-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="01822-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="01822-119">Affected APIs</span></span>

<span data-ttu-id="01822-120">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="01822-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
