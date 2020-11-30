---
ms.openlocfilehash: 9544b65f31772d0f4cee918528a73171fec4de99
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032052"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="c3ece-101">Изменение значения по умолчанию для UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="c3ece-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="c3ece-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> имеет значение `false` по умолчанию в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c3ece-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="c3ece-103">В .NET Framework его значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="c3ece-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c3ece-104">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="c3ece-104">Change description</span></span>

<span data-ttu-id="c3ece-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> позволяет запускать приложение напрямую, например с помощью кода, как `Process.Start("mspaint.exe")`, запускающего Paint.</span><span class="sxs-lookup"><span data-stu-id="c3ece-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="c3ece-106">Это также позволяет косвенно запускать связанное приложение, если для <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> установлено значение `true`.</span><span class="sxs-lookup"><span data-stu-id="c3ece-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="c3ece-107">В .NET Framework значением по умолчанию для <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> является `true`, что означает, что такой код как `Process.Start("mytextfile.txt")` будет запускать Блокнот, если вы связали файлы *.txt* с этим редактором.</span><span class="sxs-lookup"><span data-stu-id="c3ece-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="c3ece-108">Чтобы предотвратить косвенный запуск приложения на .NET Framework, необходимо явно установить `false` на <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c3ece-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="c3ece-109">В .NET Core значением по умолчанию для <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> является значение `false`.</span><span class="sxs-lookup"><span data-stu-id="c3ece-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="c3ece-110">Это означает, что связанные по умолчанию приложения не запускаются при вызове `Process.Start`.</span><span class="sxs-lookup"><span data-stu-id="c3ece-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="c3ece-111">Это изменение введено в .NET Core для повышения производительности.</span><span class="sxs-lookup"><span data-stu-id="c3ece-111">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="c3ece-112">Как правило, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> используется для непосредственного запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="c3ece-112">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="c3ece-113">Запуск приложения напрямую не требует затрагивания оболочки Windows и влечет за собой соответствующие расходы на производительность.</span><span class="sxs-lookup"><span data-stu-id="c3ece-113">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="c3ece-114">Чтобы ускорить этот вариант по умолчанию, .NET Core изменяет значение по умолчанию <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> на `false`.</span><span class="sxs-lookup"><span data-stu-id="c3ece-114">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="c3ece-115">При необходимости вы можете выбрать более медленный путь.</span><span class="sxs-lookup"><span data-stu-id="c3ece-115">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c3ece-116">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="c3ece-116">Version introduced</span></span>

<span data-ttu-id="c3ece-117">2.1</span><span class="sxs-lookup"><span data-stu-id="c3ece-117">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="c3ece-118">В более ранних версиях .NET Core `UseShellExecute` не был внедрен для Windows.</span><span class="sxs-lookup"><span data-stu-id="c3ece-118">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c3ece-119">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="c3ece-119">Recommended action</span></span>

<span data-ttu-id="c3ece-120">Если приложение полагается на прежнее поведение, вызовите <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType>, указав для параметра <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> значение `true` в объекте <xref:System.Diagnostics.ProcessStartInfo>.</span><span class="sxs-lookup"><span data-stu-id="c3ece-120">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="c3ece-121">Категория</span><span class="sxs-lookup"><span data-stu-id="c3ece-121">Category</span></span>

<span data-ttu-id="c3ece-122">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="c3ece-122">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c3ece-123">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="c3ece-123">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
