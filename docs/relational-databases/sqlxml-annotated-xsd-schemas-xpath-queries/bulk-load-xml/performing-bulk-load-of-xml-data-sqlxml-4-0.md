---
title: Ausführen von Massen Laden von XML-Daten (SQLXML)
description: Erfahren Sie, wie Sie XML-Massen laden in SQLXML 4,0 verwenden, um semistrukturierte XML-Daten in Microsoft SQL Server Tabellen zu laden.
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML]
- bulk load [SQLXML]
- data insertions [SQLXML]
- SQLXML, bulk loading
- XSD schemas [SQLXML], XML Bulk Load
- XDR schemas [SQLXML], XML Bulk Load
- inserting data
ms.assetid: 3708b493-322e-4f3c-9b27-441d0c0ee346
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b04af587bc3bfd7b7a87027c41be648736389950
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97439672"
---
# <a name="performing-bulk-load-of-xml-data-sqlxml-40"></a>Ausführen von Massenladen von XML-Daten (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  XML-Massenladen ist ein eigenständiges COM-Objekt, mit dem Sie semistrukturierte XML-Daten in Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabellen laden können.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Einführung in XML-Massen laden &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/introduction-to-xml-bulk-load-sqlxml-4-0.md)  
 Stellt allgemeine Informationen über das Massenladen von XML-Daten mit dem XML-Massenladen-Hilfsprogramm zur Verfügung. Die Themen enthalten XML-Daten-Streaming und einen Vergleich zwischen transaktiv und nicht durchgeführten Massenladevorgängen.  
  
 [Daten Satz Generierungsprozess &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/record-generation-process-sqlxml-4-0.md)  
 Beschreibt den Prozess und die Regeln, mit denen Datensätze für XML-Massenladen generiert werden.  
  
 [Interpretation der Anmerkung &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sqlxml-4-0.md)  
 Beschreibt, wie XML-Massenladen Anmerkungen in XSD- und XDR-Schemas interpretiert.  
  
 [SQL Server XML-Massen laden-Objektmodell &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/sql-server-xml-bulk-load-object-model-sqlxml-4-0.md)  
 Beschreibt das SQLXMLBulkLoad-Objekt und dessen Methoden und Eigenschaften.  
  
 [Beispiele für XML-Massen laden &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)  
 Stellt Beispielcode bereit, der XML-Massenladen verwendet.  
  
 [Datentypen und XML-Massen Ladeverhalten &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/data-types-and-xml-bulk-load-behavior-sqlxml-4-0.md)  
 Beschreibt XML-Massenladenverhalten mit verschiedenen Typen in XSD und XDR.  
  
 [Richtlinien und Einschränkungen von XML-Massen laden &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/guidelines-and-limitations-of-xml-bulk-load-sqlxml-4-0.md)  
 Führt einige Punkte auf, die beim Arbeiten mit XML-Massenladen zu beachten sind.  
  
  
