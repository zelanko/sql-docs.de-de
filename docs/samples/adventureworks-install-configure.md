---
title: Installieren und konfigurieren Sie die Beispieldatenbank "AdventureWorks"-SQL | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 06/19/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c39ecc5693297070d47afc9b989de795eb9af2c2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47676548"
---
# <a name="adventureworks-installation-and-configuration"></a>AdventureWorks-Installation und Konfiguration
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

AdventureWorks laden Links und Anweisungen zur Installation herunter. 

## <a name="prerequisites"></a>Erforderliche Komponenten

- [SQLServer](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) oder [Azure SQL-Datenbank](https://azure.microsoft.com/services/sql-database/). Verwenden Sie für die vollständige Version des Beispiels SQL Server-Evaluierung, Developer, Enterprise Edition ein.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Für die besten Ergebnisse verwenden Sie das Release vom Juni 2016 oder höher.
 
## <a name="github-links"></a>Github-links

- [Alle Dateien von AdventureWorks für SQL 2014 – 2016](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)
- [Alle Dateien von AdventureWorks für SQL 2012](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2012)
- [Alle Dateien von AdventureWorks für SQL 2008 und 2008 R2](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks2008r2)

## <a name="oltp-downloads"></a>OLTP-downloads

Direkte Links zu den OLTP-Versionen von AdventureWorks finden Sie weiter unten:

- [AdventureWorks2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2017.bak)
- [AdventureWorks2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2016.bak)
- [AdventureWorks2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2014.bak)
- [AdventureWorks2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks2012.bak)
- [AdventureWorks2008R2.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008r2-oltp.bak)


## <a name="data-warehouse-downloads"></a>Datawarehouse-downloads

Direkte Links zu den Data Warehouse-Versionen von AdventureWorks finden Sie weiter unten:

- [AdventureWorksDW2017.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak)
- [AdventureWorksDW2016.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2016.bak)
- [AdventureWorksDW2014.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2014.bak)
- [AdventureWorksDW2012.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2012.bak)
- [AdventureWorksDW2008R2.bak](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks2008r2/adventure-works-2008-dw.bak)

## <a name="creation-scripts"></a>Erstellungsskripts
Die unten angegebenen Skripts können verwendet werden, um die gesamte AdventureWorks-Datenbank, unabhängig von der Version zu erstellen. 

- [AdventureWorks-OLTP-Skripts Zip](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorks-oltp-install-script.zip)
- [AdventureWorks DW Skripts Zip](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW-data-warehouse-install-script.zip)

## <a name="install-to-sql-server"></a>Installieren Sie SQLServer

### <a name="restore-backup"></a>Sicherung wiederherstellen
Führen Sie die folgenden Schritte aus, um eine Sicherung der Datenbank mit SQL Server Management Studio wiederherzustellen. 

1. Öffnen Sie SQL Server Management Studio, und Verbinden mit der SQL Server-Zielinstanz.
2. Mit der rechten Maustaste auf die **Datenbanken** Knoten, und wählen **Restore Database**.
3. Wählen Sie **Gerät** , und klicken Sie auf die Auslassungspunkte (**...** )
4. Im Dialogfeld **Sicherungsmedien auswählen**, klicken Sie auf **hinzufügen**, navigieren Sie zu der datenbanksicherung in das Dateisystem des Servers ein, und wählen Sie die Sicherung. Klicken Sie auf **OK**.
5. Bei Bedarf ändern, das der Zielort für die Daten und Protokolldateien, in der **Dateien** Bereich. Beachten Sie, dass es wird empfohlen, zum Hinzufügen von Daten und Protokolldateien auf verschiedenen Laufwerken.
6. Klicken Sie auf **OK**. Dadurch wird die Wiederherstellung der Datenbank ausgelöst. Nachdem der Vorgang abgeschlossen ist, müssen Sie die AdventureWorks-Datenbank, die auf Ihrer SQL Server-Instanz installiert.

Weitere Informationen zum Wiederherstellen einer SQL Server-Datenbank finden Sie unter [Wiederherstellen einer datenbanksicherung mit SSMS](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).


### <a name="attach-a-datafile"></a>Fügen Sie eine Datendatei
Führen Sie die folgenden Schritte aus, um die Datendatei für Ihre Datenbank mithilfe von SQL Server Management Studio anzufügen.

1. Öffnen Sie SQL Server Management Studio, und Verbinden mit der SQL Server-Zielinstanz.
2. Mit der rechten Maustaste auf die **Datenbanken** Knoten, und wählen **Anfügen**.
3. Wählen Sie **hinzufügen** und navigieren Sie zu der. MDF-Datei, die Sie anfügen möchten. 
1. Wählen Sie die Datei, und klicken Sie auf **OK**. 
    1. Die Datenbank, die Sie ausgewählt haben, sollte im unteren Fenster angezeigt werden. Wenn die Datei aufgeführt wird als "nicht gefunden", wählen Sie die Auslassungspunkte (**...** ) neben dem Dateinamen, und aktualisieren Sie den Pfad zu den richtigen Pfad. 
    1. Wenn Sie nur die Datendatei (.mdf), und nicht die Protokolldatei (.ldf) haben, markieren Sie die .ldf im unteren Fenster, und wählen **entfernen**. Dadurch wird eine neue Protokolldatei erstellt. 
1. Wählen Sie **OK** , die Datei anzufügen. Nachdem die Datei angefügt ist, müssen Sie die AdventureWorks-Datenbank, die auf Ihrer SQL Server-Instanz installiert.  

Weitere Informationen zum Anfügen von Datenbanken, finden Sie unter [Anfügen einer Datenbank](../relational-databases/databases/attach-a-database.md). 

## <a name="install-to-azure-sql-database"></a>Installieren Sie Azure SQL-Datenbank


Wenn Sie noch keinem SQL Server in Azure verfügen, navigieren Sie zu der [Azure-Portal](https://portal.azure.com/) , und erstellen Sie eine neue SQL-Datenbank. Dabei wird eine Datenbank erstellen, erstellen Sie einen Server. Notieren Sie den Server. Finden Sie unter [in diesem Tutorial](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) zum Erstellen einer Datenbank in Minuten.

1. Verbinden Sie mit Ihrem Azure-Portal.
1. Wählen Sie **erstellen Sie eine Ressource** in der Ecke oben links im Navigationsbereich. 
1. Wählen Sie **Datenbanken** und wählen Sie dann **SQL-Datenbank**. 
1. Füllen Sie die angeforderten Informationen ein.
1. In der **Quelle auswählen** auf Feld **Beispiel (AdventureWorksLT)** , eine Sicherung der neuesten AdventureWorksLT Sicherung wiederherzustellen.
1. Wählen Sie **erstellen** Ihre neue SQL-Datenbank zu erstellen, die von der wiederhergestellten Kopie in der AdventureWorksLT-Datenbank ist. 


## <a name="see-also"></a>Siehe auch
[Tutorials für SQL Server Management Studio](../ssms/tutorials/tutorial-sql-server-management-studio.md)
[Lernprogramme für SQL Server-Datenbank-Engine](../relational-databases/database-engine-tutorials.md)
