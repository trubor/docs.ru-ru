---
title: Разработка служебных приложений Windows
description: См. ссылки на статьи, в которых объясняется, как разрабатывать приложения-службы Windows с помощью Visual Studio или пакета SDK для .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
ms.openlocfilehash: 7a19d48ee4e7b12bc6ed0ff7fa5e2c8899bffaca
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494484"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="bbe9a-103">Разработка приложений службы Windows</span><span class="sxs-lookup"><span data-stu-id="bbe9a-103">Develop Windows service apps</span></span>

<span data-ttu-id="bbe9a-104">С помощью Visual Studio или пакета SDK для .NET Framework можно легко создавать службы. Просто создайте приложение, которое устанавливается как служба.</span><span class="sxs-lookup"><span data-stu-id="bbe9a-104">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="bbe9a-105">Такие приложения называются службами Windows.</span><span class="sxs-lookup"><span data-stu-id="bbe9a-105">This type of application is called a Windows service.</span></span> <span data-ttu-id="bbe9a-106">Используя компоненты платформы, можно создавать, устанавливать, запускать, останавливать и администрировать службы.</span><span class="sxs-lookup"><span data-stu-id="bbe9a-106">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="bbe9a-107">В Visual Studio можно создать службы с помощью управляемого кода на Visual C# или Visual Basic, который при необходимости может взаимодействовать с существующим кодом C++.</span><span class="sxs-lookup"><span data-stu-id="bbe9a-107">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="bbe9a-108">Или можно создать службу Windows на машинном языке C++ с помощью [мастера проектов ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="bbe9a-108">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="bbe9a-109">Содержание раздела</span><span class="sxs-lookup"><span data-stu-id="bbe9a-109">In this section</span></span>

[<span data-ttu-id="bbe9a-110">Знакомство с приложениями служб Windows</span><span class="sxs-lookup"><span data-stu-id="bbe9a-110">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)

<span data-ttu-id="bbe9a-111">Сведения о приложениях служб Windows, времени существования служб и отличиях приложений служб от распространенных типов проектов.</span><span class="sxs-lookup"><span data-stu-id="bbe9a-111">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="bbe9a-112">Пошаговое руководство: Создание приложения служб Windows в конструкторе компонентов</span><span class="sxs-lookup"><span data-stu-id="bbe9a-112">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="bbe9a-113">Пример создания службы на Visual Basic и Visual C#.</span><span class="sxs-lookup"><span data-stu-id="bbe9a-113">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="bbe9a-114">Программная архитектура приложений служб</span><span class="sxs-lookup"><span data-stu-id="bbe9a-114">Service Application Programming Architecture</span></span>](service-application-programming-architecture.md)

<span data-ttu-id="bbe9a-115">Описание элементов языка, используемых при создании служб.</span><span class="sxs-lookup"><span data-stu-id="bbe9a-115">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="bbe9a-116">Практическое руководство. Создание служб Windows</span><span class="sxs-lookup"><span data-stu-id="bbe9a-116">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)

<span data-ttu-id="bbe9a-117">Создание и настройка служб Windows с помощью шаблона проекта службы Windows.</span><span class="sxs-lookup"><span data-stu-id="bbe9a-117">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="bbe9a-118">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="bbe9a-118">Related sections</span></span>

<span data-ttu-id="bbe9a-119"><xref:System.ServiceProcess.ServiceBase> — описываются основные характеристики класса <xref:System.ServiceProcess.ServiceBase>, который используется для создания служб.</span><span class="sxs-lookup"><span data-stu-id="bbe9a-119"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="bbe9a-120"><xref:System.ServiceProcess.ServiceProcessInstaller> — описываются возможности класса <xref:System.ServiceProcess.ServiceProcessInstaller>, который используется вместе с классом <xref:System.ServiceProcess.ServiceInstaller> для установки и удаления службы.</span><span class="sxs-lookup"><span data-stu-id="bbe9a-120"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="bbe9a-121"><xref:System.ServiceProcess.ServiceInstaller> — описываются возможности класса <xref:System.ServiceProcess.ServiceInstaller>, который используется вместе с классом <xref:System.ServiceProcess.ServiceProcessInstaller> для установки и удаления службы.</span><span class="sxs-lookup"><span data-stu-id="bbe9a-121"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="bbe9a-122">[Create Projects from Templates](/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) (Создание проектов на основе шаблонов) — описываются типы проектов, которые используются в этом разделе, и способ их выбора.</span><span class="sxs-lookup"><span data-stu-id="bbe9a-122">[Create Projects from Templates](/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -  Describes the projects types used in this chapter and how to choose between them.</span></span>
