---
description: EnvelopeCenter (geography-Datentyp)
title: EnvelopeCenter (geography-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- EnvelopeCenter
- EnvelopeCenter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeCenter method
ms.assetid: dee9d807-faad-45b8-b3f3-7e8aa7d07147
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: c6e7173111dd48e54c85410b89d5a450adfe1169
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88459075"
---
# <a name="envelopecenter-geography-data-type"></a>EnvelopeCenter (geography-Datentyp)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Gibt einen Punkt zurück, den Sie als Mittelpunkt eines umschließenden Kreises für die **geography**-Instanz verwenden können.  
  
Jeder Punkt in der Instanz wird als Vektor beschrieben. Um den umschließenden Kreis zu ermitteln, erstreckt sich der Vektor vom Erdmittelpunkt zu dem Punkt auf der Erdoberfläche. Der Mittelpunkt des umschließenden Kreises wird berechnet, indem der Durchschnitt aller Vektoren ermittelt wird. Für geschlossene Schleifen in einer **polygon**-Instanz oder **linestring**-Instanz werden der erste und letzte Punkt nur einmal verwendet.  
  
Diese **geography** -Datentypmethode unterstützt Instanzen von **FullGlobe** oder räumliche Instanzen, die größer als eine Hemisphäre sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
EnvelopeCenter( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Rückgabetypen
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Rückgabetyp: **geography**  
  
CLR-Rückgabetyp: **SqlGeography**  
  
## <a name="remarks"></a>Bemerkungen  
Diese Methode gibt einen **point**zurück. Bei Verwendung mit `EnvelopeAngle()`gibt `EnvelopeCenter()` einen umschließenden Kreis einer **geography** -Instanz verwendet werden kann.  
  
> [!NOTE]  
>  `EnvelopeCenter()`gibt einen umschließenden Kreis für eine **geography**-Instanz zurück. Es wird jedoch nicht garantiert, dass die Ergebnisse den minimalen umschließenden Kreis erstellen. Im Gegensatz dazu ist für die Methode **geometry** vom `STEnvelope()` -Datentyp garantiert, dass sie den minimalen Begrenzungsrahmen zurückgibt, wenn sie auf eine **geometry** -Instanz verwendet werden kann.  
  
In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher wird der Mittelpunkt des Kreises zurückgegeben, der den Umschlag dieser Instanz als **point** darstellt. Für alle großen Objekte, wie von `EnvelopeAngle()` = 180 definiert, wird (90,0) von `EnvelopeCenter()` zurückgegeben.  
  
Diese Methode ist nicht exakt.  
  
## <a name="examples"></a>Beispiele  
  
```  
DECLARE @g geography = 'LINESTRING(-120 45, -120 0, -90 0)';  
SELECT @g.EnvelopeCenter().ToString();  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[Erweiterte Methoden für geography-Instanzen](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
[EnvelopeAngle &#40;geography-Datentyp&#41;](../../t-sql/spatial-geography/envelopeangle-geography-data-type.md)  
  
  
