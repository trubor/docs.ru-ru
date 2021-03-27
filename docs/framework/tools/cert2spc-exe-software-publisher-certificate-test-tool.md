---
title: Cert2spc.exe (средство проверки сертификата издателя программного обеспечения)
description: Используйте Cert2spc.exe, средство проверки сертификата издателя программного обеспечения. Это средство создает сертификат издателя программного обеспечения (SPC) из одного или более сертификатов X.509.
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
ms.openlocfilehash: d2bd0fdc07b87a9b21b281669a213a048a407595
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654210"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a>Cert2spc.exe (средство проверки сертификата издателя программного обеспечения)

Программа для проверки сертификата издателя программного обеспечения служит для создания сертификата издателя программного обеспечения (SPC) из одного или нескольких сертификатов X.509. Программа Cert2spc.exe используется только для тестирования. Действительный сертификат SPC можно получить в центрах сертификации, таких как VeriSign и Thawte. Дополнительные сведения о создании сертификатов X.509 см. в разделе [Makecert.exe (средство создания сертификатов)](/windows/desktop/SecCrypto/makecert).  
  
 Эта программа автоматически устанавливается вместе с Visual Studio. Для запуска этого средства используйте [Командную строку разработчика или PowerShell для разработчиков в Visual Studio](/visualstudio/ide/reference/command-prompt-powershell).  
  
 В командной строке введите следующее.  
  
## <a name="syntax"></a>Синтаксис  
  
```console  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
## <a name="parameters"></a>Параметры  
  
|Аргумент|Описание|  
|--------------|-----------------|  
|`certN.cer`|Имя сертификата X.509, включаемого в SPC-файл. Можно указать несколько имен, разделенных пробелами.|  
|`crlN.crl`|Имя списка отзыва сертификатов для включения в SPC-файл. Можно указать несколько имен, разделенных пробелами.|  
|`outputSPCfile.spc`|Имя объекта PKCS #7, который будет содержать сертификаты X.509.|  
  
|Параметр|Описание|  
|------------|-----------------|  
|**/?**|Отображает синтаксис команд и параметров программы.|  
  
## <a name="examples"></a>Примеры  

 Следующая команда создает SPC-файл из файла `myCertificate.cer` и помещает его в файл `mySPCFile.spc`.  
  
```console
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 Следующая команда создает SPC-файл из файлов `oneCertificate.cer` и `twoCertificate.cer` и помещает его в файл `mySPCFile.spc`.  
  
```console
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a>См. также

- [Инструменты](index.md)
- [Makecert.exe (средство создания сертификатов)](/windows/desktop/SecCrypto/makecert)
- [Оболочки командной строки для разработчиков](/visualstudio/ide/reference/command-prompt-powershell)
