---
title: Включение автодополнения клавишей TAB
description: В этой статье объясняется, как включить автодополнение клавишей TAB для .NET CLI в средах PowerShell, Bash, zsh и fish.
author: adegeo
ms.author: adegeo
ms.topic: how-to
ms.date: 11/03/2019
ms.openlocfilehash: b5b63166faa1762d9fa82a93aa70aebb33167630
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585563"
---
# <a name="how-to-enable-tab-completion-for-the-net-cli"></a><span data-ttu-id="f41cc-103">Включение заполнения клавишей TAB для .NET CLI</span><span class="sxs-lookup"><span data-stu-id="f41cc-103">How to enable TAB completion for the .NET CLI</span></span>

<span data-ttu-id="f41cc-104">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.1 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="f41cc-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="f41cc-105">В этой статье описывается, как включить автодополнение клавишей TAB для четырех оболочек: PowerShell, Bash, zsh и fish.</span><span class="sxs-lookup"><span data-stu-id="f41cc-105">This article describes how to configure tab completion for four shells, PowerShell, Bash, zsh, and fish.</span></span> <span data-ttu-id="f41cc-106">Сведения о том, как настроить заполнение нажатием клавиши TAB в других оболочках, см. в соответствующей документации.</span><span class="sxs-lookup"><span data-stu-id="f41cc-106">For other shells, refer to their documentation on how to configure tab completion.</span></span>

<span data-ttu-id="f41cc-107">После настройки автодополнение можно активировать нажатием клавиши TAB для .NET CLI, введя в командной строке `dotnet` и нажав клавишу TAB.</span><span class="sxs-lookup"><span data-stu-id="f41cc-107">Once set up, tab completion for the .NET CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="f41cc-108">Текущая командная строка будет передана команде `dotnet complete`, а оболочка обработает результаты.</span><span class="sxs-lookup"><span data-stu-id="f41cc-108">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="f41cc-109">Вы можете проверить результаты без активации автодополнения клавишей TAB, передав что-либо непосредственно команде `dotnet complete`.</span><span class="sxs-lookup"><span data-stu-id="f41cc-109">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="f41cc-110">Пример:</span><span class="sxs-lookup"><span data-stu-id="f41cc-110">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="f41cc-111">Если команда не сработала, убедитесь, что установлен пакет SDK для .NET Core 2.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="f41cc-111">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="f41cc-112">Если он установлен, но команда все равно не работает, проверьте, что команда `dotnet` разрешается как минимум в версию пакета SDK для .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="f41cc-112">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="f41cc-113">Воспользуйтесь командой `dotnet --version`, чтобы узнать, к которой версии `dotnet` указывает текущий путь.</span><span class="sxs-lookup"><span data-stu-id="f41cc-113">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="f41cc-114">Дополнительные сведения см. в статье [Выбор версии .NET для использования](../versions/selection.md).</span><span class="sxs-lookup"><span data-stu-id="f41cc-114">For more information, see [Select the .NET version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="f41cc-115">Примеры</span><span class="sxs-lookup"><span data-stu-id="f41cc-115">Examples</span></span>

<span data-ttu-id="f41cc-116">Ниже приведено несколько примеров возможностей, которые предоставляет автодополнение клавишей TAB:</span><span class="sxs-lookup"><span data-stu-id="f41cc-116">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="f41cc-117">Входные данные</span><span class="sxs-lookup"><span data-stu-id="f41cc-117">Input</span></span>                                | <span data-ttu-id="f41cc-118">becomes</span><span class="sxs-lookup"><span data-stu-id="f41cc-118">becomes</span></span>                                                                     | <span data-ttu-id="f41cc-119">because</span><span class="sxs-lookup"><span data-stu-id="f41cc-119">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="f41cc-120">`add` является первой подкомандой в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="f41cc-120">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="f41cc-121">При автодополнении клавишей TAB подстроки сопоставляются и первой по алфавиту является `--help`.</span><span class="sxs-lookup"><span data-stu-id="f41cc-121">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="f41cc-122">После второго нажатия клавиши TAB подставляется следующее предложение.</span><span class="sxs-lookup"><span data-stu-id="f41cc-122">Pressing tab a second time brings up the next suggestion.</span></span>
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="f41cc-123">Результаты возвращаются в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="f41cc-123">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="f41cc-124">Автодополнение клавишей TAB зависит от файла проекта.</span><span class="sxs-lookup"><span data-stu-id="f41cc-124">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="f41cc-125">PowerShell</span><span class="sxs-lookup"><span data-stu-id="f41cc-125">PowerShell</span></span>

<span data-ttu-id="f41cc-126">Чтобы добавить автодополнение клавишей TAB для .NET CLI в **PowerShell**, создайте или измените профиль, хранящийся в переменной `$PROFILE`.</span><span class="sxs-lookup"><span data-stu-id="f41cc-126">To add tab completion to **PowerShell** for the .NET CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="f41cc-127">Дополнительные сведения см. в разделах [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) (Как создать свой профиль) и [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy) (Профили и политика выполнения).</span><span class="sxs-lookup"><span data-stu-id="f41cc-127">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span></span>

<span data-ttu-id="f41cc-128">Добавьте в свой профиль представленный ниже код:</span><span class="sxs-lookup"><span data-stu-id="f41cc-128">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="f41cc-129">bash</span><span class="sxs-lookup"><span data-stu-id="f41cc-129">bash</span></span>

<span data-ttu-id="f41cc-130">Чтобы добавить автодополнение клавишей TAB для .NET CLI в **bash**, добавьте в свой файл `.bashrc` представленный ниже код:</span><span class="sxs-lookup"><span data-stu-id="f41cc-130">To add tab completion to your **bash** shell for the .NET CLI, add the following code to your `.bashrc` file:</span></span>

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}" 2>/dev/null)"
  if [ $? -ne 0 ]; then
    completions=""
  fi

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a><span data-ttu-id="f41cc-131">zsh</span><span class="sxs-lookup"><span data-stu-id="f41cc-131">zsh</span></span>

<span data-ttu-id="f41cc-132">Чтобы добавить автодополнение клавишей TAB для .NET CLI в **zsh**, добавьте в свой файл `.zshrc` представленный ниже код:</span><span class="sxs-lookup"><span data-stu-id="f41cc-132">To add tab completion to your **zsh** shell for the .NET CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```

## <a name="fish"></a><span data-ttu-id="f41cc-133">fish</span><span class="sxs-lookup"><span data-stu-id="f41cc-133">fish</span></span>

<span data-ttu-id="f41cc-134">Чтобы добавить автодополнение клавишей TAB для .NET CLI в **fish**, добавьте в свой файл `config.fish` следующий код:</span><span class="sxs-lookup"><span data-stu-id="f41cc-134">To add tab completion to your **fish** shell for the .NET CLI, add the following code to your `config.fish` file:</span></span>

```fish
complete -f -c dotnet -a "(dotnet complete)"
```
