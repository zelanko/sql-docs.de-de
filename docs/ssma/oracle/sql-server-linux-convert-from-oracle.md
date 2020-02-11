---
title: Migrieren des Oracle HR-Schemas zu SQL Server für Linux | Microsoft-Dokumentation
description: Konvertieren eines Oracle-Beispiel Schemas in SQL Server für Linux
author: shamikg
ms.author: shamikg
manager: shamikg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: ''
ms.technology: ssma
ms.openlocfilehash: 1926c13b739de8294966fd6ce84df3d1e02a676e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68266516"
---
# <a name="migrate-an-oracle-schema-to-sql-server-2017-on-linux-with-the-sql-server-migration-assistant"></a>Migrieren eines Oracle-Schemas zu SQL Server 2017 unter Linux mit dem SQL Server Migration Assistant

In diesem Tutorial wird SQL Server Migration Assistant (SSMA) für Oracle unter Windows verwendet, um das Oracle-Beispiel- **HR** -Schema in [SQL Server 2017 unter Linux](../../linux/sql-server-linux-overview.md)zu konvertieren.

> [!div class="checklist"]
> * Herunterladen und Installieren von SSMA unter Windows
> * Erstellen eines SSMA-Projekts zum Verwalten der Migration
> * Herstellen einer Verbindung mit Oracle
> * Ausführen eines Migrationsberichts
> * Konvertieren des HR-Beispiel Schemas
> * Migrieren der Daten

## <a name="prerequisites"></a>Voraussetzungen

- Eine Instanz von Oracle 12C (12.2.0.1.0) mit installiertem **HR** -Schema
- Eine funktionierende Instanz von SQL Server für Linux

> [!NOTE]
> Die gleichen Schritte können auch für SQL Server unter Windows verwendet werden, aber Sie müssen in der Einstellung **zu Projekt migrieren** die Option Windows auswählen.

## <a name="download-and-install-ssma-for-oracle"></a>Herunterladen und Installieren von SSMA für Oracle

Abhängig von der Quelldatenbank sind mehrere Editionen von SQL Server Migration Assistant verfügbar.  Laden Sie die aktuelle Version von [SQL Server Migration Assistant für Oracle](https://aka.ms/ssmafororacle) herunter, und installieren Sie Sie mithilfe der Anweisungen auf der Downloadseite.

> [!NOTE]
> Zu diesem Zeitpunkt wird das **SSMA für Oracle Extension Pack** unter Linux nicht unterstützt, ist aber für dieses Tutorial nicht erforderlich.

## <a name="create-and-set-up-project"></a>Erstellen und Einrichten eines Projekts

Verwenden Sie die folgenden Schritte, um ein neues SSMA-Projekt zu erstellen:

1. Öffnen Sie SSMA für Oracle, und wählen Sie im Menü **Datei** die Option **Neues Projekt** aus.

1. Geben Sie dem Projekt einen Namen.

1. Wählen Sie im Feld **Migrieren zu** die Option "SQL Server 2017 (Linux)-Preview" aus.

SSMA für Oracle verwendet standardmäßig nicht die Oracle-Beispiel Schemas. Führen Sie die folgenden Schritte aus, um das HR-Schema zu aktivieren:

1. Wählen Sie in SSMA das **Menü** Extras aus.

1. Wählen Sie **Standard Projekteinstellungen**aus, und wählen Sie dann **System Objekte laden**aus.

1. Stellen Sie sicher, dass **HR** aktiviert ist, und wählen Sie **OK**aus.

## <a name="connect-to-oracle"></a>Herstellen einer Verbindung mit Oracle

Verbinden Sie als nächstes SSMA mit Oracle.

1. Klicken Sie auf der Symbolleiste auf **Verbindung mit Oracle herstellen**.

1. Geben Sie den Servernamen, den Port, die Oracle-sid, den Benutzernamen und das Kennwort ein.

   ![Herstellen einer Verbindung mit Oracle](./media/sql-server-linux-convert-from-oracle/ConnectToOracle.png)

1. Klicken Sie dann auf **Verbinden**. In wenigen Augenblicken stellt SSMA für Oracle eine Verbindung mit Ihrer Datenbank her und liest die zugehörigen Metadaten.

## <a name="create-a-report"></a>Erstellen eines Berichts

Führen Sie die folgenden Schritte aus, um einen Migrationsbericht zu generieren.

1. Erweitern Sie im **Oracle-metadatenexplorer**den Knoten des Servers.

1. Erweitern Sie **Schemas**, klicken Sie mit der rechten Maustaste auf **HR**, und wählen Sie **Bericht erstellen**.

   ![Oracle-metadatenexplorer-Bericht erstellen](./media/sql-server-linux-convert-from-oracle/CreateReport.png)

1. Ein neues Browserfenster wird mit einem Bericht geöffnet, in dem alle Warnungen und Fehler aufgeführt werden, die mit der Konvertierung verknüpft sind.

   > [!NOTE]
   > Sie müssen für dieses Tutorial nichts mit der Liste ausführen. Wenn Sie diese Schritte für Ihre eigene Oracle-Datenbank ausführen, sollten Sie den Bericht überprüfen, um alle wichtigen Konvertierungsprobleme der Datenbank zu beheben.

   ![Beispiel für einen Migrationsbericht](./media/sql-server-linux-convert-from-oracle/SSMAReport.png)

## <a name="connect-to-sql-server"></a>Verbindung mit SQL Server herstellen

Wählen Sie als nächstes **Verbinden mit SQL Server aus,** und geben Sie die entsprechenden Verbindungsinformationen ein.  Wenn Sie einen Datenbanknamen verwenden, der nicht bereits vorhanden ist, wird er von SSMA für Oracle für Sie erstellt.

![Verbindung mit SQL Server herstellen](./media/sql-server-linux-convert-from-oracle/ConnectToSQLServer.png)

## <a name="convert-schema"></a>Schema konvertieren

Klicken Sie mit der rechten Maustaste auf **HR** in **Oracle Metadata Explorer**, und wählen Sie Schema konvertieren aus.

![Schema konvertieren](./media/sql-server-linux-convert-from-oracle/ConvertSchema.png)

## <a name="synchronize-database"></a>Datenbank synchronisieren

Synchronisieren Sie als nächstes die Datenbank.

1. Nachdem die Konvertierung abgeschlossen ist, verwenden Sie den **SQL Server Metadaten-Explorer** , um zur Datenbank zu wechseln, die Sie im vorherigen Schritt erstellt haben.

1. Klicken Sie mit der rechten Maustaste auf die Datenbank, wählen Sie **mit Datenbank synchronisieren**aus, und klicken Sie dann auf OK.

   ![Mit Datenbank synchronisieren](./media/sql-server-linux-convert-from-oracle/SynchronizeWithDatabase.png)

## <a name="migrate-data"></a>Migrieren von Daten

Der letzte Schritt besteht darin, Ihre Daten zu migrieren.

1. Klicken Sie im **Oracle-metadatenexplorer**mit der rechten Maustaste auf **HR**, und wählen Sie **Daten migrieren**aus.

1. Der Daten Migrationsschritt erfordert, dass Sie Ihre Oracle-und SQL Server-Anmelde Informationen erneut eingeben.

1. Wenn Sie fertig sind, überprüfen Sie den Daten Migrationsbericht, der in etwa wie im folgenden Screenshot aussehen sollte:

   ![Bericht zur Datenmigration](./media/sql-server-linux-convert-from-oracle/DataMigrationReport.png)

## <a name="next-steps"></a>Nächste Schritte

Bei einem komplexeren Orcale-Schema umfasst der Konvertierungsprozess mehr Zeit, Tests und mögliche Änderungen an Client Anwendungen. In diesem Tutorial wird gezeigt, wie Sie SSMA für Oracle als Teil des gesamten Migrationsprozesses verwenden können.

In diesem Tutorial haben Sie Folgendes gelernt:
> [!div class="checklist"]
> * Installieren von SSMA unter Windows
> * Erstellen eines neuen SSMA-Projekts
> * Bewerten und Ausführen einer Migration von Oracle

Sehen Sie sich als nächstes andere Möglichkeiten für die Verwendung von SSMA an:

> [!div class="nextstepaction"]
>[Dokumentation zu SQL Server Migration Assistant](../sql-server-migration-assistant.md)
