---
title: Определение установленных версий платформы .NET Framework
description: Используйте код, regedit.exe или PowerShell, чтобы определить, какие версии .NET Framework установлены на компьютере, запросив реестр Windows.
ms.date: 12/04/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining installed versions
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: 817e7ad7b10e11675fb055b1243a8584196cc2b5
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102258628"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Практическое руководство. Определение установленных версий платформы .NET Framework

На компьютере можно [установить](../install/index.md) и запустить несколько версий платформы .NET Framework. При разработке или развертывании приложения могут потребоваться сведения о том, какие версии .NET Framework установлены на компьютере пользователя. Реестр содержит список версий .NET Framework, установленных на компьютере.

> [!NOTE]
> Эта статья относится к .NET Framework. Чтобы определить, какие пакеты SDK и среды выполнения .NET Core и .NET 5+ установлены, см. раздел [Как проверить, что .NET уже установлен](../../core/install/how-to-detect-installed-versions.md).

Платформа .NET Framework состоит из двух основных компонентов, версии которым присваиваются отдельно:

- набор сборок, которые являются коллекциями типов и ресурсов, обеспечивающих функции приложений (.NET Framework и сборкам назначается один номер версии); Например, версии .NET Framework включают в себя 4.5, 4.6.1 и 4.7.2.

- среда CLR, которая выполняет код приложения и управляет им. Одна версия среды CLR обычно поддерживает несколько версий .NET Framework. Например, CLR версии 4.0.30319.*xxxxx*, где *xxxxx* меньше 42000, поддерживает .NET Framework версий с 4 по 4.5.2. Версия CLR не менее 4.0.30319.42000 поддерживает версии .NET Framework начиная с .NET Framework 4.6.

Средства, поддерживаемые сообществом, помогают определить, какие версии .NET Framework установлены:

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  Программа командной строки .NET Framework 2.0.

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  Модуль PowerShell 2.0.

Сведения об определении установленных обновлений для каждой версии платформы .NET Framework см. в статье [Практическое руководство. Определение установленных обновлений платформы .NET Framework](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="determine-which-net-implementation-and-version-an-app-is-running-on"></a>Определение реализации и версии .NET, в которой работает приложение

Для запроса реализации и версии .NET, в которой работает ваше приложение, можно использовать свойство <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>. Если приложение работает в .NET Framework, выходные данные будут выглядеть примерно так:

```output
.NET Framework 4.8.4250.0
```

Если же приложение работает в .NET Core или .NET 5+, выходные данные будут выглядеть следующим образом:

```output
.NET Core 3.1.9
.NET 5.0.0
```

## <a name="detect-net-framework-45-and-later-versions"></a>Обнаружение .NET Framework 4.5 и более поздних версий

Версия .NET Framework (4.5 и более поздние), установленная на компьютере, указана в реестре в **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**. Если отсутствует подраздел **Full**, то .NET Framework 4.5 или более поздней версии не установлен.

> [!NOTE]
> Подраздел **NET Framework Setup** в пути реестра *не* начинается с точки.

Значение **Release** REG_DWORD в реестре представляет установленную версию .NET Framework.

<a name="version_table"></a>

| Версия платформы .NET Framework | Значение **Release** |
| ---------------------- | -------------------------- |
| .NET Framework 4,5     | Все версии операционной системы Windows: 378389 |
| .NET Framework 4.5.1   | Windows 8.1 и Windows Server 2012 R2: 378675<br />Все другие версии операционной системы Windows: 378758 |
| .NET Framework 4.5.2   | Все версии операционной системы Windows: 379893 |
| .NET Framework 4.6     | Windows 10: 393295<br />Все другие версии операционной системы Windows: 393297 |
| .NET Framework 4.6.1   | Windows 10 с ноябрьским обновлением: 394254<br />Все остальные версии операционной системы Windows (включая Windows 10): 394271 |
| .NET Framework 4.6.2   | В юбилейном обновлении Windows 10 и Windows Server 2016: 394802<br />Все остальные версии операционной системы Windows (включая другие операционные системы Windows 10): 394806 |
| .NET Framework 4.7     | Windows 10 Creators Update: 460798<br />Все остальные версии операционной системы Windows (включая другие операционные системы Windows 10): 460805 |
| .NET Framework 4.7.1   | Windows 10 Fall Creators Update и Windows Server версии 1709: 461308<br/>Все остальные версии операционной системы Windows (включая другие операционные системы Windows 10): 461310 |
| .NET Framework 4.7.2   | Windows 10 за апрель 2018 г. Update и Windows Server версии 1803: 461808<br/>Все остальные операционные системы, кроме Windows 10 с обновлением за апрель 2018 г. и Windows Server версии 1803: 461814 |
| .NET Framework 4.8     | Обновление Windows 10 за май 2019 года и обновление Windows 10 за ноябрь 2019 года: 528040<br/>Обновление Windows 10 за май 2020 года и обновление Windows 10 за октябрь 2020 года: 528372<br/>Все остальные версии операционной системы Windows (включая другие операционные системы Windows 10): 528049 |

### <a name="minimum-version"></a>Минимальная версия

Чтобы определить, присутствует ли *минимальная* версия .NET Framework, проверьте значение **Release** REG_DWORD, которое больше или равно соответствующему значению, указанному в следующей таблице. Например, если приложение работает в .NET Framework 4.8 или более поздней версии, проверьте, является ли значение REG_DWORD **Release** *большим или равным* 528040.

| Версия платформы .NET Framework | Минимальное значение |
| ---------------------- | ------------- |
| .NET Framework 4,5     | 378389 |
| .NET Framework 4.5.1   | 378675 |
| .NET Framework 4.5.2   | 379893 |
| .NET Framework 4.6     | 393295 |
| .NET Framework 4.6.1   | 394254 |
| .NET Framework 4.6.2   | 394802 |
| .NET Framework 4.7     | 460798 |
| .NET Framework 4.7.1   | 461308 |
| .NET Framework 4.7.2   | 461808 |
| .NET Framework 4.8     | 528040 |

### <a name="use-registry-editor"></a>Использование редактора реестра

1. В меню **Пуск** выберите **Выполнить**, введите *regedit* и нажмите кнопку **ОК**.

   (Для запуска программы regedit необходимы учетные данные администратора.)

1. В редакторе реестра откройте следующий подраздел: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**. Если подраздел **Full** отсутствует, платформа .NET Framework 4.5 или более поздней версии не установлена.

1. Проверьте значение REG_DWORD с именем **Release**. Если оно имеется, платформа .NET Framework 4.5 или более поздней версии установлена. Это значение соответствует определенной версии .NET Framework. Например, на приведенном ниже рисунке значение параметра **Release** равно 528040, что является разделом выпуска для .NET Framework 4.8.

   ![Запись реестра для .NET Framework 4.5](./media/clr-installdir.png )

### <a name="use-powershell-to-check-for-a-minimum-version"></a>Использование PowerShell для проверки минимальной версии

Используйте команды PowerShell для проверки значения параметра **Release** в подразделе **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.

В приведенных ниже примерах значение **Release** проверяется с целью определить, установлена ли версия 4.6.2 или более поздняя версия .NET Framework. Код возвращает значение `True`, если одна из таких версий установлена, и `False` в противном случае.

```powershell
(Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a>Отправка запросов в реестр с помощью кода

01. Используйте методы <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> и <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> для доступа к подразделу **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** в реестре Windows.

    > [!IMPORTANT]
    > Если вы используете 32-разрядное приложение в 64-разрядной версии Windows, пути реестра будут отличаться от указанных ранее. 64-разрядный реестр доступен в подразделе **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** . Например, подразделом реестра для .NET Framework 4.5 является **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.

01. Проверьте значение REG_DWORD **Release**, чтобы определить установленную версию. Для обеспечения совместимости с последующими версиями значение должно быть больше или равно значению, указанному в [таблице версий .NET Framework](#version_table).

В следующем примере проверяется значение **Release** в реестре для поиска установленных версий .NET Framework 4.5–4.8.

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="2":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="2":::

Этот пример выводит данные, подобные следующим:

```output
.NET Framework Version: 4.6.1
```

В этом примере применяются рекомендации для проверки версии:

- Проверяется, имеет ли параметр **Release** значение, *большее или равное* значению известных разделов выпуска.
- Проверка выполняется с самой последней до самой ранней версии.

## <a name="detect-net-framework-10-through-40"></a>Обнаружение .NET Framework с 1.0 по 4.0

Каждая версия .NET Framework с 1.1 по 4.0 указана в виде подраздела в **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**. В следующей таблице перечислены пути к каждой версии .NET Framework. Для большинства версий существует значение REG_DWORD **Install**, равное `1`, чтобы указать, что эта версия установлена. В этих подразделах также имеется значение REG_SZ **Version**, содержащее строку версии.

> [!NOTE]
> Подраздел **NET Framework Setup** в пути реестра *не* начинается с точки.

| Версия платформы  | Подраздел реестра | Значение |
| ------------------ | --------------- | ----- |
| 1.0                | **HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**     | REG_SZ **Install** равно `1` |
| 1.1                | **HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**   | REG_DWORD **Install** равно `1` |
| 2.0                | **HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**  | REG_DWORD **Install** равно `1` |
| 3.0                | **HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup** | Значение REG_DWORD **InstallSuccess** равно `1` |
| 3.5                | **HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**        | REG_DWORD **Install** равно `1` |
| Клиентский профиль 4.0 | **HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**  | REG_DWORD **Install** равно `1` |
| Полный профиль 4.0   | **HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**    | REG_DWORD **Install** равно `1` |

> [!IMPORTANT]
> Если вы используете 32-разрядное приложение в 64-разрядной версии Windows, пути реестра будут отличаться от указанных ранее. 64-разрядный реестр доступен в подразделе **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** . Например, подразделом реестра для .NET Framework 3.5 является **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.

Обратите внимание, что путь реестра к подразделу .NET Framework 1.0 отличается от остальных.

### <a name="use-registry-editor-older-framework-versions"></a>Использование редактора реестра (более ранние версии платформы)

01. В меню **Пуск** выберите **Выполнить**, введите *regedit* и нажмите кнопку **ОК**.

    Для запуска программы regedit необходимы учетные данные администратора.

01. Откройте подраздел, соответствующий версии, которую необходимо проверить. Используйте таблицу в разделе [Обнаружение .NET Framework с 1.0 по 4.0](#detect-net-framework-10-through-40).

    На приведенном ниже рисунке показан подраздел для версии .NET Framework 3.5 вместе со значением **Version**.

    ![Запись реестра для .NET Framework 3.5.](./media/net-4-and-earlier.png "NET Framework 3.5 и предыдущие версии")

### <a name="query-the-registry-using-code-older-framework-versions"></a>Запрос реестра с помощью кода (более ранние версии платформы)

Используйте класс <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> для доступа к подразделу **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** в реестре Windows.

> [!IMPORTANT]
> Если вы используете 32-разрядное приложение в 64-разрядной версии Windows, пути реестра будут отличаться от указанных ранее. 64-разрядный реестр доступен в подразделе **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** . Например, подразделом реестра для .NET Framework 3.5 является **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.

В следующем примере ищутся установленные версии .NET Framework 1–4:

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="1":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="1":::

В этом примере отобразятся выходные данные, аналогичные следующим:

```output
v2.0.50727  2.0.50727.4927  SP2
v3.0  3.0.30729.4926  SP2
v3.5  3.5.30729.4926  SP1
v4.0
  Client  4.0.0.0
```

## <a name="find-clr-versions"></a>Поиск версий CLR

.NET Framework CLR, установленный с .NET Framework, имеет отдельную версию. Есть два способа определить версию среды выполнения .NET Framework CLR:

- **Инструмент Clrver.exe**

  Для определения версий среды CLR, установленных на компьютере, можно использовать [средство CLR Version (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md). Откройте [оболочку командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell) и введите `clrver`.

  Пример результатов выполнения:

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- **Класс `Environment`**

  > [!IMPORTANT]
  > Для .NET Framework 4.5 и более поздних версий не следует использовать свойство <xref:System.Environment.Version%2A?displayProperty=nameWithType> для определения версии среды CLR. Вместо этого выполните запрос к реестру, как описано в разделе [Обнаружение .NET Framework 4.5 и более поздних версий](#detect-net-framework-45-and-later-versions).

  1. Выполните запрос к свойству <xref:System.Environment.Version?displayProperty=nameWithType>, чтобы получить объект <xref:System.Version>.

     Возвращенный объект `System.Version` указывает версию среды выполнения, в которой в настоящее время выполняется код. Он не содержит версий сборок или других версий среды выполнения, которые установлены на компьютере.

     Для платформы .NET Framework версий 4, 4.5, 4.5.1 и 4.5.2 возвращаемый объект <xref:System.Version> имеет строковое представление 4.0.30319.*xxxxx*, где *xxxxx* меньше 42000. Для .NET Framework 4.6 и более поздних версий оно имеет форму 4.0.30319.42000.

  1. Получив объект **Version**, выполните к нему запрос:

     - Чтобы получить идентификатор основного выпуска (например, *4* в случае версии 4.0), используйте свойство <xref:System.Version.Major%2A?displayProperty=nameWithType>.

     - Чтобы получить идентификатор дополнительной версии (например, *0* в случае версии 4.0), используйте свойство <xref:System.Version.Minor%2A?displayProperty=nameWithType>.

     - Чтобы получить всю строку версии (например, *4.0.30319.18010*), используйте метод <xref:System.Version.ToString%2A?displayProperty=nameWithType>. Он возвращает одно значение, соответствующее версии среды выполнения, в которой выполняется код. Он не возвращает версий сборок или других версий среды выполнения, которые установлены на компьютере.

  В следующем примере свойство <xref:System.Environment.Version%2A?displayProperty=nameWithType> используется для получения сведений о версии среды CLR:

  ```csharp
  Console.WriteLine($"Version: {Environment.Version}");
  ```

  ```vb
  Console.WriteLine($"Version: {Environment.Version}")
  ```

  В этом примере отобразятся выходные данные, аналогичные следующим:

  ```output
  Version: 4.0.30319.18010
  ```

## <a name="see-also"></a>См. также

- [Практическое руководство. Определение установленных обновлений платформы .NET Framework](how-to-determine-which-net-framework-updates-are-installed.md)
- [Установка .NET Framework для разработчиков](../install/guide-for-developers.md)
- [Версии и зависимости платформы .NET Framework](versions-and-dependencies.md)
