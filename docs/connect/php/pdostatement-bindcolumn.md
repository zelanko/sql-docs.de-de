---
title: 'Pdostatement:: Bindcolumn | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: bbdcea53-d23d-4769-89a0-95c7cf4d5390
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b01f19dcb7b55da9c547d07d07784fe1730cdd66
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38006892"
---
# <a name="pdostatementbindcolumn"></a>PDOStatement::bindColumn
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Bindet eine Variable an eine Spalte im Resultset.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
bool PDOStatement::bindColumn($column, &$param[, $type[, $maxLen[, $driverdata ]]] );  
```  
  
#### <a name="parameters"></a>Parameter  
$*column:* Die (gemischte) Nummer der Spalte (1-basierter Index) oder der Name der Spalte im Resultset.  
  
&$*param:* Der (gemischte) Name der PHP-Variable, an die die Spalte gebunden werden wird.  
  
$*type:* Der optionale Datentyp des Parameters, der durch eine PDO::PARAM_*-Konstante dargestellt wird.  
  
$*maxLen*: Optionale ganze Zahl, die von den Microsoft-Treibern für PHP für SQL Server nicht verwendet wird.  
  
$*driverdata:* Optionale(r) gemischte(r) Parameter für den Treiber. Beispielsweise können Sie PDO::SQLSRV_ENCODING_UTF8 angeben, um die Spalte an eine Variable als UTF-8-codierte Zeichenfolge zu binden.  
  
## <a name="return-value"></a>Rückgabewert  
TRUE bei Erfolg, andernfalls FALSE.  
  
## <a name="remarks"></a>Remarks  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
Dieses Beispiel zeigt, wie eine Variable an eine Spalte im Resultset gebunden werden kann.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "SELECT Title, FirstName, EmailAddress FROM Person.Contact where LastName = 'Estes'";  
$stmt = $conn->prepare($query);  
$stmt->execute();  
  
$stmt->bindColumn('EmailAddress', $email);  
while ( $row = $stmt->fetch( PDO::FETCH_BOUND ) ){  
   echo "$email\n";  
}  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
