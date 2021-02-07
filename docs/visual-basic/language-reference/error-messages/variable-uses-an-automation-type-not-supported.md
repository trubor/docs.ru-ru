---
description: 'Дополнительные сведения: переменная использует тип автоматизации, который не поддерживается в Visual Basic'
title: Переменная использует неподдерживаемый тип автоматизации
ms.date: 07/20/2015
f1_keywords:
- vbrID458
ms.assetid: bde4f4da-493b-452c-b6e4-1d370edba4cd
ms.openlocfilehash: 9aa8f8a2a49e54c547dc47d38305d40f855b1815
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666151"
---
# <a name="variable-uses-an-automation-type-not-supported-in-visual-basic"></a><span data-ttu-id="236cc-103">Переменная использует тип автоматизации, не поддерживаемый в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="236cc-103">Variable uses an Automation type not supported in Visual Basic</span></span>

<span data-ttu-id="236cc-104">Предпринята попытка использовать переменную, определенную в библиотеке типов или библиотеке объектов, которая имеет тип данных, не поддерживаемый Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="236cc-104">You tried to use a variable defined in a type library or object library that has a data type not supported by Visual Basic.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="236cc-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="236cc-105">To correct this error</span></span>

- <span data-ttu-id="236cc-106">Используйте переменную типа, распознаваемый Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="236cc-106">Use a variable of a type recognized by Visual Basic.</span></span>

     <span data-ttu-id="236cc-107">-или-</span><span class="sxs-lookup"><span data-stu-id="236cc-107">-or-</span></span>

- <span data-ttu-id="236cc-108">Если эта ошибка возникает при использовании `FileGet` или `FileGetObject` , убедитесь, что файл, который вы пытаетесь использовать, записан в с помощью `FilePut` или `FilePutObject` .</span><span class="sxs-lookup"><span data-stu-id="236cc-108">If you encounter this error while using `FileGet` or `FileGetObject`, make sure the file you are trying to use was written to with `FilePut` or `FilePutObject`.</span></span>

## <a name="see-also"></a><span data-ttu-id="236cc-109">См. также</span><span class="sxs-lookup"><span data-stu-id="236cc-109">See also</span></span>

- [<span data-ttu-id="236cc-110">Типы данных</span><span class="sxs-lookup"><span data-stu-id="236cc-110">Data Types</span></span>](../data-types/index.md)
