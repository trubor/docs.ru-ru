---
ms.openlocfilehash: 557d811e2eeaf926cb958471d214fc23c50a25f2
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96592131"
---
- Используйте безопасный сериализатор и **не позволяйте злоумышленникам указывать произвольный тип для десериализации**. Дополнительные сведения см. в разделе [Рекомендуемые альтернативы](/dotnet/standard/serialization/binaryformatter-security-guide#preferred-alternatives).
- Примените к сериализованным данным защиту от несанкционированных изменений. После сериализации криптографически подпишите сериализованные данные. Перед десериализацией проверьте криптографическую подпись. Защитите криптографический ключ от раскрытия и реализуйте регулярную смену ключей.
- Этот параметр делает код уязвимым к атакам типа "отказ в обслуживании" и возможным атакам удаленного выполнения кода в будущем. Дополнительные сведения см. в статье [Руководство по безопасности BinaryFormatter](/dotnet/standard/serialization/binaryformatter-security-guide). Ограничьте десериализованные типы. Реализуйте пользовательский <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType>. Перед десериализацией задайте свойство `Binder` для экземпляра пользовательского класса <xref:System.Runtime.Serialization.SerializationBinder> во всех путях кода. В переопределенном методе <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A>, если тип является непредвиденным, вызовите исключение для отмены десериализации.
