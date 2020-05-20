---
title: Table-Element für Schema (DTA)
description: Im dta-Hilfsprogramm gibt das Table-Element für Schema die Tabelle für die Optimierung an. In diesem Artikel wird dieses Element beschrieben.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: c7c6e1c260d91f5c835117463ac82495ec7873f8
ms.sourcegitcommit: b8933ce09d0e631d1183a84d2c2ad3dfd0602180
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83151515"
---
# <a name="table-element-for-schema-dta"></a>Table-Element für Schema (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Gibt die Tabelle zum Optimieren an.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## <a name="element-attributes"></a>Elementattribute  
  
|attribute|BESCHREIBUNG|  
|---------------|-----------------|  
|**NumberOfRows**|Optional. Eine ganze Zahl, mit der Sie Tabellen unterschiedlicher Größe simulieren können.|  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|BESCHREIBUNG|  
|--------------------|-----------------|  
|**Datentyp und -länge**|**string**, 1 bis 255 Zeichen.|  
|**Standardwert**|Keine.|  
|**Vorkommen**|Optional. Sie können beliebig viele Tabellen für die Arbeitsauslastung auflisten.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Elemente|  
|------------------|--------------|  
|**Übergeordnetes Element**|[Schema-Element für Datenbank &#40;DTA&#41;](../../tools/dta/schema-element-for-database-dta.md)|  
|**Untergeordnete Elemente**|[Name-Element für Tabelle &#40;DTA&#41;](../../tools/dta/name-element-for-table-dta.md)|  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie kein **Table** -Element angeben, geht der Datenbankoptimierungsratgeber davon aus, dass sich alle Tabellen in der angegebenen Datenbank optimieren lassen.  
  
## <a name="example"></a>Beispiel  
 Ein Beispiel für die Verwendung finden Sie unter [Server-Element &#40;DTA&#41;](../../tools/dta/server-element-dta.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [XML-Eingabedateireferenz &#40;Datenbankoptimierungsratgeber&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
