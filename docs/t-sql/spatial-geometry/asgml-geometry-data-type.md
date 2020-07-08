---
title: AsGml (geometry-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- AsGml(geometry_Data_Type)_TSQL
- AsGml
- AsGml(geometry Data Type)
- AsGml_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- AsGml (geometry Data Type)
ms.assetid: f6c2e130-05f3-4ef3-921b-d78b51437d48
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: f6d1cac186583ea5b3eea58d92946f959d4c6105
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85700936"
---
# <a name="asgml-geometry-data-type"></a>AsGml (geometry-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt die GML (Geography Markup Language)-Darstellung einer **geometry** -Instanz zurück.
  
Weitere Informationen über GML (Geography Markup Language) finden Sie in der folgenden OGC (Open Geospatial Consortium)-Spezifikation:[OGC Specifications, Geography Markup Language.](https://go.microsoft.com/fwlink/?LinkId=93629)
  
## <a name="syntax"></a>Syntax  
  
```  
  
.AsGml ( )  
```  
  
## <a name="return-types"></a>Rückgabetypen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **xml**  
  
 CLR-Rückgabetyp: **SqlXml**  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine `LineString` -Instanz erstellt und mithilfe von `AsGML()` die GML-Beschreibung der Instanz zurückgegeben.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 0 1, 1 0)', 0)  
SELECT @g.AsGml();  
```  
  
 Diese Methode gibt die Beschreibung als `LineString` -Instanz zurück.  
  
```  
<LineString xmlns="https://www.opengis.net/gml">  
<posList>0 0 0 1 1 0</posList></LineString>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweiterte Methoden für geometry-Instanzen](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

