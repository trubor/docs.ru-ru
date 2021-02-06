---
description: Дополнительные сведения см. в статье как определить строку подключения.
title: Практическое руководство. Определение строки соединения
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: 104264299e597bc142a689aa83f3207765d18c67
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650824"
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="81c29-103">Практическое руководство. Определение строки соединения</span><span class="sxs-lookup"><span data-stu-id="81c29-103">How to: Define the Connection String</span></span>

<span data-ttu-id="81c29-104">В этом разделе показано, как определить строку соединения, используемую при подключении к концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="81c29-104">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="81c29-105">Этот раздел основан на концептуальной модели [AdventureWorks Sales](/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="81c29-105">This topic is based on the [AdventureWorks Sales](/previous-versions/dotnet/netframework-4.0/bb387147(v=vs.100)) conceptual model.</span></span> <span data-ttu-id="81c29-106">Модель AdventureWorks Sales используется во всех разделах документации платформы Entity Framework, описывающих выполнение задач.</span><span class="sxs-lookup"><span data-stu-id="81c29-106">The AdventureWorks Sales Model is used throughout the task-related topics in the Entity Framework documentation.</span></span> <span data-ttu-id="81c29-107">В этом разделе предполагается, что вы уже настроили Entity Framework и определили модель AdventureWorks Sales.</span><span class="sxs-lookup"><span data-stu-id="81c29-107">This topic assumes that you have already configured the Entity Framework and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="81c29-108">Дополнительные сведения см. в разделе [руководство. Определение файлов модели и сопоставления вручную](/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="81c29-108">For more information, see [How to: Manually Define the Model and Mapping Files](/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).</span></span> <span data-ttu-id="81c29-109">Процедуры, описанные в этом разделе, также включены в [руководство по ручной настройке проекта Entity Framework](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="81c29-109">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="81c29-110">При использовании мастера EDM в проекте Visual Studio он автоматически создает EDMX-файл и настраивает проект для использования Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="81c29-110">If you use the Entity Data Model Wizard in a Visual Studio project, it automatically generates an .edmx file and configures the project to use the Entity Framework.</span></span> <span data-ttu-id="81c29-111">Дополнительные сведения см. в разделе [инструкции. Использование мастера EDM](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="81c29-111">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

## <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="81c29-112">Определение строки соединения Entity Framework</span><span class="sxs-lookup"><span data-stu-id="81c29-112">To define the Entity Framework connection string</span></span>

- <span data-ttu-id="81c29-113">Откройте файл конфигурации приложения (app.config) и добавьте следующую строку соединения:</span><span class="sxs-lookup"><span data-stu-id="81c29-113">Open the project's application configuration file (app.config) and add the following connection string:</span></span>

```xml
<connectionStrings>
    <add name="AdventureWorksEntities"
         connectionString="metadata=.\AdventureWorks.csdl|.\AdventureWorks.ssdl|.\AdventureWorks.msl;
         provider=System.Data.SqlClient;provider connection string='Data Source=localhost;
         Initial Catalog=AdventureWorks;Integrated Security=True;Connection Timeout=60;
         multipleactiveresultsets=true'" providerName="System.Data.EntityClient" />
</connectionStrings>
```

<span data-ttu-id="81c29-114">Если в проекте нет файла конфигурации приложения, его можно добавить, выбрав в меню **проект** пункт **Добавить новый элемент** , выбрав категорию **Общие** , выбрав **файл конфигурации приложения**, а затем нажав кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="81c29-114">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>

## <a name="see-also"></a><span data-ttu-id="81c29-115">См. также</span><span class="sxs-lookup"><span data-stu-id="81c29-115">See also</span></span>

- <span data-ttu-id="81c29-116">[Краткое руководство](/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="81c29-116">[Quickstart](/previous-versions/dotnet/netframework-4.0/bb399182(v=vs.100))</span></span>
- <span data-ttu-id="81c29-117">[Как создать новый EDMX-файл](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="81c29-117">[How to: Create a New .edmx File](/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))</span></span>
- <span data-ttu-id="81c29-118">[Средства работы с моделью EDM ADO.NET](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="81c29-118">[ADO.NET Entity Data Model  Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
