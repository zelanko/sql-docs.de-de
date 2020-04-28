---
title: Herstellen einer Verbindung mit SQL Server (accesstosql) | Microsoft-Dokumentation
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
ms.openlocfilehash: 4630ae8d92dbf0e9b1c5bf615dd82d436a5751f5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68006648"
---
# <a name="connecting-to-sql-server-accesstosql"></a>Herstellen einer Verbindung mit SQL Server (accesstosql)
Wenn Sie Access-Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Banken zu migrieren möchten, müssen Sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Verbindung mit der-Ziel Instanz herstellen. Wenn Sie eine Verbindung herstellen, werden von SSMA Metadaten zu den Datenbanken [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der Instanz von abgerufen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Daten Bank Metadaten im metadatenexplorer angezeigt. SSMA speichert Informationen zu der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mit der Sie verbunden sind, speichert aber keine Kenn Wörter.  
  
Die Verbindung mit SQL Server bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung mit SQL Server herstellen, wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Datenbankobjekte in SQL Server laden und Daten migrieren.  
  
Metadaten über die Instanz von SQL Server werden nicht automatisch synchronisiert. Zum Aktualisieren der Metadaten in SQL Server Metadaten-Explorer müssen Sie stattdessen die SQL Server Metadaten manuell aktualisieren. Weitere Informationen finden Sie im Abschnitt "Synchronisieren von SQL Server Metadaten" weiter unten in diesem Thema.  
  
## <a name="required-sql-server-permissions"></a>Erforderliche SQL Server Berechtigungen  
Das Konto, das verwendet wird, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Verbindung mit herzustellen, erfordert abhängig von den Aktionen, die von diesem Konto ausgeführt werden, unterschiedliche Berechtigungen.  
  
-   Das Konto muss über die [!INCLUDE[tsql](../../includes/tsql-md.md)] Berechtigung verfügen, sich bei der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]anzumelden, um Zugriffs Objekte in die-Syntax zu konvertieren, um Metadaten aus zu aktualisieren oder um konvertierte Syntax in Skripts zu speichern.  
  
-   Zum Laden von Daten Bank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekten in und zum Migrieren von Daten zu müssen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die Mindestanforderungen für die **db_owner** -Daten Bank Rolle in der Zieldatenbank erfüllt werden.  
  
## <a name="establishing-a-sql-server-connection"></a>Einrichten einer SQL Server Verbindung  
Bevor Sie Access-Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Syntax konvertieren, müssen Sie eine Verbindung mit der Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von herstellen, in der Sie die Access-Datenbanken migrieren möchten.  
  
Wenn Sie die Verbindungs Eigenschaften definieren, geben Sie auch die Datenbank an, in die Objekte und Daten migriert werden. Sie können diese Zuordnung auf der Ebene der Zugriffs Datenbank anpassen, nachdem Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]eine Verbindung mit hergestellt haben. Weitere Informationen finden Sie unter [Mapping von Quell-und Ziel Datenbanken](mapping-source-and-target-databases-accesstosql.md).  
  
> [!IMPORTANT]  
> Bevor Sie eine Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mit herstellen, stellen Sie sicher, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dass die Instanz von ausgeführt wird und Verbindungen akzeptieren kann. Weitere Informationen finden Sie unter "Herstellen einer Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit dem Datenbank-Engine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] " in der-Online Dokumentation.  
  
**So stellen Sie eine Verbindung mit SQL Server her**  
  
1.  Wählen Sie im Menü **Datei** die Option **mit SQL Server verbinden**aus.  
  
    Wenn Sie zuvor eine Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mit hergestellt haben, wird der Befehls Name **erneut mit SQL Server**verbunden.  
  
2.  Geben Sie im Feld **Server Name** den Namen der Instanz von ein, oder wählen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Sie ihn aus.  
  
    -   Wenn Sie eine Verbindung mit der Standard Instanz auf dem lokalen Computer herstellen, können Sie **localhost** oder einen Punkt (**.**) eingeben.  
  
    -   Wenn Sie eine Verbindung mit der Standard Instanz auf einem anderen Computer herstellen, geben Sie den Namen des Computers ein.  
  
    -   Wenn Sie eine Verbindung mit einer benannten Instanz herstellen, geben Sie den Computernamen, einen umgekehrten Schrägstrich und den Instanznamen ein. Beispiel: MyServer\MyInstance.  
  
    -   Stellen Sie eine Verbindung mit einer aktiven Benutzer [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)]Instanz von her, indem Sie das Named Pipes-Protokoll verwenden und den Pipenamen angeben, z \\ \\. b. .\pipe\sql\query. Weitere Informationen finden Sie in der Dokumentation zu [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)].  
  
3.  Wenn die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Annahme von Verbindungen an einem nicht standardmäßigen Port konfiguriert ist, geben Sie die Portnummer ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die im Feld **Serverport** für Verbindungen verwendet wird. Die Standard Portnummer für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die Standard Instanz von ist 1433. Bei benannten Instanzen wird von SSMA versucht, die Portnummer vom- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Dienst abzurufen.  
  
4.  Geben Sie im Feld **Datenbank** den Namen der Zieldatenbank für die Objekt-und Datenmigration ein.  
  
    Diese Option ist nicht verfügbar, wenn Sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erneute Verbindung mit herstellen.  
  
    Der Name der Zieldatenbank darf keine Leerzeichen oder Sonderzeichen enthalten. Beispielsweise können Sie Access-Datenbanken zu einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank mit dem Namen "ABC" migrieren. Access-Datenbanken können jedoch nicht zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einer Datenbank mit dem Namen "a b-c" migriert werden.  
  
    Nachdem Sie eine Verbindung hergestellt haben, können Sie diese Zuordnung pro Datenbank anpassen. Weitere Informationen finden Sie unter [Zuordnung von Quell-und Ziel Datenbanken](mapping-source-and-target-databases-accesstosql.md) .  
  
5.  Wählen Sie im Dropdown Menü **Authentifizierung** den Authentifizierungstyp aus, der für die Verbindung verwendet werden soll. Um das aktuelle Windows-Konto zu verwenden, wählen Sie **Windows-Authentifizierung**aus. Wählen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Server Authentifizierung**aus, und geben Sie einen Benutzernamen und ein Kennwort ein, um einen Anmelde Namen zu verwenden.  
  
6.  Für eine sichere Verbindung werden zwei Steuerelemente hinzugefügt, das Kontrollkästchen **Verbindung verschlüsseln** und das Kontrollkästchen **TrustServerCertificate** . Nur wenn das Kontrollkästchen **Verbindung verschlüsseln** aktiviert ist, wird das Kontrollkästchen **TrustServerCertificate** angezeigt. Wenn die Option **Verbindung verschlüsseln** (true) und **TrustServerCertificate** deaktiviert (false) aktiviert ist, überprüft das SQL Server SSL-Zertifikat. Das Überprüfen des Serverzertifikats ist Teil des SSL-Handshakes und stellt sicher, dass es sich bei dem Server tatsächlich um den Server handelt, mit dem eine Verbindung hergestellt werden soll. Um dies zu gewährleisten, muss ein Zertifikat sowohl auf Clientseite als auch auf Serverseite installiert werden.  
  
7.  Klicken Sie auf **Verbinden**.  
  
**Höhere Versions Kompatibilität**  
  
Es ist zulässig, eine Verbindung mit höheren Versionen von SQL Server herzustellen bzw. diese wiederherzustellen.  
  
1.  Wenn das erstellte Projekt SQL Server 2005 ist, können Sie eine Verbindung mit SQL Server 2008 oder SQL Server 2012 herstellen.  
  
2.  Wenn das erstellte Projekt SQL Server 2008 ist, können Sie eine Verbindung mit SQL Server 2012 herstellen, aber es ist nicht zulässig, eine Verbindung mit niedrigeren Versionen herzustellen, z. b. SQL Server 2005.  
  
3.  Sie können nur dann eine Verbindung mit SQL Server 2012 herstellen, wenn das erstellte Projekt SQL Server 2012 ist.  
  
4.  Höhere Versions Kompatibilität ist für SQL Azure ungültig.  
  
||||||||
|-|-|-|-|-|-|-|
|**Projekttyp und Ziel Server Version**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2005 (Version: 9. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2008 (Version: 10. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2012 (Version: 11. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014 (Version: 12. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2016 (Version: 13. x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|Ja|Ja|Ja|Ja|Ja||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||Ja|Ja|Ja|Ja||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||Ja|Ja|Ja||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014||||Ja|Ja||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016|||||Ja||
|SQL Azure||||||Ja|
  
> [!IMPORTANT]  
> Die Konvertierung der Datenbankobjekte wird gemäß dem Projekttyp ausgeführt, aber nicht mit der Version der SQL Server, die mit verbunden ist. Bei SQL Server 2005-Projekt wird die Konvertierung gemäß SQL Server 2005 durchgeführt, auch wenn eine Verbindung mit einer höheren Version von SQL Server (SQL Server 2008/SQL Server 2012/SQL Server 2014/SQL Server 2016) besteht.  
  
## <a name="synchronizing-sql-server-metadata"></a>Synchronisieren von SQL Server-Metadaten  
Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas geändert werden, nachdem Sie eine Verbindung hergestellt haben, können Sie die Metadaten mit dem Server synchronisieren.  
  
**So synchronisieren Sie SQL Server Metadaten**  
  
-   Klicken [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie im metadatenexplorer mit der rechten Maustaste auf **Datenbanken**, und wählen Sie dann **mit Datenbank synchronisieren**.  
  
## <a name="reconnecting-to-sql-server"></a>Erneutes Herstellen einer Verbindung mit SQL Server  
Die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindung mit herstellen, wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in laden und Daten migrieren.  
  
Die Vorgehensweise für das erneute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Herstellen einer Verbindung mit entspricht dem Verfahren zum Herstellen einer Verbindung.  
  
## <a name="next-steps"></a>Nächste Schritte  
Wenn Sie die Zuordnung zwischen Quell-und Ziel Datenbanken anpassen möchten, finden Sie weitere Informationen unter [Zuordnung von Quell-und Ziel Datenbanken](mapping-source-and-target-databases-accesstosql.md) . andernfalls ist der nächste [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schritt das Konvertieren von Datenbankobjekten in eine Syntax mithilfe von [Convert Database Objects](converting-access-database-objects-accesstosql.md) .  
  
## <a name="see-also"></a>Weitere Informationen  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
