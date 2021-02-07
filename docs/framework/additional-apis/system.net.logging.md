---
description: 'Дополнительные сведения о: класс ведения журнала'
title: Класс ведения журнала (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Logging
- System.Net.Logging.Associate
- System.Net.Logging.Enter
- System.Net.Logging.Exception
- System.Net.Logging.Exit
- System.Net.Logging.get_Http
- System.Net.Logging.get_On
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 1ae3079ab21502ee3f5bf71db57f0695da9a8571
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726212"
---
# <a name="logging-class"></a><span data-ttu-id="a6dca-103">Класс Logging</span><span class="sxs-lookup"><span data-stu-id="a6dca-103">Logging class</span></span>

<span data-ttu-id="a6dca-104">Предоставляет функции ведения журнала трассировки.</span><span class="sxs-lookup"><span data-stu-id="a6dca-104">Provides trace logging functionality.</span></span>

```csharp
internal class Logging
```

> [!WARNING]
> <span data-ttu-id="a6dca-105">Этот класс является внутренним и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="a6dca-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a6dca-106">Корпорация Майкрософт не поддерживает использование этого класса в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="a6dca-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="associate-method"></a><span data-ttu-id="a6dca-107">Метод связывания</span><span class="sxs-lookup"><span data-stu-id="a6dca-107">Associate method</span></span>

<span data-ttu-id="a6dca-108">Записывает в журнал сведения, связанные между двумя объектами.</span><span class="sxs-lookup"><span data-stu-id="a6dca-108">Logs information that two objects are associated with each other.</span></span>

```csharp
internal static void Associate(TraceSource traceSource, object objA, object objB)
```

### <a name="parameters"></a><span data-ttu-id="a6dca-109">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6dca-109">Parameters</span></span>

- <span data-ttu-id="a6dca-110">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="a6dca-110">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="a6dca-111">Источник трассировки, в который регистрируется событие.</span><span class="sxs-lookup"><span data-stu-id="a6dca-111">The trace source to log the event to.</span></span>

- <span data-ttu-id="a6dca-112">`objA` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="a6dca-112">`objA` <xref:System.Object></span></span>

  <span data-ttu-id="a6dca-113">Объект, связываемый с `objB` .</span><span class="sxs-lookup"><span data-stu-id="a6dca-113">The object to associate with `objB`.</span></span>

- <span data-ttu-id="a6dca-114">`objB` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="a6dca-114">`objB` <xref:System.Object></span></span>

  <span data-ttu-id="a6dca-115">Объект, связываемый с `objA` .</span><span class="sxs-lookup"><span data-stu-id="a6dca-115">The object to associate with `objA`.</span></span>

## <a name="entertracesource-object-string-string-method"></a><span data-ttu-id="a6dca-116">Метод Enter (TraceSource, объект, строка, строка)</span><span class="sxs-lookup"><span data-stu-id="a6dca-116">Enter(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="a6dca-117">Регистрирует вход в метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-117">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="a6dca-118">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6dca-118">Parameters</span></span>

- <span data-ttu-id="a6dca-119">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="a6dca-119">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="a6dca-120">Источник трассировки, в который регистрируется событие.</span><span class="sxs-lookup"><span data-stu-id="a6dca-120">The trace source to log the event to.</span></span>

- <span data-ttu-id="a6dca-121">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="a6dca-121">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="a6dca-122">Объект, для которого был вызван метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-122">The object that the method was called on.</span></span>

- <span data-ttu-id="a6dca-123">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-123">`method` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-124">Метод, который следует указать.</span><span class="sxs-lookup"><span data-stu-id="a6dca-124">The method that is being entered.</span></span>

- <span data-ttu-id="a6dca-125">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-125">`param` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-126">Параметры, переданные в метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-126">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-object-string-object-method"></a><span data-ttu-id="a6dca-127">Метод Enter (TraceSource, объект, строка, объект)</span><span class="sxs-lookup"><span data-stu-id="a6dca-127">Enter(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="a6dca-128">Регистрирует вход в метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-128">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="a6dca-129">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6dca-129">Parameters</span></span>

- <span data-ttu-id="a6dca-130">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="a6dca-130">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="a6dca-131">Источник трассировки, в который регистрируется событие.</span><span class="sxs-lookup"><span data-stu-id="a6dca-131">The trace source to log the event to.</span></span>

- <span data-ttu-id="a6dca-132">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="a6dca-132">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="a6dca-133">Объект, для которого был вызван метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-133">The object that the method was called on.</span></span>

- <span data-ttu-id="a6dca-134">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-134">`method` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-135">Метод, который следует указать.</span><span class="sxs-lookup"><span data-stu-id="a6dca-135">The method that is being entered.</span></span>

- <span data-ttu-id="a6dca-136">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="a6dca-136">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="a6dca-137">Параметры, переданные в метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-137">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-string-method"></a><span data-ttu-id="a6dca-138">Ввод (TraceSource, строка, строка, строка)</span><span class="sxs-lookup"><span data-stu-id="a6dca-138">Enter(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="a6dca-139">Регистрирует вход в метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-139">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="a6dca-140">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6dca-140">Parameters</span></span>

- <span data-ttu-id="a6dca-141">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="a6dca-141">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="a6dca-142">Источник трассировки, в который регистрируется событие.</span><span class="sxs-lookup"><span data-stu-id="a6dca-142">The trace source to log the event to.</span></span>

- <span data-ttu-id="a6dca-143">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-143">`obj` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-144">Объект, для которого был вызван метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-144">The object that the method was called on.</span></span>

- <span data-ttu-id="a6dca-145">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-145">`method` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-146">Метод, который следует указать.</span><span class="sxs-lookup"><span data-stu-id="a6dca-146">The method that is being entered.</span></span>

- <span data-ttu-id="a6dca-147">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-147">`param` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-148">Параметры, переданные в метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-148">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-object-method"></a><span data-ttu-id="a6dca-149">Ввод (TraceSource, строка, строка, объект) метод</span><span class="sxs-lookup"><span data-stu-id="a6dca-149">Enter(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="a6dca-150">Регистрирует вход в метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-150">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="a6dca-151">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6dca-151">Parameters</span></span>

- <span data-ttu-id="a6dca-152">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="a6dca-152">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="a6dca-153">Источник трассировки, в который регистрируется событие.</span><span class="sxs-lookup"><span data-stu-id="a6dca-153">The trace source to log the event to.</span></span>

- <span data-ttu-id="a6dca-154">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-154">`obj` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-155">Объект, для которого был вызван метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-155">The object that the method was called on.</span></span>

- <span data-ttu-id="a6dca-156">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-156">`method` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-157">Метод, который следует указать.</span><span class="sxs-lookup"><span data-stu-id="a6dca-157">The method that is being entered.</span></span>

- <span data-ttu-id="a6dca-158">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="a6dca-158">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="a6dca-159">Параметры, переданные в метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-159">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-method"></a><span data-ttu-id="a6dca-160">Ввод (TraceSource, строка, строка) метода</span><span class="sxs-lookup"><span data-stu-id="a6dca-160">Enter(TraceSource, string, string) method</span></span>

<span data-ttu-id="a6dca-161">Регистрирует вход в метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-161">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="a6dca-162">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6dca-162">Parameters</span></span>

- <span data-ttu-id="a6dca-163">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="a6dca-163">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="a6dca-164">Источник трассировки, в который регистрируется событие.</span><span class="sxs-lookup"><span data-stu-id="a6dca-164">The trace source to log the event to.</span></span>

- <span data-ttu-id="a6dca-165">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-165">`method` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-166">Метод, который следует указать.</span><span class="sxs-lookup"><span data-stu-id="a6dca-166">The method that is being entered.</span></span>

- <span data-ttu-id="a6dca-167">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-167">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-168">Параметры, переданные в метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-168">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-method"></a><span data-ttu-id="a6dca-169">Введите метод (TraceSource, String)</span><span class="sxs-lookup"><span data-stu-id="a6dca-169">Enter(TraceSource, string) method</span></span>

<span data-ttu-id="a6dca-170">Регистрирует вход в метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-170">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="a6dca-171">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6dca-171">Parameters</span></span>

- <span data-ttu-id="a6dca-172">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="a6dca-172">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="a6dca-173">Источник трассировки, в который регистрируется событие.</span><span class="sxs-lookup"><span data-stu-id="a6dca-173">The trace source to log the event to.</span></span>

- <span data-ttu-id="a6dca-174">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-174">`msg` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-175">Сообщение входа для записи в источник трассировки.</span><span class="sxs-lookup"><span data-stu-id="a6dca-175">The entrance message to log to the trace source.</span></span>

## <a name="exception-method"></a><span data-ttu-id="a6dca-176">Exception - метод</span><span class="sxs-lookup"><span data-stu-id="a6dca-176">Exception method</span></span>

<span data-ttu-id="a6dca-177">Записывает в журнал исключение и восстанавливает отступы.</span><span class="sxs-lookup"><span data-stu-id="a6dca-177">Logs an exception and restores indentation.</span></span>

```csharp
internal static void Exception(TraceSource traceSource, object obj, string method, Exception e)
```

### <a name="parameters"></a><span data-ttu-id="a6dca-178">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6dca-178">Parameters</span></span>

- <span data-ttu-id="a6dca-179">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="a6dca-179">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="a6dca-180">Источник трассировки, в который регистрируется событие.</span><span class="sxs-lookup"><span data-stu-id="a6dca-180">The trace source to log the event to.</span></span>

- <span data-ttu-id="a6dca-181">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="a6dca-181">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="a6dca-182">Объект, для которого был вызван метод, вызвавший исключение.</span><span class="sxs-lookup"><span data-stu-id="a6dca-182">The object that the method that threw an exception was called on.</span></span>

- <span data-ttu-id="a6dca-183">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-183">`method` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-184">Метод, который выдал исключение.</span><span class="sxs-lookup"><span data-stu-id="a6dca-184">The method that threw the exception.</span></span>

- <span data-ttu-id="a6dca-185">`e` <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="a6dca-185">`e` <xref:System.Exception></span></span>

  <span data-ttu-id="a6dca-186">Вызванное исключение.</span><span class="sxs-lookup"><span data-stu-id="a6dca-186">The exception that was thrown.</span></span>

## <a name="exittracesource-object-string-object-method"></a><span data-ttu-id="a6dca-187">Метод Exit (TraceSource, объект, строка, объект)</span><span class="sxs-lookup"><span data-stu-id="a6dca-187">Exit(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="a6dca-188">Записывает в журнал выход из функции.</span><span class="sxs-lookup"><span data-stu-id="a6dca-188">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="a6dca-189">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6dca-189">Parameters</span></span>

- <span data-ttu-id="a6dca-190">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="a6dca-190">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="a6dca-191">Источник трассировки, в который регистрируется событие.</span><span class="sxs-lookup"><span data-stu-id="a6dca-191">The trace source to log the event to.</span></span>

- <span data-ttu-id="a6dca-192">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="a6dca-192">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="a6dca-193">Объект, для которого был вызван метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-193">The object that the method was called on.</span></span>

- <span data-ttu-id="a6dca-194">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-194">`method` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-195">Метод, который завершается.</span><span class="sxs-lookup"><span data-stu-id="a6dca-195">The method that is being exited.</span></span>

- <span data-ttu-id="a6dca-196">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="a6dca-196">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="a6dca-197">Значение, возвращаемое методом.</span><span class="sxs-lookup"><span data-stu-id="a6dca-197">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-object-method"></a><span data-ttu-id="a6dca-198">Метод Exit (TraceSource, строка, строка, объект)</span><span class="sxs-lookup"><span data-stu-id="a6dca-198">Exit(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="a6dca-199">Записывает в журнал выход из функции.</span><span class="sxs-lookup"><span data-stu-id="a6dca-199">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="a6dca-200">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6dca-200">Parameters</span></span>

- <span data-ttu-id="a6dca-201">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="a6dca-201">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="a6dca-202">Источник трассировки, в который регистрируется событие.</span><span class="sxs-lookup"><span data-stu-id="a6dca-202">The trace source to log the event to.</span></span>

- <span data-ttu-id="a6dca-203">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-203">`obj` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-204">Объект, для которого был вызван метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-204">The object that the method was called on.</span></span>

- <span data-ttu-id="a6dca-205">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-205">`method` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-206">Метод, который завершается.</span><span class="sxs-lookup"><span data-stu-id="a6dca-206">The method that is being exited.</span></span>

- <span data-ttu-id="a6dca-207">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="a6dca-207">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="a6dca-208">Значение, возвращаемое методом.</span><span class="sxs-lookup"><span data-stu-id="a6dca-208">The value that's being returned by the method.</span></span>

## <a name="exittracesource-object-string-string-method"></a><span data-ttu-id="a6dca-209">Метод Exit (TraceSource, объект, строка, строка)</span><span class="sxs-lookup"><span data-stu-id="a6dca-209">Exit(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="a6dca-210">Записывает в журнал выход из функции.</span><span class="sxs-lookup"><span data-stu-id="a6dca-210">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="a6dca-211">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6dca-211">Parameters</span></span>

- <span data-ttu-id="a6dca-212">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="a6dca-212">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="a6dca-213">Источник трассировки, в который регистрируется событие.</span><span class="sxs-lookup"><span data-stu-id="a6dca-213">The trace source to log the event to.</span></span>

- <span data-ttu-id="a6dca-214">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="a6dca-214">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="a6dca-215">Объект, для которого был вызван метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-215">The object that the method was called on.</span></span>

- <span data-ttu-id="a6dca-216">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-216">`method` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-217">Метод, который завершается.</span><span class="sxs-lookup"><span data-stu-id="a6dca-217">The method that is being exited.</span></span>

- <span data-ttu-id="a6dca-218">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-218">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-219">Значение, возвращаемое методом.</span><span class="sxs-lookup"><span data-stu-id="a6dca-219">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-string-method"></a><span data-ttu-id="a6dca-220">Метод Exit (TraceSource, строка, строка, строка)</span><span class="sxs-lookup"><span data-stu-id="a6dca-220">Exit(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="a6dca-221">Записывает в журнал выход из функции.</span><span class="sxs-lookup"><span data-stu-id="a6dca-221">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="a6dca-222">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6dca-222">Parameters</span></span>

- <span data-ttu-id="a6dca-223">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="a6dca-223">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="a6dca-224">Источник трассировки, в который регистрируется событие.</span><span class="sxs-lookup"><span data-stu-id="a6dca-224">The trace source to log the event to.</span></span>

- <span data-ttu-id="a6dca-225">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-225">`obj` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-226">Объект, для которого был вызван метод.</span><span class="sxs-lookup"><span data-stu-id="a6dca-226">The object that the method was called on.</span></span>

- <span data-ttu-id="a6dca-227">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-227">`method` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-228">Метод, который завершается.</span><span class="sxs-lookup"><span data-stu-id="a6dca-228">The method that is being exited.</span></span>

- <span data-ttu-id="a6dca-229">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-229">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-230">Значение, возвращаемое методом.</span><span class="sxs-lookup"><span data-stu-id="a6dca-230">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-method"></a><span data-ttu-id="a6dca-231">Метод Exit (TraceSource, строка, строка)</span><span class="sxs-lookup"><span data-stu-id="a6dca-231">Exit(TraceSource, string, string) method</span></span>

<span data-ttu-id="a6dca-232">Записывает в журнал выход из функции.</span><span class="sxs-lookup"><span data-stu-id="a6dca-232">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="a6dca-233">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6dca-233">Parameters</span></span>

- <span data-ttu-id="a6dca-234">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="a6dca-234">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="a6dca-235">Источник трассировки, в который регистрируется событие.</span><span class="sxs-lookup"><span data-stu-id="a6dca-235">The trace source to log the event to.</span></span>

- <span data-ttu-id="a6dca-236">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-236">`method` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-237">Метод, который завершается.</span><span class="sxs-lookup"><span data-stu-id="a6dca-237">The method that is being exited.</span></span>

- <span data-ttu-id="a6dca-238">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-238">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-239">Параметры, переданные в метод, для которого выполняется выход.</span><span class="sxs-lookup"><span data-stu-id="a6dca-239">The parameters that were passed to the method that's being exited.</span></span>

## <a name="exittracesource-string-method"></a><span data-ttu-id="a6dca-240">Метод Exit (TraceSource, String)</span><span class="sxs-lookup"><span data-stu-id="a6dca-240">Exit(TraceSource, string) method</span></span>

<span data-ttu-id="a6dca-241">Записывает в журнал выход из функции.</span><span class="sxs-lookup"><span data-stu-id="a6dca-241">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="a6dca-242">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6dca-242">Parameters</span></span>

- <span data-ttu-id="a6dca-243">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="a6dca-243">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="a6dca-244">Источник трассировки, в который регистрируется событие.</span><span class="sxs-lookup"><span data-stu-id="a6dca-244">The trace source to log the event to.</span></span>

- <span data-ttu-id="a6dca-245">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a6dca-245">`msg` <xref:System.String></span></span>

  <span data-ttu-id="a6dca-246">Сообщение о выходе для записи в источник трассировки.</span><span class="sxs-lookup"><span data-stu-id="a6dca-246">The exit message to log to the trace source.</span></span>

## <a name="http-property"></a><span data-ttu-id="a6dca-247">Свойство HTTP</span><span class="sxs-lookup"><span data-stu-id="a6dca-247">Http property</span></span>

<span data-ttu-id="a6dca-248">Возвращает источник трассировки для "System .NET. http".</span><span class="sxs-lookup"><span data-stu-id="a6dca-248">Gets the trace source for "System.Net.Http".</span></span>

```csharp
internal static TraceSource Http { get; }
```

### <a name="property-value"></a><span data-ttu-id="a6dca-249">Значение свойства</span><span class="sxs-lookup"><span data-stu-id="a6dca-249">Property value</span></span>

<xref:System.Diagnostics.TraceSource>\
<span data-ttu-id="a6dca-250">Источник трассировки для "System .NET. http" или, `null` Если ведение журнала не включено.</span><span class="sxs-lookup"><span data-stu-id="a6dca-250">The trace source for "System.Net.Http", or `null` if logging is not enabled.</span></span>

## <a name="on-property"></a><span data-ttu-id="a6dca-251">On, свойство</span><span class="sxs-lookup"><span data-stu-id="a6dca-251">On property</span></span>

<span data-ttu-id="a6dca-252">Возвращает значение, указывающее, включено ли ведение журнала.</span><span class="sxs-lookup"><span data-stu-id="a6dca-252">Gets a value that indicates whether logging is enabled.</span></span>

```csharp
internal static bool On { get; }
```

### <a name="property-value"></a><span data-ttu-id="a6dca-253">Значение свойства</span><span class="sxs-lookup"><span data-stu-id="a6dca-253">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="a6dca-254">Значение `true`, если ведение журнала разрешено. В противном случае — значение `false`.</span><span class="sxs-lookup"><span data-stu-id="a6dca-254">`true` if logging is enabled; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="a6dca-255">Требования</span><span class="sxs-lookup"><span data-stu-id="a6dca-255">Requirements</span></span>

<span data-ttu-id="a6dca-256">**Пространство имен:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="a6dca-256">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="a6dca-257">**Сборка:** Система (в System.dll)</span><span class="sxs-lookup"><span data-stu-id="a6dca-257">**Assembly:** System (in System.dll)</span></span>
