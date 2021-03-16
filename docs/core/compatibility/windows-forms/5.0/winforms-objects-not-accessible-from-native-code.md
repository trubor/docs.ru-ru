---
title: Критическое изменение. Объекты WinForms не доступны из машинного кода
description: Узнайте о критических изменениях в .NET 5, из-за которых объекты Windows Forms больше не доступны из машинного кода.
ms.date: 01/29/2021
ms.openlocfilehash: 823d37cb8115b8669b254878325a350809393e79
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256099"
---
# <a name="native-code-cant-access-windows-forms-objects"></a>Машинный код не может получить доступ к объектам Windows Forms

Начиная с .NET 5 вы больше не можете получить доступ к объектам Windows Forms из машинного кода.

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET некоторые типы Windows Forms были декорированы как видимые для COM-взаимодействия и поэтому были доступны для машинного кода. Начиная с .NET 5 API Windows Forms недоступны для COM-взаимодействия или машинного кода. Среда выполнения .NET больше не поддерживает создание пользовательских библиотек типов без дополнительной настройки. Кроме того, среда выполнения .NET не может зависеть от библиотеки типов для .NET Framework (что потребовало бы поддержания классов в том виде, в котором они предоставлялись в .NET Framework).

## <a name="reason-for-change"></a>Причина изменения

- Удаление `ComVisible(true)` из перечислений, которые использовались для создания и поиска библиотеки типов (файл TLB): так как в .NET Core отсутствует TLB для WinForms, сохранять этот атрибут не нужно.
- Удаление `ComVisible(true)` из классов `AccessibleObject`: классы не поддерживают совместное создание (не имеют конструктор без параметров), и такой атрибут не требуется для предоставления уже существующего экземпляра для COM.
- Удаление `ComVisible(true)` из классов `Control` и `Component`: использовалось, чтобы разрешить размещение элементов управления WinForms через OLE/ActiveX, например в VB6 или MFC. Но для этого требуется TLB для WinForms (больше не предоставляется), а также активация на основе реестра (также не работает без дополнительной настройки). Как правило, обслуживание размещения элементов управления WinForms на основе COM не выполнялось, поэтому поддержка была удалена полностью, без перевода в неподдерживаемое состояние.
- Удаление атрибутов `ClassInterface` из элементов управления: если размещение через OLE/ActiveX не поддерживается, эти атрибуты больше не нужны. Они хранятся в других расположениях, где объекты по-прежнему предоставляются для COM и атрибут может быть полезен.
- Удаление `ComVisible(true)` из `EventArgs`: чаще использовались при размещении через OLE/ActiveX, которое больше не поддерживается. Они также не поддерживают возможность совместного создания, поэтому этот атрибут бесполезен. Кроме того, предоставление существующих экземпляров без предоставления TLB не имеет смысла.
- Удаление `ComVisible(true)` из делегатов: назначение неизвестно, но так как размещение элементов управления WinForms в ActiveX больше не поддерживается, полезность маловероятна.
- Удаление `ComVisible(true)` из некоторого кода без возможности общего доступа: единственным потенциальным потребителем будет новый конструктор Visual Studio, но без указания GUID маловероятно, что он все еще нужен.
- Удаление `ComVisible(true)` из некоторых произвольных общедоступных классов конструктора: старый конструктор Visual Studio мог использовать COM-взаимодействие для передачи данных в эти классы. Но старый конструктор не поддерживает .NET Core, поэтому присваивание им атрибутов `ComVisible` требуется лишь в редких случаях.
- `IWin32Window` определяет тот же GUID, который был определен в .NET Framework, что имеет опасные последствия. Если вам нужно обеспечить взаимодействие с .NET Framework, используйте `ComImport`.
- Управляемому объекту `IDataObject` WinForms присвоен атрибут `ComVisible`. Это необязательно, так как существует отдельное объявление интерфейса `ComImport` для COM-взаимодействия `IDataObject`. Если задать для объекта `IDataObject` атрибут `ComVisible`, производительность будет снижена, так как TLB не предоставляется и маршалинг всегда будет завершаться сбоем. Кроме того, идентификатор GUID не был указан и отличается от идентификатора для .NET Framework, поэтому маловероятно, что удаление недокументированного IID негативно повлияет на клиентов.
- Удаление `ComVisible(false)`: эти типы помещаются на первый взгляд в произвольные расположения и являются избыточными, если по умолчанию классы не предоставляются COM-взаимодействию.

## <a name="version-introduced"></a>Представленная версия

.NET 5.0

## <a name="recommended-action"></a>Рекомендованное действие

Приведенный ниже пример работает в .NET Framework и .NET Core 3.1. В этом примере используется библиотека типов .NET Framework, которая позволяет JavaScript отправлять обратный вызов к подклассу формы через отражение.

```cs
[PermissionSet(SecurityAction.Demand, Name="FullTrust")]
[System.Runtime.InteropServices.ComVisibleAttribute(true)]
public class Form1 : Form
{
    private WebBrowser webBrowser1 = new WebBrowser();

    protected override void OnLoad(EventArgs e)
    {
        webBrowser1.AllowWebBrowserDrop = false;
        webBrowser1.IsWebBrowserContextMenuEnabled = false;
        webBrowser1.WebBrowserShortcutsEnabled = false;
        webBrowser1.ObjectForScripting = this;

        webBrowser1.DocumentText =
            "<html><body><button " +
            "onclick=\"window.external.Test('called from script code')\">" +
            "call client code from script code</button>" +
            "</body></html>";
    }

    public void Test(String message)
    {
        MessageBox.Show(message, "client code");
    }
}
```

Обеспечить работу примера на .NET 5 и более поздних версий можно двумя способами.

- Введите объявленный пользователем объект `ObjectForScripting`, который поддерживает `IDispatch` (применяется по умолчанию, если только не изменен явно на уровне проекта).

  ```cs
  public class MyScriptObject
  {
      private Form1 _form;

      public MyScriptObject(Form1 form)
      {
          _form = form;
      }

      public void Test(string message)
      {
          MessageBox.Show(message, "client code");
      }
  }

  public partial class Form1 : Form
  {
      protected override void OnLoad(EventArgs e)
      {
          ...

          // Works correctly.
          webBrowser1.ObjectForScripting = new MyScriptObject(this);

          ...
      }
  }
  ```

- Объявите интерфейс с предоставляемыми методами.

  ```cs
  public interface IForm1
  {
      void Test(string message);
  }

  [ComDefaultInterface(typeof(IForm1))]
  public partial class Form1 : Form, IForm1
  {
      protected override void OnLoad(EventArgs e)
      {
          ...

          // Works correctly.
          webBrowser1.ObjectForScripting = this;

          ...
      }
  }
  ```

## <a name="affected-apis"></a>Затронутые API

Все API Windows Forms.

<!--

### Category

- Windows Forms

-->
