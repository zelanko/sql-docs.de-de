---
title: Herstellen einer Verbindung mit SQLServer (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- authentication
- instance of SQL Server
- metadata, refreshing
- ports
- refreshing metadata
- spaces in database names
- special characters
- SQL Server
- SQL Server, connecting
- SQL Server, connecting to
- SQL Server, reconnecting
ms.assetid: f84cf007-ddf1-4396-a07c-3e0729abc769
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 0bedb8ba74d7965df34a102fb0d53a0cbdb248dc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63139021"
---
# <a name="connecting-to-sql-server-accesstosql"></a>Herstellen einer Verbindung mit SQLServer (AccessToSQL)
Migrieren von Access-Datenbanken [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Sie müssen mit der Zielinstanz von verbinden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn Sie eine Verbindung herstellen, erhält der SSMA Metadaten zu den Datenbanken in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und zeigt Sie Datenbank-Metadaten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer. SSMA speichert Informationen über die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie verbunden sind, jedoch werden keine Kennwörter gespeichert.  
  
Die Verbindung mit SQL Server bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie mit SQL Server herstellen, wenn Sie möchten, dass eine aktive Verbindung mit dem Server. Sie können offline arbeiten, bis Sie die Datenbankobjekte in SQL Server laden und Migrieren von Daten.  
  
Metadaten zur Instanz von SQL Server wird nicht automatisch synchronisiert. Um die Metadaten in SQL Server-Metadaten-Explorer zu aktualisieren, müssen Sie stattdessen manuell SQL Server-Metadaten aktualisieren. Weitere Informationen finden Sie unter "Synchronisieren von SQL Server-Metadaten" im Abschnitt weiter unten in diesem Thema.  
  
## <a name="required-sql-server-permissions"></a>Erforderliche SQL Server-Berechtigungen  
Das Konto, das verwendet wird, für die Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] benötigen unterschiedliche Berechtigungen abhängig von den Aktionen, die von diesem Konto ausgeführt werden.  
  
-   So konvertieren Sie Objekte der Zugriff auf [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax, um Metadaten aus aktualisieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], oder um konvertierte Syntax auf Skripts speichern zu können, muss das Konto über die Berechtigung für die Anmeldung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Zum Laden von Datenbankobjekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Datenmigration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ist die Anforderung mindestens die Mitgliedschaft in der **Db_owner** Datenbankrolle in der Zieldatenbank.  
  
## <a name="establishing-a-sql-server-connection"></a>Herstellen einer SQL Server-Verbindung  
Bevor Sie den Zugriff auf Datenbankobjekte zu konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax müssen Sie eine Verbindung mit der Instanz von herstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wo Sie die Access-Datenbanken migrieren möchten.  
  
Wenn Sie die Verbindungseigenschaften definieren, geben Sie auch die Datenbank, in dem Objekte und Daten migriert werden. Sie können diese Zuordnung auf der Access-Datenbank-Ebene anpassen, nach dem Herstellen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Zuordnen von Quell- und Zieldatenbanken](mapping-source-and-target-databases-accesstosql.md).  
  
> [!IMPORTANT]  
> Vor dem Herstellen einer Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], stellen Sie sicher, dass die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird und Verbindungen akzeptieren. Weitere Informationen finden Sie unter "Herstellen einer Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Engine" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
**Verbindung mit SQL Server**  
  
1.  Auf der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit SQL Server**.  
  
    Wenn Sie zuvor mit verbunden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], der Namen des Befehls werden **Wiederherstellen der Verbindung mit SQL Server**.  
  
2.  In der **Servernamen** Feld, geben Sie ein oder wählen Sie den Namen der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Wenn Sie mit der Standardinstanz auf dem lokalen Computer herstellen, geben Sie **"localhost"** oder einen Punkt ( **.** ).  
  
    -   Wenn Sie mit der Standardinstanz auf einem anderen Computer herstellen, geben Sie den Namen des Computers ein.  
  
    -   Wenn Sie die zu einer benannten Instanz herstellen, geben Sie den Namen des Computers, einen umgekehrten Schrägstrich und den Namen der Instanz. Zum Beispiel: MyServer\MyInstance.  
  
    -   Verbindung mit einer aktiven Benutzerinstanz von [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)], eine Verbindung herstellen über named Pipes-Protokoll und Angeben des Pipenamens, z. B. \\ \\.\pipe\sql\query. Weitere Informationen finden Sie unter den [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)] Dokumentation.  
  
3.  Wenn Ihre Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konfiguriert ist annehmen von Verbindungen über einen nicht-Standardport, geben die Portnummer für die verwendeten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindungen in der **Serverport** Feld. Für die Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die Standardportnummer ist 1433. Für benannte Instanzen SSMA versucht, erhalten die Portnummer der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst.  
  
4.  In der **Datenbank** Geben Sie den Namen der Zieldatenbank für die Migration von Objekt und Daten.  
  
    Diese Option ist nicht verfügbar, wenn Sie zum Wiederherstellen der Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    Der Name der Zieldatenbank darf keine Leerzeichen oder Sonderzeichen enthalten. Sie können z. B. Access-Datenbanken Migrieren einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank mit dem Namen "Abc". Access-Datenbanken können nicht migriert werden, aber eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank mit dem Namen "a b-c".  
  
    Sie können diese Zuordnung pro Datenbank anpassen, nachdem Sie eine Verbindung herstellen. Weitere Informationen finden Sie unter [Zuordnen von Quell- und Zieldatenbanken](mapping-source-and-target-databases-accesstosql.md)  
  
5.  In der **Authentifizierung** Dropdown-Menü Wählen Sie im Menü, Authentifizierungstyp, der für die Verbindung verwendet. Um das aktuelle Windows-Konto verwenden möchten, wählen **Windows-Authentifizierung**. Verwenden einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldung wählen **SQL Server-Authentifizierung**, und geben Sie einen Benutzernamen und Kennwort.  
  
6.  Für sichere Verbindung zwei Steuerelemente hinzugefügt werden, **Verbindung verschlüsseln** Kontrollkästchen und **TrustServerCertificate** Kontrollkästchen. Nur wenn **Verbindung verschlüsseln** aktiviert ist **TrustServerCertificate** Kontrollkästchen wird angezeigt. Wenn **Verbindung verschlüsseln** ist checked(true) und **TrustServerCertificate** unchecked(false) ist, überprüft das SQL Server-SSL-Zertifikat. Das Überprüfen des Serverzertifikats ist Teil des SSL-Handshakes und stellt sicher, dass es sich bei dem Server tatsächlich um den Server handelt, mit dem eine Verbindung hergestellt werden soll. Um dies zu gewährleisten, muss ein Zertifikat auf dem Client als auch auf dem Server installiert sein.  
  
7.  Klicken Sie auf **Verbinden**.  
  
**Kompatibilität mit höheren Versionen**  
  
Es ist zulässig, eine Verbindung herstellen/sich auf höhere Versionen von SQL Server herzustellen.  
  
1.  Sie werden für die Verbindung mit SQL Server 2008 oder SQL Server 2012, wenn das Projekt erstellt wurde, SQL Server 2005 ist.  
  
2.  Sie werden für die Verbindung mit SQL Server 2012, wenn das Projekt erstellt wurde, SQL Server 2008 ist, aber es nicht zulässig ist für frühere Versionen, d. h. SQL Server 2005 die Verbindung.  
  
3.  Sie werden nur SQL Server 2012 Verbindung, wenn das Projekt erstellt wurde, SQL Server 2012 ist.  
  
4.  Kompatibilität für höhere Versionen gilt nicht für SQL Azure.  
  
||||||||
|-|-|-|-|-|-|-|
|**Projekt-Typ und VERSION des ZIELSERVERS**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 (Version: 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 (Version: 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 (Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 (Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016 (Version:13.x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|Ja|Ja|Ja|Ja|Ja||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||Ja|Ja|Ja|Ja||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||Ja|Ja|Ja||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014||||Ja|Ja||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016|||||Ja||
|SQL Azure||||||Ja|
  
> [!IMPORTANT]  
> Konvertierung der Datenbankobjekte wird gemäß den Projekttyp, aber nicht gemäß der Version von SQL Server verbunden durchgeführt. Bei SQL Server 2005-Projekt wird Konvertierung gemäß SQL Server 2005 durchgeführt, obwohl Sie mit einer höheren Version von SQL Server (SQL Server 2008/SQL Server 2012/SQL Server 2014/SQL Server 2016) verbunden sind.  
  
## <a name="synchronizing-sql-server-metadata"></a>Synchronisieren von SQL Server-Metadaten  
Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas ändern, nachdem Sie eine Verbindung herstellen, können Sie die Metadaten mit dem Server synchronisieren.  
  
**Zum Synchronisieren von SQL Server-Metadaten**  
  
-   In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, Rechtsklick **Datenbanken**, und wählen Sie dann **synchronisieren mit der Datenbank**.  
  
## <a name="reconnecting-to-sql-server"></a>Wiederherstellen der Verbindung mit SQLServer  
Die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie zum Wiederherstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ggf. eine aktive Verbindung mit dem Server. Sie können offline arbeiten, bis Sie die Datenbankobjekte in laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Daten migrieren.  
  
Das Verfahren zum Wiederherstellen der Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist identisch mit dem Verfahren zum Herstellen einer Verbindung.  
  
## <a name="next-steps"></a>Nächste Schritte  
Wenn Sie die Zuordnung zwischen Quell-und Zieldatenbanken anpassen möchten, finden Sie unter [Zuordnung Quell- und Zieldatenbank](mapping-source-and-target-databases-accesstosql.md) , andernfalls der nächste Schritt besteht, um Datenbankobjekte zu konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von Syntax [konvertieren Datenbankobjekte](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
