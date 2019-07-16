---
title: Konfigurieren von Einstellungen für den Data Migration Assistant (SQL Server) | Microsoft-Dokumentation
description: Erfahren Sie, wie Einstellungen für den Data Migration Assistant zu konfigurieren, aktualisieren Sie die Werte in der Konfigurationsdatei
ms.custom: ''
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: rajpo
ms.openlocfilehash: cb50b5380a305382bfb5494273cd335c8b60f51e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68058875"
---
# <a name="configure-settings-for-data-migration-assistant"></a>Konfigurieren von Einstellungen für den Data Migration Assistant

Sie können bestimmte Verhalten von Data Migration Assistant durch Festlegen von Konfigurationswerten in der Datei dma.exe.config optimieren. Dieser Artikel beschreibt wichtige Konfigurationswerte.

Sie finden die dma.exe.config-Datei für den Data Migration Assistant-desktop-Anwendung und des Befehlszeilen-Hilfsprogramms in den folgenden Ordnern auf Ihrem Computer.

- Desktop-Anwendung

  % ProgramFiles%\\Microsoft Data Migration Assistant\\dma.exe.config

- Befehlszeilen-Hilfsprogramm

  % ProgramFiles%\\Microsoft Data Migration Assistant\\dmacmd.exe.config 

Achten Sie darauf, dass Sie eine Kopie der ursprünglichen Konfigurationsdatei zu speichern, bevor die Änderungen. Starten Sie nach Änderungen vorgenommen wurden, neu Data Migration Assistant für die neuen Konfigurationswerte wirksam wird.

## <a name="number-of-databases-to-assess-in-parallel"></a>Anzahl der Datenbanken parallel bewerten

Data Migration Assistant bewertet wird, mehrere Datenbanken gleichzeitig. Während der Bewertung extrahiert Data Migration Assistant datenebenenanwendung (DACPAC-Datei), das Datenbankschema zu verstehen. Dieser Vorgang kann, wenn mehrere Datenbanken auf demselben Server parallel bewertet werden. 

Data Migration Assistant v2. 0 ab, können Sie dies steuern durch Festlegen der ParallelDatabases Konfigurationswert. Standardwert ist 8.

```
<advisorGroup>

<workflowSettings>

<assessment parallelDatabases="8" />

</workflowSettings>

</advisorGroup>
```




## <a name="number-of-databases-to-migrate-in-parallel"></a>Anzahl der Datenbanken parallel migrieren

Data Migration Assistant migriert mehrere Datenbanken gleichzeitig vor dem Migrieren von Anmeldungen. Während der Migration wird Data Migration Assistant erstellen Sie eine Sicherung der Quelldatenbank, optional kopieren Sie die Sicherung, und klicken Sie dann auf dem Zielserver wiederherstellen. Timeout-Fehler können auftreten, wenn mehrere Datenbanken für die Migration ausgewählt werden. 

Data Migration Assistant v2. 0 ab, wenn Sie dieses Problem auftreten, können Sie den Konfigurationswert ParallelDatabases reduzieren. Sie können den Wert für den gesamten Migration zur Reduzierung der erhöhen.

```
<advisorGroup>

<workflowSettings>

<migration parallelDatabases="8″ />

</workflowSettings>

</advisorGroup>
```


## <a name="dacfx-settings"></a>DacFX-Einstellungen

Während der Bewertung extrahiert Data Migration Assistant datenebenenanwendung (DACPAC-Datei), das Datenbankschema zu verstehen. Dieser Vorgang kann fehlschlagen, mit Timeouts für extrem große Datenbanken, oder wenn der Server ausgelastet ist. Beginnen mit der Datenmigration v1. 0, können Sie die folgenden Konfigurationswerte zur Vermeidung von Fehlern ändern. 

> [!NOTE]
> Die gesamte &lt;Dacfx&gt; Eintrag ist standardmäßig auskommentiert. Entfernen Sie die Kommentare, und klicken Sie dann ändern Sie den Wert, je nach Bedarf.

- "CommandTimeout"

   Dieser Parameter wird die Eigenschaft IDbCommand.CommandTimeout *Sekunden*. (Standard = 60)

- databaseLockTimeout

   Dieser Parameter entspricht dem [SPERRE festgelegt\_TIMEOUT Timeout\_Zeitraum](../t-sql/statements/set-lock-timeout-transact-sql.md) in *Millisekunden*. (Standard = 5000)

- maxDataReaderDegreeOfParallelism

  Dieser Parameter legt fest, die Anzahl der SQL-Verbindung-Pool-Verbindungen, die verwendet wird. (Standard = 8)

```
<advisorGroup>

<advisorSettings>

<dacFx  commandTimeout="60" databaseLockTimeout="5000"
maxDataReaderDegreeOfParallelism="8"/>

</advisorSettings>

</advisorGroup>
```

## <a name="stretch-database-recommendation-threshold"></a>Stretch Database an: Schwellenwert für die Empfehlung

Mit [SQL Server Stretch Database](https://docs.microsoft.com/sql/sql-server/stretch-database/stretch-database), Sie können dynamisches stretching von warmen und kalten Transaktionsdaten von Microsoft SQL Server 2016 nach Azure. Stretch Database ist für Transaktionsdatenbanken mit großen Mengen an inaktiven Daten gedacht. Die Stretch Database-Empfehlung, unter der Empfehlung des Speicher-Feature, identifiziert zunächst die Tabellen, dass sie annimmt, dass von dieser Funktion profitieren, und ermittelt es Änderungen, die vorgenommen werden, um die Tabelle für dieses Feature aktivieren möchten.

Data Migration Assistant v2. 0 ab, können Sie diesen Schwellenwert für eine Tabelle für die Stretch Database-Funktion, die mit den Konfigurationswert RecommendedNumberOfRows qualifizieren steuern. Standardwert ist 100.000 Zeilen. Wenn Sie die Stretch-Funktionen für die noch kleineren Tabellen analysieren möchten, setzen Sie den Wert entsprechend.

```
<advisorGroup>

<advisorSettings>

<stretchDBAdvisor  recommendedNumberOfRows="100000" />

</advisorSettings>

</advisorGroup>
```


## <a name="sql-connection-timeout"></a>SQL-Verbindungstimeout

Sie können steuern, die [SQL-Verbindungstimeout](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectiontimeout(v=vs.110).aspx) für Instanzen von Quell- und Zielserver während der Ausführung eine Bewertung oder die Migration durch Festlegen der Timeoutwert der Verbindung mit einer angegebenen Anzahl von Sekunden. Der Standardwert beträgt 15 Sekunden.

```
<appSettings>

<add key="ConnectionTimeout" value="15" />

</appSettings>
```


## <a name="see-also"></a>Siehe auch

[Data Migration Assistant herunterladen](https://www.microsoft.com/download/details.aspx?id=53595)
