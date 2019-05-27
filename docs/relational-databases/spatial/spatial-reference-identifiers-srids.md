---
title: SRIDs (Spatial Reference Identifiers) | Microsoft Dokumentation
ms.date: 03/29/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Spatial Reference Identifiers (SRIDs)
- geodetic spatial data [SQL Server], identifiers
- SRID
ms.assetid: 0612658a-7d1b-4178-bdc2-42b914ea31a7
author: MladjoA
ms.author: mlandzic
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ebeda52e81bbc3c3aaa8fab446ae74c3169970f9
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2019
ms.locfileid: "66015199"
---
# <a name="spatial-reference-identifiers-srids"></a>SRIDs (Spatial Reference Identifiers)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Jede räumliche Instanz hat einen SRID (Spatial Reference Identifier), einen räumlichen Referenzbezeichner. Der SRID bezieht sich auf ein räumliches Referenzsystem, das auf der jeweiligen Ellipsenform basiert, die für eine flache Erdabbildung oder runde Erdabbildung verwendet wird.  
  
 Eine räumliche Spalte kann Objekte mit unterschiedlichen SRIDs enthalten. Allerdings können nur räumliche Instanzen mit dem gleichen SRID verwendet werden, wenn Daten mit räumlichen Datenmethoden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bearbeitet werden. Das von zwei räumlichen Dateninstanzen abgeleitete Ergebnis einer beliebigen räumlichen Methode ist nur dann gültig, wenn diese Instanzen den gleichen SRID haben und die gleiche Maßeinheit, Bezugsebene und Projektion zur Bestimmung der Koordinaten der Instanzen verwendet wurde. Die gängigsten Maßeinheiten für einen SRID sind Meter oder Quadratmeter.  
  
 Wenn zwei räumliche Instanzen nicht über den gleichen SRID verfügen, dann geben mit diesen Instanzen verwendete Methoden des **geometry** - oder **geography** -Datentyps NULL zurück. Damit beispielsweise das folgende Prädikat ein Ergebnis ungleich NULL zurückgibt, müssen die beiden **geometry** -Instanzen `geometry1` und `geometry2`den gleichen SRID besitzen:  
  
 `geometry1.STIntersects(geometry2) = 1`  
  
> [!NOTE]  
>  Das Spatial Reference Identification-System wird durch den [European Petroleum Survey Group-Standard (EPSG)](https://go.microsoft.com/fwlink/?LinkId=99349) definiert. Hierbei handelt es sich um einen für die Kartografie, Landvermessung und Speicherung geodätischer Daten entwickelten Satz von Standards. Dieser Standard ist Eigentum des Oil and Gas Producers (OGP) Surveying and Positioning Committee.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über räumliche Datentypen](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
