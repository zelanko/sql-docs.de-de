---
title: Ausführen von „DQSInstaller.exe“ zum Abschließen der Installation von Data Quality Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 7a8c96e0-1328-4f35-97fc-b6d9cb808bae
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 88b80e0eeba26e1a2c03f795d7ae3ce6fa796f10
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65480485"
---
# <a name="run-dqsinstallerexe-to-complete-data-quality-server-installation"></a>Ausführen von DQSInstaller.exe zum Abschließen der Installation von Data Quality Server
  Um die Installation von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] abzuschließen, müssen Sie nach dem Installieren von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]die Datei DQSInstaller.exe ausführen. In diesem Thema wird beschrieben, wie Sie **DQSInstaller.exe** über den Startbildschirm, das Menü **Start** , Windows-Explorer oder die Eingabeaufforderung ausführen. Sie können die Datei „DQSInstaller.exe“ mit jeder dieser Methoden ausführen.  
  
##  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   Bei der Installation von SQL Server müssen Sie auf der Seite „Funktionsauswahl“ unter **Datenbank-Engine-Dienste** die Option **Data Quality Services** ausgewählt haben, und die SQL Server-Installation muss abgeschlossen sein. Weitere Informationen finden Sie unter [Install Data Quality Services](install-data-quality-services.md).  
  
-   Das Windows-Benutzerkonto muss Mitglied der festen Serverrolle sysadmin in der SQL Server-Datenbank-Engine-Instanz sein.  
  
-   Sie müssen als Mitglied der Administratorengruppe auf dem Computer, wo Sie DQSInstaller.exe ausführen, angemeldet sein.  
  
##  <a name="WindowsExplorer"></a> Ausführen von "DQSInstaller.exe" über den Startbildschirm, das Startmenü oder Windows-Explorer  
  
1.  Führen Sie auf dem Computer, auf dem Sie [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]installieren möchten, anhand einer der folgenden Methoden die Datei DQSInstaller.exe aus:  
  
    -   **Startbildschirm:** Klicken Sie auf dem **Startbildschirm** auf **Data Quality Server-Installationsprogramm**.  
  
    -   **Startmenü:** Klicken Sie auf der Taskleiste auf **starten**, zeigen Sie auf **Programme**, klicken Sie auf **Microsoft SQL Server 2014**. Klicken Sie unter **Microsoft SQL Server 2014**, klicken Sie auf **Data Quality Services**, und klicken Sie dann auf **Data Quality Server-Installationsprogramm.**  
  
    -   **Windows Explorer:** Suchen Sie die Datei DQSInstaller.exe aus. Wenn Sie z. B. die Standardinstanz von SQL Server installiert haben, steht die Datei DQSInstaller.exe in der Regel unter C:\Programme\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn zur Verfügung. Doppelklicken Sie auf die Datei DQSInstaller.exe.  
  
2.  Ein Eingabeaufforderungsfenster wird angezeigt, in dem Sie den Fortschritt der Installation verfolgen können. Achten Sie dabei auf die drei folgenden Punkte:  
  
    1.  Das Installationsprogramm erstellt die Installationsprotokolldatei DQS_install.log, die Informationen zu den Aktionen enthält, die beim Ausführen der Datei DQSInstaller.exe ausgeführt werden. Wenn Sie die Standardinstanz von SQL Server installiert haben, ist die Datei DQS_install.log unter C:\Programme\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log verfügbar.  
  
    2.  Das Installationsprogramm verwendet die standardmäßige Serversortierung, SQL_Latin1_General_CP1_CI_AS, zum Installieren von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)].  
  
        > [!IMPORTANT]  
        >  Sie können einen anderen Serversortierungswert zum Installieren von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] nur dann angeben, wenn Sie die Datei DQSInstaller.exe über die Eingabeaufforderung ausführen. Weitere Informationen finden Sie unter [Ausführen von „DQSInstaller.exe“ über Befehlszeile](#CommandPrompt) weiter unten in diesem Thema.  
  
    3.  Das Installationsprogramm überprüft, ob auf dem Computer aufgrund von neu installierten Updates ein Neustart aussteht. Wenn ein Neustart aussteht, wird eine Meldung angezeigt, die Sie darüber informiert. Sie können die Installation fortsetzen oder abbrechen, indem Sie J bzw. N drücken. Wenn ein Neustart aussteht, wird empfohlen, die Installation abzubrechen, den Computer neu zu starten und die Datei DQSInstaller.exe erneut auszuführen.  
  
3.  Sie werden aufgefordert, ein Kennwort für den Datenbank-Hauptschlüssel einzugeben. Der Datenbank-Hauptschlüssel ist erforderlich, um die Schlüssel des Verweisdatendienst-Anbieters zu verschlüsseln, die in der DQS_MAIN-Datenbank gespeichert werden, wenn Sie später Verweisdatenanbieter in [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) einrichten.  
  
    > [!IMPORTANT]  
    >  Das Kennwort muss mindestens 8 Zeichen lang sein und muss Zeichen aus drei der folgenden vier Kategorien enthalten: lateinische Großbuchstaben (A, B, C,... Z), lateinische Kleinbuchstaben (a, b, c,... z), Zahlen (0, 1, 2,... 9) sowie nicht alphanumerische oder Sonderzeichen (~!@#$%^&*()_-+=|\\{}[]:;"'<>,.?/). Beispiel: P@ssword. Wenn das aktuelle Kennwort die Anforderung nicht erfüllt, werden Sie vom Installationsprogramm aufgefordert, ein anderes Kennwort einzugeben.  
  
4.  Geben Sie ein Kennwort an, bestätigen Sie das Kennwort, und drücken Sie dann die EINGABETASTE, um mit der Installation fortzufahren.  
  
    > [!IMPORTANT]  
    >  Sie müssen das für den Datenbank-Hauptschlüssel angegebene Kennwort aufbewahren, da Sie es in Zukunft beim Wiederherstellen der DQS-Datenbanken aus einer Sicherung benötigen, wenn Sie dies auswählen. Weitere Informationen zum Wiederherstellen von DQS-Datenbanken finden Sie unter [Sichern und Wiederherstellen von DQS-Datenbanken](../backing-up-and-restoring-dqs-databases.md).  
  
5.  Wenn eine Master Data Services-Datenbank in der gleichen SQL Server-Instanz wie der [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]vorhanden ist, erstellt das Installationsprogramm einen der Master Data Services-Anmeldung zugeordneten Benutzer, und erteilt ihm die dqs_administrator-Rolle in der Datenbank DQS_MAIN. Informationen zum Installieren von Master Data Services und zum Erstellen einer Master Data Services-Datenbank finden Sie unter [Installieren von Master Data Services](../../master-data-services/install-windows/install-master-data-services.md).  
  
6.  Nachdem die Installation erfolgreich abgeschlossen wurde, wird eine Abschlussmeldung angezeigt. Drücken Sie eine beliebige Taste, um das Eingabeaufforderungsfenster zu schließen.  
  
##  <a name="CommandPrompt"></a> Ausführen von „DQSInstaller.exe“ über Befehlszeile  
 Sie können DQSInstaller.exe über die Eingabeaufforderung mit den folgenden Befehlszeilenparametern ausführen:  
  
|DQSInstaller.exe-Parameter|Description|Beispielsyntax|  
|--------------------------------|-----------------|-------------------|  
|-collation|Die Serversortierung, die zum Installieren von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)]verwendet werden soll.<br /><br /> DQS unterstützt nur eine Sortierung, bei der die Groß-/Kleinschreibung nicht beachtet wird. Wenn Sie eine Sortierung angeben, bei der die Groß-/Kleinschreibung beachtet wird, versucht das Installationsprogramm, die Version der angegebenen Sortierung zu verwenden, bei der die Groß-/Kleinschreibung nicht beachtet wird. Wenn keine Version vorhanden ist, bei der die Groß-/Kleinschreibung nicht beachtet wird oder wenn die Sortierung von SQL nicht unterstützt wird, kann die [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] -Installation nicht durchgeführt werden.<br /><br /> Wenn keine Serversortierung angegeben wird, wird die Standardsortierung, SQL_Latin1_General_CP1_CI_AS, verwendet.|`dqsinstaller.exe -collation <collation_name>`|  
|-upgradedlls|Überspringt das Neuerstellen der DQS-Datenbanken (DQS_MAIN, DQS_PROJECTS und DQS_STAGING_DATA) und aktualisiert nur die SQLCLR-Assemblys (SQL Common Language Runtime), die von DQS in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Datenbank verwendet werden.<br /><br /> Weitere Informationen finden Sie unter [Aktualisieren der SQLCLR-Assemblys nach dem Aktualisieren von .NET Framework](upgrade-sqlclr-assemblies-after-net-framework-update.md).|`dqsinstaller.exe -upgradedlls`|  
|-exportkbs|Exportieren Sie alle Wissensdatenbanken in eine DQS-Sicherungsdatei (DQSB-Format). Sie müssen auch den vollständigen Pfad und den Dateinamen angeben, wohin Sie alle Wissensdatenbanken exportieren möchten.<br /><br /> Weitere Informationen finden Sie unter [Export und Importieren von DQS-Wissensdatenbanken mit DQSInstaller.exe](export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md).|`dqsinstaller.exe -exportkbs <path><filename>`<br /><br /> Beispiel: `dqsinstaller.exe -exportkbs c:\DQSBackup.dqsb`|  
|-importkbs|Importieren Sie alle Wissensdatenbanken aus einer DQS-Sicherungsdatei (DQSB-Format), nachdem Sie die [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] -Installation abgeschlossen haben. Sie müssen auch den vollständigen Pfad und den Dateinamen angeben, von wo aus Sie alle Wissensdatenbanken importieren möchten.<br /><br /> Weitere Informationen finden Sie unter [Export und Importieren von DQS-Wissensdatenbanken mit DQSInstaller.exe](export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md).|`dqsinstaller.exe -importkbs <path><filename>`<br /><br /> Beispiel: `dqsinstaller.exe -importkbs c:\DQSBackup.dqsb`|  
|-upgrade|Aktualisiert das DQS-Datenbankschema. Sie müssen diesen Parameter verwenden, nachdem Sie auf einer zuvor konfigurierten DQS-Instanz ein SQL Server-Update installiert haben. Weitere Informationen finden Sie unter [Aktualisieren des DQS-Datenbankschemas nach der Installation eines SQL Server-Updates](upgrade-dqs-databases-schema-after-installing-sql-server-update.md).|`dqsinstaller.exe -upgrade`|  
|-uninstall|Deinstalliert [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] von der aktuellen SQL Server-Instanz.<br /><br /> Sie können auch alle Wissensdatenbanken in der vorhandenen Data Quality Server-Installation in eine DQS-Sicherungsdatei (DQSB-Format) exportieren und dann Data Quality Server deinstallieren. Weitere Informationen finden Sie unter [Export und Importieren von DQS-Wissensdatenbanken mit DQSInstaller.exe](export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md).<br /><br /> **\*\* Wichtig \*\*** Wenn Sie [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] mit dem `-uninstall` -Befehlszeilenparameter aus einer SQL Server-Instanz deinstallieren, werden im Rahmen des Deinstallationsvorgangs alle DQS-Objekte gelöscht. Es ist nicht erforderlich, sie nach der Deinstallation von [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] manuell zu löschen, wie unter [Entfernen von Data Quality Server-Objekten](../../sql-server/install/remove-data-quality-server-objects.md)erwähnt.|**So deinstallieren Sie nur Data Quality Server** <br /> `dqsinstaller.exe -uninstall`<br /><br /> **So exportieren Sie alle Wissensdatenbanken in eine Datei und deinstallieren dann Data Quality Server** <br /> `dqsinstaller.exe -uninstall <path><filename>` <br />Beispiel: `dqsinstaller.exe -uninstall c:\DQSBackup.dqsb`|  
  
 **So führen Sie "DQSInstaller.exe" über die Eingabeaufforderung aus**  
  
1.  Öffnen Sie die Eingabeaufforderung.  
  
2.  Wechseln Sie an der Eingabeaufforderung zu dem Verzeichnis, in dem DQSInstaller.exe enthalten ist. Wenn Sie z. B. die Standardinstanz von SQL Server installiert haben, steht die Datei DQSInstaller.exe in der Regel unter C:\Programme\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn zur Verfügung:  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
    ```  
  
3.  Führen Sie an der Eingabeaufforderung DQSInstaller.exe mit oder ohne Befehlszeilenparameter aus:  
  
    -   **Ohne Befehlszeilenparameter:** Geben Sie `dqsinstaller.exe` ein, und drücken Sie dann die EINGABETASTE.  
  
    -   **Mit Befehlszeilenparameter:** Geben Sie den erforderlichen Befehl wie in der Tabelle oben bereits erwähnt, und drücken Sie dann die EINGABETASTE.  
  
4.  Die erforderlichen Aktionen werden entsprechend des angegebenen Befehls ausgeführt. Wenn Sie [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] ohne Befehlszeilenparameter installieren möchten, entsprechen die restlichen Schritte den Schritten 2 bis 6 im vorherigen Abschnitt, [Ausführen von „DQSInstaller.exe“ über den Startbildschirm, das Startmenü oder Windows-Explorer](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#WindowsExplorer).  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   Weisen Sie den Benutzern auf der Grundlage ihres Arbeitsprofils die entsprechenden DQS-Rollen zu. Siehe [Zuweisen von DQS-Rollen an Benutzer](grant-dqs-roles-to-users.md).  
  
-   Wenn Sie von einem [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] remote auf den [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]zugreifen, aktivieren Sie das TCP/IP-Protokoll mithilfe des SQL Server-Konfigurations-Managers auf diesem Computer.  
  
-   Stellen Sie sicher, dass Sie auf die Quelldaten für die DQS-Vorgänge zugreifen können, und dass Sie die verarbeiteten Daten in eine Tabelle in einer Datenbank exportieren können. Siehe [Zugriff auf Daten für DQS-Vorgänge](access-data-for-the-dqs-operations.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Install Data Quality Services](install-data-quality-services.md)   
 [Aktualisieren der SQLCLR-Assemblys nach dem Aktualisieren von .NET Framework](upgrade-sqlclr-assemblies-after-net-framework-update.md)   
 [Export and Import DQS Knowledge Bases Using DQSInstaller.exe](export-and-import-dqs-knowledge-bases-using-dqsinstaller-exe.md)  
  
  
