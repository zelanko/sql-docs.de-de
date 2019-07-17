---
title: XML-Datentypunterstützung für SQLXML 4.0 | Microsoft-Dokumentation
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
ms.openlocfilehash: 1fd2de6167b646610e8b57898b186accbbc1593d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68135289"
---
# <a name="xml-data-type-support-in-sqlxml-40"></a>XML-Datentypunterstützung für SQLXML 4.0
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Beginnend mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt XML typisierte Daten mithilfe der **Xml** -Datentyp. Dieses Thema enthält Informationen, wie SQLXML 4.0 Instanzen von erkennt die **Xml** -Datentyp und unterstützt werden.  
  
## <a name="working-with-xml-data-types"></a>Arbeiten mit XML-Datentypen  
 Weitere Informationen zum Arbeiten mit SQL-Tabellen, die implementieren zu **Xml** Daten Spalten vom Typ in den folgenden Beispielen werden bereitgestellt:  
  
|Aufgabe|Beispiel|Thema|  
|----------|-------------|-----------|  
|Zuordnen und enthalten eine **Xml** -Spalte in eine XML-Sicht|"Zuordnen eines XML-Elements zu einer XML-Datentypspalte"|[Standardzuordnung von XSD-Elementen und-Attributen zu Tabellen und Spalten &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)|  
|Gewusst wie: Einfügen von Daten in eine **Xml** -Spalte mit Updategrams|"Einfügen von Daten in eine XML-Datentypspalte"|[Einfügen von Daten mit XML-Updategrams &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)|  
|Massenladen von XML-Daten in eine **Xml** Spalte|"Massenladen in XML-Datentypspalten"|[Beispiele für XML-Massenladen &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)|  
  
## <a name="guidelines-and-limitations"></a>Richtlinien und Einschränkungen  
  
-   **\<XSD: alle >** können nicht zugeordnet werden, um einer Spalte, eine **Xml** -Datentyp. Unterstützung in SQLXML, für dieses Szenario über erfolgt die **SQL: Overflow-Feld** Anmerkung. Eine weitere Möglichkeit ist die Zuordnung einer **Xml** datentypfeld als Element **xsd: anyType '** . Diese Problemumgehung wird im Beispiel "Zuordnen eines XML-Elements zu einer XML-Datentypspalte" gezeigt, auf das in der oben stehenden Tabelle verwiesen wird.  
  
-   XPath-Abfrage in den Inhalt von **Xml** -datentypspalten wird nicht unterstützt.  
  
-   Verwenden einer **Xml** -Datentypspalte in Anmerkungen, in dem sie wird nicht unterstützt (z. B. **SQL: Relationship** und **SQL: Key-Felder**) oder zulässig sind, führt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehler, die von Komponenten der mittleren Ebene, die Implementierung von SQLXML 4.0 nicht aufgefangen werden. Der Grund dafür ist, dass SQLXML keine SQL-Typinformationen erfordert. Dieses Verhalten von SQLXML ist dem für andere Datentypen ähnlich, z. B. BLOB und binäre Typen.  
  
-   Zuordnen von **Xml** Spalten wird nur für XSD-Schemas unterstützt. XDR-Schemas unterstützen keine Zuordnung **Xml** Spalten.  
  
-   SQLXML 4.0 verlässt sich auf die Unterstützung für die XML-Analyse, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereitgestellt wird. Ein **Xml** Spalte kann entweder als typisiertes XML oder nicht typisiertes XML zugeordnet werden. In beiden Fällen überprüft SQLXML 4.0 die XML-Eingabe nicht.  Wenn die XML-Eingabe nicht gültig oder nicht wohlgeformt ist, sendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Meldung an SQLXML und gibt alle relevanten, vom Server an den Benutzer gesendeten Fehlerinformationen weiter.  
  
-   SQLXML 4.0 basiert auf der eingeschränkten Unterstützung für DTDs, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereitgestellt wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ermöglicht die Verwendung einer internen DTD in **Xml** datentypdaten, die um Standardwerte bereitzustellen und Entitätsverweise durch ihren erweiterten Inhalt zu ersetzen verwendet werden kann. SQLXML übergibt die XML-Daten unverändert an den Server (einschließlich der internen DTD). Mithilfe von Drittanbieter-Tools können Sie DTDs in XML-Schemadokumente (XSD) konvertieren und die Daten mit XML-Inlineschemas in die Datenbank laden.  
  
-   SQLXML 4.0 behält nicht verarbeitungsanweisungen für XML-Deklaration (z. B.) auf das Verhalten des Basis [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Stattdessen wird die XML-Deklaration als Direktive an behandelt die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML-Parser und seine Attribute (Version, Codierung und eigenständige) verloren, nachdem die Daten konvertiert werden, um die **Xml** -Datentyp. Die XML-Daten werden intern als UCS-2 gespeichert. Alle anderen verarbeitungsanweisungen in der XML-Instanz beibehalten werden. Sie dürfen den **Xml** Spalte und können durch SQLXML unterstützt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Daten &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md)  
  
  
