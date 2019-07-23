---
title: Virtualisieren externer Daten in SQL Server 2019 CTP 2.0 | Microsoft-Dokumentation
description: Auf dieser Seite wird die Verwendung des Assistenten zum Erstellen externer Tabellen für eine CSV-Datei detailliert beschrieben.
author: Abiola
ms.author: aboke
ms.reviewer: mikeray
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: polybase
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: df014d179faa5321e3f4e472045eb64a9e9894be
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041141"
---
# <a name="use-the-external-table-wizard-with-csv-files"></a>Verwenden des Assistenten für externe Tabellen mit CSV-Dateien

SQL Server 2019 ermöglicht auch das Virtualisieren von Daten aus einer CSV-Datei in HDFS (Hadoop Distributed File System).  Damit können Sie Daten, die an ihrem ursprünglichen Speicherort bleiben, in einer SQL Server-Instanz **virtualisieren**. Dort können sie wie jede andere Tabelle in SQL Server abgefragt werden. Mit diesem Feature wird die Notwendigkeit von ETL-Vorgängen minimiert. Dies wird durch die Verwendung von PolyBase-Connectors ermöglicht. Weitere Informationen zur Datenvirtualisierung finden Sie in der Dokumentation zu [PolyBase](polybase-guide.md).

## <a name="prerequisite"></a>Voraussetzung

Ab CTP 2.4 werden Datenpools und Speicherpools nicht mehr standardmäßig als externe Datenquellen in Ihrem Big Data-Cluster erstellt. Bevor Sie den Assistenten verwenden, erstellen Sie die externe Standarddatenquelle **SqlStoragePool** in Ihrer Zieldatenbank mit der folgenden Transact-SQL-Abfrage. Stellen Sie sicher, dass Sie zunächst den Kontext der Abfrage gemäß Ihrer Zieldatenbank ändern.

```sql
-- Create default data sources for SQL Big Data Cluster
IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
    CREATE EXTERNAL DATA SOURCE SqlDataPool
    WITH (LOCATION = 'sqldatapool://controller-svc/default');

IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
    CREATE EXTERNAL DATA SOURCE SqlStoragePool
    WITH (LOCATION = 'sqlhdfs://controller-svc/default');
```

## <a name="launch-the-external-table-wizard"></a>Starten des Assistenten für externe Tabellen

Stellen Sie mithilfe der IP-Adresse eine Verbindung mit dem HDFS-Stamm her. Erweitern Sie die Elemente im Objekt-Explorer. Wählen Sie dann eine CSV-Datei aus, deren Daten Sie in einer vorhandenen SQL Server-Instanz virtualisieren möchten. Klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie im Kontextmenü **Create External Table From CSV File** (Externe Tabelle aus CSV-Datei erstellen) aus. Sie können externe Tabellen auch aus CSV-Dateien aus einem Ordner in HDFS erstellen, wenn die Daten im Ordner dem gleichen Schema folgen. Dies würde die Virtualisierung der Daten auf einer Ordnerebene ermöglichen, ohne einzelne Dateien verarbeiten und ein zusammengefügtes Ergebnis der kombinierten Daten abrufen zu müssen. Daraufhin wird der Assistent zum Virtualisieren von Daten gestartet. Sie können den Assistenten zum Virtualisieren von Daten auch über die Befehlspalette starten, indem Sie „Strg+Shift+P“ (Windows) bzw. Cmd+Shift+P (Mac) eingeben.

![Assistent zum Virtualisieren von Daten](media/data-virtualization/csv-virtualize-data-wizard.png)

## <a name="connect-to-a-sql-server-master-instance"></a>Herstellen einer Verbindung zu einer SQL Server-Masterinstanz

Hier können Sie mithilfe der IP-Adresse, des Ports und der Anmeldeinformationen festlegen, zu welcher SQL Server-Masterinstanz die Verbindung hergestellt wird. Auf zuvor gespeicherte Verbindungen können Sie über das Dropdownfeld **Active SQL Server connections** (Aktive SQL Server-Verbindungen) zugreifen. 
> [!NOTE]
>Wenn Sie eine gespeicherte Verbindung verwenden, sind die anderen Felder nicht verfügbar.


![Auswählen einer Datenquelle](media/data-virtualization/csv-connect-to-master.png)

Klicken Sie auf „Weiter“, um mit dem nächsten Schritt im Assistenten fortzufahren: dem Festlegen des Datenbankhauptschlüssels.

## <a name="select-destination-database"></a>Auswählen der Zieldatenbank

In diesem Schritt wählen Sie die Zieldatenbank aus, in die Sie die Daten virtualisieren möchten. Das Dropdownfeld enthält alle zulässigen Datenbanken in der SQL Server-Masterinstanz, die in der vorherigen Anzeige angegeben waren. Hier können Sie außerdem die neue externe Tabelle benennen und sehen, welches Schema sie verwenden wird.

![Erstellen eines Datenbankhauptschlüssels](media/data-virtualization/csv-select-destination.png)


## <a name="preview-data"></a>Datenvorschau

In diesem Fenster wird zur Überprüfung eine Vorschau der ersten 50 Zeilen Ihrer CSV-Datei angezeigt.

Klicken Sie auf „Weiter“, um fortzufahren, sobald Sie die Vorschau überprüft haben.

![Anmeldeinformationen für die externe Datenquelle](media/data-virtualization/csv-preview-data.png)

## <a name="modify-columns"></a>Bearbeiten von Spalten

Im daraufhin angezeigten Fenster können Sie die Spalten der externen Tabelle bearbeiten. Sie können Spaltennamen ändern, den Datentyp ändern und Zeilen mit NULL-Werten zulassen. 

![Anmeldeinformationen für die externe Datenquelle](media/data-virtualization/csv-modify-columns.png)


## <a name="summary"></a>Zusammenfassung

Dieser Schritt bietet eine Zusammenfassung Ihrer Auswahl. Diese enthält Informationen zur SQL Server-Masterinstanz und der vorgeschlagenen externen Tabelle. In diesem Schritt können Sie die beiden Optionen **Skript generieren** und **Erstellen** auswählen. Mit „Skript generieren“ wird die T-SQL-Syntax zum Erstellen der externen Datenquelle erstellt, und mit „Erstellen“ wird das Objekt der externen Datenquelle erstellt.

![Bildschirm „Zusammenfassung“](media/data-virtualization/csv-virtualize-data-summary.png)

Wenn Sie auf „Erstellen“ klicken, können Sie die in der Zieldatenbank erstellte externe Tabelle sehen.

![Externe Datenquellen](media/data-virtualization/csv-external-data-sources.png)

Wenn Sie auf **Skript generieren** klicken, wird angezeigt, wie die T-SQL-Abfrage zum Erstellen des Objekts der externen Datenquelle generiert wird.

![Skript generieren](media/data-virtualization/csv-generated-script.png)

> [!NOTE]
> „Skript generieren“ soll nur auf der letzten Seite im Assistenten angezeigt werden. Derzeit erscheint die Option auf allen Seiten.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum SQL Server-Cluster für Big Data und die entsprechenden Szenarien finden Sie unter [Was ist der SQL Server-Cluster für Big Data?](../../big-data-cluster/big-data-cluster-overview.md).
