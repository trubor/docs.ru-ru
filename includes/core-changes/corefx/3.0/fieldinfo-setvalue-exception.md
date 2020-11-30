---
ms.openlocfilehash: 02c9305a36f47dfaf0b1fa8d19b07cd2d34badae
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032119"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="fdb56-101">FieldInfo.SetValue вызывает исключение для статических полей и полей только для инициализации</span><span class="sxs-lookup"><span data-stu-id="fdb56-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="fdb56-102">Начиная с .NET Core версии 3.0, при попытке задать значение в статическом поле <xref:System.Reflection.FieldAttributes.InitOnly> путем вызова <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>, возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="fdb56-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fdb56-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="fdb56-103">Change description</span></span>

<span data-ttu-id="fdb56-104">В .NET Framework и версиях .NET Core до 3.0 можно было задать значение статического поля, которое являлось константой после его инициализации ([только для чтения в C#](~/docs/csharp/language-reference/keywords/readonly.md)) путем вызова <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="fdb56-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="fdb56-105">Однако установка такого поля таким образом приведет к непредсказуемому поведению в зависимости от целевой платформы и параметров оптимизации.</span><span class="sxs-lookup"><span data-stu-id="fdb56-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="fdb56-106">В .NET Core 3.0 и более поздних версиях, при вызове <xref:System.Reflection.FieldInfo.SetValue%2A> для статического поля <xref:System.Reflection.FieldAttributes.InitOnly> создается исключение <xref:System.FieldAccessException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fdb56-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="fdb56-107">Поле <xref:System.Reflection.FieldAttributes.InitOnly> — это поле, которое можно задать только во время объявления или в конструкторе содержащего класса.</span><span class="sxs-lookup"><span data-stu-id="fdb56-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="fdb56-108">Иными словами, оно остается константой после инициализации.</span><span class="sxs-lookup"><span data-stu-id="fdb56-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fdb56-109">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="fdb56-109">Version introduced</span></span>

<span data-ttu-id="fdb56-110">3.0</span><span class="sxs-lookup"><span data-stu-id="fdb56-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fdb56-111">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="fdb56-111">Recommended action</span></span>

<span data-ttu-id="fdb56-112">Инициализируйте статические поля <xref:System.Reflection.FieldAttributes.InitOnly> в статическом конструкторе.</span><span class="sxs-lookup"><span data-stu-id="fdb56-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="fdb56-113">Это относится как к динамическим, так и к не динамическим типам.</span><span class="sxs-lookup"><span data-stu-id="fdb56-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="fdb56-114">Кроме того, можно удалить атрибут <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> из поля, а затем вызвать <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fdb56-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="fdb56-115">Категория</span><span class="sxs-lookup"><span data-stu-id="fdb56-115">Category</span></span>

<span data-ttu-id="fdb56-116">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="fdb56-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fdb56-117">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="fdb56-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
