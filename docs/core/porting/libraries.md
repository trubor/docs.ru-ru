---
title: Перенос библиотек в .NET
description: Сведения о том, как перенести проекты библиотек из .NET Framework в .NET.
author: cartermp
ms.date: 03/04/2021
ms.openlocfilehash: 19ee6ab15597b3c99b39b47ad55ac72a3f9d681a
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873683"
---
# <a name="port-net-framework-libraries-to-net"></a>Перенос библиотек .NET Framework в .NET

Узнайте, как перенести код библиотек .NET Framework в .NET, чтобы выполнять его на разных платформах и расширить диапазон использующих его приложений.

## <a name="prerequisites"></a>Предварительные требования

В этой статье предполагается, что вы:

- используете Visual Studio 2019 или более поздней версии:
  - .NET 5 требует использования среды Visual Studio 2019 (16.9) или более поздней версии.
  - .NET Core 3.1 требует использования среды Visual Studio 2019 (16.4) или более поздней версии.
- ознакомлены с [рекомендуемым процессом переноса](index.md);
- устранили все проблемы с [зависимостями сторонних разработчиков](third-party-deps.md).

Ознакомьтесь с содержимым следующих статей:

- [.NET Standard.](../../standard/net-standard.md)\
В этой статье рассматривается официальная спецификация API-интерфейсов .NET, которые должны быть доступны во всех реализациях .NET.

- [Разработка библиотек с помощью .NET CLI.](../tutorials/libraries.md)\
В этой статье описано, как создавать библиотеки с помощью .NET CLI.

- [Пакеты SDK для проектов .NET.](../project-sdk/overview.md)\
В этой статье описывается формат файла проекта в стиле пакета SDK.

- [Анализ зависимостей для переноса кода из .NET Framework в .NET.](third-party-deps.md)\
В этой статье рассматривается переносимость зависимостей сторонних разработчиков и объясняется, что делать, если зависимость пакета NuGet не работает в .NET.

## <a name="retarget-to-net-framework-472"></a>Перенацелить на платформу .NET Framework 4.7.2

Если ваш код не предназначен для .NET Framework 4.7.2, рекомендуем изменить его целевую платформу на эту версию. Это обеспечит доступность альтернативных API-интерфейсов последних версий в случаях, когда .NET Standard не поддерживает существующие API-интерфейсы.

Для каждого проекта в Visual Studio, который нужно перенести, выполните указанные ниже действия:

01. Щелкните проект правой кнопкой мыши и выберите пункт **Свойства**.
01. В раскрывающемся списке **Требуемая версия .NET Framework** выберите значение **.NET Framework 4.7.2**.
01. Перекомпилируйте проект.

Так как ваши проекты теперь предназначены для .NET Framework 4.7.2, используйте эту версию .NET Framework в качестве основы для переноса кода.

## <a name="determine-portability"></a>Определение переносимости

Следующий шаг — запуск анализатора переносимости API (ApiPort) для создания отчета о переносимости и его анализа.

Для работы с .NET вам потребуются навыки использования [ApiPort](../../standard/analyzers/portability-analyzer.md) и создания отчетов о переносимости. Процедура зависит от ваших потребностей и личных предпочтений. В следующих разделах подробно описаны несколько различных подходов. Вы можете использовать их в различных сочетаниях в зависимости от структуры кода.

### <a name="deal-primarily-with-the-compiler"></a>Работа в первую очередь с компилятором

Такой подход оптимальный для небольших проектов или проектов, в которых используется небольшое количество интерфейсов API .NET Framework. Этот подход прост:

01. При необходимости запустите средство ApiPort для проекта. Если вы запустили ApiPort, проверьте, нет ли проблем с отчетом, которые необходимо устранить.
01. Скопируйте весь код в новый проект .NET.
01. Обращаясь к отчету о переносимости (если он создан), устраните ошибки компилятора, пока проект не будет полностью компилироваться.

Несмотря на свою неструктурированность, такой ориентированный на код подход часто устраняет проблемы. Этот подход лучше применять к проектам, содержащим только модели данных.

### <a name="stay-on-the-net-framework-until-portability-issues-are-resolved"></a>Использование .NET Framework вплоть до устранения проблем переносимости

Такой подход может быть оптимальным, если вам нужен код, который компилируется на протяжении всего процесса. Он выглядит следующим образом.

01. Запустите средство ApiPort для проекта.
01. Устраните проблемы, используя другие API-интерфейсы, являющиеся переносимыми.
01. Запомните области, в которых невозможно использовать прямые альтернативы.
01. Повторяйте предыдущие шаги для всех переносимых проектов, пока не удостоверитесь в том, что каждый из них готов к копированию в новый проект .NET.
01. Скопируйте код в новый проект .NET.
01. Устраните все проблемы, для решения которых нет прямых альтернатив.

Такой тщательный подход более систематизирован, чем простое устранение ошибок компилятора. Но он по-прежнему в некоторой степени ориентирован на код. При этом код является компилируемым на всех этапах. Есть множество способов устранения некоторых проблем, которые не удалось решить, просто использовав другой API-интерфейс. Для некоторых проектов может оказаться необходимым разработать более детальный план. Эта задача рассматривается в следующем подходе.

### <a name="develop-a-comprehensive-plan-of-attack"></a>Разработка детального плана атак

Это, возможно, оптимальный подход для более крупных и сложных проектов, при реализации которых для поддержки .NET может потребоваться реструктурировать код или полностью переписать некоторые его части. Он выглядит следующим образом.

01. Запустите средство ApiPort для проекта.
01. Определите, в каких случаях используется каждый непереносимый тип и как он влияет на переносимость в целом.

    - Изучите особенности этих типов. Их немного, но они часто используются? Или их много, но используются они нечасто? Ограничена ли область их использования или они распределены по всему коду?
    - Можно ли легко изолировать непереносимый код для более эффективной работы с ним?
    - Требуется ли рефакторинг кода?
    - Есть ли для непереносимых типов альтернативные интерфейсы API, выполняющие те же задачи? Например, если используется класс <xref:System.Net.WebClient>, вместо него используйте класс <xref:System.Net.Http.HttpClient>.
    - Есть ли другие переносимые API-интерфейсы, которые можно использовать для выполнения задачи, даже если это не совсем равноценная замена? Например, если для анализа XML вы используете класс <xref:System.Xml.Schema.XmlSchema>, но обнаружение схемы XML не требуется, вы можете использовать API <xref:System.Xml.Linq> и выполнять анализ самостоятельно без API.

01. Если у вас есть сборки, которые трудно перенести, возможно, пока стоит оставить их в .NET Framework? Следует учесть ряд факторов:

    - В библиотеке могут присутствовать функции, которые несовместимы с .NET, так как они слишком тесно связаны с возможностями .NET Framework или Windows. Возможно, стоит на время отказаться от этих функций и выпустить временную версию библиотеки для .NET с ограниченной функциональностью, пока не будет достаточно ресурсов для переноса этих функций?
    - Поможет ли рефакторинг?

01. Целесообразно ли написание собственной реализации недоступного интерфейса API .NET Framework?

    Вы можете рассмотреть возможность копирования, изменения и использования кода из [библиотеки эталонного исходного кода .NET Framework](https://github.com/Microsoft/referencesource). Эталонный исходный код распространяется по [лицензии MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), поэтому вы можете достаточно свободно использовать его в качестве источника при создании собственного кода. Только не забывайте соответствующим образом упоминать корпорацию Майкрософт в своем коде.

01. При необходимости повторите этот процесс для различных проектов.

Этап анализа может занять некоторое время в зависимости от размера базы кода. Потратив некоторое время на этот этап, чтобы тщательно проанализировать требуемый объем изменений и разработать план, вы сможете сэкономить время в долгосрочной перспективе, особенно если у вас сложная база кода.

План может предусматривать внесение существенных изменений в базу кода с ориентацией на .NET Framework 4.7.2, что делает этот подход более структурированным по сравнению с предыдущим. Способ реализации плана зависит от базы кода.

### <a name="mixed-approach"></a>Смешанный подход

В каждом конкретном случае, скорее всего, потребуется использовать описанные выше подходы в разных сочетаниях. Выбирайте оптимальные варианты для себя и вашей базы кода.

## <a name="port-your-tests"></a>Перенос тестов

Чтобы гарантировать правильную работу кода после его переноса в .NET, лучше всего тестировать код в процессе переноса. Для этого потребуется использовать платформу тестирования, которая выполняет сборку и запуск тестов для .NET. В настоящее время имеются три варианта:

- [xUnit](https://xunit.net/)
  - [Начало работы](https://xunit.net/docs/getting-started/netcore/cmdline)
  - [Средство для преобразования проекта MSTest в xUnit](https://github.com/dotnet/codeformatter/tree/main/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  - [Начало работы](https://github.com/nunit/docs/wiki/Installation)
  - [Запись блога о миграции из MSTest в NUnit](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](/visualstudio/test/unit-test-basics)

## <a name="recommended-approach"></a>Рекомендуемый подход

Процедура переноса во многом зависит от того, как структурирован ваш код .NET Framework. Перенос кода лучше всего начинать с *основных* объектов библиотеки, которые являются базовыми компонентами кода. Это могут быть модели данных или какие-либо иные базовые классы и методы, используемые всеми остальными компонентами прямо или косвенно.

01. Перенесите тестовый проект для тестирования того уровня библиотеки, который вы переносите на данном этапе.
01. Скопируйте основные объекты библиотеки в новый проект .NET и выберите версию .NET Standard, которая должна поддерживаться.
01. Внесите изменения, необходимые для компиляции кода. Как правило, для этого требуется добавить зависимости пакетов NuGet в файл *CSPROJ*.
01. Проведите тесты и внесите необходимые исправления.
01. Выберите следующий уровень кода для переноса и повторите предыдущие шаги.

Двигаясь от базовых объектов библиотеки к более высоким уровням и тестируя каждый из них требуемым образом, вы обеспечиваете систематичность переноса и изоляцию проблем, относящихся к отдельным уровням кода.

## <a name="next-steps"></a>Следующие шаги

>[!div class="nextstepaction"]
>[Организация проектов для .NET](project-structure.md)
