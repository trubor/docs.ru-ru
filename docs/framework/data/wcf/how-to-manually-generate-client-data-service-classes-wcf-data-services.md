---
description: Дополнительные сведения см. в статье как вручную создавать классы службы данных клиента (службы данных WCF)
title: Практическое руководство. Создание клиентских классов служб данных вручную (службы данных WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, client library
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
ms.openlocfilehash: 6fe878e1177055540a29fb84252eddaa4d97e536
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765208"
---
# <a name="how-to-manually-generate-client-data-service-classes-wcf-data-services"></a><span data-ttu-id="8bbca-103">Практическое руководство. Создание клиентских классов служб данных вручную (службы данных WCF)</span><span class="sxs-lookup"><span data-stu-id="8bbca-103">How to: Manually Generate Client Data Service Classes (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="8bbca-104">Службы данных WCF интегрируется с Visual Studio, позволяя автоматически создавать классы клиентских служб данных при использовании диалогового окна **Добавление ссылки на службу** для добавления ссылки на службу данных в проекте Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8bbca-104">WCF Data Services integrates with Visual Studio to enable you to automatically generate client data service classes when you use the **Add Service Reference** dialog box to add a reference to a data service in a Visual Studio project.</span></span> <span data-ttu-id="8bbca-105">Дополнительные сведения см. [в разделе инструкции. Добавление ссылки на службу данных](how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8bbca-105">For more information, see [How to: Add a Data Service Reference](how-to-add-a-data-service-reference-wcf-data-services.md).</span></span> <span data-ttu-id="8bbca-106">Эти же клиентские классы службы данных можно сформировать и вручную с помощью программы для формирования кода `DataSvcUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="8bbca-106">You can also manually generate the same client data service classes by using the code-generation tool, `DataSvcUtil.exe`.</span></span> <span data-ttu-id="8bbca-107">Это средство, которое входит в состав службы данных WCF, создает классы платформа .NET Framework из определения службы данных.</span><span class="sxs-lookup"><span data-stu-id="8bbca-107">This tool, which is included with WCF Data Services, generates .NET Framework classes from the data service definition.</span></span> <span data-ttu-id="8bbca-108">Она также может использоваться для формирования классов службы данных из файла концептуальной модели (CSDL) и из файла EDMX, представляющего модель Entity Framework в проекте Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8bbca-108">It can also be used to generate data service classes from the conceptual model (.csdl) file and from the .edmx file that represents an Entity Framework model in a Visual Studio project.</span></span>

 <span data-ttu-id="8bbca-109">Пример в этом разделе создает клиентские классы службы данных на основе образца службы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="8bbca-109">The example in this topic creates client data service classes based on the Northwind sample data service.</span></span> <span data-ttu-id="8bbca-110">Эта служба создается при завершении [краткого руководства по службы данных WCF](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8bbca-110">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="8bbca-111">Некоторые примеры в этом разделе требуют наличия файла концептуальной модели для модели Northwind.</span><span class="sxs-lookup"><span data-stu-id="8bbca-111">Some examples in this topic require the conceptual model file for the Northwind model.</span></span> <span data-ttu-id="8bbca-112">Дополнительные сведения см. в разделе [инструкции. использование EdmGen.exe для создания файлов модели и сопоставления](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="8bbca-112">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span> <span data-ttu-id="8bbca-113">Некоторые примеры в этом разделе требуют наличия файла EDMX для модели Northwind.</span><span class="sxs-lookup"><span data-stu-id="8bbca-113">Some examples in this topic require the .edmx file for the Northwind model.</span></span> <span data-ttu-id="8bbca-114">Дополнительные сведения см. в разделе [Общие сведения о файле EDMX](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8bbca-114">For more information, see [.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)).</span></span>

### <a name="to-generate-c-classes-that-support-data-binding"></a><span data-ttu-id="8bbca-115">Формирование классов C#, поддерживающих привязку данных</span><span class="sxs-lookup"><span data-stu-id="8bbca-115">To generate C# classes that support data binding</span></span>

- <span data-ttu-id="8bbca-116">Выполните в командной строке следующую команду (введя ее без разрывов строк):</span><span class="sxs-lookup"><span data-stu-id="8bbca-116">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="8bbca-117">Необходимо заменить значение, передаваемое в параметре `/uri:`, на URI имеющегося экземпляра образца службы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="8bbca-117">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-that-support-data-binding"></a><span data-ttu-id="8bbca-118">Формирование классов Visual Basic, поддерживающих привязку данных</span><span class="sxs-lookup"><span data-stu-id="8bbca-118">To generate Visual Basic classes that support data binding</span></span>

- <span data-ttu-id="8bbca-119">Выполните в командной строке следующую команду (введя ее без разрывов строк):</span><span class="sxs-lookup"><span data-stu-id="8bbca-119">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="8bbca-120">Необходимо заменить значение, передаваемое в параметре `/uri:`, на URI имеющегося экземпляра образца службы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="8bbca-120">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-service-uri"></a><span data-ttu-id="8bbca-121">Формирование классов C# на основе URI службы</span><span class="sxs-lookup"><span data-stu-id="8bbca-121">To generate C# classes based on the service URI</span></span>

- <span data-ttu-id="8bbca-122">Выполните в командной строке следующую команду (введя ее без разрывов строк):</span><span class="sxs-lookup"><span data-stu-id="8bbca-122">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="8bbca-123">Необходимо заменить значение, передаваемое в параметре `/uri:`, на URI имеющегося экземпляра образца службы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="8bbca-123">You must replace the value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-visual-basic-classes-based-on-the-service-uri"></a><span data-ttu-id="8bbca-124">Формирование классов Visual Basic на основе URI службы</span><span class="sxs-lookup"><span data-stu-id="8bbca-124">To generate Visual Basic classes based on the service URI</span></span>

- <span data-ttu-id="8bbca-125">Выполните в командной строке следующую команду (введя ее без разрывов строк):</span><span class="sxs-lookup"><span data-stu-id="8bbca-125">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc
    ```

    > [!NOTE]
    > <span data-ttu-id="8bbca-126">Необходимо заменить значение, передаваемое в параметре `/uri:`, на URI имеющегося экземпляра образца службы данных Northwind.</span><span class="sxs-lookup"><span data-stu-id="8bbca-126">You must replace value supplied to the `/uri:` parameter with the URI of your instance of the Northwind sample data service.</span></span>

### <a name="to-generate-c-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="8bbca-127">Формирование классов C# на основе файла концептуальной модели (CSDL)</span><span class="sxs-lookup"><span data-stu-id="8bbca-127">To generate C# classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="8bbca-128">Выполните в командной строке следующую команду (введя ее без разрывов строк):</span><span class="sxs-lookup"><span data-stu-id="8bbca-128">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-conceptual-model-file-csdl"></a><span data-ttu-id="8bbca-129">Формирование классов Visual Basic на основе файла концептуальной модели (CSDL)</span><span class="sxs-lookup"><span data-stu-id="8bbca-129">To generate Visual Basic classes based on the conceptual model file (CSDL)</span></span>

- <span data-ttu-id="8bbca-130">Выполните в командной строке следующую команду (введя ее без разрывов строк):</span><span class="sxs-lookup"><span data-stu-id="8bbca-130">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb
    ```

### <a name="to-generate-c-classes-based-on-the-edmx-file"></a><span data-ttu-id="8bbca-131">Формирование классов C# на основе файла EDMX</span><span class="sxs-lookup"><span data-stu-id="8bbca-131">To generate C# classes based on the .edmx file</span></span>

- <span data-ttu-id="8bbca-132">Выполните в командной строке следующую команду (введя ее без разрывов строк):</span><span class="sxs-lookup"><span data-stu-id="8bbca-132">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs
    ```

### <a name="to-generate-visual-basic-classes-based-on-the-edmx-file"></a><span data-ttu-id="8bbca-133">Формирование классов Visual Basic на основе файла EDMX</span><span class="sxs-lookup"><span data-stu-id="8bbca-133">To generate Visual Basic classes based on the .edmx file</span></span>

- <span data-ttu-id="8bbca-134">Выполните в командной строке следующую команду (введя ее без разрывов строк):</span><span class="sxs-lookup"><span data-stu-id="8bbca-134">At the command prompt, execute the following command without line breaks:</span></span>

    ```console
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb
    ```

## <a name="see-also"></a><span data-ttu-id="8bbca-135">См. также</span><span class="sxs-lookup"><span data-stu-id="8bbca-135">See also</span></span>

- [<span data-ttu-id="8bbca-136">Создание библиотеки клиентов службы данных</span><span class="sxs-lookup"><span data-stu-id="8bbca-136">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)
- [<span data-ttu-id="8bbca-137">Практическое руководство. Добавление ссылки на службу данных</span><span class="sxs-lookup"><span data-stu-id="8bbca-137">How to: Add a Data Service Reference</span></span>](how-to-add-a-data-service-reference-wcf-data-services.md)
- [<span data-ttu-id="8bbca-138">Служебная программа клиента служб данных WCF (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="8bbca-138">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>](wcf-data-service-client-utility-datasvcutil-exe.md)
