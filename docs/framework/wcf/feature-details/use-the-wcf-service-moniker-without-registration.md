---
description: Дополнительные сведения см. в статье как использовать моникер службы Windows Communication Foundation без регистрации.
title: Практическое руководство. Использование моникера службы Windows Communication Foundation без регистрации
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: ed3ea221bc32c4334f609b6740fa10bb63cb2830
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632390"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a><span data-ttu-id="01892-103">Практическое руководство. Использование моникера службы Windows Communication Foundation без регистрации</span><span class="sxs-lookup"><span data-stu-id="01892-103">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>

<span data-ttu-id="01892-104">Чтобы подключиться к службе Windows Communication Foundation (WCF) и взаимодействовать с ней, клиентское приложение WCF должно иметь сведения об адресе службы, конфигурации привязки и контракте службы.</span><span class="sxs-lookup"><span data-stu-id="01892-104">To connect to and communicate with a Windows Communication Foundation (WCF) service, a WCF client application must have the details of the service address, the binding configuration, and the service contract.</span></span>  
  
 <span data-ttu-id="01892-105">Моникер службы WCF обычно получает требуемый контракт путем выполнения предварительной регистрации требуемых типов атрибутов, но в некоторых случаях это нецелесообразно.</span><span class="sxs-lookup"><span data-stu-id="01892-105">The WCF service moniker typically obtains the required contract through prior registration of the required attribute types, but there might be cases where this is not feasible.</span></span> <span data-ttu-id="01892-106">Вместо регистрации моникер может получать определение контракта в виде документа на языке WSDL - путем использования параметра `wsdl` или с помощью обмена метаданными (MEX), путем использования параметра `mexAddress`.</span><span class="sxs-lookup"><span data-stu-id="01892-106">In place of registration, the moniker can obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document, through the use of the `wsdl` parameter or through Metadata Exchange, through the use of the `mexAddress` parameter.</span></span>  
  
 <span data-ttu-id="01892-107">Это делает возможной реализацию таких сценариев, как распространение электронной таблицы Excel, в которой значения некоторых ячеек вычисляются посредством взаимодействия с веб-службой.</span><span class="sxs-lookup"><span data-stu-id="01892-107">This enables scenarios such as the distribution of an Excel spreadsheet where some of the cell values are calculated through Web service interactions.</span></span> <span data-ttu-id="01892-108">В подобном сценарии может быть нецелесообразным регистрировать сборку контракта службы на всех клиентах, которые могут открывать документ.</span><span class="sxs-lookup"><span data-stu-id="01892-108">In this scenario, it might not be feasible to register the service contract assembly on all clients that might open the document.</span></span> <span data-ttu-id="01892-109">Параметр `wsdl` или параметр `mexAddress` позволяет получить автономное решение.</span><span class="sxs-lookup"><span data-stu-id="01892-109">The `wsdl` parameter or the `mexAddress` parameter enables a self-contained solution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01892-110">Для защиты от изменения запросов и ответов или спуфинга необходимо использовать взаимную проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="01892-110">Mutual authentication must be used to protect against request and response tampering or spoofing.</span></span> <span data-ttu-id="01892-111">В частности, важно, чтобы клиенты были уверены в том, что отвечающая конечная точка обмена данными является ожидаемой доверенной стороной.</span><span class="sxs-lookup"><span data-stu-id="01892-111">Specifically, it is important for clients to be assured that the Metadata Exchange endpoint that is responding is the intended trusted party.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01892-112">Пример</span><span class="sxs-lookup"><span data-stu-id="01892-112">Example</span></span>  

 <span data-ttu-id="01892-113">В этом примере показано использование моникера службы в сочетании с контрактом MEX.</span><span class="sxs-lookup"><span data-stu-id="01892-113">This example shows the use of the service moniker with a MEX contract.</span></span> <span data-ttu-id="01892-114">Служба со следующим контрактом предоставляется посредством привязки wsHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="01892-114">A service with the following contract is exposed with a wsHttpBinding.</span></span>  
  
```csharp
using System.ServiceModel;  
  
// ...
  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Demo")]  
public interface IAffiliate  
{  
    [OperationContract]  
    bool NewAffiliate(string ID, string company, string fullname, string accountsCode);  
    [OperationContract]  
    bool RemoveAffiliate(string ID);  
    [OperationContract]  
    double RevenueCheckMonthly(ref string ID);  
    [OperationContract]  
    double RevenueCheckTotal(ref string ID);  
}  
```  
  
 <span data-ttu-id="01892-115">Чтобы создать клиент WCF для удаленной службы, можно использовать следующий пример строки моникера.</span><span class="sxs-lookup"><span data-stu-id="01892-115">To construct a WCF client for the remote service the following example moniker string can be used.</span></span>  
  
```
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 <span data-ttu-id="01892-116">В ходе выполнения клиентского приложения клиент выполняет обмен данными `WS-MetadataExchange` с переданным параметром `mexAddress`.</span><span class="sxs-lookup"><span data-stu-id="01892-116">During the execution of the client application, the client performs a `WS-MetadataExchange` with the provided `mexAddress`.</span></span> <span data-ttu-id="01892-117">В результате могут быть возвращены сведения об адресе, привязке и контракте для ряда служб.</span><span class="sxs-lookup"><span data-stu-id="01892-117">This might return the address, binding and contract details for a number of services.</span></span> <span data-ttu-id="01892-118">Параметры `address`, `contract`, `contractNamespace`, `binding` и `bindingNamespace` используются для идентификации требуемой службы.</span><span class="sxs-lookup"><span data-stu-id="01892-118">The `address`, `contract`, `contractNamespace`, `binding` and `bindingNamespace` parameters are used to identify the intended service.</span></span> <span data-ttu-id="01892-119">После сопоставления этих параметров моникер формирует клиент WCF с соответствующим определением контракта, а затем вызовы могут выполняться с помощью клиента WCF, как и типизированный контракт.</span><span class="sxs-lookup"><span data-stu-id="01892-119">Once those parameters have been matched, the moniker constructs a WCF client with the appropriate contract definition and calls can then be made using the WCF client, as with the typed contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01892-120">Если моникер сформирован неправильно или служба недоступна, при вызове метода `GetObject` будет возвращена ошибка "Синтаксическая ошибка".</span><span class="sxs-lookup"><span data-stu-id="01892-120">If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error saying "Invalid Syntax".</span></span> <span data-ttu-id="01892-121">При получении этой ошибки убедитесь, что используется правильный моникер, а служба доступна.</span><span class="sxs-lookup"><span data-stu-id="01892-121">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01892-122">См. также</span><span class="sxs-lookup"><span data-stu-id="01892-122">See also</span></span>

- [<span data-ttu-id="01892-123">Практическое руководство. Регистрация и настройка моникера службы</span><span class="sxs-lookup"><span data-stu-id="01892-123">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)
