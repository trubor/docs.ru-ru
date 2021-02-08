---
description: 'Дополнительные сведения: моделирование и сопоставление'
title: Моделирование и сопоставление
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 063cac072b7a205a471cd808fc85ad9a3ac71288
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795005"
---
# <a name="modeling-and-mapping"></a><span data-ttu-id="ca4dd-103">Моделирование и сопоставление</span><span class="sxs-lookup"><span data-stu-id="ca4dd-103">Modeling and Mapping</span></span>

<span data-ttu-id="ca4dd-104">В Entity Framework можно определить концептуальную модель, модель хранения и сопоставление между двумя способами, которые лучше всего подходят для вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="ca4dd-104">In the Entity Framework, you can define the conceptual model, storage model, and the mapping between the two in the way that best suits your application.</span></span> <span data-ttu-id="ca4dd-105">Средства EDM в Visual Studio позволяют создавать. [EDMX-файл](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) из базы данных или графической модели, а затем обновляет этот файл при изменении базы данных или модели.</span><span class="sxs-lookup"><span data-stu-id="ca4dd-105">The Entity Data Model Tools in Visual Studio allow you to create an .[edmx file](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) from a database or a graphical model and then update that file when either the database or model changes.</span></span>  
  
 <span data-ttu-id="ca4dd-106">Начиная с версии 4.1 платформы Entity Framework модель можно также создавать программно с помощью шаблона разработки Code First.</span><span class="sxs-lookup"><span data-stu-id="ca4dd-106">Starting with the Entity Framework 4.1 you can also create a model programmatically using Code First development.</span></span> <span data-ttu-id="ca4dd-107">Шаблон разработки Code First имеет два различных сценария.</span><span class="sxs-lookup"><span data-stu-id="ca4dd-107">There are two different scenarios for Code First development.</span></span> <span data-ttu-id="ca4dd-108">В обоих случаях разработчик определяет модель, задавая в коде определения классов .NET Framework, а затем выборочно определяет дополнительные сопоставления или конфигурации с помощью заметок к данным или fluent API.</span><span class="sxs-lookup"><span data-stu-id="ca4dd-108">In both cases, the developer defines a model by coding .NET Framework class definitions, and then optionally specifies additional mapping or configuration by using Data Annotations or the fluent API.</span></span>  
  
 <span data-ttu-id="ca4dd-109">Дополнительные сведения см. в разделе [Создание модели](/ef/ef6/modeling/).</span><span class="sxs-lookup"><span data-stu-id="ca4dd-109">For more information, see [Creating a Model](/ef/ef6/modeling/).</span></span>  
  
 <span data-ttu-id="ca4dd-110">Также можно использовать генератор EDM, который входит в состав платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca4dd-110">You can also use the EDM Generator, which is included with the .NET Framework.</span></span> <span data-ttu-id="ca4dd-111">Программа EdmGen.exe формирует файлы языка CSDL, SSDL и MSL на основе существующего источника данных.</span><span class="sxs-lookup"><span data-stu-id="ca4dd-111">The EdmGen.exe generates the .csdl, .ssdl, and .msl files from an existing data source.</span></span> <span data-ttu-id="ca4dd-112">Можно также вручную создать содержимое модели и сопоставления.</span><span class="sxs-lookup"><span data-stu-id="ca4dd-112">You can also manually create the model and mapping content.</span></span> <span data-ttu-id="ca4dd-113">Дополнительные сведения см. в разделе [генератор EDM (EdmGen.exe)](edm-generator-edmgen-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ca4dd-113">For more information, see [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md).</span></span>
