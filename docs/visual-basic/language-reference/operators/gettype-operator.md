---
description: Дополнительные сведения о операторе GetType (Visual Basic)
title: GetType Operator
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 15fe9c28997aa01527f23c0cc8fdbb0fe6cc53f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665995"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="83f67-103">Оператор GetType (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83f67-103">GetType Operator (Visual Basic)</span></span>

<span data-ttu-id="83f67-104">Возвращает <xref:System.Type> объект для указанного типа.</span><span class="sxs-lookup"><span data-stu-id="83f67-104">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="83f67-105"><xref:System.Type>Объект предоставляет сведения о типе, например его свойства, методы и события.</span><span class="sxs-lookup"><span data-stu-id="83f67-105">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f67-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="83f67-106">Syntax</span></span>  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="83f67-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="83f67-107">Parameters</span></span>  
  
|<span data-ttu-id="83f67-108">Параметр</span><span class="sxs-lookup"><span data-stu-id="83f67-108">Parameter</span></span>|<span data-ttu-id="83f67-109">Описание</span><span class="sxs-lookup"><span data-stu-id="83f67-109">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="83f67-110">Имя типа, для которого требуется получить сведения.</span><span class="sxs-lookup"><span data-stu-id="83f67-110">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83f67-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="83f67-111">Remarks</span></span>  

 <span data-ttu-id="83f67-112">`GetType`Оператор возвращает <xref:System.Type> объект для указанного объекта `typename` .</span><span class="sxs-lookup"><span data-stu-id="83f67-112">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="83f67-113">Имя любого определенного типа можно передать в `typename` .</span><span class="sxs-lookup"><span data-stu-id="83f67-113">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="83f67-114">Например:</span><span class="sxs-lookup"><span data-stu-id="83f67-114">This includes the following:</span></span>  
  
- <span data-ttu-id="83f67-115">Любой тип данных Visual Basic, например `Boolean` или `Date` .</span><span class="sxs-lookup"><span data-stu-id="83f67-115">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="83f67-116">Любой платформа .NET Framework класс, структура, модуль или интерфейс, например <xref:System.ArgumentException?displayProperty=nameWithType> или <xref:System.Double?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="83f67-116">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="83f67-117">Любой класс, структура, модуль или интерфейс, определенный приложением.</span><span class="sxs-lookup"><span data-stu-id="83f67-117">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="83f67-118">Любой массив, определенный приложением.</span><span class="sxs-lookup"><span data-stu-id="83f67-118">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="83f67-119">Любой делегат, определенный приложением.</span><span class="sxs-lookup"><span data-stu-id="83f67-119">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="83f67-120">Любое перечисление, определенное Visual Basic, платформа .NET Framework или вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="83f67-120">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="83f67-121">Если требуется получить объект типа объектной переменной, используйте <xref:System.Type.GetType%2A?displayProperty=nameWithType> метод.</span><span class="sxs-lookup"><span data-stu-id="83f67-121">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="83f67-122">`GetType`Оператор может быть полезен в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="83f67-122">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="83f67-123">Необходимо получить доступ к метаданным для типа во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="83f67-123">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="83f67-124"><xref:System.Type>Объект предоставляет метаданные, такие как члены типов и сведения о развертывании.</span><span class="sxs-lookup"><span data-stu-id="83f67-124">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="83f67-125">Это необходимо, например, для отражения сборки.</span><span class="sxs-lookup"><span data-stu-id="83f67-125">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="83f67-126">Для получения дополнительной информации см. <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="83f67-126">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="83f67-127">Необходимо сравнить две ссылки на объект, чтобы определить, ссылаются ли они на экземпляры одного типа.</span><span class="sxs-lookup"><span data-stu-id="83f67-127">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="83f67-128">В противном случае `GetType` возвращает ссылки на один и тот же <xref:System.Type> объект.</span><span class="sxs-lookup"><span data-stu-id="83f67-128">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83f67-129">Пример</span><span class="sxs-lookup"><span data-stu-id="83f67-129">Example</span></span>  

 <span data-ttu-id="83f67-130">В следующих примерах показан используемый `GetType` оператор.</span><span class="sxs-lookup"><span data-stu-id="83f67-130">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="83f67-131">См. также</span><span class="sxs-lookup"><span data-stu-id="83f67-131">See also</span></span>

- [<span data-ttu-id="83f67-132">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="83f67-132">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="83f67-133">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="83f67-133">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="83f67-134">Операторы и выражения</span><span class="sxs-lookup"><span data-stu-id="83f67-134">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
