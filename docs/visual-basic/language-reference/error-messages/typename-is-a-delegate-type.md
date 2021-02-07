---
description: 'Дополнительные сведения о: BC32008: " <typename> " является типом делегата'
title: <typename> является типом делегата
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 72aac48038c433b7938c54e7f1138a5b91bf7689
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675030"
---
# <a name="bc32008-typename-is-a-delegate-type"></a><span data-ttu-id="9f81f-103">BC32008: " \<typename> " является типом делегата</span><span class="sxs-lookup"><span data-stu-id="9f81f-103">BC32008: '\<typename>' is a delegate type</span></span>

<span data-ttu-id="9f81f-104">" \<typename> " является типом делегата.</span><span class="sxs-lookup"><span data-stu-id="9f81f-104">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="9f81f-105">Конструкция делегата позволяет использовать только одно выражение AddressOf в качестве списка аргументов.</span><span class="sxs-lookup"><span data-stu-id="9f81f-105">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="9f81f-106">Часто выражение AddressOf можно использовать вместо конструкции делегата.</span><span class="sxs-lookup"><span data-stu-id="9f81f-106">Often an AddressOf expression can be used instead of a delegate construction.</span></span>

 <span data-ttu-id="9f81f-107">`New`Предложение, создающее экземпляр класса делегата, предоставляет конструктору делегата недопустимый список аргументов.</span><span class="sxs-lookup"><span data-stu-id="9f81f-107">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>

 <span data-ttu-id="9f81f-108">`AddressOf`При создании нового экземпляра делегата можно указать только одно выражение.</span><span class="sxs-lookup"><span data-stu-id="9f81f-108">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>

 <span data-ttu-id="9f81f-109">Эта ошибка может возникнуть, если вы не передаете аргументы конструктору делегата, если передаете несколько аргументов или передаете один аргумент, который не является допустимым `AddressOf` выражением.</span><span class="sxs-lookup"><span data-stu-id="9f81f-109">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>

 <span data-ttu-id="9f81f-110">**Идентификатор ошибки:** BC32008</span><span class="sxs-lookup"><span data-stu-id="9f81f-110">**Error ID:** BC32008</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9f81f-111">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="9f81f-111">To correct this error</span></span>

- <span data-ttu-id="9f81f-112">Используйте одно `AddressOf` выражение в списке аргументов для класса делегата в `New` предложении.</span><span class="sxs-lookup"><span data-stu-id="9f81f-112">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f81f-113">См. также</span><span class="sxs-lookup"><span data-stu-id="9f81f-113">See also</span></span>

- [<span data-ttu-id="9f81f-114">Создание оператора</span><span class="sxs-lookup"><span data-stu-id="9f81f-114">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="9f81f-115">Оператор AddressOf</span><span class="sxs-lookup"><span data-stu-id="9f81f-115">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="9f81f-116">Делегаты</span><span class="sxs-lookup"><span data-stu-id="9f81f-116">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="9f81f-117">Практическое руководство. Вызов метода делегата</span><span class="sxs-lookup"><span data-stu-id="9f81f-117">How to: Invoke a Delegate Method</span></span>](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
