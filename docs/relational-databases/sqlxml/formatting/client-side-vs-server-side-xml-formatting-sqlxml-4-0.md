---
title: Client seitige und Server seitige XML-Formatierung (SQLXML)
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- NESTED mode
- FOR XML clause, formatting
- client-side XML formatting
- server-side XPath
- server-side XML formatting
- AUTO mode
- client-side XPath
ms.assetid: f807ab7a-c5f8-4e61-9b00-23aebfabc47e
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 421c48590098f9dbf4ce075c213fcd1cda720649
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75247012"
---
# <a name="client-side-vs-server-side-xml-formatting-sqlxml-40"></a>Clientseitige im Vergleich zur serverseitigen XML-Formatierung (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In diesem Thema werden die allgemeinen Unterschiede zwischen clientseitiger und serverseitiger XML-Formatierung in SQLXML beschrieben.  
  
## <a name="multiple-rowset-queries-not-supported-in-client-side-formatting"></a>Keine Unterstützung von mehreren Rowset-Abfragen bei der clientseitigen Formatierung  
 Abfragen, die mehrere Rowsets generieren, werden bei einer clientseitigen XML-Formatierung nicht unterstützt. Beispiel: Sie haben ein virtuelles Verzeichnis, für das eine clientseitige Formatierung angegeben wurde. Beachten Sie diese Beispiel Vorlage mit zwei SELECT-Anweisungen in einem ** \<SQL: Query>** -Block:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query>  
     SELECT FirstName FROM Person.Contact FOR XML Nested;   
     SELECT LastName FROM Person.Contact FOR XML Nested    
  </sql:query>  
</ROOT>  
```  
  
 Sie können diese Vorlage im Anwendungscode ausführen, es wird ein Fehler zurückgegeben, da die clientseitige XML-Formatierung keine Formatierung mehrerer Rowsets unterstützt. Wenn Sie die Abfragen in zwei separaten ** \<SQL: Query>** -Blöcken angeben, erhalten Sie die gewünschten Ergebnisse.  
  
## <a name="timestamp-maps-differently-in-client--vs-server-side-formatting"></a>Unterschiedliche timestamp-Zuordnungen bei der client- und serverseitigen Formatierung  
 Bei der serverseitigen XML-Formatierung wird die Daten Bank Spalte des **Zeitstempel** -Typs dem I8 XDR-Typ zugeordnet (wenn die XMLDATA-Option in der Abfrage angegeben ist).  
  
 Bei der Client seitigen XML-Formatierung wird die Daten Bank Spalte des **Zeitstempel** -Typs entweder dem **URI** oder dem **bin. base64** -XDR-Typ zugeordnet (abhängig davon, ob die binäre Base64-Option in der Abfrage angegeben ist). Der Typ " **bin. base64** XDR" ist nützlich, wenn Sie die Features "Update Gram" und "Bulkload" verwenden, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] da dieser Typ in den **Zeitstempel** -Typ konvertiert wird. Auf diese Art werden die Einfüge-, Update- oder Löschvorgänge erfolgreich abgeschlossen.  
  
## <a name="deep-variants-are-used-in-server-side-formatting"></a>Bei serverseitiger Formatierung werden tiefe VARIANTs verwendet  
 Bei der serverseitigen XML-Formatierung werden tiefe Typen eines VARIANT-Typs verwendet. Bei der clientseitigen XML-Formatierung werden die Varianten in Unicode-Zeichenfolgen konvertiert und die Untertypen von VARIANT werden nicht verwendet.  
  
## <a name="nested-mode-vs-auto-mode"></a>NESTED-Modus im Vergleich zum AUTO-Modus  
 Der NESTED-Modus des clientseitigen FOR XML ähnelt dem AUTO-Modus des serverseitigen FOR XML. Ausnahmen:  
  
### <a name="when-you-query-views-using-auto-mode-on-the-server-side-the-view-name-is-returned-as-the-element-name-in-the-resulting-xml"></a>Wenn Sie Sichten mit AUTO-Modus serverseitig abfragen, wird der Sichtname als Elementname in der resultierenden XML zurückgegeben.  
 Nehmen Sie beispielsweise an, dass die folgende Ansicht für die Person. Contact-Tabelle in der adventureworksdatabase-Datenbank erstellt wird:  
  
```  
CREATE VIEW ContactView AS (SELECT ContactID as CID,  
                               FirstName  as FName,  
                               LastName  as LName  
                        FROM Person.Contact)  
```  
  
 Die folgende Vorlage gibt eine Abfrage der ContactView-Sicht und die serverseitige XML-Formatierung an:  
  
```  
 <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT *  
    FROM   ContactView  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 Wenn Sie die Vorlage ausführen, wird die folgende XML zurückgegeben. (Es werden nur partielle Ergebnisse angezeigt.) Beachten Sie, dass die Elementnamen die Namen der Sichten sind, für die die Abfrage ausgeführt wird.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <ContactView CID="1" FName="Gustavo" LName="Achong" />   
  <ContactView CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
 Wenn Sie die clientseitige XML-Formatierung mit dem entsprechenden NESTED-Modus angeben, werden die Basistabellennamen als Elementnamen in der resultierenden XML zurückgegeben. Beispielsweise führt die folgende überarbeitete Vorlage dieselbe SELECT-Anweisung aus, die XML-Formatierung wird jedoch auf der Clientseite ausgeführt (d. h., **Client-Side-XML** wird in der Vorlage auf true festgelegt):  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT *  
    FROM   ContactView  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 Durch die Ausführung der Vorlage wird die folgende XML erstellt. Beachten Sie, dass in diesem Fall der Elementname der Basistabellenname ist.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact CID="1" FName="Gustavo" LName="Achong" />   
  <Person.Contact CID="2" FName="Catherine" LName="Abel" />   
...  
</ROOT>  
```  
  
### <a name="when-you-use-auto-mode-of-the-server-side-for-xml-the-table-aliases-specified-in-the-query-are-returned-as-element-names-in-the-resulting-xml"></a>Wenn Sie den AUTO-Modus des serverseitigen FOR XML verwenden, werden die in der Abfrage angegebenen Tabellenaliasse als Elementnamen in der resultierenden XML zurückgegeben.  
 Betrachten Sie z. B. die folgende Vorlage:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="0">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML AUTO  
  </sql:query>  
</ROOT>  
```  
  
 Durch die Ausführung der Vorlage wird die folgende XML erstellt:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <C fname="Gustavo" lname="Achong" />   
  <C fname="Catherine" lname="Abel" />   
...  
</ROOT>   
```  
  
 Wenn Sie den NESTED-Modus des clientseitigen FOR XML verwenden, werden die Tabellennamen als Elementnamen in der resultierenden XML zurückgegeben. (Tabellen Aliase, die in der Abfrage angegeben werden, werden nicht verwendet.) Sehen Sie sich beispielsweise die folgende Vorlage an:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:query client-side-xml="1">  
    SELECT FirstName as fname,  
           LastName as lname  
    FROM   Person.Contact C  
    FOR XML NESTED  
  </sql:query>  
</ROOT>  
```  
  
 Durch die Ausführung der Vorlage wird die folgende XML erstellt:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact fname="Gustavo" lname="Achong" />   
  <Person.Contact fname="Catherine" lname="Abel" />   
...  
</ROOT>  
```  
  
### <a name="if-you-have-a-query-that-returns-columns-as-dbobject-queries-you-cannot-use-aliases-for-these-columns"></a>Wenn eine Abfrage Spalten als dbobject-Abfragen zurückgibt, können Sie keine Aliasse für diese Spalten verwenden.  
 Die folgende Vorlage führt beispielsweise eine Abfrage aus, die eine Mitarbeiter-ID und ein Foto zurückgibt.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query client-side-xml="1">  
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML NESTED, elements  
</sql:query>  
</ROOT>  
```  
  
 Wenn Sie diese Vorlage ausführen, wird die Photo-Spalte als eine dbobject-Abfrage zurückgegeben. In dieser dbobject-Abfrage verweist `@P` auf einen Spaltennamen, der nicht existiert.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@P</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
 Wenn die XML-Formatierung auf dem Server (**Client-Side-XML = "0"**) ausgeführt wird, können Sie den Alias für die Spalten verwenden, die dbobject-Abfragen zurückgeben, in denen tatsächliche Tabellen-und Spaltennamen zurückgegeben werden (auch wenn Sie Aliase angegeben haben). Die folgende Vorlage führt z. b. eine Abfrage aus, und die XML-Formatierung erfolgt auf dem Server (die **Client seitige XML-** Option ist nicht angegeben, und die Option **auf Client ausführen** ist für das virtuelle Stammverzeichnis nicht ausgewählt). Die Abfrage gibt auch den AUTO-Modus an (nicht den clientseitigen NESTED-Modus).  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<sql:query   
   SELECT ProductPhotoID, LargePhoto as P  
   FROM   Production.ProductPhoto  
   WHERE  ProductPhotoID=5  
   FOR XML AUTO, elements  
</sql:query>  
</ROOT>  
```  
  
 Wenn diese Vorlage ausgeführt wird, wird das folgende XML-Dokument zurückgegeben (beachten Sie, dass die Aliasse nicht in der dbobject-Abfrage für die LargePhoto-Spalte verwendet werden):  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Production.ProductPhoto>  
    <ProductPhotoID>5</ProductPhotoID>  
    <LargePhoto>dbobject/Production.ProductPhoto[@ProductPhotoID='5']/@LargePhoto</LargePhoto>  
  </Production.ProductPhoto>  
</ROOT>  
```  
  
### <a name="client-side-vs-server-side-xpath"></a>Clientseitiger im Vergleich zu serverseitigem XPath  
 Clientseitiger XPath und serverseitiger XPath funktionieren gleichermaßen, weisen jedoch die folgenden Unterschiede auf:  
  
-   Die Datenkonvertierungen, die angewendet werden, wenn Sie clientseitige XPath-Abfragen verwenden, unterscheiden sich von jenen, die angewendet werden, wenn Sie serverseitige XPath-Abfragen verwenden. Clientseitiger XPath verwendet CAST anstelle von CONVERT-Modus 126.  
  
-   Wenn Sie **Client-Side-XML = "0"** (false) in einer Vorlage angeben, fordern Sie die serverseitige XML-Formatierung an. Sie können somit nicht FOR XML NESTED angeben, da der Server die NESTED-Option nicht erkennt. In diesem Fall wird ein Fehler generiert. Sie müssen die Modi AUTO, RAW oder EXPLICIT verwenden, die der Server erkennt.  
  
-   Wenn Sie **Client-Side-XML = "1"** (true) in einer Vorlage angeben, fordern Sie eine Client seitige XML-Formatierung an. In diesem Fall können Sie FOR XML NESTED angeben. Wenn Sie for XML Auto angeben, erfolgt die XML-Formatierung auf der Serverseite, obwohl **Client-Side-XML = "1"** in der Vorlage angegeben ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zu den XML-Sicherheitsüberlegungen &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/for-xml-security-considerations-sqlxml-4-0.md)   
 [Client seitige XML-Formatierung &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)   
 [Server seitige XML-Formatierung &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/formatting/server-side-xml-formatting-sqlxml-4-0.md)  
  
  
