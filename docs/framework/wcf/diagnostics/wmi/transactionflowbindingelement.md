---
description: 'Дополнительные сведения о: Трансактионфловбиндинжелемент'
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: 6a96a83c563affdaef01a12d64bc1c13ab2f719e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757141"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="8779f-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="8779f-103">TransactionFlowBindingElement</span></span>

<span data-ttu-id="8779f-104">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="8779f-104">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8779f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8779f-105">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8779f-106">Методы</span><span class="sxs-lookup"><span data-stu-id="8779f-106">Methods</span></span>  

 <span data-ttu-id="8779f-107">Класс TransactionFlowBindingElement не определяет никаких методов.</span><span class="sxs-lookup"><span data-stu-id="8779f-107">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8779f-108">Свойства</span><span class="sxs-lookup"><span data-stu-id="8779f-108">Properties</span></span>  

 <span data-ttu-id="8779f-109">Класс TransactionFlowBindingElement имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="8779f-109">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="8779f-110">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="8779f-110">IssuedTokens</span></span>  

 <span data-ttu-id="8779f-111">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="8779f-111">Data type: string</span></span>  
  
 <span data-ttu-id="8779f-112">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="8779f-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8779f-113">Задает требование для заголовка выданных маркеров безопасности (IssuedTokens из WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="8779f-113">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="8779f-114">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="8779f-114">TransactionProtocol</span></span>  

 <span data-ttu-id="8779f-115">Тип данных: строка</span><span class="sxs-lookup"><span data-stu-id="8779f-115">Data type: string</span></span>  
  
 <span data-ttu-id="8779f-116">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="8779f-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8779f-117">Протокол транзакций, используемый службой для передачи транзакций.</span><span class="sxs-lookup"><span data-stu-id="8779f-117">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="8779f-118">Transactions</span><span class="sxs-lookup"><span data-stu-id="8779f-118">Transactions</span></span>  

 <span data-ttu-id="8779f-119">Тип данных: boolean</span><span class="sxs-lookup"><span data-stu-id="8779f-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="8779f-120">Тип доступа: только для чтения</span><span class="sxs-lookup"><span data-stu-id="8779f-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8779f-121">Указывает, поддерживается ли входящая транзакция.</span><span class="sxs-lookup"><span data-stu-id="8779f-121">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8779f-122">Требования</span><span class="sxs-lookup"><span data-stu-id="8779f-122">Requirements</span></span>  
  
|<span data-ttu-id="8779f-123">MOF</span><span class="sxs-lookup"><span data-stu-id="8779f-123">MOF</span></span>|<span data-ttu-id="8779f-124">Объявлено в файле Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8779f-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8779f-125">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="8779f-125">Namespace</span></span>|<span data-ttu-id="8779f-126">Определено в root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="8779f-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8779f-127">См. также</span><span class="sxs-lookup"><span data-stu-id="8779f-127">See also</span></span>

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
