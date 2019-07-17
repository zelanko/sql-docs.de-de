---
title: Herstellen einer Verbindung mit SQLServer (DB2eToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: b59803cb-3cc6-41cc-8553-faf90851410e
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7ab4c1f691820fb19dde7a3e3166abc2ff065b18
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68126635"
---
# <a name="connecting-to-sql-server-db2etosql"></a>Herstellen einer Verbindung mit SQLServer (DB2eToSQL)
Zum Migrieren von DB2-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014 oder Azure SQL-Datenbank, die Sie die mit jedem dieser Ziel-Instanzen von verbinden müssen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn Sie eine Verbindung herstellen, erhält der SSMA Metadaten zu allen Datenbanken in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und zeigt die Metadaten der Datenbank in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer. SSMA speichert Informationen über die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie verbunden sind, jedoch werden keine Kennwörter gespeichert.  
  
Die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie zum Wiederherstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ggf. eine aktive Verbindung mit dem Server. Sie können offline arbeiten, bis Sie die Datenbankobjekte in laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Daten migrieren.  
  
Metadaten zu der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird nicht automatisch synchronisiert. Stattdessen aktualisiert die Metadaten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, müssen Sie manuell aktualisieren die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten. Weitere Informationen finden Sie unter der "Synchronizing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten" weiter unten in diesem Thema.  
  
## <a name="required-sql-server-permissions"></a>Erforderliche SQL Server-Berechtigungen  
Das Konto, das verwendet wird, für die Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] benötigen unterschiedliche Berechtigungen abhängig von den Aktionen, die das Konto ausführt:  
  
-   Konvertieren von DB2-Objekten, [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax so aktualisieren Sie Metadaten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], oder um konvertierte Syntax auf Skripts speichern zu können, muss das Konto über Berechtigung zum Anmelden mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Beim Laden von Datenbankobjekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], das Konto muss ein Mitglied der **Sysadmin** -Serverrolle. Dies ist erforderlich, um CLR-Assemblys zu installieren.  
  
-   Datenmigration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], das Konto muss ein Mitglied der **Sysadmin** -Serverrolle. Dies ist erforderlich, zum Ausführen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Migration-Agent-Pakete.  
  
-   Das Konto muss zum Ausführen des Codes, die von SSMA generiert wird, verfügen **Execute** Berechtigungen für alle benutzerdefinierten Funktionen in der **ssma_DB2** Schema der Zieldatenbank. Diese Funktionen geben Sie die gleiche Funktionalität wie DB2-Systemfunktionen und von konvertierten Objekte verwendet werden.  
  
Wenn das Konto, das verwendet wird, für die Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist zum Ausführen aller Migration tasks, die das Konto muss ein Mitglied der **Sysadmin** -Serverrolle.  
  
## <a name="establishing-a-sql-server-connection"></a>Herstellen einer SQL Server-Verbindung  
Vor dem Konvertieren von DB2-Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax müssen Sie eine Verbindung mit der Instanz von herstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wo Sie die DB2-Datenbank oder Datenbanken migrieren möchten.  
  
Wenn Sie die Verbindungseigenschaften definieren, geben Sie auch die Datenbank, in dem Objekte und Daten migriert werden. Sie können diese Zuordnung auf der Schemaebene DB2 anpassen, nach dem Herstellen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Mapping DB2 Schemas in SQL Server-Schemas &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md).  
  
> [!IMPORTANT]  
> Bevor Sie versuchen, das Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], stellen Sie sicher, dass die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird und Verbindungen akzeptieren.  
  
**Verbindung mit SQL Server**  
  
1.  Auf der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit SQL Server**.  
  
    Wenn Sie zuvor mit verbunden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], der Namen des Befehls werden **Wiederherstellen der Verbindung mit SQL Server**.  
  
2.  Klicken Sie im Dialogfeld "Verbindung" eingeben, oder wählen Sie den Namen der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Wenn Sie mit der Standardinstanz auf dem lokalen Computer herstellen, geben Sie **"localhost"** oder einen Punkt ( **.** ).  
  
    -   Wenn Sie mit der Standardinstanz auf einem anderen Computer herstellen, geben Sie den Namen des Computers ein.  
  
    -   Wenn Sie die zu einer benannten Instanz auf einem anderen Computer herstellen, geben Sie den Computernamen gefolgt von einem umgekehrten Schrägstrich und dann den Namen der Instanz an, wie z. B. MyServer\MyInstance.  
  
3.  Wenn Ihre Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konfiguriert ist annehmen von Verbindungen über einen nicht-Standardport, geben die Portnummer für die verwendeten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindungen in der **Serverport** Feld. Für die Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die Standardportnummer ist 1433. Für benannte Instanzen SSMA versucht, erhalten die Portnummer der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst.  
  
4.  In der **Datenbank** Geben Sie den Namen der Zieldatenbank.  
  
    Diese Option ist nicht verfügbar, wenn Sie die Verbindung wiederherstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  In der **Authentifizierung** wählen den Authentifizierungstyp, der für die Verbindung verwendet. Um das aktuelle Windows-Konto verwenden möchten, wählen **Windows-Authentifizierung**. Verwenden einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldung wählen **SQL Server-Authentifizierung**, und geben Sie den Anmeldenamen und Kennwort.  
  
6.  Für sichere Verbindung zwei Steuerelemente hinzugefügt werden, die **Verbindung verschlüsseln** und **TrustServerCertificate** Kontrollkästchen. Nur wenn **Verbindung verschlüsseln** aktiviert ist, wird die **TrustServerCertificate** Kontrollkästchen wird angezeigt. Wenn **Verbindung verschlüsseln** (true) aktiviert ist und **TrustServerCertificate** ist deaktiviert (false), er überprüft das SQL Server-SSL-Zertifikat. Das Überprüfen des Serverzertifikats ist Teil des SSL-Handshakes und stellt sicher, dass es sich bei dem Server tatsächlich um den Server handelt, mit dem eine Verbindung hergestellt werden soll. Um dies zu gewährleisten, muss ein Zertifikat auf dem Client als auch auf dem Server installiert sein.  
  
7.  Klicken Sie auf **Verbinden**.  
  
**Kompatibilität der höheren Version**  
  
-   Sie werden zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, die bei der Migration-Projekts erstellt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005.  
  
-   Sie werden zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, die bei der Migration-Projekts erstellt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008, aber Sie werden nicht in der Lage sind, d. h. mit niedrigeren Versionen zu verbinden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005.  
  
-   Sie werden zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, wenn das Projekt, erstellt SQL Server 2012 ist.  
  
||||||  
|-|-|-|-|-|  
|**Projekt-Typ und VERSION des ZIELSERVERS**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 <br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 <br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 <br />(Version:13.x)|Azure SQL-Datenbank|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|Ja|Ja|Ja||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014||Ja|Ja||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014|||Ja||  
|Azure SQL-Datenbank||||Ja|  
  
> [!IMPORTANT]  
> Konvertierung der Datenbankobjekte erfolgt gemäß den Projekttyp, aber nicht gemäß der Version von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie verbunden sind. Im Fall von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 oder Azure SQL-Datenbank.  
  
## <a name="synchronizing-sql-server-metadata"></a>Synchronisieren von SQL Server-Metadaten  
Metadaten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken wird nicht automatisch aktualisiert. Die Metadaten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer ist eine Momentaufnahme der Metadaten aus, wenn Sie sich zunächst mit verbunden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], oder der letzten Ausführung, die Sie manuell aktualisierten Metadaten. Sie können die Metadaten für alle Datenbanken oder für jede einzelne Datenbank oder Datenbankobjekt, das manuell aktualisieren.  
  
**Zum Synchronisieren von Metadaten**  
  
1.  Stellen Sie sicher, dass Sie verbunden sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, wählen Sie das Kontrollkästchen neben der Datenbank oder das Datenbankschema, die Sie aktualisieren möchten.  
  
    Z. B. um die Metadaten für alle Datenbanken zu aktualisieren, das Kontrollkästchen neben **Datenbanken**.  
  
3.  Mit der rechten Maustaste **Datenbanken**, oder die einzelnen Datenbank oder Datenbankschema, und wählen Sie dann **synchronisieren mit der Datenbank**.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt bei der Migration hängt von den Anforderungen Ihrer Projekte:  
  
-   Zum Anpassen der Zuordnung zwischen DB2-Schemas und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken und Schemas finden Sie unter [Mapping DB2 Schemas in SQL Server-Schemas &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md).  
  
-   Informationen zum Anpassen der Konfigurationsoptionen für die Projekte finden Sie unter [Projekteinstellungen &#40;Konvertierung&#41; &#40;DB2ToSQL&#41; ](../../ssma/db2/project-settings-conversion-db2tosql.md) und Verwandte Abschnitte.  
  
-   Wenn die Zuordnung von Datentypen für Quell- und zieleinstellungen anpassen möchten, finden Sie unter [Mapping DB2- und SQL Server-Datentypen &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
-   Wenn Sie nicht zum Ausführen dieser Aufgaben verfügen, können Sie die DB2-Datenbank-Objektdefinitionen in konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objektdefinitionen. Weitere Informationen finden Sie unter [Konvertieren von DB2 Schemas &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von DB2-Datenbanken zu SQLServer &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
