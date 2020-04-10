---
title: PDOStatement::fetchObject | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 71ad1932-cab3-4c29-8950-f5e82547d3b5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 727f4545e9deb34c564363cd8e3252feeb22ac16
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928590"
---
# <a name="pdostatementfetchobject"></a>PDOStatement::fetchObject
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ruft die nächste Zeile als Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
mixed PDOStatement::fetchObject([ $class_name[,$ctor_args ]] )  
```  
  
#### <a name="parameters"></a>Parameter  
$*class_name*: Eine optionale Zeichenfolge, die den Namen der zu erstellenden Klasse angibt. Der Standardwert ist „stdClass“.  
  
$*ctor_args*: Ein optionales Array mit Argumenten für einen benutzerdefinierten Klassenkonstruktor.  
  
## <a name="return-value"></a>Rückgabewert  
Bei Erfolg wird ein Objekt mit einer Instanz der Klasse zurückgegeben. Eigenschaften sind Spalten zugeordnet. Gibt bei einem Fehler „false“ zurück.  
  
## <a name="remarks"></a>Bemerkungen  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchObject();  
   print $result->Name;  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
