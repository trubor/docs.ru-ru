---
title: Зарезервированные поля protobuf — gRPC для разработчиков WCF
description: Сведения о зарезервированных полях для обеспечения совместимости между версиями.
ms.date: 12/15/2020
ms.openlocfilehash: d82043d619c5b3b81091ae4ea381e4778c1cf6ba
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938524"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="78a3a-103">Зарезервированные поля Protobuf</span><span class="sxs-lookup"><span data-stu-id="78a3a-103">Protobuf reserved fields</span></span>

<span data-ttu-id="78a3a-104">Гарантии обратной совместимости в буфере протокола (protobuf) полагаются на номера полей, которые всегда представляют один и тот же элемент данных.</span><span class="sxs-lookup"><span data-stu-id="78a3a-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="78a3a-105">Если поле удаляется из сообщения в новой версии службы, этот номер поля никогда не следует использовать повторно.</span><span class="sxs-lookup"><span data-stu-id="78a3a-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="78a3a-106">Это поведение можно применить с помощью `reserved` ключевого слова.</span><span class="sxs-lookup"><span data-stu-id="78a3a-106">You can enforce this behavior by using the `reserved` keyword.</span></span>

<span data-ttu-id="78a3a-107">Если `displayName` поля и `marketId` были удалены из `Stock` сообщения, определенного ранее, их номера полей должны быть зарезервированы, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="78a3a-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="78a3a-108">Также можно использовать `reserved` ключевое слово в качестве заполнителя для полей, которые могут быть добавлены в будущем.</span><span class="sxs-lookup"><span data-stu-id="78a3a-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="78a3a-109">Можно выразить смежные номера полей как диапазон с помощью `to` ключевого слова.</span><span class="sxs-lookup"><span data-stu-id="78a3a-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="78a3a-110">[Назад](protobuf-repeated.md)
>[Вперед](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="78a3a-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
