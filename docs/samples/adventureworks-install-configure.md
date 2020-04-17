---
title: Installieren und Konfigurieren der AdventureWorks-Beispieldatenbank
description: Befolgen Sie diese Anweisungen, um AdventureWorks-Beispieldatenbanken mit SQL Server Management Studio oder in Azure SQL-Datenbank herunterzuladen und zu installieren.
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.date: 06/19/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 7fa3d199450750a444f2b67ae3e4583549d449b9
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484569"
---
# <a name="adventureworks-installation-and-configuration"></a>AdventureWorks Installation und Konfiguration
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

AdventureWorks laden Links und Installationsanweisungen herunter. 

## <a name="prerequisites"></a>Voraussetzungen

- [SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) oder [Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/). Verwenden Sie für die Vollversion des Beispiels SQL Server Evaluation/Developer/Enterprise Edition.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Für die besten Ergebnisse verwenden Sie die Version Juni 2016 oder höher.
 
## <a name="oltp-downloads"></a>OLTP-Downloads

Direkte Links zu den OLTP-Versionen von AdventureWorks finden Sie unten:

- [AdventureWorks2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2017.bak)
- [AdventureWorks2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2016.bak)
- [AdventureWorks2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2014.bak)
- [AdventureWorks2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2012.bak)
- [AdventureWorks2008R2.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-oltp.bak)


## <a name="data-warehouse-downloads"></a>Data Warehouse-Downloads

Direkte Links zu den Data Warehouse-Versionen von AdventureWorks finden Sie unten:

- [AdventureWorksDW2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak)
- [AdventureWorksDW2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2016.bak)
- [AdventureWorksDW2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2014.bak)
- [AdventureWorksDW2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2012.bak)
- [AdventureWorksDW2008R2.bak](https://github.com/microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-dw.bak)

## <a name="creation-scripts"></a>Erstellungsskripts
Die folgenden Skripte können verwendet werden, um die gesamte AdventureWorks-Datenbank zu erstellen, unabhängig von der Version. 

- [AdventureWorks OLTP Skripte Zip](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks-oltp-install-script.zip)
- [AdventureWorks DW Skripte Zip](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW-data-warehouse-install-script.zip)

## <a name="github-links"></a>GitHub-Links

- [Alle AdventureWorks-Dateien für SQL 2014 - 2016](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
- [Alle AdventureWorks-Dateien für SQL 2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2012)
- [Alle AdventureWorks-Dateien für SQL 2008 und 2008R2](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2008r2)

## <a name="install-to-sql-server"></a>Installieren auf SQL Server

### <a name="restore-backup"></a>Wiederherstellen von Backups
Führen Sie die folgenden Schritte aus, um eine Sicherung Ihrer Datenbank mit SQL Server Management Studio wiederherzustellen. 

1. Öffnen Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit der SQL Server-Zielinstanz her.
2. Klicken Sie mit der rechten Maustaste auf den Knoten **Datenbanken,** und wählen Sie **Datenbank wiederherstellen**aus.
3. Wählen Sie **Gerät** und klicken Sie auf die Ellipsen (**...**)
4. Klicken Sie im Dialogfeld **Sicherungsgeräte auswählen**auf **Hinzufügen**, navigieren Sie zur Datenbanksicherung im Dateisystem des Servers, und wählen Sie die Sicherung aus. Klicken Sie auf **OK**.
5. Ändern Sie bei Bedarf den Zielspeicherort für die Daten- und Protokolldateien im Bereich **Dateien.** Beachten Sie, dass es am besten ist, Daten und Protokolldateien auf verschiedenen Laufwerken zu platzieren.
6. Klicken Sie auf **OK**. Dadurch wird die Datenbankwiederherstellung initiiert. Nach Abschluss der Datei ist die AdventureWorks-Datenbank auf Ihrer SQL Server-Instance installiert.

Weitere Informationen zum Wiederherstellen einer SQL Server-Datenbank finden Sie unter [Wiederherstellen einer Datenbanksicherung mit SSMS](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).


### <a name="attach-a-datafile"></a>Anfügen einer Datendatei
Führen Sie die folgenden Schritte aus, um die Datendatei für Ihre Datenbank mithilfe von SQL Server Management Studio anzuhängen.

1. Öffnen Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit der SQL Server-Zielinstanz her.
2. Klicken Sie mit der rechten Maustaste auf den Knoten **Datenbanken,** und wählen Sie **Anfügen**aus.
3. Wählen Sie **Hinzufügen aus,** und navigieren Sie zum . MDF-Datei, die Sie anfügen möchten. 
1. Wählen Sie die Datei aus, und klicken Sie auf **OK**. 
    1. Die ausgewählte Datenbank sollte im unteren Fenster angezeigt werden. Wenn die Datei als "nicht gefunden" aufgeführt ist, wählen Sie die Ellipsen (**...**) neben dem Dateinamen aus und aktualisieren Sie den Pfad zum richtigen Pfad. 
    1. Wenn Sie nur über die Datendatei (.mdf) und nicht über die Protokolldatei (.ldf) verfügen, markieren Sie die .ldf im unteren Fenster, und wählen Sie **Entfernen**aus. Dadurch wird eine neue Protokolldatei erstellt. 
1. Wählen Sie **OK,** um die Datei anzuhängen. Nachdem die Datei angefügt wurde, wird die AdventureWorks-Datenbank auf Ihrer SQL Server-Instanz installiert.  

Weitere Informationen zum Anfügen von Datenbankdateien finden Sie [unter Anfügen einer Datenbank](../relational-databases/databases/attach-a-database.md). 

## <a name="install-to-azure-sql-database"></a>Installieren in Azure SQL-Datenbank


Wenn Sie noch nicht über einen SQL Server in Azure verfügen, navigieren Sie zum [Azure-Portal,](https://portal.azure.com/) und erstellen Sie eine neue SQL-Datenbank. Beim Erstellen einer Datenbank erstellen Sie einen Server. Notieren Sie sich den Server. In [diesem Tutorial](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) können Sie in wenigen Minuten eine Datenbank erstellen.

1. Stellen Sie eine Verbindung zu Ihrem Azure-Portal her.
1. Wählen Sie **Ressource** erstellen oben links im Navigationsbereich aus. 
1. Wählen Sie **Datenbanken** und dann **SQL-Datenbank** aus. 
1. Geben Sie die erforderlichen Informationen ein.
1. Wählen Sie im Feld **Quelle auswählen** die Option **Beispiel (AdventureWorksLT)** aus, um eine Sicherung der neuesten AdventureWorksLT-Sicherung wiederherzustellen.
1. Wählen Sie **Erstellen** aus, um Ihre neue SQL-Datenbank zu erstellen, bei der es sich um die wiederhergestellte Kopie der AdventureWorksLT-Datenbank handelt. 


## <a name="see-also"></a>Weitere Informationen
[Tutorials für SQL Server Management Studio](../ssms/tutorials/tutorial-sql-server-management-studio.md)   
[Tutorials für SQL Server-Datenbankmodul](../relational-databases/database-engine-tutorials.md)
