---
title: XSD-Anmerkungen (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, annotations listed
- XSD schemas [SQLXML], annotations
ms.assetid: c62a6785-8d66-40a2-9c5d-80c73d600a3b
author: MightyPen
ms.author: genemi
ms.reviewer: ''
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 583f9803ea7a11384ff0b27a73cfd95be5a24101
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68066869"
---
# <a name="xsd-annotations-sqlxml-40"></a>XSD-Anmerkungen (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In der folgenden Tabelle werden die mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] eingeführten XSD-Anmerkungen mit den mit [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] eingeführten XDR-Anmerkungen verglichen.  
  
|XSD-Anmerkung|Beschreibung|Themenlink|XDR-Anmerkung|  
|--------------------|-----------------|----------------|--------------------|  
|**sql:encode**|Ermöglicht bei der Zuordnung eines XML-Elements oder -Attributs zu einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-BLOB-Spalte die Abfrage eines Verweis-URIs. Dieser URI kann später verwendet werden, um BLOB-Daten zurückzugeben.|[Anfordern von URL-verweisen auf BLOB-Daten mithilfe von Sql: Codieren &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)|**url-encode**|  
|**sql:guid**|Damit können Sie angeben, ob ein von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generierter GUID-Wert oder der im Updategram für diese Spalte angegebene Wert verwendet werden soll.|[Verwenden der Anmerkungen 'sql:identity' und 'sql:guid'](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)|Nicht unterstützt|  
|**sql:hide**|Blendet das im Schema angegebene Element oder Attribut im resultierenden XML-Dokument aus.|[Ausblenden von Elementen und Attributen mit sql:hide](../../relational-databases/sqlxml-annotated-xsd-schemas-using/hiding-elements-and-attributes-by-using-sql-hide.md)|Nicht unterstützt|  
|**sql:identity**|Kann in jedem Knoten angegeben werden, der einer Datenbankspalte vom Typ IDENTITY zugeordnet ist. Der für diese Anmerkung angegebene Wert definiert, wie die entsprechende Spalte vom Typ IDENTITY in der Datenbank aktualisiert wird.|[Verwenden der Anmerkungen 'sql:identity' und 'sql:guid'](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)|Nicht unterstützt|  
|**sql:inverse**|Weist die updategramlogik an die Interpretation der über-/ unterordnungsbeziehung, die angegeben wurde  **\<SQL: Relationship >** .|[Angeben des SQL: Inverse-Attributs für SQL: Relationship &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)|Nicht unterstützt|  
|**sql:is-constant**|Erstellt ein XML-Element, das keiner Tabelle zugeordnet wird. Das Element wird in der Abfrageausgabe angezeigt.|[Erstellen von Konstanten Elementen unter Verwendung von Sql: ist Konstante &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)|Gleich|  
|**sql:key-fields**|Damit können Sie Spalten angeben, mit denen die Zeilen in einer Tabelle eindeutig identifiziert werden.|[Identifizieren von Schlüsselspalten mithilfe von SQL: Key-Felder &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)|Gleich|  
|**sql:limit-field**<br /><br /> **sql:limit-value**|Damit können Sie die Werte beschränken, die auf Grundlage eines beschränkenden Werts zurückgegeben werden.|[Filtern von Werten mithilfe von ' SQL: Limit-Field und ' SQL: Limit-Wert &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/filtering-values-using-sql-limit-field-and-sql-limit-value-sqlxml-4-0.md)|Gleich|  
|**sql:mapped**|Damit können Schemaelemente vom Ergebnis ausgeschlossen werden.|[Ausschließen von Schemaelementen aus dem resultierenden XML-Dokument mit Sql: zugeordnet &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)|**map-field**|  
|**sql:max-depth**|Damit kann die Tiefe in rekursiven, im Schema angegebenen Beziehungen angegeben werden.|[Angeben der Tiefe von rekursiven Beziehungen mit 'sql:max-depth'](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)|Nicht unterstützt|  
|**sql:overflow-field**|Identifiziert die Datenbankspalte, die die Überlaufdaten enthält.|[Abrufen von nicht verbrauchten Daten mithilfe der SQL: Overflow-Feld &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/retrieving-unconsumed-data-using-the-sql-overflow-field-sqlxml-4-0.md)|Gleich|  
|**sql:prefix**|Erstellt die gültigen XML-Attribute ID, IDREF und IDREFS. Stellt den Werten von ID, IDREF und IDREFS eine Zeichenfolge voran.|[Erstellen die gültige ID, IDREF und IDREFS-Typ Attribute verwenden Sql:prefix &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)|Gleich|  
|**sql:relationship**|Gibt Beziehungen zwischen XML-Elementen an. Die **übergeordneten**, **untergeordneten**, **übergeordneten Schlüssel**, und **untergeordneten Schlüssels** Attribute werden verwendet, um die Beziehung herzustellen.|[Angeben von Beziehungen mithilfe von SQL: Relationship &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)|Die Attributnamen lauten anders:<br /><br /> **key-relation**<br /><br /> **foreign-relation**<br /><br /> **key**<br /><br /> **foreign-key**|  
|**sql:use-cdata**|Damit kann festgelegt werden, dass für bestimmte Elemente im XML-Dokument CDATA-Abschnitte verwendet werden.|[Erstellen von CDATA-Abschnitten mithilfe von SQL: use-Cdata &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)|Gleich|  
  
> [!NOTE]  
>  Das systemeigene XSD **TargetNamespace** -Attribut ersetzt das **Zielnamespace** Anmerkung, die in eingeführt wurde die [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] XDR-Zuordnungsschema.  
  
## <a name="see-also"></a>Siehe auch  
 [Angeben eines Target Namespace mit dem ' targetNamespace '-Attribut &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
  
  
