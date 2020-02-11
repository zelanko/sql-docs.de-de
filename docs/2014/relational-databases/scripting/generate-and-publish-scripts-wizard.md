---
title: Assistenten zum Generieren und Veröffentlichen von Skripts
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.generatescriptswizard.setscriptingoptions.f1
- sql9.swb.generatescriptswizard.scriptwizarddescription.f1
- sql12.swb.generatescriptswizard.saveorpublishscripts.f1
- sql9.swb.generatescriptswizard.selectdatabase.f1
- sql9.swb.generatescriptswizard.scriptfileoption.f1
- sql12.swb.generatescriptswizard.advancedscriptingoptions.f1
- sql9.swb.generatescriptswizard.choosescriptoptions.f1
- sql12.swb.generatescriptswizard.summarypage.f1
- sql9.swb.generatescriptswizard.chooseviews.f1
- sql12.swb.generatescriptswizard.providerconfiguration.f1
- sql9.swb.generatescriptswizard.choosestoredprocedures.f1
- sql9.swb.generatescriptswizard.chooseobjecttypes.f1
- sql9.swb.generatescriptswizard.welcome.f1
- sql9.swb.generatescriptswizard.chooseudf.f1
- sql12.swb.generatescriptswizard.manageproviders.f1
- sql9.swb.generatescriptswizard.chooseuddt.f1
- sql12.swb.generatescriptswizard.advancedpublishingoptions.f1
- sql12.swb.generatescriptswizard.introduction.f1
- sql9.swb.generatescriptswizard.chooserules.f1
- sql12.swb.generatescriptswizard.chooseobjects.f1
- sql9.swb.generatescriptswizard.progress.f1
- sql9.swb.generatescriptswizard.choosedefaults.f1
- sql9.swb.generatescriptswizard.chooseobjects.f1
- sql9.swb.generatescriptswizard.choosetables.f1
helpviewer_keywords:
- databases [SQL Server], publishing
- publishing databases
- scripts [SQL Server], generating
- scripts [SQL Server], publishing
- databases [SQL Server], generating scripts
- Publish Database Wizard
ms.assetid: 5ee520ba-ec7e-4199-a441-189e9e264b37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47bf324dd757661a6f49f18b28f810c87ca1419e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75242110"
---
# <a name="generate-and-publish-scripts-wizard"></a>Assistenten zum Generieren und Veröffentlichen von Skripts
  Sie können mit dem **Assistenten zum Generieren und Veröffentlichen von Skripts** Skripts zur Übertragung einer Datenbank zwischen Instanzen von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] oder [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]erstellen. Sie können Skripts für eine Datenbank auf einer Datenbank-Engine-Instanz im lokalen Netzwerk oder von [!INCLUDE[ssSDS](../../includes/sssds-md.md)] aus generieren. Die generierten Skripts können auf einer anderen Datenbank-Engine-Instanz oder von [!INCLUDE[ssSDS](../../includes/sssds-md.md)] aus ausgeführt werden. Sie können den Assistenten außerdem dazu verwenden, den Inhalt einer Datenbank direkt in einem Webdienst zu veröffentlichen, der mit den Datenbank-Veröffentlichungsdiensten erstellt wurde. Sie können Skripts für eine gesamte Datenbank oder für eine Auswahl bestimmter Objekte erstellen.  
  
1.  Vorbereitungen **:**[Veröffentlichen in einem gehosteten Dienst](#PubHostSvc), [Berechtigungen](#Permissions)    
  
2.  **Generieren oder Veröffentlichen eines Skripts mit:**[dem Assistenten zum Generieren und veröffentlichen](#GenPubScriptWiz) von Skripts    
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Die Quell- und Zieldatenbank können sich auf [!INCLUDE[ssSDS](../../includes/sssds-md.md)]oder einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] befinden, die mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher ausgeführt wird.  
  
###  <a name="PubHostSvc"></a>Veröffentlichen in einem gehosteten Dienst  
 Der **Assistent zum Generieren und Veröffentlichen von Skripts** kann nicht nur zum Erstellen von Skripts, sondern auch zum Veröffentlichen einer Datenbank in einem bestimmten gehosteten SQL Server-Webdienst verwendet werden. Das SQL Server Hosting Toolkit stellt auf der CodePlex-Website Datenbank-Veröffentlichungsdienste als freigegebenes Quellprojekt zur Verfügung. Das Projekt für Datenbank-Veröffentlichungsdienste kann von Webhostinganbietern zum Erstellen einer Gruppe von Webdiensten verwendet werden, mit denen deren Kunden Datenbanken problemlos für den Webdienst bereitstellen können. Weitere Informationen zum Herunterladen des SQL Server Hosting Toolkits finden Sie unter [SQL Server Database Publishing Services](https://go.microsoft.com/fwlink/?LinkId=142025).  
  
 Aktivieren Sie zum Veröffentlichen einer Datenbank in einem Webhostingdienst auf der Seite **Skripterstellungsoptionen festlegen** des Assistenten die Option **In Webdienst veröffentlichen** .  
  
###  <a name="Permissions"></a> Berechtigungen  
 Zum Veröffentlichen einer Datenbank ist mindestens die Mitgliedschaft in der festen Datenbankrolle db_ddladmin in der Ursprungsdatenbank erforderlich. Zum Veröffentlichen eines Datenbankskripts in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem Hostinganbieter ist mindestens die Mitgliedschaft in der festen Datenbankrolle db_ddladmin auf der Zieldatenbank erforderlich.  
  
 Außerdem muss bei der Veröffentlichung mit dem Assistenten ein Benutzername mit zugehörigem Kennwort für den Zugriff auf das Konto beim Hostinganbieter angegeben werden. Die Zieldatenbank muss auf dem Hostinganbieter erstellt werden, bevor die Quelldatenbank veröffentlicht wird. Durch die Veröffentlichung werden Objekte in der bestehenden Datenbank überschrieben.  
  
##  <a name="GenPubScriptWiz"></a>Verwenden des Assistenten zum Generieren und Veröffentlichen von Skripts  
 **So generieren Sie ein Skript zum Veröffentlichen**  
  
1.  Erweitern Sie im **Objekt-Explorer**den Knoten für die Instanz, die die Datenbank enthält, für die ein Skript erstellt werden soll.  
  
2.  Zeigen Sie auf **Tasks**, und klicken Sie anschließend auf **Skripts generieren**.  
  
3.  Bearbeiten Sie die Dialogfenster des Assistenten:  
  
    -   [Seite "Einführung"](#Introduction)  
  
    -   [Seite "Objekte auswählen"](#ChooseObjects)  
  
    -   [Seite "Skripterstellungsoptionen festlegen"](#SetScriptOpt)  
  
    -   [Seite "Erweiterte Skripterstellungsoptionen"](#AdvScriptOpt)  
  
    -   [Seite "Anbieter verwalten"](#MgProviders)  
  
    -   [Seite "Erweiterte Veröffentlichungsoptionen"](#AdvPubOpts)  
  
    -   [Seite "Anbieterkonfiguration"](#ProvConfig)  
  
    -   [Seite "Zusammenfassung"](#Summary)  
  
    -   [Seite "Skripts speichern oder veröffentlichen"](#SavePubScripts)  
  
###  <a name="Introduction"></a> Seite "Einführung"  
 Auf dieser Seite werden die Schritte zum Generieren oder Veröffentlichen eines Skripts beschrieben.  
  
 **Diese Seite nicht mehr anzeigen** – Diese Seite wird beim nächsten Starten des **Assistenten zum Generieren und Veröffentlichen von Skripts**übersprungen.  
  
 **Nächste >** : geht zur Seite **Methode auswählen** über.  
  
 **Abbrechen** : beendet den Assistenten, ohne ein Skript aus der Datenbank zu erstellen oder zu veröffentlichen.  
  
###  <a name="ChooseObjects"></a>Seite "Objekte auswählen"  
 Wählen Sie auf dieser Seite aus, welche Objekte in die von diesem Assistenten generierten Skripts eingeschlossen werden sollen. Auf der folgenden Seite des Assistenten können Sie diese Skripts am Speicherort Ihrer Wahl speichern oder sie verwenden, um Datenbankobjekte an einen Remotewebhostinganbieter zu veröffentlichen, bei dem die [SQL Server-Datenbank-Veröffentlichungsdienste](https://go.microsoft.com/fwlink/?LinkId=142025)installiert sind.  
  
 **Skripterstellung für gesamte Datenbank** : Klicken Sie auf diese Option, um Skripts für alle Objekte in der Datenbank zu generieren und ein Skript für die Datenbank selbst einzuschließen.  
  
 **Bestimmte Datenbankobjekte auswählen** – Klicken Sie hier, um den Assistenten auf die Generierung von Skripts für von Ihnen ausgewählte Objekte in der Datenbank einzuschränken:  
  
-   **Datenbankobjekte** – Wählen Sie mindestens ein Objekt aus, das ins Skript eingeschlossen werden soll.  
  
-   **Alles auswählen** – Aktiviert alle verfügbaren Kontrollkästchen.  
  
-   **Auswahl aufheben** – Deaktiviert alle Kontrollkästchen. Sie müssen in diesem Fall mindestens ein Datenbankobjekt auswählen, um den Vorgang fortsetzen zu können.  
  
###  <a name="SetScriptOpt"></a>Seite "Skript Optionen festlegen"  
 Auf dieser Seite können Sie angeben, ob Skripts vom Assistenten am ausgewählten Speicherort gespeichert werden, oder ob damit Datenbankobjekte bei einem Remotewebhostinganbieter veröffentlicht werden. Für die Veröffentlichung müssen Sie Zugriff auf einen Webdienst haben, der mithilfe des Webdiensts "Datenbank-Veröffentlichungsdienste" installiert wird.  
  
 **Optionen** : Wenn Sie möchten, dass der Assistent Skripts an einem Speicherort Ihrer Wahl speichert, wählen Sie **Skripts an einem bestimmten Speicherort speichern**aus. Sie können die Skripts später für eine Datenbank-Engine-Instanz oder für [!INCLUDE[ssSDS](../../includes/sssds-md.md)]ausführen. Wenn der Assistent die Datenbankobjekte in einem Remote-Webhostinganbieter veröffentlichen soll, wählen Sie **In Webdienst veröffentlichen**aus.  
  
 **Skripts an einem bestimmten Speicherort speichern** : Speichern Sie mindestens einen Speicherort. Transact-SQL-Skriptdateien an einen von Ihnen angegebenen Speicherort.  
  
-   **Erweitert** : zeigt das Dialogfeld **Erweiterte Skript** Erstellungs Optionen an, in dem Sie erweiterte Optionen zum Erstellen von Skripts auswählen können.  
  
-   **In Datei speichern** : Speichern Sie das Skript in einer oder mehreren SQL-Dateien. Klicken Sie auf die Schaltfläche zum Durchsuchen (**…**), um Namen und Speicherort für die Datei anzugeben. Aktivieren Sie das Kontrollkästchen **Vorhandene Datei überschreiben** , um die Datei zu ersetzen, wenn bereits eine Datei mit dem gleichen Namen vorhanden ist. Klicken Sie auf **Einzelne Datei** oder **Einzelne Datei pro Objekt** , um anzugeben, wie die Skripts generiert werden sollen. Klicken Sie auf **Unicode-Text** oder **ANSI-Text** , um die Art von Text anzugeben, die im Skript verwendet werden soll.  
  
-   **In Zwischenablage speichern** : speichert das Transact-SQL-Skript in der Zwischenablage.  
  
-   **In neuem Abfragefenster speichern** : generiert das Skript in einem Datenbank-Engine-Abfrage-Editor-Fenster. Wenn kein Editor-Fenster geöffnet ist, wird ein neues Editor-Fenster als Skriptziel geöffnet.  
  
 **In Webdienst veröffentlichen** : veröffentlichen Sie die ausgewählten Objekte in einem remotewebhostingdienst, für den Sie einen Anbieter konfiguriert haben.  
  
-   **Anbieter verwalten** : zeigt das Dialogfeld **Anbieter verwalten** an. Verwenden Sie das Dialogfeld **Anbieter verwalten** , um Hostinganbieter hinzuzufügen, zu bearbeiten und zu löschen. Jeder Anbieter gibt die Verbindungsinformationen zu einem Webhostingdienst und zu den Zieldatenbanken für diesen Dienst an.  
  
-   **Erweitert** : zeigt das Dialogfeld **Erweiterte Veröffentlichungs Optionen** an, in dem Sie erweiterte Optionen zum Veröffentlichen von Skripts auswählen können.  
  
-   **Anbieter** : Wählen Sie den Anbieter aus, der die Verbindungsinformationen für den Webhostingdienst angibt, der die Datenbank hostet, in der Sie die ausgewählten Objekte veröffentlichen möchten. Zur Auswahl eines Anbieters muss mindestens ein Anbieter im Dialogfeld **Anbieter verwalten** verfügbar sein.  
  
-   **Zieldatenbank** : Wählen Sie die Zieldatenbank aus, in der Sie die ausgewählten Objekte veröffentlichen möchten. Sie müssen vor dem Auswählen einer Zieldatenbank einen Anbieter auswählen.  
  
###  <a name="AdvScriptOpt"></a>Seite "Erweiterte Skript Optionen"  
 Verwenden Sie diese Seite, um festzulegen, wie dieser Assistent Skripts generieren soll. Es sind viele verschiedene Optionen verfügbar. Die Optionen werden abgeblendet dargestellt, wenn sie von der SQL Server- oder [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Version, die in **Datenbank-Engine-Typ** angegeben ist, nicht unterstützt werden.  
  
 **Optionen** : Geben Sie erweiterte Optionen an, indem Sie einen Wert aus der Liste der verfügbaren Einstellungen rechts neben den einzelnen Optionen auswählen.  
  
 **Allgemein** : die folgenden Optionen gelten für das gesamte Skript.  
  
-   **ANSI Padding** : schließt `ANSI PADDING ON` im Skript ein. Der Standardwert ist " **true**".  
  
-   **An Datei anfügen** : Wenn **true**, wird dieses Skript am Ende eines vorhandenen Skripts hinzugefügt, das auf der Seite Skript Erstellungs **Optionen festlegen** angegeben ist. Im Falle von **False**überschreibt das neue Skript ein vorheriges Skript. Der Standardwert ist **False**.  
  
-   **Skripterstellung bei Fehler fortsetzen** : Wenn **true**, wird die Skripterstellung beendet, wenn ein Fehler auftritt. Im Falle von **False**wird die Skripterstellung fortgesetzt. Der Standardwert ist **False**.  
  
-   **UDDTs in Basis Typen konvertieren** : Wenn **true**, werden benutzerdefinierte Datentypen (UDDT) in die zugrunde liegenden Basis Datentypen konvertiert, die für die Erstellung verwendet wurden. Verwenden Sie **True** , wenn der UDDT in der Datenbank, in der das Skript ausgeführt wird, nicht vorhanden ist. Im Falle von **False**werden UDDTs verwendet. Der Standardwert ist **False**.  
  
-   **Skript für abhängige Objekte generieren** : generiert ein Skript für jedes Objekt, das vorhanden sein muss, wenn das Skript für das ausgewählte Objekt ausgeführt wird. Der Standardwert ist " **true**".  
  
-   **Beschreibende Header einschließen** : beim Wert " **true**" werden dem Skript beschreibende Kommentare hinzugefügt, die das Skript in Abschnitte für die einzelnen Objekte aufteilen. Der Standardwert ist **False**.  
  
-   **Include include, wenn nicht vorhanden** : Wenn **true**, enthält das Skript eine Anweisung, um zu überprüfen, ob das Objekt bereits in der Datenbank vorhanden ist, und versucht nicht, ein neues Objekt zu erstellen, wenn das Objekt bereits vorhanden ist. Der Standardwert ist **False**.  
  
-   **System Einschränkungs Namen einschließen** : bei **false**wird der Standardwert von Einschränkungen, die automatisch in der Ursprungs Datenbank benannt wurden, in der Zieldatenbank automatisch umbenannt. Im Falle von **True**haben Einschränkungen in der Ursprungs- und der Zieldatenbank den gleichen Namen.  
  
-   **Nicht unterstützte Anweisungen einschließen** : bei **false**enthält das Skript keine Anweisungen für Objekte, die für die ausgewählte Server Version bzw. den ausgewählten Engine-Typ nicht unterstützt werden. Bei **True**enthält das Skript nicht unterstützte Objekte. Jede Anweisung für ein nicht unterstütztes Objekt enthält einen Kommentar, dass die Anweisung bearbeitet werden muss, bevor das Skript für die ausgewählte SQL Server-Version bzw. den ausgewählten Engine-Typ ausgeführt werden kann. Der Standardwert ist **False**.  
  
-   **Objektnamen für Schema qualifiziere** : schließt den Schema Namen im Namen der erstellten Objekte ein. Der Standardwert ist " **true**".  
  
-   **Skript Bindung** : generiert ein Skript zum Binden von Standard-und Regel Objekten. Der Standardwert ist **False**. Weitere Informationen finden Sie unter [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql) und [CREATE RULE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-rule-transact-sql).  
  
-   **Skript Sortierung** : schließt Sortierungs Informationen in das Skript ein. Der Standardwert ist **False**. Weitere Informationen finden Sie unter [Collation and Unicode Support](../collations/collation-and-unicode-support.md).  
  
-   **Skript** Erstellung für Standard-schließt Standardobjekte ein, die zum Festlegen von Standardwerten in Tabellen Spalten verwendet werden. Der Standardwert ist " **true**". Weitere Informationen finden Sie unter [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql).  
  
-   **Script Drop und Create** : Wenn **Script erstellt**wird [!INCLUDE[tsql](../../../includes/tsql-md.md)] , werden-Anweisungen zum Erstellen von-Objekten eingeschlossen. Beim **ablegen von Skripts**werden [!INCLUDE[tsql](../../../includes/tsql-md.md)] Anweisungen zum Ablegen von Objekten eingeschlossen. Wenn **DROP und CREATE als Skript**ausgewählt ist, ist die [!INCLUDE[tsql](../../../includes/tsql-md.md)] -DROP-Anweisung im Skript für jedes geschriebene Objekt enthalten, gefolgt von der CREATE-Anweisung. Der Standardwert ist **CREATE als Skript**.  
  
-   **Skripterstellung für erweiterte Eigenschaften** : schließt erweiterte Eigenschaften in das Skript ein, wenn das Objekt über erweiterte Eigenschaften verfügt. Der Standardwert ist " **true**".  
  
-   **Skripterstellung für Engine-Typ** : erstellt ein Skript, das für den ausgewählten Typ von [!INCLUDE[ssSDS](../../includes/sssds-md.md)] oder eine Instanz des SQL Server Datenbank-Engine ausgeführt werden kann. Für den angegebenen Typ nicht unterstützte Objekte werden nicht in das Skript eingeschlossen. Der Standardwert ist der Typ des Ursprungsservers.  
  
-   **Skripterstellung für Server Version** : erstellt ein Skript, das für die ausgewählte Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt werden kann. Neue Funktionen in einer Version können für eine Skripterstellung für frühere Versionen nicht verwendet werden. Der Standard ist die Version des Ursprungsservers.  
  
-   **Skript** Erstellung für Anmeldungen: Wenn das Objekt, für das ein Skript erstellt werden soll, ein Datenbankbenutzer ist, werden mit dieser Option die Anmeldungen erstellt, von denen der Benutzer abhängig ist. Der Standardwert ist **False**.  
  
-   **Skripterstellung für Berechtigungen auf Objektebene: schließt Skripts** ein, um die Berechtigung für die Objekte in der Datenbank festzulegen. Der Standardwert ist **False**.  
  
-   **Skript** Erstellung für Statistiken: Wenn **Skript**Erstellung für Statistiken festgelegt ist `CREATE STATISTICS` , schließt diese Option die-Anweisung zum erneuten Erstellen der Statistiken für das Objekt ein. Mit der Option **Skripterstellung für Statistiken und Histogramme** können auch Histogramminformationen erstellt werden. Der Standardwert ist **Keine Skripterstellung für Statistiken**. Weitere Informationen finden Sie unter [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
-   **Skripterstellung für use Database** : `USE DATABASE` fügt dem Skript die-Anweisung hinzu. Die `USE DATABASE`-Anweisung muss enthalten sein, um sicherzustellen, dass Datenbankobjekte in der richtigen Datenbank erstellt werden. Wenn das Skript in einer anderen Datenbank verwendet werden soll, wählen Sie **false** aus, um die `USE DATABASE` -Anweisung auszulassen. Der Standardwert ist " **true**". Weitere Informationen finden Sie unter [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).  
  
-   **Datentypen, für die ein Skript** erstellt werden soll: wählt aus, wofür ein Skript erstellt werden soll: **nur Daten**, nur **Schema**oder beides. Der Standard ist **Nur Schema**.  
  
 **Tabellen** -/sichtsoptionen: die folgenden Optionen gelten nur für Skripts für Tabellen oder Sichten.  
  
-   **Skript** Erstellung für Änderungs Nachverfolgung: Skript Änderungs Nachverfolgung, wenn Sie in der Ursprungs Datenbank oder in den Tabellen in der Ursprungs Datenbank aktiviert ist. Der Standardwert ist **False**. Weitere Informationen finden Sie unter [Informationen zur Änderungsnachverfolgung &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md).  
  
-   **Skript** Erstellung für Check- `CHECK` Einschränkungen: fügt Einschränkungen zum Skript hinzu. Der Standardwert ist " **true**". Für `CHECK`-Einschränkungen ist es erforderlich, dass Daten, die in eine Tabelle eingegeben werden, eine angegebene Bedingung erfüllen. Weitere Informationen finden Sie unter [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).  
  
-   **Skripterstellung für Daten Komprimierungs Optionen: Skript** Erstellung für Daten Komprimierungs Optionen, wenn Sie in der Ursprungs Datenbank oder in den Tabellen in der Ursprungs Datenbank konfiguriert sind. Weitere Informationen finden Sie unter [Data Compression](../data-compression/data-compression.md). Der Standardwert ist **False**.  
  
-   **Skripterstellung für Fremdschlüssel** : Fügt dem Skript Fremdschlüssel hinzu. Der Standardwert ist " **true**". Mit Fremdschlüsseln können Beziehungen zwischen Tabellen angezeigt und erzwungen werden.  
  
-   **Skripterstellung für Volltextindizes: Skripts** für die Erstellung von Volltextindizes. Der Standardwert ist **False**.  
  
-   **Skripterstellung für Indizes: Skripts** für die Erstellung von Indizes. Der Standardwert ist " **true**". Mit Indizes können Sie Daten schneller finden.  
  
-   **Skripterstellung für Primärschlüssel: Skript** Erstellung für Primärschlüssel in Tabellen. Der Standardwert ist " **true**". Mit Primärschlüsseln kann jede Zeile einer Tabelle eindeutig identifiziert werden.  
  
-   **Skripterstellung für Trigger: Skripts** für die Erstellung von DML-Triggern in Tabellen. Der Standardwert ist **False**. Ein DML-Trigger ist eine Aktion, die so programmiert ist, dass sie bei Auftreten eines DML-Ereignisses (Data Manipulation Language, Datenbearbeitungssprache) auf dem Datenbankserver ausgeführt wird. Weitere Informationen finden Sie unter [DML Triggers](../triggers/dml-triggers.md).  
  
-   **Skripterstellung für eindeutige Schlüssel: Skript** Erstellung für eindeutige Schlüssel für Tabellen. Mit eindeutigen Schlüsseln kann verhindert werden, dass doppelte Daten eingegeben werden. Der Standardwert ist " **true**". Weitere Informationen finden Sie unter [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).  
  
###  <a name="MgProviders"></a>Seite "Anbieter verwalten"  
 In diesen Dialogfeld können Sie Verbindungen mit Hostinganbietern anzeigen, hinzufügen, bearbeiten, löschen oder testen. Ein Hostinganbieter gibt die Verbindungsinformationen für einen Webdienst an, der auf der CodePlex-Website vom Server Hosting Toolkit aus mithilfe des Projekts für Datenbank-Veröffentlichungsdienste erstellt wurde.  
  
 **Konfigurierte Anbieter** : Listet den Namen und die **Webdienst** Adresse aller gespeicherten Hostinganbieter auf.  
  
 **Neu** : öffnet das Dialogfeld **Anbieter Konfiguration für neuen Anbieter** zum Hinzufügen eines neuen hostinganbieters.  
  
 **Bearbeiten** : öffnet das entsprechende Dialogfeld **Anbieter Konfiguration** , um einen vorhandenen Hostinganbieter zu bearbeiten.  
  
 **Löschen** : Löscht den ausgewählten Hostinganbieter.  
  
 **Testet die** Verbindung mit einem Hostingdienst, indem die Informationen des ausgewählten Anbieters verwendet werden.  
  
 **OK** : speichert alle Änderungen, die Sie im Dialogfeld **Hostinganbieter** vorgenommen haben.  
  
 **Abbrechen** : alle Änderungen, die Sie im Dialogfeld **Hostinganbieter** vorgenommen haben, werden aufgehoben.  
  
###  <a name="AdvPubOpts"></a>Seite "Erweiterte Veröffentlichungs Optionen"  
 Verwenden Sie diese Seite, um festzulegen, wie dieser Assistent eine Datenbank veröffentlichen soll. Es sind viele verschiedene Optionen verfügbar. Die Optionen werden abgeblendet dargestellt, wenn sie von der SQL Server- oder [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Version, die in **Datenbank-Engine-Typ** angegeben ist, nicht unterstützt werden.  
  
 **Optionen** : Geben Sie erweiterte Optionen an, indem Sie einen Wert aus der Liste der verfügbaren Einstellungen rechts neben den einzelnen Optionen auswählen.  
  
 **Allgemein** : die folgenden Optionen gelten für die gesamte Veröffentlichung.  
  
1.  **UDDTs in Basis Typen konvertieren** : Wenn **true**, werden benutzerdefinierte Datentypen (UDDT) in die zugrunde liegenden Basis Datentypen konvertiert, die für die Erstellung verwendet wurden. Verwenden Sie **True** , wenn der UDDT in der Datenbank, in der das Skript ausgeführt wird, nicht vorhanden ist. Im Falle von **False**werden UDDTs verwendet. Der Standardwert ist **False**.  
  
2.  **Sortierung veröffentlichen** : schließt Sortierungs Informationen für Tabellen Spalten ein. Der Standardwert ist **False**. Weitere Informationen finden Sie unter [Collation and Unicode Support](../collations/collation-and-unicode-support.md).  
  
3.  Standardwerte **veröffentlichen** : schließt Standardobjekte ein, die zum Festlegen von Standardwerten in Tabellen Spalten verwendet werden. Der Standardwert ist " **true**". Weitere Informationen finden Sie unter [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql).  
  
4.  **Abhängige Objekte veröffentlichen** : veröffentlicht jedes Objekt, das vorhanden sein muss, wenn das Skript für das ausgewählte Objekt ausgeführt wird. Der Standardwert ist **True**.  
  
5.  **Erweiterte Eigenschaften veröffentlichen** : schließt erweiterte Eigenschaften in das Skript ein, das zur Veröffentlichung an den Anbieter gesendet wird, wenn das Objekt über erweiterte Eigenschaften verfügt. Der Standardwert ist " **true**".  
  
6.  **Publish for Server Version** : erstellt ein Skript, das zur Veröffentlichung an den Remote Anbieter gesendet wird und auf eine Weise, die für die ausgewählte Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt werden kann. Neue Funktionen in einer Version können für eine Skripterstellung für frühere Versionen nicht verwendet werden. Der Standard ist die Version des Ursprungsservers.  
  
7.  **Berechtigungen auf Objektebene veröffentlichen** : schließt die Berechtigungen für die ausgewählten Objekte in der Datenbank ein. Der Standardwert ist **False**.  
  
8.  **Statistiken veröffentlichen** : Wenn diese Einstellung auf **Statistiken veröffentlichen**festgelegt `CREATE STATISTICS` ist, enthält die-Anweisung zum erneuten Erstellen der Statistiken für das Objekt. Mithilfe der Option **Statistiken und Histogramme veröffentlichen** können auch Histogramminformationen erstellt werden. Der Standardwert ist **Statistiken nicht veröffentlichen**. Weitere Informationen finden Sie unter [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
9. **Vardecimal--Optionen veröffentlichen** : aktiviert `vardecimal` das Tabellenformat in der Ziel Datenbanktabelle, wenn es in der Ursprungs Datenbanktabelle aktiviert ist. Der Standardwert ist " **true**".  
  
10. **Objektnamen für Schema qualifiziere** : schließt den Schema Namen im Namen der erstellten Objekte ein. Der Standardwert ist " **true**".  
  
11. **Skript Bindung** : schließt die Bindung für Standard-und Regel Objekte im Skript ein, das zur Veröffentlichung an den Anbieter gesendet wird. Der Standardwert ist " **true**". Weitere Informationen finden Sie unter [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql) und [CREATE RULE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-rule-transact-sql).  
  
12. **Zu veröffentlichende Datentypen** : wählt aus, wofür ein Skript erstellt werden soll: **nur Daten**, nur **Schema**oder beides. Der Standard ist **Schema und Daten**.  
  
 **Veröffentlichungs Optionen** : Hiermit wird angegeben, ob beim Veröffentlichen auf dem webhostinstanbieter Transaktionen verwendet werden sollen.  
  
1.  **Mit Transaktion veröffentlichen** : verwendet Transaktionen, wenn die Veröffentlichung in einem remotewebhostinganbieter erfolgt. Wenn die Zieldatenbank die Veröffentlichung nicht abschließen kann, werden die Transaktionen zurückgesetzt. Der Standardwert ist " **true**".  
  
 **Tabellen-/Sichtoptionen** : die folgenden Optionen gelten nur für Tabellen oder Sichten.  
  
1.  **Check-Einschränkungen veröffentlichen** : schließt die Erstellung `CHECK` von Einschränkungen im Veröffentlichungsprozess ein. Der Standardwert ist **True**. Für `CHECK`-Einschränkungen ist es erforderlich, dass Daten, die in eine Tabelle eingegeben werden, eine angegebene Bedingung erfüllen. Weitere Informationen finden Sie unter [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).  
  
2.  **Fremdschlüssel veröffentlichen** : schließt die Erstellung von Fremdschlüsseln in den Veröffentlichungsprozess ein. Der Standardwert ist " **true**". Mit Fremdschlüsseln können Beziehungen zwischen Tabellen angezeigt und erzwungen werden. Weitere Informationen finden Sie unter [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md).  
  
3.  **Veröffentlichen von Volltextindizes** : Skripts für die Erstellung von Volltextindizes. Der Standardwert ist **False**.  
  
4.  **Indizes veröffentlichen** : schließt Indizes für Tabellen in den Veröffentlichungsprozess ein. Der Standardwert ist " **true**". Mit Indizes können Sie Daten schneller finden.  
  
5.  **Primärschlüssel veröffentlichen** : schließt die Erstellung von primär Schlüsseln in den Veröffentlichungsprozess ein. Der Standardwert ist **True**. Mit Primärschlüsseln kann jede Zeile einer Tabelle eindeutig identifiziert werden. Weitere Informationen finden Sie unter [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md).  
  
6.  **Veröffentlichungs Trigger** : schließt die Erstellung von DML-Triggern in den Veröffentlichungsprozess ein. Der Standardwert ist " **true**". Ein DML-Trigger ist eine Aktion, die so programmiert ist, dass sie bei Auftreten eines DML-Ereignisses (Data Manipulation Language, Datenbearbeitungssprache) auf dem Datenbankserver ausgeführt wird. Weitere Informationen finden Sie unter [DML Triggers](../triggers/dml-triggers.md).  
  
7.  **Eindeutige Schlüssel veröffentlichen** : schließt die Erstellung eindeutiger Schlüssel für Tabellen im Veröffentlichungsprozess ein. Mit eindeutigen Schlüsseln kann verhindert werden, dass doppelte Daten eingegeben werden. Der Standardwert ist " **true**". Weitere Informationen finden Sie unter [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).  
  
8.  **Änderungs Nachverfolgung veröffentlichen** : schließt die Änderungs Nachverfolgung in den Veröffentlichungsprozess ein, wenn Sie in der Ursprungs Datenbank oder in den Tabellen in der Ursprungs Datenbank aktiviert ist. Der Standardwert ist **False**. Weitere Informationen finden Sie unter [Informationen zur Änderungsnachverfolgung &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md).  
  
9. **Optionen für die Datenkomprimierung veröffentlichen** : schließt Daten Komprimierungs Optionen in den Veröffentlichungsprozess ein, wenn Sie in der Ursprungs Datenbank oder in den Tabellen in der Ursprungs Datenbank konfiguriert sind. Der Standardwert ist " **true**". Weitere Informationen finden Sie unter [Data Compression](../data-compression/data-compression.md).  
  
###  <a name="ProvConfig"></a>Seite "Anbieter Konfiguration"  
 Mithilfe dieses Dialogfelds können Sie Hostinganbieter-Einstellungen anzeigen oder ändern. Mithilfe dieses Dialogfeld können Sie folgende Aufgaben ausführen:  
  
-   Anzeigen, Hinzufügen oder Bearbeiten der Verbindungsinformationen für einen Hostinganbieter.  
  
-   Anzeigen, Hinzufügen, Bearbeiten oder Löschen einer Datenbank für eine Anbieterverbindung.  
  
-   Automatisches Konfigurieren von Datenbanken für einen Hostinganbieter  
  
 Ein Hostinganbieter gibt die Verbindungsinformationen für einen Webdienst an, der auf der CodePlex-Website vom Server Hosting Toolkit aus mithilfe des Projekts für Datenbank-Veröffentlichungsdienste erstellt wurde.  
  
 **Name** : Name des hostinganbieters.  
  
 **Webdienst Adresse** : die HTTPS-Adresse für den Hostingdienst.  
  
 **Webdienst Authentifizierung** : der Benutzername und das Kennwort, die für die Anmeldung beim Hostingdienst erforderlich sind.  
  
 **Kennwort speichern** : Verschlüsseln und speichern Sie das Kennwort auf dem lokalen Computer.  
  
 **Verfügbare Datenbanken** : für Hostinganbieter konfigurierte Datenbanken werden in aufsteigender Reihenfolge im folgenden Format aufgeführt: *server_name*. *database_name*.  
  
 **Neu** : Öffnen Sie das Dialogfeld **Daten Bank** Konfiguration, und fügen Sie eine neue Datenbank hinzu.  
  
 **Bearbeiten** : öffnet das Dialogfeld **Daten Bank** Konfiguration für die ausgewählte Datenbank.  
  
 **Löschen** : Löscht die ausgewählte Datenbank.  
  
 **Als Standard festlegen** : Wählen Sie die Datenbank als Standard aus.  
  
 **OK** : Speichern Sie alle Änderungen, die Sie in diesem Dialogfeld vorgenommen haben, und kehren Sie zum Assistenten zurück.  
  
 **Abbrechen** : alle Änderungen, die Sie in diesem Dialogfeld vorgenommen haben, rückgängig machen und zum Assistenten zurückkehren.  
  
###  <a name="Summary"></a> Seite "Zusammenfassung"  
 Auf dieser Seite sind die Optionen zusammengefasst, die Sie in diesem Assistenten ausgewählt haben. Um eine Option zu ändern, klicken Sie auf **Zurück**. Um mit der Generierung von Skripts zu beginnen, die gespeichert oder veröffentlicht werden, klicken Sie auf **Weiter**.  
  
 **Überprüfen Sie Ihre Auswahl** : zeigt die Auswahl an, die Sie für die einzelnen Seiten des Assistenten getroffen haben. Erweitern Sie einen Knoten, um die auf der betreffenden Seite ausgewählten Optionen anzuzeigen.  
  
###  <a name="SavePubScripts"></a>Seite "Skripts speichern oder veröffentlichen"  
 Mithilfe dieser Seite können Sie den Status des Assistenten überwachen.  
  
 **Details** : zeigen Sie die Spalte **Aktion** an, um den Fortschritt des Assistenten anzuzeigen. Nach der Generierung speichert der Assistent die Skripts in einer Datei oder verwendet sie zum Veröffentlichen in einem Webdienst, abhängig von Ihrer Auswahl. Wenn diese Schritte abgeschlossen sind, klicken Sie auf den Wert in der Spalte **Ergebnis** , um das Ergebnis des entsprechenden Schritts anzuzeigen.  
  
 **Bericht speichern** : Klicken Sie hierauf, um die Ergebnisse des Assistenten in eine Datei zu speichern.  
  
 **Abbrechen** : Klicken Sie hier, um den Assistenten zu schließen, bevor die Verarbeitung abgeschlossen ist, oder, wenn ein Fehler auftritt.  
  
 **Fertig** stellen: Klicken Sie hier, um den Assistenten zu schließen, nachdem die Verarbeitung abgeschlossen wurde, oder wenn ein Fehler auftritt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren von SMO](../server-management-objects-smo/installing-smo.md)   
 [Kopieren von Datenbanken auf andere Server](../databases/copy-databases-to-other-servers.md)  
  
  
