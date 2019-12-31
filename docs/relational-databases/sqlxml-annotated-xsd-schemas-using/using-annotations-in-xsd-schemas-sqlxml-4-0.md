---
title: Verwenden von Anmerkungen in XSD-Schemas (SQLXML)
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 00cb5a095e6186ed6009f94dedaa43a81f8165d9
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75246836"
---
# <a name="using-annotations-in-xsd-schemas-sqlxml-40"></a>Verwenden von Anmerkungen in XSD-Schemas (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0 unterstützt die XSD-Schemasprache Anmerkungen auf ähnliche Weise wie die in der XDR-Schemasprache (XML-Data Reduced) eingeführten Anmerkungen. Es gibt weitere in XSD eingeführte Anmerkungen, die in XDR nicht unterstützt werden.  
  
 Diese Anmerkungen können innerhalb des XSD-Schemas verwendet werden, um Zuordnungen von XML zu relationalen Daten anzugeben. Dazu gehört die Zuordnung von Elementen und Attributen im XSD-Schema zu Tabellen (Sichten) und Spalten in den Datenbanken.  
  
 Wenn Sie die Anmerkungen nicht angeben, wird die Standardzuordnung vorgenommen. Standardmäßig wird ein XSD-Element mit einem komplexen Typ einem Tabellennamen (Sichtnamen) in der angegebenen Datenbank zugeordnet, und ein Element oder Attribut mit einem einfachen Typ wird der Spalte mit demselben Namen wie das Element oder Attribut zugeordnet.  
  
 Diese Anmerkungen können auch zur Angabe der hierarchischen Beziehungen in XML verwendet werden, wodurch die Beziehungen in der Datenbank dargestellt werden, da ein XSD-Schema einfach eine XML-Sicht relationaler Daten ist.  
  
 Dieser Abschnitt enthält Beschreibungen der Anmerkungen, die Sie mit XSD-Schemas verwenden können, sowie Anwendungsbeispiele.  
  
> [!NOTE]  
>  Alle Beispiele in diesem Abschnitt geben einfache Xpath-Abfragen für das mit Anmerkungen versehene XSD-Schema an, das in dem jeweiligen Beispiel beschrieben wird. Kenntnisse der XPath-Sprache werden vorausgesetzt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [XSD-Anmerkungen &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/xsd-annotations-sqlxml-4-0.md)  
 Enthält eine Liste der Anmerkungen, die Sie mit XSD-Schemas verwenden können, ihre Beschreibungen und die entsprechenden Anmerkungen für XDR.  
  
 [Standard Zuordnung von XSD-Elementen und-Attributen zu Tabellen und Spalten &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
 Erläutert die Standardzuordnung und enthält Beispiele für Tasks, die im Zusammenhang mit der Standardzuordnung stehen.  
  
 [Explizite Zuordnung von XSD-Elementen und-Attributen zu Tabellen und Spalten &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns.md)  
 Erläutert die explizite Zuordnung zu den Anmerkungen " **SQL: Relation** " und " **SQL: Field** " und stellt Beispiele bereit.  
  
 [Angeben von Beziehungen mithilfe von ' SQL: Relationship ' &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
 Beschreibt Beispiele der **SQL: Relationship** -Anmerkung und stellt Beispiele bereit.  
  
 [Angeben des SQL: inverse-Attributs für SQL: Relationship &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)  
 Beschreibt die " **SQL: inverse** "-Anmerkung.  
  
 [Erstellen konstanter Elemente mithilfe von SQL: is-constant &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)  
 Beschreibt Beispiele der **SQL: is-constant-** Anmerkung und stellt Beispiele bereit.  
  
 [Ausschließen von Schema Elementen aus dem resultierenden XML-Dokument mithilfe von SQL: zugeordnet &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)  
 Beschreibt Beispiele der **SQL:** zugeordneten Anmerkung und stellt Beispiele bereit.  
  
 [Filtern von Werten mit ' SQL: limit-field ' und ' SQL: limit-value ' &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/filtering-values-using-sql-limit-field-and-sql-limit-value-sqlxml-4-0.md)  
 Beschreibt und stellt Beispiele für die Anmerkungen " **SQL: limit-field** " und " **SQL: limit-value** " bereit.  
  
 [Identifizieren von Schlüssel Spalten mithilfe von SQL: key-fields &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)  
 Beschreibt die **SQL: key-fields-** Anmerkung und stellt Beispiele bereit.  
  
 [Angeben eines Ziel Namespace mit dem targetNamespace-Attribut &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
 Beschreibt Beispiele für das **targetNamespace** -Attribut und stellt Beispiele bereit.  
  
 [Erstellen gültiger Attribute vom Typ ID, IDREF und IDREFS mithilfe von SQL: Prefix &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)  
 Beschreibt Beispiele der **SQL: Prefix** -Anmerkung und stellt Beispiele bereit.  
  
 [Datentyp Konvertierungen und die SQL: datatype-Anmerkung &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)  
 Beschreibt die **SQL: datatype** -Anmerkung und stellt Beispiele bereit.  
  
 [Zuordnung von XSD-Datentypen zu XPath-Datentypen &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/mapping-xsd-data-types-to-xpath-data-types-sqlxml-4-0.md)  
 Enthält eine Tabelle, in der die Datentypen XSD, XDR und Xpath verglichen werden, und listet die relevanten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konvertierungen auf.  
  
 [Erstellen von CDATA-Abschnitten mit SQL: use-cdata &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)  
 Beschreibt und stellt Beispiele für die " **SQL: use-Data"-** Anmerkung bereit.  
  
 [Anfordern von URL-verweisen auf BLOB-Daten mithilfe von SQL: encode &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)  
 Beschreibt Beispiele der **SQL: encode** -Anmerkung und stellt Beispiele bereit.  
  
 [Abrufen von nicht verbrauchten Daten mithilfe von ' SQL: overflow-field &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/retrieving-unconsumed-data-using-the-sql-overflow-field-sqlxml-4-0.md)  
 Beschreibt Beispiele der **SQL: overflow-field-** Anmerkung und stellt Beispiele bereit.  
  
 [Ausblenden von Elementen und Attributen mit sql:hide](../../relational-databases/sqlxml-annotated-xsd-schemas-using/hiding-elements-and-attributes-by-using-sql-hide.md)  
 Beschreibt Beispiele der **SQL: Hide** -Anmerkung und stellt Beispiele bereit.  
  
 [Verwenden der Anmerkungen 'sql:identity' und 'sql:guid'](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)  
 Beschreibt und stellt Beispiele für die Anmerkungen zu **SQL: Identity** und **SQL: GUID** bereit.  
  
 [Angeben der Tiefe von rekursiven Beziehungen mit 'sql:max-depth'](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)  
 Beschreibt Beispiele der **SQL: Max-tiefen** Anmerkung und stellt Beispiele bereit.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überlegungen zur Schema Sicherheit mit Anmerkungen &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)  
  
  
