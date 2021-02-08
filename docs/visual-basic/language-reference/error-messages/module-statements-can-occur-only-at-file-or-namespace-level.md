---
description: 'Дополнительные сведения о: BC30617: операторы "Module" могут использоваться только на уровне файла или пространства имен'
title: Операторы Module могут присутствовать только на уровне файлов или пространств имен
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: f5c3ea0cd1c08fb0243043ae50e707e2c59b00f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795785"
---
# <a name="bc30617-module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="62a3a-103">BC30617: операторы "Module" могут использоваться только на уровне файла или пространства имен</span><span class="sxs-lookup"><span data-stu-id="62a3a-103">BC30617: 'Module' statements can occur only at file or namespace level</span></span>

<span data-ttu-id="62a3a-104">`Module` операторы должны находиться в верхней части исходного файла сразу после `Option` и `Imports` инструкций, глобальных атрибутов и объявлений пространств имен, но перед всеми остальными объявлениями.</span><span class="sxs-lookup"><span data-stu-id="62a3a-104">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>

 <span data-ttu-id="62a3a-105">**Идентификатор ошибки:** BC30617</span><span class="sxs-lookup"><span data-stu-id="62a3a-105">**Error ID:** BC30617</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="62a3a-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="62a3a-106">To correct this error</span></span>

- <span data-ttu-id="62a3a-107">Переместите оператор `Module` в начало объявления пространства имен или исходного файла.</span><span class="sxs-lookup"><span data-stu-id="62a3a-107">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>

## <a name="see-also"></a><span data-ttu-id="62a3a-108">См. также</span><span class="sxs-lookup"><span data-stu-id="62a3a-108">See also</span></span>

- [<span data-ttu-id="62a3a-109">Оператор Module</span><span class="sxs-lookup"><span data-stu-id="62a3a-109">Module Statement</span></span>](../statements/module-statement.md)
