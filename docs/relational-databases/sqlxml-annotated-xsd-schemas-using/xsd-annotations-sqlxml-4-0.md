---
title: XSD-Anmerkungen (SQLXML)
description: Anzeigen einer Liste von XSD-Anmerkungen (SQLXML 4,0), die in SQL Server 2005 (9. x) eingeführt wurden, mit einem Vergleich der XDR-Anmerkungen, die in SQL Server 2000 (8. x) eingeführt wurden.
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
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: baf79cfd4048bad018df2314b9d891c47871f0d6
ms.sourcegitcommit: 5b7457c9d5302f84cc3baeaedeb515e8e69a8616
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83689226"
---
# <a name="xsd-annotations-sqlxml-40"></a>XSD-Anmerkungen (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In der folgenden Tabelle werden die mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] eingeführten XSD-Anmerkungen mit den mit [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] eingeführten XDR-Anmerkungen verglichen.  
  
|XSD-Anmerkung|Beschreibung|Themenlink|XDR-Anmerkung|  
|--------------------|-----------------|----------------|--------------------|  
|**sql:encode**|Ermöglicht bei der Zuordnung eines XML-Elements oder -Attributs zu einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-BLOB-Spalte die Abfrage eines Verweis-URIs. Dieser URI kann später verwendet werden, um BLOB-Daten zurückzugeben.|[Anfordern von URL-verweisen auf BLOB-Daten mithilfe von SQL: encode &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)|**URL-Codierung**|  
|**SQL: GUID**|Damit können Sie angeben, ob ein von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generierter GUID-Wert oder der im Updategram für diese Spalte angegebene Wert verwendet werden soll.|[Verwenden der Anmerkungen 'sql:identity' und 'sql:guid'](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)|Nicht unterstützt|  
|**sql:hide**|Blendet das im Schema angegebene Element oder Attribut im resultierenden XML-Dokument aus.|[Ausblenden von Elementen und Attributen mit sql:hide](../../relational-databases/sqlxml-annotated-xsd-schemas-using/hiding-elements-and-attributes-by-using-sql-hide.md)|Nicht unterstützt|  
|**sql:identity**|Kann in jedem Knoten angegeben werden, der einer Datenbankspalte vom Typ IDENTITY zugeordnet ist. Der für diese Anmerkung angegebene Wert definiert, wie die entsprechende Spalte vom Typ IDENTITY in der Datenbank aktualisiert wird.|[Verwenden der Anmerkungen 'sql:identity' und 'sql:guid'](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)|Nicht unterstützt|  
|**sql:inverse**|Weist die Update Gram Logik an, die Interpretation der über-/Unterordnungsbeziehung umzukehren, die mithilfe von ** \< SQL: Relationship>** angegeben wurde.|[Angeben des SQL: inverse-Attributs für SQL: Relationship &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)|Nicht unterstützt|  
|**sql:is-constant**|Erstellt ein XML-Element, das keiner Tabelle zugeordnet wird. Das Element wird in der Abfrageausgabe angezeigt.|[Erstellen konstanter Elemente mithilfe von SQL: is-constant &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)|identisch|  
|**sql:key-Felder**|Damit können Sie Spalten angeben, mit denen die Zeilen in einer Tabelle eindeutig identifiziert werden.|[Identifizieren von Schlüssel Spalten mithilfe von SQL: key-fields &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)|identisch|  
|**sql:limit-field**<br /><br /> **sql:limit-value**|Damit können Sie die Werte beschränken, die auf Grundlage eines beschränkenden Werts zurückgegeben werden.|[Filtern von Werten mit ' SQL: limit-field ' und ' SQL: limit-value ' &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/filtering-values-using-sql-limit-field-and-sql-limit-value-sqlxml-4-0.md)|identisch|  
|**sql:mapped**|Damit können Schemaelemente vom Ergebnis ausgeschlossen werden.|[Ausschließen von Schema Elementen aus dem resultierenden XML-Dokument mithilfe von SQL: zugeordnet &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)|**Map-Feld**|  
|**sql:max-depth**|Damit kann die Tiefe in rekursiven, im Schema angegebenen Beziehungen angegeben werden.|[Angeben der Tiefe von rekursiven Beziehungen mit 'sql:max-depth'](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)|Nicht unterstützt|  
|**sql:overflow-field**|Identifiziert die Datenbankspalte, die die Überlaufdaten enthält.|[Abrufen von nicht verbrauchten Daten mithilfe von ' SQL: overflow-field &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/retrieving-unconsumed-data-using-the-sql-overflow-field-sqlxml-4-0.md)|identisch|  
|**sql:prefix**|Erstellt die gültigen XML-Attribute ID, IDREF und IDREFS. Stellt den Werten von ID, IDREF und IDREFS eine Zeichenfolge voran.|[Erstellen gültiger Attribute vom Typ ID, IDREF und IDREFS mithilfe von SQL: Prefix &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)|identisch|  
|**sql:relationship**|Gibt Beziehungen zwischen XML-Elementen an. Die Attribute **Parent**, **Child**, **Parent-Key**und **Child Key** werden verwendet, um die Beziehung herzustellen.|[Angeben von Beziehungen mithilfe von ' SQL: Relationship ' &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)|Die Attributnamen lauten anders:<br /><br /> **Schlüssel Beziehung**<br /><br /> **fremd Beziehung**<br /><br /> **key**<br /><br /> **Fremdschlüssel**|  
|**sql:use-cdata**|Damit kann festgelegt werden, dass für bestimmte Elemente im XML-Dokument CDATA-Abschnitte verwendet werden.|[Erstellen von CDATA-Abschnitten mit SQL: use-cdata &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)|identisch|  
  
> [!NOTE]  
>  Das systemeigene XSD- **targetNamespace** -Attribut ersetzt die **Target-Namespace** -Anmerkung, die im XDR-Zuordnungsschema eingeführt wurde [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben eines Ziel Namespace mit dem targetNamespace-Attribut &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
  
  
