---
title: Как написать настраиваемые преобразователи для сериализации JSON — .NET
description: Узнайте, как создать настраиваемые преобразователи для классов сериализации JSON, предоставляемых в пространстве имен System.Text.Json.
ms.date: 12/09/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 33334ccd8bad4ac5a9f5dccde79ff3ae09ca8f89
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008868"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="b120c-103">Как написать настраиваемые преобразователи для сериализации JSON (маршалинг) в .NET</span><span class="sxs-lookup"><span data-stu-id="b120c-103">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="b120c-104">В этой статье показано, как создать настраиваемые преобразователи для классов сериализации JSON, предоставляемых в пространстве имен <xref:System.Text.Json>.</span><span class="sxs-lookup"><span data-stu-id="b120c-104">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="b120c-105">Общие сведения о `System.Text.Json` см. в статье [Как сериализировать и десериализировать (маршалирование и демаршалирование) JSON в .NET](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="b120c-105">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="b120c-106">*Преобразователь* — это класс, который преобразует объект или значение в формат JSON и обратно.</span><span class="sxs-lookup"><span data-stu-id="b120c-106">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="b120c-107">Пространство имен `System.Text.Json` содержит встроенные преобразователи для большинства примитивных типов, которые сопоставляются с примитивами JavaScript.</span><span class="sxs-lookup"><span data-stu-id="b120c-107">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="b120c-108">Вы можете создавать настраиваемые преобразователи для следующих целей:</span><span class="sxs-lookup"><span data-stu-id="b120c-108">You can write custom converters:</span></span>

* <span data-ttu-id="b120c-109">Чтобы переопределить поведение встроенного преобразователя, используемое по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b120c-109">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="b120c-110">Например, может потребоваться, чтобы значения `DateTime` были представлены в формате "мм/дд/гггг".</span><span class="sxs-lookup"><span data-stu-id="b120c-110">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format.</span></span> <span data-ttu-id="b120c-111">По умолчанию поддерживается стандарт ISO 8601-1:2019, включая профиль RFC 3339.</span><span class="sxs-lookup"><span data-stu-id="b120c-111">By default, ISO 8601-1:2019 is supported, including the RFC 3339 profile.</span></span> <span data-ttu-id="b120c-112">Дополнительные сведения см. в разделе [Поддержка DateTime и DateTimeOffset в System.Text.Json](../datetime/system-text-json-support.md).</span><span class="sxs-lookup"><span data-stu-id="b120c-112">For more information, see [DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md).</span></span>
* <span data-ttu-id="b120c-113">Для поддержки настраиваемого типа значения.</span><span class="sxs-lookup"><span data-stu-id="b120c-113">To support a custom value type.</span></span> <span data-ttu-id="b120c-114">Например, структуры `PhoneNumber`.</span><span class="sxs-lookup"><span data-stu-id="b120c-114">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="b120c-115">Вы также можете создать настраиваемые преобразователи для настройки или расширения `System.Text.Json` с функциональностью, не входящей в текущий выпуск.</span><span class="sxs-lookup"><span data-stu-id="b120c-115">You can also write custom converters to customize or extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="b120c-116">Далее в этой статье описываются следующие сценарии:</span><span class="sxs-lookup"><span data-stu-id="b120c-116">The following scenarios are covered later in this article:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="b120c-117">[Десериализация выводимых типов в свойства объекта](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="b120c-117">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="b120c-118">[Поддержка полиморфной десериализации](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="b120c-118">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="b120c-119">[Поддержка кругового пути для Stack\<T>](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="b120c-119">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="b120c-120">[Десериализация выводимых типов в свойства объекта](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="b120c-120">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="b120c-121">[Поддержка словаря с ключом, не являющимся строкой](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="b120c-121">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="b120c-122">[Поддержка полиморфной десериализации](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="b120c-122">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="b120c-123">[Поддержка кругового пути для Stack\<T>](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="b120c-123">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

<span data-ttu-id="b120c-124">При написании кода настраиваемого преобразователя помните о значительном снижении производительности при использовании новых экземпляров <xref:System.Text.Json.JsonSerializerOptions>.</span><span class="sxs-lookup"><span data-stu-id="b120c-124">In the code you write for a custom converter, be aware of the substantial performance penalty for using new <xref:System.Text.Json.JsonSerializerOptions> instances.</span></span> <span data-ttu-id="b120c-125">Дополнительные сведения см. в разделе [Повторное использование экземпляров JsonSerializerOptions](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span><span class="sxs-lookup"><span data-stu-id="b120c-125">For more information, see [Reuse JsonSerializerOptions instances](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="b120c-126">Шаблоны настраиваемых преобразователей</span><span class="sxs-lookup"><span data-stu-id="b120c-126">Custom converter patterns</span></span>

<span data-ttu-id="b120c-127">Существует два шаблона для создания настраиваемого преобразователя: базовый шаблон и шаблон фабрики.</span><span class="sxs-lookup"><span data-stu-id="b120c-127">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="b120c-128">Шаблон фабрики предназначен для преобразователей, обрабатывающих типы `Enum` или открытые универсальные шаблоны.</span><span class="sxs-lookup"><span data-stu-id="b120c-128">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="b120c-129">Базовый шаблон предназначен для неуниверсальных и закрытых универсальных типов.</span><span class="sxs-lookup"><span data-stu-id="b120c-129">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="b120c-130">Например, для преобразователей следующих типов требуется шаблон фабрики:</span><span class="sxs-lookup"><span data-stu-id="b120c-130">For example, converters for the following types require the factory pattern:</span></span>

* <xref:System.Collections.Generic.Dictionary%602>
* <xref:System.Enum>
* <xref:System.Collections.Generic.List%601>

<span data-ttu-id="b120c-131">Ниже приведены некоторые примеры типов, которые могут быть обработаны базовым шаблоном:</span><span class="sxs-lookup"><span data-stu-id="b120c-131">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* <xref:System.DateTime>
* <xref:System.Int32>

<span data-ttu-id="b120c-132">Базовый шаблон создает класс, который может работать с одним типом.</span><span class="sxs-lookup"><span data-stu-id="b120c-132">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="b120c-133">Шаблон фабрики создает класс, который в среде выполнения определяет, какой конкретный тип требуется, и динамически создает соответствующий преобразователь.</span><span class="sxs-lookup"><span data-stu-id="b120c-133">The factory pattern creates a class that determines, at run time, which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="b120c-134">Пример базового преобразователя</span><span class="sxs-lookup"><span data-stu-id="b120c-134">Sample basic converter</span></span>

<span data-ttu-id="b120c-135">Следующий пример представляет собой преобразователь, который переопределяет сериализацию по умолчанию для существующего типа данных.</span><span class="sxs-lookup"><span data-stu-id="b120c-135">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="b120c-136">Для свойств `DateTimeOffset` преобразователь использует формат дд.мм.гггг.</span><span class="sxs-lookup"><span data-stu-id="b120c-136">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs":::

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="b120c-137">Пример преобразователя шаблона фабрики</span><span class="sxs-lookup"><span data-stu-id="b120c-137">Sample factory pattern converter</span></span>

<span data-ttu-id="b120c-138">В следующем примере кода показан настраиваемый преобразователь, который работает с `Dictionary<Enum,TValue>`.</span><span class="sxs-lookup"><span data-stu-id="b120c-138">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="b120c-139">Код соответствует шаблону фабрики, так как первый параметр универсального типа является `Enum`, а второй — открытым.</span><span class="sxs-lookup"><span data-stu-id="b120c-139">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="b120c-140">Метод `CanConvert` возвращает `true` только для `Dictionary` с двумя универсальными параметрами, первый из которых является типом `Enum`.</span><span class="sxs-lookup"><span data-stu-id="b120c-140">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="b120c-141">Внутренний преобразователь получает существующий преобразователь для работы с любым типом, предоставленным во время выполнения для `TValue`.</span><span class="sxs-lookup"><span data-stu-id="b120c-141">The inner converter gets an existing converter to handle whichever type is provided at run time for `TValue`.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

<span data-ttu-id="b120c-142">Предыдущий код аналогичен тому, который приведен в разделе [Поддержка словаря с ключом, не являющимся строкой](#support-dictionary-with-non-string-key) далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="b120c-142">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="b120c-143">Инструкции по базовому шаблону</span><span class="sxs-lookup"><span data-stu-id="b120c-143">Steps to follow the basic pattern</span></span>

<span data-ttu-id="b120c-144">Ниже описывается, как создать преобразователь с помощью базового шаблона:</span><span class="sxs-lookup"><span data-stu-id="b120c-144">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="b120c-145">Создайте класс, производный от <xref:System.Text.Json.Serialization.JsonConverter%601>, где `T` — это тип для сериализации и десериализации.</span><span class="sxs-lookup"><span data-stu-id="b120c-145">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="b120c-146">Переопределите метод `Read`, чтобы десериализировать входящие данные JSON и преобразовать их в тип `T`.</span><span class="sxs-lookup"><span data-stu-id="b120c-146">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="b120c-147">Для чтения JSON используйте передаваемое в метод значение <xref:System.Text.Json.Utf8JsonReader>.</span><span class="sxs-lookup"><span data-stu-id="b120c-147">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="b120c-148">Переопределите метод `Write` для сериализации входящего объекта типа `T`.</span><span class="sxs-lookup"><span data-stu-id="b120c-148">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="b120c-149">Для записи JSON используйте передаваемое в метод значение <xref:System.Text.Json.Utf8JsonWriter>.</span><span class="sxs-lookup"><span data-stu-id="b120c-149">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="b120c-150">Переопределяйте метод `CanConvert` только при необходимости.</span><span class="sxs-lookup"><span data-stu-id="b120c-150">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="b120c-151">Реализация по умолчанию возвращает `true`, если тип для преобразования имеет тип `T`.</span><span class="sxs-lookup"><span data-stu-id="b120c-151">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="b120c-152">Поэтому для преобразователей, поддерживающих только тип `T`, не требуется переопределять этот метод.</span><span class="sxs-lookup"><span data-stu-id="b120c-152">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="b120c-153">Пример преобразователя, в котором требуется переопределить этот метод, см. в разделе [Поддержка полиморфной десериализации](#support-polymorphic-deserialization) далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="b120c-153">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="b120c-154">Вы можете ссылаться на [исходный код встроенных преобразователей](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) в качестве эталонных реализаций для написания настраиваемых преобразователей.</span><span class="sxs-lookup"><span data-stu-id="b120c-154">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="b120c-155">Инструкции по шаблону фабрики</span><span class="sxs-lookup"><span data-stu-id="b120c-155">Steps to follow the factory pattern</span></span>

<span data-ttu-id="b120c-156">Ниже описывается, как создать преобразователь с помощью шаблона фабрики:</span><span class="sxs-lookup"><span data-stu-id="b120c-156">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="b120c-157">Создайте класс, наследующий от класса <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span><span class="sxs-lookup"><span data-stu-id="b120c-157">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="b120c-158">Переопределите метод `CanConvert`, чтобы он возвращал значение true, если преобразователь может обрабатывать этот тип.</span><span class="sxs-lookup"><span data-stu-id="b120c-158">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="b120c-159">Например, если преобразователь предназначен для `List<T>`, он может обрабатывать только `List<int>`, `List<string>` и `List<DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="b120c-159">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="b120c-160">Переопределите метод `CreateConverter`, чтобы он возвращал экземпляр класса преобразователя, обрабатывающего тип для преобразования, который будет предоставлен во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="b120c-160">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at run time.</span></span>
* <span data-ttu-id="b120c-161">Создайте класс преобразователя с помощью метода `CreateConverter`.</span><span class="sxs-lookup"><span data-stu-id="b120c-161">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="b120c-162">Шаблон фабрики необходим для открытых универсальных шаблонов, так как код для преобразования объекта в строку и обратно не совпадает для всех типов.</span><span class="sxs-lookup"><span data-stu-id="b120c-162">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="b120c-163">Преобразователь для открытого универсального типа (например, `List<T>`) должен создать преобразователь для закрытого универсального типа (например, `List<DateTime>`) в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="b120c-163">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="b120c-164">Необходимо написать код для обработки каждого закрытого универсального типа, который может обрабатывать преобразователь.</span><span class="sxs-lookup"><span data-stu-id="b120c-164">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="b120c-165">Тип `Enum` похож на открытый универсальный тип: преобразователь для `Enum` должен создать преобразователь для определенного типа `Enum` (например, `WeekdaysEnum`) в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="b120c-165">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="b120c-166">Обработка ошибок</span><span class="sxs-lookup"><span data-stu-id="b120c-166">Error handling</span></span>

<span data-ttu-id="b120c-167">Сериализатор обеспечивает специальную обработку типов исключений <xref:System.Text.Json.JsonException> и <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="b120c-167">The serializer provides special handling for exception types <xref:System.Text.Json.JsonException> and <xref:System.NotSupportedException>.</span></span>

### <a name="jsonexception"></a><span data-ttu-id="b120c-168">JsonException</span><span class="sxs-lookup"><span data-stu-id="b120c-168">JsonException</span></span>

<span data-ttu-id="b120c-169">Если выдается исключение `JsonException` без сообщения, сериализатор создает сообщение, содержащее путь к части JSON, вызвавшей ошибку.</span><span class="sxs-lookup"><span data-stu-id="b120c-169">If you throw a `JsonException` without a message, the serializer creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="b120c-170">Например, инструкция `throw new JsonException()` выдает сообщение об ошибке, как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="b120c-170">For example, the statement `throw new JsonException()` produces an error message like the following example:</span></span>

```output
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="b120c-171">Если вы выдаете сообщение (например, `throw new JsonException("Error occurred")`), сериализатор по-прежнему устанавливает свойства <xref:System.Text.Json.JsonException.Path>, <xref:System.Text.Json.JsonException.LineNumber> и <xref:System.Text.Json.JsonException.BytePositionInLine>.</span><span class="sxs-lookup"><span data-stu-id="b120c-171">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the serializer still sets the <xref:System.Text.Json.JsonException.Path>, <xref:System.Text.Json.JsonException.LineNumber>, and <xref:System.Text.Json.JsonException.BytePositionInLine> properties.</span></span>

### <a name="notsupportedexception"></a><span data-ttu-id="b120c-172">NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="b120c-172">NotSupportedException</span></span>

<span data-ttu-id="b120c-173">При возникновении `NotSupportedException` вы всегда получаете сведения о пути в сообщении.</span><span class="sxs-lookup"><span data-stu-id="b120c-173">If you throw a `NotSupportedException`, you always get the path information in the message.</span></span> <span data-ttu-id="b120c-174">Если сообщение указано, сведения о пути добавляются к нему.</span><span class="sxs-lookup"><span data-stu-id="b120c-174">If you provide a message, the path information is appended to it.</span></span> <span data-ttu-id="b120c-175">Например, инструкция `throw new NotSupportedException("Error occurred.")` выдает сообщение об ошибке, как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="b120c-175">For example, the statement `throw new NotSupportedException("Error occurred.")` produces an error message like the following example:</span></span>

```output
Error occurred. The unsupported member type is located on type
'System.Collections.Generic.Dictionary`2[Samples.SummaryWords,System.Int32]'.
Path: $.TemperatureRanges | LineNumber: 4 | BytePositionInLine: 24
```

### <a name="when-to-throw-which-exception-type"></a><span data-ttu-id="b120c-176">Типы исключений, которые следует использовать в различных случаях</span><span class="sxs-lookup"><span data-stu-id="b120c-176">When to throw which exception type</span></span>

<span data-ttu-id="b120c-177">Если полезные данные JSON содержат токены, которые не являются допустимыми для десериализуемого типа, необходимо выдать исключение `JsonException`.</span><span class="sxs-lookup"><span data-stu-id="b120c-177">When the JSON payload contains tokens that are not valid for the type being deserialized, throw a `JsonException`.</span></span>

<span data-ttu-id="b120c-178">Если требуется запретить определенные типы, используйте исключение `NotSupportedException`.</span><span class="sxs-lookup"><span data-stu-id="b120c-178">When you want to disallow certain types, throw a `NotSupportedException`.</span></span> <span data-ttu-id="b120c-179">Это исключение автоматически выдается сериализатором для типов, которые не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="b120c-179">This exception is what the serializer automatically throws for types that are not supported.</span></span> <span data-ttu-id="b120c-180">Например, тип `System.Type` не поддерживается по соображениям безопасности, поэтому попытка десериализации приведет к исключению `NotSupportedException`.</span><span class="sxs-lookup"><span data-stu-id="b120c-180">For example, `System.Type` is not supported for security reasons, so an attempt to deserialize it results in a `NotSupportedException`.</span></span>

<span data-ttu-id="b120c-181">При необходимости можно вызвать и другие исключения, но в них не будут автоматически включаться сведения о пути JSON.</span><span class="sxs-lookup"><span data-stu-id="b120c-181">You can throw other exceptions as needed, but they don't automatically include JSON path information.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="b120c-182">Регистрация настраиваемого преобразователя</span><span class="sxs-lookup"><span data-stu-id="b120c-182">Register a custom converter</span></span>

<span data-ttu-id="b120c-183">*Зарегистрируйте* настраиваемый преобразователь, чтобы использовать методы `Serialize` и `Deserialize`.</span><span class="sxs-lookup"><span data-stu-id="b120c-183">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="b120c-184">Воспользуйтесь одним из перечисленных ниже подходов.</span><span class="sxs-lookup"><span data-stu-id="b120c-184">Choose one of the following approaches:</span></span>

* <span data-ttu-id="b120c-185">Добавьте экземпляр класса преобразователя в коллекцию <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b120c-185">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="b120c-186">Примените атрибут [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) к свойствам, для которых требуется настраиваемый преобразователь.</span><span class="sxs-lookup"><span data-stu-id="b120c-186">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="b120c-187">Примените атрибут [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) к классу или структуре, представляющей настраиваемый тип значения.</span><span class="sxs-lookup"><span data-stu-id="b120c-187">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="b120c-188">Пример регистрации — коллекция преобразователей</span><span class="sxs-lookup"><span data-stu-id="b120c-188">Registration sample - Converters collection</span></span>

<span data-ttu-id="b120c-189">Ниже приведен пример, который делает <xref:System.ComponentModel.DateTimeOffsetConverter> классом по умолчанию для свойств типа <xref:System.DateTimeOffset>.</span><span class="sxs-lookup"><span data-stu-id="b120c-189">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Serialize":::

<span data-ttu-id="b120c-190">Предположим, что вы сериализуете экземпляр следующего типа.</span><span class="sxs-lookup"><span data-stu-id="b120c-190">Suppose you serialize an instance of the following type:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

<span data-ttu-id="b120c-191">Ниже приведен пример выходных данных JSON, в котором показано использование настраиваемого преобразователя.</span><span class="sxs-lookup"><span data-stu-id="b120c-191">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="b120c-192">Следующий код использует тот же подход для десериализации с помощью настраиваемого преобразователя `DateTimeOffset`.</span><span class="sxs-lookup"><span data-stu-id="b120c-192">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="b120c-193">Пример регистрации — [JsonConverter] для свойства</span><span class="sxs-lookup"><span data-stu-id="b120c-193">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="b120c-194">В следующем примере кода выбирается настраиваемый преобразователь для свойства `Date`.</span><span class="sxs-lookup"><span data-stu-id="b120c-194">The following code selects a custom converter for the `Date` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithConverterAttribute":::

<span data-ttu-id="b120c-195">В коде для сериализации `WeatherForecastWithConverterAttribute` не нужно использовать `JsonSerializeOptions.Converters`.</span><span class="sxs-lookup"><span data-stu-id="b120c-195">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Serialize":::

<span data-ttu-id="b120c-196">В коде для десериализации также не нужно использовать `Converters`.</span><span class="sxs-lookup"><span data-stu-id="b120c-196">The code to deserialize also doesn't require the use of `Converters`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="b120c-197">Пример регистрации — [JsonConverter] для типа</span><span class="sxs-lookup"><span data-stu-id="b120c-197">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="b120c-198">Ниже приведен код, создающий структуру и применяющий к ней атрибут `[JsonConverter]`.</span><span class="sxs-lookup"><span data-stu-id="b120c-198">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Temperature.cs":::

<span data-ttu-id="b120c-199">Ниже приведен настраиваемый преобразователь для предыдущей структуры.</span><span class="sxs-lookup"><span data-stu-id="b120c-199">Here's the custom converter for the preceding struct:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/TemperatureConverter.cs":::

<span data-ttu-id="b120c-200">Атрибут `[JsonConvert]` в структуре регистрирует настраиваемый преобразователь в качестве значения по умолчанию для свойств типа `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="b120c-200">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="b120c-201">Этот преобразователь автоматически используется в свойстве `TemperatureCelsius` следующего типа при его сериализации или десериализации.</span><span class="sxs-lookup"><span data-stu-id="b120c-201">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithTemperatureStruct":::

## <a name="converter-registration-precedence"></a><span data-ttu-id="b120c-202">Очередность регистрации преобразователей</span><span class="sxs-lookup"><span data-stu-id="b120c-202">Converter registration precedence</span></span>

<span data-ttu-id="b120c-203">Во время сериализации или десериализации выбирается преобразователь для каждого элемента JSON в следующем порядке — от наивысшего приоритета к наименьшему.</span><span class="sxs-lookup"><span data-stu-id="b120c-203">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="b120c-204">Атрибут `[JsonConverter]` применяется к свойству.</span><span class="sxs-lookup"><span data-stu-id="b120c-204">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="b120c-205">Преобразователь, добавляемый в коллекцию `Converters`.</span><span class="sxs-lookup"><span data-stu-id="b120c-205">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="b120c-206">Атрибут `[JsonConverter]` применяется к настраиваемому типу значения или POCO.</span><span class="sxs-lookup"><span data-stu-id="b120c-206">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="b120c-207">Если в коллекции `Converters` зарегистрировано несколько настраиваемых преобразователей для типов, то используется первый преобразователь, возвращающий значение true для `CanConvert`.</span><span class="sxs-lookup"><span data-stu-id="b120c-207">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="b120c-208">Встроенный преобразователь выбирается только в том случае, если соответствующий настраиваемый преобразователь не зарегистрирован.</span><span class="sxs-lookup"><span data-stu-id="b120c-208">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="b120c-209">Примеры преобразователей для выполнения стандартных сценариев</span><span class="sxs-lookup"><span data-stu-id="b120c-209">Converter samples for common scenarios</span></span>

<span data-ttu-id="b120c-210">В следующих разделах приведены примеры преобразователей, в которых рассматриваются распространенные сценарии, необрабатываемые встроенными функциями.</span><span class="sxs-lookup"><span data-stu-id="b120c-210">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="b120c-211">[Десериализация выводимых типов в свойства объекта](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="b120c-211">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="b120c-212">[Поддержка полиморфной десериализации](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="b120c-212">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="b120c-213">[Поддержка кругового пути для Stack\<T>](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="b120c-213">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="b120c-214">[Десериализация выводимых типов в свойства объекта](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="b120c-214">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="b120c-215">[Поддержка словаря с ключом, не являющимся строкой](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="b120c-215">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="b120c-216">[Поддержка полиморфной десериализации](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="b120c-216">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="b120c-217">[Поддержка кругового пути для Stack\<T>](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="b120c-217">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="b120c-218">Десериализация выводимых типов в свойства объекта</span><span class="sxs-lookup"><span data-stu-id="b120c-218">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="b120c-219">При десериализации в свойство типа `object` создается объект `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="b120c-219">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="b120c-220">Причина заключается в том, что десериализатор не знает, какой тип среды выполнения создать, и не пытается угадать.</span><span class="sxs-lookup"><span data-stu-id="b120c-220">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="b120c-221">Например, если свойство JSON имеет значение true, десериализатор не определит, что значение является `Boolean`, а если у элемента есть значение 01/01/2019, десериализатор не определит, что это `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="b120c-221">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="b120c-222">Определение типа может быть неточным.</span><span class="sxs-lookup"><span data-stu-id="b120c-222">Type inference can be inaccurate.</span></span> <span data-ttu-id="b120c-223">Если десериализатор анализирует число JSON, не имеющее десятичного разделителя в качестве `long`, это может привести к проблемам в виде выхода за пределы диапазона, если значение первоначально было сериализовано как `ulong` или `BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="b120c-223">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="b120c-224">Анализ числа с десятичным разделителем в качестве `double` может привести к потере точности, если это число было первоначально сериализовано как `decimal`.</span><span class="sxs-lookup"><span data-stu-id="b120c-224">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="b120c-225">В следующем коде показан настраиваемый преобразователь для свойств `object` сценариев с определением типа.</span><span class="sxs-lookup"><span data-stu-id="b120c-225">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="b120c-226">Код преобразует:</span><span class="sxs-lookup"><span data-stu-id="b120c-226">The code converts:</span></span>

* <span data-ttu-id="b120c-227">`true` и `false` в `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b120c-227">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="b120c-228">Числа без десятичного числа в `long`.</span><span class="sxs-lookup"><span data-stu-id="b120c-228">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="b120c-229">Числа с десятичным числом в `double`.</span><span class="sxs-lookup"><span data-stu-id="b120c-229">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="b120c-230">Даты в `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="b120c-230">Dates to `DateTime`</span></span>
* <span data-ttu-id="b120c-231">Строки в `string`.</span><span class="sxs-lookup"><span data-stu-id="b120c-231">Strings to `string`</span></span>
* <span data-ttu-id="b120c-232">Все остальное в `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="b120c-232">Everything else to `JsonElement`</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs":::

<span data-ttu-id="b120c-233">В следующем коде регистрируется преобразователь.</span><span class="sxs-lookup"><span data-stu-id="b120c-233">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs" id="Register":::

<span data-ttu-id="b120c-234">Ниже приведен пример типа со свойствами `object`.</span><span class="sxs-lookup"><span data-stu-id="b120c-234">Here's an example type with `object` properties:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithObjectProperties":::

<span data-ttu-id="b120c-235">Следующий пример JSON для десериализации содержит значения, которые будут десериализованы как `DateTime`, `long` и `string`.</span><span class="sxs-lookup"><span data-stu-id="b120c-235">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="b120c-236">Без настраиваемого преобразователя десериализация помещает `JsonElement` в каждое свойство.</span><span class="sxs-lookup"><span data-stu-id="b120c-236">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="b120c-237">В [папке модульного теста](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) в пространстве имен `System.Text.Json.Serialization` содержится больше примеров настраиваемых преобразователей, обрабатывающих десериализацию свойств `object`.</span><span class="sxs-lookup"><span data-stu-id="b120c-237">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

::: zone pivot="dotnet-core-3-1"

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="b120c-238">Поддержка словаря с ключом, не являющимся строкой</span><span class="sxs-lookup"><span data-stu-id="b120c-238">Support Dictionary with non-string key</span></span>

<span data-ttu-id="b120c-239">Встроенная поддержка коллекций словарей предназначена для `Dictionary<string, TValue>`.</span><span class="sxs-lookup"><span data-stu-id="b120c-239">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="b120c-240">То есть ключ должен быть строкой.</span><span class="sxs-lookup"><span data-stu-id="b120c-240">That is, the key must be a string.</span></span> <span data-ttu-id="b120c-241">Для поддержки словаря с целым числом или другим типом в качестве ключа нужен настраиваемый преобразователь.</span><span class="sxs-lookup"><span data-stu-id="b120c-241">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="b120c-242">В следующем примере кода показан настраиваемый преобразователь, который работает с `Dictionary<Enum,TValue>`.</span><span class="sxs-lookup"><span data-stu-id="b120c-242">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

<span data-ttu-id="b120c-243">В следующем коде регистрируется преобразователь.</span><span class="sxs-lookup"><span data-stu-id="b120c-243">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs" id="Register":::

<span data-ttu-id="b120c-244">Преобразователь может сериализовать и десериализировать свойство `TemperatureRanges` следующего класса, который использует `Enum`.</span><span class="sxs-lookup"><span data-stu-id="b120c-244">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnumDictionary":::

<span data-ttu-id="b120c-245">Выходные данные JSON из сериализации выглядят так, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="b120c-245">The JSON output from serialization looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

<span data-ttu-id="b120c-246">В [папке модульного теста](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) в пространстве имен `System.Text.Json.Serialization` содержится больше примеров настраиваемых преобразователей, обрабатывающих словари с ключом, не являющимся строкой.</span><span class="sxs-lookup"><span data-stu-id="b120c-246">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>
::: zone-end

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="b120c-247">Поддержка полиморфной десериализации</span><span class="sxs-lookup"><span data-stu-id="b120c-247">Support polymorphic deserialization</span></span>

<span data-ttu-id="b120c-248">Встроенные функции предоставляют ограниченный диапазон [полиморфной сериализации](system-text-json-polymorphism.md), но совсем не поддерживают десериализацию.</span><span class="sxs-lookup"><span data-stu-id="b120c-248">Built-in features provide a limited range of [polymorphic serialization](system-text-json-polymorphism.md) but no support for deserialization at all.</span></span> <span data-ttu-id="b120c-249">Для десериализации требуется настраиваемый преобразователь.</span><span class="sxs-lookup"><span data-stu-id="b120c-249">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="b120c-250">Например, предположим, что имеется абстрактный базовый класс `Person` с производными классами `Employee` и `Customer`.</span><span class="sxs-lookup"><span data-stu-id="b120c-250">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="b120c-251">Полиморфная десериализации означает, что во время разработки можно указать `Person` в качестве цели десериализации, а объекты `Customer` и `Employee` в JSON правильно десериализованы во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="b120c-251">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at run time.</span></span> <span data-ttu-id="b120c-252">Во время десериализации необходимо найти признаки, которые определяют требуемый тип в JSON.</span><span class="sxs-lookup"><span data-stu-id="b120c-252">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="b120c-253">В каждом сценарии доступны различные типы признаков.</span><span class="sxs-lookup"><span data-stu-id="b120c-253">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="b120c-254">Например, может быть доступно свойство дискриминатора или придется полагаться на присутствие или отсутствие конкретного свойства.</span><span class="sxs-lookup"><span data-stu-id="b120c-254">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="b120c-255">В текущем выпуске `System.Text.Json` не предоставлены атрибуты для указания способов обработки сценариев полиморфной десериализации, поэтому необходимо использовать настраиваемые преобразователи.</span><span class="sxs-lookup"><span data-stu-id="b120c-255">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="b120c-256">В следующем коде показан базовый класс, два производных класса и настраиваемый преобразователь для них.</span><span class="sxs-lookup"><span data-stu-id="b120c-256">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="b120c-257">Преобразователь использует свойство дискриминатора для выполнения в полиморфной десериализации.</span><span class="sxs-lookup"><span data-stu-id="b120c-257">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="b120c-258">Дискриминатор типа не находится в определениях классов, но создается во время сериализации и считывается во время десериализации.</span><span class="sxs-lookup"><span data-stu-id="b120c-258">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Person.cs" id="Person":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs":::

<span data-ttu-id="b120c-259">В следующем коде регистрируется преобразователь.</span><span class="sxs-lookup"><span data-stu-id="b120c-259">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs" id="Register":::

<span data-ttu-id="b120c-260">Преобразователь может десериализировать JSON, созданный с помощью того же преобразователя для сериализации, например.</span><span class="sxs-lookup"><span data-stu-id="b120c-260">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

<span data-ttu-id="b120c-261">Код преобразователя в предыдущем примере считывает и записывает каждое свойство вручную.</span><span class="sxs-lookup"><span data-stu-id="b120c-261">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="b120c-262">Альтернативой является вызов `Deserialize` или `Serialize` для выполнения некоторых операций.</span><span class="sxs-lookup"><span data-stu-id="b120c-262">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="b120c-263">Пример см. в [этой публикации на сайте StackOverflow](https://stackoverflow.com/a/59744873/12509023).</span><span class="sxs-lookup"><span data-stu-id="b120c-263">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

### <a name="support-round-trip-for-stackt"></a><span data-ttu-id="b120c-264">Поддержка кругового пути для Stack\<T></span><span class="sxs-lookup"><span data-stu-id="b120c-264">Support round trip for Stack\<T></span></span>

<span data-ttu-id="b120c-265">Если десериализовать строку JSON в объект <xref:System.Collections.Generic.Stack%601>, а затем сериализовать этот объект, содержимое стека будет организовано в обратном порядке.</span><span class="sxs-lookup"><span data-stu-id="b120c-265">If you deserialize a JSON string into a <xref:System.Collections.Generic.Stack%601> object and then serialize that object, the contents of the stack are in reverse order.</span></span> <span data-ttu-id="b120c-266">Это поведение применимо к следующим типам и интерфейсу, а также пользовательским типам, производным от них:</span><span class="sxs-lookup"><span data-stu-id="b120c-266">This behavior applies to the following types and interface, and user-defined types that derive from them:</span></span>

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

<span data-ttu-id="b120c-267">Чтобы включить поддержку сериализации и десериализации, сохраняющей исходный порядок в стеке, требуется пользовательский преобразователь.</span><span class="sxs-lookup"><span data-stu-id="b120c-267">To support serialization and deserialization that retains the original order in the stack, a custom converter is required.</span></span>

<span data-ttu-id="b120c-268">В следующем коде показан пользовательский преобразователь, включающий поддержку кругового пути для объектов `Stack<T>`:</span><span class="sxs-lookup"><span data-stu-id="b120c-268">The following code shows a custom converter that enables round-tripping to and from `Stack<T>` objects:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs":::

<span data-ttu-id="b120c-269">В следующем коде регистрируется преобразователь.</span><span class="sxs-lookup"><span data-stu-id="b120c-269">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs" id="Register":::

## <a name="handle-null-values"></a><span data-ttu-id="b120c-270">Обработка значений NULL</span><span class="sxs-lookup"><span data-stu-id="b120c-270">Handle null values</span></span>

<span data-ttu-id="b120c-271">По умолчанию сериализатор обрабатывает значения NULL следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b120c-271">By default, the serializer handles null values as follows:</span></span>

* <span data-ttu-id="b120c-272">Для ссылочных типов и типов <xref:System.Nullable%601>:</span><span class="sxs-lookup"><span data-stu-id="b120c-272">For reference types and <xref:System.Nullable%601> types:</span></span>

  * <span data-ttu-id="b120c-273">Не передает `null` в пользовательские преобразователи для сериализации.</span><span class="sxs-lookup"><span data-stu-id="b120c-273">It does not pass `null` to custom converters on serialization.</span></span>
  * <span data-ttu-id="b120c-274">Не передает `JsonTokenType.Null` в пользовательские преобразователи для десериализации.</span><span class="sxs-lookup"><span data-stu-id="b120c-274">It does not pass `JsonTokenType.Null` to custom converters on deserialization.</span></span>
  * <span data-ttu-id="b120c-275">Возвращает экземпляр `null` при десериализации.</span><span class="sxs-lookup"><span data-stu-id="b120c-275">It returns a `null` instance on deserialization.</span></span>
  * <span data-ttu-id="b120c-276">Записывает `null` непосредственно с помощью модуля записи при сериализации.</span><span class="sxs-lookup"><span data-stu-id="b120c-276">It writes `null` directly with the writer on serialization.</span></span>

* <span data-ttu-id="b120c-277">Для типов значений, не допускающих значения NULL:</span><span class="sxs-lookup"><span data-stu-id="b120c-277">For non-nullable value types:</span></span>

  * <span data-ttu-id="b120c-278">Передает `JsonTokenType.Null` в пользовательские преобразователи для десериализации.</span><span class="sxs-lookup"><span data-stu-id="b120c-278">It passes `JsonTokenType.Null` to custom converters on deserialization.</span></span> <span data-ttu-id="b120c-279">(Если пользовательский преобразователь недоступен, внутренний преобразователь для типа выдает исключение `JsonException`.)</span><span class="sxs-lookup"><span data-stu-id="b120c-279">(If no custom converter is available, a `JsonException` exception is thrown by the internal converter for the type.)</span></span>

<span data-ttu-id="b120c-280">Это поведение обработки значений NULL в основном предназначено для оптимизации производительности путем пропуска дополнительного вызова преобразователя.</span><span class="sxs-lookup"><span data-stu-id="b120c-280">This null-handling behavior is primarily to optimize performance by skipping an extra call to the converter.</span></span> <span data-ttu-id="b120c-281">Кроме того, оно позволяет избежать принудительного выполнения преобразователей для типов, допускающих значение null, для проверки `null` в начале каждого переопределения метода `Read` и `Write`.</span><span class="sxs-lookup"><span data-stu-id="b120c-281">In addition, it avoids forcing converters for nullable types to check for `null` at the start of every `Read` and `Write` method override.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="b120c-282">Чтобы разрешить пользовательскому преобразователю обработку `null` для ссылочного типа или типа значения, переопределите <xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType>, чтобы возвратить `true`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="b120c-282">To enable a custom converter to handle `null` for a reference or value type, override <xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> to return `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterHandleNull.cs" highlight="19":::
::: zone-end

## <a name="other-custom-converter-samples"></a><span data-ttu-id="b120c-283">Другие примеры настраиваемых преобразователей</span><span class="sxs-lookup"><span data-stu-id="b120c-283">Other custom converter samples</span></span>

<span data-ttu-id="b120c-284">В статье о [миграции из Newtonsoft.Json в System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) приведены дополнительные примеры настраиваемых преобразователей.</span><span class="sxs-lookup"><span data-stu-id="b120c-284">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="b120c-285">В [папке модульных тестов](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) в исходном коде `System.Text.Json.Serialization` есть и другие примеры настраиваемых преобразователей, например:</span><span class="sxs-lookup"><span data-stu-id="b120c-285">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="b120c-286">[Преобразователь Int32, который преобразовывает значение NULL в 0 при десериализации](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs).</span><span class="sxs-lookup"><span data-stu-id="b120c-286">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="b120c-287">[Преобразователь Int32, который допускает как строковые, так и числовые значения при десериализации](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs).</span><span class="sxs-lookup"><span data-stu-id="b120c-287">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="b120c-288">[Преобразователь Enum](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs).</span><span class="sxs-lookup"><span data-stu-id="b120c-288">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="b120c-289">Преобразователь [List\<T>, который принимает внешние данные](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="b120c-289">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="b120c-290">[Преобразователь Long[], который работает с разделенным запятыми списком чисел](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="b120c-290">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="b120c-291">Если необходимо создать преобразователь, изменяющий поведение существующего встроенного преобразователя, можно получить [исходный код существующего преобразователя](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) в качестве отправной точки для настройки.</span><span class="sxs-lookup"><span data-stu-id="b120c-291">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b120c-292">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="b120c-292">Additional resources</span></span>

* <span data-ttu-id="b120c-293">[Исходный код для встроенных преобразователей](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="b120c-293">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span></span>
* [<span data-ttu-id="b120c-294">Общие сведения о System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="b120c-294">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="b120c-295">Практическое руководство. Сериализация и десериализация JSON</span><span class="sxs-lookup"><span data-stu-id="b120c-295">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="b120c-296">Создание экземпляров JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="b120c-296">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="b120c-297">Сопоставление без учета регистра</span><span class="sxs-lookup"><span data-stu-id="b120c-297">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="b120c-298">Настройка имен и значений свойств</span><span class="sxs-lookup"><span data-stu-id="b120c-298">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="b120c-299">Игнорирование свойств</span><span class="sxs-lookup"><span data-stu-id="b120c-299">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="b120c-300">Применение недействительного кода JSON</span><span class="sxs-lookup"><span data-stu-id="b120c-300">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="b120c-301">Обработка переполнения JSON</span><span class="sxs-lookup"><span data-stu-id="b120c-301">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="b120c-302">Сохранение ссылок</span><span class="sxs-lookup"><span data-stu-id="b120c-302">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="b120c-303">Неизменяемые типы и непубличные методы доступа</span><span class="sxs-lookup"><span data-stu-id="b120c-303">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="b120c-304">Полиморфная сериализация</span><span class="sxs-lookup"><span data-stu-id="b120c-304">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="b120c-305">Миграция из Newtonsoft.Json в System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="b120c-305">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="b120c-306">Настройка кодировки символов</span><span class="sxs-lookup"><span data-stu-id="b120c-306">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="b120c-307">Написание пользовательских сериализаторов и десериализаторов</span><span class="sxs-lookup"><span data-stu-id="b120c-307">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="b120c-308">Поддержка DateTime и DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="b120c-308">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="b120c-309">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="b120c-309">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="b120c-310">[Справочник по API System.Text.Json.Serialization](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="b120c-310">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
