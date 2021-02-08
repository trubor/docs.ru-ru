---
description: 'Дополнительные сведения о: BC30686: неоднозначность доступа к свойству по умолчанию между унаследованными членами интерфейса "" <defaultpropertyname> интерфейса "" <interfacename1> и " <defaultpropertyname> " интерфейса "<interfacename2>'
title: 'При доступе к свойству по умолчанию возникает неоднозначность между членами наследуемых интерфейсов: <defaultpropertyname> интерфейса <interfacename1> и <defaultpropertyname> интерфейса <interfacename2>'
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 5ae5e5b2dc7a61540e26d125e960d4755141d975
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796656"
---
# <a name="bc30686-default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a><span data-ttu-id="0b13d-103">BC30686: неоднозначность доступа к свойству по умолчанию между унаследованными членами интерфейса "" \<defaultpropertyname> интерфейса "" \<interfacename1> и " \<defaultpropertyname> " интерфейса " \<interfacename2> "</span><span class="sxs-lookup"><span data-stu-id="0b13d-103">BC30686: Default property access is ambiguous between the inherited interface members '\<defaultpropertyname>' of interface '\<interfacename1>' and '\<defaultpropertyname>' of interface '\<interfacename2>'</span></span>

<span data-ttu-id="0b13d-104">Интерфейс наследует от двух интерфейсов, каждый из которых объявляет свойство по умолчанию с тем же именем.</span><span class="sxs-lookup"><span data-stu-id="0b13d-104">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="0b13d-105">Компилятор не может разрешить доступ к этому свойству по умолчанию без уточнения.</span><span class="sxs-lookup"><span data-stu-id="0b13d-105">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="0b13d-106">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="0b13d-106">The following example illustrates this.</span></span>

```vb
Public Interface Iface1
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface2
    Default Property prop(ByVal arg As Integer) As Integer
End Interface
Public Interface Iface3
    Inherits Iface1, Iface2
End Interface
Public Class testClass
    Public Sub accessDefaultProperty()
        Dim testObj As Iface3
        Dim testInt As Integer = testObj(1)
    End Sub
End Class
```

<span data-ttu-id="0b13d-107">При указании `testObj(1)` компилятор пытается разрешить его в свойство по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0b13d-107">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="0b13d-108">Однако существует два возможных свойства по умолчанию из-за наследуемых интерфейсов, поэтому компилятор сообщает об этой ошибке.</span><span class="sxs-lookup"><span data-stu-id="0b13d-108">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>

<span data-ttu-id="0b13d-109">**Идентификатор ошибки:** BC30686</span><span class="sxs-lookup"><span data-stu-id="0b13d-109">**Error ID:** BC30686</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0b13d-110">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="0b13d-110">To correct this error</span></span>

- <span data-ttu-id="0b13d-111">Избегайте наследования членов с одинаковыми именами.</span><span class="sxs-lookup"><span data-stu-id="0b13d-111">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="0b13d-112">В предыдущем примере, если не `testObj` требуется ни один из членов, скажем, `Iface2` , объявить его следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0b13d-112">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>

  ```vb
  Dim testObj As Iface1
  ```

  <span data-ttu-id="0b13d-113">\-или-</span><span class="sxs-lookup"><span data-stu-id="0b13d-113">\-or-</span></span>

- <span data-ttu-id="0b13d-114">Реализуйте наследуемый интерфейс в классе.</span><span class="sxs-lookup"><span data-stu-id="0b13d-114">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="0b13d-115">Затем можно реализовать каждое из наследуемых свойств с разными именами.</span><span class="sxs-lookup"><span data-stu-id="0b13d-115">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="0b13d-116">Однако только один из них может быть свойством по умолчанию реализующего класса.</span><span class="sxs-lookup"><span data-stu-id="0b13d-116">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="0b13d-117">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="0b13d-117">The following example illustrates this.</span></span>

  ```vb
  Public Class useIface3
      Implements Iface3
      Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop
          ' Insert code to define Get and Set procedures for prop1.
      End Property
      Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop
          ' Insert code to define Get and Set procedures for prop2.
      End Property
  End Class
  ```

## <a name="see-also"></a><span data-ttu-id="0b13d-118">См. также</span><span class="sxs-lookup"><span data-stu-id="0b13d-118">See also</span></span>

- [<span data-ttu-id="0b13d-119">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="0b13d-119">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
