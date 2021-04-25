---
title: DevOps для разработчиков ASP.NET Core
author: CamSoper
description: Рекомендации по созданию сквозного решения конвейера DevOps для приложения ASP.NET Core, размещенного в Azure.
ms.author: casoper
ms.date: 04/13/2021
ms.custom: devx-track-csharp, mvc, seodec18
no-loc:
- appsettings.json
- ASP.NET Core Identity
- cookie
- Cookie
- Blazor
- Blazor Server
- Blazor WebAssembly
- Identity
- Let's Encrypt
- Razor
- SignalR
uid: azure/devops/index
ms.openlocfilehash: 5052c16e637260ede3a81578ba2280f760d086c4
ms.sourcegitcommit: 040b745ac19e4a5d23df17422ab30e72839f5754
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2021
ms.locfileid: "107810518"
---
# <a name="devops-for-aspnet-core-developers"></a>DevOps для разработчиков ASP.NET Core

[![Изображение обложки](./media/cover-large.png)](https://aka.ms/devopsbook)

**Редакция 1.1.0**

Обновления книги и вклад сообщества см. в [журнале изменений](https://aka.ms/devops-ebook-changelog).

Это руководство доступно как [загружаемая электронная книга в формате PDF](https://aka.ms/devopsbook).

ИЗДАТЕЛЬ

Подразделение Microsoft Developer Division, команды разработки .NET и Visual Studio

Подразделение корпорации Майкрософт

One Microsoft Way

Redmond, Washington 98052-6399

&copy; Корпорация Майкрософт (Microsoft Corporation), 2021.

Все права защищены. Запрещается полное или частичное воспроизведение или передача настоящей книги в любом виде или любыми средствами без письменного разрешения издателя.

Эта книга предоставляется на условиях "как есть" и выражает взгляды и мнения автора. Взгляды, мнения и сведения, содержащиеся в этой книге, включая URL-адреса и другие ссылки на веб-сайты, могут изменяться без уведомления.

Некоторые приведенные в книге примеры служат только для иллюстрации и являются вымышленными. Все совпадения с реальными наименованиями, людьми и любыми другими предметами являются непреднамеренными и случайными.

Microsoft и товарные знаки, перечисленные на странице "Товарные знаки" на сайте <https://www.microsoft.com>, являются товарными знаками группы компаний Майкрософт.

Mac и macOS являются товарными знаками Apple Inc.

Логотип Docker с изображением кита является зарегистрированным товарным знаком Docker, Inc. Используется с разрешения.

Все другие наименования и логотипы являются собственностью своих законных владельцев.

## <a name="credits"></a>Благодарности

Авторы:

> [Кэм Сопер (Cam Soper)](https://twitter.com/camsoper)
>
> [Скотт Адди (Scott Addie)](https://twitter.com/scottaddie)
>
> [Колин Дембовски (Colin Dembovsky)](https://twitter.com/colindembovsky)

## <a name="welcome"></a>Приветствие

Руководство по жизненному циклу разработки Azure для .NET В этом руководстве предоставляются основные сведения по созданию жизненного цикла разработки в Azure с помощью инструментов и процессов .NET. После его прохождения вы сможете наиболее эффективно использовать цепочку инструментов DevOps.

## <a name="who-this-guide-is-for"></a>Для кого предназначено это руководство

Вы должны быть опытным разработчиком ASP.NET Core (уровень 200–300). Вам не нужно ничего знать об Azure, так как эти сведения есть во введении. Это руководство может также оказаться полезным для инженеров DevOps, которые преимущественно работают с операциями, а не занимаются разработкой.

Это руководство предназначено для разработчиков Windows. Linux и macOS также полностью поддерживаются в .NET Core. Чтобы адаптировать это руководство для Linux или macOS, смотрите сноски, в которых приводятся характерные отличия.

## <a name="what-this-guide-doesnt-cover"></a>Темы, которые выходят за рамки этого руководства

В этом руководстве приводятся рекомендации для разработчиков .NET по сквозному непрерывному развертыванию. Это не исчерпывающее руководство по Azure, и в нем не рассматриваются подробно API .NET для служб Azure. Основное внимание уделяется непрерывной интеграции, развертыванию, мониторингу и отладке. В конце руководства предлагаются рекомендации по дальнейшим действиям. В число предложений входят службы платформы Azure, полезные для разработчиков ASP.NET Core.

## <a name="whats-in-this-guide"></a>Содержание руководства

### <a name="tools-and-downloads"></a>[Инструменты и файлы для скачивания](xref:azure/devops/tools-and-downloads)

Вы узнаете, где получить инструменты, используемые в этом руководстве.

### <a name="deploy-to-app-service"></a>[Развертывание в службу приложений](xref:azure/devops/deploy-to-app-service)

Разные способы развертывания приложения ASP.NET Core в службе приложений Azure.

### <a name="continuous-integration-and-deployment-with-azure-devops"></a>[Непрерывная поставка и интеграция с помощью Azure DevOps](xref:azure/devops/cicd)

Создание решения сквозной непрерывной интеграции и развертывания для приложения ASP.NET Core с помощью GitHub, Azure DevOps Services и Azure.

### <a name="continuous-integration-and-deployment-with-github-actions"></a>[Непрерывная поставка и интеграция с помощью GitHub Actions](xref:azure/devops/github-actions)

Создайте комплексное решение непрерывной поставки и интеграции для своего приложения ASP.NET Core, использующее GitHub, GitHub Actions и Azure, а также функции CodeQL для проверки кода на качество и безопасность.

### <a name="monitor-and-debug"></a>[Мониторинг и отладка](xref:azure/devops/monitor)

Мониторинг, устранение неполадок и настройка приложения с помощью инструментов Azure.

### <a name="next-steps"></a>[Следующие шаги](xref:azure/devops/next-steps)

Другие способы изучения Azure для разработчиков ASP.NET Core.

## <a name="additional-introductory-reading"></a>Дополнительные справочные материалы

Если это ваш первый опыт работы с облачными вычислениями, в этой статье рассматриваются основы.

* [Что такое облачные вычисления?](https://azure.microsoft.com/overview/what-is-cloud-computing/)
* [Примеры облачных вычислений](https://azure.microsoft.com/overview/examples-of-cloud-computing/)
* [Что такое IaaS?](https://azure.microsoft.com/overview/what-is-iaas/)
* [Что такое PaaS?](https://azure.microsoft.com/overview/what-is-paas/)

>[!div class="step-by-step"]
>[Вперед](tools-and-downloads.md)
