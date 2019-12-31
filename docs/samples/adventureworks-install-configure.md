---
title: Installieren und Konfigurieren der AdventureWorks-Beispieldatenbank
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 06/19/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 6a4b56a31ede0d8e011c1a2244f5d014e185e7e5
ms.sourcegitcommit: 9e026cfd9f2300f106af929d88a9b43301f5edc2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74318995"
---
# <a name="adventureworks-installation-and-configuration"></a>Installation und Konfiguration von AdventureWorks
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

AdventureWorks Download Links und Installationsanweisungen. 

## <a name="prerequisites"></a>Voraussetzungen

- [SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) oder [Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/). Verwenden Sie für die vollständige Version des Beispiels SQL Server Evaluation/Developer/Enterprise Edition.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Um die besten Ergebnisse zu erzielen, verwenden Sie die Version vom Juni 2016 oder höher.
 
## <a name="oltp-downloads"></a>OLTP-Downloads

Direkte Links zu den OLTP-Versionen von AdventureWorks finden Sie unten:

- [AdventureWorks2017. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2017.bak)
- [AdventureWorks2016. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2016.bak)
- [AdventureWorks2014. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2014.bak)
- [AdventureWorks2012. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2012.bak)
- [AdventureWorks2008R2. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-oltp.bak)


## <a name="data-warehouse-downloads"></a>Data Warehouse Downloads

Direkt Links zu den Data Warehouse Versionen von AdventureWorks finden Sie unten:

- [AdventureWorksDW2017. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak)
- [AdventureWorksDW2016. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2016.bak)
- [AdventureWorksDW2014. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2014.bak)
- [AdventureWorksDW2012. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2012.bak)
- [AdventureWorksDW2008R2. bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008-dw.bak)

## <a name="creation-scripts"></a>Erstellungs Skripts
Die folgenden Skripts können verwendet werden, um unabhängig von der Version die gesamte AdventureWorks-Datenbank zu erstellen. 

- [ZIP-Skripts für AdventureWorks-OLTP](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks-oltp-install-script.zip)
- [ZIP-Skripts für AdventureWorks DW](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW-data-warehouse-install-script.zip)

## <a name="github-links"></a>GitHub-Links

- [Alle AdventureWorks-Dateien für SQL 2014-2016](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
- [Alle AdventureWorks-Dateien für SQL 2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2012)
- [Alle AdventureWorks-Dateien für SQL 2008 und 2008R2](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2008r2)

## <a name="install-to-sql-server"></a>In SQL Server installieren

### <a name="restore-backup"></a>Sicherung wiederherstellen
Führen Sie die folgenden Schritte aus, um eine Sicherung der Datenbank mithilfe SQL Server Management Studio wiederherzustellen. 

1. Öffnen Sie SQL Server Management Studio und stellen Sie eine Verbindung mit der Ziel SQL Server Instanz her.
2. Klicken Sie mit der rechten Maustaste auf den Knoten **Datenbanken** , und wählen Sie **Datenbank wiederherstellen**.
3. Wählen Sie das **Gerät** aus, und klicken Sie auf die Ellipse (**...**)
4. Wählen Sie im Dialogfeld **Sicherungs**Medien aus, klicken Sie auf **Hinzufügen**, navigieren Sie im Dateisystem des Servers zu der Datenbanksicherung, und wählen Sie die Sicherung aus. Klicken Sie auf **OK**.
5. Ändern Sie ggf. den Zielort für die Daten-und Protokolldateien im Bereich " **Dateien** ". Beachten Sie, dass es eine bewährte Vorgehensweise ist, Daten-und Protokolldateien auf verschiedenen Laufwerken zu platzieren.
6. Klicken Sie auf **OK**. Dadurch wird die Daten Bank Wiederherstellung initiiert. Nachdem der Vorgang abgeschlossen ist, wird die AdventureWorks-Datenbank auf Ihrer SQL Server-Instanz installiert.

Weitere Informationen zum Wiederherstellen einer SQL Server Datenbank finden [Sie unter Wiederherstellen einer Datenbanksicherung mit SSMS](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).


### <a name="attach-a-datafile"></a>Anfügen einer Datendatei
Führen Sie die folgenden Schritte aus, um die Datendatei für Ihre Datenbank mithilfe von SQL Server Management Studio anzufügen.

1. Öffnen Sie SQL Server Management Studio und stellen Sie eine Verbindung mit der Ziel SQL Server Instanz her.
2. Klicken Sie mit der rechten Maustaste auf den Knoten **Datenbanken** , und wählen Sie **Anfügen**.
3. Wählen Sie **Hinzufügen** aus, und navigieren Sie zum. MDF-Datei, die Sie anfügen möchten. 
1. Wählen Sie die Datei aus, und klicken Sie auf **OK**. 
    1. Die Datenbank, die Sie ausgewählt haben, sollte im unteren Fenster angezeigt werden. Wenn die Datei als "nicht gefunden" aufgeführt ist, wählen Sie die Auslassungs Punkte (**...**) neben dem Dateinamen aus, und aktualisieren Sie den Pfad auf den richtigen Pfad. 
    1. Wenn Sie nur die Datendatei (. mdf) und nicht die Protokolldatei (. ldf) haben, markieren Sie die LDF-Datei im unteren Fenster, und wählen Sie **Entfernen**aus. Dadurch wird eine neue Protokolldatei erstellt. 
1. Wählen Sie **OK** aus, um die Datei anzufügen. Nachdem die Datei angefügt wurde, wird die AdventureWorks-Datenbank auf Ihrer SQL Server-Instanz installiert.  

Weitere Informationen zum Anfügen von Datenbankdateien finden Sie unter [Anfügen einer Datenbank](../relational-databases/databases/attach-a-database.md). 

## <a name="install-to-azure-sql-database"></a>Installieren in Azure SQL-Datenbank


Wenn Sie noch keine SQL Server in Azure haben, navigieren Sie zum [Azure-Portal](https://portal.azure.com/) , und erstellen Sie eine neue SQL-Datenbank. Beim Erstellen einer Datenbank erstellen Sie einen Server. Notieren Sie sich den Server. In [diesem Tutorial](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) erfahren Sie, wie Sie eine Datenbank in wenigen Minuten erstellen.

1. Stellen Sie eine Verbindung mit Ihrem Azure-Portal her
1. Wählen Sie oben links im Navigationsbereich **Ressource erstellen** aus. 
1. Wählen Sie **Datenbanken** und dann **SQL-Datenbank** aus. 
1. Geben Sie die erforderlichen Informationen ein.
1. Wählen Sie im Feld **Quelle auswählen** die Option **Sample (AdventureWorksLT)** aus, um eine Sicherung der neuesten AdventureWorksLT-Sicherung wiederherzustellen.
1. Wählen Sie **Erstellen** aus, um die neue SQL-Datenbank zu erstellen. Dies ist die wiederhergestellte Kopie der AdventureWorksLT-Datenbank. 


## <a name="see-also"></a>Siehe auch
[Lernprogramme für SQL Server Management Studio](../ssms/tutorials/tutorial-sql-server-management-studio.md)   
[Tutorials für SQL Server Datenbank-Engine](../relational-databases/database-engine-tutorials.md)
