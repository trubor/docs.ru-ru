---
title: Обновление приложений ASP.NET MVC до .NET 5
description: Используйте помощник по обновлению .NET, чтобы обновить существующее приложение ASP.NET MVC до .NET 5. Помощник по обновлению .NET — это средство CLI, которое помогает перенести приложение с .NET Framework на .NET 5.
author: ardalis
ms.date: 03/08/2021
ms.openlocfilehash: 421d8ce16bc1800451ee39c20c4746ea321fafd0
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604961"
---
# <a name="upgrade-an-aspnet-mvc-app-to-net-5-with-the-net-upgrade-assistant"></a>Обновление приложения ASP.NET MVC до .NET 5 с помощью помощника по обновлению .NET

[Помощник по обновлению .NET](upgrade-assistant-overview.md) — это средство командной строки, которое может помочь при обновлении приложений ASP.NET MVC до .NET 5. В этой статье приводится следующее:

- Демонстрация запуска средства для приложения ASP.NET MVC
- Советы по устранению неполадок

## <a name="upgrade-net-framework-aspnet-mvc-apps"></a>Обновление приложений .NET Framework ASP.NET MVC

В этом разделе демонстрируется запуск помощника по обновлению .NET для вновь созданного приложения ASP.NET MVC, предназначенного для платформы .NET Framework 4.6.1. Дополнительные сведения об установке этого средства см. в разделе [Обзор помощника по обновлению .NET](upgrade-assistant-overview.md).

### <a name="initial-demo-setup"></a>Начальная настройка для демонстрации

Если вы используете помощник по обновлению .NET для собственного приложения .NET Framework, этот шаг можно пропустить. Если вы просто хотите посмотреть, как это работает, на данном шаге показано, как настроить пример проекта ASP.NET MVC и веб-API (.NET Framework).

С помощью Visual Studio создайте новый проект веб-приложения ASP.NET с использованием .NET Framework.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/new-project.png" alt-text="Создание проекта веб-приложения ASP.NET в Visual Studio":::

Назовите проект **AspNetMvcTest**. Настройте проект для использования **.NET Framework 4.6.1**.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/configure-project.png" alt-text="Настройка проекта ASP.NET в Visual Studio":::

В следующем диалоговом окне выберите приложение **MVC**, а затем нажмите кнопку **Создать**.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/create-mvc-webapi.png" alt-text="Создание проекта ASP.NET MVC в Visual Studio":::

Ознакомьтесь с созданным проектом и его файлами, в особенности с файлами проекта.

### <a name="run-upgrade-assistant"></a>Запуск upgrade-assistant

Откройте терминал и перейдите в папку, в которой находится целевой проект или решение. Выполните команду `upgrade-assistant`, передав имя целевого проекта (можно выполнить команду из любого места, если путь к файлу проекта является допустимым).

```console
upgrade-assistant .\AspNetMvcTest.csproj
```

Средство запустится и отобразит список действий, которые оно будет выполнять.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/initial-run.png" alt-text="Начальный экран помощника по обновлению .NET":::

По мере завершения каждого шага средство предоставляет набор команд, позволяющих пользователю применить или пропустить следующий шаг, просмотреть дополнительные сведения, настроить ведение журнала или выйти из процесса. Если помощник обнаруживает, что шаг не выполняет никаких действий, он автоматически пропускает его и переходит к следующему, пока не достигнет шага, который будет выполнять действия. Нажатие клавиши <kbd>ВВОД</kbd> приведет к выполнению следующего шага, если не были выбраны другие действия.

В этом примере каждый раз выбирается шаг "применить". Первым шагом является резервное копирование проекта.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/backup-project.png" alt-text="Помощник по обновлению .NET: резервное копирование проекта":::

Помощник просит указать путь для резервной копии или использует значение по умолчанию, которое размещает резервную копию проекта в той же папке с расширением `.backup`. На следующем шаге происходит преобразование файла проекта в стиль пакета SDK.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/convert-project.png" alt-text="Помощник по обновлению .NET: преобразование проекта в стиль пакета SDK":::

После изменения формата проекта следующим шагом является обновление TFM проекта.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-tfm.png" alt-text="Помощник по обновлению .NET: обновление TFM":::

Затем средство обновляет пакеты NuGet проекта. В обновлении нуждаются несколько пакетов, поэтому добавляется новый пакет анализатора.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-nuget-packages.png" alt-text="Помощник по обновлению .NET: обновление пакетов NuGet":::

После обновления пакетов следующим шагом будет добавление файлов шаблонов (если они есть). Помощник определил, что необходимо добавить четыре ожидаемых элемента шаблона, и затем добавляет их. Эти элементы включают следующие файлы:

- `Program.cs`
- `Startup.cs`
- `appsettings.json`
- `appsettings.Development.json`

Эти файлы используются ASP.NET Core для [запуска приложения](/aspnet/core/fundamentals/startup) и [настройки](/aspnet/core/fundamentals/configuration).

:::image type="content" source="media/upgrade-assistant-aspnetmvc/add-template-files.png" alt-text="Помощник по обновлению .NET: добавление файлов шаблонов":::

Затем средство переносит файлы конфигурации. Помощник определяет параметры приложения и отключает неподдерживаемые разделы конфигурации, а затем переносит значения конфигурации `appSettings`.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/migrate-config.png" alt-text="Помощник по обновлению .NET: перенос конфигурации":::

В завершение переноса файлов конфигурации выполняется миграция `system.web.webPages.razor/pages/namespaces`.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/migrate-config2.png" alt-text="Помощник по обновлению .NET: перенос конфигурации завершен":::

Помощник применяет известные исправления для замены ссылок C# на новые аналоги.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-csharp.png" alt-text="Помощник по обновлению .NET: обновление исходного кода C#":::

Так как это последний проект, следующий шаг, "переход к следующему проекту", выводит запрос на завершение процесса переноса всего решения.

:::image type="content" source="media/upgrade-assistant-aspnetmvc/complete-solution.png" alt-text="Помощник по обновлению .NET: завершение обработки решения":::

После завершения этого процесса откройте файл проекта и проверьте его. Ищите статические файлы, подобные следующим:

```xml
  <ItemGroup>
    <Content Include="fonts\glyphicons-halflings-regular.woff2" />
    <Content Include="fonts\glyphicons-halflings-regular.woff" />
    <Content Include="fonts\glyphicons-halflings-regular.ttf" />
    <Content Include="fonts\glyphicons-halflings-regular.eot" />
    <Content Include="Content\bootstrap.min.css.map" />
    <Content Include="Content\bootstrap.css.map" />
    <Content Include="Content\bootstrap-theme.min.css.map" />
    <Content Include="Content\bootstrap-theme.css.map" />
    <Content Include="Scripts\jquery-3.4.1.slim.min.map" />
    <Content Include="Scripts\jquery-3.4.1.min.map" />
  </ItemGroup>
```

Статические файлы, которые должны обслуживаться веб-сервером, должны быть перемещены в соответствующую папку в папке корневого уровня с именем `wwwroot`. Дополнительные сведения см. в разделе [Статические файлы в ASP.NET Core](/aspnet/core/fundamentals/static-files?view=aspnetcore-5.0&preserve-view=true). После перемещения файлов можно удалить в файле проекта элементы `<Content>`, соответствующие этим файлам. Фактически все элементы `<Content>` и содержащиеся в них группы можно удалить. Кроме того, необходимо удалить все ссылки `<PackageReference>` на клиентские библиотеки, такие как `bootstrap` или `jQuery`.

По умолчанию проект будет преобразован в вид библиотеки классов. Измените атрибут первой строки `Sdk` на `Microsoft.NET.Sdk.Web` и присвойте свойству `<TargetFramework>` значение `net5.0`. Скомпилируйте проект. На этом этапе количество ошибок не должно быть большим. При переносе нового проекта ASP.NET 4.6.1 MVC, оставшиеся ошибки относятся к файлам в папке `App_Start`:

- BundleConfig.cs
- FilterConfig.cs
- RouteConfig.cs.

Эти файлы и всю папку `App_Start` можно удалить. Аналогично можно удалить файлы `Global.asax` и `Global.asax.cs`.

На этом этапе остались только ошибки, связанные с объединением. Существует [несколько способов настройки объединения и минификации в ASP.NET Core](/aspnet/core/migration/mvc?view=aspnetcore-5.0&preserve-view=true#configure-bundling-and-minification). Выберите наиболее подходящий для вашего проекта.

## <a name="troubleshooting-tips"></a>Советы по устранению неполадок

Существует несколько известных проблем, которые могут возникнуть при использовании помощника по обновлению .NET. В некоторых случаях эти проблемы связаны со [средством try-convert](https://github.com/dotnet/try-convert), которое помощник по обновлению .NET использует для внутренних целей. Это средство часто обновляется для учета большего количества сценариев, поэтому убедитесь, что вы используете последнюю версию.

- Средство **try-convert** должно быть установлено и обновлено по крайней мере до версии _0.7.212201_.
- Более ранние версии средства **try-convert** не поддерживали пользовательские целевые объекты и файлы PROPS. Если не удается выполнить обновление до последней версии, может потребоваться вручную решить эти проблемы. Если целевой файл проекта содержит ссылки на пользовательские целевые объекты или файлы PROPS, эти ссылки необходимо вручную удалить из файла до запуска помощника по обновлению .NET.

```xml
<Import Project="packages\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.2.0.1\build\net46\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.props" Condition="Exists('packages\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.2.0.1\build\net46\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.props')" />
```

[В репозитории GitHub этого средства](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues) содержатся дополнительные советы по устранению неполадок и известные проблемы.

## <a name="see-also"></a>См. также раздел

- [Обновление приложения WPF до .NET 5 с помощью помощника по обновлению .NET](upgrade-assistant-wpf-framework.md)
- [Обновление приложения Windows Forms до .NET 5 с помощью помощника по обновлению .NET](upgrade-assistant-winforms-framework.md)
- [Обзор помощника по обновлению .NET](upgrade-assistant-overview.md)
- [Репозиторий GitHub помощника по обновлению .NET](https://github.com/dotnet/upgrade-assistant)
