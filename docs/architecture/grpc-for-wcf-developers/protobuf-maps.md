---
title: Карты protobuf для словарей — gRPC для разработчиков WCF
description: Узнайте, как использовать карты protobuf для представления типов словарей в .NET.
ms.date: 12/15/2020
ms.openlocfilehash: d38270d4bc320cf1f758080c18843ed1d716b350
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938550"
---
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="5db71-103">Карты Protobuf для словарей</span><span class="sxs-lookup"><span data-stu-id="5db71-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="5db71-104">Важно иметь возможность представлять произвольные коллекции именованных значений в сообщениях.</span><span class="sxs-lookup"><span data-stu-id="5db71-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="5db71-105">В .NET это действие обычно обрабатывается с помощью типов словаря.</span><span class="sxs-lookup"><span data-stu-id="5db71-105">In .NET, this activity is commonly handled through dictionary types.</span></span> <span data-ttu-id="5db71-106">Эквивалентом <xref:System.Collections.Generic.IDictionary%602> типа .NET в буфере протокола (protobuf) является `map<key_type, value_type>` тип.</span><span class="sxs-lookup"><span data-stu-id="5db71-106">The equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type in Protocol Buffer (Protobuf) is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="5db71-107">В этом разделе показано, как объявить `map` тип в protobuf и как использовать созданный код.</span><span class="sxs-lookup"><span data-stu-id="5db71-107">This section shows how to declare a `map` type in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="5db71-108">В созданном коде `map` поля представлены свойствами типа, доступные только для чтения [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] .</span><span class="sxs-lookup"><span data-stu-id="5db71-108">In the generated code, `map` fields are represented by read-only properties of the [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] type.</span></span> <span data-ttu-id="5db71-109">Этот тип реализует стандартные интерфейсы коллекции .NET, включая <xref:System.Collections.Generic.IDictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="5db71-109">This type implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="5db71-110">Поля карт не могут повторяться непосредственно в определении сообщения.</span><span class="sxs-lookup"><span data-stu-id="5db71-110">Map fields can't be directly repeated in a message definition.</span></span> <span data-ttu-id="5db71-111">Однако можно создать вложенное сообщение, содержащее карту и использовать `repeated` тип сообщения, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="5db71-111">But you can create a nested message that contains a map and use `repeated` on the message type, as in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="5db71-112">Использование свойств Мапфиелд в коде</span><span class="sxs-lookup"><span data-stu-id="5db71-112">Using MapField properties in code</span></span>

<span data-ttu-id="5db71-113">`MapField`Свойства, созданные из `map` полей, доступны только для чтения и никогда не будут `null` .</span><span class="sxs-lookup"><span data-stu-id="5db71-113">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="5db71-114">Чтобы задать свойство Map, используйте `Add(IDictionary<TKey,TValue> values)` метод для свойства Empty, `MapField` чтобы скопировать значения из любого словаря .NET.</span><span class="sxs-lookup"><span data-stu-id="5db71-114">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="5db71-115">Дополнительные материалы</span><span class="sxs-lookup"><span data-stu-id="5db71-115">Further reading</span></span>

<span data-ttu-id="5db71-116">Дополнительные сведения о protobuf см. в официальной [документации protobuf](https://developers.google.com/protocol-buffers/docs/overview).</span><span class="sxs-lookup"><span data-stu-id="5db71-116">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

[map-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/map-field-t-key-t-value-

>[!div class="step-by-step"]
><span data-ttu-id="5db71-117">[Назад](protobuf-enums.md)
>[Вперед](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="5db71-117">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
