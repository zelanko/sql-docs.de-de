---
title: Erstellen eines Wartungsplans (Entwurfsoberfläche für Wartungspläne) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Maintenance Plan Design Surface
ms.assetid: 2ef803ee-a9f8-454a-ad63-fedcbe6838d1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 78f09611e71c39902e81580d752d302fee604be9
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2019
ms.locfileid: "67584144"
---
# <a name="create-a-maintenance-plan-maintenance-plan-design-surface"></a>Erstellen eines Wartungsplans (Entwurfsoberfläche für Wartungspläne)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie für einen einzelnen Server oder mehrere Server mithilfe der Entwurfsoberfläche für Wartungspläne in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ein Wartungsplan erstellt wird. Der **Wartungsplanungs-Assistent** eignet sich am besten für das Erstellen von grundlegenden Wartungsplänen. Wenn Sie die Entwurfsoberfläche zum Erstellen eines Plans verwenden, können Sie einen erweiterten Workflow nutzen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   [Erstellen eines Wartungsplans mithilfe der Entwurfsoberfläche für Wartungspläne](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Wenn Sie einen Multiserver-Wartungsplan erstellen möchten, muss eine Multiserverumgebung mit einem Masterserver und mindestens einem Zielserver konfiguriert sein. Multiserver-Wartungspläne müssen auf dem Masterserver erstellt und verwaltet werden. Diese Pläne können auf Zielservern zwar angezeigt, jedoch nicht verwaltet werden.  
  
-   Mitglieder der **db_ssisadmin** -Rolle und **dc_admin** -Rolle können ihre Berechtigungen möglicherweise auf **sysadmin**erhöhen. Diese Ausweitung von Berechtigungen ist möglich, da diese Rollen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete ändern können. Diese Pakete können von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe des **sysadmin** -Sicherheitskontexts des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents ausgeführt werden. Konfigurieren Sie als Schutz vor dieser Ausweitung von Berechtigungen beim Ausführen von Wartungsplänen, Datensammlungssätzen und anderen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketen Aufträge des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents, die Pakete ausführen, für die Verwendung eines Proxykontos mit eingeschränkten Berechtigungen, oder fügen Sie der **db_ssisadmin** -Rolle und der **dc_admin** -Rolle nur **sysadmin** -Mitglieder hinzu.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Sie müssen Mitglied der festen Serverrolle **sysadmin** sein, um Wartungspläne erstellen oder verwalten zu können. Im Objekt-Explorer wird der **Wartungspläne** -Knoten nur für Benutzer angezeigt, die Mitglied der festen Serverrolle **sysadmin** sind.  
  
##  <a name="SSMSProcedure"></a> Verwendung der Entwurfsoberfläche für Wartungspläne  
  
#### <a name="to-create-a-maintenance-plan"></a>So erstellen Sie einen Wartungsplan  
  
1.  Klicken Sie im Objekt-Explorer auf das Pluszeichen, um den Server zu erweitern, auf dem Sie einen Wartungsplan erstellen möchten.  
  
2.  Klicken Sie auf das Pluszeichen, um den Ordner **Verwaltung** zu erweitern.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Wartungspläne** , und klicken Sie anschließend auf **Neuer Wartungsplan**.  
  
4.  Geben Sie im Dialogfeld **Neuer Wartungsplan** im Feld **Name** einen Namen für den Plan ein, und klicken Sie auf **OK**. Die Toolbox und die *maintenance_plan_name* **[Entwurf]** -Oberfläche mit dem **Unterplan_1** im Hauptraster wird angezeigt.  
  
     Die folgenden Optionen sind in der Kopfzeile des Entwurfsbereichs verfügbar.  
  
     **Unterplan hinzufügen**  
     Mit dieser Option fügen Sie einen Unterplan hinzu, den Sie konfigurieren können.  
  
     **Unterplaneigenschaften**  
     Zeigt das Dialogfeld **Unterplaneigenschaften** für den ausgewählten Unterplan im Hauptraster an. Sie können im Raster auch auf einen Unterplan doppelklicken, um das Dialogfeld **Unterplaneigenschaften** anzuzeigen. Weitere Informationen zu diesem Dialogfeld finden Sie unten.  
  
     **Ausgewählten Unterplan löschen**  
     Hiermit löschen Sie den ausgewählten Unterplan.  
  
     **Zeitplan des Unterplans**  
     Zeigt das Dialogfeld **Neuer Auftragszeitplan** für den ausgewählten Unterplan an.  
  
     **Zeitplan entfernen**  
     Mit dieser Option entfernen Sie einen Zeitplan aus dem ausgewählten Unterplan.  
  
     **Verbindungen verwalten**  
     Hiermit zeigen Sie das Dialogfeld **Verbindungen verwalten** an. Es wird verwendet, um dem Wartungsplan zusätzliche [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzverbindungen hinzuzufügen. Weitere Informationen zu diesem Dialogfeld finden Sie unten.  
  
     **Berichterstellung und Protokollierung**  
     Zeigt das Dialogfeld **Berichterstellung und Protokollierung** an. Weitere Informationen zu diesem Dialogfeld finden Sie unten.  
  
     **Server**  
     Mit dieser Option zeigen Sie das Dialogfeld **Server** an, das zum Auswählen der Server verwendet wird, auf denen die Unterplantasks ausgeführt werden. Diese Option ist nur auf Masterservern in Umgebungen mit mehreren Servern aktiviert. Weitere Informationen finden Sie unter [Erstellen einer Multiserverumgebung](../../ssms/agent/create-a-multiserver-environment.md) und [Wartungsplan &#40;Servers&#41;](../../relational-databases/maintenance-plans/maintenance-plan-servers.md).  
  
     **Name**  
     Hier zeigen Sie den Namen für den Wartungsplan an. Bei neuen Wartungsplänen wird der Name in einem Dialogfeld angegeben, bevor der Designer für den Wartungsplan geöffnet wird. Wenn Sie einen Wartungsplan umbenennen möchten, klicken Sie im Objekt-Explorer mit der rechten Maustaste auf den Plan, und klicken Sie anschließend auf **Umbenennen**.  
  
     **Beschreibung**  
     Hier können Sie eine Beschreibung für den Wartungsplan anzeigen oder festlegen. Die maximale Länge für eine Beschreibung beträgt 512 Zeichen.  
  
     **Designeroberfläche**  
     Hiermit können Sie Wartungspläne entwerfen und verwalten. Verwenden Sie die Designeroberfläche, um einem Plan Wartungspläne hinzuzufügen, Tasks aus einem Plan zu entfernen, Rangfolgenlinks zwischen den Tasks anzugeben oder Taskverzweigungen und -parallelausführungen anzuzeigen.  
  
     Ein Rangfolgenlink zwischen zwei Tasks legt eine Beziehung zwischen den Tasks fest. Der zweite Task (der *abhängige Task*) wird nur ausgeführt, wenn das Ausführungsergebnis des ersten Tasks (des *Vorgängertasks*) bestimmte Kriterien erfüllt. Normalerweise ist das angegebene Ausführungsergebnis **Erfolg**, **Fehler**oder **Beendigung**. Weitere Informationen finden Sie unter Schritt **8** .  
  
5.  Doppelklicken Sie in der Kopfzeile des Entwurfsbereichs auf **Unterplan_1** , und geben Sie im Dialogfeld **Unterplaneigenschaften** einen Namen sowie eine Beschreibung für den Unterplan ein.  
  
     Die folgenden Optionen sind im Dialogfeld **Unterplaneigenschaften** verfügbar.  
  
     **Name**  
     Der Name des Unterplans.  
  
     **Beschreibung**  
     Kurze Beschreibung des Unterplans.  
  
     **Zeitplan**  
     Gibt an, nach welchem Zeitplan der Unterplan ausgeführt wird. Klicken Sie auf **Zeitplan des Unterplans** , um das Dialogfeld **Neuer Auftragszeitplan** zu öffnen. Klicken Sie auf **Zeitplan entfernen** , um den Zeitplan aus dem Unterplan zu löschen.  
  
     Liste**Ausführen als**  
     Wählen Sie das Konto aus, das zum Ausführen dieser Unteraufgabe verwendet werden soll.  
  
6.  Klicken Sie auf **Zeitplan des Unterplans** , um die Details zum Zeitplan in das Dialogfeld **Neuer Auftragszeitplan** einzugeben.  
  
7.  Um den Unterplan zu erstellen, ziehen Sie die Tasksteuerungselemente aus der **Toolbox** auf die Planentwurfsoberfläche. Doppelklicken Sie auf Tasks, um Dialogfelder zum Konfigurieren der Taskoptionen zu öffnen.  
  
     Die folgenden Wartungsplantasks sind in der **Toolbox**verfügbar:  
  
    -   **Datenbank sichern (Task)**  
  
    -   **Datenbankintegrität überprüfen (Task)**  
  
    -   **Auftrag des SQL Server-Agents ausführen (Task)**  
  
    -   **T-SQL-Anweisung ausführen (Task)**  
  
    -   **Verlaufscleanup (Task)**  
  
    -   **Wartungscleanup (Task)**  
  
    -   **Operator benachrichtigen (Task)**  
  
    -   **Index neu erstellen (Task)**  
  
    -   **Index neu organisieren (Task)**  
  
    -   **Datenbank verkleinern (Task)**  
  
    -   **Statistiken aktualisieren (Task)**  
  
     So fügen Sie der **Toolbox**Tasks hinzu:  
  
    1.  Klicken Sie im Menü **Extras** auf **Toolboxelemente auswählen**.  
  
    2.  Wählen Sie die Tools aus, die in der **Toolbox**angezeigt werden sollen, und klicken Sie dann auf **OK**.  
  
     Wenn Wartungsplantasks der **Toolbox** hinzugefügt werden, sind diese auch im **Wartungsplanungs-Assistenten**verfügbar. Weitere Informationen zu den einzelnen Tasks finden Sie unter [Verwenden des Wartungsplanungs-Assistenten](../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure) im Abschnitt **So starten Sie den Wartungsplanungs-Assistenten**.  
  
8.  So definieren Sie einen Workflow zwischen Tasks:  
  
    1.  Klicken Sie mit der rechten Maustaste auf den Vorgängertask, und wählen Sie **Rangfolgeneinschränkung hinzufügen**aus.  
  
    2.  Wählen Sie im Dialogfeld **Ablaufsteuerung** in der Liste **Zu** den abhängigen Task aus, und klicken Sie auf **OK**.  
  
    3.  Doppelklicken Sie auf den Konnektor zwischen den beiden Tasks, um das Dialogfeld **Rangfolgeneinschränkungs-Editor** zu öffnen.  
  
         Die folgenden Optionen sind im Dialogfeld **Rangfolgeneinschränkungs-Editor** verfügbar.  
  
         **Einschränkungsoption**  
         Definiert, wie eine Einschränkung zwischen zwei Tasks angewendet wird.  
  
         Liste**Auswertungsvorgang**  
         Geben Sie den Auswertungsvorgang an, den die Rangfolgeneinschränkung verwendet. Folgende Vorgänge sind möglich: **Einschränkung**, **Ausdruck**, **Ausdruck und Einschränkung**und **Ausdruck oder Einschränkung**.  
  
         Liste**Wert**  
         Geben Sie den Einschränkungswert an: **Erfolg**, **Fehler**oder **Beendigung**. **Erfolg** ist die Standardeinstellung.  
  
        > [!NOTE]  
        >  Die Rangfolgeneinschränkungszeile wird für **Erfolg**grün, für **Fehler**rot und für **Beendigung**blau angezeigt.  
  
         **Ausdruck**  
         Geben Sie, wenn Sie die Vorgänge **Ausdruck**, **Ausdruck und Einschränkung**oder **Ausdruck oder Einschränkung**verwenden, einen Ausdruck ein. Der Ausdruck muss zu einem booleschen Wert ausgewertet werden.  
  
         **Testen**  
         Überprüfen Sie den Ausdruck.  
  
         **Mehrere Einschränkungen**  
         Definieren Sie, wie mehrere Einschränkungen zusammenwirken, um die Ausführung des eingeschränkten Tasks zu steuern.  
  
         **Logisches AND**  
         Damit geben Sie an, dass für die ausführbare Datei mehrere Rangfolgeneinschränkungen gemeinsam überprüft werden müssen. Sämtliche Einschränkungen müssen bei der Auswertung True ergeben. Diese Option ist die Standardeinstellung.  
  
        > [!NOTE]  
        >  Dieser Typ der Rangfolgeneinschränkung wird als durchgehende grüne, rote oder blaue Linie dargestellt.  
  
         **Logisches OR**  
         Damit geben Sie an, dass für die ausführbare Datei mehrere Rangfolgeneinschränkungen gemeinsam überprüft werden müssen. Mindestens eine Einschränkung muss mit True ausgewertet werden.  
  
        > [!NOTE]  
        >  Dieser Typ der Rangfolgeneinschränkung wird als gestrichelte grüne, rote oder blaue Linie dargestellt.  
  
9. Um einen anderen Unterplan mit Tasks hinzuzufügen, die unter einem anderen Zeitplan ausgeführt werden, klicken Sie in der Symbolleiste auf **Unterplan hinzufügen** , um das Dialogfeld **Unterplaneigenschaften** zu öffnen.  
  
10. So fügen Sie Verbindungen zu anderen Servern hinzu:  
  
    1.  Klicken Sie in der Symbolleiste des Entwurfsbereichs auf **Verbindungen verwalten**.  
  
    2.  Klicken Sie im Dialogfeld **Verbindungen verwalten** auf **Hinzufügen**.  
  
    3.  Geben Sie im Dialogfeld **Verbindungseigenschaften** im Feld **Verbindungsname** den Namen der Verbindung ein, die Sie erstellen.  
  
    4.  Geben Sie unter **Geben Sie Folgendes für die Verbindung mit SQL Server-Daten an** im Feld **Wählen Sie einen Servernamen aus, oder geben Sie ihn ein** entweder den Namen des SQL-Servers ein, den Sie verwenden möchten, oder klicken Sie auf die Auslassungspunkte **(…)** , und wählen Sie im Dialogfeld **SQL Server** einen Server aus. Wenn Sie im Dialogfeld **SQL Server** einen Server auswählen, klicken Sie auf **OK**.  
  
    5.  Wählen Sie unter **Geben Sie Informationen zum Anmelden am Server ein**die Option **Integrierte Sicherheit von Windows NT verwenden** oder **SQL Server-Authentifizierung verwenden**aus. Wenn Sie sich für die Verwendung der SQL Server-Authentifizierung entscheiden, geben Sie die entsprechenden Informationen in die Felder **Benutzername** und **Kennwort** ein.  
  
    6.  Klicken Sie im Dialogfeld **Verbindungseigenschaften** auf **OK**.  
  
    7.  Klicken Sie im Dialogfeld **Verbindungen verwalten** auf **Schließen**.  
  
11. So geben Sie Berichtsoptionen an:  
  
    1.  Klicken Sie in der Symbolleiste des Entwurfsbereichs auf **Berichterstellung und Protokollierung**.  
  
    2.  Aktivieren Sie im Dialogfeld **Berichterstellung und Protokollierung** unter **Berichterstellung**die Option **Textdateibericht generieren** oder **Bericht an einen E-Mail-Empfänger senden** oder beide Optionen.  
  
        1.  Wenn Sie **Textdateibericht generieren**auswählen, können Sie entweder **Neue Datei erstellen** oder **An Datei anfügen**auswählen.  
  
        2.  Geben Sie je nach Ihrer Auswahl den Namen und vollständigen Pfad der neuen Datei oder der anzufügenden Datei ein, indem Sie die Informationen im Feld **Ordner** bzw. **Dateiname** angeben. Alternativ dazu können Sie auf die Auslassungspunkte **(…)** klicken und den Pfad zum Ordner oder den Dateinamen in den Dialogfeldern **Ordner suchen –** _server\_name_ oder **Datenbankdateien suchen –** _server\_name_ auswählen.  
  
        3.  Wenn Sie in der Liste **Agentoperator**die Option **Bericht an einen E-Mail-Empfänger senden** auswählen, können Sie den Empfänger des per E-Mail gesendeten Berichts angeben.  
  
            > [!NOTE]  
            >  Der SQL Server-Agent muss für die Verwendung von Datenbank-E-Mail konfiguriert werden, um E-Mails senden zu können. Weitere Informationen finden Sie unter [Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  Wählen Sie zum Speichern detaillierter Informationen unter **Protokollierung**die Option **Erweiterte Informationen protokollieren**aus.  
  
    4.  Wählen Sie zum Schreiben von Informationen zu Wartungsplanergebnissen auf einen anderen Server die Option **Auf Remoteserver protokollieren** , und wählen Sie entweder eine Serververbindung aus der Liste **Verbindung** aus, oder klicken Sie auf **Neu** , und geben Sie die Verbindungsinformationen im Dialogfeld **Verbindungseigenschaften** ein.  
  
    5.  Klicken Sie im Dialogfeld **Berichterstellung und Protokollierung** auf **OK**.  
  
12. Wenn Sie die Ergebnisse im Protokolldatei-Viewer anzeigen möchten, klicken Sie im **Objekt-Explorer**mit der rechten Maustaste entweder auf den Ordner **Wartungspläne** oder auf einen bestimmten Wartungsplan, und klicken Sie dann auf **Verlauf anzeigen**.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     The following options are available on the **Log File Viewer -**_server\_name_ dialog box.  
  
     **Load Log**  
     Open a dialog box where you can specify a log file to load.  
  
     **Export**  
     Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.  
  
     **Refresh**  
     Refresh the view of the selected logs. The **Refresh** button rereads the selected logs from the target server while applying any filter settings.  
  
     **Filter**  
     Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.  
  
     **Search**  
     Search the log file for specific text. Searching with wildcard characters is not supported.  
  
     **Stop**  
     Stops loading the log file entries. For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.  
  
     **Log file summary**  
     This information panel displays a summary of the log file filtering. If the file is not filtered, you will see the following text, **No filter applied**. If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.  
  
     **Date**  
     Displays the date of the event.  
  
     **Source**  
     Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example). This does not appear for all log types.  
  
     **Message**  
     Displays any messages associated with the event.  
  
     **Log Type**  
     Displays the type of log to which the event belongs. All selected logs appear in the log file summary window.  
  
     **Log Source**  
     Displays a description of the source log in which the event is captured.  
  
     **Selected row details**  
     Select a row to display additional details about the selected event row at the bottom of the page. The columns can be reordered by dragging them to new locations in the grid. The columns can be resized by dragging the column separator bars in the grid header to the left or right. Double-click the column separator bars in the grid header to automatically size the column to the content width.  
  
     **Instance**  
     The name of the instance on which the event occurred. This is displayed as *computer name*\\*instance name*.  
  
  
