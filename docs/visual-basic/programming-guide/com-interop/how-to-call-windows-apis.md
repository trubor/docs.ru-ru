---
description: Дополнительные сведения см. в статье как вызвать API Windows (Visual Basic).
title: Практическое руководство. Вызов API Windows
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: ec25df3715b1f8a4612c1575b5f7192d0a133c4b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464915"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="2b472-103">Практическое руководство. Вызов Windows API (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b472-103">How to: Call Windows APIs (Visual Basic)</span></span>

<span data-ttu-id="2b472-104">В этом примере определяется и вызывается `MessageBox` функция в user32.dll, а затем в нее передается строка.</span><span class="sxs-lookup"><span data-stu-id="2b472-104">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b472-105">Пример</span><span class="sxs-lookup"><span data-stu-id="2b472-105">Example</span></span>  

 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="2b472-106">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="2b472-106">Compile the code</span></span>  

 <span data-ttu-id="2b472-107">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="2b472-107">This example requires:</span></span>  
  
- <span data-ttu-id="2b472-108">ссылка на пространство имен <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="2b472-108">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2b472-109">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="2b472-109">Robust Programming</span></span>  

 <span data-ttu-id="2b472-110">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="2b472-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="2b472-111">Метод не является статическим, является абстрактным или был определен ранее.</span><span class="sxs-lookup"><span data-stu-id="2b472-111">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="2b472-112">Родительский тип является интерфейсом, или длина *имени* или *dllname* равна нулю.</span><span class="sxs-lookup"><span data-stu-id="2b472-112">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="2b472-113">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="2b472-113">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="2b472-114">*Имя* или параметр *dllname* имеет значение `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="2b472-114">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="2b472-115">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="2b472-115">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="2b472-116">Содержащий тип был создан ранее с помощью `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="2b472-116">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="2b472-117">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="2b472-117">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b472-118">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="2b472-118">See also</span></span>

- [<span data-ttu-id="2b472-119">Подробный обзор вызова неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="2b472-119">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="2b472-120">Примеры вызовов неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="2b472-120">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="2b472-121">Использование неуправляемых функций DLL</span><span class="sxs-lookup"><span data-stu-id="2b472-121">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="2b472-122">[Определение метода с помощью порождаемого отражения](/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2b472-122">[Defining a Method with Reflection Emit](/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="2b472-123">Пошаговое руководство. Вызов API Windows</span><span class="sxs-lookup"><span data-stu-id="2b472-123">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="2b472-124">COM-взаимодействие</span><span class="sxs-lookup"><span data-stu-id="2b472-124">COM Interop</span></span>](index.md)
