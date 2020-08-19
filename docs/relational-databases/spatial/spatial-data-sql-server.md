---
description: Räumliche Daten (SQL Server)
title: Räumliche Daten (SQL Server) | Microsoft-Dokumentation
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
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
author: MladjoA
ms.author: mlandzic
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 38df38923b69bf24432cf4d5d162187c0962fcfc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88403346"
---
# <a name="spatial-data-sql-server"></a>Räumliche Daten (SQL Server)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Räumliche Daten repräsentieren Daten zur physischen Position und Form geometrischer Objekte. Diese Objekte können Punktpositionen oder komplexere Objekte wie Länder, Straßen oder Seen sein.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt zwei Typen von räumlichen Daten: den Datentyp **geometry** und den Datentyp **geography** .  
  
-   Der **geometry** -Datentyp stellt Daten in einem euklidischen (flachen) Koordinatensystem dar.  
  
-   Der **geography** -Datentyp stellt Daten in einem Erdkugel-Koordinatensystem dar.  
  
 Beide Datentypen werden als .NET CLR (Common Language Runtime)-Datentypen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]implementiert.  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> Verwandte Aufgaben  
 [Erstellen, Aufbauen und Abfragen von geometry-Instanzen](../../relational-databases/spatial/create-construct-and-query-geometry-instances.md)  
 Beschreibt die Methoden, die mit Instanzen des geometry-Datentyps verwendet werden können.  
  
 [Erstellen, Aufbauen und Abfragen von geography-Instanzen](../../relational-databases/spatial/create-construct-and-query-geography-instances.md)  
 Beschreibt die Methoden, die mit Instanzen des geography-Datentyps verwendet werden können.  
  
 [Abfragen von nächsten Nachbarn aus räumlichen Daten](../../relational-databases/spatial/query-spatial-data-for-nearest-neighbor.md)  
 Beschreibt das allgemeine Abfragemuster, das zum Suchen der räumlichen Objekte, die einem bestimmten räumlichen Objekt am nächsten liegen, verwendet wird.  
  
 [Erstellen, Ändern und Löschen von räumlichen Indizes](../../relational-databases/spatial/create-modify-and-drop-spatial-indexes.md)  
 Stellt Informationen zum Erstellen, Ändern und Löschen eines räumlichen Indexes bereit.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Übersicht über räumliche Datentypen](../../relational-databases/spatial/spatial-data-types-overview.md)  
 Bietet eine Einführung in die räumlichen Datentypen.  
  
-   [Point](../../relational-databases/spatial/point.md)  
  
-   [LineString](../../relational-databases/spatial/linestring.md)  
  
-   [CircularString](../../relational-databases/spatial/circularstring.md)  
  
-   [CompoundCurve](../../relational-databases/spatial/compoundcurve.md)  
  
-   [Polygon](../../relational-databases/spatial/polygon.md)  
  
-   [CurvePolygon](../../relational-databases/spatial/curvepolygon.md)  
  
-   [MultiPoint](../../relational-databases/spatial/multipoint.md)  
  
-   [MultiLineString](../../relational-databases/spatial/multilinestring.md)  
  
-   [MultiPolygon](../../relational-databases/spatial/multipolygon.md)  
  
-   [GeometryCollection](../../relational-databases/spatial/geometrycollection.md)  
  
 [Übersicht über räumliche Indizes](../../relational-databases/spatial/spatial-indexes-overview.md)  
 Bietet eine Einführung in räumliche Indizes und beschreibt Mosaik und Mosaikschemas.  
  
  
