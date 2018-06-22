---
title: XML-Datentypunterstützung für SQLXML 4.0 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLXML, xml data type support
- xml data type [SQL Server], SQLXML
ms.assetid: 9a6f5ad8-4a8f-4de7-ac17-81d5ccf78459
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3f0c3589b34087c5615179d2e7b6449372bea54d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048928"
---
# <a name="xml-data-type-support-in-sqlxml-40"></a>XML-Datentypunterstützung für SQLXML 4.0
  Ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Eingabe von XML-Daten mithilfe des `xml`-Datentyps. Dieses Thema enthält Informationen, wie SQLXML 4.0 Instanzen von `xml`-Datentyp erkennt und unterstützt.  
  
## <a name="working-with-xml-data-types"></a>Arbeiten mit XML-Datentypen  
 Die folgenden Beispiele zeigen, wie Sie mit SQL-Tabellen arbeiten, die Spalten des `xml`-Datentyps implementieren.  
  
|Task|Beispiel|Thema|  
|----------|-------------|-----------|  
|So ordnen Sie eine `xml`-Spalte einer XML-Sicht zu und schließen diese in die Sicht ein|"Zuordnen eines XML-Elements zu einer XML-Datentypspalte"|[Standardzuordnung von XSD-Elementen und-Attributen zu Tabellen und Spalten &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)|  
|So fügen Sie Daten in eine `xml`-Spalte mit Updategrams ein|"Einfügen von Daten in eine XML-Datentypspalte"|[Einfügen von Daten mit XML-Updategrams &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md)|  
|Massenladen von XML-Daten in eine `xml`-Spalte|"Massenladen in XML-Datentypspalten"|[Beispiele für XML-Massenladen &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)|  
  
## <a name="guidelines-and-limitations"></a>Richtlinien und Einschränkungen  
  
-   **\<XSD: alle >** kann nicht zugeordnet werden, um eine Spalte z. B. eine `xml` -Datentyp. Dieses Szenario wird in SQLXML durch die `sql:overflow-field`-Anmerkung unterstützt. Eine weitere Möglichkeit, das Problem zu umgehen, ist die Zuordnung eines `xml`-Datentypfelds als ein Element von `xsd:anyType`. Diese Problemumgehung wird im Beispiel "Zuordnen eines XML-Elements zu einer XML-Datentypspalte" gezeigt, auf das in der oben stehenden Tabelle verwiesen wird.  
  
-   XPath-Abfrage in den Inhalten von `xml`-Datentypspalten wird nicht unterstützt.  
  
-   Die Verwendung einer `xml`-Datentypspalte in Anmerkungen, in denen sie nicht unterstützt werden (z. B. `sql:relationship` und `sql:key-fields`) oder nicht zulässig sind, führt zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlern, die von Komponenten der mittleren Ebene, die SQLXML 4.0 implementieren, nicht aufgefangen werden. Der Grund dafür ist, dass SQLXML keine SQL-Typinformationen erfordert. Dieses Verhalten von SQLXML ist dem für andere Datentypen ähnlich, z. B. BLOB und binäre Typen.  
  
-   Die Zuordnung von`xml`-Spalten wird nur für XSD-Schemas unterstützt. XDR-Schemas unterstützen nicht die Zuordnung von `xml`-Spalten.  
  
-   SQLXML 4.0 verlässt sich auf die Unterstützung für die XML-Analyse, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereitgestellt wird. Eine `xml`-Spalte kann entweder als typisiertes XML oder nicht typisiertes XML zugeordnet werden. In beiden Fällen überprüft SQLXML 4.0 die XML-Eingabe nicht.  Wenn die XML-Eingabe nicht gültig oder nicht wohlgeformt ist, sendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Meldung an SQLXML und gibt alle relevanten, vom Server an den Benutzer gesendeten Fehlerinformationen weiter.  
  
-   SQLXML 4.0 basiert auf der eingeschränkten Unterstützung für DTDs, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereitgestellt wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gestattet die Verwendung einer internen DTD in `xml`-Datentypdaten, die verwendet werden kann, um Standardwerte anzugeben und Entitätsverweise durch ihren erweiterten Inhalt zu ersetzen. SQLXML übergibt die XML-Daten unverändert an den Server (einschließlich der internen DTD). Mithilfe von Drittanbieter-Tools können Sie DTDs in XML-Schemadokumente (XSD) konvertieren und die Daten mit XML-Inlineschemas in die Datenbank laden.  
  
-   SQLXML 4.0 behält nicht verarbeitungsanweisungen für XML-Deklaration (z. B.) basierend auf dem Verhalten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Stattdessen wird die XML-Deklaration als Direktive an den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-XML-Parser behandelt, und seine Attribute (version, encoding und standalone) gehen nach der Konvertierung zum `xml`-Datentyp verloren. Die XML-Daten werden intern als UCS-2 gespeichert. Alle anderen Verarbeitungsanweisungen in der XML-Instanz bleiben erhalten. Sie sind in der `xml`-Spalte zulässig und können durch SQLXML unterstützt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Daten &#40;SQL Server&#41;](../xml/xml-data-sql-server.md)  
  
  