---
description: 'Дополнительные сведения: Настройка операций вставки, обновления и удаления'
title: Настройка операций вставки, обновления и удаления
ms.date: 03/30/2017
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
ms.openlocfilehash: 44bd76b61aff335019818b3c61040d10babe7301
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773216"
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="0b287-103">Настройка операций вставки, обновления и удаления</span><span class="sxs-lookup"><span data-stu-id="0b287-103">Customizing Insert, Update, and Delete Operations</span></span>

<span data-ttu-id="0b287-104">По умолчанию [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] создает динамический SQL для выполнения операций чтения, обновления и удаления.</span><span class="sxs-lookup"><span data-stu-id="0b287-104">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="0b287-105">Однако на практике обычно приходится настраивать приложение в соответствии с собственными бизнес-требованиями.</span><span class="sxs-lookup"><span data-stu-id="0b287-105">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b287-106">При использовании Visual Studio можно использовать реляционный конструктор объектов для настройки действий вставки, обновления и удаления.</span><span class="sxs-lookup"><span data-stu-id="0b287-106">If you are using Visual Studio, you can use the Object Relational Designer to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="0b287-107">В данном разделе описываются методы, представляемые [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], для настройки операций вставки, чтения, обновления и удаления в приложении.</span><span class="sxs-lookup"><span data-stu-id="0b287-107">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b287-108">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="0b287-108">In This Section</span></span>  

 [<span data-ttu-id="0b287-109">Настройка операций: Обзор</span><span class="sxs-lookup"><span data-stu-id="0b287-109">Customizing Operations: Overview</span></span>](customizing-operations-overview.md)  
 <span data-ttu-id="0b287-110">Содержит описание различных методов, представленных в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], для настройки операций вставки, чтения, обновления и удаления в приложении.</span><span class="sxs-lookup"><span data-stu-id="0b287-110">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="0b287-111">Операции вставки, обновления и удаления</span><span class="sxs-lookup"><span data-stu-id="0b287-111">Insert, Update, and Delete Operations</span></span>](insert-update-and-delete-operations.md)  
 <span data-ttu-id="0b287-112">Содержит описание заданных по умолчанию процессов [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] по управлению данными базы данных.</span><span class="sxs-lookup"><span data-stu-id="0b287-112">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="0b287-113">Ответственность разработчика при переопределении поведения по умолчанию</span><span class="sxs-lookup"><span data-stu-id="0b287-113">Responsibilities of the Developer In Overriding Default Behavior</span></span>](responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="0b287-114">Содержит описание роли разработчиков в реализации требований, не примененных [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0b287-114">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="0b287-115">Добавление бизнес-логики с использованием разделяемых методов</span><span class="sxs-lookup"><span data-stu-id="0b287-115">Adding Business Logic By Using Partial Methods</span></span>](adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="0b287-116">Содержит описание использования разделяемых методов для переопределения автоматически сгенерированных методов.</span><span class="sxs-lookup"><span data-stu-id="0b287-116">Describes how to use partial methods to override autogenerated methods.</span></span>
