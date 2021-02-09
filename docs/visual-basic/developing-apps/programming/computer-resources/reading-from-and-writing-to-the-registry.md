---
description: 'Узнайте подробнее о: Чтение данных из реестра и запись в реестр (Visual Basic)'
title: Чтение данных из реестра и запись в реестр
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: 0a9e32480845e617f6e4fde2f31c58eea8da4ee7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701551"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="1d3fa-103">Чтение данных из реестра и запись в реестр (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d3fa-103">Reading from and Writing to the Registry (Visual Basic)</span></span>

<span data-ttu-id="1d3fa-104">В этом разделе описываются задачи и приводятся основные разделы, связанные с реестром.</span><span class="sxs-lookup"><span data-stu-id="1d3fa-104">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="1d3fa-105">При программировании в Visual Basic можно получить доступ к реестру с помощью функций, предоставляемых Visual Basic, или классов .NET для работы с реестром.</span><span class="sxs-lookup"><span data-stu-id="1d3fa-105">When programming in Visual Basic, you can choose to access the registry by means of either the functions provided by Visual Basic or the registry classes of .NET.</span></span> <span data-ttu-id="1d3fa-106">Реестр содержит данные, исходящие как от операционной системы, так и от приложений, установленных на компьютере.</span><span class="sxs-lookup"><span data-stu-id="1d3fa-106">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="1d3fa-107">Работа с реестром может привести к нарушению безопасности, допуская несанкционированный доступ к системным ресурсам или защищенной информации.</span><span class="sxs-lookup"><span data-stu-id="1d3fa-107">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1d3fa-108">Содержание</span><span class="sxs-lookup"><span data-stu-id="1d3fa-108">In This Section</span></span>  

 [<span data-ttu-id="1d3fa-109">Практическое руководство. Создание раздела реестра и задание его значения</span><span class="sxs-lookup"><span data-stu-id="1d3fa-109">How to: Create a Registry Key and Set Its Value</span></span>](how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="1d3fa-110">Описывает использование методов `CreateSubKey` и `SetValue` объекта `My.Computer.Registry` для создания раздела реестра и присвоения ему значения.</span><span class="sxs-lookup"><span data-stu-id="1d3fa-110">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="1d3fa-111">Практическое руководство. Чтение значения из раздела реестра</span><span class="sxs-lookup"><span data-stu-id="1d3fa-111">How to: Read a Value from a Registry Key</span></span>](how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="1d3fa-112">Описывает использование метода `GetValue` объекта `My.Computer.Registry` для чтения значения из раздела реестра.</span><span class="sxs-lookup"><span data-stu-id="1d3fa-112">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="1d3fa-113">Практическое руководство. Удаление раздела реестра</span><span class="sxs-lookup"><span data-stu-id="1d3fa-113">How to: Delete a Registry Key</span></span>](how-to-delete-a-registry-key.md)  
 <span data-ttu-id="1d3fa-114">Описывает использование метода `DeleteSubKey` свойства `My.Computer.Registry.CurrentUser` для удаления раздела реестра.</span><span class="sxs-lookup"><span data-stu-id="1d3fa-114">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="1d3fa-115">Чтение реестра и запись в него с использованием пространства имен Microsoft.Win32</span><span class="sxs-lookup"><span data-stu-id="1d3fa-115">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="1d3fa-116">Описывает использование классов `Registry` и `RegistryKey` в .NET для доступа к реестру.</span><span class="sxs-lookup"><span data-stu-id="1d3fa-116">Describes how to use the `Registry` and `RegistryKey` classes of .NET to access the registry.</span></span>  
  
 [<span data-ttu-id="1d3fa-117">Безопасность и реестр</span><span class="sxs-lookup"><span data-stu-id="1d3fa-117">Security and the Registry</span></span>](security-and-the-registry.md)  
 <span data-ttu-id="1d3fa-118">Описывает вопросы безопасности, связанные с реестром.</span><span class="sxs-lookup"><span data-stu-id="1d3fa-118">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1d3fa-119">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="1d3fa-119">Related Sections</span></span>  

 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="1d3fa-120">Список и описание членов объекта `My.Computer.Registry`.</span><span class="sxs-lookup"><span data-stu-id="1d3fa-120">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="1d3fa-121">Обзор класса `Registry` со ссылками на отдельные разделы и члены.</span><span class="sxs-lookup"><span data-stu-id="1d3fa-121">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
