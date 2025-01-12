---
title: Миграция Windows 10
description: Углубитесь в рассмотрение таких функций Windows 10, как упаковка и XAML Islands.
ms.date: 12/29/2020
ms.openlocfilehash: 139a8f2354803dafeb0178b4dbfb57a95c4ddb34
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "98615949"
---
# <a name="windows-10-migration"></a>Миграция Windows 10

Рассмотрим следующую ситуацию: у вас есть рабочее настольное приложение, разработанное в дни Windows 7. Он использует технологию WPF, которая была доступной в тот момент, и работает нормально, но у него устарели пользовательский интерфейс и поведение при запуске в Windows 10. Это примерно как когда вы смотрите футуристический фильм, вроде "Матрицы", и видите Нео с телефоном Nokia 8110. Фильм и спустя 20 лет смотрится неплохо, но Нео не помешало бы использовать устройство поновее.

С выпуском Windows 10 корпорация Майкрософт представила множество нововведений для поддержки таких сценариев, как планшеты и сенсорные устройства, и обеспечения оптимального взаимодействия для пользователей операционной системы Майкрософт. Например, вы можете:

- Войдите с помощью Windows Hello, используя свое лицо.
- Используйте перо, чтобы рисовать или вводить текст, который автоматически распознается и преобразуется в цифровую форму.
- Запускайте локально настроенные модели AI, созданные в облаке, с помощью WinML.

Все эти функции предлагаются разработчикам Windows через библиотеки среды выполнения Windows (WinRT). Вы можете пользоваться этими функциями в существующих классических приложениях, поскольку библиотеки также доступны как для платформы .NET Framework, так и для .NET. Вы даже можете модернизировать пользовательский интерфейс, используя XAML Islands, а также приводя визуальные элементы и поведение приложений в соответствии со временем.

Важно отметить, что нет необходимости отказываться от технологии .NET Framework, чтобы следовать этому пути модернизации. Вы можете спокойно остаться на этой платформе, чтобы пользоваться всеми преимуществами Windows 10, нет необходимости переходить на .NET. Таким образом, вы получаете как большие возможности, так и гибкость при выборе пути модернизации.

## <a name="winrt-apis"></a>API WinRT

Интерфейсы API WinRT представляют собой объектно-ориентированные и хорошо структурированные прикладные программные интерфейсы (API), предоставляющие разработчикам Windows 10 доступ ко всему, что предлагает операционная система. Через API-интерфейсы WinRT можно интегрировать такие функции, как push-уведомления, API-интерфейсы устройств, Microsoft Ink и WinML, среди прочих настольных приложений.

Как правило, API-интерфейсы WinRT можно вызывать из классического приложения для настольных систем. Тем не менее две основные области представляют исключение из этого правила:

* API, для которых требуется удостоверение пакета.
* API, для которых требуется визуализация, например XAML или Композиция.

### <a name="universal-windows-platform-uwp-packages"></a>Пакеты универсальной платформы Windows (UWP)

#### <a name="application-package-identity"></a>Удостоверение пакета приложения

Приложения UWP имеют систему развертывания, в которой операционная система управляет установкой и удалением приложений. Для этого требуется декларативная установка, а это означает, что во время установки не выполняется пользовательский код. Вместо этого все, что приложение хочет интегрировать с системой, например протоколы, типы файлов и расширения, объявляется в манифесте приложения. Во время развертывания конвейер развертывания настраивает эти точки интеграции. Единственный способ, которым операционная система может управлять всеми этими функциями и контролировать их, заключается в том, что каждый "пакет" имеет удостоверение, уникальный идентификатор приложения.

Некоторые API-интерфейсы WinRT нуждаются в этом удостоверении пакета, чтобы работать должным образом. Однако классические настольные приложения, такие как собственные приложения C++ или .NET, используют различные системы развертывания, для которых не требуется удостоверение пакета. Если вы хотите использовать эти API-интерфейсы WinRT в настольном приложении, необходимо предоставить им удостоверение пакета.

Один из способов продолжить — создать дополнительный проект упаковки. Внутри проекта упаковки укажите исходный проект исходного кода и укажите сведения об удостоверении, которые необходимо предоставить. Если вы устанавливаете пакет и запускаете установленное приложение, оно автоматически получает идентификацию, позволяющую коду вызывать все API-интерфейсы WinRT, для которых требуется удостоверение.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10">
    <Identity Name="YOUR-APP-GUID "
              Publisher="CN=YOUR COMPANY"
              Version="1.x.x.x" />
</Package>
```

Вы можете проверить, какие API требуют удостоверения упакованного приложения, посмотрев, помечен ли тип, содержащий API, атрибутом [DualApiPartition](xref:Windows.Foundation.Metadata.DualApiPartitionAttribute). Если это так, его можно вызвать из неупакованного традиционного настольного приложения. В противном случае вы должны преобразовать классическое настольное приложение в UWP с помощью проекта упаковки.

<https://docs.microsoft.com/windows/desktop/apiindex/uwp-apis-callable-from-a-classic-desktop-app>

#### <a name="benefits-of-packaging"></a>Преимущества упаковки

Помимо доступа к этим API, вы получаете дополнительные преимущества, создавая пакет приложения Windows для настольного приложения, в том числе:

* **Упрощенное развертывание**. Приложения очень удобны в развертывании, гарантируя, что пользователи могут уверенно устанавливать приложение и обновлять его. Если пользователь решает удалить приложение, оно удаляется полностью и без следа, что позволяет предотвратить проблему замусоривания Windows.

* **Автоматическое обновление и лицензирование**. Приложение может пользоваться встроенными средствами лицензирования и автоматического обновления Microsoft Store. Автоматическое обновление — очень надежный и эффективный механизм, поскольку загружаются только измененные части файлов.

* **Увеличение аудитории и упрощение монетизации**. Возможно это не ваш случай, но если вы решите распространить свое приложение с помощью Microsoft Store, вы сможете представить его миллионам пользователей Windows 10.

* **Добавление возможностей UWP**. Вы можете добавить функции UWP в пакет приложения в удобном для вас темпе.

#### <a name="prepare-for-packaging"></a>Подготовка к упаковке

Прежде чем приступить к упаковке приложения для настольных систем, необходимо разобраться с некоторыми моментами, прежде чем начинать процесс. Приложение должно учитывать все правила и политики Microsoft Store и работать в модели приложений UWP. Например, оно должно работать на платформе .NET Framework 4.6.2 или более поздней версии и записывать в куст реестра `HKEY_CURRENT_USER`, а папки AppData будут виртуализированы в локальное расположение приложения, определяемое пользователем.

Целью разработки упаковки является отделение состояния приложения от состояния системы, при сохранении совместимости с другими приложениями. Windows 10 достигает этой цели, помещая приложение в пакет UWP. Она обнаруживает и перенаправляет некоторые изменения в файловой системе и реестре во время выполнения, чтобы выполнить обещание надежных и чистых установки и удаления приложения, которые дает упаковка.

Пакеты, создаваемые для настольного приложения, являются неизолированными приложениями с полным доверием только для настольных систем, хотя к приложениям применяется упрощенная виртуализация для операций записи в `HKCU` и `AppData`. Эта виртуализация позволяет им взаимодействовать с другими приложениями так же, как и классические приложения.

##### <a name="installation"></a>Установка

Пакеты приложений устанавливаются в папке *%ProgramFiles%\\WindowsApps\\package_name* с именем исполняемого файла `app_name.exe`. Каждая папка пакета содержит манифест (с именем `AppxManifest.xml`), содержащий специальное пространство имен XML для упакованных приложений. Внутри этого файла манифеста находится элемент `<EntryPoint>`, который указывает на приложение с полным доверием. При запуске этого приложения оно не выполняется в контейнере приложения, а выполняется от имени пользователя, как обычно.

После развертывания пакета файлы помечаются как доступные только для чтения и блокируются операционной системой. Windows не позволяет запускать приложения, если в эти файлы внесены несанкционированные изменения.

##### <a name="file-system"></a>Файловая система

Операционная система поддерживает различные уровни операций файловой системы для упакованных настольных приложений, в зависимости от расположения папки.

При попытке доступа к папке *AppData* пользователя система создает частное расположение для каждого пользователя и приложения в фоновом режиме. Это создает иллюзию, будто упакованное приложение изменяет реальную *AppData*, тогда как фактически оно изменяет закрытую копию. Перенаправляя операции записи таким образом, система может отслеживать все изменения, вносимые приложением в файлы. Затем она может очищать все эти файлы при удалении, что уменьшает "замусоривание" системы и улучшает процесс удаления приложений для пользователя.

##### <a name="registry"></a>Реестр

Пакеты приложений содержат файл registry.dat, который служит логическим эквивалентом `HKLM\Software` в реальном реестре. Во время выполнения этот виртуальный реестр объединяет содержимое этого куста с собственным кустом системы, чтобы обеспечить их единообразное представление.

Все операции записи сохраняются во время обновления пакета и удаляются только при удалении приложения.

##### <a name="uninstallation"></a>Удаление

Когда пользователь удаляет пакет, все файлы и папки, расположенные в `C:\Program Files\WindowsApps\package_name`, удаляются, равно как и все перенаправляемые записи в AppData или реестре, записанные во время процесса.

Дополнительные сведения о том, как упакованное приложение обрабатывает установку, доступ к файлам, реестр и удаление, см. в разделе <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-behind-the-scenes>.

Вы можете получить полный список того, что стоит проверить, в <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-prepare>.

## <a name="how-to-add-winrt-apis-to-your-desktop-project"></a>Добавление API-интерфейсов WinRT в проект для настольных систем

В этом разделе можно найти пошаговое руководство по интеграции всплывающих уведомлений в существующее приложение WPF. Хотя это и просто с точки зрения кода, это помогает проиллюстрировать весь процесс. Уведомления — это один из многих доступных API-интерфейсов WinRT, которые можно использовать в приложении .NET. В этом случае для API требуется удостоверение пакета. Этот процесс более прост, если интерфейсы API не нуждаются в удостоверении пакета.

Возьмем существующий пример приложения WPF, которое считывает файлы и отображает их содержимое на экране. Целью является отображение всплывающего уведомления при запуске приложения.

![Снимок экрана с работающим примером приложения](./media/windows-migration/sample-application.png)

Во-первых, следует проверить по следующей ссылке, требуется ли удостоверение пакета для интерфейса API Windows 10, который вы будете использовать:

<https://docs.microsoft.com/windows/apps/desktop/modernize/desktop-to-uwp-supported-api>

В нашем примере будет использоваться API <xref:Windows.UI.Notifications.Notification?displayProperty=nameWithType>, для которого требуется удостоверение пакета:

![Класс уведомлений в документации Майкрософт](./media/windows-migration/notification-class-documentation.png)

Чтобы получить доступ к API WinRT, добавьте ссылку на пакет NuGet `Microsoft.Windows.SDK.Contracts`, и этот пакет выполнит всю работу за кулисами (см. подробности в разделе <https://blogs.windows.com/windowsdeveloper/2019/04/30/calling-windows-10-apis-from-a-desktop-application-just-got-easier/>).

Теперь вы готовы приступить к добавлению кода.

Создайте метод `ShowToastNotification`, который будет вызываться при запуске приложения. Он просто создает всплывающее уведомление из XML-шаблона:

```csharp
private void ShowNotification(string title, string content, string image)
{
    string xmlString = $@"<toast><visual><binding template = 'ToastGeneric'><text>{title}</text><text>{content}</text><image src=>'{image}'</image></binding></visual></toast>";
    XmlDocument toastXml = new XmlDocument();
    toastXml.LoadXml(xmlString);
    ToastNotification toast = new ToastNotification(toastXml);
    ToastNotificationManager.CreateToastNotifier().Show(toast);
}
```

Несмотря на то, что сборка проекта выполняется, возникают ошибки из-за того, что API уведомлений требует удостоверения пакета, а вы не предоставили его. Чтобы устранить эту проблему, добавьте проект упаковки Windows в решение:

![Снимок экрана: диалоговое окно добавления нового проекта в Visual Studio.](./media/windows-migration/add-packaging-project.png)

Выберите минимальную версию Windows, которую требуется поддерживать, и версию, для которой выполняется настройка. Не все API-интерфейсы WinRT поддерживаются во всех версиях Windows 10. Каждое обновление Windows 10 добавляет новые API, которые доступны только из этой версии. поддержка старых версий отсутствует.

![Выбор минимальной версии Windows](./media/windows-migration/select-versions.png)

Следующим шагом является добавление приложения WPF в Проект упаковки Windows путем добавления ссылки на проект:

![Добавление приложения WPF в Проект упаковки Windows](./media/windows-migration/add-application.png)

![Диспетчер ссылок](./media/windows-migration/reference-manager.png)

Проект упаковки Windows может упаковывать несколько приложений, поэтому следует задать, какое из них является точкой входа:

![Настройка точки входа](./media/windows-migration/set-entry-point.png)

Следующим шагом является установка проекта WPF в качестве запускаемого проекта в конфигурации решения. Можно нажать клавишу F5 для компиляции, построения и просмотра результатов.

![Работа и отображение результатов примером приложения](./media/windows-migration/sample-app-result.png)

Давайте создадим пакет, чтобы можно было установить приложение. Щелкните правой кнопкой мыши **Магазин** > **Создать пакеты приложений**.

![Диалог создания пакетов приложений](./media/windows-migration/create-app-packages.png)

Выберите вариант загрузки неопубликованных приложений, чтобы развернуть приложение с компьютера:

![Выбор варианта загрузки неопубликованных приложений](./media/windows-migration/select-sideloading-option.png)

Выберите архитектуру приложения для своего приложения:

![Выбор архитектуры приложения](./media/windows-migration/select-app-architecture.png)

Наконец, создайте пакет, щелкнув **Создать**.

## <a name="xaml-islands"></a>XAML Islands

XAML Islands — это набор компонентов, позволяющих разработчикам классических приложений Windows использовать элементы управления XAML UWP в существующих приложениях Win32, включая Windows Forms и WPF.

![Структура XAML Islands](./media/windows-migration/xaml-islands.png)

Вы можете представить себе приложение Win32 с вашими стандартными элементами управления, а среди них "остров" пользовательского интерфейса UWP, содержащий современные элементы управления. Концепция похожа на iFrame внутри веб-страницы, показывающий содержимое из `different page.`.

Помимо добавления функций из API Windows 10, вы можете добавлять элементы XAML UWP внутри приложения с помощью XAML Islands.

В обновлении 1903 Windows 10 появился набор API-интерфейсов, позволяющих размещать содержимое UWP XAML в окнах Win32. Только приложения, работающие в Windows 10 1903, могут использовать XAML Islands.

### <a name="the-road-to-xaml-islands"></a>Путь к XAML Islands

Путь к XAML Islands начался в 2012 году, когда корпорация Майкрософт представила API-интерфейсы WinRT в качестве платформы для модернизации приложений Win32 (Windows Forms, WPF и собственных приложений Win32). Однако новые элементы управления пользовательского интерфейса в WinRT были доступны для новых приложений, но не для существующих.

В 2015 году вместе с Windows 10 родилась универсальная платформа Windows (UWP). UWP позволяет создавать приложения, работающие на любых устройствах Windows, таких как XBox, мобильные устройства и настольные ПК. Год спустя корпорация Майкрософт представила мост для классических приложений (прежнее название — Project Centennial). Мост для классических приложений — это набор средств, которые позволяли разработчикам переносить существующие приложения Win32 в Microsoft Store. В 2017 году были добавлены дополнительные возможности, позволяющие разработчикам совершенствовать приложения Win32, используя некоторые из новых API Windows 10, таких как живые плитки и уведомления в центре действий. Но всё еще без новых элементов управления пользовательским интерфейсом.

На конференции Build 2018 корпорация Майкрософт объявила о способе, позволяющем разработчикам использовать новые элементы управления XAML Windows 10 в своих текущих приложениях Win32 без полной миграции своих приложений на UWP. Он получил название XAML Islands для универсальной платформы Windows.

### <a name="how-it-works"></a>Принцип работы

В обновлении 1903 Windows 10 добавлено несколько API размещения XAML. В их число входят `WindowsXamlManager` и `DesktopWindowXamlSource`.

Класс `WindowsXamlManager` обрабатывает платформу XAML UWP. Его `InitializeForCurrentThread` метод загружает платформу XAML UWP в текущем потоке приложения Win32.

`DesktopWindowXamlSource`— это экземпляр содержимого элемента управления XAML Island. У него есть свойство `Content`, за создание экземпляра и настройку которого отвечаете вы. `DesktopWindowXamlSource` визуализирует и получает свои входные данные из HWND. Ему необходимо определить, какой другой HWND будет прикрепляться к элементу управления XAML Island. Вы отвечаете за изменение размеров и размещение HWND родителя.

Разработчики WPF или Windows Forms обычно не работают с HWND внутри своего кода, поэтому может быть трудно понять и обработать указатели HWND и скрытую проводку для взаимодействия с платформами Win32 и UWP.

#### <a name="the-xaml-islands-net-wrappers"></a>Оболочки .NET XAML Islands

В наборе средств Windows Community Toolkit предусмотрены наборы оболочек .NET XAML Islands для WPF или Windows Forms, упрощающие использование XAML Islands. Эти оболочки управляют дескрипторами HWND и управлением фокусами, помимо прочего. Разработчики Windows Forms и WPF должны использовать эти оболочки.

Набор средств Windows Community Toolkit предлагает два типа элементов управления: заключенные в оболочку элементы управления и размещаемые элементы управления.

##### <a name="wrapped-controls"></a>Заключение в оболочку элементов управления

Эта оболочка состоит в заключении некоторых элементов управления UWP в элементы управления Windows Forms или WPF, скрывая основные понятия UWP для этих разработчиков. Это такие элементы управления, как:

* WebView и WebViewCompatible
* InkCanvas и InkToolbar
* MediaPlayerElement
* MapControl

Добавьте пакет `Microsoft.Toolkit.Wpf.UI.Controls` в проект, включите ссылку на пространство имен и начните использовать их.

```xml
<Window
        ...
        xmlns:uwpControls="clr-namespace:Microsoft.Toolkit.Wpf.UI.Controls;assembly=Microsoft.Toolkit.Wpf.UI.Controls">
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="\*"/>
    </Grid.RowDefinitions>
    <uwpControls:InkToolbar TargetInkCanvas="{x:Reference Name=inkCanvas}"/>
    <uwpControls:InkCanvas Grid.Row="1" x:Name="inkCanvas" />
</Grid>
```

##### <a name="hosting-controls"></a>Размещение элементов управления

Возможности XAML Islands распространяются на большинство элементов управления от Майкрософт, сторонних элементов управления и пользовательских элементов управления, разработанных для UWP, которые можно интегрировать в Windows Forms и WPF как "острова" с полностью функциональным интерфейсом пользователя. Элемент управления `WindowsXamlHost` для WPF и Windows Forms позволяет сделать это.

Например, чтобы использовать элемент управления `WindowsXamlHost` в WPF, добавьте ссылку на пакет `Microsoft.Toolkit.Wpf.UI.XamlHost`, предоставляемый набором средств сообщества Windows.

После помещения `WindowsXamlHost` в код пользовательского интерфейса укажите тип UWP, который требуется загрузить. Можно выбрать использование заключенного в оболочку элемента управления, такого как `Button`, или более сложного, состоящего из нескольких различных элементов управления, которые являются настраиваемым элементом управления UWP.

В следующем примере демонстрируется, как добавить `Button` UWP:

```xml
<Window
        ...
        xmlns:xamlhost="clr-namespace:Microsoft.Toolkit.Wpf.UI.XamlHost;assembly=Microsoft.Toolkit.Wpf.UI.XamlHost">

<xamlhost:WindowsXamlHost x:Name="myUwpButton"
                          InitialTypeName="Windows.UI.Xaml.Controls.Button" />
```

Есть четко рекомендованный подход: лучше иметь один, более крупный "остров" XAML Island, содержащий пользовательский составной элемент управления, чем несколько островов с одним элементом управления на каждом.

Одной из основных функций XAML является привязка, она работает между кодом Win32 и таким "островом". Таким образом, можно выполнить привязку, например `Textbox` Win32 к `Textbox` UWP. Важно учитывать, что эти привязки являются односторонними привязками от UWP к Win32, поэтому при обновлении `Textbox` внутри XAML Island текстовое поле Win32 будет обновляться, но не наоборот.

Пошаговое руководство по использованию XAML Islands см. в:

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-standard-control-with-xaml-islands>

#### <a name="adding-uwp-xaml-custom-controls"></a>Добавление пользовательских элементов управления UWP XAML

Пользовательский элемент управления XAML — это элемент управления (или базовый пользовательский элемент управления), созданный вами или третьими сторонами (включая элементы управления WinUI 2.x). Чтобы разместить пользовательский элемент управления UWP в приложении Windows Forms или WPF, необходимо:

- Использовать элемента управления UWP `WindowsXamlHost` в приложении .NET.
- Создать проект приложения UWP, определяющий объект`XamlApplication`.

В проекте WPF или Windows Forms должен быть доступ к экземпляру класса `Microsoft.Toolkit.Win32.UI.XamlHost.XamlApplication`, предоставленному в наборе средств сообщества Windows. Этот объект выступает в качестве корневого поставщика метаданных для загрузки метаданных пользовательских типов XAML UWP в сборки в текущем каталоге приложения. Для этого рекомендуется добавить проект пустого приложения (универсального приложения Windows) в то же решение, что и проект WPF или Windows Forms, и изменить класс приложения по умолчанию в этом проекте.

Пользовательский элемент управления XAML UWP может быть включен в это приложение UWP или в независимый проект библиотеки классов UWP, на который вы ссылаетесь в том же решении, что и проект WPF или Windows Forms.

Подробное пошаговое описание процесса можно найти по адресу:

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

#### <a name="the-windows-ui-library-winui-2"></a>Библиотека пользовательского интерфейса Windows (WinUI 2)

Помимо входящих в операционную систему элементов управления Windows 10, одна группа XAML UWP также доставляет дополнительные элементы управления в библиотеку пользовательского интерфейса Windows (**WinUI 2**). WinUI 2 предоставляет официальные собственные элементы управления пользовательского интерфейса Майкрософт и функции для приложений UWP Windows. Эти элементы управления можно использовать внутри XAML Islands.

У WinUI 2 открытый исходный код, и вы можете найти информацию по адресу <https://github.com/microsoft/microsoft-ui-xaml>.

Следующая статься демонстрирует, как разместить элемент управления XAML UWP из библиотеки WinUI 2: <https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

### <a name="do-you-need-xaml-islands"></a>Нужны ли вам XAML Islands

XAML Islands предназначены для существующих приложений Win32, которым нужно улучшить взаимодействие с пользователем за счет новых элементов управления UWP и поведения без создания приложения заново. Вы уже могли [использовать API Windows 10](/windows/uwp/porting/desktop-to-uwp-enhance), но до появления XAML Islands — только API, не связанные с пользовательским интерфейсом.

Если вы разрабатываете новое приложение Windows, то, вероятно, [приложение UWP](/windows/uwp/get-started/universal-application-platform-guide) — правильный подход.

### <a name="the-road-ahead-xaml-islands-winui-30"></a>Предстоящий XAML Islands путь: WinUI 3.0

Начиная с Windows 8 платформа пользовательского интерфейса Windows, включая платформу пользовательского интерфейса XAML, уровень визуальной композиции и обработку ввода, поставлялась как неотъемлемая часть Windows. Значит, чтобы воспользоваться преимуществами последних улучшений в технологиях пользовательского интерфейса, необходимо выполнить обновление до последней версии пользовательского интерфейса, что замедляет темпы инноваций при разработке приложений. Для отделения этих двух циклов развития и стимуляции инноваций Майкрософт активно работает над проектом WinUI.

Начиная с WinUI 2 в 2018 г. корпорация Майкрософт приступила к отправке некоторых новых элементов управления и функций пользовательского интерфейса XAML в виде отдельных пакетов NuGet, которые создаются на основе пакета SDK для UWP.

![Структура WinUI 2.0](./media/windows-migration/winui2.png)

WinUI 3 находится в активной разработке и значительно расширяет область применения WinUI, с включением полной платформы пользовательского интерфейса, которая будет полностью отделена от пакета SDK для UWP:

![Структура WinUI 3.0](./media/windows-migration/winui3.png)

Платформа XAML теперь будет разрабатываться на сайте GitHub и поставляться извне в качестве пакетов [NuGet](/nuget/what-is-nuget).

Существующие API XAML UWP, поставляемые в составе ОС, больше не будут получать обновления возможностей. Они и дальше будут получать обновления безопасности и критические исправления в соответствии с жизненным циклом поддержки Windows 10.

Универсальная платформа Windows содержит не только платформу XAML (включая модели приложений и безопасности, а также конвейеры мультимедиа, интеграцию с оболочкой Xbox и Windows 10 и поддержку разных устройств). Мы планируем и дальше развивать это решение. Все новые функции XAML будут просто разрабатываться и поставляться как часть WinUI.

#### <a name="winui-3-in-desktop-app-and-winui-xaml-islands"></a>WinUI 3 в классических приложениях и WinUI XAML Islands

Как видите, WinUI 3 — это эволюция XAML UWP, который естественным образом работает в модели приложений UWP и всех ее требований (пакетный идентификатор MSIX, песочница, CoreWindow и т. д.). Чтобы использовать только WinUI 3 в модели приложений Win32, содержимое WinUI должно размещаться на другой платформе пользовательского интерфейса (Windows Forms, WPF и т. д.) с помощью **WinUI XAML Islands**. Это правильный путь, если вы хотите развивать свои приложения и технологии Mix. Однако если вы хотите заменить весь старый пользовательский интерфейс для WinUI, приложение не должно загружать платформы пользовательского интерфейса для простого размещения WinUI.

WinUI 3 будет включать в себя реакцию на эти ключевые отзывы, добавление **WinUI в приложения для настольных компьютеров**. Это позволит приложениям Win32 использовать WinUI 3 в качестве изолированной платформы пользовательского интерфейса, без необходимости загружать Windows Forms или WPF.

В рамках этого агрегата WinUI 3 позволяет разработчикам легко формировать правильные сочетания:

* Модель приложения: UWP, Win32
* Платформа: .NET или собственная
* Язык: .NET (C\#, Visual Basic), стандартный C++
* Упаковка: MSIX, AppX для Microsoft Store, распакованный
* Взаимодействие. Используйте WinUI 3 для расширения существующих приложений WPF, WinForms и MFC с помощью WinUI XAML Islands.

Если вы хотите получить дополнительные сведения, корпорация Майкрософт выложила эту схему в общий доступ в <https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md>.

>[!div class="step-by-step"]
>[Назад](migrate-modern-applications.md)
>[Вперед](example-migration.md)
