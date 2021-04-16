---
title: Формы и проверка
description: Сведения о том, как создавать формы с использованием проверки на стороне клиента в Blazor.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- Blazor WebAssembly
ms.date: 09/19/2019
ms.openlocfilehash: d2dce23996e996a736b04c9cdd1ccf3b549ff3ff
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "88267559"
---
# <a name="forms-and-validation"></a>Формы и проверка

Платформа ASP.NET Web Forms включает набор проверяющих серверных элементов управления для проверки данных, вводимых пользователем в форму (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator` и т. д.). Платформа ASP.NET Web Forms также поддерживает привязку модели и проверку модели на основе заметок к данным (`[Required]`, `[StringLength]`, `[Range]` и т. д.). Логика проверки может быть применена как на сервере, так и на клиенте с помощью ненавязчивой проверки на основе JavaScript. Серверный элемент управления `ValidationSummary` используется для вывода пользователю сводки по ошибкам проверки.

Blazor поддерживает совместное использование логики проверки между клиентом и сервером. ASP.NET предоставляет предварительно созданные реализации JavaScript для многих распространенных серверных проверок. Во многих случаях разработчику по-прежнему нужно писать код JavaScript, чтобы полностью реализовать логику проверки для конкретного приложения. Одни и те же типы моделей, заметки к данным и логику проверки можно использовать как на сервере, так и на клиенте.

Blazor предоставляет набор входных компонентов. Входные компоненты обрабатывают привязку данных поля к модели и проверку данных, введенных пользователем, при отправке формы.

|Компонент ввода|Отрисованный элемент HTML    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

Компонент `EditForm` заключает эти входные компоненты в оболочку и управляет процессом проверки с помощью `EditContext`. При создании `EditForm` вы указываете экземпляр модели для выполнения привязки с помощью параметра `Model`. Проверка обычно выполняется с помощью заметок к данным и является расширяемой. Чтобы включить проверку на основе заметок к данным, добавьте компонент `DataAnnotationsValidator` в качестве дочернего элемента компонента `EditForm`. Компонент `EditForm` предоставляет удобное событие для обработки допустимых (`OnValidSubmit`) и недопустимых (`OnInvalidSubmit`) отправок. Кроме того, существует более универсальное событие `OnSubmit`, которое позволяет самостоятельно активировать и выполнить проверку.

Чтобы отобразить сводку по ошибкам проверки, используйте компонент `ValidationSummary`. Чтобы отобразить сообщения проверки для определенного поля ввода, используйте компонент `ValidationMessage`, указав лямбда-выражение для параметра `For`, который указывает на соответствующий элемент модели.

Следующий тип модели определяет несколько правил проверки с помощью заметок к данным:

```csharp
using System;
using System.ComponentModel.DataAnnotations;

public class Starship
{
    [Required]
    [StringLength(16,
        ErrorMessage = "Identifier too long (16 character limit).")]
    public string Identifier { get; set; }

    public string Description { get; set; }

    [Required]
    public string Classification { get; set; }

    [Range(1, 100000,
        ErrorMessage = "Accommodation invalid (1-100000).")]
    public int MaximumAccommodation { get; set; }

    [Required]
    [Range(typeof(bool), "true", "true",
        ErrorMessage = "This form disallows unapproved ships.")]
    public bool IsValidatedDesign { get; set; }

    [Required]
    public DateTime ProductionDate { get; set; }
}
```

Следующий компонент демонстрирует создание формы в Blazor на основе типа модели `Starship`:

```razor
<h1>New Ship Entry Form</h1>

<EditForm Model="@starship" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <p>
        <label for="identifier">Identifier: </label>
        <InputText id="identifier" @bind-Value="starship.Identifier" />
        <ValidationMessage For="() => starship.Identifier" />
    </p>
    <p>
        <label for="description">Description (optional): </label>
        <InputTextArea id="description" @bind-Value="starship.Description" />
    </p>
    <p>
        <label for="classification">Primary Classification: </label>
        <InputSelect id="classification" @bind-Value="starship.Classification">
            <option value="">Select classification ...</option>
            <option value="Exploration">Exploration</option>
            <option value="Diplomacy">Diplomacy</option>
            <option value="Defense">Defense</option>
        </InputSelect>
        <ValidationMessage For="() => starship.Classification" />
    </p>
    <p>
        <label for="accommodation">Maximum Accommodation: </label>
        <InputNumber id="accommodation" @bind-Value="starship.MaximumAccommodation" />
        <ValidationMessage For="() => starship.MaximumAccommodation" />
    </p>
    <p>
        <label for="valid">Engineering Approval: </label>
        <InputCheckbox id="valid" @bind-Value="starship.IsValidatedDesign" />
        <ValidationMessage For="() => starship.IsValidatedDesign" />
    </p>
    <p>
        <label for="productionDate">Production Date: </label>
        <InputDate id="productionDate" @bind-Value="starship.ProductionDate" />
        <ValidationMessage For="() => starship.ProductionDate" />
    </p>

    <button type="submit">Submit</button>
</EditForm>

@code {
    private Starship starship = new Starship();

    private void HandleValidSubmit()
    {
        // Save the data
    }
}
```

После отправки формы данные, привязанные к модели, не сохранялись в каком-либо хранилище данных, например в базе данных. В приложении Blazor WebAssembly данные должны быть отправлены на сервер. Например, для этого может использоваться запрос HTTP POST. В приложении Blazor Server данные уже находятся на сервере, но должны быть сохранены. Обработка доступа к данным в приложениях Blazor — это тема раздела "[Работа с данными](data.md)".

## <a name="additional-resources"></a>Дополнительные ресурсы

Дополнительные сведения о [формах и проверке](/aspnet/core/blazor/forms-validation) в приложениях Blazor см. в документации по Blazor.

>[!div class="step-by-step"]
>[Назад](state-management.md)
>[Вперед](data.md)
