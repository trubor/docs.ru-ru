---
ms.openlocfilehash: dcc64fe651b219ff1416c0afcdb4c6d275160f4b
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2021
ms.locfileid: "97911546"
---
### <a name="change-in-default-value-of-useshellexecute"></a><span data-ttu-id="fbda4-101">Изменение значения по умолчанию для UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="fbda4-101">Change in default value of UseShellExecute</span></span>

<span data-ttu-id="fbda4-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> имеет значение `false` по умолчанию в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fbda4-102"><xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> has a default value of `false` on .NET Core.</span></span> <span data-ttu-id="fbda4-103">В .NET Framework его значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="fbda4-103">On .NET Framework, its default value is `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fbda4-104">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="fbda4-104">Change description</span></span>

<span data-ttu-id="fbda4-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> позволяет запускать приложение напрямую, например с помощью кода, как `Process.Start("mspaint.exe")`, запускающего Paint.</span><span class="sxs-lookup"><span data-stu-id="fbda4-105"><xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> lets you launch an application directly, for example, with code such as `Process.Start("mspaint.exe")` that launches Paint.</span></span> <span data-ttu-id="fbda4-106">Это также позволяет косвенно запускать связанное приложение, если для <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> установлено значение `true`.</span><span class="sxs-lookup"><span data-stu-id="fbda4-106">It also lets you indirectly launch an associated application if <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is set to `true`.</span></span> <span data-ttu-id="fbda4-107">В .NET Framework значением по умолчанию для <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> является `true`, что означает, что такой код как `Process.Start("mytextfile.txt")` будет запускать Блокнот, если вы связали файлы *.txt* с этим редактором.</span><span class="sxs-lookup"><span data-stu-id="fbda4-107">On .NET Framework, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`, meaning that code such as `Process.Start("mytextfile.txt")` would launch Notepad, if you've associated *.txt* files with that editor.</span></span> <span data-ttu-id="fbda4-108">Чтобы предотвратить косвенный запуск приложения на .NET Framework, необходимо явно установить `false` на <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fbda4-108">To prevent indirectly launching an app on .NET Framework, you must explicitly set <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="fbda4-109">В .NET Core значением по умолчанию для <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> является значение `false`.</span><span class="sxs-lookup"><span data-stu-id="fbda4-109">On .NET Core, the default value for <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `false`.</span></span> <span data-ttu-id="fbda4-110">Это означает, что связанные по умолчанию приложения не запускаются при вызове `Process.Start`.</span><span class="sxs-lookup"><span data-stu-id="fbda4-110">This means that, by default, associated applications are not launched when you call `Process.Start`.</span></span>

<span data-ttu-id="fbda4-111">Следующие свойства <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType> работают только в том случае, если <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> имеет значение `true`:</span><span class="sxs-lookup"><span data-stu-id="fbda4-111">The following properties on <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType> are only functional when <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> is `true`:</span></span>

- <xref:System.Diagnostics.ProcessStartInfo.CreateNoWindow?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.ErrorDialog?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo.Verb?displayProperty=nameWithType>
- <span data-ttu-id="fbda4-112"><xref:System.Diagnostics.ProcessStartInfo.WindowStyle?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fbda4-112"><xref:System.Diagnostics.ProcessStartInfo.WindowStyle?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="fbda4-113">Это изменение введено в .NET Core для повышения производительности.</span><span class="sxs-lookup"><span data-stu-id="fbda4-113">This change was introduced in .NET Core for performance reasons.</span></span> <span data-ttu-id="fbda4-114">Как правило, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> используется для непосредственного запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="fbda4-114">Typically, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> is used to launch an application directly.</span></span> <span data-ttu-id="fbda4-115">Запуск приложения напрямую не требует затрагивания оболочки Windows и влечет за собой соответствующие расходы на производительность.</span><span class="sxs-lookup"><span data-stu-id="fbda4-115">Launching an app directly does not need to involve the Windows shell and incur the associated performance cost.</span></span> <span data-ttu-id="fbda4-116">Чтобы ускорить этот вариант по умолчанию, .NET Core изменяет значение по умолчанию <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> на `false`.</span><span class="sxs-lookup"><span data-stu-id="fbda4-116">To make this default case faster, .NET Core changes the default value of <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> to `false`.</span></span> <span data-ttu-id="fbda4-117">При необходимости вы можете выбрать более медленный путь.</span><span class="sxs-lookup"><span data-stu-id="fbda4-117">You can opt in to the slower path if you need it.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fbda4-118">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="fbda4-118">Version introduced</span></span>

<span data-ttu-id="fbda4-119">2.1</span><span class="sxs-lookup"><span data-stu-id="fbda4-119">2.1</span></span>

> [!NOTE]
> <span data-ttu-id="fbda4-120">В более ранних версиях .NET Core `UseShellExecute` не был внедрен для Windows.</span><span class="sxs-lookup"><span data-stu-id="fbda4-120">In earlier versions of .NET Core, `UseShellExecute` was not implemented for Windows.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fbda4-121">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="fbda4-121">Recommended action</span></span>

<span data-ttu-id="fbda4-122">Если приложение полагается на прежнее поведение, вызовите <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType>, указав для параметра <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> значение `true` в объекте <xref:System.Diagnostics.ProcessStartInfo>.</span><span class="sxs-lookup"><span data-stu-id="fbda4-122">If your app relies on the old behavior, call <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> with <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> set to `true` on the <xref:System.Diagnostics.ProcessStartInfo> object.</span></span>

#### <a name="category"></a><span data-ttu-id="fbda4-123">Категория</span><span class="sxs-lookup"><span data-stu-id="fbda4-123">Category</span></span>

<span data-ttu-id="fbda4-124">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="fbda4-124">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fbda4-125">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="fbda4-125">Affected APIs</span></span>

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
