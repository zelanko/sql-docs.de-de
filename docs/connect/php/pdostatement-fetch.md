---
title: 'Pdostatement:: FETCH | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4368e362-5bda-4da1-8462-33714683c39f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 624f5efe97333fd76e934f94517588aede030f38
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51605260"
---
# <a name="pdostatementfetch"></a>PDOStatement::fetch
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ruft eine Zeile aus einem Resultset ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
mixed PDOStatement::fetch ([ $fetch_style[, $cursor_orientation[, $cursor_offset]]] );  
```  
  
#### <a name="parameters"></a>Parameter  
$*fetch_style:* Ein optionales ganzzahliges Symbol, das das Format der Zeilendaten angibt. Eine Liste der möglichen Werte für $*fetch_style* finden Sie im Abschnitt „Anmerkungen“. Der Standardwert ist PDO::FETCH_BOTH. $*fetch_style* in der Abrufmethode überschreibt die Angabe von $*fetch_style* in der PDO::query-Methode.  
  
$*cursor_orientation:* Ein optionales ganzzahliges Symbol, das die Zeile angibt, die abgerufen werden soll, wenn die prepare-Anweisung `PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL` angibt. Eine Liste der möglichen Werte für $*cursor_orientation* finden Sie im Abschnitt „Anmerkungen“. Ein Beispiel mit einem bildlauffähigen Cursor finden Sie unter [PDO::prepare](../../connect/php/pdo-prepare.md) .  
  
$*cursor_offset*: : Ein optionales ganzzahliges Symbol, das die Zeile angibt, die abgerufen werden soll, wenn $*cursor_orientation* entweder PDO::FETCH_ORI_ABS oder PDO::FETCH_ORI_REL und PDO::ATTR_CURSOR PDO::CURSOR_SCROLL ist.  
  
## <a name="return-value"></a>Rückgabewert  
Ein gemischter Wert, der eine Zeile oder „false“ zurückgibt.  
  
## <a name="remarks"></a>Remarks  
Der Cursor wird automatisch vorgerückt, wenn FETCH aufgerufen wird. Die folgende Tabelle enthält die Liste der möglichen Werte für $*fetch_style*.  
  
|$*fetch_style*|und Beschreibung|  
|-------------------|---------------|  
|PDO::FETCH_ASSOC|Gibt ein Array an, das von einem Spaltennamen indiziert ist.|  
|PDO::FETCH_BOTH|Gibt ein Array an, das von einem Spaltennamen und einer 0-basierten Reihenfolge indiziert ist. Dies ist die Standardeinstellung.|  
|PDO::FETCH_BOUND|Gibt „true“ zurück und weist die Werte gemäß [PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md)zu.|  
|PDO::FETCH_CLASS|Erstellt eine Instanz und ordnet Spalten den benannten Eigenschaften zu.<br /><br />Rufen Sie [PDOStatement::setFetchMode](../../connect/php/pdostatement-setfetchmode.md) auf, bevor Sie FETCH aufrufen.|  
|PDO::FETCH_INTO|Aktualisiert eine Instanz der angeforderten Klasse.<br /><br />Rufen Sie [PDOStatement::setFetchMode](../../connect/php/pdostatement-setfetchmode.md) auf, bevor Sie FETCH aufrufen.|  
|PDO::FETCH_LAZY|Erstellt Namen von Variablen während des Zugriffs sowie ein unbenanntes Objekt.|  
|PDO::FETCH_NUM|Gibt ein Array an, das von einer nullbasierten Spaltenreihenfolge indiziert ist.|  
|PDO::FETCH_OBJ|Gibt ein unbenanntes Objekt mit Eigenschaftennamen an, die Spaltennamen zugeordnet sind.|  
  
Wenn sich der Cursor am Ende des Resultsets befindet (die letzte Zeile wurde abgerufen und der Cursor befindet sich außerhalb der Begrenzung des Resultsets) und es sich um einen Vorwärtscursor handelt (PDO::ATTR_CURSOR = PDO::CURSOR_FWDONLY), schlagen nachfolgende FETCH-Aufrufe fehl.  
  
Wenn der Cursor bildlauffähig ist (PDO::ATTR_CURSOR = PDO::CURSOR_SCROLL), wird FETCH den Cursor innerhalb der Begrenzung des Resultsets bewegen. Die folgende Tabelle enthält die Liste der möglichen Werte für $*cursor_orientation*.  
  
|$*cursor_orientation*|und Beschreibung|  
|--------------------------|---------------|  
|PDO::FETCH_ORI_NEXT|Ruft die nächste Zeile ab. Dies ist die Standardeinstellung.|  
|PDO::FETCH_ORI_PRIOR|Ruft die vorherige Zeile ab.|  
|PDO::FETCH_ORI_FIRST|Ruft die erste Zeile ab.|  
|PDO::FETCH_ORI_LAST|Ruft die letzte Zeile ab.|  
|PDO::FETCH_ORI_ABS, *num*|Ruft die in $*cursor_offset* angeforderte Zeile über die Zeilennummer ab.|  
|PDO::FETCH_ORI_REL, *num*|Ruft die in $*cursor_offset* angeforderte Zeile über die relative Position von der aktuellen Position ab.|  
  
Wenn der für $*cursor_offset* oder $*cursor_orientation* angegebene Wert eine Position außerhalb der Grenzen des Resultsets ergibt, tritt ein Fehler beim Abruf auf.  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   print( "\n---------- PDO::FETCH_CLASS -------------\n" );  
   $stmt = $conn->query( "select * from HumanResources.Department order by GroupName" );  
  
   class cc {  
      function __construct( $arg ) {  
         echo "$arg";  
      }  
  
      function __toString() {  
         return $this->DepartmentID . "; " . $this->Name . "; " . $this->GroupName;  
      }  
   }  
  
   $stmt->setFetchMode(PDO::FETCH_CLASS, 'cc', array( "arg1 " ));  
   while ( $row = $stmt->fetch(PDO::FETCH_CLASS)) {   
      print($row . "\n");   
   }  
  
   print( "\n---------- PDO::FETCH_INTO -------------\n" );  
   $stmt = $conn->query( "select * from HumanResources.Department order by GroupName" );  
   $c_obj = new cc( '' );  
  
   $stmt->setFetchMode(PDO::FETCH_INTO, $c_obj);  
   while ( $row = $stmt->fetch(PDO::FETCH_INTO)) {   
      echo "$c_obj\n";  
   }  
  
   print( "\n---------- PDO::FETCH_ASSOC -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_ASSOC );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_NUM -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_NUM );  
   print_r ($result );  
  
   print( "\n---------- PDO::FETCH_BOTH -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_BOTH );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_LAZY -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_LAZY );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_OBJ -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_OBJ );  
   print $result->Name;  
   print( "\n \n" );  
  
   print( "\n---------- PDO::FETCH_BOUND -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $stmt->bindColumn('Name', $name);  
   $result = $stmt->fetch( PDO::FETCH_BOUND );  
   print $name;  
   print( "\n \n" );  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
