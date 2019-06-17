---
title: 'PDO:: ErrorCode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5864b1d8-6814-41cd-a88d-415124484c13
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bd430e026d29d0637e3b9a1543b8a89bed556bd9
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798366"
---
# <a name="pdoerrorcode"></a>PDO::errorCode
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

PDO::errorCode ruft den SQLSTATE der letzten Operation auf dem Datenbankhandle ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
mixed PDO::errorCode();  
```  
  
## <a name="return-value"></a>Rückgabewert  
PDO::errorCode gibt einen fünf Zeichen umfassenden SQLSTATE als eine Zeichenfolge oder NULL zurück, falls es auf dem Datenbankhandle keine Operation gab.  
  
## <a name="remarks"></a>Remarks  
PDO::errorCode gibt im PDO_SQLSRV-Treiber Warnungen für einige erfolgreiche Vorgänge aus. Beispielsweise wird bei einer erfolgreichen Verbindung von PDO::errorCode „01000“ zurückgegeben, um SQL_SUCCESS_WITH_INFO anzuzeigen.  
  
PDO::errorCode ruft nur die Fehlercodes ab, die diejenigen Operationen betreffen, die direkt auf der Datenbankverbindung durchgeführt wurden. Wenn Sie mittels PDO::prepare oder PDO::query eine PDOStatement-Instanz erstellen und ein Fehler im Anweisungsobjekt generiert wird, ruft PDO::errorCode diesen Fehler nicht ab. Sie müssen einen PDOStatement::errorCode aufrufen, um den Fehlercode für eine auf einem bestimmten Anweisungsobjekt durchgeführte Operation auszugeben.  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
In diesem Beispiel ist der Name der Spalte falsch geschrieben (`Cityx` anstelle von `City`) und verursacht einen Fehler, der dann gemeldet wird.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks ", "", "");  
$query = "SELECT * FROM Person.Address where Cityx = 'Essen'";  
  
$conn->query($query);  
print $conn->errorCode();  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[PDO-Klasse](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
