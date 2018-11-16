---
title: PDOStatement::bindValue | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 13bc4ece-420e-4887-8809-bf0705ddf126
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d7ae069a5bb485f4b74a11b066f5871aba2f30ec
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606280"
---
# <a name="pdostatementbindvalue"></a>PDOStatement::bindValue
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Bindet einen Wert an einen benannten Platzhalter oder Fragezeichenplatzhalter in der SQL-Anweisung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
bool PDOStatement::bindValue($parameter, $value[, $data_type]);  
```  
  
#### <a name="parameters"></a>Parameter  
$*parameter*: Ein (gemischter) Parameterbezeichner. Ein Parametername (:name) für eine Anweisung, die benannte Platzhalter verwendet. Für eine vorbereitete Anweisung mit der Fragezeichensyntax stellt dieser den 1-basierten Index des Parameters dar.
  
$*value*: Der (gemischte) Wert, der an den Parameter gebunden wird.  
  
$*data_type*: Der optionale Datentyp (Integer), der durch die Konstante PDO::PARAM_* dargestellt wird. Der Standardwert ist PDO::PARAM_STR.  
  
## <a name="return-value"></a>Rückgabewert  
„true“ bei Erfolg, andernfalls „false“.  
  
## <a name="remarks"></a>Remarks  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
Dieses Beispiel zeigt, dass nachdem der Wert für $contact gebunden wurde, eine Änderung des Werts nicht den in der Abfrage übergebenen Wert ändert.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindValue(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindValue(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
?>  
```

> [!NOTE]
> Es wird empfohlen, die Zeichenfolgen als Eingabe verwendet, bei der Bindung von Werten, eine [decimal oder numeric-Spalte](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) auf Richtigkeit und Genauigkeit zu gewährleisten, wie PHP Genauigkeit für eingeschränkten [Gleitkommazahlen](https://php.net/manual/en/language.types.float.php). Dasselbe gilt auch für Bigint-Spalten, insbesondere, wenn die Werte außerhalb des Bereichs von sind ein [Ganzzahl](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md).

## <a name="example"></a>Beispiel  
In diesem Codebeispiel wird veranschaulicht, wie einen decimal-Wert als Eingabeparameter gebunden wird.  

```
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  

// Assume TestTable exists with a decimal field 
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindValue(1, $input, PDO::PARAM_STR);
$stmt->execute();
```
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
