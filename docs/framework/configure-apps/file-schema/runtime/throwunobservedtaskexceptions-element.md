---
description: 'Дополнительные сведения о: <ThrowUnobservedTaskExceptions> element'
title: Элемент <ThrowUnobservedTaskExceptions>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
ms.openlocfilehash: 53f3f1275ea8419bed52fd73726c043e1c49eed7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802402"
---
# <a name="throwunobservedtaskexceptions-element"></a><span data-ttu-id="ce63c-103">Элемент \<ThrowUnobservedTaskExceptions></span><span class="sxs-lookup"><span data-stu-id="ce63c-103">\<ThrowUnobservedTaskExceptions> Element</span></span>

<span data-ttu-id="ce63c-104">Определяет, будут ли необработанные исключения задачи завершать выполняющийся процесс.</span><span class="sxs-lookup"><span data-stu-id="ce63c-104">Specifies whether unhandled task exceptions should terminate a running process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
## <a name="syntax"></a><span data-ttu-id="ce63c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ce63c-105">Syntax</span></span>  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce63c-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ce63c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ce63c-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ce63c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce63c-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ce63c-108">Attributes</span></span>  
  
|<span data-ttu-id="ce63c-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ce63c-109">Attribute</span></span>|<span data-ttu-id="ce63c-110">Описание</span><span class="sxs-lookup"><span data-stu-id="ce63c-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ce63c-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="ce63c-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="ce63c-112">Указывает, должны ли исключения необработанных задач завершать выполняющийся процесс.</span><span class="sxs-lookup"><span data-stu-id="ce63c-112">Specifies whether unhandled task exceptions should terminate the running process.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ce63c-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="ce63c-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="ce63c-114">Значение</span><span class="sxs-lookup"><span data-stu-id="ce63c-114">Value</span></span>|<span data-ttu-id="ce63c-115">Описание</span><span class="sxs-lookup"><span data-stu-id="ce63c-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ce63c-116">Не завершает выполняющийся процесс для исключения необработанной задачи.</span><span class="sxs-lookup"><span data-stu-id="ce63c-116">Does not terminate the running process for an unhandled task exception.</span></span> <span data-ttu-id="ce63c-117">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ce63c-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="ce63c-118">Завершает выполняющийся процесс для исключения необработанной задачи.</span><span class="sxs-lookup"><span data-stu-id="ce63c-118">Terminates the running process for an unhandled task exception.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce63c-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ce63c-119">Child Elements</span></span>  

 <span data-ttu-id="ce63c-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ce63c-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce63c-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ce63c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ce63c-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="ce63c-122">Element</span></span>|<span data-ttu-id="ce63c-123">Описание</span><span class="sxs-lookup"><span data-stu-id="ce63c-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ce63c-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce63c-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ce63c-125">Содержит сведения о параметрах инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="ce63c-125">Contains information about runtime initialization options.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="ce63c-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="ce63c-126">Remarks</span></span>  

 <span data-ttu-id="ce63c-127">Если исключение, связанное с объектом <xref:System.Threading.Tasks.Task> , не было замечено, то операция отсутствует <xref:System.Threading.Tasks.Task.Wait%2A> , родительский элемент не присоединяется, а <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> свойство не было прочитано, поэтому исключение задачи считается незамеченным.</span><span class="sxs-lookup"><span data-stu-id="ce63c-127">If an exception that is associated with a <xref:System.Threading.Tasks.Task> has not been observed, there is no <xref:System.Threading.Tasks.Task.Wait%2A> operation, the parent is not attached, and the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property was not read the task exception is considered to be unobserved.</span></span>  
  
 <span data-ttu-id="ce63c-128">В платформа .NET Framework 4, по умолчанию, если <xref:System.Threading.Tasks.Task> исключение, для которого имеется незамеченная исключительная ошибка, уничтожается сборщиком мусора, метод завершения создает исключение и завершает процесс.</span><span class="sxs-lookup"><span data-stu-id="ce63c-128">In the .NET Framework 4, by default, if a <xref:System.Threading.Tasks.Task> that has an unobserved exception is garbage collected, the finalizer throws an exception and terminates the process.</span></span> <span data-ttu-id="ce63c-129">Завершение процесса определяется временем сбора мусора и финализации.</span><span class="sxs-lookup"><span data-stu-id="ce63c-129">The termination of the process is determined by the timing of garbage collection and finalization.</span></span>  
  
 <span data-ttu-id="ce63c-130">Чтобы разработчикам было проще писать асинхронный код на основе задач, платформа .NET Framework 4,5 изменяет это поведение по умолчанию для незамеченных исключений.</span><span class="sxs-lookup"><span data-stu-id="ce63c-130">To make it easier for developers to write asynchronous code based on tasks, the .NET Framework 4.5 changes this default behavior for unobserved exceptions.</span></span> <span data-ttu-id="ce63c-131">Незамеченные исключения по-прежнему вызывают <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> событие, но по умолчанию процесс не завершается.</span><span class="sxs-lookup"><span data-stu-id="ce63c-131">Unobserved exceptions still cause the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event to be raised, but by default, the process does not terminate.</span></span> <span data-ttu-id="ce63c-132">Вместо этого исключение пропускается после возникновения события, независимо от того, отслеживает ли обработчик событий исключение.</span><span class="sxs-lookup"><span data-stu-id="ce63c-132">Instead, the exception is ignored after the event is raised, regardless of whether an event handler observes the exception.</span></span>  
  
 <span data-ttu-id="ce63c-133">В платформа .NET Framework 4,5 можно использовать [ \<ThrowUnobservedTaskExceptions> элемент](throwunobservedtaskexceptions-element.md) в файле конфигурации приложения, чтобы обеспечить платформа .NET Framework 4 действия создания исключения.</span><span class="sxs-lookup"><span data-stu-id="ce63c-133">In the .NET Framework 4.5, you can use the [\<ThrowUnobservedTaskExceptions> element](throwunobservedtaskexceptions-element.md) in an application configuration file to enable the .NET Framework 4 behavior of throwing an exception.</span></span>  
  
 <span data-ttu-id="ce63c-134">Можно также указать поведение исключения одним из следующих способов.</span><span class="sxs-lookup"><span data-stu-id="ce63c-134">You can also specify the exception behavior in one of the following ways:</span></span>  
  
- <span data-ttu-id="ce63c-135">Путем задания переменной среды `COMPlus_ThrowUnobservedTaskExceptions` ( `set COMPlus_ThrowUnobservedTaskExceptions=1` ).</span><span class="sxs-lookup"><span data-stu-id="ce63c-135">By setting the environment variable `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).</span></span>  
  
- <span data-ttu-id="ce63c-136">Установив значение DWORD реестра Сровунобсерведтаскексцептионс = 1 в HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\ . Ключ NETFramework.</span><span class="sxs-lookup"><span data-stu-id="ce63c-136">By setting the registry DWORD value ThrowUnobservedTaskExceptions = 1 in the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce63c-137">Пример</span><span class="sxs-lookup"><span data-stu-id="ce63c-137">Example</span></span>  

 <span data-ttu-id="ce63c-138">В следующем примере показано, как включить создание исключений в задачах с помощью файла конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="ce63c-138">The following example shows how to enable the throwing of exceptions in tasks by using an application configuration file.</span></span>  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="ce63c-139">Пример</span><span class="sxs-lookup"><span data-stu-id="ce63c-139">Example</span></span>  

 <span data-ttu-id="ce63c-140">В следующем примере показано, как выдается незамеченное исключение из задачи.</span><span class="sxs-lookup"><span data-stu-id="ce63c-140">The following example demonstrates how an unobserved exception is thrown from a task.</span></span> <span data-ttu-id="ce63c-141">Чтобы правильно работать, код должен быть запущен в качестве выпущенной программы.</span><span class="sxs-lookup"><span data-stu-id="ce63c-141">The code must be run as a released program to work correctly.</span></span>  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ce63c-142">См. также</span><span class="sxs-lookup"><span data-stu-id="ce63c-142">See also</span></span>

- [<span data-ttu-id="ce63c-143">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="ce63c-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ce63c-144">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="ce63c-144">Configuration File Schema</span></span>](../index.md)
