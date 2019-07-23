---
title: 'PDOStatement:: Execute | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c2e80566-fa41-4918-8521-cf2e05374cbd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 31e7465b2fca0d76f569afb83e3a7d8501fd6036
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936043"
---
# <a name="pdostatementexecute"></a>PDOStatement::execute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Führt eine Anweisung aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
bool PDOStatement::execute ([ $input ] );  
```  
  
#### <a name="parameters"></a>Parameter  
*$input*: (Optional) Ein assoziatives Array, das die Werte für Parametermarker enthält.  
  
## <a name="return-value"></a>Rückgabewert  
„true“ bei Erfolg, andernfalls „false“.  
  
## <a name="remarks"></a>Remarks  
Anweisungen, die mit PDOStatement::execute ausgeführt werden, müssen erst mit [PDO::prepare](../../connect/php/pdo-prepare.md)vorbereitet werden. Informationen zum Angeben der direkten oder vorbereiteten Ausführung von Anweisungen finden Sie unter [Direkte Anweisungsausführung und vorbereitete Anweisungsausführung im PDO_SQLSRV-Treiber](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md) .  
  
Alle Werte de Eingabeparameterarrays werden als PDO::PARAM_STR-Werte behandelt.  
  
Falls die vorbereitete Anweisung Parametermarker enthält, müssen Sie entweder PDOStatement::bindParam aufrufen, um die PHP-Variablen an die Parametermarker zu binden, oder ein Array, das nur aus Eingabeparameterwerten besteht, weitergeben.  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query );  
$stmt->execute();  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
  
echo "\n";  
$param = "Owner";  
$query = "select * from Person.ContactType where name = ?";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param));  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
?>  
```  
  
> [!NOTE]
> Es wird empfohlen, beim Binden von Werten an eine [Spalte des Datentyps „decimal“ oder „numeric“](../../t-sql/data-types/decimal-and-numeric-transact-sql.md) Zeichenfolgen als Eingabe zu verwenden, um Präzision und Genauigkeit sicherzustellen, da die Genauigkeit von PHP für [Gleitkommazahlen](https://php.net/manual/en/language.types.float.php) begrenzt ist. Dasselbe gilt für Spalten des Datentyps „bigint“, insbesondere, wenn die Werte außerhalb des Bereichs einer [ganzen Zahl](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md) liegen.

## <a name="see-also"></a>Weitere Informationen  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
