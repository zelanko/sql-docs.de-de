---
title: Herstellen einer Verbindung mit SQL Server (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to SQL Server
ms.assetid: dd368a1a-45b0-40e9-b4d3-5cdb48c26606
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 4f40fd6fa88b001eaa222789d6be35b83f9bf90a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948547"
---
# <a name="connecting-to-sql-server-sybasetosql"></a>Herstellen einer Verbindung mit SQL Server (SybaseToSQL)
Um die Datenbanken von Sybase Adaptive Server Enterprise ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ASE) zu zu migrieren, müssen Sie eine Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mit einer der Ziel Instanzen von herstellen. Wenn Sie eine Verbindung herstellen, erhält SSMA Metadaten zu allen Datenbanken in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz von und zeigt Daten Bank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten im Metadaten-Explorer an. SSMA speichert Informationen zu der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mit der Sie verbunden sind, speichert aber keine Kenn Wörter.  
  
Die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindung mit herstellen, wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in laden und Daten migrieren.  
  
Metadaten über die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden nicht automatisch synchronisiert. Wenn Sie die Metadaten im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] metadatenexplorer aktualisieren möchten, müssen Sie stattdessen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten manuell aktualisieren, wie im Abschnitt "Synchronisieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten" weiter unten in diesem Thema beschrieben.  
  
## <a name="required-sql-server-permissions"></a>Erforderliche SQL Server Berechtigungen  
Das Konto, das verwendet wird, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Verbindung mit herzustellen, erfordert abhängig von den Aktionen, die von diesem Konto ausgeführt werden, unterschiedliche Berechtigungen.  
  
-   Zum Konvertieren von ASE- [!INCLUDE[tsql](../../includes/tsql-md.md)] Objekten in Syntax, zum Aktualisieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von Metadaten aus oder zum Speichern konvertierter Syntax in Skripts muss das Konto über die Berechtigung verfügen, sich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]bei der Instanz von anzumelden.  
  
-   Zum Laden von Daten Bank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Objekten in ist die Mindestanforderung für Berechtigungen die Mitgliedschaft in der **db_owner** -Daten Bank Rolle in der Zieldatenbank.  
  
-   Zum Migrieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Daten zu muss das Konto Mitglied der **sysadmin** -Server Rolle sein. Dies ist erforderlich, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Daten Migrations Pakete auszuführen.  
  
-   Um den von SSMA generierten Code auszuführen, muss das Konto über **Ausführungs** Berechtigungen für alle benutzerdefinierten Funktionen im **ssma_syb** Schema der **sysdb** -Datenbank verfügen. Diese Funktionen bieten eine äquivalente Funktionalität von ASE-Systemfunktionen und werden von konvertierten Objekten verwendet.  
  
Wenn das Konto, das zum Herstellen einer Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit verwendet wird, alle Migrations Aufgaben durchführen soll, muss das Konto Mitglied der **sysadmin** -Server Rolle sein.  
  
## <a name="establishing-a-sql-server-connection"></a>Einrichten einer SQL Server Verbindung  
Vor dem Konvertieren von ASE-Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Bank Objekten in Syntax müssen Sie eine Verbindung mit der Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von herstellen, in der Sie die ASE-Datenbank oder die Datenbanken migrieren möchten.  
  
Wenn Sie die Verbindungs Eigenschaften definieren, geben Sie auch die Datenbank an, in die Objekte und Daten migriert werden. Sie können diese Zuordnung auf ASE-Schema Ebene anpassen, nachdem Sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Verbindung mit hergestellt haben. Weitere Informationen finden Sie unter [Mapping Sybase ASE Schemas to SQL Server Schemas &#40;sybasedesql&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).  
  
> [!IMPORTANT]  
> Bevor Sie versuchen, eine Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mit herzustellen, stellen Sie sicher, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dass die Instanz von ausgeführt wird und Verbindungen akzeptieren kann.  
  
**So stellen Sie eine Verbindung mit SQL Server her**  
  
1.  Wählen Sie im Menü **Datei** die Option **mit SQL Server verbinden**aus.  
  
    Wenn Sie zuvor eine Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mit hergestellt haben, wird der Befehls Name **erneut mit SQL Server**verbunden.  
  
2.  Geben Sie im Dialogfeld Verbindung den Namen der Instanz von ein, oder wählen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Sie ihn aus.  
  
    -   Wenn Sie eine Verbindung mit der Standard Instanz auf dem lokalen Computer herstellen, können Sie **localhost** oder einen Punkt (**.**) eingeben.  
  
    -   Wenn Sie eine Verbindung mit der Standard Instanz auf einem anderen Computer herstellen, geben Sie den Namen des Computers ein.  
  
    -   Wenn Sie eine Verbindung mit einer benannten Instanz auf einem anderen Computer herstellen, geben Sie den Computernamen gefolgt von einem umgekehrten Schrägstrich und dem Instanznamen ein, z. b. MyServer\MyInstance.  
  
3.  Wenn die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Annahme von Verbindungen an einem nicht standardmäßigen Port konfiguriert ist, geben Sie die Portnummer ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die im Feld **Serverport** für Verbindungen verwendet wird. Die Standard Portnummer für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die Standard Instanz von ist 1433. Bei benannten Instanzen wird von SSMA versucht, die Portnummer vom- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Dienst abzurufen.  
  
4.  Geben Sie im Feld **Datenbank** den Namen der Zieldatenbank ein.  
  
    Diese Option ist nicht verfügbar, wenn Sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erneute Verbindung mit herstellen.  
  
5.  Wählen Sie im Feld **Authentifizierung** den Authentifizierungstyp aus, der für die Verbindung verwendet werden soll. Um das aktuelle Windows-Konto zu verwenden, wählen Sie **Windows-Authentifizierung**aus. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Wählen Sie **SQL Server Authentifizierung** aus, und geben Sie dann den Anmelde Namen und das Kennwort an  
  
6.  Für eine sichere Verbindung werden zwei-Steuerelemente hinzugefügt: die Kontrollkästchen **Verbindung verschlüsseln** und **TrustServerCertificate** . Nur wenn **Verbindung verschlüsseln** aktiviert ist, ist das Kontrollkästchen **TrustServerCertificate** sichtbar. Wenn **Verbindung verschlüsseln** (true) und **TrustServerCertificate** deaktiviert (false) ist, wird das SQL Server SSL-Zertifikat überprüft. Das Überprüfen des Serverzertifikats ist Teil des SSL-Handshakes und stellt sicher, dass es sich bei dem Server tatsächlich um den Server handelt, mit dem eine Verbindung hergestellt werden soll. Um dies zu gewährleisten, muss ein Zertifikat sowohl auf Clientseite als auch auf Serverseite installiert werden.  
  
7.  Klicken Sie auf **Verbinden**.  
  
**Höhere Versions Kompatibilität**  
  
-   Sie können eine Verbindung mit 2008 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 herstellen, wenn das erstellte Migrationsprojekt auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 festgelegt ist.  
  
-   Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können eine Verbindung mit 2012 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 herstellen, wenn das erstellte Migrationsprojekt 2008 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist, aber Sie können keine Verbindung mit niedrigeren Versionen herstellen, z. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] b. 2005.  
  
-   Sie können nur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dann eine Verbindung mit 2012 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 herstellen, wenn das erstellte Projekt SQL Server 2012 ist.  
  
-   Höhere Versions Kompatibilität ist für SQL Azure ungültig.  
  
||||||||
|-|-|-|-|-|-|-|
|**Projekttyp und Ziel Server Version**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005<br /> (Version: 9. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2008<br /> (Version: 10. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2012 <br />(Version: 11. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014 <br />(Version: 12. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 <br />(Version: 13. x)|SQL Azure|
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005|Ja|Ja|Ja|Ja|Ja||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2008||Ja|Ja|Ja|Ja||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2012|||Ja|Ja|Ja||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014||||Ja|Ja|| 
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016|||||Ja||  
|SQL Azure||||||Ja|  
  
> [!IMPORTANT]
> Die Konvertierung der Datenbankobjekte erfolgt gemäß dem Projekttyp, jedoch nicht gemäß der Version von, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit der Sie verbunden sind. Im Fall von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 Project wird die Konvertierung gemäß [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 durchgeführt, obwohl eine Verbindung mit einer höheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016) besteht.  
  
## <a name="reconnecting-to-sql-server"></a>Erneutes Herstellen einer Verbindung mit SQL Server  
Die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindung mit herstellen, wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Metadaten aktualisieren, Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in laden und Daten migrieren.  
  
Die Vorgehensweise für das erneute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Herstellen einer Verbindung mit entspricht dem Verfahren zum Herstellen einer Verbindung.  
  
## <a name="synchronizing-sql-server-metadata"></a>Synchronisieren von SQL Server-Metadaten  
Metadaten zu den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken werden nicht automatisch aktualisiert. Bei den Metadaten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im metadatenexplorer handelt es sich um eine Momentaufnahme der Metadaten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], wenn Sie zum ersten Mal eine Verbindung mit hergestellt haben oder wenn Sie die Metadaten zuletzt manuell aktualisiert haben Sie können Metadaten für alle Datenbanken oder für eine einzelne Datenbank oder ein Datenbankobjekt manuell aktualisieren.  
  
**So synchronisieren Sie Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verbunden sind.  
  
2.  Aktivieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie im metadatenexplorer das Kontrollkästchen neben der Datenbank oder dem Datenbankschema, das Sie aktualisieren möchten.  
  
    Wenn Sie z. b. die Metadaten für alle Datenbanken aktualisieren möchten, aktivieren Sie das Kontrollkästchen neben **Datenbanken**.  
  
3.  Klicken Sie mit der rechten Maustaste auf Datenbanken oder die einzelnen Datenbanken oder Datenbankschemas, und wählen Sie dann **mit Datenbank synchronisieren**  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt der Migration hängt von Ihren Projektanforderungen ab:  
  
-   Wenn Sie die Zuordnung zwischen den ASE-Datenbanken und-Schemas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und-Datenbanken und-Schemas anpassen möchten, finden Sie weitere Informationen unterzuordnen von [Sybase-ASE-Schemas zu SQL Server Schemas &#40;Sybase&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).  
  
-   Wenn Sie die Konfigurationsoptionen für die Projekte anpassen möchten, finden Sie weitere Informationen unter [Festlegen von Projektoptionen &#40;sybaseto SQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md).  
  
-   Wenn Sie eine benutzerdefinierte Zuordnung der Quell-und Ziel Datentypen durcharbeiten möchten, finden Sie weitere Informationen unter [Mapping Sybase ASE und SQL Server Datentyp &#40;sybasetosql&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
-   Wenn Sie diese Schritte nicht ausführen müssen, können Sie die Objekt Definitionen der Sybase-ASE-Datenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekt Definitionen konvertieren. Weitere Informationen finden Sie unter " [umstellen von Sybase ASE-Datenbankobjekten &#40;sybasedesql&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von Sybase ASE-Datenbanken zu SQL Server-Azure SQL-Datenbank &#40;sybaseto SQL-&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
