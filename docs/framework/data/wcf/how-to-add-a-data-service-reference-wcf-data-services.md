---
description: 'Дополнительные сведения: как добавить ссылку на службу данных (службы данных WCF)'
title: Практическое руководство. Добавление ссылки на службу данных (службы данных WCF)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 907ad9a7dc3710a6e565de55c74a0d279d20e159
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765758"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="70fb4-103">Как добавить ссылку на службу данных (службы данных WCF)</span><span class="sxs-lookup"><span data-stu-id="70fb4-103">How to: Add a data service reference (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="70fb4-104">Можно использовать диалоговое окно **Добавление ссылки на службу** в Visual Studio, чтобы добавить ссылку на службы данных WCF.</span><span class="sxs-lookup"><span data-stu-id="70fb4-104">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to WCF Data Services.</span></span> <span data-ttu-id="70fb4-105">Это позволяет упростить доступ к службе данных в клиентском приложении, разрабатываемом в среде Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="70fb4-105">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="70fb4-106">По завершении этой процедуры формируются классы данных на основе метаданных, полученных от службы данных.</span><span class="sxs-lookup"><span data-stu-id="70fb4-106">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="70fb4-107">Дополнительные сведения см. [в разделе Создание клиентской библиотеки службы данных](generating-the-data-service-client-library-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="70fb4-107">For more information, see [Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md).</span></span>

## <a name="add-a-data-service-reference"></a><span data-ttu-id="70fb4-108">Добавить ссылку на службу данных</span><span class="sxs-lookup"><span data-stu-id="70fb4-108">Add a data service reference</span></span>

1. <span data-ttu-id="70fb4-109">Если служба данных не является частью решения и пока не запущена, запустите ее и отметьте ее URI. (Необязательно.)</span><span class="sxs-lookup"><span data-stu-id="70fb4-109">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>

2. <span data-ttu-id="70fb4-110">В **Обозреватель решений** в Visual Studio щелкните правой кнопкой мыши клиентский проект и выберите **Добавить**  >  **ссылку на службу**.</span><span class="sxs-lookup"><span data-stu-id="70fb4-110">In Visual Studio, in **Solution Explorer**, right-click the client project and then select **Add** > **Service Reference**.</span></span>

3. <span data-ttu-id="70fb4-111">Если служба данных является частью текущего решения, нажмите кнопку **обнаружить**.</span><span class="sxs-lookup"><span data-stu-id="70fb4-111">If the data service is part of the current solution, click **Discover**.</span></span>

     <span data-ttu-id="70fb4-112">-или-</span><span class="sxs-lookup"><span data-stu-id="70fb4-112">-or-</span></span>

     <span data-ttu-id="70fb4-113">В текстовом поле **адрес** введите базовый URL-адрес службы данных, например `http://localhost:1234/Northwind.svc` , и нажмите кнопку **Go**.</span><span class="sxs-lookup"><span data-stu-id="70fb4-113">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>

4. <span data-ttu-id="70fb4-114">Выберите **ОК**.</span><span class="sxs-lookup"><span data-stu-id="70fb4-114">Select **OK**.</span></span>

     <span data-ttu-id="70fb4-115">В проект добавляется новый файл кода, содержащий классы данных, которые могут получать доступ к ресурсам службы данных и взаимодействовать с ними.</span><span class="sxs-lookup"><span data-stu-id="70fb4-115">A new code file that contains the data classes that can access and interact with data service resources is added to the project.</span></span>

## <a name="see-also"></a><span data-ttu-id="70fb4-116">См. также</span><span class="sxs-lookup"><span data-stu-id="70fb4-116">See also</span></span>

- [<span data-ttu-id="70fb4-117">Краткое руководство</span><span class="sxs-lookup"><span data-stu-id="70fb4-117">Quickstart</span></span>](quickstart-wcf-data-services.md)
