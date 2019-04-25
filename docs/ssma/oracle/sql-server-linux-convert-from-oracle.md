---
title: Migrieren von Oracle HR Schema in SQLServer unter Linux | Microsoft-Dokumentation
description: Konvertieren von Oracle-Beispielschema in SQL Server unter Linux
author: shamikg
ms.author: shamikg
manager: v-thobro
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: ''
ms.technology: ssma
ms.openlocfilehash: 312797b2b883f764fc65588e72cd67d7227e327a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62629806"
---
# <a name="migrate-an-oracle-schema-to-sql-server-2017-on-linux-with-the-sql-server-migration-assistant"></a>Migrieren eines Oracle-Schemas nach SQL Server 2017 unter Linux mit der SQL Server Migration Assistant

In diesem Tutorial wird SQL Server Migration Assistant (SSMA) für Oracle unter Windows verwendet, konvertiert das Oracle-Beispiel **HR** Schema [SQL Server 2017 unter Linux](../../linux/sql-server-linux-overview.md).

> [!div class="checklist"]
> * Herunterladen und Installieren von SSMA für Windows
> * Erstellen Sie ein SSMA-Projekt, um die Migration zu verwalten.
> * Herstellen einer Verbindung mit Oracle
> * Führen Sie einen Migrationsbericht
> * Konvertieren Sie das Beispiel HR-schema
> * Die Daten migrieren

## <a name="prerequisites"></a>Erforderliche Komponenten

- Eine Instanz von Oracle 12c (12.2.0.1.0) mit der **HR** Schema installiert
- Eine Arbeitsinstanz von SQL Server unter Linux

> [!NOTE]
> Die gleichen Schritte können in SQL Server unter Windows als Ziel verwendet werden, aber Sie müssen auswählen, dass Windows in der **Migrieren zu** Projekt festlegen.

## <a name="download-and-install-ssma-for-oracle"></a>Herunterladen und Installieren von SSMA für Oracle

Es gibt verschiedene Editionen von SQL Server Migration Assistant verfügbar, abhängig von der Quelldatenbank.  Herunterladen der aktuelle Version der [SQL Server Migration Assistant für Oracle](https://aka.ms/ssmafororacle) und anhand der Anweisungen auf der Downloadseite installieren.

> [!NOTE]
> Zu diesem Zeitpunkt die **SSMA für Oracle-Erweiterungspaket** wird unter Linux nicht unterstützt, aber es ist nicht für dieses Tutorial erforderlich.

## <a name="create-and-set-up-project"></a>Erstellen und Setup-Projekt

Verwenden Sie die folgenden Schritte aus, um ein neues SSMA-Projekt zu erstellen:

1. SSMA für Oracle öffnen, und wählen **neues Projekt** aus der **Datei** Menü.

1. Geben Sie dem Projekt einen Namen zu.

1. Wählen Sie "SQLServer 2017 (Linux) – Vorschau" in der **Migrieren zu** Feld.

SSMA für Oracle verwendet die Oracle-Beispielschemas nicht standardmäßig. Um das HR-Schema zu aktivieren, verwenden Sie die folgenden Schritte aus:

1. Wählen Sie in der SSMA das **Tools** Menü.

1. Wählen Sie **Projekt Standardeinstellungen**, und wählen Sie dann **Laden von Systemobjekten**.

1. Stellen Sie sicher, dass **HR** aktiviert ist, und wählen Sie **OK**.

## <a name="connect-to-oracle"></a>Herstellen einer Verbindung mit Oracle

Verbinden Sie als Nächstes SSMA für Oracle.

1. Klicken Sie auf der Symbolleiste auf **Herstellen einer Verbindung mit Oracle**.

1. Geben Sie den Servernamen, Port, Oracle-SID, Benutzername und Kennwort.

   ![Herstellen einer Verbindung mit Oracle](./media/sql-server-linux-convert-from-oracle/ConnectToOracle.png)

1. Klicken Sie dann auf **Connect**. In wenigen Augenblicken SSMA für Oracle eine Verbindung mit Ihrer Datenbank her, und liest die Metadaten.

## <a name="create-a-report"></a>Erstellen eines Berichts

Verwenden Sie die folgenden Schritte aus, um einen Migrationsbericht zu generieren.

1. In der **Oracle-Metadaten-Explorer**, erweitern Sie den Knoten Ihres Servers.

1. Erweitern Sie **Schemas**, mit der rechten Maustaste **HR**, und wählen Sie **Bericht erstellen**.

   ![Oracle-Metadaten-Explorer den Bericht erstellen](./media/sql-server-linux-convert-from-oracle/CreateReport.png)

1. Berichte, die alle Warnungen und Fehler im Zusammenhang mit der Konvertierung enthält, wird ein neues Browserfenster geöffnet.

   > [!NOTE]
   > Sie müssen nicht alles mit dieser Liste für dieses Tutorial auszuführen. Wenn Sie diese Schritte für Oracle-Datenbank durchführen, prüfen Sie den Bericht, wichtige Konvertierungsprobleme für Ihre Datenbank zu behandeln.

   ![Beispielbericht für die Migration](./media/sql-server-linux-convert-from-oracle/SSMAReport.png)

## <a name="connect-to-sql-server"></a>Verbindung mit SQL Server herstellen

Wählen Sie anschließend **Herstellen einer Verbindung mit SQL Server** , und geben Sie die entsprechenden Verbindungsinformationen.  Wenn Sie einen Datenbanknamen verwenden, der noch nicht vorhanden ist, SSMA für Oracle wird für Sie erstellt.

![Verbindung mit SQL Server herstellen](./media/sql-server-linux-convert-from-oracle/ConnectToSQLServer.png)

## <a name="convert-schema"></a>Schema konvertieren

Mit der rechten Maustaste auf **HR** in **Oracle-Metadaten-Explorer**, und wählen Sie die Schemas konvertieren.

![Schema konvertieren](./media/sql-server-linux-convert-from-oracle/ConvertSchema.png)

## <a name="synchronize-database"></a>Synchronisieren der Datenbank

Als Nächstes synchronisieren Sie Ihre Datenbank ein.

1. Wenn die Konvertierung abgeschlossen ist, verwenden die **Metadaten-Explorer von SQL Server** zur Datenbank wechseln Sie im vorherigen Schritt erstellt haben.

1. Mit der rechten Maustaste auf Ihre Datenbank, wählen **synchronisieren mit der Datenbank**, und klicken Sie dann auf OK.

   ![Synchronisieren von mit Datenbank](./media/sql-server-linux-convert-from-oracle/SynchronizeWithDatabase.png)

## <a name="migrate-data"></a>Migrieren von Daten

Der letzte Schritt besteht, Ihre Daten migrieren.

1. In der **Oracle-Metadaten-Explorer**, mit der rechten Maustaste auf **HR**, und wählen Sie **Migrieren von Daten**.

1. Schritt der Migration erfordert, dass Sie Ihre Oracle und SQL Server-Anmeldeinformationen erneut eingeben.

1. Abschließend überprüfen Sie im Migrationsbericht Daten, der ähnlich wie im folgenden Screenshot aussehen sollte:

   ![Bericht zur Datenmigration](./media/sql-server-linux-convert-from-oracle/DataMigrationReport.png)

## <a name="next-steps"></a>Nächste Schritte

Für ein komplexeres Schema Orcale würde es sich bei der Konvertierung mehr Zeit, testen und möglichen Änderungen an den Client-Anwendungen betreffen. Der Zweck dieses Lernprogramms wird erläutert, wie Sie SSMA für Oracle als Teil des gesamten Migrationsprozesses verwenden können.

In diesem Tutorial haben Sie gelernt, wie die folgenden Aufgaben ausgeführt werden:
> [!div class="checklist"]
> * Installieren von SSMA für Windows
> * Erstellen Sie ein neues SSMA-Projekt
> * Bewerten Sie und führen Sie eine Migration von Oracle

Als Nächstes auf Möglichkeiten Sie andere, mit der SSMA:

> [!div class="nextstepaction"]
>[SQL Server Migration Assistant-Dokumentation](../sql-server-migration-assistant.md)
