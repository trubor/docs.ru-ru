---
description: Дополнительные сведения о действиях сбора в WF
title: Действия коллекции в WF
ms.date: 03/30/2017
ms.assetid: 2680c3e2-9902-4968-b98d-cab776103dbe
ms.openlocfilehash: f7b37640afa185f753f036b58367a7877f34b127
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720206"
---
# <a name="collection-activities-in-wf"></a><span data-ttu-id="d0f2b-103">Действия коллекции в WF</span><span class="sxs-lookup"><span data-stu-id="d0f2b-103">Collection Activities in WF</span></span>

<span data-ttu-id="d0f2b-104">Действия коллекции используются для работы с объектами коллекции в рамках рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d0f2b-104">Collection activities are used to work with collection objects in a workflow.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="d0f2b-105">имеет системные действия для добавления элементов в коллекцию и удаления из нее, тестирования на наличие элемента в коллекции и очистки коллекции.</span><span class="sxs-lookup"><span data-stu-id="d0f2b-105">has system-provided activities for adding and removing items from a collection, testing for the existence of an item in a collection, and clearing a collection.</span></span> <span data-ttu-id="d0f2b-106">`ExistsInCollection` и `RemoveFromCollection` имеют <xref:System.Activities.OutArgument%601> тип <xref:System.Boolean> , который указывает результат.</span><span class="sxs-lookup"><span data-stu-id="d0f2b-106">`ExistsInCollection` and `RemoveFromCollection` have an <xref:System.Activities.OutArgument%601> of type <xref:System.Boolean>, which indicates the result.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d0f2b-107">Если действие коллекции выполняется до задания базового объекта коллекции, то формируется исключение <xref:System.InvalidOperationException> и действие завершается ошибкой.</span><span class="sxs-lookup"><span data-stu-id="d0f2b-107">If a collection activity is executed before setting the underlying collection object, an <xref:System.InvalidOperationException> is thrown and the activity faults.</span></span>  
  
## <a name="collection-activities"></a><span data-ttu-id="d0f2b-108">Действия коллекции</span><span class="sxs-lookup"><span data-stu-id="d0f2b-108">Collection activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.AddToCollection%601>|<span data-ttu-id="d0f2b-109">Добавляет элемент в указанную коллекцию.</span><span class="sxs-lookup"><span data-stu-id="d0f2b-109">Adds an item to a specified collection.</span></span>|  
|<xref:System.Activities.Statements.ClearCollection%601>|<span data-ttu-id="d0f2b-110">Очищает все элементы из указанной коллекции.</span><span class="sxs-lookup"><span data-stu-id="d0f2b-110">Clears all items from a specified collection.</span></span>|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|<span data-ttu-id="d0f2b-111">Если элемент присутствует в коллекции, возвращает `true`.</span><span class="sxs-lookup"><span data-stu-id="d0f2b-111">Returns `true` if an item exists in a collection.</span></span>|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|<span data-ttu-id="d0f2b-112">Удаляет элемент из указанной коллекции и возвращает значение `true`, если элемент успешно удален.</span><span class="sxs-lookup"><span data-stu-id="d0f2b-112">Removes an item from a specified collection and returns `true` if the item was successfully removed.</span></span>|  
  
## <a name="using-collection-activities"></a><span data-ttu-id="d0f2b-113">Использование действий коллекции</span><span class="sxs-lookup"><span data-stu-id="d0f2b-113">Using collection activities</span></span>  

 <span data-ttu-id="d0f2b-114">В следующем примере кода показано, как работать с коллекцией, объявленной в виде переменной рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="d0f2b-114">The following code example demonstrates how to interact with a collection declared as a workflow variable.</span></span> <span data-ttu-id="d0f2b-115">Используемая коллекция является <xref:System.Collections.Generic.List%601> объектов <xref:System.String> по имени `fruitList`.</span><span class="sxs-lookup"><span data-stu-id="d0f2b-115">The collection used is a <xref:System.Collections.Generic.List%601> of <xref:System.String> objects named `fruitList`.</span></span>  
  
```csharp  
Variable<ICollection<string>> fruitList = new Variable<ICollection<string>>  
{  
    Default = new VisualBasicValue<ICollection<string>>("New List(Of String) From {\"Apple\", \"Orange\"}"),  
    Name = "FruitList"  
};  
  
Variable<bool> result = new Variable<bool>  
{  
    Name = "Result"  
};  
  
Activity wf = new Sequence  
{  
    Variables = { fruitList, result },  
  
    Activities =
    {  
        new If  
        {  
            Condition = new ExistsInCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Pear"  
            },  
            Then = new AddToCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Pear"  
            },  
            Else = new RemoveFromCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Apple"  
            }  
        },  
  
        new RemoveFromCollection<string>  
        {  
            Collection = fruitList,  
            Item = "Apple",  
            Result = result  
        },  
        new If  
        {  
            Condition = result,  
            Then = new ClearCollection<string>  
            {  
                Collection = fruitList,  
            }  
        }  
    }  
};  
```  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
    <x:Reference>__ReferenceID1</x:Reference>  
  </Sequence.Variables>  
  <If>  
    <If.Condition>  
      <InArgument  
         x:TypeArguments="x:Boolean">  
        <ExistsInCollection  
           x:TypeArguments="x:String"  
           Item="Pear">  
          <ExistsInCollection.Result>  
            <OutArgument  
               x:TypeArguments="x:Boolean" />  
          </ExistsInCollection.Result>  
          <InArgument  
             x:TypeArguments="scg:ICollection(x:String)">  
            <VariableValue  
               x:TypeArguments="scg:ICollection(x:String)">  
              <VariableValue.Result>  
                <OutArgument  
                   x:TypeArguments="scg:ICollection(x:String)" />  
              </VariableValue.Result>  
              <VariableValue.Variable>  
                <Variable  
                   x:TypeArguments="scg:ICollection(x:String)"  
                   x:Name="__ReferenceID0"  
                   Default="[New List(Of String) From {"Apple", "Orange"}]"  
                   Name="FruitList" />  
              </VariableValue.Variable>  
            </VariableValue>  
          </InArgument>  
        </ExistsInCollection>  
      </InArgument>  
    </If.Condition>  
    <If.Then>  
      <AddToCollection  
         x:TypeArguments="x:String"  
         Item="Pear">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </AddToCollection>  
    </If.Then>  
    <If.Else>  
      <RemoveFromCollection  
         x:TypeArguments="x:String"  
         Item="Apple"  
         Result="{x:Null}">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </RemoveFromCollection>  
    </If.Else>  
  </If>  
  <RemoveFromCollection  
     x:TypeArguments="x:String"  
     Item="Apple">  
    <RemoveFromCollection.Result>  
      <OutArgument  
         x:TypeArguments="x:Boolean">  
        <VariableReference  
           x:TypeArguments="x:Boolean">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(x:Boolean)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="x:Boolean"  
               x:Name="__ReferenceID1"  
               Name="Result" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </RemoveFromCollection.Result>  
    <InArgument  
       x:TypeArguments="scg:ICollection(x:String)">  
      <VariableValue  
         x:TypeArguments="scg:ICollection(x:String)"  
         Variable="{x:Reference __ReferenceID0}">  
        <VariableValue.Result>  
          <OutArgument  
             x:TypeArguments="scg:ICollection(x:String)" />  
        </VariableValue.Result>  
      </VariableValue>  
    </InArgument>  
  </RemoveFromCollection>  
  <If>  
    <If.Condition>  
      <InArgument  
         x:TypeArguments="x:Boolean">  
        <VariableValue  
           x:TypeArguments="x:Boolean"  
           Variable="{x:Reference __ReferenceID1}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="x:Boolean" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </If.Condition>  
    <If.Then>  
      <ClearCollection  
         x:TypeArguments="x:String">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </ClearCollection>  
    </If.Then>  
  </If>  
</Sequence>  
```  
  
 <span data-ttu-id="d0f2b-116">Перечисленные выше образцы кода можно также создать с помощью <xref:Microsoft.CSharp.Activities.CSharpValue%601> вместо <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601></span><span class="sxs-lookup"><span data-stu-id="d0f2b-116">The above code samples can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601></span></span>  
  
```csharp
Variable<ICollection<string>> fruitList = new Variable<ICollection<string>>  
{  
    Default = new CSharpValue<ICollection<string>>("new List<String> From {\"Apple\", \"Orange\"};"),  
    Name = "FruitList"  
};  
  
Variable<bool> result = new Variable<bool>  
{  
    Name = "Result"  
};  
  
Activity wf = new Sequence  
{  
    Variables = { fruitList, result },  
  
    Activities =
    {  
        new If  
        {  
            Condition = new ExistsInCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Pear"  
            },  
            Then = new AddToCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Pear"  
            },  
            Else = new RemoveFromCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Apple"  
            }  
        },  
  
        new RemoveFromCollection<string>  
        {  
            Collection = fruitList,  
            Item = "Apple",  
            Result = result  
        },  
        new If  
        {  
            Condition = result,  
            Then = new ClearCollection<string>  
            {  
                Collection = fruitList,  
            }  
        }  
    }  
};  
```  
  
```xml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
    <x:Reference>__ReferenceID1</x:Reference>  
  </Sequence.Variables>  
  <If>  
    <If.Condition>  
      <InArgument  
         x:TypeArguments="x:Boolean">  
        <ExistsInCollection  
           x:TypeArguments="x:String"  
           Item="Pear">  
          <ExistsInCollection.Result>  
            <OutArgument  
               x:TypeArguments="x:Boolean" />  
          </ExistsInCollection.Result>  
          <InArgument  
             x:TypeArguments="scg:ICollection(x:String)">  
            <VariableValue  
               x:TypeArguments="scg:ICollection(x:String)">  
              <VariableValue.Result>  
                <OutArgument  
                   x:TypeArguments="scg:ICollection(x:String)" />  
              </VariableValue.Result>  
              <VariableValue.Variable>  
                <Variable  
                   x:TypeArguments="scg:ICollection(x:String)"  
                   x:Name="__ReferenceID0"  
                   Default="[new List<String> From {"Apple", "Orange"};]"  
                   Name="FruitList" />  
              </VariableValue.Variable>  
            </VariableValue>  
          </InArgument>  
        </ExistsInCollection>  
      </InArgument>  
    </If.Condition>  
    <If.Then>  
      <AddToCollection  
         x:TypeArguments="x:String"  
         Item="Pear">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </AddToCollection>  
    </If.Then>  
    <If.Else>  
      <RemoveFromCollection  
         x:TypeArguments="x:String"  
         Item="Apple"  
         Result="{x:Null}">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </RemoveFromCollection>  
    </If.Else>  
  </If>  
  <RemoveFromCollection  
     x:TypeArguments="x:String"  
     Item="Apple">  
    <RemoveFromCollection.Result>  
      <OutArgument  
         x:TypeArguments="x:Boolean">  
        <VariableReference  
           x:TypeArguments="x:Boolean">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(x:Boolean)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="x:Boolean"  
               x:Name="__ReferenceID1"  
               Name="Result" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </RemoveFromCollection.Result>  
    <InArgument  
       x:TypeArguments="scg:ICollection(x:String)">  
      <VariableValue  
         x:TypeArguments="scg:ICollection(x:String)"  
         Variable="{x:Reference __ReferenceID0}">  
        <VariableValue.Result>  
          <OutArgument  
             x:TypeArguments="scg:ICollection(x:String)" />  
        </VariableValue.Result>  
      </VariableValue>  
    </InArgument>  
  </RemoveFromCollection>  
  <If>  
    <If.Condition>  
      <InArgument  
         x:TypeArguments="x:Boolean">  
        <VariableValue  
           x:TypeArguments="x:Boolean"  
           Variable="{x:Reference __ReferenceID1}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="x:Boolean" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </If.Condition>  
    <If.Then>  
      <ClearCollection  
         x:TypeArguments="x:String">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </ClearCollection>  
    </If.Then>  
  </If>  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0f2b-117">См. также</span><span class="sxs-lookup"><span data-stu-id="d0f2b-117">See also</span></span>

- [<span data-ttu-id="d0f2b-118">Разработка рабочих процессов, действий и выражений с помощью императивного кода</span><span class="sxs-lookup"><span data-stu-id="d0f2b-118">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
