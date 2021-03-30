---
title: Выбор .NET Framework для контейнеров Docker
description: Архитектура микрослужб .NET для упакованных в контейнеры приложений .NET | Выбор .NET Framework для контейнеров Docker
ms.date: 01/13/2021
ms.openlocfilehash: fa644753c3a39f285052aba7a8524ea96442c842
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873137"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Выбор .NET Framework для контейнеров Docker

Хотя среда .NET 5 предоставляет значительные преимущества для новых приложений и шаблонов приложений, мы рекомендуем использовать среду .NET Framework для большинства имеющихся сценариев.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Перенос существующих приложений непосредственно в контейнер Windows Server

Даже если вы не создаете микрослужбы, контейнеры Docker можно использовать для упрощения развертывания. Например, вы хотите улучшить функционирование рабочего процесса DevOps с помощью Docker. Использование контейнеров позволит вам получить хорошо изолированную тестовую среду и устранить проблемы с развертыванием, вызванные отсутствием зависимостей при перемещении в рабочую среду. В таких случаях даже при развертывании монолитных приложений имеет смысл использовать Docker и контейнеры Windows для текущего приложения .NET Framework.

В большинстве случаев при таком сценарии перенос существующих приложений на .NET 5 не требуется. Можно использовать контейнеры Docker, в которые включена традиционная платформа .NET Framework. Тем не менее для расширения готовых приложений, например для разработки новой службы в ASP.NET Core рекомендуется использовать .NET 5.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-5"></a>Использование сторонних библиотек .NET и пакетов NuGet, недоступных для .NET 5

Сторонние библиотеки [.NET Standard](../../../standard/net-standard.md) позволяют совместно использовать код в различных вариантах приложения .NET, в том числе в .NET 5. С появлением .NET Standard 2.0 и более поздних версий, совместимость области API с различными платформами стала значительно больше. Кроме того, .NET Core 2.x и более новые приложения также могут ссылаться непосредственно на существующие библиотеки .NET Framework (см. [.NET Framework 4.6.1 supporting .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20) (.NET Framework 4.6.1, поддерживающие .NET Standard 2.0)).

Кроме того, [пакет обеспечения совместимости Windows](../../../core/porting/windows-compat-pack.md) расширяет доступную для .NET Standard 2.0 область API-интерфейсов в Windows. Этот пакет позволяет почти без изменений перекомпилировать существующий код под платформу .NET Standard версии 2.x, чтобы выполнять его в Windows.

Несмотря на значительный прогресс, достигнутый после выхода .NET Standard 2.0 и .NET Core 2.1 и более поздних версий, некоторые пакеты NuGet пока запускаются только в ОС Windows и не поддерживают .NET Core и более поздних версий. Если эти пакеты имеют важное значение для вашего приложения, необходимо использовать .NET Framework в контейнерах Windows.

## <a name="using-net-technologies-not-available-for-net-5"></a>Использование технологий .NET, недоступных для .NET 5

Некоторые технологии .NET Framework отсутствуют в текущей версии .NET (версии 5.0 на момент написания этой статьи). Поддержка некоторых из них может быть доступна в последующих выпусках, однако остальные технологии не соответствуют новым шаблонам приложений, используемым в среде .NET Core, и могут быть недоступными всегда.

В следующем списке указано большинство технологий, недоступных в .NET 5.

- Веб-формы ASP.NET. Эта технология доступна только в .NET Framework. В настоящее время добавление веб-форм ASP.NET в среду .NET и более поздних версий не планируется.

- Службы WCF. Даже с [клиентской библиотекой WCF](https://github.com/dotnet/wcf), которая позволяет использовать службы WCF из среды .NET 5, по состоянию на январь 2021 г. реализация сервера WCF доступна только для .NET Framework.

- Службы, связанные с рабочим процессом. Службы Windows Workflow Foundation (WF), Workflow Services (WCF и WF в одной службе) и WCF Data Services (известные как службы данных ADO.NET) доступны только в среде .NET Framework. В настоящий момент не планируется их перенос в .NET 5.

В дополнение к технологиям, перечисленным в официальном [Плане по .NET](https://github.com/dotnet/core/blob/main/roadmap.md), в [новую унифицированную платформу](https://devblogs.microsoft.com/dotnet/introducing-net-5/) могут быть перенесены и другие функции. Вы можете принять участие в обсуждениях на сайте GitHub и выразить свое мнение. Если вы думаете, что чего-то не хватает, отправьте новый вопрос [dotnet/runtime](https://github.com/dotnet/runtime/issues/new) в репозитории GitHub.

## <a name="using-a-platform-or-api-that-doesnt-support-net-5"></a>Использование платформы или API, которые не поддерживают .NET 5

Некоторые платформы Майкрософт и платформы сторонних поставщиков не поддерживают среду .NET 5. Например, некоторые другие службы Azure предоставляют пакеты SDK, которые пока невозможно использовать в среде .NET 5. В конечном итоге, большинство пакетов SDK Azure будут перенесены в .NET 5 или Standard, но некоторые из них могут не перенестись по разным причинам. Доступные пакеты SDK для Azure можно просмотреть на странице [Azure SDK Latest Releases](https://azure.github.io/azure-sdk/releases/latest/index.html) (Последние выпуски пакета SDK Azure).

В течение этого переходного периода, если окажется, что какая-либо платформа или служба в Azure пока еще не поддерживает среду .NET 5 с ее клиентским API, вы можете использовать аналогичный интерфейс REST API службы Azure или пакет SDK для клиента на платформе .NET Framework.

### <a name="additional-resources"></a>Дополнительные ресурсы

- **Документация по .NET** \
  [https://docs.microsoft.com/dotnet/fundamentals](../../../fundamentals/index.yml)

- **Перенос проектов в .NET 5** \
  [https://channel9.msdn.com/Events/dotnetConf/2020/Porting-Projects-to-NET-5](https://channel9.msdn.com/Events/dotnetConf/2020/Porting-Projects-to-NET-5)

- **Инструкции по использованию .NET в Docker** \
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **Общие сведения о компонентах .NET** \
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[Назад](net-core-container-scenarios.md)
>[Вперед](container-framework-choice-factors.md)
