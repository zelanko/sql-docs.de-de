---
title: Installieren & konfigurieren DW WideWorldImporters-Beispieldatenbank
description: Befolgen Sie diese Anweisungen zum Herunterladen, Installieren und Konfigurieren der WideWorldImportersDW-Beispieldatenbank mit SQL Server Management Studio.
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 08/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.custom: seo-lt-2019
ms.openlocfilehash: 2f640415ecdc2ae4a48220aeec2a2c78ed79807c
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488545"
---
# <a name="wideworldimportersdw-installation-and-configuration"></a>WideWorldImportersDW Installation und Konfiguration
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
Installations- und Konfigurationsanweisungen für die WideWorldImportersDW-Datenbank.

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (oder höher) oder [Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/). Verwenden Sie SQL Server Evaluation/Developer/Enterprise Edition, um die Vollversion des Beispiels zu verwenden.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Für die besten Ergebnisse verwenden Sie die Version Juni 2016 oder höher.

## <a name="download"></a>Download

Die neueste Version des Beispiels:

[Weit-Welt-Importeur-Release](https://go.microsoft.com/fwlink/?LinkID=800630)

Laden Sie das Beispiel WideWorldImportersDW-Datenbanksicherung/-bacpac herunter, das Ihrer Edition von SQL Server oder Azure SQL Database entspricht.

Der Quellcode zum Neuerstellen der Beispieldatenbank ist am folgenden Speicherort verfügbar. Beachten Sie, dass die Datenpopulation auf ETL aus der OLTP-Datenbank (WideWorldImporters) basiert:

[Weitwelt-Importeur-Quelle](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/sample-scripts)

## <a name="install"></a>Installieren


### <a name="sql-server"></a>SQL Server

Um eine Sicherung auf einer SQL Server-Instanz wiederherzustellen, können Sie Management Studio verwenden.

1. Öffnen Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit der SQL Server-Zielinstanz her.
2. Klicken Sie mit der rechten Maustaste auf den Knoten **Datenbanken,** und wählen Sie **Datenbank wiederherstellen**aus.
3. Wählen Sie **Gerät** und klicken Sie auf die Schaltfläche **...**
4. Klicken Sie im Dialogfeld **Sicherungsgeräte auswählen**auf **Hinzufügen**, navigieren Sie zur Datenbanksicherung im Dateisystem des Servers, und wählen Sie die Sicherung aus. Klicken Sie auf **OK**.
5. Ändern Sie bei Bedarf den Zielspeicherort für die Daten- und Protokolldateien im Bereich **Dateien.** Beachten Sie, dass es am besten ist, Daten und Protokolldateien auf verschiedenen Laufwerken zu platzieren.
6. Klicken Sie auf **OK**. Dadurch wird die Datenbankwiederherstellung initiiert. Nach Abschluss der Datei ist die Datenbank WideWorldImporters auf Ihrer SQL Server-Instance installiert.

### <a name="azure-sql-database"></a>Azure SQL-Datenbank

Um ein Bacpac in eine neue SQL-Datenbank zu importieren, können Sie Management Studio verwenden.

1. (optional) Wenn Sie noch nicht über einen SQL Server in Azure verfügen, navigieren Sie zum [Azure-Portal,](https://portal.azure.com/) und erstellen Sie eine neue SQL-Datenbank. Beim Erstellen einer Datenbank erstellen Sie einen Server. Notieren Sie sich den Server.
   - In [diesem Tutorial](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) zum Erstellen einer Datenbank in wenigen Minuten
2. Öffnen Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit Ihrem Server in Azure her.
3. Klicken Sie mit der rechten Maustaste auf den Knoten **Datenbanken,** und wählen Sie **Datentier-Anwendung importieren**aus.
4. Wählen Sie in den **Importeinstellungen** **Import von einem lokalen Datenträger** aus und wählen Sie das Bacpac der Beispieldatenbank aus Ihrem Dateisystem aus.
5. Ändern Sie unter **Datenbankeinstellungen** den Datenbanknamen in *WideWorldImportersDW,* und wählen Sie die zu verwendende Zieledition und das Dienstziel aus.
6. Klicken Sie auf **Weiter** und **Beenden,** um die Bereitstellung zu starten. Dies nimmt einige Minuten in Anspruch. Wenn Sie ein Dienstziel angeben, das niedriger als S2 ist, kann es länger dauern.

## <a name="configuration"></a>Konfiguration

[Gilt für SQL Server 2016 (und höher) Entwickler/Evaluierung/Enterprise Edition]

Die Beispieldatenbank kann PolyBase verwenden, um Dateien in Hadoop oder Azure-Blobspeicher abzufragen. Diese Funktion ist jedoch nicht standardmäßig mit SQL Server installiert – Sie müssen es während der EINRICHTUNG von SQL Server auswählen. Daher ist ein Schritt nach der Installation erforderlich.

1. Stellen Sie in SQL Server Management Studio eine Verbindung mit der WideWorldImportersDW-Datenbank her, und öffnen Sie ein neues Abfragefenster.
2. Führen Sie den folgenden T-SQL-Befehl aus, um die Verwendung von PolyBase in der Datenbank zu aktivieren:

   EXECUTE [Anwendung]. [Configuration_ApplyPolyBase]
