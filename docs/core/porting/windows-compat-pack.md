---
title: Перенос кода с помощью пакета обеспечения совместимости Windows
description: Сведения о пакете обеспечения совместимости Windows и его использовании для переноса существующего кода .NET Framework на .NET 5 и .NET Core 3.1.
author: terrajobst
ms.date: 03/04/2021
ms.openlocfilehash: 655657e38f564d84ea3e56b5374debc04b405eeb
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873644"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-5"></a>Перенос кода в .NET 5+ с помощью пакета обеспечения совместимости Windows

Некоторые из наиболее распространенных проблем при переносе существующего кода из .NET Framework в .NET связаны с зависимостями от API и технологий, которые доступны только в .NET Framework. *Пакет обеспечения совместимости Windows* предоставляет многие из этих технологий. Это значительно упрощает создание приложений .NET и библиотек .NET Standard.

Пакет обеспечения совместимости является логическим [расширением платформы .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support), который значительно расширяет набор API. Существующий код компилируется практически без изменений. Чтобы сдержать обещание "это набор API, который предоставляет все реализации .NET", платформа .NET Standard не включает технологии, которые не могут работать на всех платформах, такие как реестр, инструментарий управления Windows (WMI) или API порождения отражения. Пакет обеспечения совместимости Windows основан на .NET Standard и обеспечивает доступ к таким технологиям, которые доступны только в Windows. Это особенно удобно для клиентов, которые хотят перейти на .NET, но по меньшей мере на первом этапе планируют оставаться в Windows. В этом сценарии возможность использования технологий, предназначенных только для Windows, устраняет препятствия для миграции.

## <a name="package-contents"></a>Содержимое пакета

Пакет обеспечения совместимости Windows предоставляется с помощью [пакета NuGet Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility). Ссылаться на него можно из проектов, предназначенных для .NET или .NET Standard.

Он предоставляет около 20 000 API, включая API только для Windows и кросс-платформенные API из следующих технологических областей:

- Кодовые страницы
- CodeDom
- Конфигурация
- Служба каталогов
- Рисование
- ODBC
- Разрешения
- Порты
- Списки управления доступом Windows (ACL)
- Windows Communication Foundation (WCF)
- Шифрование Windows
- Windows EventLog
- Инструментарий управления Windows (WMI)
- Счетчики производительности Windows
- реестр Windows;
- Кэширование среды выполнения Windows
- службы Windows

Дополнительные сведения см. в [характеристиках пакета обеспечения совместимости](https://github.com/dotnet/designs/blob/main/accepted/2018/compat-pack/compat-pack.md).

## <a name="get-started"></a>Начало работы

1. Перед переносом обязательно проверьте [процесс переноса](index.md).

2. При переносе существующего кода в .NET или .NET Standard установите пакет NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

   Если вы хотите остаться на Windows, больше ничего не требуется.

3. Если вы хотите запускать приложение .NET или библиотеку .NET Standard в macOS или Linux, используйте [анализатор API](../../standard/analyzers/api-analyzer.md), чтобы найти используемые API, которые не будут работать на разных платформах.

4. Удалите случаи использования этих API, замените их на кроссплатформенные альтернативы или защитите с помощью проверки платформы, например:

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

Демонстрацию см. в [видео Channel 9 по пакету обеспечения совместимости Windows](https://channel9.msdn.com/Events/Connect/2017/T123).

## <a name="see-also"></a>См. также раздел

- [Общие сведения о переносе кода в .NET Framework из .NET](index.md)
- [Миграция с ASP.NET на ASP.NET Core](/aspnet/core/migration/proper-to-2x)
- [Перенос приложений WPF из .NET Framework на .NET](/dotnet/desktop/wpf/migration/convert-project-from-net-framework?view=netdesktop-5.0&preserve-view=true)
- [Перенос приложений Windows Forms из .NET Framework на .NET Core](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
- [Перенос библиотек .NET Framework в .NET](libraries.md)
