---
title: 'PDOStatement:: bindColumn | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: bbdcea53-d23d-4769-89a0-95c7cf4d5390
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d4b159e57f6f2335e894490f7e34d159bd95b2b6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993133"
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
  
## <a name="remarks"></a>Bemerkungen  
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
  
## <a name="see-also"></a>Weitere Informationen  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
