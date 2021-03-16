---
title: Предупреждение SYSLIB0004
description: Сведения об устаревших элементах, которые приводят к появлению предупреждения во время компиляции SYSLIB0004.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 76726e233e2900c82dce1b0872533e5356e91c8c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256375"
---
# <a name="syslib0004-the-constrained-execution-region-cer-feature-is-not-supported"></a><span data-ttu-id="9ae31-103">SYSLIB0004. Функция области ограниченного выполнения (CER) не поддерживается</span><span class="sxs-lookup"><span data-stu-id="9ae31-103">SYSLIB0004: The constrained execution region (CER) feature is not supported</span></span>

<span data-ttu-id="9ae31-104">Функция [областей ограниченного выполнения (CER)](../../../framework/performance/constrained-execution-regions.md) поддерживается только в .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ae31-104">The [Constrained execution regions (CER)](../../../framework/performance/constrained-execution-regions.md) feature is supported only in .NET Framework.</span></span> <span data-ttu-id="9ae31-105">Таким образом, различные связанные этой функцией API помечаются как устаревшие, начиная с версии .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="9ae31-105">As such, various CER-related APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="9ae31-106">При использовании этих API во время компиляции создается предупреждение `SYSLIB0004`.</span><span class="sxs-lookup"><span data-stu-id="9ae31-106">Using these APIs generates warning `SYSLIB0004` at compile time.</span></span>

<span data-ttu-id="9ae31-107">Следующие интерфейсы API, связанные с функцией областей ограниченного выполнения (CER), являются устаревшими:</span><span class="sxs-lookup"><span data-stu-id="9ae31-107">The following CER-related APIs are obsolete:</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(System.Runtime.CompilerServices.RuntimeHelpers.TryCode,System.Runtime.CompilerServices.RuntimeHelpers.CleanupCode,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegionsNoOP?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareContractedDelegate(System.Delegate)?displayProperty=nameWithType>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.ProbeForSufficientStack?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Cer?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.Consistency?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute?displayProperty=nameWithType>
- <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="9ae31-108">Обходные пути</span><span class="sxs-lookup"><span data-stu-id="9ae31-108">Workarounds</span></span>

- <span data-ttu-id="9ae31-109">Если вы применили к методу атрибут CER, удалите атрибут.</span><span class="sxs-lookup"><span data-stu-id="9ae31-109">If you have applied a CER attribute to a method, remove the attribute.</span></span> <span data-ttu-id="9ae31-110">Эти атрибуты не действуют в .NET 5 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="9ae31-110">These attributes have no effect in .NET 5 and later versions.</span></span>

  ```csharp
  // REMOVE the attribute below.
  [ReliabilityContract(Consistency.WillNotCorruptState, Cer.Success)]
  public void DoSomething()
  {
  }

  // REMOVE the attribute below.
  [PrePrepareMethod]
  public void DoSomething()
  {
  }
  ```

- <span data-ttu-id="9ae31-111">При вызове `RuntimeHelpers.ProbeForSufficientStack` или `RuntimeHelpers.PrepareContractedDelegate` удалите вызов.</span><span class="sxs-lookup"><span data-stu-id="9ae31-111">If you are calling `RuntimeHelpers.ProbeForSufficientStack` or `RuntimeHelpers.PrepareContractedDelegate`, remove the call.</span></span> <span data-ttu-id="9ae31-112">Эти вызовы не действуют в .NET 5 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="9ae31-112">These calls have no effect in .NET 5 and later versions.</span></span>

  ```csharp
  public void DoSomething()
  {
      // REMOVE the call below.
      RuntimeHelpers.ProbeForSufficientStack();

      // (Remainder of your method logic here.)
  }
  ```

- <span data-ttu-id="9ae31-113">При вызове `RuntimeHelpers.PrepareConstrainedRegions` удалите вызов.</span><span class="sxs-lookup"><span data-stu-id="9ae31-113">If you are calling `RuntimeHelpers.PrepareConstrainedRegions`, remove the call.</span></span> <span data-ttu-id="9ae31-114">Этот вызов не действует в .NET 5 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="9ae31-114">This call has no effect in .NET 5 and later versions.</span></span>

  ```csharp
  public void DoSomething_Old()
  {
      // REMOVE the call below.
      RuntimeHelpers.PrepareConstrainedRegions();
      try
      {
          // try code
      }
      finally
      {
          // cleanup code
      }
  }

  public void DoSomething_Corrected()
  {
      // There is no call to PrepareConstrainedRegions. It's a normal try / finally block.

      try
      {
          // try code
      }
      finally
      {
          // cleanup code
      }
  }
  ```

- <span data-ttu-id="9ae31-115">При вызове `RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup` замените вызов на стандартный блок _try/catch/finally_.</span><span class="sxs-lookup"><span data-stu-id="9ae31-115">If you are calling `RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup`, replace the call with a standard _try / catch / finally_ block.</span></span>

  ```csharp
  // The sample below produces warning SYSLIB0004.
  public void DoSomething_Old()
  {
      RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup(MyTryCode, MyCleanupCode, null);
  }
  public void MyTryCode(object state) { /* try code */ }
  public void MyCleanupCode(object state, bool exceptionThrown) { /* cleanup code */ }

  // The corrected sample below does not produce warning SYSLIB0004.
  public void DoSomething_Corrected()
  {
      try
      {
          // try code
      }
      catch (Exception ex)
      {
          // exception handling code
      }
      finally
      {
          // cleanup code
      }
  }
  ```

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="9ae31-116">См. также</span><span class="sxs-lookup"><span data-stu-id="9ae31-116">See also</span></span>

- [<span data-ttu-id="9ae31-117">Области ограниченного выполнения</span><span class="sxs-lookup"><span data-stu-id="9ae31-117">Constrained execution regions</span></span>](../../../framework/performance/constrained-execution-regions.md)
