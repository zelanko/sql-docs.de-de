---
title: Konfigurieren von PolyBase-Konnektivität – Analytics Platform System | Microsoft-Dokumentation
description: Erläutert das Konfigurieren von PolyBase in Parallel Data Warehouse zur Verbindung mit externer Hadoop oder Microsoft Azure-BLOB-speicherdatenquellen. Verwenden Sie PolyBase zum Ausführen von Abfragen, die Daten aus mehreren Quellen, einschließlich Hadoop, Azure-BLOB-Speicher und Parallel Data Warehouse integrieren.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: da6d71521f72ff23b4caf2f27dbc663dee684592
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63057810"
---
# <a name="what-is-polybase"></a>Was ist PolyBase?
PolyBase ermöglicht Ihre Analytics Platform System (APS) zum Verarbeiten von Transact-SQL-Abfragen, die Lesen von Daten aus und Schreiben von Daten mit externen Datenquellen können. Die gleichen Abfragen, die Zugriff auf externe Daten können auch Beziehung Tabellen in Ihrem APS einschließen. Dadurch können Sie Daten aus externen Quellen mit hohem Wert relationalen Daten in Ihren APS-Datenbanken zu kombinieren.

![Logische PolyBase](media/polybase/polybase-logical.png)

PolyBase für Zugriffspunkte unterstützt das Lesen und Schreiben in HDFS (Hadoop)-Dateisystem und Azure Blob Storage. PolyBase verfügt auch über die Möglichkeit, die Übertragung der einige Berechnung an Hadoop-Knoten als Mapreduce-Aufträge, um die gesamte abfrageleistung zu optimieren. PolyBase für Zugriffspunkte kann die Dateien mit durch Trennzeichen getrennten Text, ORC und parquet-Dateien arbeiten. Finden Sie unter [neuerungen von PolyBase](https://docs.microsoft.com/sql/relational-databases/polybase/polybase-guide) für eine vollständige Beschreibung und die zugehörigen Funktionen.

> [!NOTE]
> APS unterstützt derzeit nur standard Allgemein v1 lokal redundant (LRS) Azure Blob Storage.

## <a name="features-and-limitations"></a>Features und Einschränkungen
Finden Sie unter [Funktionen und Einschränkungen für](https://docs.microsoft.com/sql/relational-databases/polybase/polybase-versioned-feature-summary) für eine Zusammenfassung der PolyBase verfügbare und bekannte Einschränkungen für Zugriffspunkten und anderen SQL Server-Produkte bietet.

> [!NOTE] 
> Die restlichen PolyBase im Zusammenhang mit Artikeln beschrieben PolyBase APS 2016 (AU6) und höher zu konfigurieren.

## <a name="see-also"></a>Siehe auch
- [Hadoop](polybase-configure-hadoop.md)
- [Azure Blob Storage](polybase-configure-azure-blob-storage.md)
<!-- MISSING LINKS [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  -->  
  
