---
description: 'Дополнительные сведения о: BC42017: разрешение с поздним связыванием; могут возникнуть ошибки времени выполнения'
title: Разрешение позднего связывания; возможно возникновение ошибок времени выполнения
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 2c783a7aff46df8ab033463f49c45f4c797220ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795928"
---
# <a name="bc42017-late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="560a2-103">BC42017: разрешение с поздним связыванием; могут возникнуть ошибки времени выполнения</span><span class="sxs-lookup"><span data-stu-id="560a2-103">BC42017: Late bound resolution; runtime errors could occur</span></span>

<span data-ttu-id="560a2-104">Объект присваивается переменной, объявленной с [типом данных Object](../data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="560a2-104">An object is assigned to a variable declared to be of the [Object Data Type](../data-types/object-data-type.md).</span></span>

 <span data-ttu-id="560a2-105">При объявлении переменной как `Object` , компилятор должен выполнить *позднее связывание*, что приводит к дополнительным операциям во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="560a2-105">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="560a2-106">Это также подвергает ваше приложение риску ошибок времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="560a2-106">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="560a2-107">Например, если присвоить значение <xref:System.Windows.Forms.Form> `Object` переменной и попытаться получить доступ к <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> свойству, среда выполнения выдаст исключение, <xref:System.MemberAccessException> поскольку <xref:System.Windows.Forms.Form> класс не предоставляет `NameTable` свойство.</span><span class="sxs-lookup"><span data-stu-id="560a2-107">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>

 <span data-ttu-id="560a2-108">Если объявить переменную с конкретным типом, компилятор может выполнять *раннее связывание* во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="560a2-108">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="560a2-109">Это приводит к повышению производительности, управляемому доступу к членам конкретного типа и повышению удобочитаемости кода.</span><span class="sxs-lookup"><span data-stu-id="560a2-109">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>

 <span data-ttu-id="560a2-110">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="560a2-110">By default, this message is a warning.</span></span> <span data-ttu-id="560a2-111">Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="560a2-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="560a2-112">**Идентификатор ошибки:** BC42017</span><span class="sxs-lookup"><span data-stu-id="560a2-112">**Error ID:** BC42017</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="560a2-113">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="560a2-113">To correct this error</span></span>

- <span data-ttu-id="560a2-114">Если возможно, объявите переменную с конкретным типом.</span><span class="sxs-lookup"><span data-stu-id="560a2-114">If possible, declare the variable to be of a specific type.</span></span>

## <a name="see-also"></a><span data-ttu-id="560a2-115">См. также</span><span class="sxs-lookup"><span data-stu-id="560a2-115">See also</span></span>

- [<span data-ttu-id="560a2-116">Раннее и позднее связывание</span><span class="sxs-lookup"><span data-stu-id="560a2-116">Early and Late Binding</span></span>](../../programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="560a2-117">Объявление объектной переменной</span><span class="sxs-lookup"><span data-stu-id="560a2-117">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
