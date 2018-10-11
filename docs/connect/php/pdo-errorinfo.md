---
title: 'PDO:: errorInfo | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9d5481d5-13bc-4388-b3aa-78676c0fc709
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8216e6c9adbb2154a1e416510b989db252572cb2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47690578"
---
# <a name="pdoerrorinfo"></a>PDO::errorInfo
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ruft erweiterte Fehlerinformationen des zuletzt ausgeführten Vorgangs des Datenbankhandles ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array PDO::errorInfo();  
```  
  
## <a name="return-value"></a>Rückgabewert  
Ein Array mit Fehlerinformationen über den zuletzt ausgeführten Vorgang des Datenbankhandles. Dieses Array besteht aus den folgenden Feldern:  
  
-   Der SQLSTATE-Fehlercode  
  
-   Der treiberspezifische Fehlercode  
  
-   Die treiberspezifische Fehlermeldung  
  
Wenn kein Fehler vorliegt oder wenn der SQLSTATE nicht festgelegt ist, sind die treiberspezifischen Felder NULL.  
  
## <a name="remarks"></a>Remarks  
PDO::errorInfo ruft nur die Fehlerinformationen für Vorgänge ab, die direkt in der Datenbank ausgeführt werden. Verwenden Sie PDOStatement::errorInfo, wenn eine PDOStatement-Instanz mit PDO::prepare oder PDO::query erstellt wird.  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
In diesem Beispiel ist der Name der Spalte falsch geschrieben (`Cityx` anstelle von `City`) und verursacht einen Fehler, der dann gemeldet wird.  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks ", "");  
$query = "SELECT * FROM Person.Address where Cityx = 'Essen'";  
  
$conn->query($query);  
print $conn->errorCode();  
echo "\n";  
print_r ($conn->errorInfo());  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[PDO-Klasse](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
