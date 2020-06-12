---
title: Schema Caching (SQLXML)
description: Erfahren Sie, wie Sie mithilfe von Registrierungs Schlüsseln das Zwischenspeichern von Schemas explizit steuern und die Leistung einer XPath-Abfrage in SQLXML 4,0 verbessern.
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- schemas [SQLXML]
ms.assetid: 7e5fda21-b435-41fd-b637-8b616560a93f
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ca7eb937f75575dd34e1857209605aeb74a2d1d6
ms.sourcegitcommit: 9921501952147b9ce3e85a1712495d5b3eb13e5b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2020
ms.locfileid: "84215794"
---
# <a name="schema-caching-sqlxml-40"></a>Zwischenspeichern von Schemas (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Bei einer parallelen Installation von XML for Microsoft SQL Server 2000 Web Release 1, Microsoft SQLXML 2.0 und SQLXML 3.0 können Sie das Zwischenspeichern von Schemas in allen Versionen mit den folgenden Registrierungsschlüsseln explizit steuern:  
  
 Web Release 1:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXMLX\SchemaCacheSize  
```  
  
 SQLXML 2,0:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML2\SchemaCacheSize  
```  
  
 SQLXML 3.0:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML3\SchemaCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 Weitere Informationen zur parallelen Installation finden Sie unter [What es New in SQLXML 4,0 SP1](../../../relational-databases/sqlxml/what-s-new-in-sqlxml-4-0-sp1.md).  
  
 Das Zwischenspeichern von Schemas verbessert die Leistung einer XPath-Abfrage deutlich. Wenn eine XPath-Abfrage für ein Zuordnungsschema ausgeführt wird, wird das Schema im Arbeitsspeicher gespeichert und werden die notwendigen Datenstrukturen im Arbeitsspeicher erstellt. Wenn das Zwischenspeichern von Schemas festgelegt ist, bleibt das Schema im Arbeitsspeicher und verbessert dadurch die Leistung für nachfolgende XPath-Abfragen.  
  
 Sie können die Größe des Schemacache durch Hinzufügen des oben angegebenen Schlüssels in der Registrierung hinzufügen.  
  
 Die Schemagröße wird basierend auf dem zur Verfügung stehenden Arbeitsspeicher und der Anzahl von Schemas festgelegt, die Sie verwenden. Die Standardgröße von **SchemaCacheSize** beträgt 31. Wenn Sie **SchemaCacheSize** höher festlegen, wird mehr Arbeitsspeicher verwendet. Sie können somit die Cachegröße erhöhen, wenn der Schemazugriff langsam erscheint, oder die Cachegröße verringern, wenn der Arbeitsspeicher zu gering ist.  
  
 Aus Leistungsgründen empfiehlt es sich, " **SchemaCacheSize** " auf einen höheren Wert als die Anzahl der Zuordnungsschemas festzulegen, die Sie normalerweise verwenden. Wenn die Anzahl der Schemas zunimmt, wird die Leistung beeinträchtigt, wenn **SchemaCacheSize** kleiner ist als die Anzahl der Schemas, die Sie besitzen.  
  
> [!NOTE]  
>  Während der Entwicklung empfiehlt es sich, die Schemas nicht zwischenzuspeichern, da Änderungen an den Schemas im Zwischenspeicher erst nach zwei Minuten enthalten sind.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zwischenspeichern von Vorlagen &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)   
 [XSL-Caching &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
  
  
