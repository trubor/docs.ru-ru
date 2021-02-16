---
description: 'Дополнительные сведения: сведения о вызывающем объекте (Visual Basic)'
title: Сведения о вызывающем
ms.date: 07/20/2015
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
ms.openlocfilehash: bcb4f553a9840a76f24825c3c2b7e2e98914abc2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437713"
---
# <a name="caller-information-visual-basic"></a><span data-ttu-id="19aab-103">Caller Information (Visual Basic) (Сведения о вызывающем (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="19aab-103">Caller Information (Visual Basic)</span></span>

<span data-ttu-id="19aab-104">С помощью информационных атрибутов вызывающего объекта можно получить сведения о вызывающем объекте метода.</span><span class="sxs-lookup"><span data-stu-id="19aab-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="19aab-105">Можно получить путь к файлу исходного кода, номер строки в исходном коде и имя вызывающего объекта.</span><span class="sxs-lookup"><span data-stu-id="19aab-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="19aab-106">Эти сведения полезны для трассировки, отладки и создания средств диагностики.</span><span class="sxs-lookup"><span data-stu-id="19aab-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="19aab-107">Для получения этих сведений используются атрибуты, которые применяются к необязательным параметрам, каждый из которых имеет значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="19aab-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="19aab-108">В следующей таблице перечислены информационные атрибуты вызывающего объекта, которые определены в пространстве имен <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="19aab-108">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="19aab-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="19aab-109">Attribute</span></span>|<span data-ttu-id="19aab-110">Описание</span><span class="sxs-lookup"><span data-stu-id="19aab-110">Description</span></span>|<span data-ttu-id="19aab-111">Type</span><span class="sxs-lookup"><span data-stu-id="19aab-111">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="19aab-112">Полный путь исходного файла, содержащего вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="19aab-112">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="19aab-113">Это путь к файлу во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="19aab-113">This is the file path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="19aab-114">Номер строки в исходном файле, в которой вызывается метод.</span><span class="sxs-lookup"><span data-stu-id="19aab-114">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="19aab-115">Имя свойства или метода вызывающего объекта.</span><span class="sxs-lookup"><span data-stu-id="19aab-115">Method or property name of the caller.</span></span> <span data-ttu-id="19aab-116">См. подраздел [Имена членов](#MEMBERNAMES) ниже.</span><span class="sxs-lookup"><span data-stu-id="19aab-116">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="19aab-117">Пример</span><span class="sxs-lookup"><span data-stu-id="19aab-117">Example</span></span>  

 <span data-ttu-id="19aab-118">В следующем примере показано, как использовать информационные атрибуты вызывающего объекта.</span><span class="sxs-lookup"><span data-stu-id="19aab-118">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="19aab-119">При каждом вызове метода `TraceMessage` сведения о вызывающем объекте подставляются в качестве аргументов необязательных параметров.</span><span class="sxs-lookup"><span data-stu-id="19aab-119">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a><span data-ttu-id="19aab-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="19aab-120">Remarks</span></span>  

 <span data-ttu-id="19aab-121">Для каждого необязательного параметра необходимо указать явное значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="19aab-121">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="19aab-122">Нельзя применять информационные атрибуты вызывающего объекта к параметрам, которые не были указаны как необязательные.</span><span class="sxs-lookup"><span data-stu-id="19aab-122">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="19aab-123">Информационные атрибуты вызывающего объекта не делают параметр необязательным.</span><span class="sxs-lookup"><span data-stu-id="19aab-123">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="19aab-124">Вместо этого они влияют на значение по умолчанию, которое передается, если аргумент был опущен.</span><span class="sxs-lookup"><span data-stu-id="19aab-124">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="19aab-125">Информационные значения вызывающего объекта передаются как литералы в IL во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="19aab-125">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="19aab-126">В отличие от результатов свойства <xref:System.Exception.StackTrace%2A> для исключений, результаты не затрагиваются запутыванием кода.</span><span class="sxs-lookup"><span data-stu-id="19aab-126">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="19aab-127">Можно явно передать необязательные аргументы, чтобы управлять сведениями о вызывающем объекте или скрывать сведения о вызывающем объекте.</span><span class="sxs-lookup"><span data-stu-id="19aab-127">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
### <a name="member-names"></a><a name="MEMBERNAMES"></a> <span data-ttu-id="19aab-128">Имена элементов</span><span class="sxs-lookup"><span data-stu-id="19aab-128">Member Names</span></span>  

 <span data-ttu-id="19aab-129">Можно использовать атрибут `CallerMemberName`, чтобы не указывать имя члена в виде аргумента `String` вызываемому методу.</span><span class="sxs-lookup"><span data-stu-id="19aab-129">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="19aab-130">Этот прием позволяет избежать проблемы, заключающейся в том, что **операция рефакторинга и переименования** не изменяет значений `String`.</span><span class="sxs-lookup"><span data-stu-id="19aab-130">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="19aab-131">Это особенно полезно при выполнении следующих задач:</span><span class="sxs-lookup"><span data-stu-id="19aab-131">This benefit is especially useful for the following tasks:</span></span>  
  
- <span data-ttu-id="19aab-132">Использование процедур трассировки и диагностики.</span><span class="sxs-lookup"><span data-stu-id="19aab-132">Using tracing and diagnostic routines.</span></span>  
  
- <span data-ttu-id="19aab-133">Реализация интерфейса <xref:System.ComponentModel.INotifyPropertyChanged> при привязке данных.</span><span class="sxs-lookup"><span data-stu-id="19aab-133">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="19aab-134">Этот интерфейс позволяет свойству объекта уведомлять связанный элемент управления об изменении свойства, чтобы элемент управления мог отображать обновленные сведения.</span><span class="sxs-lookup"><span data-stu-id="19aab-134">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="19aab-135">Если атрибут `CallerMemberName` не используется, необходимо указать имя свойства как литерал.</span><span class="sxs-lookup"><span data-stu-id="19aab-135">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="19aab-136">В следующей таблице представлены имена членов, возвращаемых при использовании атрибута `CallerMemberName`.</span><span class="sxs-lookup"><span data-stu-id="19aab-136">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="19aab-137">Фрагмент кода, в пределах которого происходит вызов</span><span class="sxs-lookup"><span data-stu-id="19aab-137">Calls occurs within</span></span>|<span data-ttu-id="19aab-138">Результат имени члена</span><span class="sxs-lookup"><span data-stu-id="19aab-138">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="19aab-139">Метод, свойство или событие</span><span class="sxs-lookup"><span data-stu-id="19aab-139">Method, property, or event</span></span>|<span data-ttu-id="19aab-140">Имя метода, свойства или события, из которого происходил вызов.</span><span class="sxs-lookup"><span data-stu-id="19aab-140">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="19aab-141">Конструктор</span><span class="sxs-lookup"><span data-stu-id="19aab-141">Constructor</span></span>|<span data-ttu-id="19aab-142">Строка ".ctor"</span><span class="sxs-lookup"><span data-stu-id="19aab-142">The string ".ctor"</span></span>|  
|<span data-ttu-id="19aab-143">Статический конструктор</span><span class="sxs-lookup"><span data-stu-id="19aab-143">Static constructor</span></span>|<span data-ttu-id="19aab-144">Строка ".cctor"</span><span class="sxs-lookup"><span data-stu-id="19aab-144">The string ".cctor"</span></span>|  
|<span data-ttu-id="19aab-145">Деструктор</span><span class="sxs-lookup"><span data-stu-id="19aab-145">Destructor</span></span>|<span data-ttu-id="19aab-146">Строка "Finalize"</span><span class="sxs-lookup"><span data-stu-id="19aab-146">The string "Finalize"</span></span>|  
|<span data-ttu-id="19aab-147">Определяемые пользователем операторы и преобразования</span><span class="sxs-lookup"><span data-stu-id="19aab-147">User-defined operators or conversions</span></span>|<span data-ttu-id="19aab-148">Созданное имя члена, например, "op_Addition".</span><span class="sxs-lookup"><span data-stu-id="19aab-148">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="19aab-149">Конструктора атрибута</span><span class="sxs-lookup"><span data-stu-id="19aab-149">Attribute constructor</span></span>|<span data-ttu-id="19aab-150">Имя члена, к которому применяется атрибут.</span><span class="sxs-lookup"><span data-stu-id="19aab-150">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="19aab-151">Если атрибут — любой элемент внутри члена (например, параметр, возвращаемое значение или параметр универсального типа), то результат — имя члена, который связан с этим элементом.</span><span class="sxs-lookup"><span data-stu-id="19aab-151">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="19aab-152">Нет содержащего члена (например, уровень сборки или атрибуты, примененные к типам)</span><span class="sxs-lookup"><span data-stu-id="19aab-152">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="19aab-153">Значение необязательного параметра по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="19aab-153">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19aab-154">См. также</span><span class="sxs-lookup"><span data-stu-id="19aab-154">See also</span></span>

- [<span data-ttu-id="19aab-155">Атрибуты (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19aab-155">Attributes (Visual Basic)</span></span>](../../language-reference/attributes.md)
- <span data-ttu-id="19aab-156">[Common Attributes (Visual Basic)](attributes/common-attributes.md) (Распространенные атрибуты (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="19aab-156">[Common Attributes (Visual Basic)](attributes/common-attributes.md)</span></span>
- [<span data-ttu-id="19aab-157">Необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="19aab-157">Optional Parameters</span></span>](../language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="19aab-158">Основные понятия программирования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19aab-158">Programming Concepts (Visual Basic)</span></span>](index.md)
