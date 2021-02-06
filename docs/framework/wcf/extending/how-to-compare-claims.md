---
description: 'Дополнительные сведения: инструкции по сравнению утверждений'
title: Практическое руководство. Сравнение утверждений
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
ms.openlocfilehash: c2088ad3992852bdc12e7bcd71d5f3598a237b45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653853"
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="36ec7-103">Практическое руководство. Сравнение утверждений</span><span class="sxs-lookup"><span data-stu-id="36ec7-103">How to: Compare Claims</span></span>

<span data-ttu-id="36ec7-104">Инфраструктура модели удостоверений в Windows Communication Foundation (WCF) используется для выполнения проверки авторизации.</span><span class="sxs-lookup"><span data-stu-id="36ec7-104">The Identity Model infrastructure in Windows Communication Foundation (WCF) is used to perform authorization checking.</span></span> <span data-ttu-id="36ec7-105">По существу общей задачей является сравнение утверждений в контексте авторизации с утверждениями, необходимыми для выполнения затребованного действия или доступа к затребованному ресурсу.</span><span class="sxs-lookup"><span data-stu-id="36ec7-105">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="36ec7-106">В этом разделе описывается сравнение утверждений, включая встроенные и пользовательские типы утверждений.</span><span class="sxs-lookup"><span data-stu-id="36ec7-106">This topic describes how to compare claims, including built-in and custom claim types.</span></span> <span data-ttu-id="36ec7-107">Дополнительные сведения о инфраструктуре модели удостоверений см. [в статье Управление утверждениями и авторизацией с помощью модели удостоверений](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="36ec7-107">For more information about the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="36ec7-108">При сравнении утверждений сравниваются три элемента одного утверждения (тип, право и ресурс) с аналогичными элементами другого утверждения, чтобы определить, одинаковы ли они.</span><span class="sxs-lookup"><span data-stu-id="36ec7-108">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="36ec7-109">См. следующий пример.</span><span class="sxs-lookup"><span data-stu-id="36ec7-109">See the following example.</span></span>

[!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
[!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]

<span data-ttu-id="36ec7-110">Оба утверждения будут иметь тип имени <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, право свойства <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> и ресурс строки «someone».</span><span class="sxs-lookup"><span data-stu-id="36ec7-110">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="36ec7-111">Поскольку все три элемента утверждения одинаковы, сами утверждения одинаковы.</span><span class="sxs-lookup"><span data-stu-id="36ec7-111">As all three parts of the claim are equal, the claims themselves are equal.</span></span>

<span data-ttu-id="36ec7-112">Встроенные типы утверждений сравниваются с помощью метода <xref:System.IdentityModel.Claims.Claim.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="36ec7-112">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="36ec7-113">При необходимости используется код сравнения, зависящий от утверждений.</span><span class="sxs-lookup"><span data-stu-id="36ec7-113">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="36ec7-114">Например, пусть заданы следующие два утверждения с именем участника-пользователя:</span><span class="sxs-lookup"><span data-stu-id="36ec7-114">For example, given the following two user principal name (UPN) claims:</span></span>

[!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
[!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]

<span data-ttu-id="36ec7-115">код сравнения в <xref:System.IdentityModel.Claims.Claim.Equals%2A> методе возвращает `true` , предполагая, что `example\someone` он идентифицирует того же пользователя домена, что и " someone@example.com ".</span><span class="sxs-lookup"><span data-stu-id="36ec7-115">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>

<span data-ttu-id="36ec7-116">Пользовательские типы утверждений также могут сравниваться с помощью метода <xref:System.IdentityModel.Claims.Claim.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="36ec7-116">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="36ec7-117">Однако в тех случаях, когда тип, возвращенный свойством <xref:System.IdentityModel.Claims.Claim.Resource%2A> утверждения, несколько отличается от типа-примитива, метод <xref:System.IdentityModel.Claims.Claim.Equals%2A> возвращает значение `true`, только если значения, возвращенные свойствами `Resource`, одинаковы для каждого метода <xref:System.IdentityModel.Claims.Claim.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="36ec7-117">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="36ec7-118">В других случаях пользовательский тип, возвращенный свойством `Resource`, должен переопределить методы <xref:System.IdentityModel.Claims.Claim.Equals%2A> и <xref:System.Object.GetHashCode%2A>, чтобы выполнить любую необходимую пользовательскую обработку.</span><span class="sxs-lookup"><span data-stu-id="36ec7-118">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>

## <a name="comparing-built-in-claims"></a><span data-ttu-id="36ec7-119">Сравнение встроенных утверждений</span><span class="sxs-lookup"><span data-stu-id="36ec7-119">Comparing built-in claims</span></span>

1. <span data-ttu-id="36ec7-120">Пусть заданы два экземпляра класса <xref:System.IdentityModel.Claims.Claim>. Используйте метод <xref:System.IdentityModel.Claims.Claim.Equals%2A> для выполнения сравнения, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="36ec7-120">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]

### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="36ec7-121">Сравнение пользовательских утверждений с типами-примитивами ресурсов</span><span class="sxs-lookup"><span data-stu-id="36ec7-121">Comparing custom claims with primitive resource types</span></span>

1. <span data-ttu-id="36ec7-122">Для пользовательских утверждений с типами-примитивами ресурсов сравнение может выполняться аналогично сравнению для встроенных утверждений, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="36ec7-122">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>

     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]

2. <span data-ttu-id="36ec7-123">Для пользовательских утверждений с типами ресурсов на основе структур или классов тип ресурса должен переопределить метод <xref:System.IdentityModel.Claims.Claim.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="36ec7-123">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>

3. <span data-ttu-id="36ec7-124">Сначала проверьте, имеет ли параметр `obj` значение `null`. Если да, верните значение `false`.</span><span class="sxs-lookup"><span data-stu-id="36ec7-124">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>

     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]

4. <span data-ttu-id="36ec7-125">Затем вызовите метод <xref:System.Object.ReferenceEquals%2A> и передайте `this` и `obj` в качестве параметров.</span><span class="sxs-lookup"><span data-stu-id="36ec7-125">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="36ec7-126">Если этот метод возвращает значение `true`, верните значение `true`.</span><span class="sxs-lookup"><span data-stu-id="36ec7-126">If it returns `true`, then return `true`.</span></span>

     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]

5. <span data-ttu-id="36ec7-127">Затем попытайтесь присвоить значение `obj` локальной переменной типа класса.</span><span class="sxs-lookup"><span data-stu-id="36ec7-127">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="36ec7-128">Если эта попытка завершается неуспешно, ссылка имеет значение `null`.</span><span class="sxs-lookup"><span data-stu-id="36ec7-128">If this fails, the reference is `null`.</span></span> <span data-ttu-id="36ec7-129">В этом случае верните значение `false`.</span><span class="sxs-lookup"><span data-stu-id="36ec7-129">In such cases, return `false`.</span></span>

6. <span data-ttu-id="36ec7-130">Выполните пользовательское сравнение, необходимое для правильного сравнения текущего утверждения с предоставленным утверждением.</span><span class="sxs-lookup"><span data-stu-id="36ec7-130">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>

## <a name="example"></a><span data-ttu-id="36ec7-131">Пример</span><span class="sxs-lookup"><span data-stu-id="36ec7-131">Example</span></span>

<span data-ttu-id="36ec7-132">В следующем примере показано сравнение пользовательских утверждений, где ресурсом утверждения является тип, отличный от типа-примитива.</span><span class="sxs-lookup"><span data-stu-id="36ec7-132">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>

[!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
[!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]

## <a name="see-also"></a><span data-ttu-id="36ec7-133">См. также</span><span class="sxs-lookup"><span data-stu-id="36ec7-133">See also</span></span>

- [<span data-ttu-id="36ec7-134">Управление утверждениями и авторизацией с помощью модели удостоверения</span><span class="sxs-lookup"><span data-stu-id="36ec7-134">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="36ec7-135">Практическое руководство. Создание пользовательского утверждения</span><span class="sxs-lookup"><span data-stu-id="36ec7-135">How to: Create a Custom Claim</span></span>](how-to-create-a-custom-claim.md)
