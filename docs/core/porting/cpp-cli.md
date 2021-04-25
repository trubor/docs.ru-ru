---
title: Перенос проектов C++/CLI в .NET Core
description: Сведения о переносе проектов C++/CLI в .NET Core.
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: 60c4cc2040b5cfb7aadc2147832d3f0a763085dc
ms.sourcegitcommit: 5ddbd1f65d0369b4cc8c8ff91c72f1b524c90221
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2021
ms.locfileid: "107514400"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a>Перенос проекта C++/CLI в .NET Core

Начиная с .NET Core 3.1 и Visual Studio 2019 версии 16.4 [проекты C++/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) можно ориентировать на .NET Core. Такая поддержка позволяет переносить классические приложения для Windows в .NET Core с помощью уровней взаимодействия C++/CLI. В этой статье описывается, как перенести проекты C++/CLI из .NET Framework в .NET Core 3.1.

## <a name="ccli-net-core-limitations"></a>Ограничения для C++/CLI .NET Core

Существуют некоторые важные ограничения, касающиеся переноса проектов C++/CLI в .NET Core, в сравнении с другими языками:

* Поддержка переноса проектов из C++/CLI в .NET Core реализована только для Windows.
* Проекты C++/CLI невозможно ориентировать на .NET Standard, только на .NET Core (или .NET Framework).
* Проекты C++/CLI не поддерживают новый формат файла проекта в стиле пакета SDK. Вместо этого даже при ориентировании на .NET Core в проектах C++/CLI используется существующий формат файлов VCXPROJ.
* Проекты C++/CLI невозможно ориентировать на несколько платформ .NET. Если необходимо создать проект C++/CLI как для .NET Framework, так и для .NET Core, следует использовать отдельные файлы проекта.
* .NET Core не поддерживает компиляцию `-clr:pure` или `-clr:safe`, только новый параметр `-clr:netcore` (эквивалентный `-clr` для .NET Framework).

## <a name="port-a-ccli-project"></a>Перенос проекта C++/CLI

Чтобы перенести проект C++/CLI в .NET Core, внесите следующие изменения в файл VCXPROJ. Эти шаги по переносу отличаются от действий, которые необходимо выполнить с проектами других типов, поскольку проекты C++/CLI не используют файлы проектов в стиле пакета SDK.

1. Замените свойства `<CLRSupport>true</CLRSupport>` на `<CLRSupport>NetCore</CLRSupport>`. Это свойство зачастую находится в группах свойств, зависящих от конфигурации, поэтому его может потребоваться заменить в нескольких местах.
2. Замените свойства `<TargetFrameworkVersion>` на `<TargetFramework>netcoreapp3.1</TargetFramework>`.
3. Удалите все ссылки .NET Framework (например, `<Reference Include="System" />`). При использовании `<CLRSupport>NetCore</CLRSupport>` сборки пакета SDK для .NET Core упоминаются автоматически.
4. При необходимости обновите использование API в файлах CPP, чтобы удалить API, которые недоступны для .NET Core. Поскольку проекты C++/CLI, как правило, представляют собой очень тонкие уровни взаимодействия, зачастую требуется внести не так много изменений. Можно использовать [анализатор переносимости .NET](../../standard/analyzers/portability-analyzer.md) для обнаружения неподдерживаемых API .NET, используемых двоичными файлами C++/CLI, так же, как и в случае с полностью управляемыми двоичными файлами. Рекомендации по определению возможности переноса кода и обновлению проектов для работы с API .NET Core представлены в [руководстве по переносу библиотек](./libraries.md#determine-portability).

### <a name="wpf-and-windows-forms-usage"></a>Использование WPF и Windows Forms

Проекты .NET C++Core/CLI могут использовать API Windows Forms и WPF. Чтобы использовать эти API Windows Desktop, в библиотеки пользовательского интерфейса необходимо добавить явные ссылки на платформы. Проекты в стиле пакета SDK, использующие API Windows Desktop, ссылаются на необходимые библиотеки платформы автоматически с помощью пакета SDK для `Microsoft.NET.Sdk.WindowsDesktop`. Поскольку проекты C++/CLI не используют формат проекта в стиле пакета SDK, в них следует добавить явные ссылки на платформы при ориентировании на .NET Core.

Чтобы использовать API Windows Forms, добавьте эту ссылку в файл VCXPROJ:

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

Чтобы использовать API WPF, добавьте эту ссылку в файл VCXPROJ:

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

Чтобы использовать как API Windows Forms, так и API WPF, добавьте эту ссылку в файл VCXPROJ:

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

В настоящее время отсутствует возможность добавить эти ссылки с помощью диспетчера ссылок Visual Studio. Вместо этого файл проекта требуется обновить вручную. Такое обновление можно выполнить в Visual Studio, выгрузив проект, а затем отредактировав файл проекта. Можно также использовать другой редактор, например VS Code.

## <a name="build-without-msbuild"></a>Сборка без MSBuild

Кроме того, проекты C++/CLI можно создавать без использования MSBuild. Выполните следующие действия, чтобы создать проект C++/CLI для .NET Core непосредственно с помощью файлов *cl.exe* и *link.exe*:

1. При компиляции передайте `-clr:netcore` в *cl.exe*.
2. Создайте ссылки на необходимые базовые сборки .NET Core.
3. При связывании укажите `LibPath` в качестве основного каталога приложения .NET Core (чтобы можно было найти файл *ijwhost.lib*).
4. Скопируйте файл *ijwhost.dll* (из основного каталога приложения .NET Core) в выходной каталог проекта.
5. Убедитесь, что для первого компонента приложения, который будет выполнять управляемый код, существует файл [runtimeconfig.json](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md). Если приложение имеет управляемую точку входа, файл `runtime.config` будет создан и скопирован автоматически. Тем не менее, если приложение имеет собственную точку входа, для первой библиотеки C++/CLI необходимо создать файл `runtimeconfig.json`, чтобы использовать среду выполнения .NET Core.

## <a name="known-issues"></a>Известные проблемы

Существует несколько известных проблем, на которые следует обратить внимание при работе с проектами C++/CLI, ориентированными на .NET Core.

* Ссылка на платформу WPF в проектах C++/CLI .NET Core в настоящее время вызывает отображение некоторых внешних предупреждений о том, что не удается импортировать символы. Эти предупреждения можно спокойно игнорировать. В скором времени это будет исправлено.
* Если приложение имеет собственную точку входа, для библиотеки C++/CLI, которая первой выполняет управляемый код, требуется файл [runtimeconfig.json](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md). Этот файл конфигурации используется при запуске среды выполнения .NET Core. Проекты C++/CLI пока не создают файлы `runtimeconfig.json` автоматически во время сборки, поэтому файл необходимо создавать вручную. Если библиотека C++/CLI вызывается из управляемой точки входа, то библиотеке C++/CLI не требуется файл `runtimeconfig.json` (поскольку сборка точки входа будет иметь имя, используемое при запуске среды выполнения). Ниже приведен пример простого файла `runtimeconfig.json`. Дополнительные сведения см. в [спецификациях на сайте GitHub](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md).

    ```json
    {
          "runtimeOptions": {
             "tfm": "netcoreapp3.1",
             "framework": {
                "name": "Microsoft.NETCore.App",
                "version": "3.1.0"
             }
          }
    }
    ```

* В Windows 7 загрузка сборки .NET Core C++/CLI может вызывать сбои, если входное приложение является платформенным. Сбои происходят из-за того, что загрузчик Windows 7 не учитывает точки входа, не относящиеся к `mscoree.dll`, для сборок C++/CLI. Рекомендуемым решением является преобразование входного приложения в управляемый код. Сценарии, предполагающие использование локального по отношению к потоку хранилища (TLS), не поддерживаются строго в Windows 7 ни для каких случаев.
