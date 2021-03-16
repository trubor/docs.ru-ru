---
description: 'Дополнительные сведения: -subsystemversion (Visual Basic)'
title: -subsystemversion
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: 2aecf08b95249b6c4285ca7fe71f4e488f8db3c8
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480826"
---
# <a name="-subsystemversion-visual-basic"></a>-subsystemversion (Visual Basic)

Указывает минимальную версию подсистемы, в которой может выполняться созданный исполняемый файл, то есть определяет версии Windows, в которых может работать исполняемый файл. Чаще всего этот параметр предоставляет исполняемому файлу возможность использовать определенные возможности безопасности, недоступные в прежних версиях Windows.

> [!NOTE]
> Чтобы задать саму подсистему, используйте параметр компилятора [-target](target.md).

## <a name="syntax"></a>Синтаксис

```vb
-subsystemversion:major.minor
```

## <a name="parameters"></a>Параметры

`major.minor`

Минимальная требуемая версия подсистемы, через точку записывается основная и дополнительная версии. Например, можно указать, что приложение не может выполняться в операционной системе старше Windows 7, если задать для этого параметра значение 6.01, как указано в таблице ниже в этом разделе. Необходимо указать значения для параметра `major` и `minor` в виде целых чисел.

Нули в начале версии `minor` не изменяют версию, нули в конце — изменяют. Например, 6.1 и 6.01 — одна версия, а 6.10 — другая. Рекомендуется указывать дополнительный номер версии двумя цифрами, чтобы избежать путаницы.

## <a name="remarks"></a>Примечания

В следующей таблице перечислены распространенные версии подсистем Windows.

|Версия Windows|Версия подсистемы|
|---------------------|-----------------------|
|Windows 2000|5.00|
|Windows XP|5.01|
|Windows Server 2003|5.02|
|Windows Vista|6.00|
|Windows 7|6.01|
|Windows Server 2008|6.01|
|Windows 8|6.02|

## <a name="default-values"></a>Значения по умолчанию

Значение по умолчанию параметра компилятора **-subsystemversion** зависит от условий в следующем списке:

- Значение по умолчанию — 6.02, если задан любой параметр компилятора из следующего списка.

  - [/target:appcontainerexe](target.md)

  - [/target:winmdobj](target.md)

  - [-platform:arm](platform.md)

- Значение по умолчанию — 6.00, если используется средство MSBuild, приложение предназначено для .NET Framework 4.5 и не установлены параметры компилятора, определенные ранее в этом списке.

- Если ни одно из предыдущих условий не верно, значение по умолчанию — 4.00.

## <a name="setting-this-option"></a>Задание этого параметра

Чтобы задать параметр компилятора **-subsystemversion** в Visual Studio, нужно открыть файл .vbproj и указать значение для свойства `SubsystemVersion` в XML MSBuild. Этот параметр невозможно задать в интегрированной среде разработки Visual Studio. Дополнительные сведения см. выше в подразделе "Значения по умолчанию" или в разделе [Общие свойства проектов MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="see-also"></a>См. также

- [Компилятор Visual Basic с интерфейсом командной строки](index.md)

- [Свойства MSBuild](/visualstudio/msbuild/msbuild-properties)
