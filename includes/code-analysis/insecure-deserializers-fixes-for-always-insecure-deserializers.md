---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: cf944ae9ca200d34a1f0f32e68bf3aee73a9500a
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96592140"
---
- <span data-ttu-id="5c4f4-101">Если возможно, используйте безопасный сериализатор и **не позволяйте злоумышленникам указывать произвольный тип для десериализации**.</span><span class="sxs-lookup"><span data-stu-id="5c4f4-101">If possible, use a secure serializer instead, and **don't allow an attacker to specify an arbitrary type to deserialize**.</span></span> <span data-ttu-id="5c4f4-102">Ниже приведены некоторые из более безопасных сериализаторов:</span><span class="sxs-lookup"><span data-stu-id="5c4f4-102">Some safer serializers include:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <span data-ttu-id="5c4f4-103"><xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> — никогда не использовать <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5c4f4-103"><xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> - Never use <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5c4f4-104">Если необходимо использовать сопоставитель типов, ограничьте десериализованные типы ожидаемым списком.</span><span class="sxs-lookup"><span data-stu-id="5c4f4-104">If you must use a type resolver, restrict deserialized types to an expected list.</span></span>
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - <span data-ttu-id="5c4f4-105">Json.NET Newtonsoft — использовать TypeNameHandling.None.</span><span class="sxs-lookup"><span data-stu-id="5c4f4-105">Newtonsoft Json.NET - Use TypeNameHandling.None.</span></span> <span data-ttu-id="5c4f4-106">Если необходимо использовать другое значение для TypeNameHandling, ограничьте десериализованные типы ожидаемым списком с помощью настраиваемого ISerializationBinder.</span><span class="sxs-lookup"><span data-stu-id="5c4f4-106">If you must use another value for TypeNameHandling, restrict deserialized types to an expected list with a custom ISerializationBinder.</span></span>
  - <span data-ttu-id="5c4f4-107">Protocol Buffers</span><span class="sxs-lookup"><span data-stu-id="5c4f4-107">Protocol Buffers</span></span>

- <span data-ttu-id="5c4f4-108">Примените к сериализованным данным защиту от несанкционированных изменений.</span><span class="sxs-lookup"><span data-stu-id="5c4f4-108">Make the serialized data tamper-proof.</span></span> <span data-ttu-id="5c4f4-109">После сериализации криптографически подпишите сериализованные данные.</span><span class="sxs-lookup"><span data-stu-id="5c4f4-109">After serialization, cryptographically sign the serialized data.</span></span> <span data-ttu-id="5c4f4-110">Перед десериализацией проверьте криптографическую подпись.</span><span class="sxs-lookup"><span data-stu-id="5c4f4-110">Before deserialization, validate the cryptographic signature.</span></span> <span data-ttu-id="5c4f4-111">Защитите криптографический ключ от раскрытия и реализуйте регулярную смену ключей.</span><span class="sxs-lookup"><span data-stu-id="5c4f4-111">Protect the cryptographic key from being disclosed and design for key rotations.</span></span>
