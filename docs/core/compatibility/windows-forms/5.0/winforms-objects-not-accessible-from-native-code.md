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
# <a name="native-code-cant-access-windows-forms-objects"></a><span data-ttu-id="d237b-103">Машинный код не может получить доступ к объектам Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d237b-103">Native code can't access Windows Forms objects</span></span>

<span data-ttu-id="d237b-104">Начиная с .NET 5 вы больше не можете получить доступ к объектам Windows Forms из машинного кода.</span><span class="sxs-lookup"><span data-stu-id="d237b-104">Starting in .NET 5, you can no longer access Windows Forms objects from native code.</span></span>

## <a name="change-description"></a><span data-ttu-id="d237b-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="d237b-105">Change description</span></span>

<span data-ttu-id="d237b-106">В предыдущих версиях .NET некоторые типы Windows Forms были декорированы как видимые для COM-взаимодействия и поэтому были доступны для машинного кода.</span><span class="sxs-lookup"><span data-stu-id="d237b-106">In previous .NET versions, some Windows Forms types were decorated as visible to COM interop, and thus were accessible to native code.</span></span> <span data-ttu-id="d237b-107">Начиная с .NET 5 API Windows Forms недоступны для COM-взаимодействия или машинного кода.</span><span class="sxs-lookup"><span data-stu-id="d237b-107">Starting in .NET 5, no Windows Forms API are visible to COM interop or accessible to native code.</span></span> <span data-ttu-id="d237b-108">Среда выполнения .NET больше не поддерживает создание пользовательских библиотек типов без дополнительной настройки.</span><span class="sxs-lookup"><span data-stu-id="d237b-108">The .NET runtime no longer supports creating custom type libraries out of the box.</span></span> <span data-ttu-id="d237b-109">Кроме того, среда выполнения .NET не может зависеть от библиотеки типов для .NET Framework (что потребовало бы поддержания классов в том виде, в котором они предоставлялись в .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="d237b-109">In addition, the .NET runtime can't depend on the type library for .NET Framework (which would require maintaining the shape of classes as they were in .NET Framework).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d237b-110">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="d237b-110">Reason for change</span></span>

- <span data-ttu-id="d237b-111">Удаление `ComVisible(true)` из перечислений, которые использовались для создания и поиска библиотеки типов (файл TLB): так как в .NET Core отсутствует TLB для WinForms, сохранять этот атрибут не нужно.</span><span class="sxs-lookup"><span data-stu-id="d237b-111">Removal of `ComVisible(true)` from enumerations that were used for type library (TLB file) generation and lookup: Since there is no WinForms TLB provided by .NET Core, there's no value in keeping this attribute.</span></span>
- <span data-ttu-id="d237b-112">Удаление `ComVisible(true)` из классов `AccessibleObject`: классы не поддерживают совместное создание (не имеют конструктор без параметров), и такой атрибут не требуется для предоставления уже существующего экземпляра для COM.</span><span class="sxs-lookup"><span data-stu-id="d237b-112">Removal of `ComVisible(true)` from `AccessibleObject` classes: The classes are not CoCreateable (they have no parameterless constructor), and exposing an already existing instance to COM does not require that attribute.</span></span>
- <span data-ttu-id="d237b-113">Удаление `ComVisible(true)` из классов `Control` и `Component`: использовалось, чтобы разрешить размещение элементов управления WinForms через OLE/ActiveX, например в VB6 или MFC.</span><span class="sxs-lookup"><span data-stu-id="d237b-113">Removal of `ComVisible(true)` from `Control` and `Component` classes: This was used to allow hosting of WinForms controls via OLE/ActiveX, for example in VB6 or MFC.</span></span> <span data-ttu-id="d237b-114">Но для этого требуется TLB для WinForms (больше не предоставляется), а также активация на основе реестра (также не работает без дополнительной настройки).</span><span class="sxs-lookup"><span data-stu-id="d237b-114">However, this requires a TLB for WinForms, which is no longer provided, as well as registry-based activation, which also would not work out of the box.</span></span> <span data-ttu-id="d237b-115">Как правило, обслуживание размещения элементов управления WinForms на основе COM не выполнялось, поэтому поддержка была удалена полностью, без перевода в неподдерживаемое состояние.</span><span class="sxs-lookup"><span data-stu-id="d237b-115">Generally, there was no maintenance of COM-based hosting of WinForms controls, so support was removed instead of leaving it in an unsupported state.</span></span>
- <span data-ttu-id="d237b-116">Удаление атрибутов `ClassInterface` из элементов управления: если размещение через OLE/ActiveX не поддерживается, эти атрибуты больше не нужны.</span><span class="sxs-lookup"><span data-stu-id="d237b-116">Removal of `ClassInterface` attributes from controls: If hosting via OLE/ActiveX is not supported, these attributes aren't needed anymore.</span></span> <span data-ttu-id="d237b-117">Они хранятся в других расположениях, где объекты по-прежнему предоставляются для COM и атрибут может быть полезен.</span><span class="sxs-lookup"><span data-stu-id="d237b-117">They are kept in other places where objects are still exposed to COM and the attribute may be relevant.</span></span>
- <span data-ttu-id="d237b-118">Удаление `ComVisible(true)` из `EventArgs`: чаще использовались при размещении через OLE/ActiveX, которое больше не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="d237b-118">Removal of `ComVisible(true)` from `EventArgs`: They were most likely used with OLE/ActiveX hosting, which is no longer supported.</span></span> <span data-ttu-id="d237b-119">Они также не поддерживают возможность совместного создания, поэтому этот атрибут бесполезен.</span><span class="sxs-lookup"><span data-stu-id="d237b-119">They are not CoCreateable either, so the attribute has no purpose.</span></span> <span data-ttu-id="d237b-120">Кроме того, предоставление существующих экземпляров без предоставления TLB не имеет смысла.</span><span class="sxs-lookup"><span data-stu-id="d237b-120">Also, exposing existing instances without providing a TLB makes no sense.</span></span>
- <span data-ttu-id="d237b-121">Удаление `ComVisible(true)` из делегатов: назначение неизвестно, но так как размещение элементов управления WinForms в ActiveX больше не поддерживается, полезность маловероятна.</span><span class="sxs-lookup"><span data-stu-id="d237b-121">Removal of `ComVisible(true)` from delegates: Purpose is unknown, but since ActiveX hosting of WinForms Controls is no longer supported, it's unlikely to have any usefulness.</span></span>
- <span data-ttu-id="d237b-122">Удаление `ComVisible(true)` из некоторого кода без возможности общего доступа: единственным потенциальным потребителем будет новый конструктор Visual Studio, но без указания GUID маловероятно, что он все еще нужен.</span><span class="sxs-lookup"><span data-stu-id="d237b-122">Removal of `ComVisible(true)` from some non-public code: The only potential consumer would be the new Visual Studio designer, but without a GUID specified, it's unlikely that it's still needed.</span></span>
- <span data-ttu-id="d237b-123">Удаление `ComVisible(true)` из некоторых произвольных общедоступных классов конструктора: старый конструктор Visual Studio мог использовать COM-взаимодействие для передачи данных в эти классы.</span><span class="sxs-lookup"><span data-stu-id="d237b-123">Removal of `ComVisible(true)` from some arbitrary public designer classes: The old Visual Studio designer may have been using COM interop to talk to these classes.</span></span> <span data-ttu-id="d237b-124">Но старый конструктор не поддерживает .NET Core, поэтому присваивание им атрибутов `ComVisible` требуется лишь в редких случаях.</span><span class="sxs-lookup"><span data-stu-id="d237b-124">However, the old designer doesn't support .NET Core, so few people would need these as `ComVisible`.</span></span>
- <span data-ttu-id="d237b-125">`IWin32Window` определяет тот же GUID, который был определен в .NET Framework, что имеет опасные последствия.</span><span class="sxs-lookup"><span data-stu-id="d237b-125">`IWin32Window` defined the same GUID that was defined in .NET Framework, which has dangerous consequences.</span></span> <span data-ttu-id="d237b-126">Если вам нужно обеспечить взаимодействие с .NET Framework, используйте `ComImport`.</span><span class="sxs-lookup"><span data-stu-id="d237b-126">If you require interop with .NET Framework, use `ComImport`.</span></span>
- <span data-ttu-id="d237b-127">Управляемому объекту `IDataObject` WinForms присвоен атрибут `ComVisible`.</span><span class="sxs-lookup"><span data-stu-id="d237b-127">The WinForms managed `IDataObject` was made `ComVisible`.</span></span> <span data-ttu-id="d237b-128">Это необязательно, так как существует отдельное объявление интерфейса `ComImport` для COM-взаимодействия `IDataObject`.</span><span class="sxs-lookup"><span data-stu-id="d237b-128">This is not required, there is a separate `ComImport` interface declaration for `IDataObject` COM interop.</span></span> <span data-ttu-id="d237b-129">Если задать для объекта `IDataObject` атрибут `ComVisible`, производительность будет снижена, так как TLB не предоставляется и маршалинг всегда будет завершаться сбоем.</span><span class="sxs-lookup"><span data-stu-id="d237b-129">It's counterproductive to have the managed `IDataObject` be `ComVisible`, since no TLB is provided and marshaling will always fail.</span></span> <span data-ttu-id="d237b-130">Кроме того, идентификатор GUID не был указан и отличается от идентификатора для .NET Framework, поэтому маловероятно, что удаление недокументированного IID негативно повлияет на клиентов.</span><span class="sxs-lookup"><span data-stu-id="d237b-130">Also, the GUID was not specified and differed from .NET Framework, so its unlikely that removing an undocumented IID will affect customers negatively.</span></span>
- <span data-ttu-id="d237b-131">Удаление `ComVisible(false)`: эти типы помещаются на первый взгляд в произвольные расположения и являются избыточными, если по умолчанию классы не предоставляются COM-взаимодействию.</span><span class="sxs-lookup"><span data-stu-id="d237b-131">Removal of `ComVisible(false)`: Those are placed in seemingly arbitrary places and are redundant when the default is to not expose classes to COM interop.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d237b-132">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="d237b-132">Version introduced</span></span>

<span data-ttu-id="d237b-133">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="d237b-133">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d237b-134">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="d237b-134">Recommended action</span></span>

<span data-ttu-id="d237b-135">Приведенный ниже пример работает в .NET Framework и .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="d237b-135">The following example works on .NET Framework and .NET Core 3.1.</span></span> <span data-ttu-id="d237b-136">В этом примере используется библиотека типов .NET Framework, которая позволяет JavaScript отправлять обратный вызов к подклассу формы через отражение.</span><span class="sxs-lookup"><span data-stu-id="d237b-136">This example relies on the .NET Framework type library, which allows the JavaScript to call back into the form subclass via reflection.</span></span>

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

<span data-ttu-id="d237b-137">Обеспечить работу примера на .NET 5 и более поздних версий можно двумя способами.</span><span class="sxs-lookup"><span data-stu-id="d237b-137">There are two possible ways to make the example work on .NET 5 and later versions:</span></span>

- <span data-ttu-id="d237b-138">Введите объявленный пользователем объект `ObjectForScripting`, который поддерживает `IDispatch` (применяется по умолчанию, если только не изменен явно на уровне проекта).</span><span class="sxs-lookup"><span data-stu-id="d237b-138">Introduce a user-declared `ObjectForScripting` object that supports `IDispatch` (which is applied by default, unless changed explicitly at the project level).</span></span>

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

- <span data-ttu-id="d237b-139">Объявите интерфейс с предоставляемыми методами.</span><span class="sxs-lookup"><span data-stu-id="d237b-139">Declare an interface with the methods to expose.</span></span>

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

## <a name="affected-apis"></a><span data-ttu-id="d237b-140">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="d237b-140">Affected APIs</span></span>

<span data-ttu-id="d237b-141">Все API Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d237b-141">All Windows Forms APIs.</span></span>

<!--

### Category

- Windows Forms

-->
