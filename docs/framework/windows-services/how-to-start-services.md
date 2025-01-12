---
title: Практическое руководство. Запуск служб
description: Ознакомьтесь с несколькими способами запуска служб. Установленную службу необходимо запустить. Процедура запуска вызывает метод OnStart в классе службы.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
ms.openlocfilehash: bf1a4f676c3c7789036cc3650169e04892c2a191
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494549"
---
# <a name="how-to-start-services"></a>Практическое руководство. Запуск служб

Установленную службу необходимо запустить. Процедура запуска вызывает метод <xref:System.ServiceProcess.ServiceBase.OnStart%2A> в классе службы. Как правило, метод <xref:System.ServiceProcess.ServiceBase.OnStart%2A> определяет полезные действия, которые будет выполнять служба. Запущенная служба остается активной, пока не будет приостановлена или остановлена вручную.

Службы можно настроить на запуск автоматически или вручную. Служба, которая запускается автоматически, будет запущена при первом включении или перезагрузке компьютера, на котором она установлена. Службу, которая запускается вручную, должен запустить пользователь.

> [!NOTE]
> По умолчанию службы, созданные с помощью Visual Studio, настроены на запуск вручную.

Есть несколько способов запуска службы вручную: из **диспетчера служб** или **обозревателя сервера** либо из кода, используя компонент, который называется <xref:System.ServiceProcess.ServiceController>.

Вы можете задать свойство <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> в классе <xref:System.ServiceProcess.ServiceInstaller>, чтобы определить способ запуска службы — вручную или автоматически.

## <a name="specify-how-a-service-should-start"></a>Указание способа запуска службы

1. Создав службу, добавьте для нее необходимые установщики. Дополнительные сведения см. в разделе [Практическое руководство. Добавление установщиков в приложение-службу](how-to-add-installers-to-your-service-application.md).

2. В конструкторе щелкните установщик процессов службы, с которой вы работаете.

3. В **окне свойств** задайте свойству <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> одно из следующих значений:

    |Чтобы установить службу|Задайте это значение|
    |----------------------------------|--------------------|
    |При перезапуске компьютера|**Автоматический**|
    |При запуске службы с помощью явного действия пользователя|**Manual** (Вручную)|

    > [!TIP]
    > Чтобы полностью запретить запуск службы, можно задать свойству <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> значение **Disabled** (Отключено). Это можно сделать, если вы собираетесь перезагружать сервер несколько раз и хотите сэкономить время, запретив запуск служб, которые обычно запускаются одновременно.

    > [!NOTE]
    > Эти и другие свойства можно изменить после установки службы.

    Есть несколько способов запуска службы, для процесса <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> которой настроено значение **Manual** (Вручную): из **диспетчера служб** или **обозревателя серверов** либо из кода. Важно отметить, что в действительности не все эти методы приводят к запуску службы в контексте **диспетчера служб**. При использовании **обозревателя сервера** и программных способов применяется контроллер.

## <a name="start-a-service-from-server-explorer"></a>Запуск службы из обозревателя сервера

1. В **обозревателе сервера** добавьте нужный сервер, если его нет в списке. Дополнительные сведения см. в разделах "Практическое руководство. Подключение и инициализация обозревателя серверов или обозревателя баз данных".

2. Разверните узел **Службы** и выберите службу, которую нужно запустить.

3. Щелкните имя службы правой кнопкой мыши и выберите **Запуск**.

### <a name="start-a-service-from-services"></a>Запуск службы из приложения "Службы"

1. Откройте приложение **Службы**.

2. Выберите службу в списке, щелкните ее правой кнопкой мыши и выберите **Запуск**.

## <a name="start-a-service-from-code"></a>Запуск службы из кода

1. Создайте экземпляр класса <xref:System.ServiceProcess.ServiceController> и настройте его для взаимодействия со службой, которой нужно управлять.

2. Чтобы запустить службу, вызовите метод <xref:System.ServiceProcess.ServiceController.Start%2A>.

## <a name="see-also"></a>См. также

- [Знакомство с приложениями служб Windows](introduction-to-windows-service-applications.md)
- [Практическое руководство. Создание служб Windows](how-to-create-windows-services.md)
- [Практическое руководство. Добавление установщиков в приложение-службу](how-to-add-installers-to-your-service-application.md)
