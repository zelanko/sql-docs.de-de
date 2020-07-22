---
title: MakeValid (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- MakeValid method (geography)
ms.assetid: f67038e3-4f62-4465-994e-e95ac27d8ada
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 86fb119dfaac7f8069aba96402b5f2a0bab31a88
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86556160"
---
# <a name="makevalid-geography-data-type"></a>MakeValid (geography-Datentyp)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Konvertiert eine ungültige **geography**-Instanz in eine gültige **geography**-Instanz mit einem gültigen Open Geospatial-Consortium-Typ (OGC).  
  
 Wenn von einem Eingabeobjekt FALSE für STIsValid() zurückgegeben wird, konvertiert `MakeValid()` die ungültige in eine gültige Instanz.  
  
 Diese geography-Datentypmethode unterstützt Instanzen von **FullGlobe** oder räumliche Instanzen, die größer als eine Hemisphäre sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
.MakeValid ()  
```  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
 CLR-Rückgabetyp: **SqlGeography**  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ändert möglicherweise den Typ der Instanz von **geography**. Darüber hinaus ist eine geringfügige Verschiebung der Punkte der Instanz von **geography** möglich. Die Ergebnisse einiger Methoden wie NumPoint() können sich ändern.  
  
 In Fällen, in denen die ungültige räumliche Instanz den Äquator schneidet und einen EnvelopeAngle() = 180 aufweist, wird eine Instanz von **FullGlobe** zurückgegeben. Die `MakeValid()`**geography**-Datentypmethode versucht, gültige Instanzen zurückzugeben. Die Richtigkeit oder Vollständigkeit der Ergebnisse kann jedoch nicht garantiert werden.  
  
> [!NOTE]  
>  Objekte, die nicht gültig sind, können in der Datenbank gespeichert werden. Für ungültige Instanzen (für die von STIsValid() FALSE zurückgegeben wird) können Methoden verwendet werden, die die Gültigkeit überprüfen oder Exporte ermöglichen: STIsValid(), MakeValid(), STAsText(), STAsBinary(), ToString(), AsTextZM() und AsGml().  
  
 Diese Methode ist nicht exakt.  
  
## <a name="examples"></a>Beispiele  
 Im ersten Beispiel wird eine ungültige `LineString` -Instanz erstellt, die sich selbst überlappt. Mithilfe von `STIsValid()` wird die Ungültigkeit dieser Instanz bestätigt. `STIsValid()` gibt für eine ungültige Instanz den Wert 0 (null) zurück.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('LINESTRING(0 2, 1 1, 1 0, 1 1, 2 2)', 4326);  
SELECT @g.STIsValid();  
```  
  
 Im zweiten Beispiel wird die Instanz mit `MakeValid()` gültig gemacht, und die tatsächliche Gültigkeit wird überprüft. `STIsValid()` gibt für eine gültige Instanz den Wert 1 zurück.  
  
```  
SET @g = @g.MakeValid();  
SELECT @g.STIsValid();  
```  
  
 Das dritte Beispiel überprüft, ob die Instanz zu einer gültigen Instanz geändert wurde.  
  
```  
SELECT @g.ToString();  
```  
  
 Wenn in diesem Beispiel die `LineString` -Instanz ausgewählt wird, werden die Werte als gültige `MultiLineString` -Instanz zurückgegeben.  
  
```  
MULTILINESTRING ((0 2, 1 1, 2 2), (1 1, 1 0))  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [STIsValid &#40;geometry-Datentyp&#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)   
 [Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
