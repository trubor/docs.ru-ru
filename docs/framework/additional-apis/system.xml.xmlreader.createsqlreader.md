---
description: Дополнительные сведения о методе XmlReader. Креатесклреадер
title: Метод XmlReader. Креатесклреадер (System.Xml)
ms.date: 10/17/2019
topic_type:
- apiref
api_name:
- System.Xml.XmlReader.CreateSqlReader
api_location:
- system.xml.dll
api_type:
- Assembly
ms.openlocfilehash: 61d594c0438c86863ce4052387439f5483d8a34c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740438"
---
# <a name="xmlreadercreatesqlreader-method"></a><span data-ttu-id="4855e-103">Метод XmlReader.CreateSqlReader</span><span class="sxs-lookup"><span data-stu-id="4855e-103">XmlReader.CreateSqlReader Method</span></span>

<span data-ttu-id="4855e-104">Создает новый экземпляр <xref:System.Xml.XmlReader>, используя заданный поток, параметры и контекстную информацию для анализа.</span><span class="sxs-lookup"><span data-stu-id="4855e-104">Creates a new <xref:System.Xml.XmlReader> instance using the specified stream, settings, and context information for parsing.</span></span>

```csharp
internal static XmlReader CreateSqlReader(Stream input,
  XmlReaderSettings settings, XmlParserContext inputContext)
```

## <a name="parameters"></a><span data-ttu-id="4855e-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="4855e-105">Parameters</span></span>

- <span data-ttu-id="4855e-106">`input` <xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="4855e-106">`input` <xref:System.IO.Stream></span></span>  
  <span data-ttu-id="4855e-107">Поток, содержащий XML-данные.</span><span class="sxs-lookup"><span data-stu-id="4855e-107">The stream that contains the XML data.</span></span>

- <span data-ttu-id="4855e-108">`settings` <xref:System.Xml.XmlReaderSettings></span><span class="sxs-lookup"><span data-stu-id="4855e-108">`settings` <xref:System.Xml.XmlReaderSettings></span></span>  
  <span data-ttu-id="4855e-109">Параметры нового экземпляра <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="4855e-109">The settings for the new <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="4855e-110">Это значение может быть равно `null`.</span><span class="sxs-lookup"><span data-stu-id="4855e-110">This value can be `null`.</span></span>

- <span data-ttu-id="4855e-111">`inputContext` <xref:System.Xml.XmlParserContext></span><span class="sxs-lookup"><span data-stu-id="4855e-111">`inputContext` <xref:System.Xml.XmlParserContext></span></span>  
  <span data-ttu-id="4855e-112">Для синтаксического анализа фрагмента XML необходимы контекстные сведения.</span><span class="sxs-lookup"><span data-stu-id="4855e-112">The context information required to parse the XML fragment.</span></span> <span data-ttu-id="4855e-113">Это значение может быть равно `null`.</span><span class="sxs-lookup"><span data-stu-id="4855e-113">This value can be `null`.</span></span>

## <a name="returns"></a><span data-ttu-id="4855e-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4855e-114">Returns</span></span>

<xref:System.Xml.XmlReader>  
<span data-ttu-id="4855e-115">Объект, используемый для чтения данных XML в потоке.</span><span class="sxs-lookup"><span data-stu-id="4855e-115">An object that is used to read the XML data in the stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="4855e-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="4855e-116">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="4855e-117">`XmlReader.CreateSqlReader`Метод является внутренним и не предназначен для непосредственного использования в коде.</span><span class="sxs-lookup"><span data-stu-id="4855e-117">The `XmlReader.CreateSqlReader` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="4855e-118">Корпорация Майкрософт не поддерживает использование этого метода в рабочем приложении при каких-либо обстоятельствах.</span><span class="sxs-lookup"><span data-stu-id="4855e-118">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="4855e-119">Требования</span><span class="sxs-lookup"><span data-stu-id="4855e-119">Requirements</span></span>

<span data-ttu-id="4855e-120">**Пространство имен:** <xref:System.Xml></span><span class="sxs-lookup"><span data-stu-id="4855e-120">**Namespace:** <xref:System.Xml></span></span>

<span data-ttu-id="4855e-121">**Сборка:** System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="4855e-121">**Assembly:** System.Xml.dll</span></span>

<span data-ttu-id="4855e-122">**Платформа .NET Framework версии:** Доступно с 2,0.</span><span class="sxs-lookup"><span data-stu-id="4855e-122">**.NET Framework versions:** Available since 2.0.</span></span>
