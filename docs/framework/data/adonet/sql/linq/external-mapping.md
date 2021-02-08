---
description: 'Дополнительные сведения: внешнее сопоставление'
title: Внешнее сопоставление
ms.date: 03/30/2017
ms.assetid: 076606b8-d889-4ba0-b5da-ae577b146f23
ms.openlocfilehash: 8c09e3bdf1798757bedfac9e568a0384a8e6bb49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786086"
---
# <a name="external-mapping"></a><span data-ttu-id="11f86-103">Внешнее сопоставление</span><span class="sxs-lookup"><span data-stu-id="11f86-103">External Mapping</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="11f86-104">поддерживает *внешнее сопоставление*— процесс, в котором используется отдельный XML-файл для указания сопоставления между моделью данных базы данных и объектной моделью.</span><span class="sxs-lookup"><span data-stu-id="11f86-104">supports *external mapping*, a process by which you use a separate XML file to specify mapping between the data model of the database and your object model.</span></span> <span data-ttu-id="11f86-105">Файл внешнего сопоставления имеет следующие преимущества.</span><span class="sxs-lookup"><span data-stu-id="11f86-105">Advantages of using an external mapping file include the following:</span></span>  
  
- <span data-ttu-id="11f86-106">Код сопоставления можно хранить вне кода приложения.</span><span class="sxs-lookup"><span data-stu-id="11f86-106">You can keep your mapping code out of your application code.</span></span> <span data-ttu-id="11f86-107">Этот подход уменьшает перегруженность кода приложения.</span><span class="sxs-lookup"><span data-stu-id="11f86-107">This approach reduces clutter in your application code.</span></span>  
  
- <span data-ttu-id="11f86-108">Файл внешнего сопоставления можно считать подобным файлу конфигурации.</span><span class="sxs-lookup"><span data-stu-id="11f86-108">You can treat an external mapping file something like a configuration file.</span></span> <span data-ttu-id="11f86-109">Например, можно изменить поведение приложения после предоставления двоичных файлов, просто выгрузив файл внешнего сопоставления.</span><span class="sxs-lookup"><span data-stu-id="11f86-109">For example, you can update how your application behaves after shipping the binaries by just swapping out the external mapping file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11f86-110">Требования</span><span class="sxs-lookup"><span data-stu-id="11f86-110">Requirements</span></span>  

 <span data-ttu-id="11f86-111">Файл сопоставления должен быть XML-файлом, а файл должен быть проверен на соответствие с [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] файлом определения схемы (XSD).</span><span class="sxs-lookup"><span data-stu-id="11f86-111">The mapping file must be an XML file, and the file must validate against a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] schema definition (.xsd) file.</span></span>  
  
 <span data-ttu-id="11f86-112">Применяются следующие правила.</span><span class="sxs-lookup"><span data-stu-id="11f86-112">The following rules apply:</span></span>  
  
- <span data-ttu-id="11f86-113">Файл сопоставления должен быть файлом XML.</span><span class="sxs-lookup"><span data-stu-id="11f86-113">The mapping file must be an XML file.</span></span>  
  
- <span data-ttu-id="11f86-114">Файл сопоставления XML должен быть проверен на соответствие файлу определения схемы XML.</span><span class="sxs-lookup"><span data-stu-id="11f86-114">The XML mapping file must be valid against the XML schema definition file.</span></span> <span data-ttu-id="11f86-115">Дополнительные сведения см. [в разделе инструкции. Проверка DBML и внешних файлов сопоставления](how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="11f86-115">For more information, see [How to: Validate DBML and External Mapping Files](how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
- <span data-ttu-id="11f86-116">Внешнее сопоставление переопределяет сопоставление на основе атрибутов.</span><span class="sxs-lookup"><span data-stu-id="11f86-116">External mapping overrides attribute-based mapping.</span></span> <span data-ttu-id="11f86-117">Другими словами, если для создания <xref:System.Data.Linq.DataContext> используется источник внешнего сопоставления, <xref:System.Data.Linq.DataContext> игнорирует все созданные в классах атрибуты сопоставления.</span><span class="sxs-lookup"><span data-stu-id="11f86-117">In other words, when you use an external mapping source to create a <xref:System.Data.Linq.DataContext>, the <xref:System.Data.Linq.DataContext> ignores all mapping attributes you have created on classes.</span></span> <span data-ttu-id="11f86-118">Данная модель работает, если класс включен в файл внешнего сопоставления.</span><span class="sxs-lookup"><span data-stu-id="11f86-118">This behavior is true whether the class is included in the external mapping file.</span></span>  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="11f86-119">не поддерживает комбинированное использование двух типов сопоставлений (на основе атрибутов и внешнее).</span><span class="sxs-lookup"><span data-stu-id="11f86-119">does not support the hybrid use of the two mapping approaches (attribute-based and external).</span></span>  
  
## <a name="xml-schema-definition-file"></a><span data-ttu-id="11f86-120">Файл определения схемы XML</span><span class="sxs-lookup"><span data-stu-id="11f86-120">XML Schema Definition File</span></span>  

 <span data-ttu-id="11f86-121">Внешнее сопоставление в [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] должно быть проверено на соответствие определению схемы XML.</span><span class="sxs-lookup"><span data-stu-id="11f86-121">External mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be valid against the following XML schema definition.</span></span>  
  
 <span data-ttu-id="11f86-122">Следует отличать этот файл определения схемы от файла определения схемы, который используется для проверки DBML-файла.</span><span class="sxs-lookup"><span data-stu-id="11f86-122">Distinguish this schema definition file from the schema definition file that is used to validate a DBML file.</span></span> <span data-ttu-id="11f86-123">Дополнительные сведения см. [в разделе Создание кода в LINQ to SQL](code-generation-in-linq-to-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="11f86-123">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11f86-124">Пользователи Visual Studio также будут искать этот XSD-файл в диалоговом окне схемы XML в формате "Линктосклмаппинг. xsd".</span><span class="sxs-lookup"><span data-stu-id="11f86-124">Visual Studio users will also find this XSD file in the XML Schemas dialog box as "LinqToSqlMapping.xsd".</span></span> <span data-ttu-id="11f86-125">Чтобы правильно использовать этот файл для проверки внешнего файла сопоставления, см. раздел [как проверить DBML и внешние файлы сопоставления](how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="11f86-125">To use this file correctly for validating an external mapping file, see [How to: Validate DBML and External Mapping Files](how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://schemas.microsoft.com/linqtosql/mapping/2007" xmlns="http://schemas.microsoft.com/linqtosql/mapping/2007"  
elementFormDefault="qualified" >  
  <xs:element name="Database" type="Database" />  
  <xs:complexType name="Database">  
    <xs:sequence>  
      <xs:element name="Table" type="Table" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Function" type="Function" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Provider" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Table">  
    <xs:sequence>  
      <xs:element name="Type" type="Type" minOccurs="1" maxOccurs="1" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Type">  
    <xs:sequence>  
      <xs:choice minOccurs="0" maxOccurs="unbounded">  
        <xs:element name="Column" type="Column" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Association" type="Association" minOccurs="0" maxOccurs="unbounded" />  
      </xs:choice>  
      <xs:element name="Type" type="Type" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="InheritanceCode" type="xs:string" use="optional" />  
    <xs:attribute name="IsInheritanceDefault" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Column">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="IsPrimaryKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsDbGenerated" type="xs:boolean" use="optional" />  
    <xs:attribute name="CanBeNull" type="xs:boolean" use="optional" />  
    <xs:attribute name="UpdateCheck" type="UpdateCheck" use="optional" />  
    <xs:attribute name="IsDiscriminator" type="xs:boolean" use="optional" />  
    <xs:attribute name="Expression" type="xs:string" use="optional" />  
    <xs:attribute name="IsVersion" type="xs:boolean" use="optional" />  
    <xs:attribute name="AutoSync" type="AutoSync" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Association">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="ThisKey" type="xs:string" use="optional" />  
    <xs:attribute name="OtherKey" type="xs:string" use="optional" />  
    <xs:attribute name="IsForeignKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsUnique" type="xs:boolean" use="optional" />  
    <xs:attribute name="DeleteRule" type="xs:string" use="optional" />  
    <xs:attribute name="DeleteOnNull" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Function">  
    <xs:sequence>  
      <xs:element name="Parameter" type="Parameter" minOccurs="0" maxOccurs="unbounded" />  
      <xs:choice>  
        <xs:element name="ElementType" type="Type" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Return" type="Return" minOccurs="0" maxOccurs="1" />  
      </xs:choice>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Method" type="xs:string" use="required" />  
    <xs:attribute name="IsComposable" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Parameter">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Parameter" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="Direction" type="ParameterDirection" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Return">  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:simpleType name="UpdateCheck">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="WhenChanged" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="ParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In" />  
      <xs:enumeration value="Out" />  
      <xs:enumeration value="InOut" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="AutoSync">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="OnInsert" />  
      <xs:enumeration value="OnUpdate" />  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Default" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11f86-126">См. также</span><span class="sxs-lookup"><span data-stu-id="11f86-126">See also</span></span>

- [<span data-ttu-id="11f86-127">Создание кода в LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="11f86-127">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="11f86-128">Ссылки</span><span class="sxs-lookup"><span data-stu-id="11f86-128">Reference</span></span>](reference.md)
- [<span data-ttu-id="11f86-129">Практическое руководство. Как создать модель объектов в виде внешнего файла</span><span class="sxs-lookup"><span data-stu-id="11f86-129">How to: Generate the Object Model as an External File</span></span>](how-to-generate-the-object-model-as-an-external-file.md)
