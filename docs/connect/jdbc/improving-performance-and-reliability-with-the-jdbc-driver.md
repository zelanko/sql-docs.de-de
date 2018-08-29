---
title: Verbessern von Leistung und Zuverlässigkeit mit dem JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e1592499-b87b-45ee-bab8-beaba8fde841
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9108ab6ac330086acab16a73550d5fcab5d3970
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784040"
---
# <a name="improving-performance-and-reliability-with-the-jdbc-driver"></a>Verbessern von Leistung und Zuverlässigkeit mit dem JDBC-Treiber

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Ein allen Anwendungen gemeinsamer Aspekt der Anwendungsentwicklung ist die ständige Notwendigkeit, Leistung und Zuverlässigkeit zu verbessern. Nachstehend sind einige Verfahren aufgeführt, um dieses Ziel mit [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] zu erreichen.  
  
Die Themen in diesem Abschnitt beschreiben verschiedene Verfahren, um die Leistung und Zuverlässigkeit von Anwendungen zu verbessern, wenn der JDBC-Treiber verwendet wird.  

## <a name="in-this-section"></a>In diesem Abschnitt

|Thema|und Beschreibung|  
|-----------|-----------------|  
|[Schließen von nicht verwendeten Objekten](../../connect/jdbc/closing-objects-when-not-in-use.md)|Beschreibt die Bedeutung des Schließens von JDBC-Treiberobjekten, wenn sie nicht mehr benötigt werden.|  
|[Verwalten des Transaktionsumfangs](../../connect/jdbc/managing-transaction-size.md)|Beschreibt Verfahren zur Steigerung der Transaktionsleistung.|  
|[Arbeiten mit Anweisungen und Resultsets](../../connect/jdbc/working-with-statements-and-result-sets.md)|Beschreibt Verfahren zur Steigerung der Leistung, wenn die Anweisung oder der ResultSet-Objekte verwenden.|  
|[Verwenden der adaptiven Pufferung](../../connect/jdbc/using-adaptive-buffering.md)|Beschreibt die Funktion für die adaptive Pufferung, durch die alle Daten mit großen Werten ohne den Aufwand für Servercursor abgerufen werden können.|  
|[Spalten mit geringer Dichte](../../connect/jdbc/sparse-columns.md)|Erläutert, auf welche Weise vom JDBC-Treiber Sparsespalten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt werden.|  
|[Vorbereitetes Caching von Anweisungsmetadaten für den JDBC-Treiber](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)|Beschreibt die Techniken zum Verbessern der Leistung mit vorbereitete Abfragen.|
|[Verwenden der Massenkopierungs-API für den Batcheinfügungsvorgang](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md)|Beschreibt, wie die API für Massenkopieren für Insert-Vorgänge für Batch und dessen Vorteile zu aktivieren.|

## <a name="see-also"></a>Siehe auch

[Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  