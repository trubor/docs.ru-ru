---
description: Дополнительные сведения см. в статье как создать настраиваемый код путем изменения DBML-файла.
title: Практическое руководство. Как генерировать настраиваемый код путем изменения DBML-файла
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 0dd4024b3f6a0ca0583de6bfbdb7463fab14d969
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786008"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="098e5-103">Практическое руководство. Как генерировать настраиваемый код путем изменения DBML-файла</span><span class="sxs-lookup"><span data-stu-id="098e5-103">How to: Generate Customized Code by Modifying a DBML File</span></span>

<span data-ttu-id="098e5-104">Исходный код Visual Basic или C# можно создать из файла метаданных на языке разметки базы данных (. DBML).</span><span class="sxs-lookup"><span data-stu-id="098e5-104">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="098e5-105">Этот способ предоставляет возможность настройки заданного по умолчанию DBML-файла до создания кода сопоставления приложений.</span><span class="sxs-lookup"><span data-stu-id="098e5-105">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="098e5-106">Данная возможность является дополнительной.</span><span class="sxs-lookup"><span data-stu-id="098e5-106">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="098e5-107">Ниже указаны действия, необходимые для выполнения данного процесса.</span><span class="sxs-lookup"><span data-stu-id="098e5-107">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="098e5-108">Создайте DBML-файл.</span><span class="sxs-lookup"><span data-stu-id="098e5-108">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="098e5-109">Для изменения DBML-файла используйте редактор.</span><span class="sxs-lookup"><span data-stu-id="098e5-109">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="098e5-110">Обратите внимание, что DBML-файл должен проверяться на соответствие файлу определения схемы (XSD) [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] файлам. dbml.</span><span class="sxs-lookup"><span data-stu-id="098e5-110">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="098e5-111">Дополнительные сведения см. [в разделе Создание кода в LINQ to SQL](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="098e5-111">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="098e5-112">Создайте исходный код Visual Basic или C#.</span><span class="sxs-lookup"><span data-stu-id="098e5-112">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="098e5-113">В следующих примерах используется средства командной строки SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="098e5-113">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="098e5-114">Дополнительные сведения см. в разделе [SQLMetal.exe (средство создания кода)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="098e5-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="098e5-115">Пример</span><span class="sxs-lookup"><span data-stu-id="098e5-115">Example</span></span>  

 <span data-ttu-id="098e5-116">В следующем коде DBML-файл создается из учебной базы данных "Northwind".</span><span class="sxs-lookup"><span data-stu-id="098e5-116">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="098e5-117">В качестве источника метаданных база данных можно использовать либо имя базы данных, либо имя MDF-файла.</span><span class="sxs-lookup"><span data-stu-id="098e5-117">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```console  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="098e5-118">Пример</span><span class="sxs-lookup"><span data-stu-id="098e5-118">Example</span></span>  

 <span data-ttu-id="098e5-119">Следующий код создает Visual Basic или файл исходного кода C# из DBML-файла.</span><span class="sxs-lookup"><span data-stu-id="098e5-119">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```console
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="098e5-120">См. также</span><span class="sxs-lookup"><span data-stu-id="098e5-120">See also</span></span>

- [<span data-ttu-id="098e5-121">Создание кода в LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="098e5-121">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="098e5-122">SqlMetal.exe (средство создания кода)</span><span class="sxs-lookup"><span data-stu-id="098e5-122">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="098e5-123">Создание модели объектов</span><span class="sxs-lookup"><span data-stu-id="098e5-123">Creating the Object Model</span></span>](creating-the-object-model.md)
