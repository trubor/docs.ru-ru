---
description: Дополнительные сведения о параметре кодирования экземпляра
title: Параметр кодировки экземпляров
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: 8cca7fd536673ca99b1014173e172508e3d97b7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631168"
---
# <a name="instance-encoding-option"></a><span data-ttu-id="00538-103">Параметр кодировки экземпляров</span><span class="sxs-lookup"><span data-stu-id="00538-103">Instance Encoding Option</span></span>

<span data-ttu-id="00538-104">Свойство **параметра кодировки экземпляра** хранилища экземпляров рабочих процессов SQL позволяет указать, следует ли поставщику сохраняемости SQL сжимать сведения о состоянии экземпляра рабочего процесса с помощью алгоритма GZip перед сохранением информации в базе данных сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="00538-104">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="00538-105">Допустимы значения этого свойства GZip и None.</span><span class="sxs-lookup"><span data-stu-id="00538-105">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="00538-106">По умолчанию используется None.</span><span class="sxs-lookup"><span data-stu-id="00538-106">The default value is None.</span></span> <span data-ttu-id="00538-107">Эти варианты описаны в следующем списке.</span><span class="sxs-lookup"><span data-stu-id="00538-107">The following list describes these options.</span></span>  
  
1. <span data-ttu-id="00538-108">**Gzip**.</span><span class="sxs-lookup"><span data-stu-id="00538-108">**GZip**.</span></span> <span data-ttu-id="00538-109">Поставщик сохраняемости кодирует сведения о состоянии с использованием алгоритма сжатия GZip перед их сохранением в базе данных сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="00538-109">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2. <span data-ttu-id="00538-110">**Нет**.</span><span class="sxs-lookup"><span data-stu-id="00538-110">**None**.</span></span> <span data-ttu-id="00538-111">Поставщик сохраняемости не сжимает сведения о состоянии перед их сохранением в базе данных сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="00538-111">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="00538-112">При кодировании и сжатии сведений о состоянии экземпляра рабочего процесса с использованием экземпляра GZip снижается потребление памяти базой данных SQL, а также снижается нагрузка на сеть (в случае если база данных расположена на другом компьютере в сети, а не на компьютере, на котором запущена служба рабочего процесса).</span><span class="sxs-lookup"><span data-stu-id="00538-112">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="00538-113">Общее руководство заключается в том, чтобы задать для свойства **параметра кодировки экземпляра** значение **None** , если экземпляр рабочего процесса имеет немалое состояние.</span><span class="sxs-lookup"><span data-stu-id="00538-113">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
