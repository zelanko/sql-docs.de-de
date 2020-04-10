---
title: PDOStatement::errorCode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4161abec-c12b-444e-9de5-f1dac7b3e0e4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1092f1736c4d217a3e875a7df8060b0f722fd080
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80907910"
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
  
## <a name="remarks"></a>Bemerkungen  
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
  
## <a name="see-also"></a>Weitere Informationen  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
