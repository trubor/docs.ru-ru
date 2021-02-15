---
description: 'Дополнительные сведения о: BC30712: не удается загрузить сведения для класса " <classname> "'
title: Не удается выполнить загрузку сведений для класса <classname>
ms.date: 07/20/2015
f1_keywords:
- vbc30712
- bc30712
helpviewer_keywords:
- BC30712
ms.assetid: c7ffbd6d-05c6-4261-b44b-1bcd521bb350
ms.openlocfilehash: 5325afabfd267f15f0d0497be6ef03c8f5c828c0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480535"
---
# <a name="bc30712-unable-to-load-information-for-class-classname"></a><span data-ttu-id="534ac-103">BC30712: не удалось загрузить сведения для класса " \<classname> "</span><span class="sxs-lookup"><span data-stu-id="534ac-103">BC30712: Unable to load information for class '\<classname>'</span></span>

<span data-ttu-id="534ac-104">Была сделана ссылка на класс, который недоступен.</span><span class="sxs-lookup"><span data-stu-id="534ac-104">A reference was made to a class that is not available.</span></span>

 <span data-ttu-id="534ac-105">**Идентификатор ошибки:** BC30712</span><span class="sxs-lookup"><span data-stu-id="534ac-105">**Error ID:** BC30712</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="534ac-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="534ac-106">To correct this error</span></span>

1. <span data-ttu-id="534ac-107">Убедитесь, что класс определен и имя указано правильно.</span><span class="sxs-lookup"><span data-stu-id="534ac-107">Verify that the class is defined and that you spelled the name correctly.</span></span>

2. <span data-ttu-id="534ac-108">Попробуйте обратиться к одному из членов, объявленных в модуле.</span><span class="sxs-lookup"><span data-stu-id="534ac-108">Try accessing one of the members declared in the module.</span></span> <span data-ttu-id="534ac-109">В некоторых случаях среда отладки не может найти члены, потому что модули, в которых они объявлены, еще не были загружены.</span><span class="sxs-lookup"><span data-stu-id="534ac-109">In some cases, the debugging environment cannot locate members because the modules where they are declared have not been loaded yet.</span></span>

## <a name="see-also"></a><span data-ttu-id="534ac-110">См. также</span><span class="sxs-lookup"><span data-stu-id="534ac-110">See also</span></span>

- [<span data-ttu-id="534ac-111">Отладка в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="534ac-111">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
