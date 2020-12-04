---
title: Типы системных событий среды выполнения
description: См. раздел события среды выполнения .NET, собирающие диагностическую информацию, относящуюся к системе типов .NET, например Типелоадстарт и Типелоадстоп.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- type system events (CoreCLR)
- ETW, EventPipe, LTTng type system events (CoreCLR)
ms.openlocfilehash: 8eee89cddb0098da2cb449a4be21945adac725e3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "96594038"
---
# <a name="net-runtime-type-events"></a><span data-ttu-id="b5f84-103">События типа среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="b5f84-103">.NET runtime type events</span></span>

<span data-ttu-id="b5f84-104">Эти события собираются сведения, связанные с загрузкой типов.</span><span class="sxs-lookup"><span data-stu-id="b5f84-104">These events collect information relating to loading types.</span></span> <span data-ttu-id="b5f84-105">Дополнительные сведения об использовании этих событий в целях диагностики см. в разделе [ведение журнала и трассировка приложений .NET](../../core/diagnostics/logging-tracing.md) .</span><span class="sxs-lookup"><span data-stu-id="b5f84-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="typeloadstart-event"></a><span data-ttu-id="b5f84-106">Событие Типелоадстарт</span><span class="sxs-lookup"><span data-stu-id="b5f84-106">TypeLoadStart Event</span></span>

|<span data-ttu-id="b5f84-107">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="b5f84-107">Keyword for raising the event</span></span>|<span data-ttu-id="b5f84-108">Событие</span><span class="sxs-lookup"><span data-stu-id="b5f84-108">Event</span></span>|<span data-ttu-id="b5f84-109">Level</span><span class="sxs-lookup"><span data-stu-id="b5f84-109">Level</span></span>|  
|-----------------------------------|-----------|-----------|  
|<span data-ttu-id="b5f84-110">`TypeDiagnosticKeyword` (0x8000000000)</span><span class="sxs-lookup"><span data-stu-id="b5f84-110">`TypeDiagnosticKeyword` (0x8000000000)</span></span>|<span data-ttu-id="b5f84-111">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="b5f84-111">Informational (4)</span></span>|  

|<span data-ttu-id="b5f84-112">Событие</span><span class="sxs-lookup"><span data-stu-id="b5f84-112">Event</span></span>|<span data-ttu-id="b5f84-113">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="b5f84-113">Event ID</span></span>|<span data-ttu-id="b5f84-114">Описание</span><span class="sxs-lookup"><span data-stu-id="b5f84-114">Description</span></span>|  
|-----------|--------------|-----------------|  
|`TypeLoadStart`|<span data-ttu-id="b5f84-115">73</span><span class="sxs-lookup"><span data-stu-id="b5f84-115">73</span></span>|<span data-ttu-id="b5f84-116">Начата загрузка типа.</span><span class="sxs-lookup"><span data-stu-id="b5f84-116">A type load has started.</span></span>|

|<span data-ttu-id="b5f84-117">Имя поля</span><span class="sxs-lookup"><span data-stu-id="b5f84-117">Field name</span></span>|<span data-ttu-id="b5f84-118">Тип данных</span><span class="sxs-lookup"><span data-stu-id="b5f84-118">Data type</span></span>|<span data-ttu-id="b5f84-119">Описание</span><span class="sxs-lookup"><span data-stu-id="b5f84-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|<span data-ttu-id="b5f84-120">ИДЕНТИФИКАТОР операции загрузки типа.</span><span class="sxs-lookup"><span data-stu-id="b5f84-120">ID for the type load operation.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="b5f84-121">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b5f84-121">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="typeloadstop-event"></a><span data-ttu-id="b5f84-122">Событие Типелоадстоп</span><span class="sxs-lookup"><span data-stu-id="b5f84-122">TypeLoadStop Event</span></span>

|<span data-ttu-id="b5f84-123">Ключевое слово для вызова события</span><span class="sxs-lookup"><span data-stu-id="b5f84-123">Keyword for raising the event</span></span>|<span data-ttu-id="b5f84-124">Level</span><span class="sxs-lookup"><span data-stu-id="b5f84-124">Level</span></span>|  
|-----------------------------------|-----------|-----------|  
|<span data-ttu-id="b5f84-125">`TypeDiagnosticKeyword` (0x8000000000)</span><span class="sxs-lookup"><span data-stu-id="b5f84-125">`TypeDiagnosticKeyword` (0x8000000000)</span></span>|<span data-ttu-id="b5f84-126">Информационный (4)</span><span class="sxs-lookup"><span data-stu-id="b5f84-126">Informational (4)</span></span>|  

|<span data-ttu-id="b5f84-127">Событие</span><span class="sxs-lookup"><span data-stu-id="b5f84-127">Event</span></span>|<span data-ttu-id="b5f84-128">Идентификатор события</span><span class="sxs-lookup"><span data-stu-id="b5f84-128">Event ID</span></span>|<span data-ttu-id="b5f84-129">Описание</span><span class="sxs-lookup"><span data-stu-id="b5f84-129">Description</span></span>|  
|-----------|--------------|-----------------|  
|`TypeLoadStop`|<span data-ttu-id="b5f84-130">74</span><span class="sxs-lookup"><span data-stu-id="b5f84-130">74</span></span>|<span data-ttu-id="b5f84-131">Загрузка типа завершена.</span><span class="sxs-lookup"><span data-stu-id="b5f84-131">A type load is finished.</span></span>|

|<span data-ttu-id="b5f84-132">Имя поля</span><span class="sxs-lookup"><span data-stu-id="b5f84-132">Field name</span></span>|<span data-ttu-id="b5f84-133">Тип данных</span><span class="sxs-lookup"><span data-stu-id="b5f84-133">Data type</span></span>|<span data-ttu-id="b5f84-134">Описание</span><span class="sxs-lookup"><span data-stu-id="b5f84-134">Description</span></span>|  
|----------------|---------------|-----------------|  
|`TypeLoadStartID`|`win:UInt32`|<span data-ttu-id="b5f84-135">Идентификатор для операции загрузки типа (соответствует соответствующему Типелоадстартиду события Типелоадстарт).</span><span class="sxs-lookup"><span data-stu-id="b5f84-135">ID for the type load operation (matches the corresponding TypeLoadStart event's TypeLoadStartID).</span></span>|
|`LoadLevel`|`win:UInt16`|<span data-ttu-id="b5f84-136">Введите уровень загрузки.</span><span class="sxs-lookup"><span data-stu-id="b5f84-136">Type load level.</span></span>|
|`TypeID`|`win:UInt64`|<span data-ttu-id="b5f84-137">Указатель на маркер типа.</span><span class="sxs-lookup"><span data-stu-id="b5f84-137">Pointer to the type handle.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="b5f84-138">Имя типа данных.</span><span class="sxs-lookup"><span data-stu-id="b5f84-138">Name of the type.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="b5f84-139">Уникальный идентификатор экземпляра CLR или CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b5f84-139">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
