---
title: XML-Datentypunterstützung für SQLXML 4.0
description: Erfahren Sie, wie SQLXML 4,0 Instanzen des XML-Datentyps erkennt und Unterstützung dafür implementiert.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, xml data type support
- xml data type [SQL Server], SQLXML
ms.assetid: 9a6f5ad8-4a8f-4de7-ac17-81d5ccf78459
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: afaee239422b557b53117441f36c79d1180802db
ms.sourcegitcommit: 6593b3b6365283bb76c31102743cdccc175622fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84306099"
---
# <a name="xml-data-type-support-in-sqlxml-40"></a>XML-Datentypunterstützung für SQLXML 4.0
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt XML-typisierte Daten mithilfe des **XML** -Datentyps. Dieses Thema enthält Informationen darüber, wie SQLXML 4,0 Instanzen des **XML** -Datentyps erkennt und Unterstützung für Sie implementiert.  
  
## <a name="working-with-xml-data-types"></a>Arbeiten mit XML-Datentypen  
 Weitere Informationen zum Arbeiten mit SQL-Tabellen, die Spalten des **XML** -Datentyps implementieren, finden Sie in den folgenden Beispielen:  
  
|Aufgabe|Beispiel|Thema|  
|----------|-------------|-----------|  
|Zuordnen und Einschließen einer **XML** -Spalte in eine XML-Ansicht|"Zuordnen eines XML-Elements zu einer XML-Datentypspalte"|[Standard Zuordnung von XSD-Elementen und-Attributen zu Tabellen und Spalten &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)|  
|Einfügen von Daten in eine **XML** -Spalte mit Update grams|"Einfügen von Daten in eine XML-Datentypspalte"|[Einfügen von Daten mit XML-Update grams &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)|  
|Massen Laden von XML-Daten in eine **XML** -Spalte|"Massenladen in XML-Datentypspalten"|[Beispiele für XML-Massen laden &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)|  
  
## <a name="guidelines-and-limitations"></a>Richtlinien und Einschränkungen  
  
-   **\<xsd:any>** kann keiner Spalte zugeordnet werden, einschließlich eines **XML** -Datentyps. Die Unterstützung in SQLXML für dieses Szenario wird durch die **SQL: overflow-field-** Anmerkung bereitgestellt. Eine weitere Lösung ist das Zuordnen eines **XML** -Datentyp Felds als Element von **xsd: anyType**. Diese Problemumgehung wird im Beispiel "Zuordnen eines XML-Elements zu einer XML-Datentypspalte" gezeigt, auf das in der oben stehenden Tabelle verwiesen wird.  
  
-   Die XPath-Abfrage in den Inhalt von Spalten des **XML** -Datentyps wird nicht unterstützt.  
  
-   Die Verwendung einer **XML** -Datentyp Spalte in Anmerkungen, bei denen Sie nicht unterstützt wird (z. b. **SQL: Relationship** und **SQL: key-fields**), führt zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehlern, die von Komponenten der mittleren Ebene, die SQLXML 4,0 implementieren, nicht erfasst werden. Der Grund dafür ist, dass SQLXML keine SQL-Typinformationen erfordert. Dieses Verhalten von SQLXML ist dem für andere Datentypen ähnlich, z. B. BLOB und binäre Typen.  
  
-   Das Mapping von **XML** -Spalten wird nur für XSD-Schemas unterstützt. XDR-Schemas unterstützen keine Zuordnung von **XML** -Spalten.  
  
-   SQLXML 4.0 verlässt sich auf die Unterstützung für die XML-Analyse, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereitgestellt wird. Eine **XML** -Spalte kann entweder als typisiertes XML oder nicht typisiertes XML zugeordnet werden. In beiden Fällen überprüft SQLXML 4.0 die XML-Eingabe nicht.  Wenn die XML-Eingabe nicht gültig oder nicht wohlgeformt ist, sendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Meldung an SQLXML und gibt alle relevanten, vom Server an den Benutzer gesendeten Fehlerinformationen weiter.  
  
-   SQLXML 4.0 basiert auf der eingeschränkten Unterstützung für DTDs, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereitgestellt wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ermöglicht eine interne DTD in **XML** -Datentyp Daten, die verwendet werden können, um Standardwerte bereitzustellen und Entitäts Verweise durch ihren erweiterten Inhalt zu ersetzen. SQLXML übergibt die XML-Daten unverändert an den Server (einschließlich der internen DTD). Mithilfe von Drittanbieter-Tools können Sie DTDs in XML-Schemadokumente (XSD) konvertieren und die Daten mit XML-Inlineschemas in die Datenbank laden.  
  
-   SQLXML 4,0 behält keine Verarbeitungsanweisungen für die XML-Deklaration bei (z. b.), basierend auf dem Verhalten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Stattdessen wird die XML-Deklaration als Direktive an den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML-Parser behandelt, und die zugehörigen Attribute (Version, Codierung und Standalone) gehen verloren, nachdem Daten in den **XML** -Datentyp konvertiert wurden. Die XML-Daten werden intern als UCS-2 gespeichert. Alle anderen Verarbeitungsanweisungen in der XML-Instanz werden beibehalten. Sie sind in der **XML** -Spalte zulässig und können von SQLXML unterstützt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Daten &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md)  
  
  
