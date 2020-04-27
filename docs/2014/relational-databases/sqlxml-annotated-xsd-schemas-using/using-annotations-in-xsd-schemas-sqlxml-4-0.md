---
title: Verwenden von Anmerkungen in XSD-Schemas (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, about annotated XSD schemas
- annotations [SQLXML]
- relationships [SQLXML]
- relationships [SQLXML], hierarchical relationships
- hierarchical relationships [SQLXML]
- mapping schema [SQLXML], scenarios for using
ms.assetid: 78f318a4-7a36-473b-9852-a4bae6940ce5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c62357496d0b143fcd8736bc61117d43c6a0fac
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66013601"
---
# <a name="using-annotations-in-xsd-schemas-sqlxml-40"></a>Verwenden von Anmerkungen in XSD-Schemas (SQLXML 4.0)
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0 unterstützt die XSD-Schemasprache Anmerkungen auf ähnliche Weise wie die in der XDR-Schemasprache (XML-Data Reduced) eingeführten Anmerkungen. Es gibt weitere in XSD eingeführte Anmerkungen, die in XDR nicht unterstützt werden.  
  
 Diese Anmerkungen können innerhalb des XSD-Schemas verwendet werden, um Zuordnungen von XML zu relationalen Daten anzugeben. Dazu gehört die Zuordnung von Elementen und Attributen im XSD-Schema zu Tabellen (Sichten) und Spalten in den Datenbanken.  
  
 Wenn Sie die Anmerkungen nicht angeben, wird die Standardzuordnung vorgenommen. Standardmäßig wird ein XSD-Element mit einem komplexen Typ einem Tabellennamen (Sichtnamen) in der angegebenen Datenbank zugeordnet, und ein Element oder Attribut mit einem einfachen Typ wird der Spalte mit demselben Namen wie das Element oder Attribut zugeordnet.  
  
 Diese Anmerkungen können auch zur Angabe der hierarchischen Beziehungen in XML verwendet werden, wodurch die Beziehungen in der Datenbank dargestellt werden, da ein XSD-Schema einfach eine XML-Sicht relationaler Daten ist.  
  
 Dieser Abschnitt enthält Beschreibungen der Anmerkungen, die Sie mit XSD-Schemas verwenden können, sowie Anwendungsbeispiele.  
  
> [!NOTE]  
>  Alle Beispiele in diesem Abschnitt geben einfache Xpath-Abfragen für das mit Anmerkungen versehene XSD-Schema an, das in dem jeweiligen Beispiel beschrieben wird. Kenntnisse der XPath-Sprache werden vorausgesetzt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [XSD-Anmerkungen &#40;SQLXML 4,0&#41;](xsd-annotations-sqlxml-4-0.md)  
 Enthält eine Liste der Anmerkungen, die Sie mit XSD-Schemas verwenden können, ihre Beschreibungen und die entsprechenden Anmerkungen für XDR.  
  
 [Standard Zuordnung von XSD-Elementen und-Attributen zu Tabellen und Spalten &#40;SQLXML 4,0&#41;](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
 Erläutert die Standardzuordnung und enthält Beispiele für Tasks, die im Zusammenhang mit der Standardzuordnung stehen.  
  
 [Explizite Zuordnung von XSD-Elementen und-Attributen zu Tabellen und Spalten &#40;SQLXML 4,0&#41;](explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns.md)  
 Erklärt die explizite Zuordnung mit der `sql:relation`-Anmerkung und der `sql:field`-Anmerkung anhand von Beispielen.  
  
 [Angeben von Beziehungen mithilfe von ' SQL: Relationship ' &#40;SQLXML 4,0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
 Beschreibt die `sql:relationship`-Anmerkung und gibt Beispiele.  
  
 [Angeben des SQL: inverse-Attributs für SQL: Relationship &#40;SQLXML 4,0&#41;](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)  
 Beschreibt die `sql:inverse`-Anmerkung.  
  
 [Erstellen konstanter Elemente mithilfe von SQL: is-constant &#40;SQLXML 4,0&#41;](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)  
 Beschreibt die `sql:is-constant`-Anmerkung und gibt Beispiele.  
  
 [Ausschließen von Schema Elementen aus dem resultierenden XML-Dokument mithilfe von SQL: zugeordnet &#40;SQLXML 4,0&#41;](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)  
 Beschreibt die `sql:mapped`-Anmerkung und gibt Beispiele.  
  
 [Filtern von Werten mit ' SQL: limit-field ' und ' SQL: limit-value ' &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 Beschreibt die `sql:limit-field`-Anmerkung und die `sql:limit-value`-Anmerkung und gibt Beispiele.  
  
 [Identifizieren von Schlüssel Spalten mithilfe von SQL: key-fields &#40;SQLXML 4,0&#41;](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)  
 Beschreibt die `sql:key-fields`-Anmerkung und gibt Beispiele.  
  
 [Angeben eines Ziel Namespace mit dem targetNamespace-Attribut &#40;SQLXML 4,0&#41;](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
 Beschreibt Beispiele für das **targetNamespace** -Attribut und stellt Beispiele bereit.  
  
 [Erstellen gültiger Attribute vom Typ ID, IDREF und IDREFS mithilfe von SQL: Prefix &#40;SQLXML 4,0&#41;](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)  
 Beschreibt die `sql:prefix`-Anmerkung und gibt Beispiele.  
  
 [Datentyp Umwandlungen und die SQL: datatype-Anmerkung &#40;SQLXML 4,0&#41;](data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)  
 Beschreibt die `sql:datatype`-Anmerkung und gibt Beispiele.  
  
 [Zuordnung von XSD-Datentypen zu XPath-Datentypen &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)  
 Enthält eine Tabelle, in der die Datentypen XSD, XDR und Xpath verglichen werden, und listet die relevanten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konvertierungen auf.  
  
 [Erstellen von CDATA-Abschnitten mit SQL: use-cdata &#40;SQLXML 4,0&#41;](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)  
 Beschreibt die `sql:use-data`-Anmerkung und gibt Beispiele.  
  
 [Anfordern von URL-verweisen auf BLOB-Daten mithilfe von SQL: encode &#40;SQLXML 4,0&#41;](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)  
 Beschreibt die `sql:encode`-Anmerkung und gibt Beispiele.  
  
 [Abrufen von nicht verbrauchten Daten mithilfe von ' SQL: overflow-field &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 Beschreibt die `sql:overflow-field`-Anmerkung und gibt Beispiele.  
  
 [Ausblenden von Elementen und Attributen mit sql:hide](hiding-elements-and-attributes-by-using-sql-hide.md)  
 Beschreibt die `sql:hide`-Anmerkung und gibt Beispiele.  
  
 [Verwenden der Anmerkungen 'sql:identity' und 'sql:guid'](using-the-sql-identity-and-sql-guid-annotations.md)  
 Beschreibt die `sql:identity`-Anmerkung und die `sql:guid`-Anmerkung und gibt Beispiele.  
  
 [Angeben der Tiefe von rekursiven Beziehungen mit 'sql:max-depth'](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)  
 Beschreibt die `sql:max-depth`-Anmerkung und gibt Beispiele.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überlegungen zur Schema Sicherheit mit Anmerkungen &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)  
  
  
