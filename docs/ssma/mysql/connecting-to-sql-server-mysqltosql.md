---
title: Herstellen einer Verbindung mit SQL Server (mysqlto SQL) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Verbindung mit einer Ziel Instanz von SQL Server, um MySQL-Datenbanken zu migrieren SSMA Ruft Metadaten zu Datenbanken in SQL Server ab.
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- connecting to SQL Server 2008, SQL Server permission
- connecting to SQL Server 2008, synchronization
ms.assetid: 08233267-693e-46e6-9ca3-3a3dfd3d2be7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: f79784b6498f080b15f1ef370e8a3f31be81a871
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823295"
---
# <a name="connecting-to-sql-server-mysqltosql"></a>Herstellen einer Verbindung mit SQL Server (MySqlToSql)
Um MySQL-Datenbanken zu SQL Server zu migrieren, müssen Sie eine Verbindung mit der Ziel Instanz von SQL Server herstellen. Wenn Sie eine Verbindung herstellen, erhält SSMA Metadaten zu allen Datenbanken in der Instanz von SQL Server und zeigt Daten Bank Metadaten im SQL Server Metadaten-Explorer an. SSMA speichert Informationen über die Instanz von SQL Server mit denen Sie verbunden sind, speichert aber keine Kenn Wörter.  
  
Die Verbindung mit SQL Server bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung mit SQL Server herstellen, wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Datenbankobjekte in SQL Server laden und Daten migrieren.  
  
Metadaten über die Instanz von SQL Server werden nicht automatisch synchronisiert. Zum Aktualisieren der Metadaten in SQL Server Metadaten-Explorer müssen Sie stattdessen die SQL Server Metadaten manuell aktualisieren. Weitere Informationen finden Sie im Abschnitt "Synchronisieren von SQL Server Metadaten" weiter unten in diesem Thema.  
  
## <a name="required-sql-server-permissions"></a>Erforderliche SQL Server Berechtigungen  
Das Konto, das zum Herstellen einer Verbindung mit SQL Server verwendet wird, erfordert abhängig von den Aktionen, die das Konto ausführt, unterschiedliche Berechtigungen:  
  
-   Um MySQL-Objekte in [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax zu konvertieren, um Metadaten aus SQL Server zu aktualisieren oder um konvertierte Syntax in Skripts zu speichern, muss das Konto über die Berechtigung verfügen, sich bei der Instanz von SQL Server anzumelden.  
  
-   Zum Laden von Datenbankobjekten in SQL Server ist die Mindestanforderung für Berechtigungen die Mitgliedschaft in der Daten Bank Rolle **db_owner** in der Zieldatenbank.  
  
## <a name="establishing-a-sql-server-connection"></a>Einrichten einer SQL Server Verbindung  
Bevor Sie MySQL-Datenbankobjekte in SQL Server-Syntax konvertieren, müssen Sie eine Verbindung mit der Instanz von herstellen, SQL Server der Sie die MySQL-Datenbank oder die Datenbanken migrieren möchten.  
  
Wenn Sie die Verbindungs Eigenschaften definieren, geben Sie auch die Datenbank an, in die Objekte und Daten migriert werden. Sie können diese Zuordnung auf der MySQL-Schema Ebene anpassen, nachdem Sie eine Verbindung mit SQL Server hergestellt haben. Weitere Informationen finden Sie unter [Mapping MySQL-Datenbanken zu SQL Server Schemas &#40;mysqldesql&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
> [!IMPORTANT]  
> Bevor Sie versuchen, eine Verbindung mit SQL Server herzustellen, stellen Sie sicher, dass die Instanz von SQL Server ausgeführt wird und Verbindungen akzeptieren kann.  
  
**So stellen Sie eine Verbindung mit SQL Server her**  
  
1.  Wählen Sie im Menü **Datei** die Option **Verbinden mit SQL Server** aus (diese Option wird nach der Erstellung eines Projekts aktiviert).  
  
    Wenn Sie zuvor eine Verbindung mit SQL Server hergestellt haben, wird der Befehls Name **erneut mit SQL Server**verbunden.  
  
2.  Geben Sie im Dialogfeld Verbindung den Namen der Instanz von SQL Server ein, oder wählen Sie ihn aus.  
  
    -   Wenn Sie eine Verbindung mit der Standard Instanz auf dem lokalen Computer herstellen, können Sie **localhost** oder einen Punkt (**.**) eingeben.  
  
    -   Wenn Sie eine Verbindung mit der Standard Instanz auf einem anderen Computer herstellen, geben Sie den Namen des Computers ein.  
  
    -   Wenn Sie eine Verbindung mit einer benannten Instanz auf einem anderen Computer herstellen, geben Sie den Computernamen gefolgt von einem umgekehrten Schrägstrich und dem Instanznamen ein, z. b. MyServer\MyInstance.  
  
3.  Wenn die Instanz von SQL Server für die Annahme von Verbindungen an einem nicht standardmäßigen Port konfiguriert ist, geben Sie die Portnummer ein, die für SQL Server Verbindungen im Feld **Serverport** verwendet wird. Für die Standard Instanz von SQL Server ist die Standard Portnummer 1433. Bei benannten Instanzen wird von SSMA versucht, die Portnummer vom SQL Server-Browser-Dienst abzurufen.  
  
4.  Wählen Sie im Feld **Authentifizierung** den Authentifizierungstyp aus, der für die Verbindung verwendet werden soll. Um das aktuelle Windows-Konto zu verwenden, wählen Sie **Windows-Authentifizierung**aus. Wählen Sie SQL Server Authentifizierung aus, und geben Sie dann den Anmelde Namen und das Kennwort ein, um eine SQL Server Anmeldung zu verwenden.  
  
5.  Für eine sichere Verbindung werden zwei-Steuerelemente hinzugefügt: die Kontrollkästchen **Verbindung verschlüsseln** und **TrustServerCertificate** . Nur wenn **Verbindung verschlüsseln** aktiviert ist, ist das Kontrollkästchen **TrustServerCertificate** sichtbar. Wenn **Verbindung verschlüsseln** (true) und **TrustServerCertificate** deaktiviert (false) ist, wird das SQL Server SSL-Zertifikat überprüft. Das Überprüfen des Serverzertifikats ist Teil des SSL-Handshakes und stellt sicher, dass es sich bei dem Server tatsächlich um den Server handelt, mit dem eine Verbindung hergestellt werden soll. Um dies zu gewährleisten, muss ein Zertifikat sowohl auf Clientseite als auch auf Serverseite installiert werden.  
  
6.  Klicken Sie auf „Verbinden“.  
  
**Höhere Versions Kompatibilität**  
  
Es ist zulässig, eine Verbindung mit höheren Versionen von SQL Server herzustellen bzw. diese wiederherzustellen.  
  
1.  Sie können eine Verbindung mit 2008, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 oder 2016 herstellen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Wenn das erstellte Projekt auf 2005 festgelegt ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  Sie können eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 oder 2016 herstellen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Wenn das erstellte Projekt 2008 ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aber keine Verbindung mit niedrigeren Versionen, z. b. 2005, möglich ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Wenn das erstellte Projekt 2012 ist, können Sie eine Verbindung mit 2012 oder 2014 oder 2016 herstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
4.  Sie können nur dann eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 oder 2016 herstellen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Wenn das erstellte Projekt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 ist.  
  
5.  Höhere Versions Kompatibilität ist für "SQL Azure" nicht gültig.  
  
|Projekttyp und Ziel Server Version|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005<br /> (Version: 9. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008<br /> (Version: 10. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012<br />(Version: 11. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014<br />(Version: 12. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016<br />(Version: 13. x)|SQL Azure|  
|-|-|-|-|-|-|-|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|Ja|Ja|Ja|Ja|Ja||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||Ja|Ja|Ja|Ja||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||Ja|Ja|Ja||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014||||Ja|Ja||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2016|||||Ja||  
|SQL Azure||||||Ja|  
  
> [!IMPORTANT]  
> Die Konvertierung der Datenbankobjekte erfolgt gemäß dem Projekttyp, aber nicht mit der Version von, die mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verbunden ist. Im Fall von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 Project wird die Konvertierung gemäß 2005 durchgeführt, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auch wenn eine Verbindung mit einer höheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQL Server 2008/SQL Server 2012/SQL Server 2014/SQL Server 2016) besteht.  
  
## <a name="synchronizing-sql-server-metadata"></a>Synchronisieren von SQL Server-Metadaten  
Metadaten zu SQL Server-Datenbanken werden nicht automatisch aktualisiert. Bei den Metadaten in SQL Server Metadaten-Explorer handelt es sich um eine Momentaufnahme der Metadaten, wenn Sie zum ersten Mal eine Verbindung mit SQL Server hergestellt haben oder wenn Sie die Metadaten zuletzt manuell aktualisiert haben. Sie können Metadaten für alle Datenbanken oder für eine einzelne Datenbank oder ein Datenbankobjekt manuell aktualisieren.  
  
**So synchronisieren Sie Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit SQL Server verbunden sind.  
  
2.  Aktivieren Sie in SQL Server metadatenexplorer das Kontrollkästchen neben dem zu aktualisierenden Datenbankschema oder Datenbankschema.  
  
    Wenn Sie z. b. die Metadaten für alle Datenbanken aktualisieren möchten, aktivieren Sie das Kontrollkästchen neben Datenbanken.  
  
3.  Klicken Sie mit der rechten Maustaste auf Datenbanken oder die einzelne Datenbank oder das Datenbankschema, und wählen Sie dann **mit Datenbank synchronisieren**aus.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt der Migration hängt von Ihren Projektanforderungen ab:  
  
-   Informationen zum Anpassen der Zuordnung zwischen MySQL-Schemas und SQL Server-Datenbanken und-Schemas finden Sie unter [Mapping MySQL-Datenbanken zu SQL Server Schemas &#40;mysqlto SQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
-   Informationen zum Anpassen der Konfigurationsoptionen für die Projekte finden Sie unter [Festlegen von Projektoptionen &#40;mysqlto SQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)  
  
-   Informationen zum Anpassen der Zuordnung von Quell-und Ziel Datentypen finden Sie unter [Mapping MySQL and SQL Server Data Types &#40;mysqltosql&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   Wenn Sie diese Aufgaben nicht ausführen müssen, können Sie die MySQL-Datenbankobjekt Definitionen in SQL Server Objekt Definitionen konvertieren. Weitere Informationen finden Sie unter [umstellen von MySQL-Datenbanken &#40;mysqlto SQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von MySQL-Datenbanken zu SQL Server Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
