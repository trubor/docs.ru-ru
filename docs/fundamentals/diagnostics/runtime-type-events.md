---
title: События среды выполнения системы типов
description: См. события среды выполнения .NET, собирающие диагностическую информацию, относящуюся к системе типов .NET, например TypeLoadStart и TypeLoadStop.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- type system events (CoreCLR)
- ETW, EventPipe, LTTng type system events (CoreCLR)
ms.openlocfilehash: 8eee89cddb0098da2cb449a4be21945adac725e3
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96594038"
---
# <a name="net-runtime-type-events"></a><span data-ttu-id="3ec67-103">События типов среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="3ec67-103">.NET runtime type events</span></span>

<span data-ttu-id="3ec67-104">Эти события собирают сведения, связанные с загрузкой типов.</span><span class="sxs-lookup"><span data-stu-id="3ec67-104">These events collect information relating to loading types.</span></span> <span data-ttu-id="3ec67-105">Дополнительные сведения об использовании этих событий в целях диагностики см. в статье [Ведение журнала и трассировка в приложениях .NET](../../core/diagnostics/logging-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="3ec67-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="typeloadstart-event"></a><span data-ttu-id="3ec67-106">Событие TypeLoadStart</span><span class="sxs-lookup"><span data-stu-id="3ec67-106">TypeLoadStart Event</span></span>

|<span data-ttu-id="3ec67-107">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="3ec67-107">Keyword for raising the event</span></span>|<span data-ttu-id="3ec67-108">Событие</span><span class="sxs-lookup"><span data-stu-id="3ec67-108">Event</span></span>|<span data-ttu-id="3ec67-109">Level</span><span class="sxs-lookup"><span data-stu-id="3ec67-109">Level</span></span>|  
|-----------------------------------|-----------|-----------|  
|<span data-ttu-id="3ec67-110">`TypeDiagnosticKeyword` (0x8000000000)</span><span class="sxs-lookup"><span data-stu-id="3ec67-110">`TypeDiagnosticKeyword` (0x8000000000)</span></span>|<span data-ttu-id="3ec67-111">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="3ec67-111">Informational (4)</span></span>|  

|<span data-ttu-id="3ec67-112">Событие</span><span class="sxs-lookup"><span data-stu-id="3ec67-112">Event</span></span>|<span data-ttu-id="3ec67-113">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="3ec67-113">Event ID</span></span>|<span data-ttu-id="3ec67-114">Описание</span><span class="sxs-lookup"><span data-stu-id="3ec67-114">Description</span></span>|  
|-----------|--------------|-----------------|  
|`TypeLoadStart`|<span data-ttu-id="3ec67-115">73</span><span class="sxs-lookup"><span data-stu-id="3ec67-115">73</span></span>|<span data-ttu-id="3ec67-116">Начата загрузка типа.</span><span class="sxs-lookup"><span data-stu-id="3ec67-116">A type load has started.</span></span>|

|<span data-ttu-id="3ec67-117">Имя поля</span><span class="sxs-lookup"><span data-stu-id="3ec67-117">Field name</span></span>|<span data-ttu-id="3ec67-118">Тип данных</span><span class="sxs-lookup"><span data-stu-id="3ec67-118">Data type</span></span>|<span data-ttu-id="3ec67-119">Описание</span><span class="sxs-lookup"><span data-stu-id="3ec67-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|<span data-ttu-id="3ec67-120">Идентификатор операции загрузки типа.</span><span class="sxs-lookup"><span data-stu-id="3ec67-120">ID for the type load operation.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="3ec67-121">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3ec67-121">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="typeloadstop-event"></a><span data-ttu-id="3ec67-122">Событие TypeLoadStop</span><span class="sxs-lookup"><span data-stu-id="3ec67-122">TypeLoadStop Event</span></span>

|<span data-ttu-id="3ec67-123">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="3ec67-123">Keyword for raising the event</span></span>|<span data-ttu-id="3ec67-124">Level</span><span class="sxs-lookup"><span data-stu-id="3ec67-124">Level</span></span>|  
|-----------------------------------|-----------|-----------|  
|<span data-ttu-id="3ec67-125">`TypeDiagnosticKeyword` (0x8000000000)</span><span class="sxs-lookup"><span data-stu-id="3ec67-125">`TypeDiagnosticKeyword` (0x8000000000)</span></span>|<span data-ttu-id="3ec67-126">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="3ec67-126">Informational (4)</span></span>|  

|<span data-ttu-id="3ec67-127">Событие</span><span class="sxs-lookup"><span data-stu-id="3ec67-127">Event</span></span>|<span data-ttu-id="3ec67-128">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="3ec67-128">Event ID</span></span>|<span data-ttu-id="3ec67-129">Описание</span><span class="sxs-lookup"><span data-stu-id="3ec67-129">Description</span></span>|  
|-----------|--------------|-----------------|  
|`TypeLoadStop`|<span data-ttu-id="3ec67-130">74</span><span class="sxs-lookup"><span data-stu-id="3ec67-130">74</span></span>|<span data-ttu-id="3ec67-131">Загрузка типа завершена.</span><span class="sxs-lookup"><span data-stu-id="3ec67-131">A type load is finished.</span></span>|

|<span data-ttu-id="3ec67-132">Имя поля</span><span class="sxs-lookup"><span data-stu-id="3ec67-132">Field name</span></span>|<span data-ttu-id="3ec67-133">Тип данных</span><span class="sxs-lookup"><span data-stu-id="3ec67-133">Data type</span></span>|<span data-ttu-id="3ec67-134">Описание</span><span class="sxs-lookup"><span data-stu-id="3ec67-134">Description</span></span>|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|<span data-ttu-id="3ec67-135">Идентификатор для операции загрузки типа (совпадает с TypeLoadStartID соответствующего события TypeLoadStart).</span><span class="sxs-lookup"><span data-stu-id="3ec67-135">ID for the type load operation (matches the corresponding TypeLoadStart event's TypeLoadStartID).</span></span>|
|`LoadLevel`|`win:UInt16`|<span data-ttu-id="3ec67-136">Уровень загрузки типа.</span><span class="sxs-lookup"><span data-stu-id="3ec67-136">Type load level.</span></span>|
|`TypeID`|`win:UInt64`|<span data-ttu-id="3ec67-137">Указатель на дескриптор типа.</span><span class="sxs-lookup"><span data-stu-id="3ec67-137">Pointer to the type handle.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="3ec67-138">Имя типа данных.</span><span class="sxs-lookup"><span data-stu-id="3ec67-138">Name of the type.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="3ec67-139">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3ec67-139">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
