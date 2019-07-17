---
title: Herstellen einer Verbindung mit SQLServer (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to SQL Server,Synchronizing SQL Server Metadata
ms.assetid: 1b2a8059-1829-4904-a82f-9c06de1e245f
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: cd8f0e57554f32d3b02a6e0e98d3a3645d683bac
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266162"
---
# <a name="connecting-to-sql-server-oracletosql"></a>Herstellen einer Verbindung mit SQL Server (OracleToSQL)
Migrieren von Oracle-Datenbanken in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 R2 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 müssen Sie mit diesen verbinden Ziel Instanzen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn Sie eine Verbindung herstellen, erhält der SSMA Metadaten zu allen Datenbanken in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und zeigt die Metadaten der Datenbank in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer. SSMA speichert Informationen über die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie verbunden sind, jedoch werden keine Kennwörter gespeichert.  
  
Die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie zum Wiederherstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ggf. eine aktive Verbindung mit dem Server. Sie können offline arbeiten, bis Sie die Datenbankobjekte in laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Daten migrieren.  
  
Metadaten zu der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird nicht automatisch synchronisiert. Stattdessen aktualisiert die Metadaten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, müssen Sie manuell aktualisieren die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten. Weitere Informationen finden Sie unter der "Synchronizing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten" weiter unten in diesem Thema.  
  
## <a name="required-sql-server-permissions"></a>Erforderliche SQL Server-Berechtigungen  
Das Konto, das verwendet wird, für die Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] benötigen unterschiedliche Berechtigungen abhängig von den Aktionen, die das Konto ausführt:  
  
-   So konvertieren Sie Oracle-Objekte zu [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax so aktualisieren Sie Metadaten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], oder um konvertierte Syntax auf Skripts speichern zu können, muss das Konto über Berechtigung zum Anmelden mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Beim Laden von Datenbankobjekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], das Konto muss ein Mitglied der **Sysadmin** -Serverrolle. Dies ist erforderlich, um CLR-Assemblys zu installieren.  
  
-   Datenmigration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], das Konto muss ein Mitglied der **Sysadmin** -Serverrolle. Dies ist erforderlich, zum Ausführen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Migration-Agent-Pakete.  
  
-   Das Konto muss zum Ausführen des Codes, die von SSMA generiert wird, verfügen **Execute** Berechtigungen für alle benutzerdefinierten Funktionen in der **Ssma_oracle** Schema der Zieldatenbank. Diese Funktionen bieten die gleiche Funktionalität wie Oracle-System-Funktionen und von konvertierten Objekte verwendet werden.  
  
Wenn das Konto, das verwendet wird, für die Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist zum Ausführen aller Migration tasks, die das Konto muss ein Mitglied der **Sysadmin** -Serverrolle.  
  
## <a name="establishing-a-sql-server-connection"></a>Herstellen einer SQL Server-Verbindung  
Vor dem Konvertieren von Oracle-Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax müssen Sie eine Verbindung mit der Instanz von herstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wo Sie die Oracle-Datenbank oder Datenbanken migrieren möchten.  
  
Wenn Sie die Verbindungseigenschaften definieren, geben Sie auch die Datenbank, in dem Objekte und Daten migriert werden. Sie können diese Zuordnung auf der Ebene des Oracle anpassen, nach dem Herstellen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Mapping Oracle Schemas in SQL Server-Schemas &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md).  
  
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
  
||||||||  
|-|-|-|-|-|-|-|  
|**Projekt-Typ und VERSION des ZIELSERVERS**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005<br /> (Version: 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008<br /> (Version: 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 <br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 <br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 <br />(Version:13.x)|Azure SQL-Datenbank|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|Ja|Ja|Ja|Ja|Ja||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||Ja|Ja|Ja|Ja||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||Ja|Ja|Ja||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014||||Ja|Ja||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016|||||Ja||
|Azure SQL-Datenbank||||||Ja|
  
> [!IMPORTANT]
> Konvertierung der Datenbankobjekte erfolgt gemäß den Projekttyp, aber nicht gemäß der Version von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie verbunden sind. Im Fall von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005-Projekt Konvertierung erfolgt gemäß [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, obwohl Sie mit einer höheren Version verbunden sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016).  
  
## <a name="synchronizing-sql-server-metadata"></a>Synchronisieren von SQL Server-Metadaten  
Metadaten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken wird nicht automatisch aktualisiert. Die Metadaten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer ist eine Momentaufnahme der Metadaten aus, wenn Sie sich zunächst mit verbunden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], oder der letzten Ausführung, die Sie manuell aktualisierten Metadaten. Sie können die Metadaten für alle Datenbanken oder für jede einzelne Datenbank oder Datenbankobjekt, das manuell aktualisieren.  
  
**Zum Synchronisieren von Metadaten**  
  
1.  Stellen Sie sicher, dass Sie verbunden sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, wählen Sie das Kontrollkästchen neben der Datenbank oder das Datenbankschema, die Sie aktualisieren möchten.  
  
    Z. B. um die Metadaten für alle Datenbanken zu aktualisieren, das Kontrollkästchen neben **Datenbanken**.  
  
3.  Mit der rechten Maustaste **Datenbanken**, oder die einzelnen Datenbank oder Datenbankschema, und wählen Sie dann **synchronisieren mit der Datenbank**.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt bei der Migration hängt von den Anforderungen Ihrer Projekte:  
  
-   Zum Anpassen der Zuordnung zwischen Oracle Schemas und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken und Schemas finden Sie unter [Mapping Oracle Schemas in SQL Server-Schemas &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md).  
  
-   Informationen zum Anpassen der Konfigurationsoptionen für die Projekte finden Sie unter [Setting Project Options Projektoptionen &#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md).  
  
-   Wenn die Zuordnung von Datentypen für Quell- und zieleinstellungen anpassen möchten, finden Sie unter [Mapping Oracle und SQL Server-Datentypen &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
-   Wenn Sie nicht zum Ausführen dieser Aufgaben verfügen, können Sie die Oracle-Datenbank-Objektdefinitionen in konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Objektdefinitionen. Weitere Informationen finden Sie unter [Konvertieren von Oracle Schemas &#40;OracleToSQL&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Oracle zu SQLServer-Datenbanken &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
