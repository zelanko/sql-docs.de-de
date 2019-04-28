---
title: Einführung in die XML-Massenladen (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e81a952e72875353880bff0367389ce7139932d2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62717513"
---
# <a name="introduction-to-xml-bulk-load-sqlxml-40"></a>Einführung in XML-Massenladen (SQLXML 4.0)
  XML-Massenladen ist ein eigenständiges COM-Objekt, das Ihnen ermöglicht, laden semistrukturierte XML-Daten in Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tabellen.  
  
 Sie können XML-Daten in eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank einfügen, indem Sie eine INSERT-Anweisung und die OPENXML-Funktion verwenden. Das Massenladen-Hilfsprogramm zeigt jedoch eine bessere Leistung beim Einfügen großer XML-Datenmengen.  
  
 Die Execute-Methode des XML-Massenladen-Objektmodells verwendet zwei Parameter:  
  
-   Eine XML-Schemadefinition (XSD) mit Anmerkungen oder ein XDR-Schema (XML-Data Reduced). Das XML-Massenladen-Hilfsprogramm interpretiert dieses Zuordnungsschema und die im Schema angegebenen Anmerkungen durch Identifizieren der SQL Server-Tabellen, in die die XML-Daten eingefügt werden sollen.  
  
-   Ein XML-Dokument oder Dokumentfragment (ein Dokumentfragment ist ein Dokument ohne Einzelelement auf der obersten Ebene). Sie können einen Dateinamen oder einen Datenstrom angeben, von dem XML-Massenladen lesen kann.  
  
 Das XML-Massenladen-Hilfsprogramm interpretiert das Zuordnungsschema und identifiziert die Tabelle(n), in die die XML-Daten eingefügt werden soll(en).  
  
 Es wird vorausgesetzt, dass Sie mit den folgenden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Funktionen vertraut sind:  
  
-   XSD- und XDR-Schemas mit Anmerkungen Weitere Informationen über XSD-Schemas mit Anmerkungen finden Sie unter [Einführung in XSD-Schemas mit Anmerkungen &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md). Weitere Informationen über XDR-Schemas mit Anmerkungen finden Sie unter [mit Anmerkungen versehene XDR-Schemas &#40;in SQLXML 4.0 veraltet&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Masseneinfügemechanismen, z. B. die [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT-Anweisung und das bcp-Hilfsprogramm. Weitere Informationen finden Sie unter [BULK INSERT &#40;Transact-SQL&#41; ](/sql/t-sql/statements/bulk-insert-transact-sql) und [Hilfsprogramm "Bcp"](../../../tools/bcp-utility.md).  
  
## <a name="streaming-of-xml-data"></a>Streamen von XML-Daten  
 Da das XML-Quelldokument unter Umständen groß ist, wird das gesamte Dokument für die Massenladenverarbeitung nicht in den Speicher gelesen. Stattdessen interpretiert XML-Massenladen die XML-Daten als Datenstrom und liest diesen. Während das Hilfsprogramm die Daten liest, identifiziert es die Datenbanktabelle(n), generiert den entsprechenden Datensatz bzw. Datensätze aus der XML-Datenquelle und sendet den Datensatz bzw. die Datensätze zum Einfügen an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Beispielsweise besteht der folgende XML-Quelldokument  **\<Kunden >** Elemente und  **\<Reihenfolge >** untergeordnete Elemente:  
  
```  
<Customer ...>  
    <Order.../>  
    <Order .../>  
     ...  
</Customer>  
...  
```  
  
 Als XML-Massenladen liest die  **\<Kunden >** -Element, generiert es einen Datensatz für die Kundentabelle. Beim Lesen der  **\</Customer >** -Endtag fügt XML-Massenladen, die in die Tabelle aufzeichnen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. In der gleichen Weise beim Lesen der  **\<Reihenfolge >** -Element, XML-Massenladen generiert einen Datensatz für die Ordertable und fügt dann diesen Datensatz in die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tabelle beim Lesen der  **\< / Order >** Endtag.  
  
## <a name="transacted-and-nontransacted-xml-bulk-load-operations"></a>Transaktive und nicht durchgeführte XML-Massenladevorgänge  
 XML-Massenladen kann entweder in einem transaktiven oder einem nicht durchgeführten Modus operieren. Leistung ist in der Regel optimal, wenn Sie beim Massenladen in einem nicht durchgeführten Modus sind: d. h. die Transaktionseigenschaft auf "false" festgelegt ist) und eine der folgenden Bedingungen zutrifft:  
  
-   Die Tabellen, in die die Daten massengeladen werden, sind leer und ohne Indizes.  
  
-   Die Tabellen weisen Daten und eindeutige Indizes auf.  
  
 Der nicht durchgeführte Ansatz garantiert keinen Rollback, wenn beim Massenladen ein Fehler auftritt (Teilrollbacks sind allerdings möglich). Das nicht durchgeführte Massenladen ist geeignet, wenn die Datenbank leer ist. Wenn ein Fehler auftritt, können Sie so die Datenbank bereinigen und das XML-Massenladen erneut starten.  
  
> [!NOTE]  
>  Im nicht durchgeführten Modus verwendet XML-Massenladen eine interne Standardtransaktion und führt einen Commit dafür aus. Wenn die Transaktionseigenschaft auf "true" festgelegt ist, ruft XML-Massenladen nicht Commit für diese Transaktion auf.  
  
 Wenn die Transaktionseigenschaft auf "true" festgelegt ist, erstellt der XML-Massenladen temporäre Dateien, eins für jede Tabelle, die im Zuordnungsschema identifiziert wird. XML-Massenladen speichert zunächst die Datensätze aus dem XML-Quelldokument in diesen temporären Dateien. Anschließend ruft eine [!INCLUDE[tsql](../../../includes/tsql-md.md)] BULK INSERT-Anweisung diese Datensätze aus den Dateien ab und speichert sie in den entsprechenden Tabellen. Sie können den Speicherort für die temporären Dateien angeben, über die TempFilePath-Eigenschaft. Das für XML-Massenladen verwendete [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konto muss auf diesen Pfad zugreifen können. Wenn die TempFilePath-Eigenschaft nicht angegeben ist, wird der Standardpfad für die Datei, der in der Umgebungsvariablen TEMP angegeben wird zum Erstellen der temporären Dateien.  
  
 Wenn die Transaktionseigenschaft auf "false" (die Standardeinstellung) festgelegt ist, verwendet das XML-Massenladen die OLE DB-Schnittstelle IRowsetFastLoad für das Massenladen der Daten.  
  
 Wenn die ConnectionString-Eigenschaft legt die Verbindungszeichenfolge fest, und die Transaktionseigenschaft auf "true" festgelegt ist, gibt es XML-Massenladen in einem eigenen Transaktionskontext. (Zum Beispiel startet XML-Massenladen eine eigene Transaktion und führt ggf. einen Commit oder Rollback aus.)  
  
 Wenn bei der "connectioncommand"-Eigenschaft die Verbindung mit einem vorhandenen Verbindungsobjekt und die Transaktionseigenschaft auf "true" festgelegt ist, XML-Massenladevorgang gibt keine aus einer Commit- oder ROLLBACK-Anweisung im Erfolgsfall oder ein Fehler auftritt, bzw. Tritt ein Fehler auf, gibt XML-Massenladen die entsprechende Fehlermeldung zurück. Die Entscheidung, ob eine COMMIT- oder ROLLBACK-Anweisung ausgegeben wird, obliegt dem Client, der das Massenladen gestartet hat. Das Verbindungsobjekt, das für XML-Massenladen verwendet wird oder sein soll vom Typ ICommand ein ADO-Befehlsobjekt.  
  
 In SQLXML 4.0 kann eine ConnectionObject den Transaktionssatz-Eigenschaft auf "false" verwendet werden. Der nicht durchgeführte Modus wird nicht mit einem ConnectionObject unterstützt, da es unmöglich ist, mehr als eine IRowsetFastLoad-Schnittstelle für eine übergebene Sitzung zu öffnen.  
  
  
