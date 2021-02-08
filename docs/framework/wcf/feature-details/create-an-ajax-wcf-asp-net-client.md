---
description: Дополнительные сведения см. в статье Создание AJAX-Enabled службы WCF и клиента ASP.NET, обращающегося к службе.
title: Создание AJAX-Enabled службы WCF и клиента ASP.NET в Visual Studio
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 59b0cab9b28dd68b27529b5d880138cc283144a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780353"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="0816f-103">Практическое руководство. Создание службы WCF с поддержкой AJAX и клиента ASP.NET для обращения к службе</span><span class="sxs-lookup"><span data-stu-id="0816f-103">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>

<span data-ttu-id="0816f-104">В этом разделе показано, как использовать Visual Studio для создания службы Windows Communication Foundation (WCF) с поддержкой AJAX и клиента ASP.NET, обращающегося к службе.</span><span class="sxs-lookup"><span data-stu-id="0816f-104">This topic shows how to use Visual Studio to create an AJAX-enabled Windows Communication Foundation (WCF) service and an ASP.NET client that accesses the service.</span></span>

## <a name="create-an-aspnet-web-app"></a><span data-ttu-id="0816f-105">Создание веб-приложения ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0816f-105">Create an ASP.NET web app</span></span>

1. <span data-ttu-id="0816f-106">Запустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0816f-106">Open Visual Studio.</span></span>

1. <span data-ttu-id="0816f-107">В меню **файл** выберите пункт **создать**  >  **проект** .</span><span class="sxs-lookup"><span data-stu-id="0816f-107">From the **File** menu, select **New** > **Project**</span></span>

1. <span data-ttu-id="0816f-108">В диалоговом окне **Новый проект** разверните узел **установленная**  >    >  **веб-** Категория Visual C#, а затем выберите **ASP.NET веб-приложение (платформа .NET Framework)**.</span><span class="sxs-lookup"><span data-stu-id="0816f-108">In the **New Project** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select **ASP.NET Web Application (.NET Framework)**.</span></span>

1. <span data-ttu-id="0816f-109">Присвойте проекту имя **сандвичсервицес** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="0816f-109">Name the Project **SandwichServices** and click **OK**.</span></span>

1. <span data-ttu-id="0816f-110">В диалоговом окне **новое веб-приложение ASP.NET** выберите **пусто** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="0816f-110">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

   ![Диалоговое окно типа веб-приложения ASP.NET в Visual Studio](./media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a><span data-ttu-id="0816f-112">Добавление веб-формы</span><span class="sxs-lookup"><span data-stu-id="0816f-112">Add a web form</span></span>

1. <span data-ttu-id="0816f-113">Щелкните правой кнопкой мыши проект сандвичсервицес в **Обозреватель решений** и выберите команду **Добавить**  >  **новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="0816f-113">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="0816f-114">В диалоговом окне **Добавление нового элемента** разверните узел **установленная**  >    >  **веб-** Категория Visual C#, а затем выберите шаблон **веб-форма** .</span><span class="sxs-lookup"><span data-stu-id="0816f-114">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **Web Form** template.</span></span>

1. <span data-ttu-id="0816f-115">Примите имя по умолчанию (**WebForm1**) и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="0816f-115">Accept the default name (**WebForm1**), and then select **Add**.</span></span>

   <span data-ttu-id="0816f-116">В представлении **исходного кода** откроется *WebForm1. aspx* .</span><span class="sxs-lookup"><span data-stu-id="0816f-116">*WebForm1.aspx* opens in **Source** view.</span></span>

1. <span data-ttu-id="0816f-117">Добавьте в теги следующую разметку **\<body>** :</span><span class="sxs-lookup"><span data-stu-id="0816f-117">Add the following markup inside the **\<body>** tags:</span></span>

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a><span data-ttu-id="0816f-118">Создание службы WCF с поддержкой AJAX</span><span class="sxs-lookup"><span data-stu-id="0816f-118">Create an AJAX-enabled WCF service</span></span>

1. <span data-ttu-id="0816f-119">Щелкните правой кнопкой мыши проект сандвичсервицес в **Обозреватель решений** и выберите команду **Добавить**  >  **новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="0816f-119">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="0816f-120">В диалоговом окне **Добавление нового элемента** разверните категорию **установленные**  >  **Visual C#**  >  **Web** , а затем выберите шаблон **Служба WCF (с поддержкой AJAX)** .</span><span class="sxs-lookup"><span data-stu-id="0816f-120">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **WCF Service (AJAX-enabled)** template.</span></span>

   ![Шаблон элемента службы WCF (с поддержкой AJAX) в Visual Studio](./media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. <span data-ttu-id="0816f-122">Назовите службу **костсервице** и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="0816f-122">Name the service **CostService** and then select **Add**.</span></span>

   <span data-ttu-id="0816f-123">*CostService.svc.CS* откроется в редакторе.</span><span class="sxs-lookup"><span data-stu-id="0816f-123">*CostService.svc.cs* opens in the editor.</span></span>

1. <span data-ttu-id="0816f-124">Реализуйте операцию в службе.</span><span class="sxs-lookup"><span data-stu-id="0816f-124">Implement the operation in the service.</span></span> <span data-ttu-id="0816f-125">Добавьте следующий метод в класс Костсервице для вычисления стоимости количества бутерброды:</span><span class="sxs-lookup"><span data-stu-id="0816f-125">Add the following method to the CostService class to calculate the cost of a quantity of sandwiches:</span></span>

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a><span data-ttu-id="0816f-126">Настройка клиента для доступа к службе</span><span class="sxs-lookup"><span data-stu-id="0816f-126">Configure the client to access the service</span></span>

1. <span data-ttu-id="0816f-127">Откройте файл *WebForm1. aspx* и выберите представление **конструктора** .</span><span class="sxs-lookup"><span data-stu-id="0816f-127">Open the *WebForm1.aspx* file and select the **Design** view.</span></span>

2. <span data-ttu-id="0816f-128">В меню **вид** выберите пункт **область элементов**.</span><span class="sxs-lookup"><span data-stu-id="0816f-128">From the **View** menu, select **Toolbox**.</span></span>

3. <span data-ttu-id="0816f-129">Разверните узел **расширения AJAX** и перетащите **ScriptManager** на форму.</span><span class="sxs-lookup"><span data-stu-id="0816f-129">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** onto the form.</span></span>

4. <span data-ttu-id="0816f-130">В представлении **исходного** кода добавьте следующий код между **\<ScriptManager>** тегами, чтобы указать путь к службе WCF:</span><span class="sxs-lookup"><span data-stu-id="0816f-130">Back in the **Source** view, add the following code between the **\<ScriptManager>** tags to specify the path to the WCF service:</span></span>

    ```xml
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

5. <span data-ttu-id="0816f-131">Добавьте код для функции JavaScript `Calculate()` .</span><span class="sxs-lookup"><span data-stu-id="0816f-131">Add the code for the JavaScript function `Calculate()`.</span></span> <span data-ttu-id="0816f-132">Поместите следующий код в раздел **head** веб-формы:</span><span class="sxs-lookup"><span data-stu-id="0816f-132">Place the following code in the **head** section of the web form:</span></span>

    ```html
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
    ```

   <span data-ttu-id="0816f-133">Этот код вызывает метод Костсервице для вычисления цены на три бутерброды, а затем отображает результат в диапазоне с именем **аддитионресулт**.</span><span class="sxs-lookup"><span data-stu-id="0816f-133">This code calls the method of CostService to calculate the price for three sandwiches, and then displays the result in the span called **additionResult**.</span></span>

## <a name="run-the-program"></a><span data-ttu-id="0816f-134">Запуск программы</span><span class="sxs-lookup"><span data-stu-id="0816f-134">Run the program</span></span>

<span data-ttu-id="0816f-135">Убедитесь, что в элементе *WebForm1. aspx* установлен фокус, а затем нажмите кнопку **запустить** , чтобы запустить веб-клиент.</span><span class="sxs-lookup"><span data-stu-id="0816f-135">Make sure that *WebForm1.aspx* has focus, and then press **Start** button to launch the web client.</span></span> <span data-ttu-id="0816f-136">Кнопка имеет зеленый треугольник и говорит нечто вроде **IIS Express (Microsoft ребр)**.</span><span class="sxs-lookup"><span data-stu-id="0816f-136">The button has a green triangle and says something like **IIS Express (Microsoft Edge)**.</span></span> <span data-ttu-id="0816f-137">Можно также нажать клавишу <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="0816f-137">Or, you can press <kbd>F5</kbd>.</span></span> <span data-ttu-id="0816f-138">Чтобы создать ожидаемый результат "3,75", нажмите кнопку **Цена, равную 3 бутерброды** .</span><span class="sxs-lookup"><span data-stu-id="0816f-138">Click the **Price of 3 sandwiches** button to generate the expected output of "3.75".</span></span>

## <a name="example"></a><span data-ttu-id="0816f-139">Пример</span><span class="sxs-lookup"><span data-stu-id="0816f-139">Example</span></span>

<span data-ttu-id="0816f-140">Ниже приведен полный код в файле *CostService.svc.CS* :</span><span class="sxs-lookup"><span data-stu-id="0816f-140">The following is the full code in the *CostService.svc.cs* file:</span></span>

```csharp
using System.ServiceModel;
using System.ServiceModel.Activation;

namespace SandwichServices
{
    [ServiceContract(Namespace = "")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class CostService
    {
        [OperationContract]
        public double CostOfSandwiches(int quantity)
        {
            return 1.25 * quantity;
        }
    }
}
```

<span data-ttu-id="0816f-141">Ниже приведено полное содержимое страницы *WebForm1. aspx* :</span><span class="sxs-lookup"><span data-stu-id="0816f-141">The following is the full contents of the *WebForm1.aspx* page:</span></span>

```aspx-csharp
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SandwichServices.WebForm1" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
</head>
<body>
    <form id="form1" runat="server">
        <div>
        </div>
        <asp:ScriptManager ID="ScriptManager1" runat="server">
            <Services>
                <asp:ServiceReference Path="~/CostService.svc" />
            </Services>
        </asp:ScriptManager>

        <input type="button" value="Price of 3 sandwiches" onclick="Calculate()" />
        <br />
        <span id="additionResult"></span>
    </form>
</body>
</html>
```
