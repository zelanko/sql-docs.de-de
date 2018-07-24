---
title: 'Einen pdostatement:: ErrorCode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4161abec-c12b-444e-9de5-f1dac7b3e0e4
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07c5851453426ce1109f871ed3bd756a071ecb8b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38019392"
---
# <a name="pdostatementerrorcode"></a>PDOStatement::errorCode
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ruft den SQLSTATE des letzten Vorgangs auf dem Statementobjekt der Datenbank auf.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
string PDOStatement::errorCode();  
```  
  
## <a name="return-value"></a>Rückgabewert  
Gibt ein SQLSTATE mit fünf Zeichen als Zeichenfolge oder NULL zurück, wenn kein Vorgang über das Anweisungshandle erfolgte.  
  
## <a name="remarks"></a>Remarks  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
Dieses Beispiel zeigt eine SQL-Abfrage, die einen Fehler aufweist.  Der Fehlercode wird angezeigt.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks", "", "");  
$stmt = $conn->prepare('SELECT * FROM Person.Addressx');  
  
$stmt->execute();  
print $stmt->errorCode();  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
