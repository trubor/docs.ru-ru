---
title: Устранение неполадок при получении сообщения "Не удалось запустить это приложение"
description: Сведения о том, что делать, если отображается сообщение "Не удалось запустить это приложение".
ms.date: 09/05/2019
ms.openlocfilehash: 92055bf40500eba4f7c892d11af12d8e675ddd5d
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605247"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a>Устранение неполадок при получении сообщения об ошибке "Не удалось запустить это приложение"

Для приложений, разработанных для .NET Framework, обычно требуется, чтобы на компьютере была установлена определенная версия .NET Framework. В некоторых случаях вы можете попытаться запустить приложение без установленной или ожидаемой версии .NET Framework. В результате этого часто выводится примерно такое диалоговое окно с сообщением об ошибке:

![Не удалось запустить это приложение.](media/application-not-started/app-could-not-be-started.png)

Эта ошибка указывает на то, что выполняется одно из следующих условий:

- установка .NET Framework в системе повреждена;

- не удалось обнаружить версию .NET Framework, необходимую для приложения.

Чтобы устранить эту проблему и запустить приложение, сделайте следующее:

1. Скачайте [средство восстановления .NET Framework (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135). Средство запускается автоматически после завершения скачивания.

1. Если средство восстановления .NET Framework рекомендует какое-либо дополнительное действие, подобное показанному на следующем рисунке, нажмите кнопку **Далее**.

   ![Рекомендуемые изменения в средстве восстановления](media/application-not-started/repair-tool-recommended-changes.png)

1. В средстве восстановления .NET Framework отображается диалоговое окно, показанное на следующем рисунке, в котором указано, что изменения внесены. Не закрывайте диалоговое окно, пока выполняется повторная попытка запуска приложения. Запуск должен быть выполнен успешно, если средство восстановления .NET Framework обнаружило и устранило поврежденную установку .NET Framework.

   ![Завершенные изменения в средстве восстановления](media/application-not-started/repair-tool-changes-complete.png)

1. Если приложение успешно запускается, нажмите кнопку **Готово**. В противном случае нажмите кнопку **Далее**.

1. Если вы нажали кнопку **Далее**, в средстве восстановления .NET Framework отобразится диалоговое окно, как показано ниже. Нажмите кнопку **Готово**, чтобы отправить диагностические данные в корпорацию Майкрософт.

   ![Не удалось устранить проблему](media/application-not-started/repair-tool-no-resolution.png)

1. Если по-прежнему не удается запустить приложение, установите последнюю версию .NET Framework, поддерживаемую вашей версией Windows, как показано в следующей таблице.

   |Версия Windows|Установка .NET Framework|
   |---|---|
   |Юбилейное обновление Windows 10 или более поздние версии|[Среда выполнения .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 10, Windows 10 с обновлением за ноябрь|[.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |Windows 8.1|[Среда выполнения .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 8|[.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |Windows 7 с пакетом обновления 1 (SP1)|[Среда выполнения .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows Vista SP2|[.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > .NET Framework 4.8, предустановленная в Windows 10 с обновлением за май 2019 г.

1. Попытайтесь запустить приложение.

1. В некоторых случаях отображается диалоговое окно, подобное приведенному ниже, с предложением установить .NET Framework 3.5. Выберите **Скачать и установить этот компонент**, чтобы установить .NET Framework 3.5, а затем запустите приложение еще раз.

   ![Диалоговое окно "Компоненты Windows" с предложением установить .NET Framework 3.5](media/application-not-started/install-3-5.png)

## <a name="see-also"></a>См. также раздел

- [Требования к системе для .NET Framework](../get-started/system-requirements.md)
- [направляющая установки .NET Framework](index.md)
- [Устранение неполадок с заблокированными установками и удалениями .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
