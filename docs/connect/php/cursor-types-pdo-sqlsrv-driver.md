---
title: Cursortypen (PDO_SQLSRV-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/03/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 49ea6a6e-78d4-40f8-85eb-180b527f0537
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c62c2a35123e77f5366dd5348fd51b3c50c85605
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993690"
---
# <a name="cursor-types-pdo_sqlsrv-driver"></a>Cursortypen (PDO_SQLSRV-Treiber)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Mit dem PDO_SQLSRV-Treiber können Sie scrollbare Resultsets mit einem von mehreren Cursor erstellen.

Informationen zum Angeben eines Cursors mithilfe des PDO_SQLSRV-Treibers sowie Codebeispiele finden Sie unter [PDO::prepare](../../connect/php/pdo-prepare.md).

## <a name="pdo_sqlsrv-and-server-side-cursors"></a>PDO_SQLSRV und serverseitige Cursor
Vor Version 3.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] war es möglich, mit dem PDO_SQLSRV-Treiber ein Resultset mit einem serverseitigen Vorwärtscursor oder einem statischen Cursor zu erstellen. Ab Version 3.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] sind auch Keyset- und dynamische Cursor verfügbar.

Mit [PDO::prepare](../../connect/php/pdo-prepare.md) können Sie den Typ des serverseitigen Cursors angeben, indem Sie einen der folgenden Cursortypen auswählen:

-   `PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY`

-   `PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL`

Sie können einen dynamischen, statischen oder Keysetcursor anfordern, indem Sie `PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL` angeben und anschließend den geeigneten Wert an `PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE` übergeben. Die folgenden Werte können für serverseitige Cursor an `PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE` übergeben werden:

-   `PDO::SQLSRV_CURSOR_DYNAMIC`

-   `PDO::SQLSRV_CURSOR_STATIC`

-   `PDO::SQLSRV_CURSOR_KEYSET`

## <a name="pdo_sqlsrv-and-client-side-cursors"></a>PDO_SQLSRV und clientseitige Cursor
Clientseitige Cursor wurden ab Version 3.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] hinzugefügt. Mit ihnen kann ein komplettes Resultset im Arbeitsspeicher zwischengespeichert werden. Ein Vorteil besteht darin, dass die Zeilenanzahl nach dem Ausführen einer Abfrage verfügbar ist.

Clientseitige Cursor eignen sich für kleine bis mittelgroße Resultsets. Für große Resultsets sollten serverseitige Cursor verwendet werden.

Ist der Puffer bei einem clientseitigen Cursor nicht groß genug für ein komplettes Resultset, gibt die Abfrage FALSE zurück. Sie können die Puffergröße bis zur Grenze des PHP-Speichers erhöhen.

Die Größe des Puffers, der das Resultset enthält, kann mithilfe des Attributs `PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE` von [PDO::setAttribute](../../connect/php/pdo-setattribute.md) oder [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md) konfiguriert werden. Die maximale Puffergröße kann auch mit pdo_sqlsrv.client_buffer_max_kb_size (z. B. pdo_sqlsrv.client_buffer_max_kb_size = 1024) in der Datei „php.ini“ festgelegt werden.

Sie können einen clientseitigen Cursor mithilfe von [PDO::prepare](../../connect/php/pdo-prepare.md) anfordern. Geben Sie dafür den Cursortyp `PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL` und anschließend `PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_BUFFERED` an.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird veranschaulicht, wie ein gepufferter Cursor angegeben wird:
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

## <a name="see-also"></a>Weitere Informationen
[Festlegen eines Cursortyps und Zeilenauswahl](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)

