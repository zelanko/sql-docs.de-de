---
title: Herstellen einer Verbindung mit MySQL (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to MySQL, MySQL permission
- Connecting to MySQL,reconnecting
ms.assetid: 084c7020-f729-4f91-90e0-143f85fa68d1
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 6cb47c0f06d7133b8c7454a4fa538937a0e78e19
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68103170"
---
# <a name="connecting-to-mysql-mysqltosql"></a>Herstellen einer Verbindung mit MySQL (MySqlToSql)
Um MySQL-Datenbanken zu SQL Server oder SQL Azure zu migrieren, müssen Sie mit der MySQL-Datenbank verbinden, die Sie migrieren möchten. Wenn Sie eine Verbindung herstellen, SSMA Ruft Metadaten über alle MySQL-Schemas ab, und anschließend in der MySQL-Metadaten-Explorer-Bereich angezeigt. SSMA speichert Informationen zu den Datenbankserver, aber die Kennwörter werden nicht gespeichert.  
  
Die Verbindung mit der Datenbank bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut verbinden, wenn Sie möchten, dass eine aktive Verbindung mit der Datenbank.  
  
Metadaten für die MySQL-Datenbank wird nicht automatisch aktualisiert. Stattdessen sollten Sie die Metadaten in der MySQL-Metadaten-Explorer zu aktualisieren, müssen Sie manuell es aktualisieren. Weitere Informationen finden Sie im Abschnitt "Aktualisieren der MySQL-Metadaten" weiter unten in diesem Thema.  
  
## <a name="required-mysql-permissions"></a>Erforderliche MySQL-Berechtigungen  
Das Konto, das verwendet wird, für die Verbindung mit der MySQL-Datenbank muss zumindest **CONNECT** Berechtigungen. Dies ermöglicht der SSMA zum Abrufen von Metadaten aus Schemas im Besitz des Benutzers eine Verbindung herstellt. Um Metadaten für Objekte in anderen Schemas zu erhalten, und klicken Sie dann die Objekte in diesen Schemas konvertieren, muss das Konto folgenden Berechtigungen verfügen:  
  
-   "SHOW" Berechtigungen für Datenbankobjekte  
  
-   "SELECT" auf "Information_schema"  
  
-   "SELECT-Berechtigung für Mysql (für benutzerdefinierte Funktionen)  
  
## <a name="establishing-a-connection-to-mysql"></a>Herstellen einer Verbindung mit MySQL  
Wenn Sie eine Verbindung mit einer Datenbank herstellen, SSMA liest die Datenbankmetadaten und fügt dann diese Metadaten zu der Projektdatei. Diese Metadaten werden von SSMA verwendet, wenn sie Objekte in SQL Server oder SQL Azure-Syntax konvertiert und Daten in SQL Server oder SQL Azure migriert werden. Sie können diese Metadaten im MySQL-Metadaten-Explorer durchsuchen und überprüfen Sie die Eigenschaften einzelner Datenbankobjekte.  
  
> [!IMPORTANT]  
> Bevor Sie versuchen, eine Verbindung herstellen, stellen Sie sicher, dass der Datenbankserver ausgeführt wird und Verbindungen akzeptieren.  
  
**Verbindung mit MySQL**  
  
1.  Auf der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit MySQL** (diese Option wird nach der Erstellung des Projekts aktiviert werden).  
  
    Wenn Sie zuvor mit MySQL verbunden sind, gibt der Namen des Befehls werden **Wiederherstellen der Verbindung mit MySQL**.  
  
2.  In der **Anbieter** wählen MySQL 5.1 Odbcdriver (vertrauenswürdig). Es ist der Standardanbieter in den Modus "standard".  
  
3.  In der **Modus** Kontrollkästchen **Modus "Standard"** . Es handelt sich hierbei um den Standardmodus.  
  
    Verwenden Sie Modus "standard", um den Servernamen und Port anzugeben.  
  
4.  In **Modus "Standard"** , geben Sie die folgenden Werte:  
  
    1.  In der **Servernamen** Geben Sie den Namen des MySQL-Servers. In der **Serverport** Geben Sie die Portnummer, um 3306 sein. Es ist der Standardport.  
  
    2.  In der **Benutzernamen** Geben Sie eine MySQL-Konto, das die erforderlichen Berechtigungen verfügt.  
  
    3.  In der **Kennwort** Geben Sie das Kennwort für den angegebenen Benutzernamen ein.  
  
5.  **SSL:** Wenn Sie die sichere Verbindung mit MySQL herstellen möchten, verwenden von Secure Socket Layer (SSL) anhand der **SSL** Kontrollkästchen.  
  
6.  **Konfigurieren:** Es bietet eine Option aus, um die Verbindung mit MySQL über Secure Socket Layer (SSL) konfigurieren.  
  
    > [!NOTE]  
    > So aktivieren Sie **konfigurieren**, SSL muss festgelegt werden, um **"true"** .  
  
    Wird Sie durch Klicken auf die Schaltfläche "Konfigurieren", ein Dialogfeld angezeigt. Definiert [Privacy Enhanced Mail-Zertifikate (PEM)], Verschlüsselung zu verwenden, beim Herstellen einer Verbindung mit MySQL-Datenbank, Pfad, an den folgenden drei Dateien, die in das Dialogfeld vorhanden sein muss:  
  
    -   **SSL-Zertifizierungsstelle:** Gibt den Pfad zu einer Datei mit einer Liste von vertrauenswürdigen Zertifizierungsstellen mit SSL.  
  
    -   **SSL-Zertifikat:** Gibt den Namen der Datei die SSL-Zertifikat zum Herstellen einer sicheren Verbindung verwendet.  
  
    -   **SSL-SCHLÜSSEL:** Gibt den Namen der Schlüsseldatei SSL zum Herstellen einer sicheren Verbindung verwendet.  
  
    > [!NOTE]  
    > -   Die **OK** Schaltfläche ist aktiviert, wenn die erforderliche Informationen bereitgestellt wurde. Wenn die Dateipfade ungültig sind, bleiben die Schaltfläche "OK" deaktiviert.  
    > -   Die **Abbrechen** Schaltfläche wird das Dialogfeld geschlossen und **deaktiviert** das Hauptformular der Verbindung die Option "SSL".  
  
7.  Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connect-to-mysql-mysqltosql.md)  
  
## <a name="reconnecting-to-mysql"></a>Wiederherstellen der Verbindung mit MySQL  
Die Verbindung mit dem Datenbankserver bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut verbinden, wenn Sie möchten, dass eine aktive Verbindung mit der Datenbank. Sie können offline arbeiten, bis Sie die Metadaten aktualisieren, Laden von Datenbankobjekten in SQL Server- oder SQL Azure, und Daten migrieren möchten.  
  
## <a name="refreshing-mysql-metadata"></a>Aktualisieren von MySQL-Metadaten  
Metadaten für die MySQL-Datenbank wird nicht automatisch aktualisiert. Die Metadaten in der MySQL-Metadaten-Explorer ist eine Momentaufnahme der Metadaten, wenn Sie zuerst eine Verbindung hergestellt oder der letzten, dass Sie manuell die Metadaten aktualisiert werden. Sie können die Metadaten für alle Schemas, ein einzelnes Schema oder einzelne Datenbankobjekte manuell aktualisieren.  
  
**Aktualisieren von Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit der Datenbank verbunden sind.  
  
2.  Wählen Sie in der MySQL-Metadaten-Explorer das Kontrollkästchen neben jedem Schema oder die Datenbank-Objekt, das Sie aktualisieren möchten.  
  
3.  Mit der rechten Maustaste **Schemas**, oder die einzelnes Schema oder die Datenbank-Objekt, und wählen Sie dann **Refresh from Database aktualisieren**.  
  
    SSMA wird angezeigt, wenn Sie nicht über eine aktive Verbindung verfügen, die **Herstellen einer Verbindung mit MySQL** Dialogfeld, sodass Sie eine Verbindung herstellen können.  
  
4.  Geben Sie in der Aktualisierung von Datenbank (Dialogfeld) welche Objekte aktualisiert.  
  
    -   Um ein Objekt zu aktualisieren, klicken Sie auf die **Active** Feld neben dem Objekt, bis ein Pfeil angezeigt wird.  
  
    -   Um zu verhindern, dass ein Objekt aktualisiert wird, klicken Sie auf die **Active** Feld neben dem Objekt, bis ein **X** angezeigt wird.  
  
    -   Klicken Sie zum Aktualisieren, oder lehnen Sie eine Kategorie von Objekten ab, auf die **Active** Feld neben dem Ordner "Kategorie".  
  
    -   Um die Definitionen der farbcodierung anzuzeigen, klicken Sie auf die **Legende** Schaltfläche.  
  
5.  Klicken Sie auf **OK**.  
  
## <a name="next-step"></a>Nächster Schritt  
Im nächsten Schritt des Migrationsvorgangs [Herstellen einer Verbindung mit SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von MySQL-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
