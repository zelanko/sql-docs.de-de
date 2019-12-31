---
title: Einführung in XML-Massen laden (SQLXML)
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nontransacted XML Bulk Load operations
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
- transacted XML Bulk Load operations
- streaming XML data
ms.assetid: 38bd3cbd-65ef-4c23-9ef3-e70ecf6bb88a
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4116bef21a70e6de699046019fd404798826bf18
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75246739"
---
# <a name="introduction-to-xml-bulk-load-sqlxml-40"></a>Einführung in XML-Massenladen (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Beim XML-Massen laden handelt es sich um ein eigenständiges com-Objekt, mit dem Sie semistrukturierte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML-Daten in Microsoft-Tabellen laden können.  
  
 Sie können XML-Daten in eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank einfügen, indem Sie eine INSERT-Anweisung und die OPENXML-Funktion verwenden. Das Massenladen-Hilfsprogramm zeigt jedoch eine bessere Leistung beim Einfügen großer XML-Datenmengen.  
  
 Die Execute-Methode des XML-Massen laden-Objektmodells nimmt zwei Parameter an:  
  
-   Eine XML-Schemadefinition (XSD) mit Anmerkungen oder ein XDR-Schema (XML-Data Reduced). Das XML-Massenladen-Hilfsprogramm interpretiert dieses Zuordnungsschema und die im Schema angegebenen Anmerkungen durch Identifizieren der SQL Server-Tabellen, in die die XML-Daten eingefügt werden sollen.  
  
-   Ein XML-Dokument oder Dokumentfragment (ein Dokumentfragment ist ein Dokument ohne Einzelelement auf der obersten Ebene). Sie können einen Dateinamen oder einen Datenstrom angeben, von dem XML-Massenladen lesen kann.  
  
 Das XML-Massenladen-Hilfsprogramm interpretiert das Zuordnungsschema und identifiziert die Tabelle(n), in die die XML-Daten eingefügt werden soll(en).  
  
 Es wird vorausgesetzt, dass Sie mit den folgenden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Funktionen vertraut sind:  
  
-   XSD- und XDR-Schemas mit Anmerkungen Weitere Informationen zu XSD-Schemas mit Anmerkungen finden Sie unter [Einführung in XSD-Schemas mit Anmerkungen &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md). Informationen zu XDR-Schemas mit Anmerkungen finden Sie unter [mit Anmerkungen versehene XDR-Schemas &#40;in SQLXML 4,0&#41;veraltet ](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
-   
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Masseneinfügemechanismen, z. B. die [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT-Anweisung und das bcp-Hilfsprogramm. Weitere Informationen finden Sie unter [Bulk Insert &#40;Transact-SQL-&#41;](../../../t-sql/statements/bulk-insert-transact-sql.md) und [bcp-Hilfsprogramm](../../../tools/bcp-utility.md).  
  
## <a name="streaming-of-xml-data"></a>Streaming von XML-Daten  
 Da das XML-Quelldokument unter Umständen groß ist, wird das gesamte Dokument für die Massenladenverarbeitung nicht in den Speicher gelesen. Stattdessen interpretiert XML-Massenladen die XML-Daten als Datenstrom und liest diesen. Während das Hilfsprogramm die Daten liest, identifiziert es die Datenbanktabelle(n), generiert den entsprechenden Datensatz bzw. Datensätze aus der XML-Datenquelle und sendet den Datensatz bzw. die Datensätze zum Einfügen an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Das folgende XML-Quelldokument besteht z. b. aus ** \<Kunden>** Elementen und ** \<Order>** untergeordneten Elementen:  
  
```  
<Customer ...>  
    <Order.../>  
    <Order .../>  
     ...  
</Customer>  
...  
```  
  
 Wenn das XML-Massen laden das ** \<Customer->** Element liest, generiert es einen Datensatz für die CustomerTable. Beim Lesen des ** \</Customer->** Endtags fügt XML-Massen laden diesen Datensatz in die Tabelle in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ein. Auf dieselbe Weise generiert XML-Massen Laden beim Lesen des ** \<Order>** -Elements einen Datensatz für ordertable und fügt diesen Datensatz beim Lesen des ** \</Order->** Endtags in die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tabelle ein.  
  
## <a name="transacted-and-nontransacted-xml-bulk-load-operations"></a>Transaktive und nicht durchgeführte XML-Massenladevorgänge  
 XML-Massenladen kann entweder in einem transaktiven oder einem nicht durchgeführten Modus operieren. Die Leistung ist in der Regel optimal, wenn Sie ein Massen laden in einem nicht transaktiven Modus ausführen, das heißt, die Transaction-Eigenschaft ist auf false festgelegt, und eine der folgenden Bedingungen ist erfüllt:  
  
-   Die Tabellen, in die die Daten massengeladen werden, sind leer und ohne Indizes.  
  
-   Die Tabellen weisen Daten und eindeutige Indizes auf.  
  
 Der nicht durchgeführte Ansatz garantiert keinen Rollback, wenn beim Massenladen ein Fehler auftritt (Teilrollbacks sind allerdings möglich). Das nicht durchgeführte Massenladen ist geeignet, wenn die Datenbank leer ist. Wenn ein Fehler auftritt, können Sie so die Datenbank bereinigen und das XML-Massenladen erneut starten.  
  
> [!NOTE]  
>  Im nicht durchgeführten Modus verwendet XML-Massenladen eine interne Standardtransaktion und führt einen Commit dafür aus. Wenn die Transaction-Eigenschaft auf true festgelegt ist, ruft der XML-Massen Ladevorgang für diese Transaktion keinen Commit auf.  
  
 Wenn die Transaction-Eigenschaft auf true festgelegt ist, erstellt das XML-Massen laden temporäre Dateien, eine für jede Tabelle, die im Zuordnungsschema identifiziert wird. XML-Massenladen speichert zunächst die Datensätze aus dem XML-Quelldokument in diesen temporären Dateien. Anschließend ruft eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT-Anweisung diese Datensätze aus den Dateien ab und speichert sie in den entsprechenden Tabellen. Sie können den Speicherort für diese temporären Dateien mithilfe der TempFilePath-Eigenschaft angeben. Das für XML-Massenladen verwendete [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konto muss auf diesen Pfad zugreifen können. Wenn die TempFilePath-Eigenschaft nicht angegeben ist, wird der in der TEMP-Umgebungsvariablen angegebene Standard Dateipfad zum Erstellen der temporären Dateien verwendet.  
  
 Wenn die Transaction-Eigenschaft auf false festgelegt ist (Standardeinstellung), verwendet XML-Massen laden die OLE DB-Schnittstelle IRowsetFastLoad zum Massen Laden der Daten.  
  
 Wenn die ConnectionString-Eigenschaft die Verbindungs Zeichenfolge festlegt und die Transaction-Eigenschaft auf true festgelegt ist, wird das XML-Massen laden in einem eigenen Transaktionskontext betrieben. (Zum Beispiel startet XML-Massenladen eine eigene Transaktion und führt ggf. einen Commit oder Rollback aus.)  
  
 Wenn die ConnectionCommand-Eigenschaft die Verbindung mit einem vorhandenen Verbindungs Objekt festlegt und die Transaction-Eigenschaft auf true festgelegt ist, gibt das XML-Massen laden keine Commit-oder Rollback-Anweisung im Falle eines Erfolgs oder Fehlers aus. Tritt ein Fehler auf, gibt XML-Massenladen die entsprechende Fehlermeldung zurück. Die Entscheidung, ob eine COMMIT- oder ROLLBACK-Anweisung ausgegeben wird, obliegt dem Client, der das Massenladen gestartet hat. Das Verbindungs Objekt, das für XML-Massen Laden verwendet wird, muss vom Typ ICommand oder ein ADO-Befehls Objekt sein.  
  
 In SQLXML 4,0 kann ein ConnectionObject nicht verwendet werden, wenn die Transaction-Eigenschaft auf false festgelegt ist. Der nicht transaktive Modus wird mit einem ConnectionObject nicht unterstützt, da es nicht möglich ist, mehr als eine IRowsetFastLoad-Schnittstelle für eine übergebenen Sitzung zu öffnen.  
  
  
