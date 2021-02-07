---
description: 'Дополнительные сведения: модели транзакций'
title: Модели транзакций
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 9abccf74ef5b242cfbe63605046e30e397b8eda6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752708"
---
# <a name="transaction-models"></a><span data-ttu-id="3ae6b-103">Модели транзакций</span><span class="sxs-lookup"><span data-stu-id="3ae6b-103">Transaction Models</span></span>

<span data-ttu-id="3ae6b-104">В этом разделе описывается связь между моделями программирования транзакций и компонентами инфраструктуры, предоставляемыми корпорацией Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3ae6b-104">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="3ae6b-105">При использовании транзакций в Windows Communication Foundation (WCF) важно понимать, что не выбирается между различными моделями транзакций, а работает на разных уровнях интегрированной и согласованной модели.</span><span class="sxs-lookup"><span data-stu-id="3ae6b-105">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="3ae6b-106">В следующих подразделах рассматриваются три основных компонента транзакции.</span><span class="sxs-lookup"><span data-stu-id="3ae6b-106">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="3ae6b-107">Транзакции Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3ae6b-107">Windows Communication Foundation Transactions</span></span>  

 <span data-ttu-id="3ae6b-108">Поддержка транзакций в WCF позволяет создавать транзакционные службы.</span><span class="sxs-lookup"><span data-stu-id="3ae6b-108">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="3ae6b-109">Кроме того, благодаря поддержке протокола WS-AtomicTransaction (WS-AT) приложения могут передавать транзакции веб-службам, созданным с помощью WCF или технологии сторонних разработчиков.</span><span class="sxs-lookup"><span data-stu-id="3ae6b-109">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="3ae6b-110">В службе WCF или приложении функции транзакций WCF предоставляют атрибуты и конфигурацию для декларативного указания того, как и когда инфраструктура должна создавать, подавать и синхронизировать транзакции.</span><span class="sxs-lookup"><span data-stu-id="3ae6b-110">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="3ae6b-111">Транзакции System.Transactions</span><span class="sxs-lookup"><span data-stu-id="3ae6b-111">System.Transactions Transactions</span></span>  

 <span data-ttu-id="3ae6b-112">Пространство имен <xref:System.Transactions> предоставляет как модель явного программирования, основанную на классе <xref:System.Transactions.Transaction>, так и модель неявного программирования, использующая класс <xref:System.Transactions.TransactionScope>, в котором транзакции автоматически управляются инфраструктурой.</span><span class="sxs-lookup"><span data-stu-id="3ae6b-112">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="3ae6b-113">Дополнительные сведения о создании транзакционного приложения с помощью этих двух моделей см. [в разделе Написание транзакционного приложения](https://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="3ae6b-113">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](https://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="3ae6b-114">В службе или приложении WCF <xref:System.Transactions> предоставляет модель программирования для создания транзакций в клиентском приложении и для явного взаимодействия с транзакцией, когда это необходимо, в службе.</span><span class="sxs-lookup"><span data-stu-id="3ae6b-114">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="3ae6b-115">Транзакции MSDTC</span><span class="sxs-lookup"><span data-stu-id="3ae6b-115">MSDTC Transactions</span></span>  

 <span data-ttu-id="3ae6b-116">Координатор распределенных транзакций (Майкрософт) (MSDTC) представляет собой диспетчер транзакций, обеспечивающий поддержку распределенных транзакций.</span><span class="sxs-lookup"><span data-stu-id="3ae6b-116">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="3ae6b-117">Дополнительные сведения см. в [справочнике программиста по DTC](/previous-versions/windows/desktop/ms686108(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="3ae6b-117">For more information, see the [DTC Programmer's Reference](/previous-versions/windows/desktop/ms686108(v=vs.85)).</span></span>  
  
 <span data-ttu-id="3ae6b-118">В службе или приложении WCF служба MSDTC предоставляет инфраструктуру для координации транзакций, созданных в клиенте или службе.</span><span class="sxs-lookup"><span data-stu-id="3ae6b-118">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
