---
title: Verwenden von Anmerkungen in XSD-Schemas (SQLXML 4.0) | Microsoft-Dokumentation
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
- annotated XSD schemas, about annotated XSD schemas
- annotations [SQLXML]
- relationships [SQLXML]
- relationships [SQLXML], hierarchical relationships
- hierarchical relationships [SQLXML]
- mapping schema [SQLXML], scenarios for using
ms.assetid: 78f318a4-7a36-473b-9852-a4bae6940ce5
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 26fd2f853697765fda82b869aae7780976753749
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321950"
---
# <a name="using-annotations-in-xsd-schemas-sqlxml-40"></a>Verwenden von Anmerkungen in XSD-Schemas (SQLXML 4.0)
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0 unterstützt die XSD-Schemasprache Anmerkungen auf ähnliche Weise wie die in der XDR-Schemasprache (XML-Data Reduced) eingeführten Anmerkungen. Es gibt weitere in XSD eingeführte Anmerkungen, die in XDR nicht unterstützt werden.  
  
 Diese Anmerkungen können innerhalb des XSD-Schemas verwendet werden, um Zuordnungen von XML zu relationalen Daten anzugeben. Dazu gehört die Zuordnung von Elementen und Attributen im XSD-Schema zu Tabellen (Sichten) und Spalten in den Datenbanken.  
  
 Wenn Sie die Anmerkungen nicht angeben, wird die Standardzuordnung vorgenommen. Standardmäßig wird ein XSD-Element mit einem komplexen Typ einem Tabellennamen (Sichtnamen) in der angegebenen Datenbank zugeordnet, und ein Element oder Attribut mit einem einfachen Typ wird der Spalte mit demselben Namen wie das Element oder Attribut zugeordnet.  
  
 Diese Anmerkungen können auch zur Angabe der hierarchischen Beziehungen in XML verwendet werden und somit die Beziehungen in der Datenbank darstellen, denn ein XSD-Schema ist nicht anderes als eine XML-Sicht relationaler Daten.  
  
 Dieser Abschnitt enthält Beschreibungen der Anmerkungen, die Sie mit XSD-Schemas verwenden können, sowie Anwendungsbeispiele.  
  
> [!NOTE]  
>  Alle Beispiele in diesem Abschnitt geben einfache Xpath-Abfragen für das mit Anmerkungen versehene XSD-Schema an, das in dem jeweiligen Beispiel beschrieben wird. Kenntnisse der XPath-Sprache werden vorausgesetzt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [XSD-Anmerkungen &#40;SQLXML 4.0&#41;](xsd-annotations-sqlxml-4-0.md)  
 Enthält eine Liste der Anmerkungen, die Sie mit XSD-Schemas verwenden können, ihre Beschreibungen und die entsprechenden Anmerkungen für XDR.  
  
 [Standardzuordnung von XSD-Elementen und-Attributen zu Tabellen und Spalten &#40;SQLXML 4.0&#41;](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
 Erläutert die Standardzuordnung und enthält Beispiele für Tasks, die im Zusammenhang mit der Standardzuordnung stehen.  
  
 [Explizite Zuordnung von XSD-Elementen und-Attributen zu Tabellen und Spalten &#40;SQLXML 4.0&#41;](explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns.md)  
 Erklärt die explizite Zuordnung mit der `sql:relation`-Anmerkung und der `sql:field`-Anmerkung anhand von Beispielen.  
  
 [Angeben von Beziehungen mithilfe von SQL: Relationship &#40;SQLXML 4.0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
 Beschreibt die `sql:relationship`-Anmerkung und gibt Beispiele.  
  
 [Angeben des SQL: Inverse-Attributs für SQL: Relationship &#40;SQLXML 4.0&#41;](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)  
 Beschreibt die `sql:inverse`-Anmerkung.  
  
 [Erstellen von Konstanten Elementen unter Verwendung von Sql: ist Konstante &#40;SQLXML 4.0&#41;](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)  
 Beschreibt die `sql:is-constant`-Anmerkung und gibt Beispiele.  
  
 [Ausschließen von Schemaelementen aus dem resultierenden XML-Dokument mit Sql: zugeordnet &#40;SQLXML 4.0&#41;](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)  
 Beschreibt die `sql:mapped`-Anmerkung und gibt Beispiele.  
  
 [Filtern von Werten mithilfe von ' SQL: Limit-Field und ' SQL: Limit-Wert &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 Beschreibt die `sql:limit-field`-Anmerkung und die `sql:limit-value`-Anmerkung und gibt Beispiele.  
  
 [Identifizieren von Schlüsselspalten mithilfe von SQL: Key-Felder &#40;SQLXML 4.0&#41;](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)  
 Beschreibt die `sql:key-fields`-Anmerkung und gibt Beispiele.  
  
 [Angeben eines Target Namespace mit dem ' targetNamespace '-Attribut &#40;SQLXML 4.0&#41;](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
 Beschreibt und enthält Beispiele für die **TargetNamespace** Attribut.  
  
 [Erstellen die gültige ID, IDREF und IDREFS-Typ Attribute verwenden Sql:prefix &#40;SQLXML 4.0&#41;](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)  
 Beschreibt die `sql:prefix`-Anmerkung und gibt Beispiele.  
  
 [Datentypumwandlungen und die SQL: DataType-Anmerkung &#40;SQLXML 4.0&#41;](data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)  
 Beschreibt die `sql:datatype`-Anmerkung und gibt Beispiele.  
  
 [Zuordnen von XSD-Datentypen zu XPath-Datentypen &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)  
 Enthält eine Tabelle, in der die Datentypen XSD, XDR und Xpath verglichen werden, und listet die relevanten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konvertierungen auf.  
  
 [Erstellen von CDATA-Abschnitten mithilfe von SQL: use-Cdata &#40;SQLXML 4.0&#41;](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)  
 Beschreibt die `sql:use-data`-Anmerkung und gibt Beispiele.  
  
 [Anfordern von URL-verweisen auf BLOB-Daten mithilfe von Sql: Codieren &#40;SQLXML 4.0&#41;](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)  
 Beschreibt die `sql:encode`-Anmerkung und gibt Beispiele.  
  
 [Abrufen von nicht verbrauchten Daten mithilfe der SQL: Overflow-Feld &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 Beschreibt die `sql:overflow-field`-Anmerkung und gibt Beispiele.  
  
 [Ausblenden von Elementen und Attributen mit sql:hide](hiding-elements-and-attributes-by-using-sql-hide.md)  
 Beschreibt die `sql:hide`-Anmerkung und gibt Beispiele.  
  
 [Verwenden der Anmerkungen 'sql:identity' und 'sql:guid'](using-the-sql-identity-and-sql-guid-annotations.md)  
 Beschreibt die `sql:identity`-Anmerkung und die `sql:guid`-Anmerkung und gibt Beispiele.  
  
 [Angeben der Tiefe von rekursiven Beziehungen mit 'sql:max-depth'](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)  
 Beschreibt die `sql:max-depth`-Anmerkung und gibt Beispiele.  
  
## <a name="see-also"></a>Siehe auch  
 [Überlegungen zur Sicherheit von Schemas versehen &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)  
  
  
