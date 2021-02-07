---
description: Дополнительные сведения см. в статье схема параметров шифрования.
title: Схема параметров криптографии
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: a7b3c020ed760aba24c9faf020281b7ad4bf3af7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730087"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="1c7b1-103">Схема параметров криптографии</span><span class="sxs-lookup"><span data-stu-id="1c7b1-103">Cryptography Settings Schema</span></span>

<span data-ttu-id="1c7b1-104">Схема параметров шифрования содержит элементы, с помощью которых можно сопоставить понятные имена алгоритмов с классами, реализующими алгоритмы шифрования.</span><span class="sxs-lookup"><span data-stu-id="1c7b1-104">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)

|<span data-ttu-id="1c7b1-105">Элемент</span><span class="sxs-lookup"><span data-stu-id="1c7b1-105">Element</span></span>|<span data-ttu-id="1c7b1-106">Описание</span><span class="sxs-lookup"><span data-stu-id="1c7b1-106">Description</span></span>|  
|-------------|-----------------|  
|[**\<cryptoClasses**>](cryptoclasses-element.md)|<span data-ttu-id="1c7b1-107">Содержит список криптографических классов, сопоставленных с понятным именем в **\<nameEntry>** элементе.</span><span class="sxs-lookup"><span data-stu-id="1c7b1-107">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptoClass**>](cryptoclass-element.md)|<span data-ttu-id="1c7b1-108">Содержит криптографический класс, сопоставленный с понятным именем в **\<nameEntry>** элементе.</span><span class="sxs-lookup"><span data-stu-id="1c7b1-108">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptographySettings**>](cryptographysettings-element.md)|<span data-ttu-id="1c7b1-109">Содержит параметры шифрования.</span><span class="sxs-lookup"><span data-stu-id="1c7b1-109">Contains cryptography settings.</span></span>|  
|[**\<cryptoNameMapping**>](cryptonamemapping-element.md)|<span data-ttu-id="1c7b1-110">Содержит сопоставления классов с понятными именами.</span><span class="sxs-lookup"><span data-stu-id="1c7b1-110">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="1c7b1-111">**\<mscorlib>** элемент для параметров шифрования</span><span class="sxs-lookup"><span data-stu-id="1c7b1-111">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="1c7b1-112">Содержит **\<cryptographySettings>** элемент.</span><span class="sxs-lookup"><span data-stu-id="1c7b1-112">Contains the **\<cryptographySettings>** element.</span></span>|  
|[**\<nameEntry>**](nameentry-element.md)|<span data-ttu-id="1c7b1-113">Сопоставляет имя класса с понятным именем алгоритма, что позволяет одному классу иметь несколько понятных имен.</span><span class="sxs-lookup"><span data-stu-id="1c7b1-113">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[**\<oidEntry>**](oidentry-element.md)|<span data-ttu-id="1c7b1-114">Сопоставляет идентификатор объекта (OID) ASN.1 с понятным именем.</span><span class="sxs-lookup"><span data-stu-id="1c7b1-114">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[**\<oidMap>**](oidmap-element.md)|<span data-ttu-id="1c7b1-115">Содержит сопоставления идентификатора объекта ASN.1 с классами.</span><span class="sxs-lookup"><span data-stu-id="1c7b1-115">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c7b1-116">См. также</span><span class="sxs-lookup"><span data-stu-id="1c7b1-116">See also</span></span>

- [<span data-ttu-id="1c7b1-117">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="1c7b1-117">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1c7b1-118">службы шифрования</span><span class="sxs-lookup"><span data-stu-id="1c7b1-118">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
