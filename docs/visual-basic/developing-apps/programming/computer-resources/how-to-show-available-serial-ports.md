---
description: 'Подробнее о следующем: Практическое руководство. Отображение доступных последовательных портов в Visual Basic'
title: Практическое руководство. Отображение доступных последовательных портов
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: 7fdbd5577ca40d1a900bc9442cb4bfeedae82c64
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494575"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Практическое руководство. Отображение доступных последовательных портов в Visual Basic

В этом разделе описывается использование объекта `My.Computer.Ports` для отображения доступных последовательных портов компьютера в Visual Basic.  
  
 Чтобы дать пользователю возможность выбрать используемый порт, имена последовательных портов отображаются в элементе управления <xref:System.Windows.Forms.ListBox>.  
  
## <a name="example"></a>Пример  

 В этом примере циклически перебираются все строки, которые возвращает свойство `My.Computer.Ports.SerialPortNames`. Эти строки представляют собой имена доступных последовательных портов на компьютере.  
  
 Как правило, пользователь выбирает, какой последовательный порт приложение должно использовать из списка доступных портов. В этом примере имена последовательных портов хранятся в элементе управления <xref:System.Windows.Forms.ListBox>. Дополнительные сведения см. в разделе [Элемент управления ListBox](/dotnet/desktop/winforms/controls/listbox-control-windows-forms).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Этот пример кода также доступен в качестве фрагмента кода IntelliSense. В средстве выбора фрагмента кода он расположен в разделе **Связь и сеть**. Дополнительные сведения см. в статье [Фрагменты кода](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Компиляция кода  

 Для этого примера требуются:  
  
- Ссылка проекта на System.Windows.Forms.dll.  
  
- Доступ к членам пространства имен <xref:System.Windows.Forms>. Добавьте оператор `Imports`, если в коде не используются полные имена членов. Дополнительные сведения см. в статье [Оператор Imports (пространство имен .NET и тип)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
- Ваша форма должна включать элемент управления <xref:System.Windows.Forms.ListBox> с именем `ListBox1`.  
  
## <a name="robust-programming"></a>Отказоустойчивость  

 Необязательно использовать элемент управления <xref:System.Windows.Forms.ListBox> для отображения имен доступных последовательных портов. Вместо него можно использовать <xref:System.Windows.Forms.ComboBox> или другой элемент управления. Если приложение не требует реакции от пользователя, можно использовать для отображения информации элемент управления <xref:System.Windows.Forms.TextBox>.
  
## <a name="see-also"></a>См. также раздел

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Практическое руководство. Дозвон при помощи модема, подключенного к последовательному порту компьютера](how-to-dial-modems-attached-to-serial-ports.md)
- [Практическое руководство. Отправка строк в последовательные порты](how-to-send-strings-to-serial-ports.md)
- [Практическое руководство. Получение строк из последовательных портов](how-to-receive-strings-from-serial-ports.md)
