---
description: 'Дополнительные сведения о: BC42104: переменная " <variablename> " используется до того, как ей было присвоено значение'
title: Переменная <variablename> используется до того, как ей присвоено значение
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 501c3e3971c5ca0ebdba6981134f5029b77d0075
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701499"
---
# <a name="bc42104-variable-variablename-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="142c6-103">BC42104: переменная " \<variablename> " используется до того, как ей было присвоено значение</span><span class="sxs-lookup"><span data-stu-id="142c6-103">BC42104: Variable '\<variablename>' is used before it has been assigned a value</span></span>

<span data-ttu-id="142c6-104">Переменная " \<variablename> " используется до того, как ей было присвоено значение.</span><span class="sxs-lookup"><span data-stu-id="142c6-104">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="142c6-105">Во время выполнения может возникнуть исключение "пустая ссылка".</span><span class="sxs-lookup"><span data-stu-id="142c6-105">A null reference exception could result at run time.</span></span>

 <span data-ttu-id="142c6-106">Приложение имеет по крайней мере один возможный путь в коде, который считывает переменную, прежде чем ей будет присвоено значение.</span><span class="sxs-lookup"><span data-stu-id="142c6-106">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>

 <span data-ttu-id="142c6-107">Если переменной никогда не назначалось значение, она содержит значение по умолчанию для своего типа данных.</span><span class="sxs-lookup"><span data-stu-id="142c6-107">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="142c6-108">Для ссылочного типа данных значение по умолчанию — [Nothing](../nothing.md).</span><span class="sxs-lookup"><span data-stu-id="142c6-108">For a reference data type, that default value is [Nothing](../nothing.md).</span></span> <span data-ttu-id="142c6-109">Чтение переменной ссылки, которая имеет значение `Nothing` , в некоторых случаях может привести к исключению <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="142c6-109">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>

 <span data-ttu-id="142c6-110">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="142c6-110">By default, this message is a warning.</span></span> <span data-ttu-id="142c6-111">Дополнительные сведения о скрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="142c6-111">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="142c6-112">**Идентификатор ошибки:** BC42104</span><span class="sxs-lookup"><span data-stu-id="142c6-112">**Error ID:** BC42104</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="142c6-113">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="142c6-113">To correct this error</span></span>

- <span data-ttu-id="142c6-114">Проверьте логику потока управления и убедитесь, что переменная имеет допустимое значение, прежде чем управление передается в любую инструкцию, которая ее считывает.</span><span class="sxs-lookup"><span data-stu-id="142c6-114">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>

- <span data-ttu-id="142c6-115">Один из способов гарантировать, что переменная всегда имеет допустимое значение, — инициализировать ее как часть объявления.</span><span class="sxs-lookup"><span data-stu-id="142c6-115">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="142c6-116">См. раздел "Инициализация" в [операторе Dim](../statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="142c6-116">See "Initialization" in [Dim Statement](../statements/dim-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="142c6-117">См. также</span><span class="sxs-lookup"><span data-stu-id="142c6-117">See also</span></span>

- [<span data-ttu-id="142c6-118">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="142c6-118">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="142c6-119">Объявление переменной</span><span class="sxs-lookup"><span data-stu-id="142c6-119">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="142c6-120">Устранение неполадок, связанных с переменными</span><span class="sxs-lookup"><span data-stu-id="142c6-120">Troubleshooting Variables</span></span>](../../programming-guide/language-features/variables/troubleshooting-variables.md)
