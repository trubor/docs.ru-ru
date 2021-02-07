---
description: 'Дополнительные сведения: Справочник по схеме контракта данных'
title: Справочник по схеме контрактов данных
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: 3449340600ea5c55ef46433031e53266a218bd6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756647"
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="522e1-103">Справочник по схеме контрактов данных</span><span class="sxs-lookup"><span data-stu-id="522e1-103">Data Contract Schema Reference</span></span>

<span data-ttu-id="522e1-104">В данном разделе описывается подмножество схемы XML (XSD), используемое <xref:System.Runtime.Serialization.DataContractSerializer> для описания типов среды CLR, применяемых для сериализации XML.</span><span class="sxs-lookup"><span data-stu-id="522e1-104">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>

## <a name="datacontractserializer-mappings"></a><span data-ttu-id="522e1-105">DataContractSerializer - сопоставления</span><span class="sxs-lookup"><span data-stu-id="522e1-105">DataContractSerializer Mappings</span></span>

<span data-ttu-id="522e1-106">`DataContractSerializer`Сопоставляет типы CLR с XSD при экспорте метаданных из службы Windows Communication Foundation (WCF) с помощью конечной точки метаданных или [средства служебной программы метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="522e1-106">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a Windows Communication Foundation (WCF) service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="522e1-107">Дополнительные сведения см. в разделе [сериализатор контрактов данных](data-contract-serializer.md).</span><span class="sxs-lookup"><span data-stu-id="522e1-107">For more information, see [Data Contract Serializer](data-contract-serializer.md).</span></span>

<span data-ttu-id="522e1-108">`DataContractSerializer` также сопоставляет типы XSD типам среды CLR, когда для доступа к документам WSDL или XSD и создания контрактов данных для служб или клиентов используется Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="522e1-108">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>

<span data-ttu-id="522e1-109">Сопоставление типам CLR с помощью `DataContractSerializer`может выполняться только для экземпляров схемы XML, удовлетворяющих требованиям, описанным в данном документе.</span><span class="sxs-lookup"><span data-stu-id="522e1-109">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>

### <a name="support-levels"></a><span data-ttu-id="522e1-110">Уровни поддержки</span><span class="sxs-lookup"><span data-stu-id="522e1-110">Support Levels</span></span>

<span data-ttu-id="522e1-111">`DataContractSerializer` обеспечивает следующие уровни поддержки для данной функции схемы XML:</span><span class="sxs-lookup"><span data-stu-id="522e1-111">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>

- <span data-ttu-id="522e1-112">**поддерживается**.</span><span class="sxs-lookup"><span data-stu-id="522e1-112">**Supported**.</span></span> <span data-ttu-id="522e1-113">Существует явное сопоставление этой функции типам и (или) атрибутам CLR с помощью `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="522e1-113">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>

- <span data-ttu-id="522e1-114">**Игнорируется**.</span><span class="sxs-lookup"><span data-stu-id="522e1-114">**Ignored**.</span></span> <span data-ttu-id="522e1-115">Эта функция используется в схемах, импортируемых `DataContractSerializer`, но не влияет на создание кода.</span><span class="sxs-lookup"><span data-stu-id="522e1-115">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>

- <span data-ttu-id="522e1-116">**Запрещено**.</span><span class="sxs-lookup"><span data-stu-id="522e1-116">**Forbidden**.</span></span> <span data-ttu-id="522e1-117">`DataContractSerializer` не поддерживает импорт схемы с использованием данной функции.</span><span class="sxs-lookup"><span data-stu-id="522e1-117">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="522e1-118">Например, при доступе Svcutil.exe к WSDL посредством схемы, использующей данную функцию, доступ осуществляется с помощью <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="522e1-118">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="522e1-119">Это выполняется по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="522e1-119">This is by default.</span></span>

## <a name="general-information"></a><span data-ttu-id="522e1-120">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="522e1-120">General Information</span></span>

- <span data-ttu-id="522e1-121">Пространство имен схемы описывается в разделе [Схема XML](https://www.w3.org/2001/XMLSchema).</span><span class="sxs-lookup"><span data-stu-id="522e1-121">The schema namespace is described at [XML Schema](https://www.w3.org/2001/XMLSchema).</span></span> <span data-ttu-id="522e1-122">В этом документе используется префикс «xs».</span><span class="sxs-lookup"><span data-stu-id="522e1-122">The prefix "xs" is used in this document.</span></span>

- <span data-ttu-id="522e1-123">Атрибуты с пространством имен, отличным от пространства имен схемы, игнорируются.</span><span class="sxs-lookup"><span data-stu-id="522e1-123">Any attributes with a non-schema namespace are ignored.</span></span>

- <span data-ttu-id="522e1-124">Любые заметки (за исключением описанных в данном документе) игнорируются.</span><span class="sxs-lookup"><span data-stu-id="522e1-124">Any annotations (except for those described in this document) are ignored.</span></span>

### <a name="xsschema-attributes"></a><span data-ttu-id="522e1-125">\<xs:schema>: атрибуты</span><span class="sxs-lookup"><span data-stu-id="522e1-125">\<xs:schema>: attributes</span></span>

|<span data-ttu-id="522e1-126">attribute</span><span class="sxs-lookup"><span data-stu-id="522e1-126">Attribute</span></span>|<span data-ttu-id="522e1-127">DataContract</span><span class="sxs-lookup"><span data-stu-id="522e1-127">DataContract</span></span>|
|---------------|------------------|
|`attributeFormDefault`|<span data-ttu-id="522e1-128">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-128">Ignored.</span></span>|
|`blockDefault`|<span data-ttu-id="522e1-129">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-129">Ignored.</span></span>|
|`elementFormDefault`|<span data-ttu-id="522e1-130">Должен иметь полное имя.</span><span class="sxs-lookup"><span data-stu-id="522e1-130">Must be qualified.</span></span> <span data-ttu-id="522e1-131">Для того чтобы схема поддерживалась `DataContractSerializer`, все элементы должны иметь полное имя.</span><span class="sxs-lookup"><span data-stu-id="522e1-131">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="522e1-132">Это можно сделать, задав для параметра значение " xs:schema/@elementFormDefault полное" или задав xs:element/@form для каждого объявления отдельного элемента значение "квалифицировано".</span><span class="sxs-lookup"><span data-stu-id="522e1-132">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|
|`finalDefault`|<span data-ttu-id="522e1-133">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-133">Ignored.</span></span>|
|`Id`|<span data-ttu-id="522e1-134">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-134">Ignored.</span></span>|
|`targetNamespace`|<span data-ttu-id="522e1-135">Поддерживается и сопоставляется пространству имен контракта данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-135">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="522e1-136">Если данный атрибут не определен, используется пустое пространство имен.</span><span class="sxs-lookup"><span data-stu-id="522e1-136">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="522e1-137">Не может быть зарезервированным пространством имен `http://schemas.microsoft.com/2003/10/Serialization/` .</span><span class="sxs-lookup"><span data-stu-id="522e1-137">Cannot be the reserved namespace `http://schemas.microsoft.com/2003/10/Serialization/`.</span></span>|
|`version`|<span data-ttu-id="522e1-138">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-138">Ignored.</span></span>|

### <a name="xsschema-contents"></a><span data-ttu-id="522e1-139">\<xs:schema>: содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-139">\<xs:schema>: contents</span></span>

|<span data-ttu-id="522e1-140">Содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-140">Contents</span></span>|<span data-ttu-id="522e1-141">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-141">Schema</span></span>|
|--------------|------------|
|`include`|<span data-ttu-id="522e1-142">Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="522e1-142">Supported.</span></span> <span data-ttu-id="522e1-143">`DataContractSerializer` поддерживает xs:include и xs:import.</span><span class="sxs-lookup"><span data-stu-id="522e1-143">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="522e1-144">Однако при загрузке метаданных из локального файла средство Svcutil.exe ограничивает следование ссылкам `xs:include/@schemaLocation` и `xs:import/@location` .</span><span class="sxs-lookup"><span data-stu-id="522e1-144">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="522e1-145">В этом случае список файлов схемы должен передаваться по нештатному механизму, а не посредством `include` ; документы схемы, переданные посредством `include`, не учитываются.</span><span class="sxs-lookup"><span data-stu-id="522e1-145">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`redefine`|<span data-ttu-id="522e1-146">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-146">Forbidden.</span></span> <span data-ttu-id="522e1-147">Использование `xs:redefine` запрещено `DataContractSerializer` по соображениям безопасности: для `x:redefine` требуется следовать `schemaLocation` .</span><span class="sxs-lookup"><span data-stu-id="522e1-147">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="522e1-148">В некоторых случаях Svcutil.exe, использующее DataContract, ограничивает применение `schemaLocation`.</span><span class="sxs-lookup"><span data-stu-id="522e1-148">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|
|`import`|<span data-ttu-id="522e1-149">Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="522e1-149">Supported.</span></span> <span data-ttu-id="522e1-150">`DataContractSerializer` поддерживает `xs:include` и `xs:import`.</span><span class="sxs-lookup"><span data-stu-id="522e1-150">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="522e1-151">Однако при загрузке метаданных из локального файла средство Svcutil.exe ограничивает следование ссылкам `xs:include/@schemaLocation` и `xs:import/@location` .</span><span class="sxs-lookup"><span data-stu-id="522e1-151">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="522e1-152">В этом случае список файлов схемы должен передаваться по нештатному механизму, а не посредством `include` ; документы схемы, переданные посредством `include`, не учитываются.</span><span class="sxs-lookup"><span data-stu-id="522e1-152">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`simpleType`|<span data-ttu-id="522e1-153">Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="522e1-153">Supported.</span></span> <span data-ttu-id="522e1-154">См. раздел `xs:simpleType` .</span><span class="sxs-lookup"><span data-stu-id="522e1-154">See the `xs:simpleType` section.</span></span>|
|`complexType`|<span data-ttu-id="522e1-155">Поддерживается, сопоставляется контрактам данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-155">Supported, maps to data contracts.</span></span> <span data-ttu-id="522e1-156">См. раздел `xs:complexType` .</span><span class="sxs-lookup"><span data-stu-id="522e1-156">See the `xs:complexType` section.</span></span>|
|`group`|<span data-ttu-id="522e1-157">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-157">Ignored.</span></span> <span data-ttu-id="522e1-158">`DataContractSerializer` не поддерживает использование `xs:group`, `xs:attributeGroup`и `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="522e1-158">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="522e1-159">Эти объявления игнорируются как дочерние элементы `xs:schema`, но ссылки на них невозможны из `complexType` или других поддерживаемых конструкторов.</span><span class="sxs-lookup"><span data-stu-id="522e1-159">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`attributeGroup`|<span data-ttu-id="522e1-160">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-160">Ignored.</span></span> <span data-ttu-id="522e1-161">`DataContractSerializer` не поддерживает использование `xs:group`, `xs:attributeGroup`и `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="522e1-161">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="522e1-162">Эти объявления игнорируются как дочерние элементы `xs:schema`, но ссылки на них невозможны из `complexType` или других поддерживаемых конструкторов.</span><span class="sxs-lookup"><span data-stu-id="522e1-162">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`element`|<span data-ttu-id="522e1-163">Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="522e1-163">Supported.</span></span> <span data-ttu-id="522e1-164">См. «Объявление глобального элемента».</span><span class="sxs-lookup"><span data-stu-id="522e1-164">See Global Element Declaration (GED).</span></span>|
|`attribute`|<span data-ttu-id="522e1-165">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-165">Ignored.</span></span> <span data-ttu-id="522e1-166">`DataContractSerializer` не поддерживает использование `xs:group`, `xs:attributeGroup`и `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="522e1-166">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="522e1-167">Эти объявления игнорируются как дочерние элементы `xs:schema`, но ссылки на них невозможны из `complexType` или других поддерживаемых конструкторов.</span><span class="sxs-lookup"><span data-stu-id="522e1-167">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`notation`|<span data-ttu-id="522e1-168">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-168">Ignored.</span></span>|

## <a name="complex-types--xscomplextype"></a><span data-ttu-id="522e1-169">Сложные типы – \<xs:complexType></span><span class="sxs-lookup"><span data-stu-id="522e1-169">Complex Types – \<xs:complexType></span></span>

### <a name="general-information"></a><span data-ttu-id="522e1-170">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="522e1-170">General Information</span></span>

<span data-ttu-id="522e1-171">Каждый сложный тип \<xs:complexType> сопоставляется с контрактом данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-171">Each complex type \<xs:complexType> maps to a data contract.</span></span>

### <a name="xscomplextype-attributes"></a><span data-ttu-id="522e1-172">\<xs:complexType>: атрибуты</span><span class="sxs-lookup"><span data-stu-id="522e1-172">\<xs:complexType>: attributes</span></span>

|<span data-ttu-id="522e1-173">attribute</span><span class="sxs-lookup"><span data-stu-id="522e1-173">Attribute</span></span>|<span data-ttu-id="522e1-174">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-174">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="522e1-175">По умолчанию должен иметь значение false.</span><span class="sxs-lookup"><span data-stu-id="522e1-175">Must be false (default).</span></span>|
|`block`|<span data-ttu-id="522e1-176">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-176">Forbidden.</span></span>|
|`final`|<span data-ttu-id="522e1-177">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-177">Ignored.</span></span>|
|`id`|<span data-ttu-id="522e1-178">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-178">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="522e1-179">По умолчанию должен иметь значение false.</span><span class="sxs-lookup"><span data-stu-id="522e1-179">Must be false (default).</span></span>|
|`name`|<span data-ttu-id="522e1-180">Поддерживается и сопоставляется имени контракта данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-180">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="522e1-181">Если в имени имеются точки, выполняется попытка сопоставить тип внутреннему типу.</span><span class="sxs-lookup"><span data-stu-id="522e1-181">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="522e1-182">Например, сложный тип с именем `A.B` сопоставляется контракту данных, который является внутренним типом для типа с именем контракта данных `A`, но только в том случае, если данный контракт данных существует.</span><span class="sxs-lookup"><span data-stu-id="522e1-182">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="522e1-183">Может существовать более одного уровня вложения: например, `A.B.C` может быть внутренним типом, но только при условии, что и `A` , и `A.B` существуют.</span><span class="sxs-lookup"><span data-stu-id="522e1-183">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|

### <a name="xscomplextype-contents"></a><span data-ttu-id="522e1-184">\<xs:complexType>: содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-184">\<xs:complexType>: contents</span></span>

|<span data-ttu-id="522e1-185">Содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-185">Contents</span></span>|<span data-ttu-id="522e1-186">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-186">Schema</span></span>|
|--------------|------------|
|`simpleContent`|<span data-ttu-id="522e1-187">Расширения запрещены.</span><span class="sxs-lookup"><span data-stu-id="522e1-187">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="522e1-188">Ограничение разрешено только из `anySimpleType`.</span><span class="sxs-lookup"><span data-stu-id="522e1-188">Restriction is allowed only from `anySimpleType`.</span></span>|
|`complexContent`|<span data-ttu-id="522e1-189">Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="522e1-189">Supported.</span></span> <span data-ttu-id="522e1-190">См. «Наследование».</span><span class="sxs-lookup"><span data-stu-id="522e1-190">See "Inheritance".</span></span>|
|`group`|<span data-ttu-id="522e1-191">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-191">Forbidden.</span></span>|
|`all`|<span data-ttu-id="522e1-192">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-192">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="522e1-193">Запрещено</span><span class="sxs-lookup"><span data-stu-id="522e1-193">Forbidden</span></span>|
|`sequence`|<span data-ttu-id="522e1-194">Поддерживается, сопоставляется членам данных контракта данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-194">Supported, maps to data members of a data contract.</span></span>|
|`attribute`|<span data-ttu-id="522e1-195">Запрещено, даже если use="prohibited" (существует одно исключение).</span><span class="sxs-lookup"><span data-stu-id="522e1-195">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="522e1-196">Только необязательные атрибуты из стандартного пространства имен сериализации поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="522e1-196">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="522e1-197">Они не сопоставляются членам данных в модели программирования контракта данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-197">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="522e1-198">В настоящее время только один подобный атрибут имеет значение; он рассматривается в разделе ISerializable.</span><span class="sxs-lookup"><span data-stu-id="522e1-198">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="522e1-199">Другие атрибуты игнорируются.</span><span class="sxs-lookup"><span data-stu-id="522e1-199">All others are ignored.</span></span>|
|`attributeGroup`|<span data-ttu-id="522e1-200">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-200">Forbidden.</span></span> <span data-ttu-id="522e1-201">В выпуске WCF v1 не `DataContractSerializer` учитывает присутствие `attributeGroup` внутри `xs:complexType` .</span><span class="sxs-lookup"><span data-stu-id="522e1-201">In the WCF v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|
|`anyAttribute`|<span data-ttu-id="522e1-202">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-202">Forbidden.</span></span>|
|<span data-ttu-id="522e1-203">(пусто)</span><span class="sxs-lookup"><span data-stu-id="522e1-203">(empty)</span></span>|<span data-ttu-id="522e1-204">Сопоставляется с контрактом данных, не имеющем элементов данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-204">Maps to a data contract with no data members.</span></span>|

### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="522e1-205">\<xs:sequence> в сложном типе: атрибуты</span><span class="sxs-lookup"><span data-stu-id="522e1-205">\<xs:sequence> in a complex type: attributes</span></span>

|<span data-ttu-id="522e1-206">attribute</span><span class="sxs-lookup"><span data-stu-id="522e1-206">Attribute</span></span>|<span data-ttu-id="522e1-207">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-207">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="522e1-208">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-208">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="522e1-209">По умолчанию должен иметь значение 1.</span><span class="sxs-lookup"><span data-stu-id="522e1-209">Must be 1 (default).</span></span>|
|`minOccurs`|<span data-ttu-id="522e1-210">По умолчанию должен иметь значение 1.</span><span class="sxs-lookup"><span data-stu-id="522e1-210">Must be 1 (default).</span></span>|

### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="522e1-211">\<xs:sequence> в сложном типе: содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-211">\<xs:sequence> in a complex type: contents</span></span>

|<span data-ttu-id="522e1-212">Содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-212">Contents</span></span>|<span data-ttu-id="522e1-213">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-213">Schema</span></span>|
|--------------|------------|
|`element`|<span data-ttu-id="522e1-214">Каждый экземпляр сопоставляется с элементом данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-214">Each instance maps to a data member.</span></span>|
|`group`|<span data-ttu-id="522e1-215">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-215">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="522e1-216">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-216">Forbidden.</span></span>|
|`sequence`|<span data-ttu-id="522e1-217">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-217">Forbidden.</span></span>|
|`any`|<span data-ttu-id="522e1-218">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-218">Forbidden.</span></span>|
|<span data-ttu-id="522e1-219">(пусто)</span><span class="sxs-lookup"><span data-stu-id="522e1-219">(empty)</span></span>|<span data-ttu-id="522e1-220">Сопоставляется с контрактом данных, не имеющем элементов данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-220">Maps to a data contract with no data members.</span></span>|

## <a name="elements--xselement"></a><span data-ttu-id="522e1-221">Элементы – \<xs:element></span><span class="sxs-lookup"><span data-stu-id="522e1-221">Elements – \<xs:element></span></span>

### <a name="general-information"></a><span data-ttu-id="522e1-222">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="522e1-222">General Information</span></span>

<span data-ttu-id="522e1-223">`<xs:element>` может использоваться в следующих случаях.</span><span class="sxs-lookup"><span data-stu-id="522e1-223">`<xs:element>` can occur in the following contexts:</span></span>

- <span data-ttu-id="522e1-224">Он может использоваться в `<xs:sequence>`, описывающей член данных обычного контракта данных (не коллекции).</span><span class="sxs-lookup"><span data-stu-id="522e1-224">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="522e1-225">В этом случае атрибут `maxOccurs` должен быть равен 1.</span><span class="sxs-lookup"><span data-stu-id="522e1-225">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="522e1-226">(Значение 0 недопустимо).</span><span class="sxs-lookup"><span data-stu-id="522e1-226">(A value of 0 is not allowed).</span></span>

- <span data-ttu-id="522e1-227">Он может использоваться в `<xs:sequence>`, описывающей член данных контракта данных коллекции.</span><span class="sxs-lookup"><span data-stu-id="522e1-227">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="522e1-228">В этом случае атрибут `maxOccurs` должен иметь значение больше 1 или unbounded.</span><span class="sxs-lookup"><span data-stu-id="522e1-228">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>

- <span data-ttu-id="522e1-229">Он может использоваться в `<xs:schema>` в качестве объявления глобального элемента.</span><span class="sxs-lookup"><span data-stu-id="522e1-229">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="522e1-230">\<xs:element> с maxOccurs = 1 в \<xs:sequence> (элементы данных)</span><span class="sxs-lookup"><span data-stu-id="522e1-230">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>

|<span data-ttu-id="522e1-231">attribute</span><span class="sxs-lookup"><span data-stu-id="522e1-231">Attribute</span></span>|<span data-ttu-id="522e1-232">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-232">Schema</span></span>|
|---------------|------------|
|`ref`|<span data-ttu-id="522e1-233">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-233">Forbidden.</span></span>|
|`name`|<span data-ttu-id="522e1-234">Поддерживается, сопоставляется с именем элемента данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-234">Supported, maps to the data member name.</span></span>|
|`type`|<span data-ttu-id="522e1-235">Поддерживается, сопоставляется типу члена данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-235">Supported, maps to the data member type.</span></span> <span data-ttu-id="522e1-236">Дополнительные сведения см. в разделе «Сопоставление тип-примитив».</span><span class="sxs-lookup"><span data-stu-id="522e1-236">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="522e1-237">Если не задан (и элемент не содержит анонимный тип), предполагается `xs:anyType` .</span><span class="sxs-lookup"><span data-stu-id="522e1-237">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|
|`block`|<span data-ttu-id="522e1-238">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-238">Ignored.</span></span>|
|`default`|<span data-ttu-id="522e1-239">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-239">Forbidden.</span></span>|
|`fixed`|<span data-ttu-id="522e1-240">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-240">Forbidden.</span></span>|
|`form`|<span data-ttu-id="522e1-241">Должен иметь полное имя.</span><span class="sxs-lookup"><span data-stu-id="522e1-241">Must be qualified.</span></span> <span data-ttu-id="522e1-242">Этот атрибут может быть задан через `elementFormDefault` в `xs:schema`.</span><span class="sxs-lookup"><span data-stu-id="522e1-242">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|
|`id`|<span data-ttu-id="522e1-243">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-243">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="522e1-244">1</span><span class="sxs-lookup"><span data-stu-id="522e1-244">1</span></span>|
|`minOccurs`|<span data-ttu-id="522e1-245">Сопоставляется со свойством <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> элемента данных (`IsRequired` имеет значение true, когда `minOccurs` имеет значение 1).</span><span class="sxs-lookup"><span data-stu-id="522e1-245">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|
|`nillable`|<span data-ttu-id="522e1-246">Влияет на сопоставление типов.</span><span class="sxs-lookup"><span data-stu-id="522e1-246">Affects type mapping.</span></span> <span data-ttu-id="522e1-247">См. "Сопоставление тип-примитив".</span><span class="sxs-lookup"><span data-stu-id="522e1-247">See Type/primitive mapping.</span></span>|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="522e1-248">\<xs:element> с maxOccurs>1 в \<xs:sequence> коллекции (коллекций)</span><span class="sxs-lookup"><span data-stu-id="522e1-248">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>

- <span data-ttu-id="522e1-249">Сопоставляется <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="522e1-249">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>

- <span data-ttu-id="522e1-250">В типах коллекции только один xs:element допустим в xs:sequence.</span><span class="sxs-lookup"><span data-stu-id="522e1-250">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>

 <span data-ttu-id="522e1-251">Коллекции могут быть следующих типов:</span><span class="sxs-lookup"><span data-stu-id="522e1-251">Collections can be of the following types:</span></span>

- <span data-ttu-id="522e1-252">Обычные коллекции (например, массивы).</span><span class="sxs-lookup"><span data-stu-id="522e1-252">Regular collections (for example, arrays).</span></span>

- <span data-ttu-id="522e1-253">Коллекции-словари (сопоставляющие одно значение другому; например, <xref:System.Collections.Hashtable>).</span><span class="sxs-lookup"><span data-stu-id="522e1-253">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>

- <span data-ttu-id="522e1-254">Единственное отличие между словарем и массивом типа пара ключ/значение заключается в создаваемой модели программирования.</span><span class="sxs-lookup"><span data-stu-id="522e1-254">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="522e1-255">Существует механизм заметки схемы, который можно использовать чтобы указать, что данный тип является коллекцией-словарем.</span><span class="sxs-lookup"><span data-stu-id="522e1-255">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>

<span data-ttu-id="522e1-256">Правила для атрибутов `ref`, `block`, `default`, `fixed`, `form`и `id` те же, что и в случае типов, не являющихся коллекциями.</span><span class="sxs-lookup"><span data-stu-id="522e1-256">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="522e1-257">Другие атрибуты приведены в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="522e1-257">Other attributes include those in the following table.</span></span>

|<span data-ttu-id="522e1-258">attribute</span><span class="sxs-lookup"><span data-stu-id="522e1-258">Attribute</span></span>|<span data-ttu-id="522e1-259">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-259">Schema</span></span>|
|---------------|------------|
|`name`|<span data-ttu-id="522e1-260">Поддерживается, сопоставляется свойству <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> в атрибуте `CollectionDataContractAttribute` .</span><span class="sxs-lookup"><span data-stu-id="522e1-260">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|
|`type`|<span data-ttu-id="522e1-261">Поддерживается, сопоставляется типу, хранящемуся в коллекции.</span><span class="sxs-lookup"><span data-stu-id="522e1-261">Supported, maps to the type stored in the collection.</span></span>|
|`maxOccurs`|<span data-ttu-id="522e1-262">Больше, чем 1 или unbounded.</span><span class="sxs-lookup"><span data-stu-id="522e1-262">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="522e1-263">Для схемы контроллера домена следует использовать unbounded.</span><span class="sxs-lookup"><span data-stu-id="522e1-263">The DC schema should use "unbounded".</span></span>|
|`minOccurs`|<span data-ttu-id="522e1-264">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-264">Ignored.</span></span>|
|`nillable`|<span data-ttu-id="522e1-265">Влияет на сопоставление типов.</span><span class="sxs-lookup"><span data-stu-id="522e1-265">Affects type mapping.</span></span> <span data-ttu-id="522e1-266">Этот атрибут игнорируется в случае коллекций-словарей.</span><span class="sxs-lookup"><span data-stu-id="522e1-266">This attribute is ignored for dictionary collections.</span></span>|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="522e1-267">\<xs:element> в \<xs:schema> объявлении глобального элемента</span><span class="sxs-lookup"><span data-stu-id="522e1-267">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>

- <span data-ttu-id="522e1-268">Объявление глобального элемента, имеющего то же имя и пространство имен, что и тип в схеме, или определяющего анонимный тип внутри себя, означает связь с типом.</span><span class="sxs-lookup"><span data-stu-id="522e1-268">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>

- <span data-ttu-id="522e1-269">Экспорт схемы: связанные объявления глобальных элементов создаются для каждого создаваемого типа, как простого, так и сложного.</span><span class="sxs-lookup"><span data-stu-id="522e1-269">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>

- <span data-ttu-id="522e1-270">Десериализация/сериализация: связанные объявления глобальных элементов используются в качестве корневых элементов данного типа.</span><span class="sxs-lookup"><span data-stu-id="522e1-270">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>

- <span data-ttu-id="522e1-271">Импорт схемы: связанные объявления глобальных элементов не требуются и игнорируются, если они соответствуют следующим правилам (если только они не определяют типы).</span><span class="sxs-lookup"><span data-stu-id="522e1-271">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>

|<span data-ttu-id="522e1-272">attribute</span><span class="sxs-lookup"><span data-stu-id="522e1-272">Attribute</span></span>|<span data-ttu-id="522e1-273">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-273">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="522e1-274">Должен иметь значение false для связанных объявлений глобальных элементов.</span><span class="sxs-lookup"><span data-stu-id="522e1-274">Must be false for associated GEDs.</span></span>|
|`block`|<span data-ttu-id="522e1-275">Запрещено в связанных объявлениях глобальных элементов.</span><span class="sxs-lookup"><span data-stu-id="522e1-275">Forbidden in associated GEDs.</span></span>|
|`default`|<span data-ttu-id="522e1-276">Запрещено в связанных объявлениях глобальных элементов.</span><span class="sxs-lookup"><span data-stu-id="522e1-276">Forbidden in associated GEDs.</span></span>|
|`final`|<span data-ttu-id="522e1-277">Должен иметь значение false для связанных объявлений глобальных элементов.</span><span class="sxs-lookup"><span data-stu-id="522e1-277">Must be false for associated GEDs.</span></span>|
|`fixed`|<span data-ttu-id="522e1-278">Запрещено в связанных объявлениях глобальных элементов.</span><span class="sxs-lookup"><span data-stu-id="522e1-278">Forbidden in associated GEDs.</span></span>|
|`id`|<span data-ttu-id="522e1-279">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-279">Ignored.</span></span>|
|`name`|<span data-ttu-id="522e1-280">Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="522e1-280">Supported.</span></span> <span data-ttu-id="522e1-281">См. определение связанных объявлений глобальных элементов.</span><span class="sxs-lookup"><span data-stu-id="522e1-281">See the definition of associated GEDs.</span></span>|
|`nillable`|<span data-ttu-id="522e1-282">Должен иметь значение true для связанных объявлений глобальных элементов.</span><span class="sxs-lookup"><span data-stu-id="522e1-282">Must be true for associated GEDs.</span></span>|
|`substitutionGroup`|<span data-ttu-id="522e1-283">Запрещено в связанных объявлениях глобальных элементов.</span><span class="sxs-lookup"><span data-stu-id="522e1-283">Forbidden in associated GEDs.</span></span>|
|`type`|<span data-ttu-id="522e1-284">Поддерживается и должен соответствовать связанному типу связанных объявлений глобальных элементов (если только элемент не содержит анонимный тип).</span><span class="sxs-lookup"><span data-stu-id="522e1-284">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|

### <a name="xselement-contents"></a><span data-ttu-id="522e1-285">\<xs:element>: содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-285">\<xs:element>: contents</span></span>

|<span data-ttu-id="522e1-286">Содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-286">Contents</span></span>|<span data-ttu-id="522e1-287">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-287">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="522e1-288">Поддерживается.\*</span><span class="sxs-lookup"><span data-stu-id="522e1-288">Supported.\*</span></span>|
|`complexType`|<span data-ttu-id="522e1-289">Поддерживается.\*</span><span class="sxs-lookup"><span data-stu-id="522e1-289">Supported.\*</span></span>|
|`unique`|<span data-ttu-id="522e1-290">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-290">Ignored.</span></span>|
|`key`|<span data-ttu-id="522e1-291">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-291">Ignored.</span></span>|
|`keyref`|<span data-ttu-id="522e1-292">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-292">Ignored.</span></span>|
|<span data-ttu-id="522e1-293">(пусто)</span><span class="sxs-lookup"><span data-stu-id="522e1-293">(blank)</span></span>|<span data-ttu-id="522e1-294">Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="522e1-294">Supported.</span></span>|

<span data-ttu-id="522e1-295">\* При использовании `simpleType` сопоставления и `complexType,` для анонимных типов такая же, как и для неанонимных типов, за исключением того, что нет анонимных контрактов данных, поэтому создается именованный контракт данных с созданным именем, производным от имени элемента.</span><span class="sxs-lookup"><span data-stu-id="522e1-295">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="522e1-296">Ниже перечислены правила для анонимных типов.</span><span class="sxs-lookup"><span data-stu-id="522e1-296">The rules for anonymous types are in the following list:</span></span>

- <span data-ttu-id="522e1-297">Сведения о реализации WCF: Если `xs:element` имя не содержит точек, то анонимный тип сопоставляется внутреннему типу внешнего типа контракта данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-297">WCF implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="522e1-298">Если имя содержит точки, итоговый тип контракта данных является независимым (не внутренним типом).</span><span class="sxs-lookup"><span data-stu-id="522e1-298">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>

- <span data-ttu-id="522e1-299">Создаваемое имя контракта данных внутреннего типа - это имя контракта данных внешнего типа, за которым следует точка, имя элемента и строка Type.</span><span class="sxs-lookup"><span data-stu-id="522e1-299">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>

- <span data-ttu-id="522e1-300">Если контракт данных с таким именем уже существует, уникальное имя создается путем добавления "1", "2", "3" и т. д., пока не будет создано уникальное имя.</span><span class="sxs-lookup"><span data-stu-id="522e1-300">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>

## <a name="simple-types---xssimpletype"></a><span data-ttu-id="522e1-301">Простые типы - \<xs:simpleType></span><span class="sxs-lookup"><span data-stu-id="522e1-301">Simple Types - \<xs:simpleType></span></span>

### <a name="xssimpletype-attributes"></a><span data-ttu-id="522e1-302">\<xs:simpleType>: атрибуты</span><span class="sxs-lookup"><span data-stu-id="522e1-302">\<xs:simpleType>: attributes</span></span>

|<span data-ttu-id="522e1-303">attribute</span><span class="sxs-lookup"><span data-stu-id="522e1-303">Attribute</span></span>|<span data-ttu-id="522e1-304">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-304">Schema</span></span>|
|---------------|------------|
|`final`|<span data-ttu-id="522e1-305">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-305">Ignored.</span></span>|
|`id`|<span data-ttu-id="522e1-306">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-306">Ignored.</span></span>|
|`name`|<span data-ttu-id="522e1-307">Поддерживается, сопоставляется имени контракта данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-307">Supported, maps to the data contract name.</span></span>|

### <a name="xssimpletype-contents"></a><span data-ttu-id="522e1-308">\<xs:simpleType>: содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-308">\<xs:simpleType>: contents</span></span>

|<span data-ttu-id="522e1-309">Содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-309">Contents</span></span>|<span data-ttu-id="522e1-310">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-310">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="522e1-311">Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="522e1-311">Supported.</span></span> <span data-ttu-id="522e1-312">Сопоставляется контрактам данных перечислений.</span><span class="sxs-lookup"><span data-stu-id="522e1-312">Maps to enumeration data contracts.</span></span> <span data-ttu-id="522e1-313">Если этот атрибут не соответствует шаблону перечисления, он игнорируется.</span><span class="sxs-lookup"><span data-stu-id="522e1-313">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="522e1-314">См. раздел «Ограничения `xs:simpleType` ».</span><span class="sxs-lookup"><span data-stu-id="522e1-314">See the `xs:simpleType` restrictions section.</span></span>|
|`list`|<span data-ttu-id="522e1-315">Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="522e1-315">Supported.</span></span> <span data-ttu-id="522e1-316">Сопоставляется контрактам данных перечислений флагов.</span><span class="sxs-lookup"><span data-stu-id="522e1-316">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="522e1-317">См. раздел "Списки `xs:simpleType` ".</span><span class="sxs-lookup"><span data-stu-id="522e1-317">See the `xs:simpleType` lists section.</span></span>|
|`union`|<span data-ttu-id="522e1-318">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-318">Forbidden.</span></span>|

### \<xs:restriction>

- <span data-ttu-id="522e1-319">Ограничения сложных типов поддерживаются только для base="`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="522e1-319">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>

- <span data-ttu-id="522e1-320">Ограничения простых типов `xs:string` , не имеющие никаких других аспектов ограничения, кроме `xs:enumeration` , сопоставляются контрактам данных перечисления.</span><span class="sxs-lookup"><span data-stu-id="522e1-320">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>

- <span data-ttu-id="522e1-321">Все другие ограничения простых типов сопоставляются типам, которые они ограничивают.</span><span class="sxs-lookup"><span data-stu-id="522e1-321">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="522e1-322">Например, ограничение `xs:int` сопоставляется с целым числом так же, как и `xs:int` .</span><span class="sxs-lookup"><span data-stu-id="522e1-322">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> <span data-ttu-id="522e1-323">Дополнительные сведения о сопоставлении типов-примитивов см. в разделе Сопоставление типов и примитивов.</span><span class="sxs-lookup"><span data-stu-id="522e1-323">For more information about primitive type mapping, see Type/primitive mapping.</span></span>

### <a name="xsrestriction-attributes"></a><span data-ttu-id="522e1-324">\<xs:restriction>: атрибуты</span><span class="sxs-lookup"><span data-stu-id="522e1-324">\<xs:restriction>: attributes</span></span>

|<span data-ttu-id="522e1-325">attribute</span><span class="sxs-lookup"><span data-stu-id="522e1-325">Attribute</span></span>|<span data-ttu-id="522e1-326">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-326">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="522e1-327">Должен быть поддерживаемым простым типом или `xs:anyType`.</span><span class="sxs-lookup"><span data-stu-id="522e1-327">Must be a supported simple type or `xs:anyType`.</span></span>|
|`id`|<span data-ttu-id="522e1-328">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-328">Ignored.</span></span>|

### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="522e1-329">\<xs:restriction> для всех остальных случаев: содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-329">\<xs:restriction> for all other cases: contents</span></span>

|<span data-ttu-id="522e1-330">Содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-330">Contents</span></span>|<span data-ttu-id="522e1-331">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-331">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="522e1-332">Если существует, должен быть образован от поддерживаемого примитивного типа.</span><span class="sxs-lookup"><span data-stu-id="522e1-332">If present, must be derived from a supported primitive type.</span></span>|
|`minExclusive`|<span data-ttu-id="522e1-333">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-333">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="522e1-334">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-334">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="522e1-335">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-335">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="522e1-336">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-336">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="522e1-337">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-337">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="522e1-338">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-338">Ignored.</span></span>|
|`length`|<span data-ttu-id="522e1-339">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-339">Ignored.</span></span>|
|`minLength`|<span data-ttu-id="522e1-340">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-340">Ignored.</span></span>|
|`maxLength`|<span data-ttu-id="522e1-341">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-341">Ignored.</span></span>|
|`enumeration`|<span data-ttu-id="522e1-342">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-342">Ignored.</span></span>|
|`whiteSpace`|<span data-ttu-id="522e1-343">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-343">Ignored.</span></span>|
|`pattern`|<span data-ttu-id="522e1-344">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-344">Ignored.</span></span>|
|<span data-ttu-id="522e1-345">(пусто)</span><span class="sxs-lookup"><span data-stu-id="522e1-345">(blank)</span></span>|<span data-ttu-id="522e1-346">Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="522e1-346">Supported.</span></span>|

## <a name="enumeration"></a><span data-ttu-id="522e1-347">Перечисление</span><span class="sxs-lookup"><span data-stu-id="522e1-347">Enumeration</span></span>

### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="522e1-348">\<xs:restriction> для перечислений: атрибуты</span><span class="sxs-lookup"><span data-stu-id="522e1-348">\<xs:restriction> for enumerations: attributes</span></span>

|<span data-ttu-id="522e1-349">attribute</span><span class="sxs-lookup"><span data-stu-id="522e1-349">Attribute</span></span>|<span data-ttu-id="522e1-350">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-350">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="522e1-351">Если существует, должен быть `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="522e1-351">If present, must be `xs:string`.</span></span>|
|`id`|<span data-ttu-id="522e1-352">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-352">Ignored.</span></span>|

### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="522e1-353">\<xs:restriction> для перечислений: содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-353">\<xs:restriction> for enumerations: contents</span></span>

|<span data-ttu-id="522e1-354">Содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-354">Contents</span></span>|<span data-ttu-id="522e1-355">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-355">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="522e1-356">Если существует, должен быть ограничением перечисления, поддерживаемым контрактом данных (этот раздел).</span><span class="sxs-lookup"><span data-stu-id="522e1-356">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|
|`minExclusive`|<span data-ttu-id="522e1-357">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-357">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="522e1-358">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-358">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="522e1-359">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-359">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="522e1-360">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-360">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="522e1-361">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-361">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="522e1-362">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-362">Ignored.</span></span>|
|`length`|<span data-ttu-id="522e1-363">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-363">Forbidden.</span></span>|
|`minLength`|<span data-ttu-id="522e1-364">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-364">Forbidden.</span></span>|
|`maxLength`|<span data-ttu-id="522e1-365">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-365">Forbidden.</span></span>|
|`enumeration`|<span data-ttu-id="522e1-366">Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="522e1-366">Supported.</span></span> <span data-ttu-id="522e1-367">Перечисление id не учитывается, а value сопоставляется с именем значения в контракте данных перечисления.</span><span class="sxs-lookup"><span data-stu-id="522e1-367">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|
|`whiteSpace`|<span data-ttu-id="522e1-368">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-368">Forbidden.</span></span>|
|`pattern`|<span data-ttu-id="522e1-369">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-369">Forbidden.</span></span>|
|<span data-ttu-id="522e1-370">(пусто)</span><span class="sxs-lookup"><span data-stu-id="522e1-370">(empty)</span></span>|<span data-ttu-id="522e1-371">Поддерживается, сопоставляется пустому типу перечисления.</span><span class="sxs-lookup"><span data-stu-id="522e1-371">Supported, maps to empty enumeration type.</span></span>|

 <span data-ttu-id="522e1-372">В следующем коде показан класс перечисления C#.</span><span class="sxs-lookup"><span data-stu-id="522e1-372">The following code shows a C# enumeration class.</span></span>

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

<span data-ttu-id="522e1-373">`DataContractSerializer`сопоставляет этот класс следующей схеме.</span><span class="sxs-lookup"><span data-stu-id="522e1-373">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="522e1-374">Если значения перечисления начинаются с 1, блоки `xs:annotation` не создаются.</span><span class="sxs-lookup"><span data-stu-id="522e1-374">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>

```xml
<xs:simpleType name="MyEnum">
  <xs:restriction base="xs:string">
    <xs:enumeration value="first">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          3
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
    <xs:enumeration value="second">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          4
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
  </xs:restriction>
</xs:simpleType>
```

### \<xs:list>

<span data-ttu-id="522e1-375">`DataContractSerializer` сопоставляет типы перечисления, отмеченные `System.FlagsAttribute` , `xs:list` , образованному из `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="522e1-375">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="522e1-376">Никакие другие виды `xs:list` не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="522e1-376">No other `xs:list` variations are supported.</span></span>

### <a name="xslist-attributes"></a><span data-ttu-id="522e1-377">\<xs:list>: атрибуты</span><span class="sxs-lookup"><span data-stu-id="522e1-377">\<xs:list>: attributes</span></span>

|<span data-ttu-id="522e1-378">attribute</span><span class="sxs-lookup"><span data-stu-id="522e1-378">Attribute</span></span>|<span data-ttu-id="522e1-379">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-379">Schema</span></span>|
|---------------|------------|
|`itemType`|<span data-ttu-id="522e1-380">Запрещено.</span><span class="sxs-lookup"><span data-stu-id="522e1-380">Forbidden.</span></span>|
|`id`|<span data-ttu-id="522e1-381">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-381">Ignored.</span></span>|

### <a name="xslist-contents"></a><span data-ttu-id="522e1-382">\<xs:list>: содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-382">\<xs:list>: contents</span></span>

|<span data-ttu-id="522e1-383">Содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-383">Contents</span></span>|<span data-ttu-id="522e1-384">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-384">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="522e1-385">Должен быть ограничением из `xs:string` , использующей аспект `xs:enumeration` .</span><span class="sxs-lookup"><span data-stu-id="522e1-385">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|

<span data-ttu-id="522e1-386">Если значение перечисления не является членом последовательности степеней 2 (по умолчанию для флагов), значение помещается в элемент `xs:annotation/xs:appInfo/ser:EnumerationValue` .</span><span class="sxs-lookup"><span data-stu-id="522e1-386">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>

<span data-ttu-id="522e1-387">В следующем коде показана установка флагов для типа перечисления.</span><span class="sxs-lookup"><span data-stu-id="522e1-387">For example, the following code flags an enumeration type.</span></span>

```csharp
[Flags]
public enum AuthFlags
{
  AuthAnonymous = 1,
  AuthBasic = 2,
  AuthNTLM = 4,
  AuthMD5 = 16,
  AuthWindowsLiveID = 64,
}
```

<span data-ttu-id="522e1-388">Этот тип сопоставляется следующей схеме.</span><span class="sxs-lookup"><span data-stu-id="522e1-388">This type maps to the following schema.</span></span>

```xml
<xs:simpleType name="AuthFlags">
    <xs:list>
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="AuthAnonymous" />
          <xs:enumeration value="AuthBasic" />
          <xs:enumeration value="AuthNTLM" />
          <xs:enumeration value="AuthMD5">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
          <xs:enumeration value="AuthWindowsLiveID">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">64</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
        </xs:restriction>
      </xs:simpleType>
    </xs:list>
  </xs:simpleType>
```

## <a name="inheritance"></a><span data-ttu-id="522e1-389">Наследование</span><span class="sxs-lookup"><span data-stu-id="522e1-389">Inheritance</span></span>

### <a name="general-rules"></a><span data-ttu-id="522e1-390">Основные правила</span><span class="sxs-lookup"><span data-stu-id="522e1-390">General rules</span></span>

<span data-ttu-id="522e1-391">Контракт данных может наследовать от другого контракта данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-391">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="522e1-392">Такие контракты данных сопоставляются базовым и образуются типами расширения с помощью конструктора схемы XML `<xs:extension>` .</span><span class="sxs-lookup"><span data-stu-id="522e1-392">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>

<span data-ttu-id="522e1-393">Контракт данных не может наследовать от контракта данных коллекции.</span><span class="sxs-lookup"><span data-stu-id="522e1-393">A data contract cannot inherit from a collection data contract.</span></span>

<span data-ttu-id="522e1-394">В следующем коде показан пример контракта данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-394">For example, the following code is a data contract.</span></span>

```csharp
[DataContract]
public class Person
{
  [DataMember]
  public string Name;
}
[DataContract]
public class Employee : Person
{
  [DataMember]
  public int ID;
}
```

<span data-ttu-id="522e1-395">Этот контракт данных сопоставляется следующему объявлению типа схемы XML.</span><span class="sxs-lookup"><span data-stu-id="522e1-395">This data contract maps to the following XML Schema type declaration.</span></span>

```xml
<xs:complexType name="Employee">
 <xs:complexContent mixed="false">
  <xs:extension base="tns:Person">
   <xs:sequence>
    <xs:element minOccurs="0" name="ID" type="xs:int"/>
   </xs:sequence>
  </xs:extension>
 </xs:complexContent>
</xs:complexType>
<xs:complexType name="Person">
 <xs:sequence>
  <xs:element minOccurs="0" name="Name"
    nillable="true" type="xs:string"/>
 </xs:sequence>
</xs:complexType>
```

### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="522e1-396">\<xs:complexContent>: атрибуты</span><span class="sxs-lookup"><span data-stu-id="522e1-396">\<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="522e1-397">attribute</span><span class="sxs-lookup"><span data-stu-id="522e1-397">Attribute</span></span>|<span data-ttu-id="522e1-398">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-398">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="522e1-399">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-399">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="522e1-400">Должен иметь значение false.</span><span class="sxs-lookup"><span data-stu-id="522e1-400">Must be false.</span></span>|

### <a name="xscomplexcontent-contents"></a><span data-ttu-id="522e1-401">\<xs:complexContent>: содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-401">\<xs:complexContent>: contents</span></span>

|<span data-ttu-id="522e1-402">Содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-402">Contents</span></span>|<span data-ttu-id="522e1-403">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-403">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="522e1-404">Запрещено, за исключением случая, когда base="`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="522e1-404">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="522e1-405">Последнее эквивалентно помещению содержимого `xs:restriction` прямо под контейнер `xs:complexContent`.</span><span class="sxs-lookup"><span data-stu-id="522e1-405">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|
|`extension`|<span data-ttu-id="522e1-406">Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="522e1-406">Supported.</span></span> <span data-ttu-id="522e1-407">Сопоставляется наследованию контракта данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-407">Maps to data contract inheritance.</span></span>|

### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="522e1-408">\<xs:extension> в \<xs:complexContent> : атрибуты</span><span class="sxs-lookup"><span data-stu-id="522e1-408">\<xs:extension> in \<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="522e1-409">attribute</span><span class="sxs-lookup"><span data-stu-id="522e1-409">Attribute</span></span>|<span data-ttu-id="522e1-410">схема</span><span class="sxs-lookup"><span data-stu-id="522e1-410">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="522e1-411">Не обрабатывается.</span><span class="sxs-lookup"><span data-stu-id="522e1-411">Ignored.</span></span>|
|`base`|<span data-ttu-id="522e1-412">Поддерживается.</span><span class="sxs-lookup"><span data-stu-id="522e1-412">Supported.</span></span> <span data-ttu-id="522e1-413">Сопоставляется базовому типу контракта данных, от которого наследует этот тип.</span><span class="sxs-lookup"><span data-stu-id="522e1-413">Maps to the base data contract type that this type inherits from.</span></span>|

### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="522e1-414">\<xs:extension> в \<xs:complexContent> : содержимое</span><span class="sxs-lookup"><span data-stu-id="522e1-414">\<xs:extension> in \<xs:complexContent>: contents</span></span>

<span data-ttu-id="522e1-415">Применяются те же правила, что и для содержимого `<xs:complexType>` .</span><span class="sxs-lookup"><span data-stu-id="522e1-415">The rules are the same as for `<xs:complexType>` contents.</span></span>

<span data-ttu-id="522e1-416">Если дается `<xs:sequence>` , ее элементы сопоставляются дополнительным членам данных, присутствующим в производном контракте данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-416">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>

<span data-ttu-id="522e1-417">Если производный тип содержит элемент с тем же именем, что и элемент базового типа, дублирующееся объявление элемента сопоставляется члену данных с создаваемым уникальным именем.</span><span class="sxs-lookup"><span data-stu-id="522e1-417">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="522e1-418">Положительные целые числа добавляются к имени члена данных («member1», «member2» и т. д.) до тех пор, пока не будет найдено уникальное имя.</span><span class="sxs-lookup"><span data-stu-id="522e1-418">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="522e1-419">И наоборот:</span><span class="sxs-lookup"><span data-stu-id="522e1-419">Conversely:</span></span>

- <span data-ttu-id="522e1-420">Если производный контракт данных имеет член данных с тем же именем и типом, что и член данных в базовом контракте данных, `DataContractSerializer` создает соответствующий элемент в производном типе.</span><span class="sxs-lookup"><span data-stu-id="522e1-420">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>

- <span data-ttu-id="522e1-421">Если производный контракт данных имеет член данных с тем же именем, что и член данных в базовом контракте данных, но другой тип, `DataContractSerializer` импортирует схему с элементом типа `xs:anyType` как в базовый тип, так и в объявления производного типа.</span><span class="sxs-lookup"><span data-stu-id="522e1-421">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="522e1-422">Исходное имя типа сохраняется в `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span><span class="sxs-lookup"><span data-stu-id="522e1-422">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>

<span data-ttu-id="522e1-423">В обоих случаях может возникнуть схема с неоднозначной моделью содержимого, которая зависит от порядка соответствующих членов данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-423">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>

## <a name="typeprimitive-mapping"></a><span data-ttu-id="522e1-424">Сопоставление тип-примитив</span><span class="sxs-lookup"><span data-stu-id="522e1-424">Type/primitive mapping</span></span>

<span data-ttu-id="522e1-425">`DataContractSerializer` использует следующие сопоставления для примитивных типов схемы XML.</span><span class="sxs-lookup"><span data-stu-id="522e1-425">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>

|<span data-ttu-id="522e1-426">Тип XSD</span><span class="sxs-lookup"><span data-stu-id="522e1-426">XSD type</span></span>|<span data-ttu-id="522e1-427">Тип .NET</span><span class="sxs-lookup"><span data-stu-id="522e1-427">.NET type</span></span>|
|--------------|---------------|
|`anyType`|<span data-ttu-id="522e1-428"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="522e1-428"><xref:System.Object>.</span></span>|
|`anySimpleType`|<span data-ttu-id="522e1-429"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-429"><xref:System.String>.</span></span>|
|`duration`|<span data-ttu-id="522e1-430"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="522e1-430"><xref:System.TimeSpan>.</span></span>|
|`dateTime`|<span data-ttu-id="522e1-431"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="522e1-431"><xref:System.DateTime>.</span></span>|
|`dateTimeOffset`|<span data-ttu-id="522e1-432"><xref:System.DateTime> и <xref:System.TimeSpan> для смещения.</span><span class="sxs-lookup"><span data-stu-id="522e1-432"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="522e1-433">См. «Сериализация DateTimeOffset» ниже.</span><span class="sxs-lookup"><span data-stu-id="522e1-433">See DateTimeOffset Serialization below.</span></span>|
|`time`|<span data-ttu-id="522e1-434"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-434"><xref:System.String>.</span></span>|
|`date`|<span data-ttu-id="522e1-435"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-435"><xref:System.String>.</span></span>|
|`gYearMonth`|<span data-ttu-id="522e1-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-436"><xref:System.String>.</span></span>|
|`gYear`|<span data-ttu-id="522e1-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-437"><xref:System.String>.</span></span>|
|`gMonthDay`|<span data-ttu-id="522e1-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-438"><xref:System.String>.</span></span>|
|`gDay`|<span data-ttu-id="522e1-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-439"><xref:System.String>.</span></span>|
|`gMonth`|<span data-ttu-id="522e1-440"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-440"><xref:System.String>.</span></span>|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|<span data-ttu-id="522e1-441">Массив <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="522e1-441"><xref:System.Byte> array.</span></span>|
|`hexBinary`|<span data-ttu-id="522e1-442"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-442"><xref:System.String>.</span></span>|
|`float`|<span data-ttu-id="522e1-443"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="522e1-443"><xref:System.Single>.</span></span>|
|`double`|<span data-ttu-id="522e1-444"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="522e1-444"><xref:System.Double>.</span></span>|
|`anyURI`|<span data-ttu-id="522e1-445"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="522e1-445"><xref:System.Uri>.</span></span>|
|`QName`|<span data-ttu-id="522e1-446"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="522e1-446"><xref:System.Xml.XmlQualifiedName>.</span></span>|
|`string`|<span data-ttu-id="522e1-447"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-447"><xref:System.String>.</span></span>|
|`normalizedString`|<span data-ttu-id="522e1-448"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-448"><xref:System.String>.</span></span>|
|`token`|<span data-ttu-id="522e1-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-449"><xref:System.String>.</span></span>|
|`language`|<span data-ttu-id="522e1-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-450"><xref:System.String>.</span></span>|
|`Name`|<span data-ttu-id="522e1-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-451"><xref:System.String>.</span></span>|
|`NCName`|<span data-ttu-id="522e1-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-452"><xref:System.String>.</span></span>|
|`ID`|<span data-ttu-id="522e1-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-453"><xref:System.String>.</span></span>|
|`IDREF`|<span data-ttu-id="522e1-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-454"><xref:System.String>.</span></span>|
|`IDREFS`|<span data-ttu-id="522e1-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-455"><xref:System.String>.</span></span>|
|`ENTITY`|<span data-ttu-id="522e1-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-456"><xref:System.String>.</span></span>|
|`ENTITIES`|<span data-ttu-id="522e1-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-457"><xref:System.String>.</span></span>|
|`NMTOKEN`|<span data-ttu-id="522e1-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-458"><xref:System.String>.</span></span>|
|`NMTOKENS`|<span data-ttu-id="522e1-459"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="522e1-459"><xref:System.String>.</span></span>|
|`decimal`|<span data-ttu-id="522e1-460"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="522e1-460"><xref:System.Decimal>.</span></span>|
|`integer`|<span data-ttu-id="522e1-461"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="522e1-461"><xref:System.Int64>.</span></span>|
|`nonPositiveInteger`|<span data-ttu-id="522e1-462"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="522e1-462"><xref:System.Int64>.</span></span>|
|`negativeInteger`|<span data-ttu-id="522e1-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="522e1-463"><xref:System.Int64>.</span></span>|
|`long`|<span data-ttu-id="522e1-464"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="522e1-464"><xref:System.Int64>.</span></span>|
|`int`|<span data-ttu-id="522e1-465"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="522e1-465"><xref:System.Int32>.</span></span>|
|`short`|<span data-ttu-id="522e1-466"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="522e1-466"><xref:System.Int16>.</span></span>|
|`Byte`|<span data-ttu-id="522e1-467"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="522e1-467"><xref:System.SByte>.</span></span>|
|`nonNegativeInteger`|<span data-ttu-id="522e1-468"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="522e1-468"><xref:System.Int64>.</span></span>|
|`unsignedLong`|<span data-ttu-id="522e1-469"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="522e1-469"><xref:System.UInt64>.</span></span>|
|`unsignedInt`|<span data-ttu-id="522e1-470"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="522e1-470"><xref:System.UInt32>.</span></span>|
|`unsignedShort`|<span data-ttu-id="522e1-471"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="522e1-471"><xref:System.UInt16>.</span></span>|
|`unsignedByte`|<span data-ttu-id="522e1-472"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="522e1-472"><xref:System.Byte>.</span></span>|
|`positiveInteger`|<span data-ttu-id="522e1-473"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="522e1-473"><xref:System.Int64>.</span></span>|

## <a name="iserializable-types-mapping"></a><span data-ttu-id="522e1-474">Сопоставление типов ISerializable</span><span class="sxs-lookup"><span data-stu-id="522e1-474">ISerializable types mapping</span></span>

<span data-ttu-id="522e1-475">В платформа .NET Framework версии 1,0 <xref:System.Runtime.Serialization.ISerializable> было представлено как общий механизм сериализации объектов для сохранения или обмена данными.</span><span class="sxs-lookup"><span data-stu-id="522e1-475">In .NET Framework version 1.0, <xref:System.Runtime.Serialization.ISerializable> was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="522e1-476">Существует множество типов платформа .NET Framework, которые реализуют `ISerializable` и могут передаваться между приложениями.</span><span class="sxs-lookup"><span data-stu-id="522e1-476">There are many .NET Framework types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="522e1-477"><xref:System.Runtime.Serialization.DataContractSerializer> поддерживает классы `ISerializable` .</span><span class="sxs-lookup"><span data-stu-id="522e1-477"><xref:System.Runtime.Serialization.DataContractSerializer> naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="522e1-478">`DataContractSerializer` сопоставляет типы схемы реализации `ISerializable` , отличающиеся только полным именем типа (QName) и фактически являющиеся коллекциями свойств.</span><span class="sxs-lookup"><span data-stu-id="522e1-478">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="522e1-479">Например, объект `DataContractSerializer` сопоставляется со <xref:System.Exception> следующим типом XSD в `http://schemas.datacontract.org/2004/07/System` пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="522e1-479">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the `http://schemas.datacontract.org/2004/07/System` namespace.</span></span>

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

<span data-ttu-id="522e1-480">Необязательный атрибут `ser:FactoryType` , объявленный в схеме сериализации контракта данных ссылается на класс фабрики, который может выполнить десериализацию типа.</span><span class="sxs-lookup"><span data-stu-id="522e1-480">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="522e1-481">Класс фабрики может входить в коллекцию известных типов используемого экземпляра `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="522e1-481">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> <span data-ttu-id="522e1-482">Дополнительные сведения об известных типах см. в разделе [Data Contract известные типы](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="522e1-482">For more information about known types, see [Data Contract Known Types](data-contract-known-types.md).</span></span>

## <a name="datacontract-serialization-schema"></a><span data-ttu-id="522e1-483">DataContract - схема сериализации</span><span class="sxs-lookup"><span data-stu-id="522e1-483">DataContract Serialization Schema</span></span>

<span data-ttu-id="522e1-484">Ряд схем, импортируемых `DataContractSerializer` , использует типы, элементы и атрибуты специального пространства имен сериализации контракта данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-484">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>

`http://schemas.microsoft.com/2003/10/Serialization`

<span data-ttu-id="522e1-485">Ниже приведен пример полного объявления схемы сериализации контракта данных.</span><span class="sxs-lookup"><span data-stu-id="522e1-485">The following is a complete Data Contract Serialization schema declaration.</span></span>

```xml
<xs:schema attributeFormDefault="qualified"
   elementFormDefault="qualified"
   targetNamespace =
    "http://schemas.microsoft.com/2003/10/Serialization/"
   xmlns:xs="http://www.w3.org/2001/XMLSchema"
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">

 <!-- Top-level elements for primitive types. -->
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>
 <xs:element name="base64Binary"
       nillable="true" type="xs:base64Binary"/>
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>
 <xs:element name="byte" nillable="true" type="xs:byte"/>
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>
 <xs:element name="double" nillable="true" type="xs:double"/>
 <xs:element name="float" nillable="true" type="xs:float"/>
 <xs:element name="int" nillable="true" type="xs:int"/>
 <xs:element name="long" nillable="true" type="xs:long"/>
 <xs:element name="QName" nillable="true" type="xs:QName"/>
 <xs:element name="short" nillable="true" type="xs:short"/>
 <xs:element name="string" nillable="true" type="xs:string"/>
 <xs:element name="unsignedByte"
       nillable="true" type="xs:unsignedByte"/>
 <xs:element name="unsignedInt"
       nillable="true" type="xs:unsignedInt"/>
 <xs:element name="unsignedLong"
       nillable="true" type="xs:unsignedLong"/>
 <xs:element name="unsignedShort"
       nillable="true" type="xs:unsignedShort"/>

 <!-- Primitive types introduced for certain .NET simple types. -->
 <xs:element name="char" nillable="true" type="tns:char"/>
 <xs:simpleType name="char">
  <xs:restriction base="xs:int"/>
 </xs:simpleType>

 <!-- xs:duration is restricted to an ordered value space,
    to map to System.TimeSpan -->
 <xs:element name="duration" nillable="true" type="tns:duration"/>
 <xs:simpleType name="duration">
  <xs:restriction base="xs:duration">
   <xs:pattern
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>
  </xs:restriction>
 </xs:simpleType>

 <xs:element name="guid" nillable="true" type="tns:guid"/>
 <xs:simpleType name="guid">
  <xs:restriction base="xs:string">
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>
  </xs:restriction>
 </xs:simpleType>

 <!-- This is used for schemas exported from ISerializable type. -->
 <xs:attribute name="FactoryType" type="xs:QName"/>
</xs:schema>
```

<span data-ttu-id="522e1-486">Необходимо отметить следующее.</span><span class="sxs-lookup"><span data-stu-id="522e1-486">The following should be noted:</span></span>

- <span data-ttu-id="522e1-487">`ser:char` введен для представления символов Юникода типа <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="522e1-487">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>

- <span data-ttu-id="522e1-488">`valuespace``xs:duration` сокращается до упорядоченного набора, чтобы можно было выполнить его сопоставление <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="522e1-488">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>

- <span data-ttu-id="522e1-489">`FactoryType` используется в схемах, экспортируемых из типов, унаследованных от <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="522e1-489">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>

## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="522e1-490">Импорт схем, отличных от DataContract</span><span class="sxs-lookup"><span data-stu-id="522e1-490">Importing non-DataContract schemas</span></span>

<span data-ttu-id="522e1-491">В`DataContractSerializer` имеется функция `ImportXmlTypes` , которая выполняет импорт схем, не соответствующих профилю XSD `DataContractSerializer` (см. свойство <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> ).</span><span class="sxs-lookup"><span data-stu-id="522e1-491">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="522e1-492">Если задать этому параметру значение `true` , типы схемы, не удовлетворяющие требованиям, будут приняты и сопоставлены следующей реализации; <xref:System.Xml.Serialization.IXmlSerializable> упакует массив <xref:System.Xml.XmlNode> (отличается только имя класса).</span><span class="sxs-lookup"><span data-stu-id="522e1-492">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>

```csharp
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]
public partial class Person : object, IXmlSerializable
{
  private XmlNode[] nodesField;
  private static XmlQualifiedName typeName =
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");
  public XmlNode[] Nodes
  {
    get {return this.nodesField;}
    set {this.nodesField = value;}
  }
  public void ReadXml(XmlReader reader)
  {
    this.nodesField = XmlSerializableServices.ReadNodes(reader);
  }
  public void WriteXml(XmlWriter writer)
  {
    XmlSerializableServices.WriteNodes(writer, this.Nodes);
  }
  public System.Xml.Schema.XmlSchema GetSchema()
  {
    return null;
  }
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)
  {
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);
    return typeName;
  }
}
```

## <a name="datetimeoffset-serialization"></a><span data-ttu-id="522e1-493">DateTimeOffset - сериализация</span><span class="sxs-lookup"><span data-stu-id="522e1-493">DateTimeOffset Serialization</span></span>

<span data-ttu-id="522e1-494"><xref:System.DateTimeOffset> не обрабатывается как примитивный тип.</span><span class="sxs-lookup"><span data-stu-id="522e1-494">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="522e1-495">Вместо этого он сериализуется как сложный элемент с двумя частями.</span><span class="sxs-lookup"><span data-stu-id="522e1-495">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="522e1-496">Первая часть представляет дату и время, а вторая - смещение даты и времени.</span><span class="sxs-lookup"><span data-stu-id="522e1-496">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="522e1-497">В следующем примере кода показано значение DateTimeOffset.</span><span class="sxs-lookup"><span data-stu-id="522e1-497">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>

```xml
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">
  <DateTime i:type="b:dateTime" xmlns=""
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00
  </DateTime>
  <OffsetMinutes i:type="b:short" xmlns=""
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480
   </OffsetMinutes>
</OffSet>
```

<span data-ttu-id="522e1-498">Схема выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="522e1-498">The schema is as follows.</span></span>

```xml
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">
   <xs:complexType name="DateTimeOffset">
      <xs:sequence minOccurs="1" maxOccurs="1">
         <xs:element name="DateTime" type="xs:dateTime"
         minOccurs="1" maxOccurs="1" />
         <xs:element name="OffsetMinutes" type="xs:short"
         minOccurs="1" maxOccurs="1" />
      </xs:sequence>
   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a><span data-ttu-id="522e1-499">См. также</span><span class="sxs-lookup"><span data-stu-id="522e1-499">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [<span data-ttu-id="522e1-500">Использование контрактов данных</span><span class="sxs-lookup"><span data-stu-id="522e1-500">Using Data Contracts</span></span>](using-data-contracts.md)
