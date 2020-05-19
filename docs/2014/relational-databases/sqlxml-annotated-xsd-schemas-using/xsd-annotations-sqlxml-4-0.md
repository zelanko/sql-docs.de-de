---
title: XSD-Anmerkungen (SQLXML 4,0) | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b7fa444ebbf33c48a243703a19d1f296ce91816e
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703464"
---
# <a name="xsd-annotations-sqlxml-40"></a>XSD-Anmerkungen (SQLXML 4.0)
  In der folgenden Tabelle werden die mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] eingeführten XSD-Anmerkungen mit den mit [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] eingeführten XDR-Anmerkungen verglichen.  
  
|XSD-Anmerkung|Beschreibung|Themenlink|XDR-Anmerkung|  
|--------------------|-----------------|----------------|--------------------|  
|`sql:encode`|Ermöglicht bei der Zuordnung eines XML-Elements oder -Attributs zu einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-BLOB-Spalte die Abfrage eines Verweis-URIs. Dieser URI kann später verwendet werden, um BLOB-Daten zurückzugeben.|[Anfordern von URL-verweisen auf BLOB-Daten mithilfe von SQL: encode &#40;SQLXML 4,0&#41;](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)|`url-encode`|  
|`sql:guid`|Damit können Sie angeben, ob ein von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generierter GUID-Wert oder der im Updategram für diese Spalte angegebene Wert verwendet werden soll.|[Verwenden der Anmerkungen 'sql:identity' und 'sql:guid'](using-the-sql-identity-and-sql-guid-annotations.md)|Nicht unterstützt|  
|`sql:hide`|Blendet das im Schema angegebene Element oder Attribut im resultierenden XML-Dokument aus.|[Ausblenden von Elementen und Attributen mit sql:hide](hiding-elements-and-attributes-by-using-sql-hide.md)|Nicht unterstützt|  
|`sql:identity`|Kann in jedem Knoten angegeben werden, der einer Datenbankspalte vom Typ IDENTITY zugeordnet ist. Der für diese Anmerkung angegebene Wert definiert, wie die entsprechende Spalte vom Typ IDENTITY in der Datenbank aktualisiert wird.|[Verwenden der Anmerkungen 'sql:identity' und 'sql:guid'](using-the-sql-identity-and-sql-guid-annotations.md)|Nicht unterstützt|  
|`sql:inverse`|Weist die Update Gram Logik an, die Interpretation der über-/Unterordnungsbeziehung umzukehren, die mithilfe von ** \< SQL: Relationship>** angegeben wurde.|[Angeben des SQL: inverse-Attributs für SQL: Relationship &#40;SQLXML 4,0&#41;](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)|Nicht unterstützt|  
|`sql:is-constant`|Erstellt ein XML-Element, das keiner Tabelle zugeordnet wird. Das Element wird in der Abfrageausgabe angezeigt.|[Erstellen konstanter Elemente mithilfe von SQL: is-constant &#40;SQLXML 4,0&#41;](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)|identisch|  
|`sql:key-fields`|Damit können Sie Spalten angeben, mit denen die Zeilen in einer Tabelle eindeutig identifiziert werden.|[Identifizieren von Schlüssel Spalten mithilfe von SQL: key-fields &#40;SQLXML 4,0&#41;](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)|identisch|  
|`sql:limit-field`<br /><br /> `sql:limit-value`|Damit können Sie die Werte beschränken, die auf Grundlage eines beschränkenden Werts zurückgegeben werden.|[Filtern von Werten mit ' SQL: limit-field ' und ' SQL: limit-value ' &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)|identisch|  
|`sql:mapped`|Damit können Schemaelemente vom Ergebnis ausgeschlossen werden.|[Ausschließen von Schema Elementen aus dem resultierenden XML-Dokument mithilfe von SQL: zugeordnet &#40;SQLXML 4,0&#41;](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)|`map-field`|  
|`sql:max-depth`|Damit kann die Tiefe in rekursiven, im Schema angegebenen Beziehungen angegeben werden.|[Angeben der Tiefe von rekursiven Beziehungen mit 'sql:max-depth'](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)|Nicht unterstützt|  
|`sql:overflow-field`|Identifiziert die Datenbankspalte, die die Überlaufdaten enthält.|[Abrufen von nicht verbrauchten Daten mithilfe von ' SQL: overflow-field &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)|identisch|  
|`sql:prefix`|Erstellt die gültigen XML-Attribute ID, IDREF und IDREFS. Stellt den Werten von ID, IDREF und IDREFS eine Zeichenfolge voran.|[Erstellen gültiger Attribute vom Typ ID, IDREF und IDREFS mithilfe von SQL: Prefix &#40;SQLXML 4,0&#41;](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)|identisch|  
|`sql:relationship`|Gibt Beziehungen zwischen XML-Elementen an. Die Beziehung wird mithilfe der Attribute `parent`, `child`, `parent-key` und `child-key` festgelegt.|[Angeben von Beziehungen mithilfe von ' SQL: Relationship ' &#40;SQLXML 4,0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)|Die Attributnamen lauten anders:<br /><br /> `key-relation`<br /><br /> `foreign-relation`<br /><br /> `key`<br /><br /> `foreign-key`|  
|`sql:use-cdata`|Damit kann festgelegt werden, dass für bestimmte Elemente im XML-Dokument CDATA-Abschnitte verwendet werden.|[Erstellen von CDATA-Abschnitten mit SQL: use-cdata &#40;SQLXML 4,0&#41;](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)|identisch|  
  
> [!NOTE]  
>  Das systemeigene XSD-Attribut `targetNamespace` ersetzt die `target-namespace`-Anmerkung, die mit dem XDR-Zuordnungsschema von [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] eingeführt wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben eines Ziel Namespace mit dem targetNamespace-Attribut &#40;SQLXML 4,0&#41;](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
  
  
