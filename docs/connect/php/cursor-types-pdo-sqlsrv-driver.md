---
title: Cursortypen (PDO_SQLSRV-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 49ea6a6e-78d4-40f8-85eb-180b527f0537
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72cf83b4c4903c7df0b6a857746937e848fccf80
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38062357"
---
# <a name="cursor-types-pdosqlsrv-driver"></a>Cursortypen (PDO_SQLSRV-Treiber)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Der PDO_SQLSRV-Treiber können Sie die scrollfähigen Resultsets mit mehreren Cursor erstellen.  
  
Informationen zum Angeben eines Cursors, der mit dem PDO_SQLSRV-Treiber und Codebeispiele, finden Sie unter [PDO:: Prepare](../../connect/php/pdo-prepare.md).  
  
## <a name="pdosqlsrv-and-server-side-cursors"></a>PDO_SQLSRV und serverseitiger Cursor  
Vor Version 3.0, der die [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], der PDO_SQLSRV-Treiber konnten Sie ein Resultset mit einem serverseitigen Vorwärtscursor oder statische Cursor erstellen. Ab Version 3.0 von der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], keysetgesteuerte und dynamische Cursor sind auch verfügbar.  
  
Sie können den Typ des serverseitigen Cursor angeben, indem Sie mithilfe von PDO:: Prepare oder pdostatement:: setAttribute entweder Cursortyp auswählen:  
  
-   PDO:: ATTR_CURSOR = &GT; PDO:: CURSOR_FWDONLY  
  
-   PDO:: ATTR_CURSOR = &GT; CURSOR_SCROLL  
  
Sie können ein Keyset oder dynamic-Cursor durch Angeben von PDO:: attr_cursor anfordern = > cursor_scroll und übergeben Sie den entsprechenden Wert zu sqlsrv_attr_cursor_scroll_type. Mögliche Werte, die an sqlsrv_attr_cursor_scroll_type übergeben werden können, sind:  
  
-   PDO::SQLSRV_CURSOR_BUFFERED  
  
-   PDO::SQLSRV_CURSOR_DYNAMIC  
  
-   PDO::SQLSRV_CURSOR_KEYSET_DRIVEN  
  
-   PDO::SQLSRV_CURSOR_STATIC  
  
## <a name="pdosqlsrv-and-client-side-cursors"></a>PDO_SQLSRV und clientseitigen Cursorn  
Clientseitige Cursor wurden hinzugefügt, Version 3.0 der der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] , mit der Sie ein komplettes Resultset im Arbeitsspeicher zwischengespeichert. Ein Vorteil ist, dass die Zeilenanzahl verfügbar ist, nachdem eine Abfrage ausgeführt wird.  
  
Clientseitige Cursor sollte für kleine-mittelgroße Resultsets verwendet werden. Umfangreichen Resultsets sollten serverseitige Cursor verwenden.  
  
Eine Abfrage zurückgeben wird "false", wenn der Puffer nicht groß genug für einen kompletten Ergebnissatz, wenn Sie einen clientseitigen Cursor zu verwenden ist. Sie können die Größe des Puffers bis zu PHP-Speichergrenze erhöhen.  
  
Sie können konfigurieren, dass die Größe des Puffers, das Resultset mit dem Attribut PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE von enthält [PDO:: setAttribute](../../connect/php/pdo-setattribute.md) oder [pdostatement:: setAttribute](../../connect/php/pdostatement-setattribute.md). Sie können auch die maximale Puffergröße in der Datei "PHP.ini" mit pdo_sqlsrv.client_buffer_max_kb_size festlegen (z. B. pdo_sqlsrv.client_buffer_max_kb_size = 1024).  
  
Sie angeben, dass Sie einen clientseitigen Cursor mithilfe von PDO:: Prepare oder pdostatement:: setAttribute werden soll, und wählen die PDO:: attr_cursor = > cursor_scroll Cursortyp.  Geben Sie dann sqlsrv_attr_cursor_scroll_type = > PDO::SQLSRV_CURSOR_BUFFERED.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_BUFFERED));  
$stmt->execute();  
print $stmt->rowCount();  
  
echo "\n";  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
echo "\n..\n";  
  
$row = $stmt->fetch( PDO::FETCH_BOTH, PDO::FETCH_ORI_FIRST );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_ASSOC, PDO::FETCH_ORI_REL, 1 );  
print "$row[Name]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_NEXT );  
print "$row[1]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_PRIOR );  
print "$row[1]..\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_ABS, 0 );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_LAST );  
print_r($row);  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Festlegen eines Cursortyps und Zeilenauswahl](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)  
  
