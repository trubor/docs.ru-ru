---
ms.openlocfilehash: 54ef49755dc0b9d1b821ae7999ab218626d455e1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032110"
---
### <a name="custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively"></a><span data-ttu-id="d6fb2-101">Пользовательские экземпляры EncoderFallbackBuffer не поддерживают рекурсивный откат</span><span class="sxs-lookup"><span data-stu-id="d6fb2-101">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>

<span data-ttu-id="d6fb2-102">Пользовательские экземпляры <xref:System.Text.EncoderFallbackBuffer> не поддерживают рекурсивный откат.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-102">Custom <xref:System.Text.EncoderFallbackBuffer> instances cannot fall back recursively.</span></span> <span data-ttu-id="d6fb2-103">В результате реализации <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> должна быть создана последовательность символов, которая преобразуется в целевую кодировку.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-103">The implementation of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must result in a character sequence that is convertible to the destination encoding.</span></span> <span data-ttu-id="d6fb2-104">В противном случае возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-104">Otherwise, an exception occurs.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d6fb2-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="d6fb2-105">Change description</span></span>

<span data-ttu-id="d6fb2-106">При перекодировании символов в байты среда выполнения обнаруживает некорректные или непреобразуемые последовательности UTF-16 и передает эти символы методу <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-106">During a character-to-byte transcoding operation, the runtime detects ill-formed or nonconvertible UTF-16 sequences and provides those characters to the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d6fb2-107">Метод `Fallback` определяет, какие символы следует заменить в исходных непреобразуемых данных, и эти символы удаляются путем вызова <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> в цикле.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-107">The `Fallback` method determines which characters should be substituted for the original nonconvertible data, and these characters are drained by calling <xref:System.Text.EncoderFallbackBuffer.GetNextChar%2A?displayProperty=nameWithType> in a loop.</span></span>

<span data-ttu-id="d6fb2-108">Затем среда выполнения пытается перекодировать эти символы подстановки в целевую кодировку.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-108">The runtime then attempts to transcode these substitution characters to the target encoding.</span></span> <span data-ttu-id="d6fb2-109">Если это удалось выполнить, среда выполнения продолжит перекодировку с того места, где она остановилась на исходной входной строке.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-109">If this operation succeeds, the runtime continues transcoding from where it left off in the original input string.</span></span>

<span data-ttu-id="d6fb2-110">Ранее пользовательские реализации <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> могли возвращать последовательности символов, которые нельзя преобразовать в целевую кодировку.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-110">Previously, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> can return character sequences that are not convertible to the destination encoding.</span></span> <span data-ttu-id="d6fb2-111">Если подставляемые символы не поддерживают такое преобразование, среда выполнения снова вызовет метод <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> с символами подстановки, ожидая, что метод <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> вернет новую последовательность символов подстановки.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-111">If the substituted characters cannot be transcoded to the target encoding, the runtime invokes the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> method once again with the substitution characters, expecting the <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> method to return a new substitution sequence.</span></span> <span data-ttu-id="d6fb2-112">Этот процесс продолжится до тех пор, пока среда выполнения не увидит правильно сформированную и преобразуемую последовательность символов подстановки или пока не будет достигнуто максимальное число рекурсий.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-112">This process continues until the runtime eventually sees a well-formed, convertible substitution, or until a maximum recursion count is reached.</span></span>

<span data-ttu-id="d6fb2-113">Начиная с версии .NET Core 3.0, пользовательские реализации <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> должны возвращать последовательности символов, преобразуемые в целевую кодировку.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-113">Starting with .NET Core 3.0, custom implementations of <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType> must return character sequences that are convertible to the destination encoding.</span></span> <span data-ttu-id="d6fb2-114">Если подставляемые символы нельзя перекодировать в целевую кодировку, создается исключение <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-114">If the substituted characters cannot be transcoded to the target encoding, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="d6fb2-115">Среда выполнения больше не будет выполнять рекурсивные вызовы к экземпляру <xref:System.Text.EncoderFallbackBuffer>.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-115">The runtime will no longer make recursive calls into the <xref:System.Text.EncoderFallbackBuffer> instance.</span></span>

<span data-ttu-id="d6fb2-116">Такой подход применяется только в том случае, если выполнены все следующие три условия:</span><span class="sxs-lookup"><span data-stu-id="d6fb2-116">This behavior only applies when all three of the following conditions are met:</span></span>

- <span data-ttu-id="d6fb2-117">Среда выполнения обнаруживает последовательность UTF-16, которая была неправильно сформирована или не подлежит преобразованию в целевую кодировку.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-117">The runtime detects an ill-formed UTF-16 sequence or a UTF-16 sequence that cannot be converted to the target encoding.</span></span>
- <span data-ttu-id="d6fb2-118">Указана пользовательская реализация <xref:System.Text.EncoderFallback>.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-118">A custom <xref:System.Text.EncoderFallback> has been specified.</span></span>
- <span data-ttu-id="d6fb2-119">Пользовательская реализация <xref:System.Text.EncoderFallback> пытается заменить новую неправильно сформированную или непреобразуемую последовательность UTF-16.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-119">The custom <xref:System.Text.EncoderFallback> attempts to substitute a new ill-formed or nonconvertible UTF-16 sequence.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d6fb2-120">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="d6fb2-120">Version introduced</span></span>

<span data-ttu-id="d6fb2-121">3.0</span><span class="sxs-lookup"><span data-stu-id="d6fb2-121">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d6fb2-122">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="d6fb2-122">Recommended action</span></span>

<span data-ttu-id="d6fb2-123">В большинстве случаев от разработчиков не требуется никаких действий.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-123">Most developers needn't take any action.</span></span>

<span data-ttu-id="d6fb2-124">Если приложение использует пользовательский класс <xref:System.Text.EncoderFallback> и <xref:System.Text.EncoderFallbackBuffer>, убедитесь, что реализация <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> заполняет буфер отката правильно сформированными данными UTF-16, которые можно сразу же преобразовать в целевую кодировку, когда среда выполнения впервые вызывает метод <xref:System.Text.EncoderFallbackBuffer.Fallback%2A>.</span><span class="sxs-lookup"><span data-stu-id="d6fb2-124">If an application uses a custom <xref:System.Text.EncoderFallback> and <xref:System.Text.EncoderFallbackBuffer> class, ensure the implementation of <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType> populates the fallback buffer with well-formed UTF-16 data that is directly convertible to the target encoding when the <xref:System.Text.EncoderFallbackBuffer.Fallback%2A> method is first invoked by the runtime.</span></span>

#### <a name="category"></a><span data-ttu-id="d6fb2-125">Категория</span><span class="sxs-lookup"><span data-stu-id="d6fb2-125">Category</span></span>

<span data-ttu-id="d6fb2-126">Библиотеки Core .NET</span><span class="sxs-lookup"><span data-stu-id="d6fb2-126">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d6fb2-127">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="d6fb2-127">Affected APIs</span></span>

- <xref:System.Text.EncoderFallbackBuffer.Fallback%2A?displayProperty=nameWithType>
- <xref:System.Text.EncoderFallbackBuffer.GetNextChar?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.EncoderFallbackBuffer.Fallback`
- `M:System.Text.EncoderFallbackBuffer.GetNextChar`

-->
