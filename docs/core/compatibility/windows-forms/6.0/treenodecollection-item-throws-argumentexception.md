---
title: Критическое изменение. TreeNodeCollection.Item(Int32) создает для используемого узла исключение ArgumentException
description: 'Сведения о критическом изменении в .NET 6: теперь TreeNodeCollection.Item(Int32) создает исключение ArgumentException, если назначаемый узел уже назначен какому-либо представлению TreeView.'
ms.date: 01/19/2021
ms.openlocfilehash: 29727da2e4bc3d6ac89ed88819bf03d058603f77
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255700"
---
# <a name="treenodecollectionitem-throws-exception-if-node-is-assigned-elsewhere"></a><span data-ttu-id="3857e-103">TreeNodeCollection.Item создает исключение, если узел назначен в другом месте</span><span class="sxs-lookup"><span data-stu-id="3857e-103">TreeNodeCollection.Item throws exception if node is assigned elsewhere</span></span>

<span data-ttu-id="3857e-104"><xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> создает исключение <xref:System.ArgumentException>, если назначаемый узел уже привязан к другому представлению <xref:System.Windows.Forms.TreeView> или к этому же представлению <xref:System.Windows.Forms.TreeView> в другом индексе.</span><span class="sxs-lookup"><span data-stu-id="3857e-104"><xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> throws an <xref:System.ArgumentException> if the node being assigned is already bound to another <xref:System.Windows.Forms.TreeView> or to this <xref:System.Windows.Forms.TreeView> at a different index.</span></span>

## <a name="change-description"></a><span data-ttu-id="3857e-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="3857e-105">Change description</span></span>

<span data-ttu-id="3857e-106">В предыдущих версиях .NET узел дерева можно назначить коллекции, даже если он уже привязан к какому-либо <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="3857e-106">In previous .NET versions, you can assign a tree node to a collection even if it's already bound to a <xref:System.Windows.Forms.TreeView>.</span></span> <span data-ttu-id="3857e-107">Это может привести к дублированию узлов.</span><span class="sxs-lookup"><span data-stu-id="3857e-107">This can lead to duplicated nodes.</span></span> <span data-ttu-id="3857e-108">Начиная с версии NET 6 <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> создает исключение <xref:System.ArgumentException>, если назначаемый узел уже привязан к другому представлению <xref:System.Windows.Forms.TreeView> или к этому же представлению <xref:System.Windows.Forms.TreeView> в другом индексе.</span><span class="sxs-lookup"><span data-stu-id="3857e-108">Starting in .NET 6, <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> throws an <xref:System.ArgumentException> if the node being assigned is already bound to another <xref:System.Windows.Forms.TreeView> or to this <xref:System.Windows.Forms.TreeView> at a different index.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="3857e-109">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="3857e-109">Reason for change</span></span>

<span data-ttu-id="3857e-110">Проверка входного параметра согласуется с поведением других API `TreeNodeCollection`.</span><span class="sxs-lookup"><span data-stu-id="3857e-110">Validating the input parameter is consistent with the behavior of other `TreeNodeCollection` APIs.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3857e-111">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="3857e-111">Version introduced</span></span>

<span data-ttu-id="3857e-112">.NET 6, предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="3857e-112">.NET 6 Preview 1</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3857e-113">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="3857e-113">Recommended action</span></span>

<span data-ttu-id="3857e-114">Не забудьте отменить привязку узла `TreeNode`, прежде чем назначать его коллекции.</span><span class="sxs-lookup"><span data-stu-id="3857e-114">Make sure to unbind a `TreeNode` before assigning it to the collection.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="3857e-115">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="3857e-115">Affected APIs</span></span>

<xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`

### Category

Windows Forms

-->
