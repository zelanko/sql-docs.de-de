---
title: PDO::getAvailableDrivers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: eab561e6-1229-401a-9482-008c23f9a4e6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 632663b813db9a8b9a5b425c717613c24fa58ad5
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993258"
---
# <a name="pdogetavailabledrivers"></a>PDO::getAvailableDrivers
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Gibt ein Array der PDO-Treiber in Ihrer PHP-Installation zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array PDO::getAvailableDrivers ();  
```  
  
## <a name="return-value"></a>Rückgabewert  
Ein Array mit der Liste der PDO-Treiber.  
  
## <a name="remarks"></a>Bemerkungen  
Der Name des PDO-Treibers wird verwendet in PDO::__construct, um eine PDO-Instanz zu erstellen.  
  
PDO::getAvailableDrivers muss nicht von PHP-Treibern implementiert werden. Weitere Informationen zu dieser Methode finden Sie in der PHP-Dokumentation.  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
  
```  
<?php  
print_r(PDO::getAvailableDrivers());  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[PDO-Klasse](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
