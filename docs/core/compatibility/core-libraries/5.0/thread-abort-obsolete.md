---
title: Критическое изменение. Thread.Abort устарел
description: Сведения о критическом изменении .NET 5.0 в основных библиотеках .NET, в которых устарел API Thread.Abort.
ms.date: 11/01/2020
ms.openlocfilehash: 6d7dfce8fda393bfd88c9b4cf0c59d53942cee25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759637"
---
# <a name="threadabort-is-obsolete"></a><span data-ttu-id="e1452-103">Thread.Abort устарел</span><span class="sxs-lookup"><span data-stu-id="e1452-103">Thread.Abort is obsolete</span></span>

<span data-ttu-id="e1452-104">API <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> являются устаревшими.</span><span class="sxs-lookup"><span data-stu-id="e1452-104">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> APIs are obsolete.</span></span> <span data-ttu-id="e1452-105">В проектах, предназначенных для .NET 5.0 или более поздней версии, можно столкнуться с предупреждениями во время компиляции `SYSLIB0006` при вызове этих методов.</span><span class="sxs-lookup"><span data-stu-id="e1452-105">Projects that target .NET 5.0 or a later version will encounter compile-time warning `SYSLIB0006` if these methods are called.</span></span>

## <a name="change-description"></a><span data-ttu-id="e1452-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="e1452-106">Change description</span></span>

<span data-ttu-id="e1452-107">Ранее вызовы <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> не создавали предупреждения во время компиляции, однако метод вызывал <xref:System.PlatformNotSupportedException> во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="e1452-107">Previously, calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> did not produce compile-time warnings, however, the method did throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="e1452-108">Начиная с .NET 5.0 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> помечен как устаревший с отображением соответствующего предупреждения.</span><span class="sxs-lookup"><span data-stu-id="e1452-108">Starting in .NET 5.0, <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is marked obsolete as warning.</span></span> <span data-ttu-id="e1452-109">При вызове этого метода выдается предупреждение компилятора `SYSLIB0006`.</span><span class="sxs-lookup"><span data-stu-id="e1452-109">Calling this method produces compiler warning `SYSLIB0006`.</span></span> <span data-ttu-id="e1452-110">Реализация метода остается неизменной, и по-прежнему возникнет исключение <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="e1452-110">The implementation of the method is unchanged, and it continues to throw a <xref:System.PlatformNotSupportedException>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e1452-111">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="e1452-111">Reason for change</span></span>

<span data-ttu-id="e1452-112">Учитывая, что <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> всегда создает <xref:System.PlatformNotSupportedException> для всех реализаций .NET, кроме .NET Framework, был добавлен в метод <xref:System.ObsoleteAttribute>, чтобы привлечь внимание к местам, где он вызывается.</span><span class="sxs-lookup"><span data-stu-id="e1452-112">Given that <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> always throws a <xref:System.PlatformNotSupportedException> on all .NET implementations except .NET Framework, <xref:System.ObsoleteAttribute> was added to the method to draw attention to places where it's called.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e1452-113">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="e1452-113">Version introduced</span></span>

<span data-ttu-id="e1452-114">5.0</span><span class="sxs-lookup"><span data-stu-id="e1452-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e1452-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="e1452-115">Recommended action</span></span>

- <span data-ttu-id="e1452-116">Используйте <xref:System.Threading.CancellationToken>, чтобы прервать обработку единицы работы вместо вызова <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e1452-116">Use a <xref:System.Threading.CancellationToken> to abort processing of a unit of work instead of calling <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e1452-117">В следующем примере демонстрируется применение <xref:System.Threading.CancellationToken>.</span><span class="sxs-lookup"><span data-stu-id="e1452-117">The following example illustrates the use of <xref:System.Threading.CancellationToken>.</span></span>

  ```csharp
  void ProcessPendingWorkItemsNew(CancellationToken cancellationToken)
  {
      if (QueryIsMoreWorkPending())
      {
          // If the CancellationToken is marked as "needs to cancel",
          // this will throw the appropriate exception.
          cancellationToken.ThrowIfCancellationRequested();

          WorkItem work = DequeueWorkItem();
          ProcessWorkItem(work);
      }
  }
  ```

  <span data-ttu-id="e1452-118">Подробные сведения см. в статье [Отмена в управляемых потоках](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="e1452-118">For more information, see [Cancellation in managed threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>

- <span data-ttu-id="e1452-119">Чтобы отключить предупреждение во время компиляции, отключите код предупреждения `SYSLIB0006`.</span><span class="sxs-lookup"><span data-stu-id="e1452-119">To suppress the compile-time warning, suppress warning code `SYSLIB0006`.</span></span> <span data-ttu-id="e1452-120">Код предупреждения относится только к <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>, и подавление не влияет на другие предупреждения об устаревании в коде.</span><span class="sxs-lookup"><span data-stu-id="e1452-120">The warning code is specific to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> and suppressing it doesn't suppress other obsoletion warnings in your code.</span></span> <span data-ttu-id="e1452-121">Однако рекомендуется удалить вызовы <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> вместо того, чтобы подавлять предупреждение.</span><span class="sxs-lookup"><span data-stu-id="e1452-121">However, we recommend that you remove calls to <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> instead of suppressing the warning.</span></span>

  ```csharp
  void MyMethod()
  {
  #pragma warning disable SYSLIB0006
      Thread.CurrentThread.Abort();
  #pragma warning restore SYSLIB0006
  }
  ```

  <span data-ttu-id="e1452-122">Предупреждение можно также отключить в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="e1452-122">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "Thread.Abort is obsolete" warnings for entire project. -->
    <NoWarn>$(NoWarn);SYSLIB0006</NoWarn>
  </PropertyGroup>
  ```

## <a name="affected-apis"></a><span data-ttu-id="e1452-123">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="e1452-123">Affected APIs</span></span>

- <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `Overload:System.Threading.Thread.Abort`

-->
