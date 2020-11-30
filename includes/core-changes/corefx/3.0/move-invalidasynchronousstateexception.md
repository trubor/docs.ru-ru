---
ms.openlocfilehash: 78678b4b352bb063d1521e9aee3492c0cee059b8
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032135"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="9152e-101">Исключение InvalidAsynchronousStateException перенесено в другую сборку</span><span class="sxs-lookup"><span data-stu-id="9152e-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="9152e-102">Класс <xref:System.ComponentModel.InvalidAsynchronousStateException> перемещен.</span><span class="sxs-lookup"><span data-stu-id="9152e-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9152e-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="9152e-103">Change description</span></span>

<span data-ttu-id="9152e-104">В .NET Core 2.2 и более ранних версиях класс <xref:System.ComponentModel.InvalidAsynchronousStateException> находится в сборке *System.ComponentModel.TypeConverter*.</span><span class="sxs-lookup"><span data-stu-id="9152e-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="9152e-105">Начиная с .NET Core 3.0, он находится в сборке *System.ComponentModel.Primitives*.</span><span class="sxs-lookup"><span data-stu-id="9152e-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9152e-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="9152e-106">Version introduced</span></span>

<span data-ttu-id="9152e-107">3.0</span><span class="sxs-lookup"><span data-stu-id="9152e-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9152e-108">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="9152e-108">Recommended action</span></span>

<span data-ttu-id="9152e-109">Это изменение влияет только на приложения, использующие отражение для загрузки <xref:System.ComponentModel.InvalidAsynchronousStateException> путем вызова метода, такого как <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>, или перегрузки <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>, которая предполагает, что тип находится в определенной сборке.</span><span class="sxs-lookup"><span data-stu-id="9152e-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="9152e-110">В этом случае обновите сборку, указанную в вызове метода, в соответствии с новым расположением сборки типа.</span><span class="sxs-lookup"><span data-stu-id="9152e-110">If that is the case, update the assembly referenced in the method call to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="9152e-111">Категория</span><span class="sxs-lookup"><span data-stu-id="9152e-111">Category</span></span>

<span data-ttu-id="9152e-112">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="9152e-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9152e-113">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="9152e-113">Affected APIs</span></span>

<span data-ttu-id="9152e-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="9152e-114">None.</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis

-->
