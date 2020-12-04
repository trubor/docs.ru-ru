---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: cf944ae9ca200d34a1f0f32e68bf3aee73a9500a
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2020
ms.locfileid: "96592140"
---
- <span data-ttu-id="8baaa-101">Если это возможно, используйте защищенный сериализатор, а **не разрешите ему указать произвольный тип для десериализации**.</span><span class="sxs-lookup"><span data-stu-id="8baaa-101">If possible, use a secure serializer instead, and **don't allow an attacker to specify an arbitrary type to deserialize**.</span></span> <span data-ttu-id="8baaa-102">Ниже приведены некоторые более безопасные сериализаторы.</span><span class="sxs-lookup"><span data-stu-id="8baaa-102">Some safer serializers include:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <span data-ttu-id="8baaa-103"><xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -Никогда не использовать <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8baaa-103"><xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> - Never use <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8baaa-104">Если необходимо использовать сопоставитель типов, ограничьте десериализованные типы до ожидаемого списка.</span><span class="sxs-lookup"><span data-stu-id="8baaa-104">If you must use a type resolver, restrict deserialized types to an expected list.</span></span>
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - <span data-ttu-id="8baaa-105">Newtonsoft Json.NET — используйте Типенамехандлинг. None.</span><span class="sxs-lookup"><span data-stu-id="8baaa-105">Newtonsoft Json.NET - Use TypeNameHandling.None.</span></span> <span data-ttu-id="8baaa-106">Если необходимо использовать другое значение для Типенамехандлинг, ограничьте десериализованные типы до ожидаемого списка с помощью настраиваемого Исериализатионбиндер.</span><span class="sxs-lookup"><span data-stu-id="8baaa-106">If you must use another value for TypeNameHandling, restrict deserialized types to an expected list with a custom ISerializationBinder.</span></span>
  - <span data-ttu-id="8baaa-107">Protocol Buffers</span><span class="sxs-lookup"><span data-stu-id="8baaa-107">Protocol Buffers</span></span>

- <span data-ttu-id="8baaa-108">Сделайте сериализованные данные несанкционированными.</span><span class="sxs-lookup"><span data-stu-id="8baaa-108">Make the serialized data tamper-proof.</span></span> <span data-ttu-id="8baaa-109">После сериализации криптографически подписывает сериализованные данные.</span><span class="sxs-lookup"><span data-stu-id="8baaa-109">After serialization, cryptographically sign the serialized data.</span></span> <span data-ttu-id="8baaa-110">Перед десериализациюм проверьте криптографическую подпись.</span><span class="sxs-lookup"><span data-stu-id="8baaa-110">Before deserialization, validate the cryptographic signature.</span></span> <span data-ttu-id="8baaa-111">Защитите криптографический ключ от раскрывать и разрабатывать для смены ключей.</span><span class="sxs-lookup"><span data-stu-id="8baaa-111">Protect the cryptographic key from being disclosed and design for key rotations.</span></span>
