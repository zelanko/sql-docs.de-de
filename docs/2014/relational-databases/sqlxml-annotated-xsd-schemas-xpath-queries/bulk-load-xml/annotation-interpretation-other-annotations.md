---
title: Andere Anmerkungen (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- url-encode annotation
- sql:key-fields
- use-cdata annotation
- sql:is-mapping-schema
- sql:url-encode
- sql:id-prefix
- sql:use-cdata
- key-fields annotation
- id-prefix annotation [SQLXML]
- is-mapping-schema annotation
ms.assetid: f7b4d37b-d6d3-4ac3-b2fd-a0b534a924e4
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 01e0af9b72790b8a2ddf396434c84f25ee270313
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37223130"
---
# <a name="other-annotations-sqlxml-40"></a>Andere Anmerkungen (SQLXML 4.0)
  Neben den in den vorherigen Themen in diesem Abschnitt beschriebenen Anmerkungen interpretiert XML-Massenladen diese anderen Anmerkungen folgendermaßen:  
  
 `sql:id-prefix`  
 Wenn das Schema Präfixe für die XML-Daten festlegt, entfernt XML-Massenladen die Präfixe, bevor die Daten an Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gesendet werden.  
  
 `sql:use-cdata`  
 XML-Massenladen liest der Text an, die in den CDATA gespeichert sind, Abschnitte und sendet sie an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 `sql:url-encode`  
 XML-Massenladen unterstützt diese Anmerkung nicht. Eine in der XML-Dateneingabe angegebene URL wird beispielsweise von XML-Massenladen an diesem Speicherort nicht gelesen, sodass sie in der Datenbank gespeichert werden kann.  
  
 `sql:is-mapping-schema`  
 XML-Massenladen unterstützt weder diese Anmerkung noch `sql:id`.  
  
> [!NOTE]  
>  XML-Massenladen unterstützt keine Inlinezuordnungsschemas.  
  
 `sql:key-fields`  
 XML-Massenladen ignoriert stets diese Anmerkung.  
  
## <a name="see-also"></a>Siehe auch  
 [Interpretation von Anmerkungen &#40;SQLXML 4.0&#41;](annotation-interpretation-sqlxml-4-0.md)  
  
  
