---
title: PDO::quote | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab9ddc48-42f8-4edf-aa8b-b0fc66706161
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b14ce7da2a7cb7fbc59de41fc7a651c6e67c86c
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51604731"
---
# <a name="pdoquote"></a>PDO::quote
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Verarbeitet eine Zeichenfolge für die Verwendung in einer Abfrage, indem die Eingabezeichenfolge gemäß der zugrunde liegenden SQL Server-Datenbank in Anführungszeichen gesetzt wird. PDO::quote umgeht Sonderzeichen in der Eingabezeichenfolge unter Verwendung eines für den SQL Server geeigneten Zitierstils.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
string PDO::quote( $string[, $parameter_type ] )  
```  
  
#### <a name="parameters"></a>Parameter  
$*string*: Die zu zitierende Zeichenfolge.  
  
$*parameter_type:* Ein optionales Symbol (ganze Zahl), das den Datentyp angibt.  Der Standardwert ist PDO::PARAM_STR.  
  
## <a name="return-value"></a>Rückgabewert  
Eine Zeichenfolge in Anführungszeichen, die an eine SQL-Anweisung oder bei einem Fehler an false übergeben werden kann.  
  
## <a name="remarks"></a>Remarks  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
  
```  
<?php  
$database = "test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$param = 'a \' g';  
$param2 = $conn->quote( $param );  
  
$query = "INSERT INTO Table1 VALUES( ?, '1' )";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param));  
  
$query = "INSERT INTO Table1 VALUES( ?, ? )";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param, $param2));  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[PDO-Klasse](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
