---
description: 'Дополнительные сведения: отладка глобальных статических функций'
title: Глобальные статические функции отладки
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
ms.openlocfilehash: efee1bfb6eb61ae2311320a4c12bf08ec0f9534b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661458"
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="de338-103">Глобальные статические функции отладки</span><span class="sxs-lookup"><span data-stu-id="de338-103">Debugging Global Static Functions</span></span>

<span data-ttu-id="de338-104">В этом разделе описываются неуправляемые глобальные статистические функции, которые используют API отладки.</span><span class="sxs-lookup"><span data-stu-id="de338-104">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="de338-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="de338-105">In This Section</span></span>  

 [<span data-ttu-id="de338-106">Функция _EFN_GetManagedExcepStack</span><span class="sxs-lookup"><span data-stu-id="de338-106">_EFN_GetManagedExcepStack Function</span></span>](efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="de338-107">Учитывая адрес объекта управляемого исключения, возвращает строковую версию трассировки стека, содержащейся внутри.</span><span class="sxs-lookup"><span data-stu-id="de338-107">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="de338-108">Функция _EFN_GetManagedObjectFieldInfo</span><span class="sxs-lookup"><span data-stu-id="de338-108">_EFN_GetManagedObjectFieldInfo Function</span></span>](efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="de338-109">Возвращает смещение от начала объекта до поля и значение поля, используя предоставленный указатель объекта и имя поля.</span><span class="sxs-lookup"><span data-stu-id="de338-109">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="de338-110">Функция _EFN_GetManagedObjectName</span><span class="sxs-lookup"><span data-stu-id="de338-110">_EFN_GetManagedObjectName Function</span></span>](efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="de338-111">Получает имя типа с помощью предоставленного указателя управляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="de338-111">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="de338-112">Функция _EFN_StackTrace</span><span class="sxs-lookup"><span data-stu-id="de338-112">_EFN_StackTrace Function</span></span>](efn-stacktrace-function.md)  
 <span data-ttu-id="de338-113">Предоставляет текстовое представление трассировки управляемого стека и массив записей `CONTEXT`, по одной для каждого перехода между неуправляемым и управляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="de338-113">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="de338-114">Функция CLRDataCreateInstance</span><span class="sxs-lookup"><span data-stu-id="de338-114">CLRDataCreateInstance Function</span></span>](clrdatacreateinstance-function.md)  
 <span data-ttu-id="de338-115">Вызывается службами доступа к данным среды CLR для создания указанного объекта интерфейса для заданного целевого процесса.</span><span class="sxs-lookup"><span data-stu-id="de338-115">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="de338-116">Указатель функции PFN_CLRDataCreateInstance</span><span class="sxs-lookup"><span data-stu-id="de338-116">PFN_CLRDataCreateInstance Function Pointer</span></span>](pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="de338-117">Указывает на функцию, вызываемую службами доступа к данным среды CLR, чтобы создать указанный объект интерфейса для заданного целевого процесса.</span><span class="sxs-lookup"><span data-stu-id="de338-117">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="de338-118">См. также</span><span class="sxs-lookup"><span data-stu-id="de338-118">Related Sections</span></span>  

 [<span data-ttu-id="de338-119">Компонентные классы отладки</span><span class="sxs-lookup"><span data-stu-id="de338-119">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="de338-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="de338-120">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="de338-121">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="de338-121">Debugging Enumerations</span></span>](debugging-enumerations.md)  
  
 [<span data-ttu-id="de338-122">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="de338-122">Debugging Structures</span></span>](debugging-structures.md)
