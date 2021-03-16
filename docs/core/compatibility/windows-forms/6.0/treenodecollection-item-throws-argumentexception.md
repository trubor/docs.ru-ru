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
# <a name="treenodecollectionitem-throws-exception-if-node-is-assigned-elsewhere"></a>TreeNodeCollection.Item создает исключение, если узел назначен в другом месте

<xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> создает исключение <xref:System.ArgumentException>, если назначаемый узел уже привязан к другому представлению <xref:System.Windows.Forms.TreeView> или к этому же представлению <xref:System.Windows.Forms.TreeView> в другом индексе.

## <a name="change-description"></a>Описание изменений

В предыдущих версиях .NET узел дерева можно назначить коллекции, даже если он уже привязан к какому-либо <xref:System.Windows.Forms.TreeView>. Это может привести к дублированию узлов. Начиная с версии NET 6 <xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=nameWithType> создает исключение <xref:System.ArgumentException>, если назначаемый узел уже привязан к другому представлению <xref:System.Windows.Forms.TreeView> или к этому же представлению <xref:System.Windows.Forms.TreeView> в другом индексе.

## <a name="reason-for-change"></a>Причина изменения

Проверка входного параметра согласуется с поведением других API `TreeNodeCollection`.

## <a name="version-introduced"></a>Представленная версия

.NET 6, предварительная версия 1

## <a name="recommended-action"></a>Рекомендованное действие

Не забудьте отменить привязку узла `TreeNode`, прежде чем назначать его коллекции.

## <a name="affected-apis"></a>Затронутые API

<xref:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.TreeNodeCollection.Item(System.Int32)`

### Category

Windows Forms

-->
