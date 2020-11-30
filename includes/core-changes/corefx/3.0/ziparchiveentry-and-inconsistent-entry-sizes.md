---
ms.openlocfilehash: 8c8e87c885c99d28aa9a7a5d5a2b48c80d40d7db
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032164"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a><span data-ttu-id="66e4c-101">ZipArchiveEntry больше не обрабатывает архивы с несогласованными размерами записей</span><span class="sxs-lookup"><span data-stu-id="66e4c-101">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>

<span data-ttu-id="66e4c-102">Для ZIP-архивов указывается размер в сжатом и несжатом виде в центральном каталоге и в локальном заголовке.</span><span class="sxs-lookup"><span data-stu-id="66e4c-102">Zip archives list both compressed size and uncompressed size in the central directory and local header.</span></span>  <span data-ttu-id="66e4c-103">В данных записи также содержится информация о ее размере.</span><span class="sxs-lookup"><span data-stu-id="66e4c-103">The entry data itself also indicates its size.</span></span>  <span data-ttu-id="66e4c-104">В .NET Core 2.2 и более ранних версиях эти значения не проверялись на согласованность.</span><span class="sxs-lookup"><span data-stu-id="66e4c-104">In .NET Core 2.2 and earlier versions, these values were never checked for consistency.</span></span> <span data-ttu-id="66e4c-105">Начиная с версии .NET Core 3.0 такая проверка выполняется.</span><span class="sxs-lookup"><span data-stu-id="66e4c-105">Starting with .NET Core 3.0, they now are.</span></span>

#### <a name="change-description"></a><span data-ttu-id="66e4c-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="66e4c-106">Change description</span></span>

<span data-ttu-id="66e4c-107">В .NET Core 2.2 и более ранних версиях метод <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> выполняется успешно, даже если данные в локальном заголовке не совпадают с данными в центральном заголовке ZIP-файла.</span><span class="sxs-lookup"><span data-stu-id="66e4c-107">In .NET Core 2.2 and earlier versions, <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> succeeds even if the local header disagrees with the central header of the zip file.</span></span> <span data-ttu-id="66e4c-108">Данные распаковываются до тех пор, пока не будет достигнут конец сжатого потока, даже если его длина превышает размер несжатого файла, указанный в центральном каталоге или в локальном заголовке.</span><span class="sxs-lookup"><span data-stu-id="66e4c-108">Data is decompressed until the end of the compressed stream is reached, even if its length exceeds the uncompressed file size listed in the central directory/local header.</span></span>

<span data-ttu-id="66e4c-109">Начиная с .NET Core 3.0 метод <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> проверяет, чтобы данные в локальном и центральном заголовках о размерах сжатой и несжатой записи были согласованными.</span><span class="sxs-lookup"><span data-stu-id="66e4c-109">Starting with .NET Core 3.0, the <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> method checks that local header and central header agree on compressed and uncompressed sizes of an entry.</span></span>  <span data-ttu-id="66e4c-110">Если в локальном заголовке архива и/или в дескрипторе данных указаны размеры, которые отличаются от размеров в центральном каталоге ZIP-файла, метод вызывает исключение <xref:System.IO.InvalidDataException>.</span><span class="sxs-lookup"><span data-stu-id="66e4c-110">If they do not, the method throws an <xref:System.IO.InvalidDataException> if the archive's local header and/or data descriptor list sizes that disagree with the central directory of the zip file.</span></span> <span data-ttu-id="66e4c-111">При считывании записи распакованные данные усекаются до размера несжатого файла, который указан в заголовке.</span><span class="sxs-lookup"><span data-stu-id="66e4c-111">When reading an entry, decompressed data is truncated to the uncompressed file size listed in the header.</span></span>

<span data-ttu-id="66e4c-112">Это изменение позволит <xref:System.IO.Compression.ZipArchiveEntry> корректно представлять размер данных и обеспечит считывание именно такого объема данных.</span><span class="sxs-lookup"><span data-stu-id="66e4c-112">This change was made to ensure that a <xref:System.IO.Compression.ZipArchiveEntry> correctly represents the size of its data and that only that amount of data is read.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="66e4c-113">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="66e4c-113">Version introduced</span></span>

<span data-ttu-id="66e4c-114">3,0</span><span class="sxs-lookup"><span data-stu-id="66e4c-114">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="66e4c-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="66e4c-115">Recommended action</span></span>

<span data-ttu-id="66e4c-116">Переархивируйте все ZIP-файлы, с которыми возникают такие проблемы.</span><span class="sxs-lookup"><span data-stu-id="66e4c-116">Repackage any zip archive that exhibits these problems.</span></span>

#### <a name="category"></a><span data-ttu-id="66e4c-117">Категория</span><span class="sxs-lookup"><span data-stu-id="66e4c-117">Category</span></span>

<span data-ttu-id="66e4c-118">CoreFX</span><span class="sxs-lookup"><span data-stu-id="66e4c-118">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="66e4c-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="66e4c-119">Affected APIs</span></span>

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
