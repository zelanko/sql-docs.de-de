---
title: Herstellen einer Verbindung mit SQLServer (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- connecting to SQL Server 2008, SQL Server permission
- connecting to SQL Server 2008, synchronization
ms.assetid: 08233267-693e-46e6-9ca3-3a3dfd3d2be7
caps.latest.revision: 18
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 08744f04acbc5ad066be78b90f8880459ce74629
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "40392527"
---
# <a name="connecting-to-sql-server-mysqltosql"></a>Herstellen einer Verbindung mit SQL Server (MySqlToSql)
Um MySQL-Datenbanken zu SQL Server zu migrieren, müssen Sie mit der Zielinstanz von SQL Server verbinden. Wenn Sie eine Verbindung herstellen, wird SSMA Ruft Metadaten zu allen Datenbanken in der Instanz von SQL Server ab und Datenbank-Metadaten in der SQL Server-Metadaten-Explorer angezeigt. SSMA speichert Informationen von der Instanz von SQL Server Sie verbunden sind, jedoch werden keine Kennwörter gespeichert werden.  
  
Die Verbindung mit SQL Server bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie mit SQL Server herstellen, wenn Sie möchten, dass eine aktive Verbindung mit dem Server. Sie können offline arbeiten, bis Sie die Datenbankobjekte in SQL Server laden und Migrieren von Daten.  
  
Metadaten zur Instanz von SQL Server wird nicht automatisch synchronisiert. Um die Metadaten in SQL Server-Metadaten-Explorer zu aktualisieren, müssen Sie stattdessen manuell SQL Server-Metadaten aktualisieren. Weitere Informationen finden Sie unter "Synchronisieren von SQL Server-Metadaten" im Abschnitt weiter unten in diesem Thema.  
  
## <a name="required-sql-server-permissions"></a>Erforderliche SQL Server-Berechtigungen  
Das Konto, das verwendet wird, für die Verbindung mit SQL Server erfordert unterschiedliche Berechtigungen abhängig von den Aktionen, die das Konto ausführt:  
  
-   So konvertieren Sie Objekte von MySQL auf [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax, um Metadaten aus SQL Server zu aktualisieren, oder zum Speichern der konvertierten Syntax, um Skripts, das Konto muss die Berechtigung zum Anmelden bei der SQL Server-Instanz verfügen.  
  
-   Um Datenbankobjekte in SQL Server zu laden, ist die Anforderung mindestens die Mitgliedschaft in der **Db_owner** Datenbankrolle in der Zieldatenbank.  
  
## <a name="establishing-a-sql-server-connection"></a>Herstellen einer SQL Server-Verbindung  
Bevor Sie Objekte des MySQL-Datenbank in SQL Server-Syntax konvertieren, müssen Sie eine Verbindung mit SQL Server-Instanz einrichten, die MySQL-Datenbank oder Datenbanken migriert werden sollen.  
  
Wenn Sie die Verbindungseigenschaften definieren, geben Sie auch die Datenbank, in dem Objekte und Daten migriert werden. Sie können diese Zuordnung auf der Schemaebene MySQL anpassen, nach dem Herstellen einer Verbindung mit SQL Server. Weitere Informationen finden Sie unter [Zuordnen von MySQL-Datenbanken in SQL Server-Schemas &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
> [!IMPORTANT]  
> Bevor Sie versuchen, eine Verbindung mit SQL Server herstellen, stellen Sie sicher, dass die Instanz von SQL Server ausgeführt wird und Verbindungen akzeptieren.  
  
**Verbindung mit SQL Server**  
  
1.  Auf der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit SQL Server** (diese Option ist aktiviert, nach der Erstellung eines Projekts).  
  
    Wenn Sie zuvor eine Verbindung mit SQL Server hergestellt haben, gibt der Namen des Befehls werden **Wiederherstellen der Verbindung mit SQL Server**.  
  
2.  Klicken Sie im Dialogfeld Verbindung geben Sie ein, oder wählen Sie den Namen der Instanz von SQL Server.  
  
    -   Wenn Sie mit der Standardinstanz auf dem lokalen Computer herstellen, geben Sie **"localhost"** oder einen Punkt (**.**).  
  
    -   Wenn Sie mit der Standardinstanz auf einem anderen Computer herstellen, geben Sie den Namen des Computers ein.  
  
    -   Wenn Sie die zu einer benannten Instanz auf einem anderen Computer herstellen, geben Sie den Computernamen gefolgt von einem umgekehrten Schrägstrich und dann den Namen der Instanz an, wie z. B. MyServer\MyInstance.  
  
3.  Wenn Ihre Instanz von SQL Server für die Annahme von Verbindungen über einen nicht standardmäßigen Port konfiguriert ist, geben Sie die Portnummer, die verwendet wird, für die SQL Server-Verbindungen in der **Serverport** Feld. Für die Standardinstanz von SQL Server ist die Standardportnummer 1433. SSMA versucht für benannte Instanzen, die Nummer des Ports aus dem SQL Server-Browser-Dienst zu erhalten.  
  
4.  In der **Authentifizierung** wählen den Authentifizierungstyp, der für die Verbindung verwendet. Um das aktuelle Windows-Konto verwenden möchten, wählen **Windows-Authentifizierung**. Um eine SQL Server-Anmeldung verwenden, wählen Sie SQL Server-Authentifizierung, und geben Sie den Anmeldenamen und Kennwort.  
  
5.  Für sichere Verbindung zwei Steuerelemente hinzugefügt werden, die **Verbindung verschlüsseln** und **TrustServerCertificate** Kontrollkästchen. Nur wenn **Verbindung verschlüsseln** aktiviert ist, wird die **TrustServerCertificate** Kontrollkästchen wird angezeigt. Wenn **Verbindung verschlüsseln** (true) aktiviert ist und **TrustServerCertificate** ist deaktiviert (false), er überprüft das SQL Server-SSL-Zertifikat. Das Überprüfen des Serverzertifikats ist Teil des SSL-Handshakes und stellt sicher, dass es sich bei dem Server tatsächlich um den Server handelt, mit dem eine Verbindung hergestellt werden soll. Um dies zu gewährleisten, muss ein Zertifikat auf dem Client als auch auf dem Server installiert sein.  
  
6.  Klicken Sie auf Verbinden.  
  
**Kompatibilität mit höheren Versionen**  
  
Es ist zulässig, eine Verbindung herstellen/sich auf höhere Versionen von SQL Server herzustellen.  
  
1.  Sie werden zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, wenn das Projekt erstellt wurde ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005.  
  
2.  Sie werden zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, wenn das Projekt erstellt wurde ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008, aber es ist nicht zulässig, d. h. Verbindung mit niedrigeren Versionen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005.  
  
3.  Sie werden zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, wenn das Projekt erstellt wurde ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012.  
  
4.  Sie werden für die Verbindung nur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014 oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016, wenn das Projekt erstellt wurde ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014.  
  
5.  Kompatibilität mit höheren Versionen ist ungültig für "SQL Azure".  
  
||||||||  
|-|-|-|-|-|-|-|  
|**Projekt-Typ und VERSION des ZIELSERVERS**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005<br /> (Version: 9.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008<br /> (Version: 10.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012<br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014<br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016<br />(Version:13.x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008||Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012|||Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2014||||Benutzerkontensteuerung|Benutzerkontensteuerung||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]2016|||||Benutzerkontensteuerung||  
|SQL Azure||||||Benutzerkontensteuerung|  
  
> [!IMPORTANT]  
> Konvertierung der Datenbankobjekte erfolgt gemäß den Projekttyp, aber nicht gemäß der Version von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verbunden. Im Fall von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005-Projekt Konvertierung erfolgt gemäß [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, obwohl Sie mit einer höheren Version verbunden sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQL Server 2008/SQL Server 2012/SQL Server 2014/SQL Server 2016).  
  
## <a name="synchronizing-sql-server-metadata"></a>Synchronisieren von SQL Server-Metadaten  
Metadaten zu SQL Server-Datenbanken wird nicht automatisch aktualisiert. Die Metadaten in SQL Server-Metadaten-Explorer ist, dass eine Momentaufnahme der Metadaten, wenn Sie zunächst mit SQL Server verbunden, oder der letzten Ausführung, die Sie manuell die Metadaten aktualisiert werden. Sie können die Metadaten für alle Datenbanken oder für jede einzelne Datenbank oder Datenbankobjekt, das manuell aktualisieren.  
  
**Zum Synchronisieren von Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit SQL Server verbunden sind.  
  
2.  Wählen Sie in SQL Server-Metadaten-Explorer das Kontrollkästchen neben der Datenbank oder das Datenbankschema, die Sie aktualisieren möchten.  
  
    Z. B. um die Metadaten für alle Datenbanken zu aktualisieren, wählen Sie das Kontrollkästchen neben den Datenbanken an.  
  
3.  Mit der rechten Maustaste, Datenbanken, oder die einzelne Datenbank oder das Datenbankschema, und wählen Sie dann **synchronisieren mit der Datenbank**.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt bei der Migration hängt von den Anforderungen Ihrer Projekte:  
  
-   Informationen zum Anpassen der Zuordnung zwischen Schemas von MySQL und SQL Server-Datenbanken und Schemas finden Sie unter [Mapping MySQL-Datenbanken in SQL Server-Schemas &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
-   Informationen zum Anpassen der Konfigurationsoptionen für die Projekte finden Sie unter [Setting Project Options Projektoptionen &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)  
  
-   Wenn die Zuordnung von Datentypen für Quell- und zieleinstellungen anpassen möchten, finden Sie unter [Mapping MySQL und SQL Server-Datentypen &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   Wenn Sie nicht zum Ausführen dieser Aufgaben verfügen, können Sie die Objektdefinitionen für MySQL-Datenbank in SQL Server-Objektdefinitionen konvertieren. Weitere Informationen finden Sie unter [MySQL-Datenbanken konvertieren &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von MySQL-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
