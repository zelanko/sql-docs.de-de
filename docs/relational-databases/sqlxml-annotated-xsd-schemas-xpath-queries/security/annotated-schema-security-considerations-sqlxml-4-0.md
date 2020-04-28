---
title: Überlegungen zur Schema Sicherheit mit Anmerkungen (SQLXML)
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping schema [SQLXML], security
- annotated XDR schemas, security
- XDR schemas [SQLXML], security
- annotations [SQLXML]
- annotated XSD schemas, security
- SQLXML, annotated XSD schemas
- SQLXML, annotated XDR schemas
- security [SQLXML], annotated schemas
- XSD schemas [SQLXML], security
ms.assetid: 7d7e44dc-b6d3-4e0f-95c7-8f99930c94f2
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 87af92866658e2fa5b4f8648e2a22dbf3d1cb13f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "75252512"
---
# <a name="annotated-schema-security-considerations-sqlxml-40"></a>Überlegungen zur Sicherheit von Schemas mit Anmerkungen (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Im Folgenden werden Sicherheitsrichtlinien zur Verwendung von Schemas mit Anmerkungen gegeben:  
  
-   Vermeiden Sie die Verwendung der Standardzuordnung in den Zuordnungsschemas. Die Standardzuordnung macht die Datenbankinformationen (Tabellen- und Spaltennamen) im resultierenden XML-Dokument verfügbar, da standardmäßig die Elementnamen den Tabellennamen und die Attributnamen den Spaltennamen zugeordnet werden. Daher hat jeder Benutzer, der das XML-Dokument einsehen kann, auch Zugriff auf die Tabellen- und Spalteninformationen in der Datenbank, was ein mögliches Sicherheitsrisiko bedeutet. Geben Sie daher willkürlich gewählte Element- und Attributnamen im Schema an, und verwenden Sie Anmerkungen zur expliziten Zuordnung derselben zu den Tabellen und Spalten. Auf diese Weise wird das Sicherheitsrisiko vermieden. Weitere Informationen zum Verwenden der Standard Zuordnung beim Erstellen von XSD-Schemas finden Sie [unter Standard Zuordnung von XSD-Elementen und-Attributen zu Tabellen und Spalten &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md).  
  
-   Die mithilfe von Anmerkungen angegebene explizite Zuordnung macht die Datenbankinformationen (wie Tabellennamen und Spaltennamen) verfügbar. Daher werden Sie es möglicherweise vorziehen, diese Schemas nicht öffentlich verfügbar zu machen.  
  
-   Bestimmte Abfragen, wie z. b. die, die für die Zuordnung des Schemas mit Rekursion angegeben werden (angegeben mithilfe der **maximalen tiefen** Anmerkung, die auf einen höheren Wert festgelegt ist), können länger Sie können optional ein Timeout Limit angeben, indem Sie die Eigenschaft Befehls Timeout (in Sekunden) festlegen. Beispiel:  
  
    ```  
    cn.Open "Provider=SQLOLEDB;Server=localhost;Database=tempdb;Integrated Security=SSPI;Command Properties='Command Time Out=50';"  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [XSD-Schemas mit Anmerkungen in SQLXML 4.0](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xsd-schemas-in-sqlxml-4-0.md)  
  
  
