---
title: Пример MsgBox
description: Пример передачи строковых типов по значениям в качестве параметров ввода с помощью MsgBox. Здесь демонстрируется использование полей EntryPoint, CharSet и ExactSpelling в .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
ms.openlocfilehash: 024ed612115ce73646596651fe454238418446db
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242023"
---
# <a name="msgbox-sample"></a><span data-ttu-id="85935-104">Пример MsgBox</span><span class="sxs-lookup"><span data-stu-id="85935-104">MsgBox Sample</span></span>

<span data-ttu-id="85935-105">В этом примере демонстрируется, как передавать строковые типы по значению в качестве параметров ввода и когда следует использовать поля <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> и <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>.</span><span class="sxs-lookup"><span data-stu-id="85935-105">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="85935-106">В примере используются следующие неуправляемые функции, показанные с исходными объявлениями:</span><span class="sxs-lookup"><span data-stu-id="85935-106">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="85935-107">**MessageBox** экспортируется из User32.dll.</span><span class="sxs-lookup"><span data-stu-id="85935-107">**MessageBox** exported from User32.dll.</span></span>  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,
       UINT uType);  
    ```  
  
 <span data-ttu-id="85935-108">В этом примере класс `NativeMethods` содержит управляемый прототип для каждой неуправляемой функции, вызываемой классом `MsgBoxSample`.</span><span class="sxs-lookup"><span data-stu-id="85935-108">In this sample, the `NativeMethods` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="85935-109">Управляемые прототипы методов `MsgBox`, `MsgBox2` и `MsgBox3` содержат разные объявления для одной и той же неуправляемой функции.</span><span class="sxs-lookup"><span data-stu-id="85935-109">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="85935-110">Объявление `MsgBox2` приводит к выводу некорректных данных в окне сообщения, поскольку символьный тип, указанный как ANSI, не соответствует точке входа `MessageBoxW`, которая определяет функцию Юникода.</span><span class="sxs-lookup"><span data-stu-id="85935-110">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="85935-111">Объявление `MsgBox3` приводит к несоответствию между полями **EntryPoint**, **CharSet** и **ExactSpelling**.</span><span class="sxs-lookup"><span data-stu-id="85935-111">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="85935-112">При вызове `MsgBox3` возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="85935-112">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="85935-113">Дополнительные сведения об именовании строк и маршалинге имен см. в разделе [Определение кодировки](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="85935-113">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="85935-114">Объявление прототипов</span><span class="sxs-lookup"><span data-stu-id="85935-114">Declaring Prototypes</span></span>  

 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="85935-115">Вызов функций</span><span class="sxs-lookup"><span data-stu-id="85935-115">Calling Functions</span></span>  

 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="85935-116">См. также</span><span class="sxs-lookup"><span data-stu-id="85935-116">See also</span></span>

- [<span data-ttu-id="85935-117">Mаршалинг строк</span><span class="sxs-lookup"><span data-stu-id="85935-117">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="85935-118">Маршалинг по умолчанию для строк</span><span class="sxs-lookup"><span data-stu-id="85935-118">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
- [<span data-ttu-id="85935-119">Создание прототипов в управляемом коде</span><span class="sxs-lookup"><span data-stu-id="85935-119">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="85935-120">Определение кодировки</span><span class="sxs-lookup"><span data-stu-id="85935-120">Specifying a Character Set</span></span>](specifying-a-character-set.md)
