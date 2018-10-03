---
title: Räumliche Daten (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- dbe-spatial
ms.topic: conceptual
helpviewer_keywords:
- geography data type [SQL Server], spatial storage design
- planar spatial data [SQL Server], designing
- spatial data types [SQL Server]
- geodetic spatial data [SQL Server]
- geometry data type [SQL Server], spatial storage design
- spatial storage [SQL Server]
- geodetic spatial data [SQL Server], designing
ms.assetid: 41a132a1-09e2-4426-b9df-225270cb8e15
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f25de7e1aa60d482d5256470d3fb2e1ada08f356
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222170"
---
# <a name="spatial-data-sql-server"></a>Räumliche Daten (SQL Server)
  Räumliche Daten stellen Informationen über die physische Position und die Form geometrischer Objekte dar. Bei diesen Objekten kann es sich um Punktpositionen oder komplexere Objekte handeln, z.&nbsp;B. Länder, Straßen oder Seen.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt zwei Typen von räumlichen Daten: den `geometry`-Datentyp und den `geography`-Datentyp.  
  
-   Der `geometry`-Typ stellt Daten in einem euklidischen (flachen) Koordinatensystem dar.  
  
-   Die `geography` Typ stellt Daten in einem Erdkugel-Koordinatensystem dar.  
  
 Beide Datentypen werden als .NET CLR (Common Language Runtime)-Datentypen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]implementiert.  
  
> [!IMPORTANT]  
>  Laden Sie für eine ausführliche Beschreibung und Beispiele der in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]eingeführten räumlichen Funktionen das Whitepaper [Neue räumliche Funktionen in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=226407)herunter.  
  
##  <a name="reltasks"></a> Verwandte Aufgaben  
 [Erstellen, Aufbauen und Abfragen von geometry-Instanzen](create-construct-and-query-geometry-instances.md)  
 Beschreibt die Methoden, die mit Instanzen des geometry-Datentyps verwendet werden können.  
  
 [Erstellen, Aufbauen und Abfragen von geography-Instanzen](create-construct-and-query-geography-instances.md)  
 Beschreibt die Methoden, die mit Instanzen des geography-Datentyps verwendet werden können.  
  
 [Abfragen von nächsten Nachbarn aus räumlichen Daten](query-spatial-data-for-nearest-neighbor.md)  
 Beschreibt das allgemeine Abfragemuster, das zum Suchen der räumlichen Objekte, die einem bestimmten räumlichen Objekt am nächsten liegen, verwendet wird.  
  
 [Erstellen, Ändern und Löschen von räumlichen Indizes](create-modify-and-drop-spatial-indexes.md)  
 Stellt Informationen zum Erstellen, Ändern und Löschen eines räumlichen Indexes bereit.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Übersicht über räumliche Datentypen](spatial-data-types-overview.md)  
 Bietet eine Einführung in die räumlichen Datentypen.  
  
-   [Punkt](point.md)  
  
-   [LineString](linestring.md)  
  
-   [CircularString](circularstring.md)  
  
-   [CompoundCurve](compoundcurve.md)  
  
-   [Polygon](polygon.md)  
  
-   [CurvePolygon](curvepolygon.md)  
  
-   [MultiPoint](multipoint.md)  
  
-   [MultiLineString](multilinestring.md)  
  
-   [MultiPolygon](multipolygon.md)  
  
-   [GeometryCollection](geometrycollection.md)  
  
 [Übersicht über räumliche Indizes](spatial-indexes-overview.md)  
 Bietet eine Einführung in räumliche Indizes und beschreibt Mosaik und Mosaikschemas.  
  
  
