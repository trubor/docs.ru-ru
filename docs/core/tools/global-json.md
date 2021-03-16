---
title: Обзор global.json
description: Узнайте, как использовать файл global.json, чтобы задать версию пакета SDK для .NET при выполнении команд .NET CLI.
ms.topic: how-to
ms.date: 05/01/2020
ms.custom: updateeachrelease
ms.openlocfilehash: cc471cf5b50cf91c38b46607ccf38bd4d087aa6a
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104145"
---
# <a name="globaljson-overview"></a><span data-ttu-id="14704-103">Обзор global.json</span><span class="sxs-lookup"><span data-stu-id="14704-103">global.json overview</span></span>

<span data-ttu-id="14704-104">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.0 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="14704-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="14704-105">С помощью файла *global.json* можно определить, какая версия пакета SDK для .NET используется при выполнении команд .NET CLI.</span><span class="sxs-lookup"><span data-stu-id="14704-105">The *global.json* file allows you to define which .NET SDK version is used when you run .NET CLI commands.</span></span> <span data-ttu-id="14704-106">Выбор пакета SDK для .NET не зависит от указания целевой среды выполнения проекта.</span><span class="sxs-lookup"><span data-stu-id="14704-106">Selecting the .NET SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="14704-107">Версия пакета SDK для .NET указывает, какие версии .NET CLI используются.</span><span class="sxs-lookup"><span data-stu-id="14704-107">The .NET SDK version indicates which versions of the .NET CLI is used.</span></span>

<span data-ttu-id="14704-108">Как правило, необходимо использовать последнюю версию средств пакета SDK, поэтому вам нужен файл *global.json*.</span><span class="sxs-lookup"><span data-stu-id="14704-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="14704-109">В некоторых сложных сценариях может потребоваться управление версией средств пакета SDK, и в этой статье объясняется, как это сделать.</span><span class="sxs-lookup"><span data-stu-id="14704-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="14704-110">Дополнительные сведения о том, как вместо этого указать среду выполнения, см. в разделе [Целевые платформы](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="14704-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="14704-111">Пакет SDK для .NET ищет файл *global.json* в текущем рабочем каталоге (который не обязательно совпадает с каталогом проекта) или в одном из его родительских каталогов.</span><span class="sxs-lookup"><span data-stu-id="14704-111">The .NET SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="14704-112">Схема файла global.json</span><span class="sxs-lookup"><span data-stu-id="14704-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="14704-113">sdk</span><span class="sxs-lookup"><span data-stu-id="14704-113">sdk</span></span>

<span data-ttu-id="14704-114">Тип: `object`</span><span class="sxs-lookup"><span data-stu-id="14704-114">Type: `object`</span></span>

<span data-ttu-id="14704-115">Указывает сведения о пакете SDK для .NET для выбора.</span><span class="sxs-lookup"><span data-stu-id="14704-115">Specifies information about the .NET SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="14704-116">version</span><span class="sxs-lookup"><span data-stu-id="14704-116">version</span></span>

- <span data-ttu-id="14704-117">Тип: `string`</span><span class="sxs-lookup"><span data-stu-id="14704-117">Type: `string`</span></span>

- <span data-ttu-id="14704-118">Доступно начиная с пакета SDK для .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="14704-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="14704-119">Версия пакета SDK для .NET для использования.</span><span class="sxs-lookup"><span data-stu-id="14704-119">The version of the .NET SDK to use.</span></span>

<span data-ttu-id="14704-120">Это поле:</span><span class="sxs-lookup"><span data-stu-id="14704-120">This field:</span></span>

- <span data-ttu-id="14704-121">Не поддерживает подстановочные знаки, то есть необходимо указать полный номер версии.</span><span class="sxs-lookup"><span data-stu-id="14704-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="14704-122">Не поддерживает диапазон версий.</span><span class="sxs-lookup"><span data-stu-id="14704-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="14704-123">allowPrerelease</span><span class="sxs-lookup"><span data-stu-id="14704-123">allowPrerelease</span></span>

- <span data-ttu-id="14704-124">Тип: `boolean`</span><span class="sxs-lookup"><span data-stu-id="14704-124">Type: `boolean`</span></span>

- <span data-ttu-id="14704-125">Доступно начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="14704-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="14704-126">Указывает, должен ли сопоставитель пакетов SDK учитывать предварительные версии при выборе версии пакета SDK, которую следует использовать.</span><span class="sxs-lookup"><span data-stu-id="14704-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="14704-127">Если это значение не задано явно, значение по умолчанию зависит от того, работаете ли вы в Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="14704-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="14704-128">Если вы **не** работаете в Visual Studio, значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="14704-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="14704-129">Если работаете в Visual Studio, используется запрошенное состояние предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="14704-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="14704-130">То есть если вы используете предварительную версию Visual Studio или включили параметр **Использовать предварительные версии пакета SDK для .NET Core** (в разделе **Сервис** > **Параметры** > **Среда** > **Функции предварительной версии**), значением по умолчанию будет `true`; в противном случае — `false`.</span><span class="sxs-lookup"><span data-stu-id="14704-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="14704-131">rollForward</span><span class="sxs-lookup"><span data-stu-id="14704-131">rollForward</span></span>

- <span data-ttu-id="14704-132">Тип: `string`</span><span class="sxs-lookup"><span data-stu-id="14704-132">Type: `string`</span></span>

- <span data-ttu-id="14704-133">Доступно начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="14704-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="14704-134">Политика наката, используемая при выборе версии пакета SDK (либо в качестве резервной, если определенная версия пакета SDK отсутствует, либо в качестве директивы для использования более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="14704-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="14704-135">[Версия](#version) должна быть указана со значением `rollForward`, если только вы не настраиваете ее равной `latestMajor`.</span><span class="sxs-lookup"><span data-stu-id="14704-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>
<span data-ttu-id="14704-136">Поведение наката по умолчанию определяется [правилами сопоставления](#matching-rules).</span><span class="sxs-lookup"><span data-stu-id="14704-136">The default roll forward behavior is determined by the [matching rules](#matching-rules).</span></span>

<span data-ttu-id="14704-137">Для понимания доступных политик и их поведения примите во внимание следующие определения для версии пакета SDK в формате `x.y.znn`:</span><span class="sxs-lookup"><span data-stu-id="14704-137">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="14704-138">`x` — основной номер версии.</span><span class="sxs-lookup"><span data-stu-id="14704-138">`x` is the major version.</span></span>
- <span data-ttu-id="14704-139">`y` — дополнительный номер версии.</span><span class="sxs-lookup"><span data-stu-id="14704-139">`y` is the minor version.</span></span>
- <span data-ttu-id="14704-140">`z` — набор возможностей.</span><span class="sxs-lookup"><span data-stu-id="14704-140">`z` is the feature band.</span></span>
- <span data-ttu-id="14704-141">`nn` — версия исправления.</span><span class="sxs-lookup"><span data-stu-id="14704-141">`nn` is the patch version.</span></span>

<span data-ttu-id="14704-142">В следующей таблице описаны возможные значения параметра `rollForward`.</span><span class="sxs-lookup"><span data-stu-id="14704-142">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="14704-143">Значение</span><span class="sxs-lookup"><span data-stu-id="14704-143">Value</span></span>         | <span data-ttu-id="14704-144">Поведение</span><span class="sxs-lookup"><span data-stu-id="14704-144">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="14704-145">Использует указанную версию.</span><span class="sxs-lookup"><span data-stu-id="14704-145">Uses the specified version.</span></span> <br> <span data-ttu-id="14704-146">Если не найдено, выполняет накат до последнего уровня обновления.</span><span class="sxs-lookup"><span data-stu-id="14704-146">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="14704-147">Если не найдено, происходит сбой.</span><span class="sxs-lookup"><span data-stu-id="14704-147">If not found, fails.</span></span> <br><br> <span data-ttu-id="14704-148">Это значение является устаревшим поведением по сравнению с предыдущими версиями пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="14704-148">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="14704-149">Использует последний уровень обновления для указанного основного номера версии, дополнительного номера версии и набора возможностей.</span><span class="sxs-lookup"><span data-stu-id="14704-149">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="14704-150">Если не найдено, выполняет накат до следующего набора возможностей более высокого уровня в пределах одного и того же основного или дополнительного номера версии и использует последний уровень обновления для этого набора возможностей.</span><span class="sxs-lookup"><span data-stu-id="14704-150">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="14704-151">Если не найдено, происходит сбой.</span><span class="sxs-lookup"><span data-stu-id="14704-151">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="14704-152">Использует последний уровень обновления для указанного основного номера версии, дополнительного номера версии и набора возможностей.</span><span class="sxs-lookup"><span data-stu-id="14704-152">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="14704-153">Если не найдено, выполняет накат до следующего набора возможностей более высокого уровня в пределах одного и того же основного или дополнительного номера версии и использует последний уровень обновления для этого набора возможностей.</span><span class="sxs-lookup"><span data-stu-id="14704-153">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="14704-154">Если не найдено, выполняет накат до следующего основного номера версии и набора возможностей более высокого уровня в пределах одного и того же основного номера версии и использует последний уровень обновления для этого набора возможностей.</span><span class="sxs-lookup"><span data-stu-id="14704-154">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="14704-155">Если не найдено, происходит сбой.</span><span class="sxs-lookup"><span data-stu-id="14704-155">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="14704-156">Использует последний уровень обновления для указанного основного номера версии, дополнительного номера версии и набора возможностей.</span><span class="sxs-lookup"><span data-stu-id="14704-156">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="14704-157">Если не найдено, выполняет накат до следующего набора возможностей более высокого уровня в пределах одного и того же основного или дополнительного номера версии и использует последний уровень обновления для этого набора возможностей.</span><span class="sxs-lookup"><span data-stu-id="14704-157">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="14704-158">Если не найдено, выполняет накат до следующего основного номера версии и набора возможностей более высокого уровня в пределах одного и того же основного номера версии и использует последний уровень обновления для этого набора возможностей.</span><span class="sxs-lookup"><span data-stu-id="14704-158">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="14704-159">Если не найдено, выполняет накат до следующего основного номера версии, дополнительного номера версии и набора возможностей более высокого уровня и использует последний уровень обновления для этого набора возможностей.</span><span class="sxs-lookup"><span data-stu-id="14704-159">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="14704-160">Если не найдено, происходит сбой.</span><span class="sxs-lookup"><span data-stu-id="14704-160">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="14704-161">Использует последний установленный уровень обновления, соответствующий запрошенному основному номеру версии, дополнительному номеру версии и набору возможностей с уровнем обновления, который соответствует указанному значению или превышает его.</span><span class="sxs-lookup"><span data-stu-id="14704-161">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="14704-162">Если не найдено, происходит сбой.</span><span class="sxs-lookup"><span data-stu-id="14704-162">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="14704-163">Использует установленные набор возможностей и уровень обновления с самой высокой версией. Уровень обновления должен соответствовать запрошенному основному номеру версии и дополнительному номеру версии с набором возможностей и уровнем обновления, который соответствует указанному значению или превышает его.</span><span class="sxs-lookup"><span data-stu-id="14704-163">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band and patch level that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="14704-164">Если не найдено, происходит сбой.</span><span class="sxs-lookup"><span data-stu-id="14704-164">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="14704-165">Использует установленные дополнительный номер версии, набор возможностей и уровень обновления с самой высокой версией. Уровень обновления должен соответствовать запрошенному основному номеру версии и дополнительному номеру версии с набором возможностей и уровнем обновления, который соответствует указанному значению или превышает его.</span><span class="sxs-lookup"><span data-stu-id="14704-165">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor, feature band, and patch level that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="14704-166">Если не найдено, происходит сбой.</span><span class="sxs-lookup"><span data-stu-id="14704-166">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="14704-167">Использует установленный пакет SDK для .NET с самой высокой версией, которая соответствует указанному значению или превышает его.</span><span class="sxs-lookup"><span data-stu-id="14704-167">Uses the highest installed .NET SDK with a version that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="14704-168">Если не найдено, происходит сбой.</span><span class="sxs-lookup"><span data-stu-id="14704-168">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="14704-169">Накат не выполняется.</span><span class="sxs-lookup"><span data-stu-id="14704-169">Doesn't roll forward.</span></span> <span data-ttu-id="14704-170">Требуется точное соответствие.</span><span class="sxs-lookup"><span data-stu-id="14704-170">Exact match required.</span></span> |

### <a name="msbuild-sdks"></a><span data-ttu-id="14704-171">msbuild-sdks</span><span class="sxs-lookup"><span data-stu-id="14704-171">msbuild-sdks</span></span>

<span data-ttu-id="14704-172">Тип: `object`</span><span class="sxs-lookup"><span data-stu-id="14704-172">Type: `object`</span></span>

<span data-ttu-id="14704-173">Позволяет управлять версией пакета SDK для проекта в одном месте, а не в отдельном проекте.</span><span class="sxs-lookup"><span data-stu-id="14704-173">Lets you control the project SDK version in one place rather than in each individual project.</span></span> <span data-ttu-id="14704-174">Дополнительные сведения см. в статье [Как разрешаются ссылки на пакеты SDK проекта](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved).</span><span class="sxs-lookup"><span data-stu-id="14704-174">For more information, see [How project SDKs are resolved](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved).</span></span>

## <a name="examples"></a><span data-ttu-id="14704-175">Примеры</span><span class="sxs-lookup"><span data-stu-id="14704-175">Examples</span></span>

<span data-ttu-id="14704-176">В следующем примере показано, как не использовать предварительные версии:</span><span class="sxs-lookup"><span data-stu-id="14704-176">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="14704-177">В следующем примере показано, как использовать наивысший установленный номер версии, который соответствует указанной версии или больше нее.</span><span class="sxs-lookup"><span data-stu-id="14704-177">The following example shows how to use the highest version installed that is greater or equal than the specified version.</span></span> <span data-ttu-id="14704-178">Показанный JSON не позволяет использовать версию пакета SDK до 2.2.200 и разрешает 2.2.200 или любую более позднюю версию, включая 3.0.xxx и 3.1.xxx.</span><span class="sxs-lookup"><span data-stu-id="14704-178">The JSON shown disallows any SDK version earlier than 2.2.200 and allows 2.2.200 or any later version, including 3.0.xxx and 3.1.xxx.</span></span>

```json
{
  "sdk": {
    "version": "2.2.200",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="14704-179">В следующем примере показано, как использовать точную указанную версию:</span><span class="sxs-lookup"><span data-stu-id="14704-179">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="14704-180">В следующем примере показано, как использовать последнюю версию набора возможностей и обновления, установленную для конкретных основной и дополнительной версий.</span><span class="sxs-lookup"><span data-stu-id="14704-180">The following example shows how to use the latest feature band and patch version installed of a specific major and minor version.</span></span> <span data-ttu-id="14704-181">Показанный JSON не позволяет использовать версию пакета SDK до 3.1.102 и разрешает 3.1.102 или любую более позднюю версию 3.1.xxx, например 3.1.103 или 3.1.200.</span><span class="sxs-lookup"><span data-stu-id="14704-181">The JSON shown disallows any SDK version earlier than 3.1.102 and allows 3.1.102 or any later 3.1.xxx version, such as 3.1.103 or 3.1.200.</span></span>

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestFeature"
  }
}
```

<span data-ttu-id="14704-182">В следующем примере показано, как использовать наивысшую версию обновления, установленную для конкретной версии.</span><span class="sxs-lookup"><span data-stu-id="14704-182">The following example shows how to use the highest patch version installed of a specific version.</span></span> <span data-ttu-id="14704-183">Показанный JSON не позволяет использовать версию пакета SDK до 3.1.102 и разрешает 3.1.102 или любую более позднюю версию 3.1.1xx, например 3.1.103 или 3.1.199.</span><span class="sxs-lookup"><span data-stu-id="14704-183">The JSON shown disallows any SDK version earlier than 3.1.102 and allows 3.1.102 or any later 3.1.1xx version, such as 3.1.103 or 3.1.199.</span></span>

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-cli"></a><span data-ttu-id="14704-184">global.json и .NET CLI</span><span class="sxs-lookup"><span data-stu-id="14704-184">global.json and the .NET CLI</span></span>

<span data-ttu-id="14704-185">Полезно знать, какие версии пакета SDK установлены на компьютере, чтобы задать их в файле *global.json*.</span><span class="sxs-lookup"><span data-stu-id="14704-185">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="14704-186">Дополнительные сведения о том, как это сделать, см. в разделе [Проверка того, установлена ли платформа .NET](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span><span class="sxs-lookup"><span data-stu-id="14704-186">For more information on how to do that, see [How to check that .NET is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="14704-187">Чтобы установить дополнительные версии пакета SDK для .NET на компьютере, посетите страницу [скачиваемых файлов .NET](https://dotnet.microsoft.com/download/dotnet).</span><span class="sxs-lookup"><span data-stu-id="14704-187">To install additional .NET SDK versions on your machine, visit the [Download .NET](https://dotnet.microsoft.com/download/dotnet) page.</span></span>

<span data-ttu-id="14704-188">Вы можете создать новый файл *global.json* в текущем каталоге, выполнив команду [dotnet new](dotnet-new.md), как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="14704-188">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="14704-189">Правила сопоставления</span><span class="sxs-lookup"><span data-stu-id="14704-189">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="14704-190">Правила сопоставления определяются точкой входа `dotnet.exe`, которая является общей для всех установленных сред выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="14704-190">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET installed runtimes.</span></span> <span data-ttu-id="14704-191">Правила сопоставления для последней установленной версии среды выполнения .NET используются, если установлено сразу нескольких сред выполнения или применяется файл *global.json*.</span><span class="sxs-lookup"><span data-stu-id="14704-191">The matching rules for the latest installed version of the .NET Runtime are used when you have multiple runtimes installed side-by-side or if or you're using a *global.json* file.</span></span>

## <a name="net-core-3x"></a>[<span data-ttu-id="14704-192">.NET Core 3.x</span><span class="sxs-lookup"><span data-stu-id="14704-192">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="14704-193">Начиная с .NET Core 3.0 при определении версии пакета SDK для использования применяются следующие правила:</span><span class="sxs-lookup"><span data-stu-id="14704-193">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="14704-194">Если файл *global.json* не найден или в файле *global.json* не указаны версия пакета SDK или значение `allowPrerelease`, используется наивысшая версия пакета SDK (эквивалентная заданию значения `rollForward` для параметра `latestMajor`).</span><span class="sxs-lookup"><span data-stu-id="14704-194">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="14704-195">Необходимость учитывать предварительные версии пакета SDK зависит от того, как вызывается `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="14704-195">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="14704-196">Если вы **не** работаете в Visual Studio, учитываются предварительные версии.</span><span class="sxs-lookup"><span data-stu-id="14704-196">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="14704-197">Если работаете в Visual Studio, используется запрошенное состояние предварительной версии.</span><span class="sxs-lookup"><span data-stu-id="14704-197">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="14704-198">То есть если вы используете предварительную версию Visual Studio или включили параметр **Использовать предварительные версии пакета SDK для .NET Core** (в разделе **Сервис** > **Параметры** > **Среда** > **Функции предварительной версии**), учитываются предварительные версии; в противном случае учитываются только выпущенные версии.</span><span class="sxs-lookup"><span data-stu-id="14704-198">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="14704-199">Если найден файл *global.json*, в котором не указана версия пакета SDK, но указано значение `allowPrerelease`, используется наивысшая версия пакета SDK (аналогично заданию значения `rollForward` для параметра `latestMajor`).</span><span class="sxs-lookup"><span data-stu-id="14704-199">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="14704-200">На то, может ли последняя версия пакета SDK выпускаться или быть предварительным выпуском, влияет значение `allowPrerelease`.</span><span class="sxs-lookup"><span data-stu-id="14704-200">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="14704-201">`true` указывает на то, что предварительные версии учитываются. `false` указывает на то, что учитываются только выпущенные версии.</span><span class="sxs-lookup"><span data-stu-id="14704-201">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="14704-202">Если файл *global.json* найден и в нем указана версия пакета SDK:</span><span class="sxs-lookup"><span data-stu-id="14704-202">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="14704-203">Если значение `rollForward` не задано, в качестве политики `rollForward` по умолчанию используется `latestPatch`.</span><span class="sxs-lookup"><span data-stu-id="14704-203">If no `rollForward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="14704-204">В противном случае проверьте каждое значение и их поведение в разделе [rollForward](#rollforward).</span><span class="sxs-lookup"><span data-stu-id="14704-204">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="14704-205">Сведения о том, учитываются ли предварительные версии и каково поведение по умолчанию, если параметр `allowPrerelease` не задан, представлены в разделе [allowPrerelease](#allowprerelease).</span><span class="sxs-lookup"><span data-stu-id="14704-205">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2x"></a>[<span data-ttu-id="14704-206">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="14704-206">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="14704-207">В пакете SDK для .NET Core 2 при определении версии пакета SDK для использования применяются следующие правила:</span><span class="sxs-lookup"><span data-stu-id="14704-207">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="14704-208">Если файл *global.json* не найден или в файле *global.json* не указана версия пакета SDK, используется последняя установленная версия пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="14704-208">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="14704-209">Последняя версия пакета SDK может быть обычным или предварительным выпуском — выбирается наибольший номер версии.</span><span class="sxs-lookup"><span data-stu-id="14704-209">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="14704-210">Если в файле *global.json* указана версия пакета SDK:</span><span class="sxs-lookup"><span data-stu-id="14704-210">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="14704-211">Если указанная версия пакета SDK найдена на компьютере, используется именно эта версия.</span><span class="sxs-lookup"><span data-stu-id="14704-211">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="14704-212">Если указанная версия пакета SDK не найдена на компьютере, используется последняя установленная **версия исправления** этой версии пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="14704-212">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="14704-213">Последняя установленная **версия обновления** для пакета SDK может быть обычным или предварительным выпуском — используется наибольший номер версии.</span><span class="sxs-lookup"><span data-stu-id="14704-213">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="14704-214">В .NET Core 2.1 и более поздних версиях **версии исправления** ниже указанной **версии исправления** не учитываются при выборе пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="14704-214">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="14704-215">Если указанная версия пакета SDK и соответствующая **версия исправления** пакета SDK не найдена, выдается ошибка.</span><span class="sxs-lookup"><span data-stu-id="14704-215">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="14704-216">Версия пакета SDK состоит из следующих частей:</span><span class="sxs-lookup"><span data-stu-id="14704-216">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="14704-217">**Главный выпуск** пакета SDK для .NET Core обозначен первой цифрой (`x`) в последней части номера (`xyz`) для версии пакета SDK 2.1.100 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="14704-217">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="14704-218">Как правило, пакет SDK для .NET Core имеет более короткий цикл выпуска, чем .NET Core.</span><span class="sxs-lookup"><span data-stu-id="14704-218">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="14704-219">**Версия исправления** обозначена двумя последними цифрами (`yz`) в последней части номера (`xyz`) для версии пакета SDK 2.1.100 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="14704-219">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="14704-220">Например, если вы указываете `2.1.300` в качестве версии пакета SDK, ищется пакет SDK до версии `2.1.399`, но `2.1.400` не считается версией исправления для `2.1.300`.</span><span class="sxs-lookup"><span data-stu-id="14704-220">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="14704-221">Версии пакета SDK для .NET Core с `2.1.100` по `2.1.201` были выпущены во время перехода между схемами номеров версий и некорректно обрабатывают нотацию `xyz`.</span><span class="sxs-lookup"><span data-stu-id="14704-221">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="14704-222">Если вы указываете эти версии в файле *global.json*, мы рекомендуем убедиться, что указанные версии установлены на целевых компьютерах.</span><span class="sxs-lookup"><span data-stu-id="14704-222">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshoot-build-warnings"></a><span data-ttu-id="14704-223">Устранение неполадок с предупреждениями сборки</span><span class="sxs-lookup"><span data-stu-id="14704-223">Troubleshoot build warnings</span></span>

* <span data-ttu-id="14704-224">Следующее предупреждение означает, что проект был скомпилирован с использованием предварительной версии пакета SDK для .NET Core:</span><span class="sxs-lookup"><span data-stu-id="14704-224">The following warning indicates that your project was compiled using a prerelease version of the .NET Core SDK:</span></span>

  > <span data-ttu-id="14704-225">Вы работаете с предварительной версией пакета SDK для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="14704-225">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="14704-226">Версию пакета SDK можно указать в файле global.json в текущем проекте.</span><span class="sxs-lookup"><span data-stu-id="14704-226">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="14704-227">Дополнительные сведения см. на странице <https://go.microsoft.com/fwlink/?linkid=869452>.</span><span class="sxs-lookup"><span data-stu-id="14704-227">More at <https://go.microsoft.com/fwlink/?linkid=869452>.</span></span>

  <span data-ttu-id="14704-228">Версии пакета SDK для .NET Core имеют гарантированное качество.</span><span class="sxs-lookup"><span data-stu-id="14704-228">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="14704-229">Однако если вы не хотите использовать предварительную версию, ознакомьтесь с различными стратегиями, которые можно применять в отношении пакета SDK для .NET Core 3.0 или более поздней версии, обратившись к разделу [allowPrerelease](#allowprerelease).</span><span class="sxs-lookup"><span data-stu-id="14704-229">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="14704-230">Для компьютеров, на которые никогда не устанавливалась среда выполнения .NET Core 3.0 или более поздней версии или пакет SDK, необходимо создать файл *global.json* и указать точную версию, которую требуется использовать.</span><span class="sxs-lookup"><span data-stu-id="14704-230">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

* <span data-ttu-id="14704-231">Следующее предупреждение означает, что проект предназначен для EF Core 1.0 или 1.1, которые несовместимы с пакетом SDK для .NET Core 2.1 и более поздних версий:</span><span class="sxs-lookup"><span data-stu-id="14704-231">The following warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions:</span></span>

  > <span data-ttu-id="14704-232">Запускаемый проект '{startupProject}' нацелен на версию платформы '.NETCoreApp' '{targetFrameworkVersion}'.</span><span class="sxs-lookup"><span data-stu-id="14704-232">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="14704-233">Эта версия средств командной строки .NET Entity Framework Core поддерживает только версию 2.0 или более позднюю.</span><span class="sxs-lookup"><span data-stu-id="14704-233">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="14704-234">Сведения об использовании более старой версии средств см. на странице <https://go.microsoft.com/fwlink/?linkid=871254>.</span><span class="sxs-lookup"><span data-stu-id="14704-234">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254>.</span></span>

  <span data-ttu-id="14704-235">Начиная с пакета SDK для .NET Core 2.1 (версия 2.1.300) поддерживается команда `dotnet ef`.</span><span class="sxs-lookup"><span data-stu-id="14704-235">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="14704-236">Чтобы скомпилировать проект, установите пакет SDK для .NET Core 2.0 (версия 2.1.201) или более ранней версии на своем компьютере и определите необходимую версию пакета SDK с помощью файла *global.json*.</span><span class="sxs-lookup"><span data-stu-id="14704-236">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) or earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="14704-237">Дополнительные сведения о команде `dotnet ef` см. в разделе [Утилиты командной строки для EF Core .NET](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="14704-237">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="14704-238">См. также</span><span class="sxs-lookup"><span data-stu-id="14704-238">See also</span></span>

- [<span data-ttu-id="14704-239">Как разрешаются пакеты SDK проекта</span><span class="sxs-lookup"><span data-stu-id="14704-239">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
