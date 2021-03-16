---
title: Обновление приложений WPF до .NET 5
description: Используйте помощник по обновлению .NET, чтобы обновить существующее приложение WPF до .NET 5. Помощник по обновлению .NET — это средство CLI, которое помогает перенести приложение с .NET Framework на .NET 5.
author: ardalis
ms.date: 02/25/2021
ms.openlocfilehash: e71cdc0ef5b72fcb7ae3985a26672e23ed0c1f12
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102108295"
---
# <a name="upgrade-a-wpf-app-to-net-5-with-the-net-upgrade-assistant"></a>Обновление приложения WPF до .NET 5 с помощью помощника по обновлению .NET

[Помощник по обновлению .NET](upgrade-assistant-overview.md) — это средство командной строки, которое может помочь при обновлении приложений WPF до .NET 5. В этой статье приводится следующее:

* Демонстрация запуска средства для приложения WPF
* Советы по устранению неполадок

## <a name="upgrade-net-framework-wpf-apps"></a>Обновление приложений .NET Framework WPF

В этом разделе демонстрируется запуск помощника по обновлению .NET для вновь созданного приложения WPF, предназначенного для платформы .NET Framework 4.6.1. Дополнительные сведения об установке этого средства см. в разделе [Обзор помощника по обновлению .NET](upgrade-assistant-overview.md).

### <a name="initial-demo-setup"></a>Начальная настройка для демонстрации

Если вы используете помощник по обновлению .NET для собственного приложения .NET Framework, этот шаг можно пропустить. Если вы просто хотите посмотреть, как это работает, на этом шаге вы узнаете, как настроить пример проекта .NET WPF.

С помощью Visual Studio создайте новое приложение WPF с использованием платформы .NET Framework.

:::image type="content" source="media/upgrade-assistant-wpf-framework/new-project.png" alt-text="Создание нового проекта WPF в Visual Studio":::

Присвойте проекту имя **WpfTest**. Настройте проект для использования **.NET Framework 4.6.1**.

:::image type="content" source="media/upgrade-assistant-wpf-framework/configure-project.png" alt-text="Настройка проекта Windows Forms в Visual Studio":::

Ознакомьтесь с созданным проектом и его файлами, в особенности с файлами проекта.

### <a name="run-upgrade-assistant"></a>Запуск upgrade-assistant

Откройте терминал и перейдите в папку, в которой находится целевой проект или решение. Выполните команду `upgrade-assistant`, передав имя целевого проекта (можно выполнить команду из любого места, если путь к файлу проекта является допустимым).

```console
upgrade-assistant .\WpfTest.csproj
```

Средство запустится и отобразит список действий, которые оно будет выполнять.

:::image type="content" source="media/upgrade-assistant-wpf-framework/initial-run.png" alt-text="Начальный экран помощника по обновлению .NET":::

По мере завершения каждого шага средство предоставляет набор команд, позволяющих пользователю применить или пропустить следующий шаг, просмотреть дополнительные сведения, настроить ведение журнала или выйти из процесса. Если помощник обнаруживает, что шаг не выполняет никаких действий, он автоматически пропускает его и переходит к следующему, пока не достигнет шага, который будет выполнять действия. Нажатие клавиши ВВОД приведет к выполнению следующего шага, если не были выбраны другие действия.

В этом примере каждый раз выбирается шаг "применить". Первым шагом является резервное копирование проекта.

:::image type="content" source="media/upgrade-assistant-wpf-framework/backup-project.png" alt-text="Помощник по обновлению .NET: резервное копирование проекта":::

Помощник просит указать путь для резервной копии или использует значение по умолчанию, которое размещает резервную копию проекта в той же папке с расширением `.backup`. На следующем шаге происходит преобразование файла проекта в стиль пакета SDK.

:::image type="content" source="media/upgrade-assistant-wpf-framework/convert-project.png" alt-text="Помощник по обновлению .NET: преобразование проекта в стиль пакета SDK":::

После изменения формата проекта следующим шагом является обновление TFM проекта.

:::image type="content" source="media/upgrade-assistant-wpf-framework/update-tfm.png" alt-text="Помощник по обновлению .NET: преобразование проекта в стиль пакета SDK":::

Затем средство обновляет пакеты NuGet проекта.

:::image type="content" source="media/upgrade-assistant-wpf-framework/update-nuget-packages.png" alt-text="Помощник по обновлению .NET: обновление пакетов NuGet":::

После обновления пакетов следующим шагом будет добавление файлов шаблонов (если они есть). В этом примере отсутствуют файлы шаблонов, которые нужно добавить. Этот шаг продолжит выполнение и перенесет файлы конфигурации приложения и обновит исходный код C#, чтобы применить исправления, как показано ниже. Для этого проекта не требуется вносить изменения в файл конфигурации или исходный код, поэтому этот шаг пройдет автоматически.

:::image type="content" source="media/upgrade-assistant-wpf-framework/add-template-files.png" alt-text="Помощник по обновлению .NET: добавление файлов шаблонов и миграция конфигурации":::

Так как это последний проект, следующий шаг, "переход к следующему проекту", выводит запрос на завершение процесса переноса всего решения.

:::image type="content" source="media/upgrade-assistant-wpf-framework/complete-solution.png" alt-text="Помощник по обновлению .NET: завершение обработки решения":::

После завершения этого процесса перенесенный проект WPF будет выглядеть примерно так:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net5.0-windows</TargetFramework>
    <OutputType>WinExe</OutputType>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <UseWPF>true</UseWPF>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Microsoft.CSharp" Version="4.7.0" />
    <PackageReference Include="Microsoft.DotNet.UpgradeAssistant.Extensions.Default.Analyzers" Version="0.2.211942">
      <PrivateAssets>all</PrivateAssets>
    </PackageReference>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="5.0.2" />
  </ItemGroup>
</Project>
```

Обратите внимание, что помощник по обновлению .NET также добавляет в проект анализаторы, помогающие продолжить процесс обновления.

## <a name="troubleshooting-tips"></a>Советы по устранению неполадок

Существует несколько известных проблем, которые могут возникнуть при использовании помощника по обновлению .NET. В некоторых случаях эти проблемы связаны со [средством try-convert](https://github.com/dotnet/try-convert), которое помощник по обновлению .NET использует для внутренних целей. Это средство часто обновляется для учета большего количества сценариев, поэтому убедитесь, что вы используете последнюю версию.

- Средство try-convert должно быть установлено и обновлено по крайней мере до версии _0.7.21201_.
- Более ранние версии средства try-convert не поддерживали пользовательские целевые объекты и файлы PROPS. Если не удается выполнить обновление до последней версии, может потребоваться вручную решить эти проблемы. Если целевой файл проекта содержит ссылки на пользовательские целевые объекты или файлы PROPS, эти ссылки необходимо вручную удалить из файла до запуска помощника по обновлению .NET.

[В репозитории GitHub этого средства](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues) содержатся дополнительные советы по устранению неполадок и известные проблемы.

## <a name="see-also"></a>См. также раздел

- [Обновление приложения Windows Forms до .NET 5 с помощью помощника по обновлению .NET](upgrade-assistant-winforms-framework.md)
- [Обновление приложения ASP.NET MVC до .NET 5 с помощью помощника по обновлению .NET](upgrade-assistant-aspnetmvc.md)
- [Обзор помощника по обновлению .NET](upgrade-assistant-overview.md)
- [Репозиторий GitHub помощника по обновлению .NET](https://github.com/dotnet/upgrade-assistant)
