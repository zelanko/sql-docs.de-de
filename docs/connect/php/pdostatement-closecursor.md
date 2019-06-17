---
title: 'Pdostatement:: closecursor auf | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8997ab61-e948-4d54-8d32-fc080d55525c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0100c20c2a6ebaaa0eecdcf0bfe21829740e2d65
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66780547"
---
# <a name="pdostatementclosecursor"></a>PDOStatement::closeCursor
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Schließt den Cursor und erlaubt erneute Ausführung der Anwendung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
bool PDOStatement::closeCursor();  
```  
  
## <a name="return-value"></a>Rückgabewert  
„true“ bei Erfolg, andernfalls „false“.  
  
## <a name="remarks"></a>Remarks  
„closeCursor“ ist wirksam, wenn die Verbindungsoption MultipleActiveResultSets auf „false“ gesetzt ist.  Weitere Informationen über die Option „MultipleActiveResultSets“ finden Sie unter [Vorgehensweise: Deaktivieren von mehreren aktiven Resultsets (MARS)](../../connect/php/how-to-disable-multiple-active-resultsets-mars.md).  
  
Statt „closeCursor“ aufzurufen, können Sie auch einfach das Anweisungshandle auf NULL setzen.  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets' => false ) );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
$stmt2 = $conn->prepare('SELECT * FROM HumanResources.Department');  
  
$stmt->execute();  
  
$result = $stmt->fetch();  
print_r($result);  
  
$stmt->closeCursor();  
  
$stmt2->execute();  
$result = $stmt2->fetch();  
print_r($result);  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[PDOStatement-Klasse](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
