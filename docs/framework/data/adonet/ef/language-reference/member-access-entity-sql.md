---
description: Дополнительные сведения:. (Доступ к членам) (язык Entity SQL)
title: . (Доступ к членам) (язык Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 94833d3525c7d17cadaef15065b3dcbdb43a6ded
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739382"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="cbd22-105">.</span><span class="sxs-lookup"><span data-stu-id="cbd22-105">.</span></span> <span data-ttu-id="cbd22-106">(Доступ к членам) (язык Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="cbd22-106">(Member Access) (Entity SQL)</span></span>

<span data-ttu-id="cbd22-107">Оператор "точка" (.) является [!INCLUDE[esql](../../../../../../includes/esql-md.md)] оператором доступа к члену.</span><span class="sxs-lookup"><span data-stu-id="cbd22-107">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="cbd22-108">Оператор доступа к элементу можно использовать, чтобы выдавать значение свойства или поля экземпляра структурного типа концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="cbd22-108">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbd22-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cbd22-109">Syntax</span></span>  
  
```sql  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="cbd22-110">Аргументы</span><span class="sxs-lookup"><span data-stu-id="cbd22-110">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="cbd22-111">Экземпляр структурного типа концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="cbd22-111">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="cbd22-112">Свойство или поле, принадлежащее экземпляру объекта.</span><span class="sxs-lookup"><span data-stu-id="cbd22-112">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbd22-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="cbd22-113">Remarks</span></span>  

 <span data-ttu-id="cbd22-114">Оператор «точка» (.) можно использовать для извлечения полей из записи подобно извлечению свойств сложного типа или типа сущности.</span><span class="sxs-lookup"><span data-stu-id="cbd22-114">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="cbd22-115">Например, если «n» типа Name является элементом типа Name, а «p» является элементом типа Person, то «p.n» будет допустимым выражением доступа к элементу, которое выдаст значение типа Name.</span><span class="sxs-lookup"><span data-stu-id="cbd22-115">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="cbd22-116">См. также</span><span class="sxs-lookup"><span data-stu-id="cbd22-116">See also</span></span>

- [<span data-ttu-id="cbd22-117">Справочник по Entity SQL</span><span class="sxs-lookup"><span data-stu-id="cbd22-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
