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
- Если возможно, используйте безопасный сериализатор и **не позволяйте злоумышленникам указывать произвольный тип для десериализации**. Ниже приведены некоторые из более безопасных сериализаторов:

  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> — никогда не использовать <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>. Если необходимо использовать сопоставитель типов, ограничьте десериализованные типы ожидаемым списком.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Json.NET Newtonsoft — использовать TypeNameHandling.None. Если необходимо использовать другое значение для TypeNameHandling, ограничьте десериализованные типы ожидаемым списком с помощью настраиваемого ISerializationBinder.
  - Protocol Buffers

- Примените к сериализованным данным защиту от несанкционированных изменений. После сериализации криптографически подпишите сериализованные данные. Перед десериализацией проверьте криптографическую подпись. Защитите криптографический ключ от раскрытия и реализуйте регулярную смену ключей.
