---
description: Дополнительные сведения о том, как создать объект WindowsPrincipal.
title: Практическое руководство. Создание объекта WindowsPrincipal
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET], creating a WindowsPrincipal object
- security [.NET], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
ms.openlocfilehash: eee33eb419e8626b8b7f627b9ab1e46ea8dceab5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685235"
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="acfb5-103">Практическое руководство. Создание объекта WindowsPrincipal</span><span class="sxs-lookup"><span data-stu-id="acfb5-103">How to: Create a WindowsPrincipal Object</span></span>

> [!NOTE]
> <span data-ttu-id="acfb5-104">Эта статья относится к Windows.</span><span class="sxs-lookup"><span data-stu-id="acfb5-104">This article applies to Windows.</span></span>
>
> <span data-ttu-id="acfb5-105">Сведения о ASP.NET Core см. в разделе [ASP.NET Core Security](/aspnet/core/security/).</span><span class="sxs-lookup"><span data-stu-id="acfb5-105">For information about ASP.NET Core, see [ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="acfb5-106">Существует два способа создания объекта <xref:System.Security.Principal.WindowsPrincipal> в зависимости от того, должен ли код выполнять проверку на основании ролей многократно или всего один раз.</span><span class="sxs-lookup"><span data-stu-id="acfb5-106">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
<span data-ttu-id="acfb5-107">Если код должен многократно выполнять проверку на основе ролей, первая из следующих процедур создает меньше служебных данных.</span><span class="sxs-lookup"><span data-stu-id="acfb5-107">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="acfb5-108">Если коду требуется выполнять проверку на основе ролей только один раз, можно создать объект <xref:System.Security.Principal.WindowsPrincipal> при помощи второй из приведенных ниже процедур.</span><span class="sxs-lookup"><span data-stu-id="acfb5-108">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="acfb5-109">Создание объекта WindowsPrincipal для повторяющейся проверки</span><span class="sxs-lookup"><span data-stu-id="acfb5-109">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1. <span data-ttu-id="acfb5-110">Вызовите метод <xref:System.AppDomain.SetPrincipalPolicy%2A> для объекта <xref:System.AppDomain>, возвращенного статическим свойством <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType>, передав в метод <xref:System.Security.Principal.PrincipalPolicy> значение перечисления, которое указывает, какой должна быть новая политика.</span><span class="sxs-lookup"><span data-stu-id="acfb5-110">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="acfb5-111">Поддерживаются значения <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> и <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="acfb5-111">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="acfb5-112">Вызов этого метода демонстрируется в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="acfb5-112">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. <span data-ttu-id="acfb5-113">После задания политики используйте статическое свойство <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> для извлечения субъекта, инкапсулирующего текущего пользователя Windows.</span><span class="sxs-lookup"><span data-stu-id="acfb5-113">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="acfb5-114">Поскольку возвращаемое свойство имеет тип <xref:System.Security.Principal.IPrincipal>, результат необходимо привести к типу <xref:System.Security.Principal.WindowsPrincipal>.</span><span class="sxs-lookup"><span data-stu-id="acfb5-114">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="acfb5-115">Следующий код инициализирует новый объект <xref:System.Security.Principal.WindowsPrincipal> значением субъекта, связанного с текущим потоком.</span><span class="sxs-lookup"><span data-stu-id="acfb5-115">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal =
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)
    ```  
  
3. <span data-ttu-id="acfb5-116">После создания объекта субъекта можно использовать один из нескольких методов для его проверки.</span><span class="sxs-lookup"><span data-stu-id="acfb5-116">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="acfb5-117">Создание объекта WindowsPrincipal для однократной проверки</span><span class="sxs-lookup"><span data-stu-id="acfb5-117">To create a WindowsPrincipal object for a single validation</span></span>  
  
1. <span data-ttu-id="acfb5-118">Инициализируйте новый объект <xref:System.Security.Principal.WindowsIdentity> путем вызова статического метода <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType>, который отправляет запрос в текущую учетную запись Windows и помещает сведения об этой учетной записи во вновь созданный объект идентификатора.</span><span class="sxs-lookup"><span data-stu-id="acfb5-118">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="acfb5-119">Следующий код создает новый объект <xref:System.Security.Principal.WindowsIdentity> и инициализирует его текущим пользователем, прошедшим проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="acfb5-119">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. <span data-ttu-id="acfb5-120">Создайте новый объект <xref:System.Security.Principal.WindowsPrincipal> и передайте ему значение объекта <xref:System.Security.Principal.WindowsIdentity>, созданного в предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="acfb5-120">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. <span data-ttu-id="acfb5-121">После создания объекта субъекта можно использовать один из нескольких методов для его проверки.</span><span class="sxs-lookup"><span data-stu-id="acfb5-121">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acfb5-122">См. также</span><span class="sxs-lookup"><span data-stu-id="acfb5-122">See also</span></span>

- [<span data-ttu-id="acfb5-123">Объекты Principal и Identity</span><span class="sxs-lookup"><span data-stu-id="acfb5-123">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="acfb5-124">Безопасность ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="acfb5-124">ASP.NET Core Security</span></span>](/aspnet/core/security/)
