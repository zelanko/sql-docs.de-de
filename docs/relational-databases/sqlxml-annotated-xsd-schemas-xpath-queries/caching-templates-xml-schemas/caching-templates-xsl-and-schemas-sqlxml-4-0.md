---
title: Zwischenspeichern von Vorlagen, XSL und Schemas (SQLXML)
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6201cd2cf27e48f5a5101c3bdcda4da644756a13
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75246693"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a>Zwischenspeichern von Vorlagen, XSL und Schemas (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Um die Leistung zu verbessern, unterstützt [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 das Zwischenspeichern von Vorlagen, XSL und Schemas.  
  
 Alle Schemas, Vorlagen und XSL-Dateien (mit Ausnahme der Dateien aus einem https://-oder FTP://-Speicherort) werden zwischengespeichert. Die zwischengespeicherten Dateien bleiben im Arbeitsspeicher, während der Prozess ausgeführt wird. Wenn der Prozess beendet wird, geht der gesamte Cacheinhalt verloren. Wenn Sie nur einen Prozess pro Abfrage ausführen, ist der Vorteil der Zwischenspeicherung möglicherweise nicht erkennbar.  
  
 Die Themen in diesem Abschnitt liefern weitere Informationen über das Zwischenspeichern:  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Zwischenspeichern von Vorlagen &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/template-caching-sqlxml-4-0.md)  
 Beschreibt einen Registrierungsschlüssel zum Zwischenspeichern von Vorlagen und stellt ihn bereit.  
  
 [XSL-Caching &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
 Beschreibt einen Registrierungsschlüssel zum Zwischenspeichern von XSL und stellt ihn bereit.  
  
 [Schema Caching &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)  
 Erläutert Probleme der parallelen Installation in SQLXML, die beim Zwischenspeichern von Schemas auftreten können, und stellt Registrierungsschlüssel für das Zwischenspeichern von Schemas bereit.  
  
  
