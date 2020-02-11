---
title: Abrufen und Abfragen von XML-Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML data [SQL Server], retrieving
- XML instance retrieval
ms.assetid: 24a28760-1225-42b3-9c89-c9c0332d9c51
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0f556bfccdd117b23db36bb9551e885f4c38614e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63241207"
---
# <a name="retrieve-and-query-xml-data"></a>Abrufen und Abfragen von XML-Daten
  In diesem Thema werden die Abfrageoptionen beschrieben, die für die Abfrage von XML-Daten anzugeben sind. Es beschreibt auch die Teile der XML-Instanzen, die nicht beibehalten werden, wenn sie in Datenbanken gespeichert werden.  
  
##  <a name="features"></a> Funktionen einer XML-Instanz, die nicht beibehalten werden  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] behält den Inhalt der XML-Instanz bei. Allerdings werden die Aspekte der XML-Instanz nicht beibehalten, die im Hinblick auf das XML-Datenmodell als nicht signifikant betrachtet werden. Das bedeutet, dass eine abgerufene XML-Instanz möglicherweise nicht mit der Instanz identisch ist, die auf dem Server gespeichert wurde, aber die gleichen Informationen enthält.  
  
### <a name="xml-declaration"></a>XML-Deklaration  
 Die XML-Deklaration in einer Instanz wird nicht beibehalten, wenn die Instanz in der Datenbank gespeichert wird. Beispiel:  
  
```  
CREATE TABLE T1 (Col1 int primary key, Col2 xml)  
GO  
INSERT INTO T1 values (1, '<?xml version="1.0" encoding="windows-1252" ?><doc></doc>')  
GO  
SELECT Col2  
FROM T1  
```  
  
 Das Ergebnis ist `<doc/>`.  
  
 Die XML-Deklaration, z. B. `<?xml version='1.0'?>`, wird nicht beibehalten, wenn die XML-Daten in einer `xml`-Datentypinstanz gespeichert werden. Dies ist beabsichtigt. Die XML-Deklaration () und die zugehörigen Attribute (Version/Codierung/eigenständige) gehen verloren, nachdem Daten in `xml`den Typ konvertiert wurden. Die XML-Deklaration wird als Direktive für den XML-Parser behandelt. Die XML-Daten werden intern als ucs-2 gespeichert. Alle anderen PIs in der XML-Instanz werden beibehalten.  
  
  
### <a name="order-of-attributes"></a>Reihenfolge von Attributen  
 Die Reihenfolge der Attribute in einer XML-Instanz wird nicht erhalten. Bei einer Abfrage der in der `xml`-Typspalte gespeicherten XML-Instanz kann die Reihenfolge der Attribute in der resultierenden XML von der der ursprünglichen XML-Instanz abweichen.  
  
  
### <a name="quotation-marks-around-attribute-values"></a>Anführungszeichen um Attributwerte  
 Einfache Anführungszeichen und doppelte Anführungszeichen um Attributwerte werden nicht erhalten. Die Attributwerte werden in der Datenbank als Name/Wert-Paar gespeichert. Die Anführungszeichen werden nicht gespeichert. Wenn eine XQuery-Abfrage für eine XML-Instanz ausgeführt wird, wird die resultierende XML mit doppelten Anführungszeichen um die Attributwerte serialisiert.  
  
```  
DECLARE @x xml  
-- Use double quotation marks.  
SET @x = '<root a="1" />'  
SELECT @x  
GO  
DECLARE @x xml  
-- Use single quotation marks.  
SET @x = '<root a=''1'' />'  
SELECT @x  
GO  
```  
  
 Für beide Abfragen wird Folgendes zurückgeben: = `<root a="1" />`.  
  
  
### <a name="namespace-prefixes"></a>Namespacepräfixe  
 Namespacepräfixe werden nicht erhalten. Wenn Sie eine XQuery-Abfrage für eine `xml`-Typspalte angeben, werden vom serialisierten XML-Ergebnis möglicherweise andere Namespacepräfixe zurückgeben.  
  
```  
DECLARE @x xml  
SET @x = '<ns1:root xmlns:ns1="abc" xmlns:ns2="abc">  
            <ns2:SomeElement/>  
          </ns1:root>'  
SELECT @x  
SELECT @x.query('/*')  
GO  
```  
  
 Das Namespacepräfix des Ergebnisses kann unterschiedlich sein. Beispiel:  
  
```  
<p1:root xmlns:p1="abc"><p1:SomeElement/></p1:root>  
```  
  
  
##  <a name="query"></a> Festlegen der erforderlichen Abfrageoptionen  
 Beim Abfragen von `xml` Typspalten oder Variablen mithilfe `xml` von-Datentyp Methoden müssen die folgenden Optionen wie dargestellt festgelegt werden.  
  
|SET-Optionen|Erforderliche Werte|  
|-----------------|---------------------|  
|ANSI_NULLS|EIN|  
|ANSI_PADDING|EIN|  
|ANSI_WARNINGS|EIN|  
|ARITHABORT|EIN|  
|CONCAT_NULL_YIELDS_NULL|EIN|  
|NUMERIC_ROUNDABORT|OFF|  
|QUOTED_IDENTIFIER|EIN|  
  
 Wenn die Optionen nicht wie dargestellt festgelegt sind, schlagen Abfragen und `xml` Änderungen an Datentyp Methoden fehl.  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Instanzen der XML-Daten](create-instances-of-xml-data.md)  
  
  
