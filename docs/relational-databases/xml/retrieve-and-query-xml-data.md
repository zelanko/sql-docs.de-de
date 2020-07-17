---
title: Abrufen und Abfragen von XML-Daten | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Optionen, die beim Abfragen von XML-Daten angegeben werden müssen, sowie darüber, welche Bestandteile von XML-Instanzen beim Speichern in Datenbanken nicht beibehalten werden.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XML data [SQL Server], retrieving
- XML instance retrieval
ms.assetid: 24a28760-1225-42b3-9c89-c9c0332d9c51
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 86f908d6aa221b2c69be3d8960efac929cbf5306
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85738399"
---
# <a name="retrieve-and-query-xml-data"></a>Abrufen und Abfragen von XML-Daten
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  In diesem Thema werden die Abfrageoptionen beschrieben, die für die Abfrage von XML-Daten anzugeben sind. Es beschreibt auch die Teile der XML-Instanzen, die nicht beibehalten werden, wenn sie in Datenbanken gespeichert werden.  
  
##  <a name="features-of-an-xml-instance-that-are-not-preserved"></a><a name="features"></a> Funktionen einer XML-Instanz, die nicht beibehalten werden  
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
  
 Die XML-Deklaration, z. B. `<?xml version='1.0'?>`, wird nicht beibehalten, wenn die XML-Daten in einer **xml** -Datentypinstanz gespeichert werden. Dies ist beabsichtigt. Die XML-Deklaration () und die Attribute (Version/Codierung/Eigenständigkeit) gehen bei der Konvertierung in den Typ **xml**verloren. Die XML-Deklaration wird als Direktive für den XML-Parser behandelt. Die XML-Daten werden intern als ucs-2 gespeichert. Alle anderen PIs in der XML-Instanz werden beibehalten.  
  
  
### <a name="order-of-attributes"></a>Reihenfolge von Attributen  
 Die Reihenfolge der Attribute in einer XML-Instanz wird nicht erhalten. Bei einer Abfrage der in der **xml** -Typspalte gespeicherten XML-Instanz kann die Reihenfolge der Attribute in der resultierenden XML von der der ursprünglichen XML-Instanz abweichen.  
  
  
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
 Namespacepräfixe werden nicht erhalten. Wenn Sie eine XQuery-Abfrage für eine **xml** -Typspalte angeben, werden vom serialisierten XML-Ergebnis möglicherweise andere Namespacepräfixe zurückgeben.  
  
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
  
  
##  <a name="setting-required-query-options"></a><a name="query"></a> Festlegen der erforderlichen Abfrageoptionen  
 Beim Abfragen von Spalten oder Variablen des **xml** -Datentyps mithilfe von **xml** -Datentypmethoden müssen die folgenden Optionen wie dargestellt festgelegt werden.  
  
|SET-Optionen|Erforderliche Werte|  
|-----------------|---------------------|  
|ANSI_NULLS|EIN|  
|ANSI_PADDING|EIN|  
|ANSI_WARNINGS|EIN|  
|ARITHABORT|EIN|  
|CONCAT_NULL_YIELDS_NULL|EIN|  
|NUMERIC_ROUNDABORT|OFF|  
|QUOTED_IDENTIFIER|EIN|  
  
 Wenn die Optionen nicht wie dargestellt festgelegt sind, schlagen Abfragen und Änderungen für **xml** -Datentypmethoden fehl.  
  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Instanzen der XML-Daten](../../relational-databases/xml/create-instances-of-xml-data.md)  
  
  
