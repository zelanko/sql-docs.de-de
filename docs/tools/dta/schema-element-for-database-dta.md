---
title: Schema-Element für Datenbank (DTA)
description: Im Hilfsprogramm „DTA“ gibt das Element „Schema“ für die Datenbank das Schema der Datenbank an, die Sie optimieren möchten.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Schema element
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: ee28954c4206e2e26edfa567bae5a1b282d41dea
ms.sourcegitcommit: b8933ce09d0e631d1183a84d2c2ad3dfd0602180
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83151814"
---
# <a name="schema-element-for-database-dta"></a>Schema-Element für Datenbank (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Gibt das Schema der zu optimierenden Datenbank an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Database>  
...code removed here...  
    <Schema>...</Schema>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|BESCHREIBUNG|  
|--------------------|-----------------|  
|**Datentyp und -länge**|Keine.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Einmalig erforderlich für das **Database** -Element, das unter dem **Server** -Element angegeben ist.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Database-Element für Server &#40;DTA&#41;](../../tools/dta/database-element-for-server-dta.md)|  
|**Untergeordnete Elemente**|[Name-Element für Schema &#40;DTA&#41;](../../tools/dta/name-element-for-schema-dta.md)<br /><br /> [Table-Element für Schema &#40;DTA&#41;](../../tools/dta/table-element-for-schema-dta.md)|  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung dieses Elements finden Sie unter [Server-Element &#40;DTA&#41;](../../tools/dta/server-element-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
