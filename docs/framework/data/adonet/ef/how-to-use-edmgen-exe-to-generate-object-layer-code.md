---
description: Дополнительные сведения см. в статье как использовать EdmGen.exe для создания кода Object-Layer
title: Практическое руководство. Использование EdmGen.exe для создания кода объектного уровня
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 1c1f614247f10c8819709b9494fb1ec04271b634
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697469"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="bcc29-103">Практическое руководство. Использование EdmGen.exe для создания кода объектного уровня</span><span class="sxs-lookup"><span data-stu-id="bcc29-103">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>

<span data-ttu-id="bcc29-104">В этом разделе показано, как использовать средство [генератора EDM (EdmGen.exe)](edm-generator-edmgen-exe.md) для создания кода уровня объекта на основе CSDL-файла.</span><span class="sxs-lookup"><span data-stu-id="bcc29-104">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="bcc29-105">Создание кода уровня объекта для модели School в проекте Visual Basic с помощью EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="bcc29-105">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="bcc29-106">Создайте базу данных School.</span><span class="sxs-lookup"><span data-stu-id="bcc29-106">Create the School database.</span></span> <span data-ttu-id="bcc29-107">Дополнительные сведения см. [в разделе Создание образца базы данных School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bcc29-107">For more information, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="bcc29-108">Создайте модель School или получите файл School.csdl.</span><span class="sxs-lookup"><span data-stu-id="bcc29-108">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="bcc29-109">Дополнительные сведения см. в разделе [инструкции. использование EdmGen.exe для создания файлов модели и сопоставления](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="bcc29-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="bcc29-110">Выполните в командной строке следующую команду (введя ее без разрывов строк):</span><span class="sxs-lookup"><span data-stu-id="bcc29-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="bcc29-111">Создание кода уровня объектов для модели School в проекте С# с помощью программы EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="bcc29-111">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="bcc29-112">Создайте базу данных School.</span><span class="sxs-lookup"><span data-stu-id="bcc29-112">Create the School database.</span></span> <span data-ttu-id="bcc29-113">Дополнительные сведения см. [в разделе Создание образца базы данных School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bcc29-113">For more information, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="bcc29-114">Создайте модель School или получите файл School.csdl.</span><span class="sxs-lookup"><span data-stu-id="bcc29-114">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="bcc29-115">Дополнительные сведения см. в разделе [инструкции. использование EdmGen.exe для создания файлов модели и сопоставления](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="bcc29-115">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="bcc29-116">Выполните в командной строке следующую команду (введя ее без разрывов строк):</span><span class="sxs-lookup"><span data-stu-id="bcc29-116">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bcc29-117">См. также</span><span class="sxs-lookup"><span data-stu-id="bcc29-117">See also</span></span>

- [<span data-ttu-id="bcc29-118">Моделирование и сопоставление</span><span class="sxs-lookup"><span data-stu-id="bcc29-118">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="bcc29-119">[Практическое руководство. Настройка проекта Entity Framework вручную](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bcc29-119">[How to: Manually Configure an Entity Framework Project](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="bcc29-120">[Средства работы с моделью EDM ADO.NET](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bcc29-120">[ADO.NET Entity Data Model  Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="bcc29-121">[Практическое руководство. Предварительное создание представлений для повышения производительности запросов](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bcc29-121">[How to: Pre-Generate Views to Improve Query Performance](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="bcc29-122">Практическое руководство. Использование EdmGen.exe для создания файлов модели и сопоставления</span><span class="sxs-lookup"><span data-stu-id="bcc29-122">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
