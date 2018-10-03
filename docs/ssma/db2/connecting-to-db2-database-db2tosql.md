---
title: Herstellen einer Verbindung mit DB2-Datenbank (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 5eb5801d-f0c3-4127-97c0-0b1ef49f4844
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: c280b28082a1f85074b129d7a659333d7323d879
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47735548"
---
# <a name="connecting-to-db2-database-db2tosql"></a>Herstellen einer Verbindung mit DB2-Datenbank (DB2ToSQL)
Zum Migrieren von DB2-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Sie müssen eine Verbindung, mit der DB2-Datenbank, die Sie migrieren möchten. Wenn Sie eine Verbindung herstellen, SSMA Ruft Metadaten für alle DB2-Schemas, und klicken Sie dann im DB2-Metadaten-Explorer-Bereich angezeigt. SSMA speichert Informationen zu den Datenbankserver, aber die Kennwörter werden nicht gespeichert.  
  
Die Verbindung mit der Datenbank bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut verbinden, wenn Sie möchten, dass eine aktive Verbindung mit der Datenbank.  
  
Metadaten zu der DB2-Datenbank wird nicht automatisch aktualisiert. Stattdessen sollten Sie die Metadaten in DB2-Metadaten-Explorer zu aktualisieren, müssen Sie manuell es aktualisieren. Weitere Informationen finden Sie im Abschnitt "Aktualisieren der DB2-Metadaten" weiter unten in diesem Thema.  
  
## <a name="required-db2-permissions"></a>Erforderlichen DB2-Berechtigungen  
Benutzerautorisierung definiert die Liste der Befehle und Objekte, die für einen Benutzer verfügbar sind. Dadurch werden Benutzeraktionen Listensteuerelemente. In DB2 sind vordefinierte Gruppen von Berechtigungen für die Autorisierung, sowohl auf Instanzebene und auf der Ebene einer DB2-Datenbank. Dies ermöglicht der SSMA zum Abrufen von Metadaten aus Schemas im Besitz des Benutzers eine Verbindung herstellt. Um Metadaten für Objekte in anderen Schemas zu erhalten, und klicken Sie dann die Objekte in diesen Schemas konvertieren, muss das Konto folgenden Berechtigungen verfügen:  
  
-   Schema wird für die schemamigration normalerweise auf öffentlichen zugreifen, wenn das Schlüsselwort "RESTRICT" in erstellen verwendet wurde  
  
-   Datenzugriff für die Datenmigration erfordert DATAACCESS  
  
## <a name="establishing-a-connection-to-db2"></a>Herstellen einer Verbindung mit DB2  
Wenn Sie eine Verbindung mit einer Datenbank herstellen, SSMA liest die Datenbankmetadaten und fügt dann diese Metadaten zu der Projektdatei. Diese Metadaten werden vom SSMA verwendet, wenn Objekte konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax, und wenn es Daten migriert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können diese Metadaten im DB2-Metadaten-Explorer durchsuchen und überprüfen Sie die Eigenschaften einzelner Datenbankobjekte.  
  
> [!IMPORTANT]  
> Bevor Sie versuchen, eine Verbindung herstellen, stellen Sie sicher, dass der Datenbankserver ausgeführt wird und Verbindungen akzeptieren.  
  
**Verbindung mit DB2**  
  
1.  Auf der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit DB2**.  
  
    Wenn Sie zuvor mit DB2 verbunden, gibt der Namen des Befehls werden **Wiederherstellen der Verbindung mit DB2**.  
  
2.  In der **Anbieter** Feld Sie sehen die **OLE DB-Anbieter** dort gilt zurzeit der einzige DB2 Client Access-Provider.  
  
3.  In der **Manager** Feld, Sie haben die Wahl zwischen **Db2 für zOS erörtert**, oder **DB2 für LUW**  
  
4.  In der **Modus** wählen **Modus "Standard"**, oder **verbindungszeichenfolgenmodus**.  
  
    Verwenden Sie Modus "standard", um den Servernamen und Port anzugeben. Verwenden Sie Namen Dienstmodus, um den Namen des DB2-Diensts manuell anzugeben. Verwenden Sie verbindungszeichenfolgenmodus, um eine vollständige Verbindungszeichenfolge bereitstellen.  
  
5.  Bei Auswahl von **Modus "Standard"**, geben Sie die folgenden Werte:  
  
    -   In der **Servernamen** Feld eingeben oder auswählen, den Namen oder IP-Adresse des Datenbankservers.  
  
    -   Wenn der Datenbankserver nicht konfiguriert ist, um auf Clientverbindungen standardmäßig port (1521) verwenden, geben Sie die Portnummer, die verwendet wird, für die DB2-Verbindungen in der **Serverport** Feld.  
  
    -   In der **Serverport** Geben Sie die Nummer des TCP/IP-Ports.  
  
    -   In der **Anfangskatalog** Geben Sie den Datenbanknamen  
  
    -   In der **Benutzernamen** Geben Sie ein DB2-Konto, das die erforderlichen Berechtigungen verfügt.  
  
    -   In der **Kennwort** Geben Sie das Kennwort für den angegebenen Benutzernamen ein.  
  
6.  Bei Auswahl von **verbindungszeichenfolgenmodus**, geben Sie eine Verbindungszeichenfolge in der **Verbindungszeichenfolge** Feld.  
  
    Das folgende Beispiel zeigt eine OLE DB-Verbindungszeichenfolge:  
  
    `Provider=OraOLEDB.DB2;Data Source=MyDB2DB;User Id=myUsername;Password=myPassword;`  
  
    Das folgende Beispiel zeigt eine DB2-Client-Verbindungszeichenfolge, die die integrierte Sicherheit verwendet wird:  
  
    `Data Source=MyDB2DB;Integrated Security=yes;`  
  
    Weitere Informationen finden Sie unter [auf Oracle Verbinden &#40;OracleToSQL&#41;](../../ssma/oracle/connect-to-oracle-oracletosql.md).  
  
## <a name="reconnecting-to-db2"></a>Wiederherstellen der Verbindung mit DB2  
Die Verbindung mit dem Datenbankserver bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut verbinden, wenn Sie möchten, dass eine aktive Verbindung mit der Datenbank. Sie können offline arbeiten, bis Sie die Metadaten aktualisieren, laden Sie die Datenbankobjekte in möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und Daten migrieren.  
  
## <a name="refreshing-db2-metadata"></a>Aktualisieren von DB2-Metadaten  
Metadaten zu der DB2-Datenbank wird nicht automatisch aktualisiert. Die Metadaten in DB2-Metadaten-Explorer ist eine Momentaufnahme der Metadaten, wenn Sie zuerst eine Verbindung hergestellt oder der letzten, dass Sie manuell die Metadaten aktualisiert werden. Sie können die Metadaten für alle Schemas, ein einzelnes Schema oder einzelne Datenbankobjekte manuell aktualisieren.  
  
**Aktualisieren von Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit der Datenbank verbunden sind.  
  
2.  Wählen Sie in DB2-Metadaten-Explorer das Kontrollkästchen neben jedem Schema oder die Datenbank-Objekt, das Sie aktualisieren möchten.  
  
3.  Mit der rechten Maustaste **Schemas**, oder die einzelnes Schema oder die Datenbank-Objekt, und wählen Sie dann **Refresh from Database aktualisieren**.  
  
    SSMA wird angezeigt, wenn Sie nicht über eine aktive Verbindung verfügen, die **Herstellen einer Verbindung mit DB2** Dialogfeld, sodass Sie eine Verbindung herstellen können.  
  
4.  Geben Sie in der Aktualisierung von Datenbank (Dialogfeld) welche Objekte aktualisiert.  
  
    -   Um ein Objekt zu aktualisieren, klicken Sie auf die **Active** Feld neben dem Objekt, bis ein Pfeil angezeigt wird.  
  
    -   Um zu verhindern, dass ein Objekt aktualisiert wird, klicken Sie auf die **Active** Feld neben dem Objekt, bis ein **X** angezeigt wird.  
  
    -   Klicken Sie zum Aktualisieren, oder lehnen Sie eine Kategorie von Objekten ab, auf die **Active** Feld neben dem Ordner "Kategorie".  
  
    Um die Definitionen der farbcodierung anzuzeigen, klicken Sie auf die **Legende** Schaltfläche.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-step"></a>Nächster Schritt  
  
-   Der nächste Schritt des Migrationsvorgangs besteht darin [Herstellen einer Verbindung mit SQL Server](http://msdn.microsoft.com/b59803cb-3cc6-41cc-8553-faf90851410e).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von DB2-Datenbanken zu SQLServer &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
