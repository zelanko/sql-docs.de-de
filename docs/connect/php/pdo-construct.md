---
title: 'PDO:: __construct | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3ee53aff-6fe4-44cd-a15b-51770c98c712
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 848a06e1b383b1416396111bf4d0e907bfba3568
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785132"
---
# <a name="pdoconstruct"></a>PDO::__construct
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Stellt eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank her.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
PDO::__construct($dsn [,$username [,$password [,$driver_options ]]] )  
```  
  
#### <a name="parameters"></a>Parameter  
*$dsn*: Eine Zeichenfolge mit dem Präfixnamen (immer `sqlsrv`), einem Doppelpunkt und dem Server-Schlüsselwort. Beispiel: `"sqlsrv:server=(local)"`. Sie können optional auch andere Schlüsselwörter angeben. Unter [Connection Options](../../connect/php/connection-options.md) finden Sie eine Beschreibung des Server-Schlüsselworts und anderer Verbindungsschlüsselwörter. Die gesamte *$dsn* wird in Anführungszeichen gesetzt, daher sollten die einzelnen Verbindungsschlüsselwörter nicht in separate Anführungszeichen gesetzt werden.  
  
*$username*: Optional. Eine Zeichenfolge, die den Namen des Benutzers enthält. Um eine Verbindung mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung herzustellen, geben Sie die Anmelde-ID an. Um eine Verbindung mithilfe der Windows-Authentifizierung herzustellen, geben Sie `""`an.  
  
*$password*: Optional. Eine Zeichenfolge, die das Kennwort des Benutzers enthält. Um eine Verbindung mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung herzustellen, geben Sie das Kennwort an. Um eine Verbindung mithilfe der Windows-Authentifizierung herzustellen, geben Sie `""`an.  
  
*$Driver_options*: Optional. Sie können Attribute des PDO-Treiber-Managers und bestimmte Attribute des [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]-Treibers angeben, z.B. PDO::SQLSRV_ATTR_ENCODING, PDO::SQLSRV_ATTR_DIRECT_QUERY. Ein ungültiges Attribut generiert keine Ausnahme. Ungültige Attribute generieren Ausnahmen, wenn sie mit [PDO::setAttribute](../../connect/php/pdo-setattribute.md)spezifiziert werden.  
  
## <a name="return-value"></a>Rückgabewert  
Gibt ein PDO-Objekt zurück. Wenn der Fehler auftritt, wird ein PDOException-Objekt zurückgegeben.  
  
## <a name="exceptions"></a>Ausnahmen  
PDOException  
  
## <a name="remarks"></a>Remarks  
Sie können ein Verbindungsobjekt schließen, indem Sie die Instanz auf NULL setzen.  
  
Nach der eine Verbindung wird PDO:: ErrorCode 01000 anstelle von 00000 angezeigt.  
  
Wenn PDO::__construct aus irgendeinem Grund fehlschlägt, wird eine Ausnahme ausgelöst, selbst wenn PDO::ATTR_ERRMODE auf PDO::ERRMODE_SILENT festgelegt ist.  
  
Unterstützung für PDO wurde in Version 2.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]hinzugefügt.  
  
## <a name="example"></a>Beispiel  
Dieses Beispiel zeigt, wie Sie eine Verbindung mit einem Server mithilfe der Windows-Authentifizierung herstellen und eine Datenbank angeben.  
  
```  
<?php  
   $c = new PDO( "sqlsrv:Server=(local) ; Database = AdventureWorks ", "", "", array(PDO::SQLSRV_ATTR_DIRECT_QUERY => true));   
  
   $query = 'SELECT * FROM Person.ContactType';   
   $stmt = $c->query( $query );   
   while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ) {   
      print_r( $row );   
   }  
   $c = null;   
?>  
```  
  
## <a name="example"></a>Beispiel  
Dieses Beispiel zeigt, wie Sie eine Verbindung mit einem Server herstellen und später die Datenbank festlegen.  
  
```  
<?php  
   $c = new PDO( "sqlsrv:server=(local)");  
  
   $c->exec( "USE AdventureWorks");  
   $query = 'SELECT * FROM Person.ContactType';  
   $stmt = $c->query( $query );  
   while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
      print_r( $row );  
   }  
   $c = null;  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[PDO-Klasse](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
