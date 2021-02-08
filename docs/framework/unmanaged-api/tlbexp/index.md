---
description: 'Узнайте подробнее о: Вспомогательные функции Tlbexp (справочник по неуправляемым API)'
title: Вспомогательные функции Tlbexp (справочник по неуправляемым API)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: 8d5aacbe63d111b0b53f6bc76357a37ee4660d0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646261"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="a0861-103">Вспомогательные функции Tlbexp (справочник по неуправляемым API)</span><span class="sxs-lookup"><span data-stu-id="a0861-103">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>

<span data-ttu-id="a0861-104">[Средство экспорта библиотек типов](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) загружает библиотеку динамической компоновки TlbRef.dll.</span><span class="sxs-lookup"><span data-stu-id="a0861-104">The [Type Library Exporter tool](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="a0861-105">Эта библиотека DLL имеет две вспомогательные функции и интерфейс, который использует средство экспорта в ходе преобразования сборки в библиотеку типов.</span><span class="sxs-lookup"><span data-stu-id="a0861-105">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a0861-106">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="a0861-106">In This Section</span></span>  

 [<span data-ttu-id="a0861-107">Функция GetTypeLibInfo</span><span class="sxs-lookup"><span data-stu-id="a0861-107">GetTypeLibInfo Function</span></span>](gettypelibinfo-function.md)  
 <span data-ttu-id="a0861-108">Предоставляет сведения о локализации и операционной системе для библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="a0861-108">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="a0861-109">Функция LoadTypeLibWithResolver</span><span class="sxs-lookup"><span data-stu-id="a0861-109">LoadTypeLibWithResolver Function</span></span>](loadtypelibwithresolver-function.md)  
 <span data-ttu-id="a0861-110">Загружает библиотеку типов, используя реализацию [интерфейса ITypeLibResolver](itypelibresolver-interface.md) для разрешения указанных библиотек типов.</span><span class="sxs-lookup"><span data-stu-id="a0861-110">Loads a type library by using an implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="a0861-111">Интерфейс ITypeLibResolver</span><span class="sxs-lookup"><span data-stu-id="a0861-111">ITypeLibResolver Interface</span></span>](itypelibresolver-interface.md)  
 <span data-ttu-id="a0861-112">Предоставляет [метод ResolveTypeLib](resolvetypelib-method.md), который возвращает полный путь к библиотеке типов.</span><span class="sxs-lookup"><span data-stu-id="a0861-112">Provides the [ResolveTypeLib method](resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
