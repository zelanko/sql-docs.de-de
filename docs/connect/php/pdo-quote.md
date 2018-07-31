---
title: PDO::quote | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ab9ddc48-42f8-4edf-aa8b-b0fc66706161
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 29147b488ea6f66870db4355021d2cf76d48496b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38064276"
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

[PDO](http://php.net/manual/book.pdo.php)  
  
