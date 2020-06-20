---
title: 'Angeben des SQL: inverse-Attributs für SQL: Relationship (SQLXML 4,0) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b0781102371b98cced72a5a0edee70c9567c372
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85003073"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a>Angeben des sql:inverse-Attributs für sql:relationship (SQLXML 4.0)
  Das `sql:inverse`-Attribut ist nur dann nützlich, wenn das XSD-Schema zum Massenladen oder von einem Updategram verwendet wird. Das- `sql:inverse` Attribut kann für das- **\<sql:relationship>** Element angegeben werden. In Updategrams interpretiert die Updategramlogik das Schema beim Bestimmen der Tabellen und Spalten, die durch den Updategramvorgang aktualisiert werden. Die im Schema angegebenen Über-/Unterordnungsbeziehungen legen die Reihenfolge fest, in der die Datensätze modifiziert (eingefügt oder gelöscht) werden.  
  
 Wenn ein XSD-Schema gegeben ist, in dem die Über-/Unterordnungsbeziehung invers zur Primär-/Fremdschlüssel-Beziehung zwischen den zugehörigen Datenbankspalten angegeben ist, dann schlägt der Updategramvorgang zum Einfügen oder Löschen wegen der Primär-/Fremdschlüsselverletzung fehl. In solchen Fällen wird das `sql:inverse` -Attribut ( `sql:inverse="true"` ) im **\<sql:relationship>** -Element angegeben, und die Update Gram Logik kehrt die Interpretation der im Schema angegebenen über-/Unterordnungsbeziehung um.  
  
 Das `sql:inverse`-Attribut akzeptiert einen booleschen Wert (0 = false, 1 = true). Zulässig sind die Werte 0, 1, true und false.  
  
 Ein funktionierendes Beispiel mit der-Anmerkung `sql:inverse` finden Sie unter [Angeben eines Mapping-Schemas mit Anmerkungen in einem Update Gram](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben von Beziehungen mithilfe von ' SQL: Relationship ' &#40;SQLXML 4,0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  
