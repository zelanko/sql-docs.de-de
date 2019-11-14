---
title: Konfigurieren von Einstellungen für Datenmigrations-Assistent
description: Erfahren Sie, wie Sie die Einstellungen für die Datenmigrations-Assistent konfigurieren, indem Sie Werte in der Konfigurationsdatei aktualisieren.
ms.custom: seo-lt-2019
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
ms.openlocfilehash: fc280fa541e2a6b5ea984086d694ffdd3f7c39a8
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056540"
---
# <a name="configure-settings-for-data-migration-assistant"></a>Konfigurieren von Einstellungen für Datenmigrations-Assistent

Sie können ein bestimmtes Verhalten von Datenmigrations-Assistent optimieren, indem Sie Konfigurationswerte in der Datei "DMA. exe. config" festlegen. In diesem Artikel werden die wichtigsten Konfigurationswerte beschrieben.

Sie finden die Datei "DMA. exe. config" für die Datenmigrations-Assistent Desktop Anwendung und das Befehlszeilen-Hilfsprogramm in den folgenden Ordnern auf dem Computer.

- Desktop Anwendung

  % Program Files%\\Microsoft-Datenmigrations-Assistent\\DMA. exe. config

- Befehlszeilen-Hilfsprogramm

  % Program Files%\\Microsoft-Datenmigrations-Assistent\\dmacmd. exe. config 

Stellen Sie sicher, dass Sie eine Kopie der ursprünglichen Konfigurationsdatei speichern, bevor Sie Änderungen vornehmen. Nachdem Sie die Änderungen vorgenommen haben, starten Sie Datenmigrations-Assistent neu, damit die neuen Konfigurationswerte wirksam werden.

## <a name="number-of-databases-to-assess-in-parallel"></a>Anzahl von Datenbanken, die parallel bewertet werden sollen

Datenmigrations-Assistent mehrere Datenbanken parallel bewertet. Während der Bewertung Datenmigrations-Assistent extrahiert eine Datenebenenanwendung (dacpac), um das Datenbankschema zu verstehen. Bei diesem Vorgang kann ein Timeout entstehen, wenn mehrere Datenbanken auf demselben Server parallel bewertet werden. 

Ab Datenmigrations-Assistent v 2.0 können Sie dies steuern, indem Sie den Konfigurations Wert paralleldatenbanken festlegen. Der Standardwert ist 8.

```
<advisorGroup>

<workflowSettings>

<assessment parallelDatabases="8" />

</workflowSettings>

</advisorGroup>
```




## <a name="number-of-databases-to-migrate-in-parallel"></a>Anzahl von Datenbanken, die parallel migriert werden sollen

Datenmigrations-Assistent migriert mehrere Datenbanken parallel, bevor-Anmeldungen migriert werden. Während der Migration wird Datenmigrations-Assistent eine Sicherung der Quelldatenbank durchführen, die Sicherung optional kopieren und auf dem Zielserver wiederherstellen. Möglicherweise treten Timeout Fehler auf, wenn mehrere Datenbanken für die Migration ausgewählt werden. 

Ab Datenmigrations-Assistent v 2.0 können Sie den paralleldatenbanken-Konfigurations Wert verringern, wenn Sie dieses Problem auftreten. Sie können den Wert erhöhen, um die gesamte Migrationszeit zu verringern.

```
<advisorGroup>

<workflowSettings>

<migration parallelDatabases="8″ />

</workflowSettings>

</advisorGroup>
```


## <a name="dacfx-settings"></a>Dacfx-Einstellungen

Während der Bewertung extrahiert Datenmigrations-Assistent eine Datenebenenanwendung (dacpac), um das Datenbankschema zu verstehen. Dieser Vorgang kann mit Timeouts für extrem große Datenbanken fehlschlagen, oder wenn der Server ausgelastet ist. Ab der Daten Migration v 1.0 können Sie die folgenden Konfigurationswerte ändern, um Fehler zu vermeiden. 

> [!NOTE]
> Der gesamte &lt;dacfx-&gt; Eintrag ist standardmäßig kommentiert. Entfernen Sie die Kommentare, und ändern Sie den Wert nach Bedarf.

- CommandTimeout

   Dieser Parameter legt die IDbCommand. CommandTimeout-Eigenschaft in *Sekunden*fest. (Standardwert = 60)

- databaseLockTimeout

   Dieser Parameter entspricht dem [Festlegen des Timeouts für Sperr\_\_Zeitraum](../t-sql/statements/set-lock-timeout-transact-sql.md) in *Millisekunden*. (Standardwert = 5.000)

- maxDataReaderDegreeOfParallelism

  Mit diesem Parameter wird die Anzahl der zu verwendenden SQL-Verbindungspool Verbindungen festgelegt. (Standardwert = 8)

```
<advisorGroup>

<advisorSettings>

<dacFx  commandTimeout="60" databaseLockTimeout="5000"
maxDataReaderDegreeOfParallelism="8"/>

</advisorSettings>

</advisorGroup>
```

## <a name="stretch-database-recommendation-threshold"></a>Stretch Database: Empfehlungs Schwellenwert

Mit [SQL Server Stretch Database](https://docs.microsoft.com/sql/sql-server/stretch-database/stretch-database)können Sie sowohl warm-als auch kalte Transaktionsdaten dynamisch von Microsoft SQL Server 2016 auf Azure ausdehnen. Stretch Database als Ziel für Transaktions Datenbanken mit großen Mengen an kaltdaten. Die Stretch Database Empfehlung unter Empfehlung zu Speicher Features identifiziert zunächst die Tabellen, die von diesem Feature genutzt werden, und identifiziert dann Änderungen, die vorgenommen werden müssen, um die Tabelle für dieses Feature zu aktivieren.

Ab Datenmigrations-Assistent v 2.0 können Sie diesen Schwellenwert für eine Tabelle steuern, damit Sie sich für die Stretch Database-Funktion mit dem Konfigurations Wert "Empfehlungs Konfigurations Wert" qualifizieren. Der Standardwert ist 100.000 Zeilen. Wenn Sie die Stretch-Funktionen für noch kleinere Tabellen analysieren möchten, verringern Sie den Wert entsprechend.

```
<advisorGroup>

<advisorSettings>

<stretchDBAdvisor  recommendedNumberOfRows="100000" />

</advisorSettings>

</advisorGroup>
```


## <a name="sql-connection-timeout"></a>SQL-Verbindungs Timeout

Sie können das Timeout der [SQL-Verbindung](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectiontimeout(v=vs.110).aspx) für Quell-und Ziel Instanzen während der Ausführung einer Bewertung oder Migration steuern, indem Sie den Wert für das Verbindungs Timeout auf eine angegebene Anzahl von Sekunden festlegen. Der Standardwert beträgt 15 Sekunden.

```
<appSettings>

<add key="ConnectionTimeout" value="15" />

</appSettings>
```

## <a name="ignore-error-codes"></a>Fehlercodes ignorieren

Jede Regel weist einen Fehlercode im Titel auf. Wenn Sie keine Regeln benötigen und diese ignorieren möchten, verwenden Sie die ignoreerrorcodes-Eigenschaft. Sie können angeben, um einen einzelnen Fehler oder mehrere Fehler zu ignorieren. Um mehrere Fehler zu ignorieren, verwenden Sie ein Semikolon, z. b. ignoreerrorcodes = "46010; 71501". Der Standardwert ist 71501, der nicht aufgelösten verweisen zugeordnet ist, wenn ein Objekt auf Systemobjekte, z. b. Prozeduren, Sichten usw., verweist.

```
<workflowSettings>

<assessment parallelDatabases="8" ignoreErrorCodes="71501" />

</workflowSettings>
```

## <a name="see-also"></a>Siehe auch

[Datenmigrations-Assistent Download](https://www.microsoft.com/download/details.aspx?id=53595)
