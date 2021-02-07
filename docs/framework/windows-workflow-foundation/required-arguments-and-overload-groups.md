---
description: 'Дополнительные сведения о: обязательных аргументах и группах перегрузок'
title: Обязательные аргументы и группы перегруженных аргументов
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 1eea77276ad976c81d891e45cfbe5217b298b4fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720037"
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="b1c78-103">Обязательные аргументы и группы перегруженных аргументов</span><span class="sxs-lookup"><span data-stu-id="b1c78-103">Required Arguments and Overload Groups</span></span>

<span data-ttu-id="b1c78-104">Действия можно настроить таким образом, чтобы для их выполнения требовалась привязка определенных аргументов.</span><span class="sxs-lookup"><span data-stu-id="b1c78-104">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="b1c78-105">Атрибут `RequiredArgument` указывает, что для действия необходимы определенные аргументы, а атрибут `OverloadGroup` используется для группирования категорий необходимых аргументов.</span><span class="sxs-lookup"><span data-stu-id="b1c78-105">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="b1c78-106">С помощью атрибутов авторы действий могут реализовать простые или сложные конфигурации проверки правильности действий.</span><span class="sxs-lookup"><span data-stu-id="b1c78-106">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="b1c78-107">Использование обязательных аргументов</span><span class="sxs-lookup"><span data-stu-id="b1c78-107">Using Required Arguments</span></span>  

 <span data-ttu-id="b1c78-108">Чтобы использовать атрибут `RequiredArgument` в действии, укажите необходимые аргументы с помощью <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b1c78-108">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="b1c78-109">В этом примере действие `Add` определено, как имеющее два обязательных аргумента.</span><span class="sxs-lookup"><span data-stu-id="b1c78-109">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="b1c78-110">В XAML необходимые аргументы также обозначаются с помощью <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b1c78-110">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="b1c78-111">В данном примере действие `Add` определено с помощью трех аргументов и использует действие <xref:System.Activities.Statements.Assign%601> для выполнения операции сложения.</span><span class="sxs-lookup"><span data-stu-id="b1c78-111">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
```xaml  
<Activity x:Class="ValidationDemo.Add" ...>  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Result" Type="OutArgument(x:Int32)" />  
  </x:Members>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[Result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[Operand1 + Operand2]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Activity>  
```  
  
 <span data-ttu-id="b1c78-112">При использовании действия, если любой из необходимых аргументов не привязан, будет возвращена следующая ошибка проверки.</span><span class="sxs-lookup"><span data-stu-id="b1c78-112">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="b1c78-113">**Не указано значение необходимого аргумента действия Operand1.**</span><span class="sxs-lookup"><span data-stu-id="b1c78-113">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
> <span data-ttu-id="b1c78-114">Дополнительные сведения о проверке и обработке ошибок и предупреждений проверки см. в разделе [вызов проверки активности](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="b1c78-114">For more information about checking for and handling validation errors and warnings, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="b1c78-115">Использование групп перегрузки</span><span class="sxs-lookup"><span data-stu-id="b1c78-115">Using Overload Groups</span></span>

<span data-ttu-id="b1c78-116">Группы перегрузки предоставляют метод, позволяющий определить, какие комбинации аргументов допустимы для действия.</span><span class="sxs-lookup"><span data-stu-id="b1c78-116">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="b1c78-117">Аргументы группируются с помощью <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b1c78-117">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="b1c78-118">Каждой группе присваивается имя, заданное параметром <xref:System.Activities.OverloadGroupAttribute> .</span><span class="sxs-lookup"><span data-stu-id="b1c78-118">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="b1c78-119">Действие допустимо, только если привязываются только один набор аргументов в группе перегрузки.</span><span class="sxs-lookup"><span data-stu-id="b1c78-119">The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="b1c78-120">В следующем примере определяется класс `CreateLocation`.</span><span class="sxs-lookup"><span data-stu-id="b1c78-120">In the following example, a `CreateLocation` class is defined.</span></span>  
  
```csharp  
class CreateLocation: Activity  
{  
    [RequiredArgument]  
    public InArgument<string> Name { get; set; }  
  
    public InArgument<string> Description { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Latitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Longitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    [OverloadGroup("G3")]  
    public InArgument<string> Street { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> City { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> State { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G3")]  
    public InArgument<int> Zip { get; set; }
}  
```  
  
 <span data-ttu-id="b1c78-121">Задача данного действия - указать местоположение в США.</span><span class="sxs-lookup"><span data-stu-id="b1c78-121">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="b1c78-122">Для этого пользователь действия может указать местоположение с помощью одной из трех групп аргументов.</span><span class="sxs-lookup"><span data-stu-id="b1c78-122">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="b1c78-123">Чтобы указать допустимые сочетания аргументов, определены 3 группы перегрузки.</span><span class="sxs-lookup"><span data-stu-id="b1c78-123">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="b1c78-124">`G1` содержит аргументы `Latitude` и `Longitude`.</span><span class="sxs-lookup"><span data-stu-id="b1c78-124">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="b1c78-125">`G2` содержит `Street`, `City` и `State`.</span><span class="sxs-lookup"><span data-stu-id="b1c78-125">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="b1c78-126">`G3` содержит `Street` и `Zip`.</span><span class="sxs-lookup"><span data-stu-id="b1c78-126">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="b1c78-127">`Name` также является обязательным аргументом, но не входит в группу перегрузки.</span><span class="sxs-lookup"><span data-stu-id="b1c78-127">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="b1c78-128">Чтобы данное действие было допустимым, `Name` должно быть привязано вместе со всеми аргументами только из одной группы перегрузки.</span><span class="sxs-lookup"><span data-stu-id="b1c78-128">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="b1c78-129">В следующем примере, взятом из примера [действий доступа к базе данных](./samples/database-access-activities.md) , есть две группы перегруженных версий: `ConnectionString` и `ConfigFileSectionName` .</span><span class="sxs-lookup"><span data-stu-id="b1c78-129">In the following example, taken from the [Database Access Activities](./samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="b1c78-130">Чтобы данное действие было допустимым, должны быть связаны либо аргументы `ProviderName` и `ConnectionString`, либо аргумент `ConfigName`, но не оба.</span><span class="sxs-lookup"><span data-stu-id="b1c78-130">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
```csharp  
public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }
}  
```  
  
 <span data-ttu-id="b1c78-131">При определении группы перегрузки:</span><span class="sxs-lookup"><span data-stu-id="b1c78-131">When defining an overload group:</span></span>  
  
- <span data-ttu-id="b1c78-132">Группа перегрузки не может быть подмножеством или эквивалентным набором другой группы перегрузки.</span><span class="sxs-lookup"><span data-stu-id="b1c78-132">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b1c78-133">Существует одно исключение из данного правила.</span><span class="sxs-lookup"><span data-stu-id="b1c78-133">There is one exception to this rule.</span></span> <span data-ttu-id="b1c78-134">Если группа перегрузки является подмножеством другой группы перегрузки и подмножество содержит только аргументы, где `RequiredArgument` равен `false`, то группа перегрузки допустима.</span><span class="sxs-lookup"><span data-stu-id="b1c78-134">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
- <span data-ttu-id="b1c78-135">Группы перегрузки могут пересекаться, но это приведет к ошибке, если пересечение групп содержит все обязательные аргументы одной или обеих групп.</span><span class="sxs-lookup"><span data-stu-id="b1c78-135">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="b1c78-136">В предыдущем примере группы перегрузки `G2` и `G3` перекрываются, но поскольку пересечение не содержит все аргументы одной или обеих групп, то это допустимо.</span><span class="sxs-lookup"><span data-stu-id="b1c78-136">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="b1c78-137">Если имеет место привязка аргументов в группе перегрузки:</span><span class="sxs-lookup"><span data-stu-id="b1c78-137">When binding arguments in an overload group:</span></span>  
  
- <span data-ttu-id="b1c78-138">Группа перегрузки считается связанной, если все аргументы `RequiredArgument` в этой группе - связанные.</span><span class="sxs-lookup"><span data-stu-id="b1c78-138">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
- <span data-ttu-id="b1c78-139">Если в группе нет ни одного аргумента `RequiredArgument` и хотя бы один аргумент связан, то группа также считается связанной.</span><span class="sxs-lookup"><span data-stu-id="b1c78-139">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
- <span data-ttu-id="b1c78-140">Возникает ошибка проверки, если ни одна из групп перегрузки не является связанной и при этом нет ни одной группы перегрузки без аргументов `RequiredArgument`.</span><span class="sxs-lookup"><span data-stu-id="b1c78-140">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
- <span data-ttu-id="b1c78-141">При наличии нескольких привязанных групп перегрузки возникнет ошибка, т. е. все обязательные аргументы в одной группе являются связанными и любой аргумент в другой группе перегрузки также связан.</span><span class="sxs-lookup"><span data-stu-id="b1c78-141">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
