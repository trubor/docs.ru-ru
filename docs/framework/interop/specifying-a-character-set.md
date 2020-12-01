---
title: Определение кодировки
description: Сведения о том, как указать набор символов, использующий обычную (ANSI) или двухбайтовую (Юникод) кодировку. Можно также настроить автоматический выбор во время выполнения.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
ms.openlocfilehash: 8cc4198d6c13d4705ffc5ce5229cce7a205aec8a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278184"
---
# <a name="specify-a-character-set"></a><span data-ttu-id="2f328-104">Определение кодировки</span><span class="sxs-lookup"><span data-stu-id="2f328-104">Specify a character set</span></span>

<span data-ttu-id="2f328-105">Поле <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> управляет маршалингом строк и определяет, каким образом при вызове неуправляемого кода будут обнаруживаться имена функций в библиотеке DLL.</span><span class="sxs-lookup"><span data-stu-id="2f328-105">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field controls string marshaling and determines how platform invoke finds function names in a DLL.</span></span> <span data-ttu-id="2f328-106">В этом разделе описываются оба механизма.</span><span class="sxs-lookup"><span data-stu-id="2f328-106">This topic describes both behaviors.</span></span>  
  
 <span data-ttu-id="2f328-107">Некоторые API экспортируют две версии функций, которые принимают строковые аргументы: обычные (ANSI) и двухбайтовые (Юникод).</span><span class="sxs-lookup"><span data-stu-id="2f328-107">Some APIs export two versions of functions that take string arguments: narrow (ANSI) and wide (Unicode).</span></span> <span data-ttu-id="2f328-108">Например, API Windows включает следующие имена точек входа для функции **MessageBox**:</span><span class="sxs-lookup"><span data-stu-id="2f328-108">The Windows API, for instance, includes the following entry-point names for the **MessageBox** function:</span></span>  
  
- <span data-ttu-id="2f328-109">**MessageBoxA**</span><span class="sxs-lookup"><span data-stu-id="2f328-109">**MessageBoxA**</span></span>  
  
     <span data-ttu-id="2f328-110">Обеспечивает форматирование однобайтовых символов ANSI и имеет суффикс "A" в имени точки входа.</span><span class="sxs-lookup"><span data-stu-id="2f328-110">Provides 1-byte character ANSI formatting, distinguished by an "A" appended to the entry-point name.</span></span> <span data-ttu-id="2f328-111">При вызове **MessageBoxA** строки всегда маршалируются в формате ANSI.</span><span class="sxs-lookup"><span data-stu-id="2f328-111">Calls to **MessageBoxA** always marshal strings in ANSI format.</span></span>  
  
- <span data-ttu-id="2f328-112">**MessageBoxW**</span><span class="sxs-lookup"><span data-stu-id="2f328-112">**MessageBoxW**</span></span>  
  
     <span data-ttu-id="2f328-113">Обеспечивает форматирование двухбайтовых символов Юникода и имеет суффикс "W" в имени точки входа.</span><span class="sxs-lookup"><span data-stu-id="2f328-113">Provides 2-byte character Unicode formatting, distinguished by a "W" appended to the entry-point name.</span></span> <span data-ttu-id="2f328-114">При вызове **MessageBoxW** строки всегда маршалируются в формате Юникод.</span><span class="sxs-lookup"><span data-stu-id="2f328-114">Calls to **MessageBoxW** always marshal strings in Unicode format.</span></span>  
  
## <a name="string-marshaling-and-name-matching"></a><span data-ttu-id="2f328-115">Маршалинг строк и сопоставление имен</span><span class="sxs-lookup"><span data-stu-id="2f328-115">String Marshaling and Name Matching</span></span>  

 <span data-ttu-id="2f328-116">Поле `CharSet` принимает следующие значения:</span><span class="sxs-lookup"><span data-stu-id="2f328-116">The `CharSet` field accepts the following values:</span></span>  
  
 <span data-ttu-id="2f328-117"><xref:System.Runtime.InteropServices.CharSet.Ansi> (значение по умолчанию)</span><span class="sxs-lookup"><span data-stu-id="2f328-117"><xref:System.Runtime.InteropServices.CharSet.Ansi> (default value)</span></span>  
  
- <span data-ttu-id="2f328-118">Маршалинг строк</span><span class="sxs-lookup"><span data-stu-id="2f328-118">String marshaling</span></span>  
  
     <span data-ttu-id="2f328-119">При вызове неуправляемого кода выполняется маршалинг строк из соответствующего управляемого формата (Юникод) в формат ANSI.</span><span class="sxs-lookup"><span data-stu-id="2f328-119">Platform invoke marshals strings from their managed format (Unicode) to ANSI format.</span></span>  
  
- <span data-ttu-id="2f328-120">Сопоставление имен</span><span class="sxs-lookup"><span data-stu-id="2f328-120">Name matching</span></span>  
  
     <span data-ttu-id="2f328-121">Если поле <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> имеет значение `true` (значение по умолчанию в Visual Basic), при вызове неуправляемого кода осуществляется поиск только указанного имени.</span><span class="sxs-lookup"><span data-stu-id="2f328-121">When the <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="2f328-122">Например, если указать **MessageBox**, при вызове неуправляемого кода будет выполнен поиск **MessageBox**, который может завершиться сбоем из-за невозможности найти точное совпадение.</span><span class="sxs-lookup"><span data-stu-id="2f328-122">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails when it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="2f328-123">Если поле `ExactSpelling` имеет значение `false` (по умолчанию для C++ и C#), при вызове неуправляемого кода выполняется поиск сначала неуправляемого псевдонима (**MessageBox**), а затем, если неуправляемый псевдоним не найден, управляемого имени (**MessageBoxA**).</span><span class="sxs-lookup"><span data-stu-id="2f328-123">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the unmangled alias first (**MessageBox**), then the mangled name (**MessageBoxA**) if the unmangled alias is not found.</span></span> <span data-ttu-id="2f328-124">Обратите внимание, что принципы сопоставления имен ANSI и Юникода различаются.</span><span class="sxs-lookup"><span data-stu-id="2f328-124">Notice that ANSI name-matching behavior differs from Unicode name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Unicode>  
  
- <span data-ttu-id="2f328-125">Маршалинг строк</span><span class="sxs-lookup"><span data-stu-id="2f328-125">String marshaling</span></span>  
  
     <span data-ttu-id="2f328-126">При вызове неуправляемого кода строки копируются из соответствующего управляемого формата (Юникод) в формат Юникода.</span><span class="sxs-lookup"><span data-stu-id="2f328-126">Platform invoke copies strings from their managed format (Unicode) to Unicode format.</span></span>  
  
- <span data-ttu-id="2f328-127">Сопоставление имен</span><span class="sxs-lookup"><span data-stu-id="2f328-127">Name matching</span></span>  
  
     <span data-ttu-id="2f328-128">Если поле `ExactSpelling` имеет значение `true` (значение по умолчанию в Visual Basic), при вызове неуправляемого кода осуществляется поиск только указанного имени.</span><span class="sxs-lookup"><span data-stu-id="2f328-128">When the `ExactSpelling` field is `true`, as it is by default in Visual Basic, platform invoke searches only for the name you specify.</span></span> <span data-ttu-id="2f328-129">Например, если указать **MessageBox**, при вызове неуправляемого кода будет выполнен поиск **MessageBox**, который может завершиться сбоем из-за невозможности найти точное совпадение.</span><span class="sxs-lookup"><span data-stu-id="2f328-129">For example, if you specify **MessageBox**, platform invoke searches for **MessageBox** and fails if it cannot locate the exact spelling.</span></span>  
  
     <span data-ttu-id="2f328-130">Если поле `ExactSpelling` имеет значение `false` (по умолчанию для C++ и C#), при вызове неуправляемого кода выполняется поиск сначала управляемого имени (**MessageBoxW**), а затем, если управляемое имя не найдено, неуправляемого псевдонима (**MessageBox**).</span><span class="sxs-lookup"><span data-stu-id="2f328-130">When the `ExactSpelling` field is `false`, as it is by default in C++ and C#, platform invoke searches for the mangled name first (**MessageBoxW**), then the unmangled alias (**MessageBox**) if the mangled name is not found.</span></span> <span data-ttu-id="2f328-131">Обратите внимание, что принципы сопоставления имен Юникода и ANSI различаются.</span><span class="sxs-lookup"><span data-stu-id="2f328-131">Notice that Unicode name-matching behavior differs from ANSI name-matching behavior.</span></span>  
  
 <xref:System.Runtime.InteropServices.CharSet.Auto>  
  
- <span data-ttu-id="2f328-132">При вызове неуправляемого кода во время выполнения осуществляется выбор между форматами ANSI и Юникода в соответствии с целевой платформой.</span><span class="sxs-lookup"><span data-stu-id="2f328-132">Platform invoke chooses between ANSI and Unicode formats at run time, based on the target platform.</span></span>  
  
## <a name="specify-a-character-set-in-visual-basic"></a><span data-ttu-id="2f328-133">Определение кодировки в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f328-133">Specify a character set in Visual Basic</span></span>

<span data-ttu-id="2f328-134">В Visual Basic можно указать поведение кодировки, добавив ключевое слово `Ansi`, `Unicode` или `Auto` в операторе объявления.</span><span class="sxs-lookup"><span data-stu-id="2f328-134">You can specify character-set behavior in Visual Basic by adding the `Ansi`, `Unicode`, or `Auto` keyword to the declaration statement.</span></span> <span data-ttu-id="2f328-135">Если опустить ключевое слово кодировки, в поле <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> по умолчанию будет задана кодировка ANSI.</span><span class="sxs-lookup"><span data-stu-id="2f328-135">If you omit the character-set keyword, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field defaults to the ANSI character set.</span></span>

<span data-ttu-id="2f328-136">В следующем примере функция **MessageBox** объявляется три раза с разными кодировками.</span><span class="sxs-lookup"><span data-stu-id="2f328-136">The following example declares the **MessageBox** function three times, each time with different character-set behavior.</span></span> <span data-ttu-id="2f328-137">В первом операторе ключевое слово кодировки опущено, в связи с чем по умолчанию устанавливается кодировка ANSI.</span><span class="sxs-lookup"><span data-stu-id="2f328-137">The first statement omits the character-set keyword, so the character set defaults to ANSI.</span></span> <span data-ttu-id="2f328-138">Во втором и третьем операторе кодировка задается явно с использованием ключевого слова.</span><span class="sxs-lookup"><span data-stu-id="2f328-138">The second and third statements explicitly specify a character set with a keyword.</span></span>

```vb
Friend Class NativeMethods
    Friend Declare Function MessageBoxA Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Unicode Function MessageBoxW Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer

    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="specify-a-character-set-in-c-and-c"></a><span data-ttu-id="2f328-139">Определение кодировки в C# и C++</span><span class="sxs-lookup"><span data-stu-id="2f328-139">Specify a character set in C# and C++</span></span>

<span data-ttu-id="2f328-140">Поле <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> определяет базовую кодировку как ANSI или Юникод.</span><span class="sxs-lookup"><span data-stu-id="2f328-140">The <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field identifies the underlying character set as ANSI or Unicode.</span></span> <span data-ttu-id="2f328-141">Кодировка определяет порядок маршалинга строковых аргументов в метод.</span><span class="sxs-lookup"><span data-stu-id="2f328-141">The character set controls how string arguments to a method should be marshaled.</span></span> <span data-ttu-id="2f328-142">Чтобы указать кодировку, используйте одну из следующих форм:</span><span class="sxs-lookup"><span data-stu-id="2f328-142">Use one of the following forms to indicate the character set:</span></span>  
  
```csharp
[DllImport("DllName", CharSet = CharSet.Ansi)]
[DllImport("DllName", CharSet = CharSet.Unicode)]
[DllImport("DllName", CharSet = CharSet.Auto)]
```
  
```cpp
[DllImport("DllName", CharSet = CharSet::Ansi)]
[DllImport("DllName", CharSet = CharSet::Unicode)]
[DllImport("DllName", CharSet = CharSet::Auto)]
```
  
 <span data-ttu-id="2f328-143">В следующем примере показаны три управляемых определения функции **MessageBox** с атрибутами, задающими кодировку.</span><span class="sxs-lookup"><span data-stu-id="2f328-143">The following example shows three managed definitions of the **MessageBox** function attributed to specify a character set.</span></span> <span data-ttu-id="2f328-144">В первом определении соответствующее ключевое слово опущено, в результате чего в поле `CharSet` по умолчанию устанавливается кодировка ANSI.</span><span class="sxs-lookup"><span data-stu-id="2f328-144">In the first definition, by its omission, the `CharSet` field defaults to the ANSI character set.</span></span>  
  
```csharp  
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll")]
    internal static extern int MessageBoxA(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Unicode)]
    internal static extern int MessageBoxW(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);

    [DllImport("user32.dll", CharSet = CharSet.Auto)]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```  
  
```cpp
typedef void* HWND;

// Can use MessageBox or MessageBoxA.
[DllImport("user32")]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Can use MessageBox or MessageBoxW.
[DllImport("user32", CharSet = CharSet::Unicode)]
extern "C" int MessageBoxW(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);

// Must use MessageBox.
[DllImport("user32", CharSet = CharSet::Auto)]
extern "C" int MessageBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a><span data-ttu-id="2f328-145">См. также</span><span class="sxs-lookup"><span data-stu-id="2f328-145">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="2f328-146">Создание прототипов в управляемом коде</span><span class="sxs-lookup"><span data-stu-id="2f328-146">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="2f328-147">Примеры вызовов неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="2f328-147">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="2f328-148">Маршалинг данных при вызове неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="2f328-148">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
