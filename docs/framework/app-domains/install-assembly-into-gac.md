---
title: Практическое руководство. установку сборки в глобальный кэш сборок
description: Установка сборки в глобальный кэш сборок в .NET для ее совместного использования несколькими приложениями. Использование установщика Windows или средства глобального кэша сборок.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 581736d27d8b90430838fc78aa192a3efa21cbb5
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258303"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Практическое руководство. установку сборки в глобальный кэш сборок

В глобальном кэше сборок сохраняются сборки, которые могут использоваться несколькими приложениями. Установите сборку в [глобальный кэш сборок](gac.md) с одним из следующих компонентов:

- [Установщик Windows](#windows-installer)
- [Средство глобального кэша сборок](#global-assembly-cache-tool)

> [!IMPORTANT]
> В глобальный кэш сборок можно установить только сборки со строгими именами. Дополнительные сведения о создании сборки со строгим именем см. в разделе [Практическое руководство. Подписание сборки со строгим именем](../../standard/assembly/sign-strong-name.md).

## <a name="windows-installer"></a>Установщик Windows

[Установщик Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache) — средство установки Windows, которое рекомендуется использовать для добавления сборок в GAC. Установщик Windows предоставляет возможность подсчета ссылок на сборки в GAC и другие дополнительные возможности. Создать пакет установщика для установщика Windows можно с помощью [расширения Wix Toolset для Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>Средство глобального кэша сборок

[Служебную программу глобального кэша сборок .NET (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) можно использовать для добавления сборок в глобальный кэш сборок и для просмотра содержимого указанного кэша.

   > [!NOTE]
   > *Gacutil.exe* предназначен только для разработки. Не используйте его для установки рабочих сборок в глобальный кэш сборок.

Синтаксис для использования *gacutil.exe* для установки сборки в глобальном кэше сборок выглядит следующим образом:

```cmd
gacutil -i <assembly name>
```

В этой команде *\<assembly name>* представляет собой имя сборки, устанавливаемой в глобальный кэш сборок.

Если *gacutil.exe* нет в системном пути, используйте [оболочку командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell).

В следующем примере выполняется установка сборки с именем файла *hello.dll* в глобальный кэш сборок.

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> В предыдущих версиях .NET Framework расширение оболочки Windows *Shfusion.dll* позволяло устанавливать сборки, перетаскивая их в проводнике. Начиная с версии .NET Framework 4 расширение оболочки *Shfusion.dll* является устаревшим.

## <a name="see-also"></a>См. также

- [Работа со сборками и глобальным кэшем сборок](working-with-assemblies-and-the-gac.md)
- [Практическое руководство. Удаление сборки из глобального кэша сборок](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (программа глобального кэша сборок)](../tools/gacutil-exe-gac-tool.md)
- [Практическое руководство. Подписание сборки строгим именем](../../standard/assembly/sign-strong-name.md)
