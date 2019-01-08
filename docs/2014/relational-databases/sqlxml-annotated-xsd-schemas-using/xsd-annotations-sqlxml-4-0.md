---
title: XSD-Anmerkungen (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, annotations listed
- XSD schemas [SQLXML], annotations
ms.assetid: c62a6785-8d66-40a2-9c5d-80c73d600a3b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8cfb0078672a56ba85692fdb836a17ea9c9db302
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52758062"
---
# <a name="xsd-annotations-sqlxml-40"></a>XSD-Anmerkungen (SQLXML 4.0)
  In der folgenden Tabelle werden die mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] eingeführten XSD-Anmerkungen mit den mit [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] eingeführten XDR-Anmerkungen verglichen.  
  
|XSD-Anmerkung|Description|Themenlink|XDR-Anmerkung|  
|--------------------|-----------------|----------------|--------------------|  
|`sql:encode`|Ermöglicht bei der Zuordnung eines XML-Elements oder -Attributs zu einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-BLOB-Spalte die Abfrage eines Verweis-URIs. Dieser URI kann später verwendet werden, um BLOB-Daten zurückzugeben.|[Anfordern von URL-verweisen auf BLOB-Daten mithilfe von Sql: Codieren &#40;SQLXML 4.0&#41;](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)|`url-encode`|  
|`sql:guid`|Damit können Sie angeben, ob ein von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generierter GUID-Wert oder der im Updategram für diese Spalte angegebene Wert verwendet werden soll.|[Verwenden der Anmerkungen 'sql:identity' und 'sql:guid'](using-the-sql-identity-and-sql-guid-annotations.md)|Nicht unterstützt|  
|`sql:hide`|Blendet das im Schema angegebene Element oder Attribut im resultierenden XML-Dokument aus.|[Ausblenden von Elementen und Attributen mit sql:hide](hiding-elements-and-attributes-by-using-sql-hide.md)|Nicht unterstützt|  
|`sql:identity`|Kann in jedem Knoten angegeben werden, der einer Datenbankspalte vom Typ IDENTITY zugeordnet ist. Der für diese Anmerkung angegebene Wert definiert, wie die entsprechende Spalte vom Typ IDENTITY in der Datenbank aktualisiert wird.|[Verwenden der Anmerkungen 'sql:identity' und 'sql:guid'](using-the-sql-identity-and-sql-guid-annotations.md)|Nicht unterstützt|  
|`sql:inverse`|Weist die updategramlogik an die Interpretation der über-/ unterordnungsbeziehung, die angegeben wurde  **\<SQL: Relationship >**.|[Angeben des SQL: Inverse-Attributs für SQL: Relationship &#40;SQLXML 4.0&#41;](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)|Nicht unterstützt|  
|`sql:is-constant`|Erstellt ein XML-Element, das keiner Tabelle zugeordnet wird. Das Element wird in der Abfrageausgabe angezeigt.|[Erstellen von Konstanten Elementen unter Verwendung von Sql: ist Konstante &#40;SQLXML 4.0&#41;](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)|Gleich|  
|`sql:key-fields`|Damit können Sie Spalten angeben, mit denen die Zeilen in einer Tabelle eindeutig identifiziert werden.|[Identifizieren von Schlüsselspalten mithilfe von SQL: Key-Felder &#40;SQLXML 4.0&#41;](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)|Gleich|  
|`sql:limit-field`<br /><br /> `sql:limit-value`|Damit können Sie die Werte beschränken, die auf Grundlage eines beschränkenden Werts zurückgegeben werden.|[Filtern von Werten mithilfe von ' SQL: Limit-Field und ' SQL: Limit-Wert &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)|Gleich|  
|`sql:mapped`|Damit können Schemaelemente vom Ergebnis ausgeschlossen werden.|[Ausschließen von Schemaelementen aus dem resultierenden XML-Dokument mit Sql: zugeordnet &#40;SQLXML 4.0&#41;](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)|`map-field`|  
|`sql:max-depth`|Damit kann die Tiefe in rekursiven, im Schema angegebenen Beziehungen angegeben werden.|[Angeben der Tiefe von rekursiven Beziehungen mit 'sql:max-depth'](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)|Nicht unterstützt|  
|`sql:overflow-field`|Identifiziert die Datenbankspalte, die die Überlaufdaten enthält.|[Abrufen von nicht verbrauchten Daten mithilfe der SQL: Overflow-Feld &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)|Gleich|  
|`sql:prefix`|Erstellt die gültigen XML-Attribute ID, IDREF und IDREFS. Stellt den Werten von ID, IDREF und IDREFS eine Zeichenfolge voran.|[Erstellen die gültige ID, IDREF und IDREFS-Typ Attribute verwenden Sql:prefix &#40;SQLXML 4.0&#41;](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)|Gleich|  
|`sql:relationship`|Gibt Beziehungen zwischen XML-Elementen an. Die Beziehung wird mithilfe der Attribute `parent`, `child`, `parent-key` und `child-key` festgelegt.|[Angeben von Beziehungen mithilfe von SQL: Relationship &#40;SQLXML 4.0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)|Die Attributnamen lauten anders:<br /><br /> `key-relation`<br /><br /> `foreign-relation`<br /><br /> `key`<br /><br /> `foreign-key`|  
|`sql:use-cdata`|Damit kann festgelegt werden, dass für bestimmte Elemente im XML-Dokument CDATA-Abschnitte verwendet werden.|[Erstellen von CDATA-Abschnitten mithilfe von SQL: use-Cdata &#40;SQLXML 4.0&#41;](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)|Gleich|  
  
> [!NOTE]  
>  Das systemeigene XSD-Attribut `targetNamespace` ersetzt die `target-namespace`-Anmerkung, die mit dem XDR-Zuordnungsschema von [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] eingeführt wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Angeben eines Target Namespace mit dem ' targetNamespace '-Attribut &#40;SQLXML 4.0&#41;](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
  
  
