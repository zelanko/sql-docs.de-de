---
title: PDOStatement::bindParam
description: API-Referenz für die PDOStatement::bindParam-Funktion im Microsoft PDO_SQLSRV-Treiber für PHP für SQL Server.
ms.custom: ''
ms.date: 08/10/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 65212058-2632-47a4-ba7d-2206883abf09
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dd2d1feb1ae156d685dbd18595447a248836eba9
ms.sourcegitcommit: 7eb80038c86acfef1d8e7bfd5f4e30e94aed3a75
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2020
ms.locfileid: "92081419"
---
# <a name="pdostatementbindparam"></a>PDOStatement::bindParam
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Bindet einen Parameter an einen benannten Platzhalter oder Fragezeichenplatzhalter in der SQL-Anweisung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
bool PDOStatement::bindParam($parameter, &$variable[, $data_type[, $length[, $driver_options]]]);  
```  
  
#### <a name="parameters"></a>Parameter  
$*parameter*: Ein (gemischter) Parameterbezeichner. Ein Parametername (:name) für eine Anweisung, die benannte Platzhalter verwendet. Für eine vorbereitete Anweisung mit der Fragezeichensyntax stellt dieser den 1-basierten Index des Parameters dar.  
  
&$*variable:* Der (gemischte) Name der PHP-Variablen, die an den SQL-Anweisungsparameter gebunden werden soll.  
  
$*data_type:* Eine optionale (ganzzahlige) PDO::PARAM_*-Konstante. Der Standardwert ist PDO::PARAM_STR.  
  
$*length:* Eine optionale (ganzzahlige) Länge des Datentyps. Sie können PDO::SQLSRV_PARAM_OUT_DEFAULT_SIZE festlegen, um die Standardgröße anzugeben, wenn Sie PDO::PARAM_INT oder PDO::PARAM_BOOL in $*data_type* verwenden.  
  
$*driver_options*: Dies sind die optionalen (gemischten) treiberspezifischen Optionen. Beispielsweise können Sie PDO::SQLSRV_ENCODING_UTF8 angeben, um die Spalte an eine Variable als UTF-8-codierte Zeichenfolge zu binden.  
  
## <a name="return-value"></a>Rückgabewert  
„true“ bei Erfolg, andernfalls „false“.  
  
## <a name="remarks"></a>Bemerkungen  
Beim Binden von NULL-Daten an Serverspalten vom Typ „varbinary“, „binary“ oder „varbinary(max)“ sollten Sie die binäre Codierung (PDO::SQLSRV_ENCODING_BINARY) unter Verwendung von $*driver_options* angeben. Weitere Informationen zu Codierungskonstanten finden Sie unter [Konstanten](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  

## <a name="parameter-example"></a>Parameterbeispiel  
Dieses Codebeispiel zeigt, dass, nachdem $contact an den Parameter gebunden wurde, das Ändern des Werts nicht den in der Abfrage übergebenen Wert ändert.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindParam(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindParam(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
?>  
```  
  
## <a name="output-parameter-example"></a>Ausgabeparameterbeispiel  
In diesem Codebeispiel wird veranschaulicht, wie auf einen Output-Parameter zugegriffen wird.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$input1 = 'bb';  
  
$stmt = $conn->prepare("select ? = count(*) from Sys.tables");  
$stmt->bindParam(1, $input1, PDO::PARAM_STR, 10);  
$stmt->execute();  
echo $input1;  
?>  
```  
  
> [!NOTE]
> Wenn beim Binden eines Ausgabeparameters an einen bigint-Typ der Wert möglicherweise außerhalb des Bereichs einer [ganzen Zahl](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md) liegt, kann die Verwendung von PDO::PARAM_INT mit PDO::SQLSRV_PARAM_OUT_DEFAULT_SIZE zu einem „Wert außerhalb des gültigen Bereichs“ führen. Verwenden Sie stattdessen den Standardwert PDO::PARAM_STR, und geben Sie die Größe der resultierenden Zeichenfolge an (höchstens 21). Dabei handelt es sich um die maximale Anzahl von Ziffern (einschließlich des negativen Zeichens) eines beliebigen bigint-Werts. 

## <a name="inputoutput-example"></a>Eingabe-/Ausgabebeispiel  
In diesem Codebeispiel wird veranschaulicht, wie ein Input/Output-Parameter verwendet wird.  
  
```  
<?php  
   $database = "AdventureWorks";  
   $server = "(local)";  
   $dbh = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
   $dbh->query("IF OBJECT_ID('dbo.sp_ReverseString', 'P') IS NOT NULL DROP PROCEDURE dbo.sp_ReverseString");  
   $dbh->query("CREATE PROCEDURE dbo.sp_ReverseString @String as VARCHAR(2048) OUTPUT as SELECT @String = REVERSE(@String)");  
   $stmt = $dbh->prepare("EXEC dbo.sp_ReverseString ?");  
   $string = "123456789";  
   $stmt->bindParam(1, $string, PDO::PARAM_STR | PDO::PARAM_INPUT_OUTPUT, 2048);  
   $stmt->execute();  
   print $string;   // Expect 987654321  
?>  
```  

> [!NOTE]
> Es wird empfohlen, beim Binden von Werten an eine [Spalte des Datentyps „decimal“ oder „numeric“](../../t-sql/data-types/decimal-and-numeric-transact-sql.md) Zeichenfolgen als Eingabe zu verwenden, um Präzision und Genauigkeit sicherzustellen, da die Genauigkeit von PHP für [Gleitkommazahlen](https://php.net/manual/en/language.types.float.php) begrenzt ist. Dasselbe gilt für Spalten des Datentyps „bigint“, insbesondere, wenn die Werte außerhalb des Bereichs einer [ganzen Zahl](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md) liegen.

## <a name="decimal-input-example"></a>Dezimaleingabebeispiel  
In diesem Codebeispiel wird das Binden eines Dezimalwerts als Eingabeparameter veranschaulicht.  

```
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  

// Assume TestTable exists with a decimal field 
$input = "9223372036854.80000";
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindParam(1, $input, PDO::PARAM_STR);
$stmt->execute();
```


## <a name="see-also"></a>Weitere Informationen  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
