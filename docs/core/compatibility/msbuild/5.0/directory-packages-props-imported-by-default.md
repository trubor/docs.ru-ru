---
title: Критическое изменение. Файлы Directory.Packages.props импортируются по умолчанию
description: Узнайте о критическом изменении в .NET 5, где файлы PROPS NuGet автоматически импортируют файл с именем Directory.Packages.props, если он находится в папке проекта.
ms.date: 09/17/2020
ms.openlocfilehash: a031d9b2bd832be06dedb20495c24075d1239b02
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256586"
---
# <a name="directorypackagesprops-files-is-imported-by-default"></a>Файлы Directory.Packages.props импортируются по умолчанию

Файлы *.props* NuGet автоматически импортируют файл с именем *Directory.Packages.props*, если он находится в папке проекта или любом из ее предков.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET в файле проекта у вас мог быть файл с именем *Directory.Packages.props*, который автоматически не импортировался файлом *.props* NuGet во время сборки.

Начиная с .NET 5 такой файл автоматически *импортируется*, если он существует в папке проекта или любом из ее предков. Если в папке проекта есть файл с таким именем, эта операция автоматического импорта может изменить поведение сборки. Например, файл будет импортирован, но не импортировался ранее, или порядок, в котором он импортируется, может измениться в случае его намеренного импорта.

## <a name="reason-for-change"></a>Причина изменения

Это изменение было внесено для поддержки [централизованного управления версиями пакетов](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) для NuGet.

## <a name="recommended-action"></a>Рекомендованное действие

Переименуйте существующий файл *Directory.Packages.props*, если он не должен импортироваться автоматически.

## <a name="affected-apis"></a>Затронутые API

Н/Д

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
