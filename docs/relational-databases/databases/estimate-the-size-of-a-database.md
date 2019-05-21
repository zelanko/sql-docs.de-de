---
title: Schätzen der Größe einer Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], database size
- calculating database size
- increasing database size
- database size [SQL Server], estimating
- predicting database size
- size [SQL Server], databases
- estimating database size
- designing databases [SQL Server], estimating size
ms.assetid: 5b240161-eba4-44b0-946c-61a8fc00fc8c
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 86494a697cb16e0e47d7d52de0312b3a799f68b4
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51557807"
---
# <a name="estimate-the-size-of-a-database"></a>Schätzen der Größe einer Datenbank
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Wenn Sie eine Datenbank entwerfen, müssen Sie möglicherweise die Größe der Datenbank schätzen, wenn diese mit Daten aufgefüllt ist. Das Schätzen der Datenbankgröße kann Ihnen helfen, die Hardwarekonfiguration zu bestimmen, die für Folgendes benötigt wird:  
  
-   Erzielen der Leistung, die von den Anwendungen benötigt wird.  
  
-   Bereitstellen von physischem Speicherplatz in angemessenem Umfang, um Daten und Indizes zu speichern.  
  
 Durch das Schätzen der Datenbankgröße können Sie auch bestimmen, ob der Datenbankentwurf verfeinert werden muss. Sie könnten z. B. feststellen, dass die geschätzte Größe der Datenbank viel zu groß ist, um in Ihrer Organisation implementiert zu werden, und dass eine weitere Normalisierung erforderlich ist. Umgekehrt kann es auch vorkommen, dass der geschätzte Umfang kleiner ist als erwartet. Dann könnten Sie die Normalisierung teilweise oder ganz aufheben, um auf diese Weise die Abfrageleistung zu verbessern.  
  
 Um die Größe einer Datenbank zu schätzen, sollten Sie die Größe jeder einzelnen Tabelle schätzen und dann die ermittelten Werte addieren. Die Größe einer Tabelle hängt davon ab, ob die Tabelle über Indizes verfügt und, wenn dies der Fall ist, welcher Typ von Indizes verwendet wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Schätzen der Größe einer Tabelle](../../relational-databases/databases/estimate-the-size-of-a-table.md)|Beschreibt die Schritte und Berechnungen, die zum Schätzen des Umfangs des Speicherplatzes erforderlich sind, der zum Speichern der Daten in einer Tabelle und für die zugehörigen Indizes benötigt wird.|  
|[Schätzen der Größe eines Heaps](../../relational-databases/databases/estimate-the-size-of-a-heap.md)|Beschreibt die Schritte und Berechnungen, die zum Schätzen des Umfangs des Speicherplatzes erforderlich sind, der zum Speichern der Daten in einem Heap benötigt wird. Ein Heap ist eine Tabelle, die nicht über einen gruppierten Index verfügt.|  
|[Schätzen der Größe eines gruppierten Indexes](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)|Beschreibt die Schritte und Berechnungen, die zum Schätzen des Umfangs des Speicherplatzes erforderlich sind, der zum Speichern der Daten in einem gruppierten Index benötigt wird.|  
|[Schätzen der Größe eines nicht gruppierten Index](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)|Beschreibt die Schritte und Berechnungen, die zum Schätzen des Umfangs des Speicherplatzes erforderlich sind, der zum Speichern der Daten in einem nicht gruppierten Index benötigt wird.|  
  
  
