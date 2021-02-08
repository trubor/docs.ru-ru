---
description: Дополнительные сведения о том, как указать, какие элементы проверяются на конфликты параллелизма.
title: Практическое руководство. Как указать, для каких элементов тестируется возникновение конфликтов параллелизма
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: f2623c1e6afcf97ee2de62b94b80145ca2a5cad3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785863"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a><span data-ttu-id="7b77d-103">Практическое руководство. Как указать, для каких элементов тестируется возникновение конфликтов параллелизма</span><span class="sxs-lookup"><span data-stu-id="7b77d-103">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>

<span data-ttu-id="7b77d-104">Примените одно из трех перечислений к [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> свойству <xref:System.Data.Linq.Mapping.ColumnAttribute> атрибута, чтобы указать, какие элементы должны включаться в проверки обновления для обнаружения конфликтов оптимистичного параллелизма.</span><span class="sxs-lookup"><span data-stu-id="7b77d-104">Apply one of three enums to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify which members are to be included in update checks for the detection of optimistic concurrency conflicts.</span></span>  
  
 <span data-ttu-id="7b77d-105">Свойство <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> (сопоставляемое во время разработки) используется в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] вместе с возможностями параллелизма времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="7b77d-105">The <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property (mapped at design time) is used together with run-time concurrency features in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="7b77d-106">Дополнительные сведения см. в разделе [Оптимистическая блокировка: обзор](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7b77d-106">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b77d-107">Если ни одному члену не присвоено значение `IsVersion=true`, исходные значения членов сравниваются с текущим состоянием базы данных.</span><span class="sxs-lookup"><span data-stu-id="7b77d-107">Original member values are compared with the current database state as long as no member is designated as `IsVersion=true`.</span></span> <span data-ttu-id="7b77d-108">Для получения дополнительной информации см. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="7b77d-108">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 <span data-ttu-id="7b77d-109">Примеры кода см. в разделе <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="7b77d-109">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="7b77d-110">Чтобы всегда использовать этот член для обнаружения конфликтов, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="7b77d-110">To always use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="7b77d-111">Добавьте свойство <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> атрибуту <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7b77d-111">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="7b77d-112">Задайте свойству <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> значение `Always`.</span><span class="sxs-lookup"><span data-stu-id="7b77d-112">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Always`.</span></span>  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="7b77d-113">Чтобы никогда не использовать этот член для обнаружения конфликтов, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="7b77d-113">To never use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="7b77d-114">Добавьте свойство <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> атрибуту <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7b77d-114">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="7b77d-115">Задайте свойству <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> значение `Never`.</span><span class="sxs-lookup"><span data-stu-id="7b77d-115">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Never`.</span></span>  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a><span data-ttu-id="7b77d-116">Чтобы использовать этот член для обнаружения конфликтов, только когда приложение изменяет его значение, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="7b77d-116">To use this member for detecting conflicts only when the application has changed the value of the member</span></span>  
  
1. <span data-ttu-id="7b77d-117">Добавьте свойство <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> атрибуту <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7b77d-117">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="7b77d-118">Задайте свойству <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> значение `WhenChanged`.</span><span class="sxs-lookup"><span data-stu-id="7b77d-118">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `WhenChanged`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b77d-119">Пример</span><span class="sxs-lookup"><span data-stu-id="7b77d-119">Example</span></span>  

 <span data-ttu-id="7b77d-120">В следующем примере указывается, что объекты `HomePage` никогда не должны включаться в проверки обновлений.</span><span class="sxs-lookup"><span data-stu-id="7b77d-120">The following example specifies that `HomePage` objects should never be tested during update checks.</span></span> <span data-ttu-id="7b77d-121">Для получения дополнительной информации см. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="7b77d-121">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7b77d-122">См. также</span><span class="sxs-lookup"><span data-stu-id="7b77d-122">See also</span></span>

- [<span data-ttu-id="7b77d-123">Практическое руководство. Как управлять конфликтами изменений</span><span class="sxs-lookup"><span data-stu-id="7b77d-123">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="7b77d-124">Внесение и отправка изменений данных</span><span class="sxs-lookup"><span data-stu-id="7b77d-124">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
