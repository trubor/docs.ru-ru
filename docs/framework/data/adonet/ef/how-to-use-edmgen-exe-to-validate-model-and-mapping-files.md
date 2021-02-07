---
description: Дополнительные сведения см. в статье как использовать EdmGen.exe для проверки файлов модели и сопоставления.
title: Практическое руководство. Использование EdmGen.exe для проверки файлов модели и сопоставления
ms.date: 03/30/2017
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
ms.openlocfilehash: e729ea36b7ff17dc318f4488a669b968161aea8b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697352"
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="15e6c-103">Практическое руководство. Использование EdmGen.exe для проверки файлов модели и сопоставления</span><span class="sxs-lookup"><span data-stu-id="15e6c-103">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>

<span data-ttu-id="15e6c-104">В этом разделе показано, как использовать средство [генератора EDM (EdmGen.exe)](edm-generator-edmgen-exe.md) для проверки файлов модели и сопоставления.</span><span class="sxs-lookup"><span data-stu-id="15e6c-104">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="15e6c-105">Дополнительные сведения см. в разделе [EDM](../entity-data-model.md).</span><span class="sxs-lookup"><span data-stu-id="15e6c-105">For more information, see [Entity Data Model](../entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="15e6c-106">Проверка модели School при помощи программы EdmGen.exe</span><span class="sxs-lookup"><span data-stu-id="15e6c-106">To validate the School model using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="15e6c-107">Создайте базу данных School.</span><span class="sxs-lookup"><span data-stu-id="15e6c-107">Create the School database.</span></span> <span data-ttu-id="15e6c-108">Дополнительные сведения см. [в разделе Создание образца базы данных School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="15e6c-108">For more information, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="15e6c-109">Сформируйте модель School.</span><span class="sxs-lookup"><span data-stu-id="15e6c-109">Generate the School model.</span></span> <span data-ttu-id="15e6c-110">Дополнительные сведения см. в разделе [инструкции. использование EdmGen.exe для создания файлов модели и сопоставления](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="15e6c-110">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="15e6c-111">Выполните в командной строке следующую команду (введя ее без разрывов строк):</span><span class="sxs-lookup"><span data-stu-id="15e6c-111">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="15e6c-112">См. также</span><span class="sxs-lookup"><span data-stu-id="15e6c-112">See also</span></span>

- <span data-ttu-id="15e6c-113">[Практическое руководство. Настройка проекта Entity Framework вручную](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="15e6c-113">[How to: Manually Configure an Entity Framework Project](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="15e6c-114">[Средства EDM ADO.NET](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="15e6c-114">[ADO.NET Entity Data Model Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="15e6c-115">[Практическое руководство. Предварительное создание представлений для повышения производительности запросов](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="15e6c-115">[How to: Pre-Generate Views to Improve Query Performance](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="15e6c-116">Практическое руководство. Использование EdmGen.exe для создания кода объектного уровня</span><span class="sxs-lookup"><span data-stu-id="15e6c-116">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](how-to-use-edmgen-exe-to-generate-object-layer-code.md)
