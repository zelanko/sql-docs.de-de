---
title: Exportieren und Importieren einer Datenbank unter Linux
description: ''
author: VanMSFT
ms.author: vanto
manager: jroth
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 2210cfc3-c23a-4025-a551-625890d6845f
ms.openlocfilehash: 9f676cf8c4ed6c5659074e422b3e01a6019e592e
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834846"
---
# <a name="export-and-import-a-database-on-linux-with-ssms-or-sqlpackageexe-on-windows"></a>Exportieren und Importieren einer Datenbank unter Linux mit SSMS oder SqlPackage.exe auf Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel wird gezeigt, wie Sie mit [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) und [SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx) exportieren und importieren eine Datenbank auf SQL Server unter Linux. SSMS und SqlPackage.exe sind Windows-Anwendungen, also verwenden Sie dieses Verfahren, wenn Sie einen Windows-Computer verfügen, der zu einer Remoteinstanz von SQL Server unter Linux eine Verbindung herstellen können.

Sollten Sie immer installieren und verwenden Sie die neueste Version von SQL Server Management Studio (SSMS), siehe [Verwenden von SSMS unter Windows zur Verbindung mit SQL Server unter Linux](sql-server-linux-manage-ssms.md)

> [!NOTE]
> Wenn Sie eine Datenbank von einer SQL Server-Instanz zu einem anderen migrieren, es wird empfohlen, verwenden Sie [Sicherungs- und Wiederherstellungsvorgänge](sql-server-linux-migrate-restore-database.md).

## <a name="export-a-database-with-ssms"></a>Exportieren einer Datenbank mit SSMS

1. Starten Sie SSMS, indem Sie eingeben **Microsoft SQL Server Management Studio** in der Windows-Suchfeld ein, und klicken Sie dann auf die desktop-app.

    ![SQL Server Management Studio](./media/sql-server-linux-manage-ssms/ssms.png) 

2. Verbinden Sie mit Ihrer Quelldatenbank im Objekt-Explorer. Die Quelldatenbank kann in Microsoft SQL Server lokal oder in der Cloud unter Linux, Windows oder Docker und Azure SQL-Datenbank oder Azure SQL Data Warehouse sein.

3. Mit der rechten Maustaste in der Quelldatenbank im Objekt-Explorer, zeigen Sie auf **Aufgaben**, und klicken Sie auf **Datenebenenanwendung exportieren...**

4. Im Export-Assistenten, klicken Sie auf **Weiter**, und klicken Sie dann auf die **Einstellungen** konfigurieren die exportieren, um die bacpac-Datei auf einen lokalen Speicherort oder in ein Azure-Blob zu speichern.

5. Standardmäßig werden alle Objekte in der Datenbank exportiert. Klicken Sie auf die **Registerkarte "Erweitert"** , und wählen Sie die Datenbankobjekte, die Sie exportieren möchten.

6. Klicken Sie auf **Weiter** und anschließend auf **Fertig stellen**.

Die *. Bacpac-Datei wurde erfolgreich erstellt, an der Position, die Sie ausgewählt haben, und Sie bereit sind, die sie in eine Zieldatenbank importieren.

## <a name="import-a-database-with-ssms"></a>Importieren einer Datenbank mit SSMS

1. Starten Sie SSMS, indem Sie eingeben **Microsoft SQL Server Management Studio** in der Windows-Suchfeld ein, und klicken Sie dann auf die desktop-app.

    ![SQL Server Management Studio](./media/sql-server-linux-manage-ssms/ssms.png) 

2. Verbinden Sie mit Ihrem Ziel-Server im Objekt-Explorer. Der Zielserver kann Microsoft SQL Server, die lokal ausgeführt werden oder in der Cloud unter Linux, Windows oder Docker und Azure SQL-Datenbank oder Azure SQL Data Warehouse.

3. Mit der rechten Maustaste die **Datenbanken** Ordner im Objekt-Explorer, und klicken Sie auf **Datenebenenanwendung importieren...**

4. Klicken Sie zum Erstellen der Datenbank auf Ihrem Zielserver, geben Sie eine bacpac-Datei von Ihrem lokalen Datenträger, oder wählen Sie das Azure-Speicherkonto und den Container, zu dem Sie die bacpac-Datei hochgeladen haben.

5. Geben Sie den neuen Datenbanknamen für die Datenbank an. Wenn Sie eine Datenbank auf Azure SQL-Datenbank importieren, legen Sie die Edition von Microsoft Azure SQL-Datenbank (Dienstebene), maximale Datenbankgröße und Dienstziel (Leistungsstufe).

6. Klicken Sie auf **Weiter** , und klicken Sie dann auf **Fertig stellen** die bacpac-Datei in eine neue Datenbank auf dem Zielserver zu importieren.

Die *. Bacpac-Datei wird importiert, um eine neue Datenbank auf dem Zielserver zu erstellen, die Sie angegeben haben.

## <a id="sqlpackage"></a> Die Befehlszeilenoption "Sqlpackage"

Es ist auch möglich, die SQL Server Data Tools (SSDT), Befehlszeilentools [SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx), zum Exportieren und Importieren der bacpac-Dateien.

Der Befehl im folgenden Beispiel wird eine bacpac-Datei exportiert:

```bash
SqlPackage.exe /a:Export /ssn:tcp:<your_server> /sdn:<your_database> /su:<username> /sp:<password> /tf:<path_to_bacpac>
```

Verwenden Sie zum Importieren von Datenbank-Schema und Daten aus den folgenden Befehl ein. Bacpac-Datei:

```bash
SqlPackage.exe /a:Import /tsn:tcp:<your_server> /tdn:<your_database> /tu:<username> /tp:<password> /sf:<path_to_bacpac>

```

## <a name="see-also"></a>Siehe auch
Weitere Informationen zur Verwendung von SSMS finden Sie unter [Verwenden von SQL Server Management Studio](https://msdn.microsoft.com/library/ms174173.aspx). Weitere Informationen zu SqlPackage.exe, finden Sie unter den ["Sqlpackage" Referenzdokumentation](https://msdn.microsoft.com/library/hh550080.aspx).
