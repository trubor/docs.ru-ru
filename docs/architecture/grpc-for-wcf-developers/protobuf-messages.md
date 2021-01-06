---
title: Сообщения protobuf — gRPC для разработчиков WCF
description: Узнайте, как сообщения protobuf определяются в IDL и создаются в C#.
ms.date: 12/15/2020
ms.openlocfilehash: c1f2a3071d45dcbe4b98d747f19fed508bad102f
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938108"
---
# <a name="protobuf-messages"></a><span data-ttu-id="52ac6-103">Сообщения Protobuf</span><span class="sxs-lookup"><span data-stu-id="52ac6-103">Protobuf messages</span></span>

<span data-ttu-id="52ac6-104">В этом разделе описано, как объявлять сообщения в виде буфера протокола (protobuf) в `.proto` файлах.</span><span class="sxs-lookup"><span data-stu-id="52ac6-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="52ac6-105">В нем объясняются фундаментальные понятия чисел и типов полей, а также рассматривается код C#, `protoc` создаваемый компилятором.</span><span class="sxs-lookup"><span data-stu-id="52ac6-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span>

<span data-ttu-id="52ac6-106">Оставшаяся часть главы посвящена более подробному рассмотрению того, как различные типы данных представлены в protobuf.</span><span class="sxs-lookup"><span data-stu-id="52ac6-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="52ac6-107">Объявление сообщения</span><span class="sxs-lookup"><span data-stu-id="52ac6-107">Declaring a message</span></span>

<span data-ttu-id="52ac6-108">В Windows Communication Foundation (WCF) `Stock` класс для торгового приложения на фондовой бирже может быть определен как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="52ac6-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

<span data-ttu-id="52ac6-109">Чтобы реализовать эквивалентный класс в protobuf, необходимо объявить его в `.proto` файле.</span><span class="sxs-lookup"><span data-stu-id="52ac6-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="52ac6-110">`protoc`Компилятор создаст класс .NET как часть процесса сборки.</span><span class="sxs-lookup"><span data-stu-id="52ac6-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

<span data-ttu-id="52ac6-111">В первой строке объявляется используемая версия синтаксиса.</span><span class="sxs-lookup"><span data-stu-id="52ac6-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="52ac6-112">Версия 3 языка была выпущена в 2016.</span><span class="sxs-lookup"><span data-stu-id="52ac6-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="52ac6-113">Это версия, которую мы рекомендуем использовать для gRPC Services.</span><span class="sxs-lookup"><span data-stu-id="52ac6-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="52ac6-114">В `option csharp_namespace` строке указывается пространство имен, используемое для создаваемых типов C#.</span><span class="sxs-lookup"><span data-stu-id="52ac6-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="52ac6-115">Этот параметр будет проигнорирован при `.proto` компиляции файла для других языков.</span><span class="sxs-lookup"><span data-stu-id="52ac6-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="52ac6-116">Файлы protobuf часто содержат параметры, зависящие от языка, для нескольких языков.</span><span class="sxs-lookup"><span data-stu-id="52ac6-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="52ac6-117">`Stock`Определение сообщения указывает четыре поля.</span><span class="sxs-lookup"><span data-stu-id="52ac6-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="52ac6-118">Каждый из них имеет тип, имя и номер поля.</span><span class="sxs-lookup"><span data-stu-id="52ac6-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="52ac6-119">Номера полей</span><span class="sxs-lookup"><span data-stu-id="52ac6-119">Field numbers</span></span>

<span data-ttu-id="52ac6-120">Номера полей являются важной частью protobuf.</span><span class="sxs-lookup"><span data-stu-id="52ac6-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="52ac6-121">Они используются для указания полей в зашифрованных двоичных данных, что означает, что они не могут быть изменены с версии до версии вашей службы.</span><span class="sxs-lookup"><span data-stu-id="52ac6-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="52ac6-122">Преимущество в том, что возможна обратная совместимость и прямая совместимость.</span><span class="sxs-lookup"><span data-stu-id="52ac6-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="52ac6-123">Клиенты и службы будут игнорировать номера полей, о которых они не известны, при условии, что вероятность отсутствующих значений будет обработана.</span><span class="sxs-lookup"><span data-stu-id="52ac6-123">Clients and services will ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="52ac6-124">В двоичном формате номер поля объединяется с идентификатором типа.</span><span class="sxs-lookup"><span data-stu-id="52ac6-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="52ac6-125">Номера полей от 1 до 15 могут быть закодированы с помощью одного байта.</span><span class="sxs-lookup"><span data-stu-id="52ac6-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="52ac6-126">Числа от 16 до 2 047 принимают 2 байта.</span><span class="sxs-lookup"><span data-stu-id="52ac6-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="52ac6-127">Если в сообщении по какой-либо причине требуется более 2 047 полей для сообщения, можно увеличить значение.</span><span class="sxs-lookup"><span data-stu-id="52ac6-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="52ac6-128">Однобайтовые идентификаторы полей с номерами от 1 до 15 обеспечивают лучшую производительность, поэтому их следует использовать для самых базовых и часто используемых полей.</span><span class="sxs-lookup"><span data-stu-id="52ac6-128">The single-byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="52ac6-129">Типы</span><span class="sxs-lookup"><span data-stu-id="52ac6-129">Types</span></span>

<span data-ttu-id="52ac6-130">Объявления типов используют собственные скалярные типы данных protobuf, которые более подробно обсуждаются в [следующем разделе](protobuf-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="52ac6-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="52ac6-131">В оставшейся части этой главы будут рассмотрены встроенные типы protobuf и показано, как они связаны с распространенными типами .NET.</span><span class="sxs-lookup"><span data-stu-id="52ac6-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="52ac6-132">Protobuf изначально не поддерживает `decimal` тип, поэтому `double` вместо него используется.</span><span class="sxs-lookup"><span data-stu-id="52ac6-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="52ac6-133">Для приложений, требующих полной десятичной точности, ознакомьтесь с [разделом десятичные знаки](protobuf-data-types.md#decimals) в следующей части этой главы.</span><span class="sxs-lookup"><span data-stu-id="52ac6-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="52ac6-134">Сформированный код</span><span class="sxs-lookup"><span data-stu-id="52ac6-134">The generated code</span></span>

<span data-ttu-id="52ac6-135">При сборке приложения protobuf создает классы для каждого сообщения, сопоставляя собственные типы с типами C#.</span><span class="sxs-lookup"><span data-stu-id="52ac6-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="52ac6-136">Созданный `Stock` тип будет иметь следующую сигнатуру:</span><span class="sxs-lookup"><span data-stu-id="52ac6-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="52ac6-137">Фактически созданный код гораздо более сложен.</span><span class="sxs-lookup"><span data-stu-id="52ac6-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="52ac6-138">Причина заключается в том, что каждый класс содержит весь код, необходимый для сериализации и десериализации в двоичном формате сети.</span><span class="sxs-lookup"><span data-stu-id="52ac6-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="52ac6-139">Имена свойств</span><span class="sxs-lookup"><span data-stu-id="52ac6-139">Property names</span></span>

<span data-ttu-id="52ac6-140">Обратите внимание, что компилятор protobuf применяется `PascalCase` к именам свойств, хотя они были `snake_case` в `.proto` файле.</span><span class="sxs-lookup"><span data-stu-id="52ac6-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="52ac6-141">В соответствии с [руководством по стилю protobuf](https://developers.google.com/protocol-buffers/docs/style) рекомендуется использовать `snake_case` в определениях сообщений, чтобы создание кода для других платформ выработало ожидаемый вариант для своих соглашений.</span><span class="sxs-lookup"><span data-stu-id="52ac6-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="52ac6-142">[Назад](protocol-buffers.md)
>[Вперед](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="52ac6-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
