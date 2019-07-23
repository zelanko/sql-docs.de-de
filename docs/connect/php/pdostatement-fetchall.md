---
title: 'PDOStatement:: fetchAll | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: be74188a-77cd-4d19-b16e-77278373c979
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5bd53aedf65bd1e7935c7e51eb90fb78d65d2bed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936033"
---
# <a name="pdostatementfetchall"></a>PDOStatement::fetchAll
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Gibt die Zeilen in einem Resultset in einem Array zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
array PDOStatement::fetchAll([ $fetch_style[, $column_index ][, ctor_args]] );  
```  
  
#### <a name="parameters"></a>Parameter  
$*fetch_style:* Ein ganzzahliges Symbol, das das Format der Zeilendaten angibt. Unter [PDOStatement::fetch](../../connect/php/pdostatement-fetch.md) finden Sie eine Liste der Werte. PDO::FETCH_COLUMN ist ebenfalls zulässig. PDO::FETCH_BOTH ist der Standard.  
  
$*column_index:* Ein ganzzahliger Wert, der die zurückzugebende Spalte darstellt, falls für $*fetch_style* PDO::FETCH_COLUMN festgelegt ist. Der Standardwert ist 0.  
  
$*ctor_args:* Ein Array der Parameter für einen Klassenkonstruktor, wenn für $*fetch_style* PDO::FETCH_CLASS oder PDO::FETCH_OBJ festgelegt ist.  
  
## <a name="return-value"></a>Rückgabewert  
Ein Array der verbleibenden Zeilen im Resultset oder „false“ falls der Methodenaufruf fehlschlägt.  
  
## <a name="remarks"></a>Remarks  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   print "-----------\n";  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchall(PDO::FETCH_BOTH);  
   print_r( $result );  
   print "\n-----------\n";  
  
   print "-----------\n";  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchall(PDO::FETCH_NUM);  
   print_r( $result );  
   print "\n-----------\n";  
  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchall(PDO::FETCH_COLUMN, 1);  
   print_r( $result );  
   print "\n-----------\n";  
  
   class cc {  
      function __construct( $arg ) {  
         echo "$arg\n";  
      }  
  
      function __toString() {  
         echo "To string\n";  
      }  
   };  
  
   $stmt = $conn->query( 'SELECT TOP(2) * FROM Person.ContactType' );  
   $all = $stmt->fetchAll( PDO::FETCH_CLASS, 'cc', array( 'Hi!' ));  
   var_dump( $all );  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
