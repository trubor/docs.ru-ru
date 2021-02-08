---
description: 'Дополнительные сведения об инструкции: Error'
title: Оператор Error
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 6c152e9e4fb4fa3a937042761c7d776b337f4fef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769147"
---
# <a name="error-statement"></a><span data-ttu-id="e41bc-103">Оператор Error</span><span class="sxs-lookup"><span data-stu-id="e41bc-103">Error Statement</span></span>

<span data-ttu-id="e41bc-104">Имитирует возникновение ошибки.</span><span class="sxs-lookup"><span data-stu-id="e41bc-104">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e41bc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e41bc-105">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="e41bc-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="e41bc-106">Parts</span></span>  

 `errornumber`  
 <span data-ttu-id="e41bc-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="e41bc-107">Required.</span></span> <span data-ttu-id="e41bc-108">Может быть любым допустимым номером ошибки.</span><span class="sxs-lookup"><span data-stu-id="e41bc-108">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e41bc-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="e41bc-109">Remarks</span></span>  

 <span data-ttu-id="e41bc-110">Эта `Error` инструкция поддерживается для обеспечения обратной совместимости.</span><span class="sxs-lookup"><span data-stu-id="e41bc-110">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="e41bc-111">В новом коде, особенно при создании объектов, используйте `Err` `Raise` метод объекта для создания ошибок времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="e41bc-111">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="e41bc-112">Если `errornumber` определено, `Error` инструкция вызывает обработчик ошибок после того, как свойства `Err` объекта присвоены следующие значения по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="e41bc-112">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="e41bc-113">Свойство</span><span class="sxs-lookup"><span data-stu-id="e41bc-113">Property</span></span>|<span data-ttu-id="e41bc-114">Значение</span><span class="sxs-lookup"><span data-stu-id="e41bc-114">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="e41bc-115">Значение, указанное в качестве аргумента `Error` инструкции.</span><span class="sxs-lookup"><span data-stu-id="e41bc-115">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="e41bc-116">Может быть любым допустимым номером ошибки.</span><span class="sxs-lookup"><span data-stu-id="e41bc-116">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="e41bc-117">Имя текущего проекта Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e41bc-117">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="e41bc-118">Строковое выражение, соответствующее возвращаемому значению `Error` функции для указанного объекта `Number` , если эта строка существует.</span><span class="sxs-lookup"><span data-stu-id="e41bc-118">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="e41bc-119">Если строка не существует, `Description` содержит строку нулевой длины ("").</span><span class="sxs-lookup"><span data-stu-id="e41bc-119">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="e41bc-120">Полный диск, путь и имя файла подходящего файла справки Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e41bc-120">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="e41bc-121">Соответствующий идентификатор контекста файла справки Visual Basic для ошибки, соответствующей `Number` свойству.</span><span class="sxs-lookup"><span data-stu-id="e41bc-121">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="e41bc-122">Ноль.</span><span class="sxs-lookup"><span data-stu-id="e41bc-122">Zero.</span></span>|  
  
 <span data-ttu-id="e41bc-123">Если обработчик ошибок не существует или не включен, сообщение об ошибке создается и отображается в `Err` свойствах объекта.</span><span class="sxs-lookup"><span data-stu-id="e41bc-123">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e41bc-124">Некоторые приложения Visual Basic узла не могут создавать объекты.</span><span class="sxs-lookup"><span data-stu-id="e41bc-124">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="e41bc-125">Чтобы определить, может ли он создавать классы и объекты, см. документацию по ведущему приложению.</span><span class="sxs-lookup"><span data-stu-id="e41bc-125">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e41bc-126">Пример</span><span class="sxs-lookup"><span data-stu-id="e41bc-126">Example</span></span>  

 <span data-ttu-id="e41bc-127">В этом примере используется `Error` оператор для создания номера ошибки 11.</span><span class="sxs-lookup"><span data-stu-id="e41bc-127">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="e41bc-128">Требования</span><span class="sxs-lookup"><span data-stu-id="e41bc-128">Requirements</span></span>  

 <span data-ttu-id="e41bc-129">**Пространство имен:** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="e41bc-129">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="e41bc-130">**Сборка:** Библиотека времени выполнения Visual Basic (в Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="e41bc-130">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e41bc-131">См. также</span><span class="sxs-lookup"><span data-stu-id="e41bc-131">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="e41bc-132">Оператор On Error</span><span class="sxs-lookup"><span data-stu-id="e41bc-132">On Error Statement</span></span>](on-error-statement.md)
- [<span data-ttu-id="e41bc-133">Оператор Resume</span><span class="sxs-lookup"><span data-stu-id="e41bc-133">Resume Statement</span></span>](resume-statement.md)
- [<span data-ttu-id="e41bc-134">Сообщения об ошибках</span><span class="sxs-lookup"><span data-stu-id="e41bc-134">Error Messages</span></span>](../error-messages/index.md)
