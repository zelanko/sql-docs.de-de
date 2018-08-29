---
title: Zwischenspeichern von Vorlagen (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4db2ada968947442f031308bb1b10a50b68be144
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43061269"
---
# <a name="template-caching-sqlxml-40"></a>Zwischenspeichern von Vorlagen (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Das Zwischenspeichern von Vorlagen verbessert die Leistung erheblich. Wenn das Zwischenspeichern von Vorlagen festgelegt ist, verbleibt die Vorlage nach ihrer ersten Ausführung im Arbeitsspeicher. Auf diese Weise wird die Leistung der nächsten Vorlagenausführung verbessert.  
  
 Sie können die Cachegröße für Vorlagen festlegen, indem Sie den folgenden Schlüssel in der Registrierung hinzufügen:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 Die Größe sollte auf Basis des vorhandenen Arbeitsspeichers und der Anzahl der von Ihnen verwendeten Vorlagen festgelegt werden. Die Standardeinstellung **TemplateCacheSize** lautet 31. Sie können die Cachegröße erhöhen, wenn der Vorlagenzugriff langsam erscheint, oder die Cachegröße verringern, wenn der Arbeitsspeicher zu gering ist.  
  
 Aus Leistungsgründen wird empfohlen, dass Sie festlegen, **TemplateCacheSize** höher als die Anzahl der Vorlagen, die Sie in der Regel verwenden. Wenn **Templatecachesize** ist kleiner als die Anzahl der Vorlagen, die Sie verfügen, Leistung beeinträchtigt wird, als die Anzahl der Vorlagen zunimmt. Die **TemplateCacheSize** kann auf ein Maximum von 128 festgelegt werden.  
  
 Jedes Mal, wenn eine zwischengespeicherte Vorlage verwendet wird, wird die Änderungszeit der Vorlagendatei überprüft, um festzustellen, ob sie aktualisiert werden muss. Das liegt daran, dass die Datenträgerkopie neuer als die Cachekopie ist.  
  
> [!NOTE]  
>  Vorlagenparameter und Befehlseigenschaften werden nicht zwischengespeichert.  
  
## <a name="see-also"></a>Siehe auch  
 [Das Zwischenspeichern von Schemas &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/schema-caching-sqlxml-4-0.md)   
 [XSL-zwischenspeichern &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/caching-templates-xml-schemas/xsl-caching-sqlxml-4-0.md)  
  
  
