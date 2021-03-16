---
description: 'Дополнительные сведения: ресурсы приложений для библиотек, предназначенных для нескольких платформ'
title: Ресурсы приложений для библиотек, предназначенных для нескольких платформ
ms.date: 07/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multiple platforms, resources for
- resources [.NET Framework]
- .NET Framework, resources when targeting multiple platforms
- resources, for multiple platforms
- targeting multiple platforms, resources for
ms.assetid: 72c76f0b-7255-4576-9261-3587f949669c
ms.openlocfilehash: c6d1a8d19c58174e4b08842c4965dfbe3389d1e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "102402275"
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a>Ресурсы приложений для библиотек, предназначенных для нескольких платформ

Чтобы доступ к ресурсам в библиотеках классов можно было получать из нескольких платформ, можно использовать тип проекта [Переносимая библиотека классов](portable-class-library.md) .NET Framework. Проект этого типа доступен в Visual Studio 2012 и нацелен на переносимое подмножество библиотеки классов .NET Framework. Использование переносимой библиотеки классов гарантирует, что доступ к библиотеке можно получить из классических приложений, приложений Silverlight, Windows Phone и приложений Магазина Windows 8.x.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 Проект переносимой библиотеки классов предоставляет приложению только очень ограниченное подмножество типов в пространстве имен <xref:System.Resources>, но позволяет использовать класс <xref:System.Resources.ResourceManager> для извлечения ресурсов. Однако при создании приложения с помощью Visual Studio необходимо использовать строго типизированную оболочку, созданную Visual Studio, а не класс <xref:System.Resources.ResourceManager> непосредственно.

 Для создания строго типизированной оболочки в Visual Studio присвойте параметру **Модификатор доступа** основного файла ресурсов в конструкторе ресурсов Visual Studio значение **Открытый**. При этом создастся файл [имя_файла_ресурсов].designer.cs или [имя_файла_ресурсов].designer.vb, содержащий строго типизированную оболочку ResourceManager. Подробнее об использовании строго типизированной оболочки ресурсов см. в подразделе "Создание класса ресурсов со строгой типизацией" раздела [Resgen.exe (генератор файлов ресурсов)](../../framework/tools/resgen-exe-resource-file-generator.md).

## <a name="resource-manager-in-the-portable-class-library"></a>Resource Manager в переносимой библиотеке классов

 В проекте переносимой библиотеки классов весь доступ к ресурсам обрабатывается классом <xref:System.Resources.ResourceManager>. Поскольку типы в пространстве имен <xref:System.Resources>, в частности <xref:System.Resources.ResourceReader> и <xref:System.Resources.ResourceSet>, недоступны из проекта переносимой библиотеки классов, их нельзя использовать для доступа к ресурсам.

 Проект переносимой библиотеки классов содержит четыре члена <xref:System.Resources.ResourceManager>, перечисленных в представленной ниже таблице. Эти конструкторы и методы позволяют создать экземпляр объекта <xref:System.Resources.ResourceManager> и извлечь строковые ресурсы.

|Член`ResourceManager`|Описание|
|------------------------------|-----------------|
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|Создает экземпляр <xref:System.Resources.ResourceManager> для доступа к именованному файлу ресурсов, найденному в заданной сборке.|
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|Создает экземпляр <xref:System.Resources.ResourceManager>, соответствующий указанному типу.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|Извлекает именованный ресурс для текущих языка и региональных параметров.|
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|Извлекает именованный ресурс, относящийся к указанным языку и региональным параметрам.|

 Исключение других членов <xref:System.Resources.ResourceManager> из переносимой библиотеки классов означает, что сериализованные объекты, нестроковые данные и изображения невозможно извлечь из файла ресурсов. Чтобы использовать ресурсы из переносимой библиотеки классов, необходимо хранить все данные объекта в строковом формате. Например, числовые значения можно сохранять в файле ресурсов, преобразуя в строки. Их также можно извлекать и затем преобразовывать обратно в числа с помощью метода `Parse` или `TryParse` числового типа данных. Изображения и другие двоичные данные можно преобразовать в строковое представление, вызвав метод <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType>, и восстановить их в массив байтов с помощью метода <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType>.

## <a name="the-portable-class-library-and-windows-store-apps"></a>Переносимые библиотеки классов и приложения для Магазина Windows

 В проектах переносимой библиотеки классов ресурсы хранятся в файлах с расширением RESX, которые затем компилируются в файлы с расширением RESOURCES и встраиваются в основную или вспомогательные сборки во время компиляции. Приложения Магазина Windows 8.x, с другой стороны, требуют, чтобы ресурсы хранились в файлах с расширением RESW, которые затем компилируются в единый файл индекса ресурсов пакета (PRI). Однако, несмотря на несовместимые форматы файлов, переносимая библиотека классов будет работать в приложениях Магазина Windows 8.x.

 Чтобы использовать библиотеку классов из приложения Магазина Windows 8.x, добавьте ссылку на него в проекте приложения для Магазина Windows. Visual Studio прозрачно извлечет ресурсы из сборки в файл RESW и использует его для создания файла PRI, из которого среда выполнения Windows может извлекать ресурсы. Во время выполнения среда выполнения Windows выполняет код в переносимой библиотеке классов, но извлекает ее ресурсы из файла PRI.

 Если проект переносимой библиотеки классов содержит локализованные ресурсы, то для их развертывания используется модель "звезда" так же, как и для библиотеки в настольном приложении. Для использования основного файла ресурсов и любых локализованных файлов ресурсов в приложении Магазина Windows 8.x следует добавить ссылку на основную сборку. Во время компиляции Visual Studio извлекает ресурсы из основного файла ресурсов и всех локализованных файлов ресурсов в отдельные файлы RESW. Затем Visual Studio компилирует файлы RESW в единый файл PRI, к которому среда выполнения Windows обращается во время выполнения.

<a name="NonLoc"></a>

## <a name="example-non-localized-portable-class-library"></a>Пример. Нелокализованная переносимая библиотека классов

 В следующем простом примере нелокализованная переносимая библиотека классов использует ресурсы для хранения имен столбцов и определения числа символов, которые следует зарезервировать для табличных данных. В этом примере используется файл с именем LibResources.resx для хранения строковых ресурсов, перечисленных в следующей таблице.

|Имя ресурса|Значение ресурса|
|-------------------|--------------------|
|Born|Birthdate|
|BornLength|12|
|Hired|Дата приема на работу|
|HiredLength|12|
|ID|ID|
|ID.Length|12|
|Имя|Имя|
|NameLength|25|
|Заголовок|Employee Database|

 В следующем примере кода определяется класс `UILibrary`, который использует оболочку Resource Manager с именем `resources`, созданную Visual Studio при изменении значения параметра **Модификатор доступа** для файла на **Открытый**. Класс UILibrary анализирует строковые данные по мере необходимости. . Обратите внимание, что класс находится в пространстве имен `MyCompany.Employees`.

 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]

 В следующем примере кода показано, как к классу `UILibrary` и его ресурсам можно обращаться из консольного приложения. Для этого требуется добавить в проект консольного приложения ссылку на файл UILibrary.dll.

 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]

 В следующем примере кода показано, как к классу `UILibrary` и его ресурсам можно обращаться из приложения Магазина Windows 8.x. Для этого требуется добавить в проект приложения для Магазина Windows ссылку на файл UILibrary.dll.

 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]

## <a name="example-localized-portable-class-library"></a>Пример. Локализованная переносимая библиотека классов

 Следующий пример локализованной переносимой библиотеки классов содержит ресурсы французского (Франция) и английского (США) языков и региональных параметров. Английский (США) язык и региональные параметры приняты в приложении по умолчанию. Эти ресурсы показаны в таблице в [предыдущем разделе](app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc). Файл ресурсов для французского (Франция) языка и региональных параметров называется LibResources.fr-FR.resx и состоит из строковых ресурсов, перечисленных в представленной ниже таблице. Исходный код для класса `UILibrary` такой же, как и в предыдущем разделе.

|Имя ресурса|Значение ресурса|
|-------------------|--------------------|
|Born|Date de naissance|
|BornLength|20|
|Hired|Date embauché|
|HiredLength|16|
|ID|ID|
|Имя|Nom|
|Заголовок|Base de données des employés|

 В следующем примере кода показано, как к классу `UILibrary` и его ресурсам можно обращаться из консольного приложения. Для этого требуется добавить в проект консольного приложения ссылку на файл UILibrary.dll.

 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]

 В следующем примере кода показано, как к классу `UILibrary` и его ресурсам можно обращаться из приложения Магазина Windows 8.x. Для этого требуется добавить в проект приложения для Магазина Windows ссылку на файл UILibrary.dll. В коде используется статическое свойство `ApplicationLanguages.PrimaryLanguageOverride`, чтобы в качестве предпочтительного языка приложения указать французский язык.

 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a>См. также

- <xref:System.Resources.ResourceManager>
- [Ресурсы в приложениях для настольных систем](../../framework/resources/index.md)
- [Упаковка и развертывание ресурсов](../../framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
