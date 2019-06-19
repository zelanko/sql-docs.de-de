---
title: 'Angeben des SQL: Inverse-Attributs für SQL: Relationship (SQLXML 4.0) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- bulk load [SQLXML]
- inverse attribute
- relationships [SQLXML], inverse orders
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- updategrams [SQLXML], relationships
- sql:inverse
ms.assetid: 08904cbd-9c86-493d-90c3-f5e1d13ce59d
author: MightyPen
ms.author: genemi
ms.reviewer: ''
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1d8a6390ded6250355936dbef29051f76be14266
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65980695"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a>Angeben des sql:inverse-Attributs für sql:relationship (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Die **SQL: inverse** Attribut ist nützlich, nur wenn das XSD-Schema zum Massenladen oder von einem Updategram verwendet wird. Die **SQL: inverse** -Attribut angegeben werden, auf die  **\<SQL: Relationship >** Element. In Updategrams interpretiert die Updategramlogik das Schema beim Bestimmen der Tabellen und Spalten, die durch den Updategramvorgang aktualisiert werden. Die im Schema angegebenen Über-/Unterordnungsbeziehungen legen die Reihenfolge fest, in der die Datensätze modifiziert (eingefügt oder gelöscht) werden.  
  
 Wenn ein XSD-Schema gegeben ist, in dem die Über-/Unterordnungsbeziehung invers zur Primär-/Fremdschlüssel-Beziehung zwischen den zugehörigen Datenbankspalten angegeben ist, dann schlägt der Updategramvorgang zum Einfügen oder Löschen wegen der Primär-/Fremdschlüsselverletzung fehl. In solchen Fällen die **SQL: inverse** -Attribut angegeben ist (**SQL: Inverse = "true"** ) in der  **\<SQL: Relationship >** Element, und die updategramlogik Gegenstücke der Interpretation der über-/ unterordnungsbeziehung im Schema angegeben.  
  
 Die **SQL: inverse** Attribut akzeptiert einen booleschen Wert (0 = False, 1 = True). Zulässig sind die Werte 0, 1, true und false.  
  
 Für eine funktionierende Beispiel mit der **SQL: inverse** Anmerkung, finden Sie unter [angeben eines Zuordnungsschemas in einem Updategram](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Angeben von Beziehungen mithilfe von SQL: Relationship &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  
