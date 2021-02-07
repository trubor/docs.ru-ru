---
description: 'Дополнительные сведения о: BC40041: тип несовместим с <typename> CLS'
title: Тип <typename> несовместим с CLS
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: a1e807dba64f2fce70b0fb39147087d91ca80fbc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675043"
---
# <a name="bc40041-type-typename-is-not-cls-compliant"></a><span data-ttu-id="88c1d-103">BC40041: тип несовместим с \<typename> CLS</span><span class="sxs-lookup"><span data-stu-id="88c1d-103">BC40041: Type \<typename> is not CLS-compliant</span></span>

<span data-ttu-id="88c1d-104">Переменная, свойство или возвращаемое значение функции объявлены с типом данных, который не является CLS-совместимым.</span><span class="sxs-lookup"><span data-stu-id="88c1d-104">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>

 <span data-ttu-id="88c1d-105">Чтобы приложение было совместимо с [независимостьм от языка и Language-Independent компонентами](../../../standard/language-independence-and-language-independent-components.md) (CLS), оно должно использовать только совместимые с CLS типы.</span><span class="sxs-lookup"><span data-stu-id="88c1d-105">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>

 <span data-ttu-id="88c1d-106">Следующие типы данных Visual Basic несовместимы с CLS:</span><span class="sxs-lookup"><span data-stu-id="88c1d-106">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="88c1d-107">Тип данных SByte</span><span class="sxs-lookup"><span data-stu-id="88c1d-107">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="88c1d-108">Тип данных UInteger</span><span class="sxs-lookup"><span data-stu-id="88c1d-108">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="88c1d-109">Тип данных ULong</span><span class="sxs-lookup"><span data-stu-id="88c1d-109">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="88c1d-110">Тип данных UShort</span><span class="sxs-lookup"><span data-stu-id="88c1d-110">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="88c1d-111">**Идентификатор ошибки:** BC40041</span><span class="sxs-lookup"><span data-stu-id="88c1d-111">**Error ID:** BC40041</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="88c1d-112">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="88c1d-112">To correct this error</span></span>

- <span data-ttu-id="88c1d-113">Если приложение должно быть совместимо с CLS, измените тип данных этого элемента на ближайший CLS-совместимый тип.</span><span class="sxs-lookup"><span data-stu-id="88c1d-113">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="88c1d-114">Например, вместо `UInteger` вы можете использовать `Integer` , если вам не нужен диапазон значений, превышающий 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="88c1d-114">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="88c1d-115">Если вам нужен расширенный диапазон, вы можете заменить `UInteger` на `Long`.</span><span class="sxs-lookup"><span data-stu-id="88c1d-115">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="88c1d-116">Если приложение не обязательно должно быть CLS-совместимым, вам не нужно ничего менять.</span><span class="sxs-lookup"><span data-stu-id="88c1d-116">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="88c1d-117">Однако следует помнить о несоответствии.</span><span class="sxs-lookup"><span data-stu-id="88c1d-117">You should be aware of its noncompliance, however.</span></span>
