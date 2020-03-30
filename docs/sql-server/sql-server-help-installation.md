---
title: Hilfeinhalt und Help Viewer für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/10/2019
ms.prod: sql
ms.technology: ''
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1352a7f469e72100f7a2e0573c87cbb8422fe413
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "77608488"
---
# <a name="sql-server-offline-help-and-help-viewer"></a>Offlinehilfe und Help Viewer für SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Sie können Microsoft Help Viewer verwenden, um Hilfepakete für SQL Server von Onlinequellen oder lokalen Datenträgern herunterzuladen und zu installieren. Dann können Sie den Inhalt offline anzeigen. Help Viewer wird mit verschiedenen Tools installiert. In diesem Artikel werden die Tools beschrieben, die Help Viewer installieren. Außerdem erhalten Sie eine Anleitung zum Installieren von Hilfeinhalt, der offline verfügbar ist, und es wird beschrieben, wie Sie Hilfe abrufen.

Sie müssen mit dem Internet verbunden sein, um Help Viewer-Inhalte herunterladen zu können. Sie können die Inhalte dann auf einen Computer ohne Internetzugang migrieren.

>[!NOTE]
> Installieren Sie die aktuelle Version von SQL Server Management Studio ([SQL Server Management Studio 18.x](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)), um lokale Inhalte für die aktuelle Version von SQL Server zu erhalten.

## <a name="what-tools-install-the-help-viewer-versions"></a>Welche Tools werden zum Installieren der Help Viewer-Versionen verwendet?

Es gibt zwei Hauptversionen von Microsoft Help Viewer.  Dabei handelt es sich um Version 1.x und Version 2.x. Jede Version unterstützt verschiedene Versionen von SQL Server-Inhalten.  Das Format der offline verfügbaren Handbücher hat sich im Laufe der Zeit geändert. Ältere Versionen von Help Viewer unterstützen neuere Versionen der Handbücher nicht:

|**Version**|**Tools, die Help Viewer installieren**|**Help Viewer-Version**|
|-|-|-|
|SQL Server 2019 <br><br><br>SQL Server 2017 <br>SQL Server 2016 | [Visual Studio 2019 (\*1)](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019) <br>[SQL Server Management Studio 18.x](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) <br><br>[Visual Studio 2017 (\*1)](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2017) <br>[SQL Server Management Studio 17.x](https://docs.microsoft.com/sql/ssms/release-notes-ssms?view=sql-server-2017#1791) <br>[SQL Server Data Tools für Visual Studio 2015](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) <br>Visual Studio 2015 | v2.3 <br><br><br>v2.2 |
|SQL Server 2014<br>SQL Server 2012|SQL Server 2016-Setup (\*2)<br>SQL Server 2014 Management Studio<br>SQL Server 2014-Setup (\*2)<br>SQL Server Management Studio 2012<br>SQL Server 2012-Setup (\*2)| v1.x|
| | | |

(\*1) Um Help Viewer mit Visual Studio 2019 oder 2017 zu installieren, wählen Sie im Visual Studio-Installer auf der Registerkarte **Einzelne Komponenten** die Optionen **Codetools** \> **Help Viewer** \> **Installieren** aus.

(\*2) Gibt die Option **Dokumentationskomponenten** im SQL Server-Setup an.

>[!NOTE]
> - SQL Server 2016 installiert Help Viewer 1.1. Diese Version unterstützt allerdings nicht die Hilfe für SQL Server 2016-Inhalte. Sie benötigen Version v2.x von Help Viewer, um SQL Server 2016-Inhalte anzuzeigen. Weitere Informationen finden Sie unter [SQL Server 2016 Release Notes (Versionshinweise zu SQL Server 2016)](sql-server-2016-release-notes.md).
> - Help Viewer 2.x kann mindestens die Dokumentation für die SQL Server-Versionen 2014 – 2019 anzeigen.
> - Eine einfache Möglichkeit zum Erhalt von Help Viewer 2.3 oder höher besteht darin, zuerst die neueste Version von `SSMS.exe` herunterzuladen. Diese ist kostenlos. Verwenden Sie dann das SSMS-Menü **Hilfe**.
> - Ab SQL Server 2017 kann Help Viewer nicht mehr über das SQL Server-Setup installiert werden.

## <a name="use-help-viewer-v2x"></a>Verwenden Sie Help Viewer v2.x

Für diesen Ansatz wird Help Viewer 2.3 oder höher empfohlen. Das **Hilfe**-Menü der [neuesten Version von SSMS.exe](../ssms/download-sql-server-management-studio-ssms.md) bietet Version 2.3 oder höher.

### <a name="to-download-and-install-offline-help-content-with-help-viewer-v2x"></a>Herunterladen und Installieren von offline verfügbarem Hilfeinhalt mit Help Viewer v2.x

1. Klicken Sie in SSMS oder VS im Menü „Hilfe“auf **Hilfeinhalt hinzufügen und entfernen**. 

   ![HelpViewer2: Hinzufügen und Entfernen von Inhalt](../sql-server/media/sql-server-help-installation/addremovecontent.png)  

   Help Viewer öffnet die Registerkarte „Inhalt verwalten“.  
   
2. Wählen Sie unter „Installationsquelle“ **Online** aus, um das neuste Paket mit Hilfeinhalten zu installieren.
   
   ![HelpViewer2_ManageContent_OnlineSource](../sql-server/media/sql-server-help-installation/helpviewer2-managecontent-onlinesource.png)  
   
   >[!NOTE]
   > Wenn Sie die Installation über einen Datenträger (Hilfe für SQL Server 2014) installieren möchten, wählen Sie unter „Installationsquelle“ **Datenträger** aus, und geben Sie den Speicherort der Datenquelle an.
   
   Der lokale Speicherpfad auf der Registerkarte „Inhalt verwalten“ zeigt an, wo der Inhalt auf dem lokalen Computer installiert wird. Wenn Sie den Speicherort ändern möchten, klicken Sie auf **Verschieben**, geben Sie einen anderen Ordnerpfad im Feld **Nach** ein, und klicken Sie anschließend auf **OK**.
   Wenn die Installation der Hilfe nach dem Ändern des lokalen Speicherpfads fehlschlägt, müssen Sie Help Viewer schließen und anschließend wieder öffnen. Stellen Sie sicher, dass der neue Speicherort im lokalen Speicherpfad angezeigt wird, und versuchen Sie dann noch mal, die Installation durchzuführen.

3. Klicken Sie neben jedem Inhaltspaket (Buch), das Sie installieren möchten, auf **Hinzufügen**. 
   Fügen Sie alle 13 Bücher unter „SQL Server“ hinzu, um sämtlichen Hilfeinhalt auf SQL Server zu installieren. 
   
4. Klicken Sie im unteren rechten Bereich auf **Aktualisieren**. 
   Das Inhaltsverzeichnis der Hilfe im linken Bereich wird automatisch mit den hinzugefügten Büchern aktualisiert. 
   
   ![HelpViewer2_ManageContent_AddContent](../sql-server/media/sql-server-help-installation/helpviewer2-managecontent-addcontent.png)     
   
> [!NOTE]
> Nicht alle Titel des höchsten Knotens im Inhaltsverzeichnis von SQL Server stimmen genau mit den Namen der jeweiligen Hilfebücher überein, die heruntergeladen werden können. Die Titel im Inhaltsverzeichnis werden den Buchnamen wie folgt zugeordnet:

(*) Inhalt, der aus der ersten allgemein verfügbaren Version der Inhalte von SQL Server 2017 zusammen mit älteren Inhalten von SQL Server 2016 stammt. Diese Handbücher werden entfernt, da die separaten und vollständigen Handbücher für SQL Server 2016 und SQL Server 2017 überarbeitete Inhalte enthalten (Stand: Januar 2019).  

| | Inhaltsbereich | SQL Server-Buch |
|-----|-----|-----|
|*|Analysis Services-Sprachreferenz | Analysis Services-Sprachreferenz (MDX)|
|*|DAX-Referenz (Data Analysis Expressions) | DAX-Referenz (Data Analysis Expressions)|
|*|DMX-Referenz (Data Mining-Erweiterungen) | DMX-Referenz (Data Mining-Erweiterungen)|
|*|Erste Schritte mit Machine Learning in SQL Server | Microsoft Machine Learning Services|
|*|Referenz zu Power Query M | Referenz zu Power Query M|
||Dokumentation zu SQL Server 2016 | Dokumentation zu SQL Server 2016|
||Dokumentation zu SQL Server 2017| Dokumentation zu SQL Server 2017|
|*|Leitfäden für Entwickler für SQL Server | SQL Server Developer-Referenz|
|*|Hier können Sie SQL Server Management Studio herunterladen. | SQL Server Management Studio|
|*|Startseite für das Programmieren von Clients in Microsoft SQL Server | Treiber für die SQL Server-Verbindung|
|*|SQL Server unter Linux | SQL Server unter Linux|
|*|Technische Dokumentation zu SQL Server | Technische Dokumentation für SQL Server (SSIS, SSRS, Datenbank-Engine, Setup)|
|*|Tools und Hilfsprogramme für Azure SQL-Datenbank | SQL Server-Tools|
|*|Transact-SQL-Referenz (Datenbank-Engine) | Transact-SQL-Referenz|
|*|XQuery-Sprachreferenz (SQL Server) | XQuery-Sprachreferenz (SQL Server)|
| &nbsp; | &nbsp; | &nbsp; |

> [!NOTE]
> Wenn Help Viewer beim Hinzufügen von Inhalt nicht mehr reagieren sollte, ändern Sie die Cachezeile „LastRefreshed=\<mm/dd/yyyy> 00:00:00“ in den Dateien „%LOCALAPPDATA%\Microsoft\HelpViewer2.x\HlpViewer_SSMSx_en-US.settings“ oder „HlpViewer_VisualStudiox_en-US.settings“ in ein Datum, das in der Zukunft liegt. Weitere Informationen zu diesem Problem finden Sie unter [Visual Studio Help Viewer friert beim Begrüßungsbildschirm ein](/visualstudio/welcome-to-visual-studio).

### <a name="to-view-offline-help-content-in-ssms-with-help-viewer-v2x"></a>Anzeigen von offline verfügbarem Hilfeinhalt in SSMS mit Help Viewer v2.x

Drücken Sie STRG+ALT+F1, um die installierte Hilfe in SSMS anzuzeigen, oder wählen Sie im Menü „Hilfe“ **Hilfeinhalt hinzufügen und entfernen** aus, um Help Viewer zu starten. 

   ![HelpViewer2: Hinzufügen und Entfernen von Inhalt](../sql-server/media/sql-server-help-installation/addremovecontent.png)  

Help Viewer öffnet sich in der Registerkarte „Inhalt verwalten“ mit dem installierten Inhaltsverzeichnis für die Hilfe im linken Bereich. Klicken Sie im Inhaltsverzeichnis auf Artikel, um diese auf der rechten Seite anzuzeigen.
> [!TIP]
> Wenn der Inhaltsbereich nicht angezeigt wird, klicken Sie auf „Inhalt“ auf der linken Seite. Klicken Sie auf das Reißzweckensymbol, damit der Inhaltsbereich geöffnet bleibt.  

   ![Help Viewer v2.x mit Inhalt](../sql-server/media/sql-server-help-installation/helpviewer2-withcontentinstalled.png)

### <a name="to-view-offline-help-content-in-vs-with-help-viewer-v2x"></a>Anzeigen von offline verfügbarem Hilfeinhalt in VS mit Help Viewer v2.x

Führen Sie die folgenden Schritte aus, damit die in Visual Studio installierte Hilfe angezeigt wird:
1. Zeigen Sie im Menü „Hilfe“ auf **Hilfeeinstellungen festlegen**, und wählen Sie **In Help Viewer starten** aus. 

   ![Hilfeansicht für Visual Studio: Einstellungen für Help Viewer festlegen](../sql-server/media/sql-server-help-installation/launchviewer.png)

2. Klicken Sie im Menü „Hilfe“ auf **Hilfe anzeigen**, damit der Inhalt in Help Viewer angezeigt wird. 

   ![Hilfe anzeigen](../sql-server/media/sql-server-help-installation/viewhelp.png)

   Das Inhaltsverzeichnis der Hilfe wird auf der linken Seite und der ausgewählte Hilfsartikel auf der rechten Seite angezeigt.
  
## <a name="use-help-viewer-v1x"></a>Verwenden von Help Viewer v1.x

In diesem Abschnitt führen Sie die folgenden allgemeinen Schritte aus:

- Sie laden manuell die SQL Server 2014-Offlinedokumentation herunter, die aus vier Teilen besteht.
- Sie verwenden das **Hilfe**-Menü von SSMS oder VS, um Help Viewer zu starten.
- Zum Schluss informieren Sie Help Viewer darüber, wo sich die `*.msha`-Datei von SQL Server 2014 auf Ihrer lokalen Festplatte befindet.

Frühere Versionen von SSMS und VS haben die 1.x-Versionen von Help Viewer bereitgestellt. Version 1.x kann die Offlinedokumentation für die SQL Server-Versionen 2012 und 2014 anzeigen. Die Offlinedokumentation für SQL Server 2016 oder höher kann in Version 1.x jedoch nicht angezeigt werden.

Help Viewer 2.3 kann auch die Offlinedokumentation für SQL Server 2014 anzeigen, nachdem Sie diese auf Ihre lokale Festplatte heruntergeladen haben.

### <a name="to-download-and-install-offline-help-content-with-help-viewer-v1x"></a>Herunterladen und Installieren von offline verfügbarem Hilfeinhalt mit Help Viewer v1.x

In diesem Vorgang wird Help Viewer 1.x verwendet, um die Hilfe für SQL Server 2014 aus dem Microsoft Download Center herunterzuladen und auf dem Computer zu installieren.

1. Navigieren Sie zur Downloadwebsite [Product Documentation for Microsoft SQL Server 2014 (Produktdokumentation für Microsoft SQL Server 2014)](https://www.microsoft.com/download/details.aspx?id=42557), und klicken Sie auf **Herunterladen**.

2. Klicken Sie im Meldungsfeld auf **Speichern**, um die Datei *SQLServer2014Documentation\_\*.exe* auf Ihrem Computer zu speichern.

   > [!NOTE]
   > Speichern Sie bei firewall- und proxygeschützten Umgebungen die Downloaddatei auf einem USB-Laufwerk oder anderen Wechselmedium, auf das in der Umgebung zugegriffen werden kann.

3. Doppelklicken Sie auf die EXE-Datei, um die Datei mit Hilfeinhalten zu entpacken und in einem lokalen oder freigegebenen Ordner zu speichern.

4. Öffnen Sie den **Hilfebibliotheks-Manager**, indem Sie SSMS oder Visual Studio starten und im Menü „Hilfe“ auf **Hilfeeinstellungen verwalten** klicken.

5. Klicken Sie auf **Install content from disk** (Inhalt von Datenträger installieren), und suchen Sie nach dem Ordner, in dem Sie die Datei mit Hilfeinhalten entpackt haben.

   ![HelpLibraryManager_MainPage_InstallFromDisk](../sql-server/media/sql-server-help-installation/helplibrarymanager-mainpage-installfromdisk.png)

   ![HelpLibraryManager_InstallContentFromDisk_dialog1](../sql-server/media/sql-server-help-installation/helplibrarymanager-installcontentfromdisk-dialog1.png)

   > [!IMPORTANT]
   > Verwenden Sie im **Hilfebibliotheks-Manager** die Option **Install content from disk** (Inhalt von Datenträger installieren), um zu vermeiden, dass lokale Hilfeinhalte installiert werden, bei denen das Inhaltsverzeichnis nur teilweise vorhanden ist.  Wenn Sie **Install content from online** (Inhalt von Onlinespeicherort installieren) ausgewählt haben und Help Viewer das Inhaltsverzeichnis nur teilweise anzeigt, finden Sie in diesem [Blogbeitrag](https://blogs.msdn.microsoft.com/womeninanalytics/2016/06/21/troubleshoot-local-help-for-sql-server-2014/) Anweisungen zur Fehlerbehebung.

6. Klicken Sie nacheinander auf die Datei `HelpContentSetup.msha`, auf **Öffnen** und auf **Weiter**K.

7. Klicken Sie neben der Dokumentation, die Sie installieren möchten, auf **Hinzufügen** und dann auf **Aktualisieren**.

   ![HelpLibraryManager_InstallContentFromDisk_dialog2](../sql-server/media/sql-server-help-installation/helplibrarymanager-installcontentfromdisk-dialog2.png)

8. Klicken Sie auf **Fertig stellen** und dann auf **Beenden**.

### <a name="to-view-offline-help-content-with-help-viewer-v1x"></a>Anzeigen von offline verfügbarem Hilfeinhalt mit Help Viewer v1.x

1. Öffnen Sie erneut den **Hilfebibliotheks-Manager**, klicken Sie auf **Choose online or local help** (Onlinehilfe oder lokale Hilfe auswählen), und klicken Sie dann auf **I want to use local help** (Ich möchte lokale Hilfe verwenden).

2. Öffnen Sie den Help Viewer zum Anzeigen des Inhalts, indem Sie im Menü **Hilfe** auf **Hilfe anzeigen** klicken. Die von Ihnen installierten Inhalte werden auf der linken Seite aufgeführt.

   ![HelpViewer1_withContentInstalled_ZoomedIn](../sql-server/media/sql-server-help-installation/helpviewer1-withcontentinstalled-zoomedin.png)  

## <a name="view-online-help"></a>Anzeigen der Onlinehilfe

In der Onlinehilfe werden stets die aktuellsten Inhalte angezeigt. 

### <a name="to-view-sql-server-online-help-in-ssms-17x"></a>Anzeigen der Onlinehilfe für SQL Server in SSMS 17.x

- Klicken Sie im Menü **Hilfe** auf **Hilfe anzeigen**. Die neueste Dokumentation zu SQL Server 2016 und SQL Server 2017 von [https://docs.microsoft.com/sql/sql-server/](https://docs.microsoft.com/sql/sql-server/) wird in einem Browser angezeigt.

   ![Hilfe anzeigen](../sql-server/media/sql-server-help-installation/viewhelp.png)

### <a name="to-view-visual-studio-online-help-in-visual-studio"></a>Anzeigen der Visual Studio Onlinehilfe in Visual Studio

1. Zeigen Sie im Menü „Hilfe“ auf **Hilfeeinstellungen festlegen**, und wählen Sie entweder **In Browser starten** oder **In Help Viewer starten** aus. 
2. Klicken Sie im Menü „Hilfe“ auf **Hilfe anzeigen**. Die neuste Hilfe für Visual Studio wird in der ausgewählten Umgebung angezeigt. 

**Anzeigen der Onlinehilfe mit Help Viewer v1.x**

1. Öffnen Sie den **Hilfebibliotheks-Manager**, indem Sie im Menü „Hilfe“ auf **Hilfeeinstellungen verwalten** klicken.  
2. Klicken Sie im Dialogfeld „Hilfebibliotheks-Manager“ auf **Choose online or local help** (Onlinehilfe oder lokale Hilfe auswählen).  
   
   ![HelpLibraryManager_MainPage_ChooseOnlineORLocal.png](../sql-server/media/sql-server-help-installation/helplibrarymanager-mainpage-chooseonlineorlocal.png.png)  
   
3. Klicken Sie auf **I want to use online help** (Ich möchte Onlinehilfe verwenden), dann auf **OK** und anschließend auf **Beenden**.  
   
   ![HelpLibraryManager_ChooseOnlineORLocalHelp_OnlineHelpSelected_dialog](../sql-server/media/sql-server-help-installation/helplibrarymanager-chooseonlineorlocalhelp-onlinehelpselected-dialog.png)

4. Öffnen Sie den Help Viewer zum Anzeigen des Inhalts, indem Sie im Menü **Hilfe** auf **Hilfe anzeigen** klicken.

## <a name="view-f1-help"></a>Anzeigen der F1-Hilfe

Wenn Sie F1 drücken oder in einem Dialogfeld in SSMS oder Visual Studio auf **Hilfe** oder das Symbol **?** klicken, wird ein Artikel der kontextbezogenen Onlinehilfe im Browser oder in Help Viewer angezeigt.

### <a name="to-view-f1-help"></a>Anzeigen der F1-Hilfe

1. Klicken Sie im Menü „Hilfe“ auf **Hilfeeinstellungen festlegen**, und wählen Sie entweder **In Browser starten** oder **In Help Viewer starten** aus.
2. Drücken Sie F1, oder klicken Sie in den Dialogfeldern auf **Hilfe** oder **?** , falls verfügbar, um kontextbezogene Onlineartikel in der ausgewählten Umgebung anzuzeigen.

> [!NOTE]
> Die F1-Hilfe funktioniert nur, wenn Sie online sind. Es sind keine Offlinequellen für F1-Hilfe verfügbar.

## <a name="systems-without-internet-access"></a>Systeme ohne Internetzugang
Sobald Sie die offline verfügbaren Handbücher auf ein System mit Internetzugang heruntergeladen haben, können Sie den Inhalt mithilfe der folgenden Schritte auf ein System migrieren, das keinen Internetzugang hat.

  >[!NOTE]
  >Software, die den Help Viewer unterstützt, wie z. B. SQL Server Management Studio, muss auf dem Offlinesystem installiert sein.

1. Öffnen Sie den Help Viewer (STRG+ALT+F1).
1. Wählen Sie die Dokumentation aus, die Sie interessiert. Filtern Sie beispielsweise nach SQL Server, und wählen Sie „Technische Dokumentation zu SQL Server“ aus.
1. Bestimmen Sie den physischen Pfad der Dateien auf dem Datenträger, der unter **Lokaler Speicherpfad** zu finden ist.
1. Navigieren Sie im Dateisystem-Explorer zu diesem Speicherort.
    1.  Der Standardspeicherort lautet: `C:\Program Files (x86)\Microsoft SQL Server\140\Tools\Binn\ManagementStudio\Extensions\Application`.
1. Wählen Sie die drei Ordner **ContentStore**, **Incoming** und **IndexStore** aus, und kopieren Sie sie auf Ihrem Offlinesystem an den gleichen Speicherort. Sie müssen möglicherweise einen Wechseldatenträger wie einen USB-Stick oder eine CD verwenden.
1. Sobald diese Dateien verschoben wurden, starten Sie den Help Viewer auf dem Offlinesystem, woraufhin die technische Dokumentation zu SQL Server verfügbar ist.

![physical-location-of-offline-content.png](media/sql-server-help-installation/physical-location-of-offline-content.png)

## <a name="next-steps"></a>Nächste Schritte
[Microsoft Help Viewer – Visual Studio](/visualstudio/ide/microsoft-help-viewer)  

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
