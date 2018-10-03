---
title: Verbessern von Leistung und Zuverlässigkeit mit dem JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e1592499-b87b-45ee-bab8-beaba8fde841
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7650a51e21cd6d1b6a8d4bbacddf6cabdb9cc1e5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47627908"
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
  
