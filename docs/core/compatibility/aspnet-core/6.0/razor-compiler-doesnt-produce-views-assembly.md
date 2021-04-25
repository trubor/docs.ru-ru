---
title: 'Критическое изменение. Razor: теперь компилятор создает одну сборку'
description: Сведения о критическом изменении в ASP.NET Core 6.0. Теперь компилятор Razor больше не использует двухэтапный процесс компиляции для создания двух отдельных сборок.
no-loc:
- Razor
ms.date: 04/08/2021
ms.openlocfilehash: 8b6817563c4670aebfe681d5f24c8e309d2500ad
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299282"
---
# <a name="razor-compiler-no-longer-produces-a-views-assembly"></a>Razor: компилятор больше не создает сборку Views

Компилятор Razor больше не создает отдельный файл *Views.dll*, содержащий представления CSHTML, определенные в приложении.

## <a name="version-introduced"></a>Представленная версия

ASP.NET Core 6.0 (предварительная версия 3)

## <a name="old-behavior"></a>Старое поведение

В предыдущих версиях компилятор Razor использует двухэтапный процесс компиляции, создающий два файла:

- главная сборка *AppName.dll*, которая содержит типы приложений;
- сборка *AppName.Views.dll*, которая содержит созданные представления, определенные в приложении. Созданные представления относятся к типу `public` и принадлежат пространству имен `AspNetCore`.

## <a name="new-behavior"></a>Новое поведение

Типы представлений и приложений включены в одну сборку *AppName.dll*. Типы представлений по умолчанию имеют модификаторы доступа `internal` и `sealed` и включены в пространство имен `AspNetCoreGeneratedDocument`.

## <a name="reason-for-change"></a>Причина изменения

Отказ от двухэтапного процесса компиляции:

* улучшает сборку приложений, использующих представления Razor;
* позволяет использовать представления Razor в функциях горячей перезагрузки Visual Studio.

## <a name="recommended-action"></a>Рекомендованное действие

Отсутствует.

## <a name="affected-apis"></a>Затронутые API

Отсутствует.

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
