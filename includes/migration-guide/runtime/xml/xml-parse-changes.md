---
ms.openlocfilehash: dfa8235fcfd868b80d3a610bddb492899519e289
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009073"
---
### <a name="xml-parsing-changes"></a><span data-ttu-id="3cf07-101">Изменения синтаксического анализа языка XML</span><span class="sxs-lookup"><span data-stu-id="3cf07-101">XML parsing changes</span></span>

| <span data-ttu-id="3cf07-102">Имя</span><span class="sxs-lookup"><span data-stu-id="3cf07-102">Name</span></span>    | <span data-ttu-id="3cf07-103">Значение</span><span class="sxs-lookup"><span data-stu-id="3cf07-103">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="3cf07-104">Область</span><span class="sxs-lookup"><span data-stu-id="3cf07-104">Scope</span></span>   | <span data-ttu-id="3cf07-105">Дополнительный номер</span><span class="sxs-lookup"><span data-stu-id="3cf07-105">Minor</span></span>   |
| <span data-ttu-id="3cf07-106">Version</span><span class="sxs-lookup"><span data-stu-id="3cf07-106">Version</span></span> | <span data-ttu-id="3cf07-107">4.5.2</span><span class="sxs-lookup"><span data-stu-id="3cf07-107">4.5.2</span></span>   |
| <span data-ttu-id="3cf07-108">Type</span><span class="sxs-lookup"><span data-stu-id="3cf07-108">Type</span></span>    | <span data-ttu-id="3cf07-109">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="3cf07-109">Runtime</span></span> |

#### <a name="details"></a><span data-ttu-id="3cf07-110">Сведения</span><span class="sxs-lookup"><span data-stu-id="3cf07-110">Details</span></span>

<span data-ttu-id="3cf07-111">По соображениям безопасности в API синтаксического анализа языка XML были внесены следующие изменения.</span><span class="sxs-lookup"><span data-stu-id="3cf07-111">For security reasons, the following changes were introduced into XML parsing APIS:</span></span>

- <span data-ttu-id="3cf07-112">Для <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=nameWithType> устанавливается значение 10 миллионов при инициализации <xref:System.Xml.XmlReaderSettings>.</span><span class="sxs-lookup"><span data-stu-id="3cf07-112"><xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=nameWithType> is set to 10 million when <xref:System.Xml.XmlReaderSettings> is initialized.</span></span>
- <span data-ttu-id="3cf07-113">По умолчанию свойству <xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=nameWithType> присваивается значение `null`.</span><span class="sxs-lookup"><span data-stu-id="3cf07-113"><xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=nameWithType> is set to `null` by default.</span></span>

> [!NOTE]
> <span data-ttu-id="3cf07-114"><xref:System.Xml.XmlReaderSettings> используется всеми средствами синтаксического анализа XML, поэтому хотя это изменение помогает в случае <xref:System.Xml.XmlReader>, оно также влияет на другие сценарии.</span><span class="sxs-lookup"><span data-stu-id="3cf07-114"><xref:System.Xml.XmlReaderSettings> is used by all XML parsers, so while this change helps the <xref:System.Xml.XmlReader> case, it also affects other scenarios.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3cf07-115">Предложение</span><span class="sxs-lookup"><span data-stu-id="3cf07-115">Suggestion</span></span>

<span data-ttu-id="3cf07-116">Чтобы вернуться к предыдущему поведению, можно задать значение в реестре.</span><span class="sxs-lookup"><span data-stu-id="3cf07-116">To revert to the previous behavior, you can set a value in the registry.</span></span> <span data-ttu-id="3cf07-117">Добавьте значение DWORD с именем `EnableLegacyXmlSettings` в раздел реестра `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\XML` и задайте для него значение `1`.</span><span class="sxs-lookup"><span data-stu-id="3cf07-117">Add a DWORD value named `EnableLegacyXmlSettings` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\XML` registry key, and set its value to `1`.</span></span> <span data-ttu-id="3cf07-118">Вместо этого можно также добавить значение реестра в куст HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="3cf07-118">You can also add the registry value in the HKEY_CURRENT_USER hive instead.</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3cf07-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="3cf07-119">Affected APIs</span></span>

- <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName>
- <xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=fullName>

<span data-ttu-id="3cf07-120">Затрагиваются также все API XML, которые прямо или косвенно зависят от <xref:System.Xml.XmlResolver>.</span><span class="sxs-lookup"><span data-stu-id="3cf07-120">In addition, any XML API that depends on <xref:System.Xml.XmlResolver>, either directly or indirectly, is affected.</span></span>

<!--

#### Affected APIs

- `P:System.Xml.XmlReaderSettings.MaxCharactersFromEntities`
- `P:System.Xml.XmlReaderSettings.XmlResolver`

-->
