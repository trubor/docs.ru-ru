---
title: Практическое руководство. Создание сборок взаимодействия из библиотек типов
description: Создайте сборки взаимодействия из библиотек типов. Используйте программу импорта библиотек типов (Tlbimp.exe) для преобразования коклассов и интерфейсов из библиотеки типов COM в метаданные.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
ms.openlocfilehash: 3146d607392a590974f452e06eb5a8b125e58e69
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236368"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="61bdc-104">Практическое руководство. Создание сборок взаимодействия из библиотек типов</span><span class="sxs-lookup"><span data-stu-id="61bdc-104">How to: Generate Interop Assemblies from Type Libraries</span></span>

<span data-ttu-id="61bdc-105">[Программа импорта библиотек типов (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) — это средство командной строки, которое преобразует коклассы и интерфейсы, содержащиеся в библиотеке типов COM, в метаданные.</span><span class="sxs-lookup"><span data-stu-id="61bdc-105">The [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="61bdc-106">Это средство автоматически создает сборку взаимодействия и пространство имен для сведений о типе.</span><span class="sxs-lookup"><span data-stu-id="61bdc-106">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="61bdc-107">После того как метаданные класса стали доступными, управляемые клиенты могут создавать экземпляры типа COM и вызывать его методы, как если бы это был экземпляр .NET.</span><span class="sxs-lookup"><span data-stu-id="61bdc-107">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="61bdc-108">Средство Tlbimp.exe преобразует всю библиотеку типов в метаданные за один раз и не может создать сведения о типах для подмножества типов, определенных в библиотеке типов.</span><span class="sxs-lookup"><span data-stu-id="61bdc-108">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="61bdc-109">Создание сборки взаимодействия из библиотеки типов</span><span class="sxs-lookup"><span data-stu-id="61bdc-109">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="61bdc-110">Используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="61bdc-110">Use the following command:</span></span>  
  
     <span data-ttu-id="61bdc-111">**tlbimp** \<*type-library-file*></span><span class="sxs-lookup"><span data-stu-id="61bdc-111">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="61bdc-112">При указании параметра **/out:** создается сборка взаимодействия с измененным именем, например LOANLib.dll.</span><span class="sxs-lookup"><span data-stu-id="61bdc-112">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="61bdc-113">Изменение имени сборки взаимодействия помогает отличить эту сборку от исходного файла DLL COM и избежать возможных проблем с повторяющимися именами.</span><span class="sxs-lookup"><span data-stu-id="61bdc-113">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61bdc-114">Пример</span><span class="sxs-lookup"><span data-stu-id="61bdc-114">Example</span></span>  

 <span data-ttu-id="61bdc-115">Следующая команда создает сборку Loanlib.dll в пространстве имен `Loanlib`.</span><span class="sxs-lookup"><span data-stu-id="61bdc-115">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```console  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="61bdc-116">Следующая команда создает сборку взаимодействия с измененным именем (LOANLib.dll).</span><span class="sxs-lookup"><span data-stu-id="61bdc-116">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```console  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="61bdc-117">См. также</span><span class="sxs-lookup"><span data-stu-id="61bdc-117">See also</span></span>

- [<span data-ttu-id="61bdc-118">Импорт библиотеки типов в виде сборки</span><span class="sxs-lookup"><span data-stu-id="61bdc-118">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="61bdc-119">Предоставление COM-компонентов платформе .NET Framework</span><span class="sxs-lookup"><span data-stu-id="61bdc-119">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
