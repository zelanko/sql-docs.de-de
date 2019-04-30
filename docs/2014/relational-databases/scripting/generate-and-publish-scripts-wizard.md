---
title: Assistenten zum Generieren und Veröffentlichen von Skripts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
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
ms.openlocfilehash: 7d7c1da71445659d61fa95dc30bc7f128a1e1d40
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63225442"
---
# <a name="generate-and-publish-scripts-wizard"></a>Assistenten zum Generieren und Veröffentlichen von Skripts
  Sie können mit dem **Assistenten zum Generieren und Veröffentlichen von Skripts** Skripts zur Übertragung einer Datenbank zwischen Instanzen von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] oder [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]erstellen. Sie können Skripts für eine Datenbank auf einer Datenbank-Engine-Instanz im lokalen Netzwerk oder von [!INCLUDE[ssSDS](../../includes/sssds-md.md)] aus generieren. Die generierten Skripts können auf einer anderen Datenbank-Engine-Instanz oder von [!INCLUDE[ssSDS](../../includes/sssds-md.md)] aus ausgeführt werden. Sie können den Assistenten außerdem dazu verwenden, den Inhalt einer Datenbank direkt in einem Webdienst zu veröffentlichen, der mit den Datenbank-Veröffentlichungsdiensten erstellt wurde. Sie können Skripts für eine gesamte Datenbank oder für eine Auswahl bestimmter Objekte erstellen.  
  
1.  **Vorbereitungen:**  [Veröffentlichen in einem gehosteten Dienst](#PubHostSvc), [Berechtigungen](#Permissions)  
  
2.  **Zum Generieren oder Veröffentlichen eines Skripts verwenden:**  [Das Generieren und Veröffentlichen von Skripts-Assistenten](#GenPubScriptWiz)  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Die Quell- und Zieldatenbank können sich auf [!INCLUDE[ssSDS](../../includes/sssds-md.md)]oder einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] befinden, die mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höher ausgeführt wird.  
  
###  <a name="PubHostSvc"></a> Veröffentlichen in einem gehosteten Dienst  
 Der **Assistent zum Generieren und Veröffentlichen von Skripts** kann nicht nur zum Erstellen von Skripts, sondern auch zum Veröffentlichen einer Datenbank in einem bestimmten gehosteten SQL Server-Webdienst verwendet werden. Das SQL Server Hosting Toolkit stellt auf der CodePlex-Website Datenbank-Veröffentlichungsdienste als freigegebenes Quellprojekt zur Verfügung. Das Projekt für Datenbank-Veröffentlichungsdienste kann von Webhostinganbietern zum Erstellen einer Gruppe von Webdiensten verwendet werden, mit denen deren Kunden Datenbanken problemlos für den Webdienst bereitstellen können. Weitere Informationen zum Herunterladen des SQL Server Hosting Toolkits finden Sie unter [SQL Server Database Publishing Services](https://go.microsoft.com/fwlink/?LinkId=142025).  
  
 Aktivieren Sie zum Veröffentlichen einer Datenbank in einem Webhostingdienst auf der Seite **Skripterstellungsoptionen festlegen** des Assistenten die Option **In Webdienst veröffentlichen** .  
  
###  <a name="Permissions"></a> Berechtigungen  
 Zum Veröffentlichen einer Datenbank ist mindestens die Mitgliedschaft in der festen Datenbankrolle db_ddladmin in der Ursprungsdatenbank erforderlich. Zum Veröffentlichen eines Datenbankskripts in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem Hostinganbieter ist mindestens die Mitgliedschaft in der festen Datenbankrolle db_ddladmin auf der Zieldatenbank erforderlich.  
  
 Außerdem muss bei der Veröffentlichung mit dem Assistenten ein Benutzername mit zugehörigem Kennwort für den Zugriff auf das Konto beim Hostinganbieter angegeben werden. Die Zieldatenbank muss auf dem Hostinganbieter erstellt werden, bevor die Quelldatenbank veröffentlicht wird. Durch die Veröffentlichung werden Objekte in der bestehenden Datenbank überschrieben.  
  
##  <a name="GenPubScriptWiz"></a> Verwenden des Assistenten zum Generieren und Veröffentlichen von Skripts  
 **So erstellen und veröffentlichen Sie ein Skript**  
  
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
  
 **Diese Seite nicht mehr anzeigen** – Diese Seite wird beim nächsten Starten des **Assistenten zum Generieren und Veröffentlichen von Skripts** übersprungen.  
  
 **Weiter >** – Geht zur Seite **Methode auswählen** über.  
  
 **Abbrechen** – Beendet den Assistenten, ohne ein Skript aus der Datenbank zu generieren oder veröffentlichen.  
  
###  <a name="ChooseObjects"></a> Seite "Objekte auswählen"  
 Wählen Sie auf dieser Seite aus, welche Objekte in die von diesem Assistenten generierten Skripts eingeschlossen werden sollen. Auf der folgenden Seite des Assistenten können Sie diese Skripts am Speicherort Ihrer Wahl speichern oder sie verwenden, um Datenbankobjekte an einen Remotewebhostinganbieter zu veröffentlichen, bei dem die [SQL Server-Datenbank-Veröffentlichungsdienste](https://go.microsoft.com/fwlink/?LinkId=142025)installiert sind.  
  
 **Option „Skript für gesamte Datenbank erstellen“** – Klicken Sie hier, um Skripts für alle Objekte in der Datenbank zu generieren und ein Skript für die Datenbank selbst einzuschließen.  
  
 **Bestimmte Datenbankobjekte auswählen** – Klicken Sie hier, um den Assistenten auf die Generierung von Skripts für von Ihnen ausgewählte Objekte in der Datenbank einzuschränken:  
  
-   **Datenbankobjekte** – Wählen Sie mindestens ein Objekt aus, das ins Skript eingeschlossen werden soll.  
  
-   **Alles auswählen** – Aktiviert alle verfügbaren Kontrollkästchen.  
  
-   **Auswahl aufheben** – Deaktiviert alle Kontrollkästchen. Sie müssen in diesem Fall mindestens ein Datenbankobjekt auswählen, um den Vorgang fortsetzen zu können.  
  
###  <a name="SetScriptOpt"></a> Seite "Skripterstellungsoptionen festlegen"  
 Auf dieser Seite können Sie angeben, ob Skripts vom Assistenten am ausgewählten Speicherort gespeichert werden, oder ob damit Datenbankobjekte bei einem Remotewebhostinganbieter veröffentlicht werden. Für die Veröffentlichung müssen Sie Zugriff auf einen Webdienst haben, der mithilfe des Webdiensts "Datenbank-Veröffentlichungsdienste" installiert wird.  
  
 **Optionen** – Wenn der Assistent Skripts an einem Speicherort Ihrer Wahl speichern soll, wählen Sie **Skripts an einem bestimmten Speicherort speichern**aus. Sie können die Skripts später für eine Datenbank-Engine-Instanz oder für [!INCLUDE[ssSDS](../../includes/sssds-md.md)]ausführen. Wenn der Assistent die Datenbankobjekte in einem Remote-Webhostinganbieter veröffentlichen soll, wählen Sie **In Webdienst veröffentlichen**aus.  
  
 **Skripts an einem bestimmten Speicherort speichern** – speichern Sie eine oder mehrere. Transact-SQL-Skriptdateien an einem Speicherort Geben Sie an.  
  
-   **Erweitert** – Zeigt das Dialogfeld **Erweiterte Skripterstellungsoptionen** an, in dem Sie erweiterte Optionen für die Skripterstellung auswählen können.  
  
-   **In Datei speichern** – Speichert das Skript in einer oder mehreren SQL-Dateien. Klicken Sie auf die Schaltfläche zum Durchsuchen (**…**), um Namen und Speicherort für die Datei anzugeben. Aktivieren Sie das Kontrollkästchen **Vorhandene Datei überschreiben** , um die Datei zu ersetzen, wenn bereits eine Datei mit dem gleichen Namen vorhanden ist. Klicken Sie auf **Einzelne Datei** oder **Einzelne Datei pro Objekt** , um anzugeben, wie die Skripts generiert werden sollen. Klicken Sie auf **Unicode-Text** oder **ANSI-Text** , um die Art von Text anzugeben, die im Skript verwendet werden soll.  
  
-   **In Zwischenablage speichern** – Speichert das Transact-SQL-Skript in die Zwischenablage.  
  
-   **In neuem Abfragefenster speichern** – Generiert das Skript in einem Fenster des Datenbank-Engine-Abfrage-Editors. Wenn kein Editor-Fenster geöffnet ist, wird ein neues Editor-Fenster als Skriptziel geöffnet.  
  
 **In Webdienst veröffentlichen** – Veröffentlichen Sie die ausgewählten Objekte in einem Remote-Webhostingdienst, für den Sie einen Anbieter konfiguriert haben.  
  
-   **Anbieter verwalten** – Zeigt das Dialogfeld **Anbieter verwalten** an. Verwenden Sie das Dialogfeld **Anbieter verwalten** , um Hostinganbieter hinzuzufügen, zu bearbeiten und zu löschen. Jeder Anbieter gibt die Verbindungsinformationen zu einem Webhostingdienst und zu den Zieldatenbanken für diesen Dienst an.  
  
-   **Erweitert** – Zeigt das Dialogfeld **Erweiterte Veröffentlichungsoptionen** an, in dem Sie erweiterte Optionen für die Skriptveröffentlichung auswählen können.  
  
-   **Anbieter** – Wählen Sie den Anbieter aus, der die Verbindungsinformationen für den Webhostingdienst angibt, der die Datenbank, in der Sie die ausgewählten Objekte veröffentlichen möchten, hostet. Zur Auswahl eines Anbieters muss mindestens ein Anbieter im Dialogfeld **Anbieter verwalten** verfügbar sein.  
  
-   **Zieldatenbank** – Wählt die Zieldatenbank aus, in der Sie die von Ihnen ausgewählten Objekte veröffentlichen möchten. Sie müssen vor dem Auswählen einer Zieldatenbank einen Anbieter auswählen.  
  
###  <a name="AdvScriptOpt"></a> Seite "Erweiterte Skripterstellungsoptionen"  
 Verwenden Sie diese Seite, um festzulegen, wie dieser Assistent Skripts generieren soll. Es sind viele verschiedene Optionen verfügbar. Die Optionen werden abgeblendet dargestellt, wenn sie von der SQL Server- oder [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Version, die in **Datenbank-Engine-Typ** angegeben ist, nicht unterstützt werden.  
  
 **Optionen** – Sie können erweiterte Skriptoptionen angeben, indem Sie einen Wert aus der Liste der verfügbaren Einstellungen rechts neben den einzelnen Optionen auswählen.  
  
 **Allgemein**: Die folgenden Optionen gelten für das ganze Skript.  
  
-   **ANSI-Auffüllung** -enthält `ANSI PADDING ON` im Skript. Der Standardwert ist **True**.  
  
-   **An Datei anfügen** – Im Falle von **True**wird dieses Skript am Ende eines vorhandenen Skripts angefügt, angegeben auf der Seite **Skripterstellungsoptionen festlegen** . Im Falle von **False**überschreibt das neue Skript ein vorheriges Skript. Der Standardwert ist **False**.  
  
-   **Skripterstellung bei einem Fehler fortsetzen** – Im Falle von **True**wird die Skripterstellung bei Auftreten eines Fehlers beendet. Im Falle von **False**wird die Skripterstellung fortgesetzt. Der Standardwert ist **False**.  
  
-   **UDDTs in Basistypen konvertieren** – Im Falle von **True**werden benutzerdefinierte Datentypen (UDDT) in die zugrunde liegenden Basisdatentypen konvertiert, die zu ihrer Erstellung verwendet wurden. Verwenden Sie **True** , wenn der UDDT in der Datenbank, in der das Skript ausgeführt wird, nicht vorhanden ist. Im Falle von **False**werden UDDTs verwendet. Der Standardwert ist **False**.  
  
-   **Skript für abhängige Objekte generieren** – Generiert ein Skript für jedes Objekt, das vorhanden sein muss, wenn das Skript für das ausgewählte Objekt ausgeführt wird. Der Standardwert ist **True**.  
  
-   **Beschreibende Header einschließen** – Im Falle von **True**werden dem Skript beschreibende Kommentare hinzugefügt, mit denen das Skript für jedes Objekt in Abschnitte unterteilt wird. Der Standardwert ist **False**.  
  
-   **„IF NOT EXISTS“ einschließen** – Im Falle von **True**enthält das Skript eine Anweisung, um zu überprüfen, ob das Objekt bereits in der Datenbank vorhanden ist, und versucht nicht, ein neues Objekt zu erstellen, wenn das Objekt bereits vorhanden ist. Der Standardwert ist **False**.  
  
-   **Einschränkungsnamen des Systems einschließen** – Im Falle von **False**(Standardwert) werden Einschränkungen, die automatisch in der Ursprungsdatenbank benannt wurden, in der Zieldatenbank automatisch umbenannt. Im Falle von **True**haben Einschränkungen in der Ursprungs- und der Zieldatenbank den gleichen Namen.  
  
-   **Nicht unterstützte Anweisungen einschließen** – Im Falle von **False**enthält das Skript keine Anweisungen für Objekte, die unter der ausgewählten Serverversion bzw. dem ausgewählten Engine-Typ nicht unterstützt werden. Bei **True**enthält das Skript nicht unterstützte Objekte. Jede Anweisung für ein nicht unterstütztes Objekt enthält einen Kommentar, dass die Anweisung bearbeitet werden muss, bevor das Skript für die ausgewählte SQL Server-Version bzw. den ausgewählten Engine-Typ ausgeführt werden kann. Der Standardwert ist **False**.  
  
-   **Objektnamen mit Schema qualifizieren** – Schließt den Schemanamen im Namen der erstellten Objekte ein. Der Standardwert ist **True**.  
  
-   **Skriptbindung** – Generiert ein Skript zum Binden von Standard- und Regelobjekten. Der Standardwert ist **False**. Weitere Informationen finden Sie unter [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql) und [CREATE RULE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-rule-transact-sql).  
  
-   **Skriptsortierung** – Schließt Sortierungsinformationen ins Skript ein. Der Standardwert ist **False**. Weitere Informationen finden Sie unter [Collation and Unicode Support](../collations/collation-and-unicode-support.md).  
  
-   **Skripterstellung für Standard** – Schließt Standardobjekte ein, die zum Festlegen von Standardwerten in Tabellenspalten verwendet wurden. Der Standardwert ist **True**. Weitere Informationen finden Sie unter [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql).  
  
-   **DROP und CREATE als Skript** – Bei **Script CREATE** werden [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Anweisungen bei der Erstellung von Objekten eingeschlossen. Wenn **DROP als Skript**ausgewählt ist, sind [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Anweisungen eingeschlossen, um Objekte zu löschen. Wenn **DROP und CREATE als Skript**ausgewählt ist, ist die [!INCLUDE[tsql](../../../includes/tsql-md.md)] -DROP-Anweisung im Skript für jedes geschriebene Objekt enthalten, gefolgt von der CREATE-Anweisung. Der Standardwert ist **CREATE als Skript**.  
  
-   **Skripterstellung für erweiterte Eigenschaften** – Enthält erweiterte Eigenschaften im Skript, wenn das Objekt über erweiterte Eigenschaften verfügt. Der Standardwert ist **True**.  
  
-   **Skripterstellung für Engine-Typ** – Erstellt ein Skript, das für den ausgewählten Typ von [!INCLUDE[ssSDS](../../includes/sssds-md.md)] bzw. den ausgewählten Typ einer Instanz der SQL Server-Datenbank-Engine ausgeführt werden kann. Für den angegebenen Typ nicht unterstützte Objekte werden nicht in das Skript eingeschlossen. Der Standardwert ist der Typ des Ursprungsservers.  
  
-   **Skripterstellung für Serverversion** – Erstellt ein Skript, das für die ausgewählte Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt werden kann. Neue Funktionen in einer Version können für eine Skripterstellung für frühere Versionen nicht verwendet werden. Der Standard ist die Version des Ursprungsservers.  
  
-   **Skripterstellung für Anmeldungen** – Wenn das Objekt, für das ein Skript erstellt werden soll, ein Datenbankbenutzer ist, werden mit dieser Option die Anmeldungen erstellt, von denen der Benutzer abhängig ist. Der Standardwert ist **False**.  
  
-   **Skripterstellung für Berechtigungen auf Objektebene** – Schließt Skripts ein, um die Berechtigung für Objekte in der Datenbank festzulegen. Der Standardwert ist **False**.  
  
-   **Skripterstellung für Statistiken** : bei Festlegung auf **Skripterstellung für Statistiken**, schließt diese Option die `CREATE STATISTICS` -Anweisung zum erneuten Erstellen von Statistiken für das Objekt. Mit der Option **Skripterstellung für Statistiken und Histogramme** können auch Histogramminformationen erstellt werden. Der Standardwert ist **Keine Skripterstellung für Statistiken**. Weitere Informationen finden Sie unter [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
-   **Skripterstellung für USE DATABASE** -fügt die `USE DATABASE` Anweisung, um das Skript. Die `USE DATABASE`-Anweisung muss enthalten sein, um sicherzustellen, dass Datenbankobjekte in der richtigen Datenbank erstellt werden. Wenn das Skript in einer anderen Datenbank verwendet werden soll, wählen Sie **"false"** zum Auslassen der `USE DATABASE` Anweisung. Der Standardwert ist **True**. Weitere Informationen finden Sie unter [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).  
  
-   **Typen von Skript** -wählt aus, was geskriptet werden soll: **Nur Daten**, **nur Schema**, oder beides. Der Standard ist **Nur Schema**.  
  
 **Tabellen-/Sichtoptionen** – Die folgenden Optionen gelten nur für Skripts für Tabellen oder Sichten.  
  
-   **Skript für Änderungsnachverfolgung erstellen** – Die Änderungsnachverfolgung für Skripts wird in der Ursprungsdatenbank oder in den Tabellen in der Ursprungsdatenbank aktiviert. Der Standardwert ist **False**. Weitere Informationen finden Sie unter [Informationen zur Änderungsnachverfolgung &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md).  
  
-   **Skripterstellung für Check-Einschränkungen** -fügt `CHECK` Einschränkungen an das Skript. Der Standardwert ist **True**. Für `CHECK`-Einschränkungen ist es erforderlich, dass Daten, die in eine Tabelle eingegeben werden, eine angegebene Bedingung erfüllen. Weitere Informationen finden Sie unter [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).  
  
-   **Skripterstellung für Datenkomprimierungsoptionen** – Schließt Datenkomprimierungsoptionen ein, wenn sie in der Ursprungsdatenbank oder den Tabellen in der Ursprungsdatenbank konfiguriert werden. Weitere Informationen finden Sie unter [Data Compression](../data-compression/data-compression.md). Der Standardwert ist **False**.  
  
-   **Skripterstellung für Fremdschlüssel** – Fügt dem Skript Fremdschlüssel hinzu. Der Standardwert ist **True**. Mit Fremdschlüsseln können Beziehungen zwischen Tabellen angezeigt und erzwungen werden.  
  
-   **Skripterstellung für Volltextindizes** – Dient zur Skripterstellung für Volltextindizes. Der Standardwert ist **False**.  
  
-   **Skripterstellung für Indizes** – Dient zur Skripterstellung für Indizes für die Tabellen. Der Standardwert ist **True**. Mit Indizes können Sie Daten schneller finden.  
  
-   **Skripterstellung für Primärschlüssel** – Dient zur Skripterstellung für Primärschlüssel für die Tabellen. Der Standardwert ist **True**. Mit Primärschlüsseln kann jede Zeile einer Tabelle eindeutig identifiziert werden.  
  
-   **Skripterstellung für Trigger** – Dient zur Skripterstellung für DML-Trigger für Tabellen. Der Standardwert ist **False**. Ein DML-Trigger ist eine Aktion, die so programmiert ist, dass sie bei Auftreten eines DML-Ereignisses (Data Manipulation Language, Datenbearbeitungssprache) auf dem Datenbankserver ausgeführt wird. Weitere Informationen finden Sie unter [DML Triggers](../triggers/dml-triggers.md).  
  
-   **Skripterstellung für eindeutige Schlüssel** – Dient zur Skripterstellung für eindeutige Schlüssel für Tabellen. Mit eindeutigen Schlüsseln kann verhindert werden, dass doppelte Daten eingegeben werden. Der Standardwert ist **True**. Weitere Informationen finden Sie unter [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).  
  
###  <a name="MgProviders"></a> Seite "Anbieter verwalten"  
 In diesen Dialogfeld können Sie Verbindungen mit Hostinganbietern anzeigen, hinzufügen, bearbeiten, löschen oder testen. Ein Hostinganbieter gibt die Verbindungsinformationen für einen Webdienst an, der auf der CodePlex-Website vom Server Hosting Toolkit aus mithilfe des Projekts für Datenbank-Veröffentlichungsdienste erstellt wurde.  
  
 **Konfigurierte Anbieter** – Listet den Namen und die **Webdienstadresse** aller gespeicherten Hostinganbieter auf.  
  
 **Neu** – Öffnet das Dialogfeld **Anbieterkonfiguration** für neuen Anbieter zum Hinzufügen eines neuen Hostinganbieters.  
  
 **Bearbeiten** – Öffnet das entsprechende Dialogfeld **Anbieterkonfiguration** zum Bearbeiten eines vorhandenen Hostinganbieters.  
  
 **Löschen** – Löscht den ausgewählten Hostinganbieter.  
  
 **Testen** – Testet die Verbindung mit einem Hostingdienst, wobei die Informationen des ausgewählten Anbieters verwendet werden.  
  
 **OK** – Speichert alle Änderungen, die Sie im Dialogfeld **Hostinganbieter** vorgenommen haben.  
  
 **Abbrechen** – Macht alle Änderungen rückgängig, die Sie im Dialogfeld **Hostinganbieter** vorgenommen haben.  
  
###  <a name="AdvPubOpts"></a> Seite "Erweiterte Veröffentlichungsoptionen"  
 Verwenden Sie diese Seite, um festzulegen, wie dieser Assistent eine Datenbank veröffentlichen soll. Es sind viele verschiedene Optionen verfügbar. Die Optionen werden abgeblendet dargestellt, wenn sie von der SQL Server- oder [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Version, die in **Datenbank-Engine-Typ** angegeben ist, nicht unterstützt werden.  
  
 **Optionen** – Sie können erweiterte Skriptoptionen angeben, indem Sie einen Wert aus der Liste der verfügbaren Einstellungen rechts neben den einzelnen Optionen auswählen.  
  
 **Allgemein**: Die folgenden Optionen gelten für die gesamte Veröffentlichung.  
  
1.  **UDDTs in Basistypen konvertieren** – Im Falle von **True**werden benutzerdefinierte Datentypen (UDDT) in die zugrunde liegenden Basisdatentypen konvertiert, die zu ihrer Erstellung verwendet wurden. Verwenden Sie **True** , wenn der UDDT in der Datenbank, in der das Skript ausgeführt wird, nicht vorhanden ist. Im Falle von **False**werden UDDTs verwendet. Der Standardwert ist **False**.  
  
2.  **Sortierung veröffentlichen** – Enthält Sortierungsinformationen für Tabellenspalten. Der Standardwert ist **False**. Weitere Informationen finden Sie unter [Collation and Unicode Support](../collations/collation-and-unicode-support.md).  
  
3.  **Standardwerte veröffentlichen** – Schließt Standardobjekte ein, die zum Festlegen von Standardwerten in Tabellenspalten verwendet wurden. Der Standardwert ist **True**. Weitere Informationen finden Sie unter [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql).  
  
4.  **Abhängige Objekte veröffentlichen** – Veröffentlicht jedes Objekt, das vorhanden sein muss, wenn das Skript für das ausgewählte Objekt ausgeführt wird. Der Standardwert ist **True**.  
  
5.  **Erweiterte Eigenschaften veröffentlichen** – Schließt erweiterte Eigenschaften in das Skript ein, das zur Veröffentlichung an den Anbieter gesendet wird, wenn das Objekt erweiterte Eigenschaften hat. Der Standardwert ist **True**.  
  
6.  **Für Serverversion veröffentlichen** – Erstellt ein Skript, das zur Veröffentlichung an den Remoteanbieter gesendet wird, sodass es auf der ausgewählten Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt werden kann. Neue Funktionen in einer Version können für eine Skripterstellung für frühere Versionen nicht verwendet werden. Der Standard ist die Version des Ursprungsservers.  
  
7.  **Berechtigungen auf Objektebene veröffentlichen** – Schließt die Berechtigungen für die ausgewählten Objekte in der Datenbank ein. Der Standardwert ist **False**.  
  
8.  **Statistiken veröffentlichen** : bei Festlegung auf **Statistiken veröffentlichen**, enthält die `CREATE STATISTICS` -Anweisung zum erneuten Erstellen von Statistiken für das Objekt. Mithilfe der Option **Statistiken und Histogramme veröffentlichen** können auch Histogramminformationen erstellt werden. Der Standardwert ist **Statistiken nicht veröffentlichen**. Weitere Informationen finden Sie unter [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
9. **Vardecimal-Optionen veröffentlichen** -ermöglicht die `vardecimal` -Tabellenformat in der Zieldatenbanktabelle, wenn sie in der ursprungsdatenbanktabelle aktiviert ist. Der Standardwert ist **True**.  
  
10. **Objektnamen mit Schema qualifizieren** – Schließt den Schemanamen im Namen der erstellten Objekte ein. Der Standardwert ist **True**.  
  
11. **Skriptbindung** – Schließt die Bindung für Standard- und Regelobjekte im Skript ein, das zum Veröffentlichen an den Anbieter gesendet wird. Der Standardwert ist **True**. Weitere Informationen finden Sie unter [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql) und [CREATE RULE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-rule-transact-sql).  
  
12. **Typen der zu veröffentlichenden Daten** -wählt aus, was geskriptet werden soll: **Nur Daten**, **nur Schema**, oder beides. Der Standard ist **Schema und Daten**.  
  
 **Veröffentlichungsoptionen**: Gibt an, ob beim Veröffentlichen auf dem Webhostinganbieter Transaktionen verwendet werden sollen.  
  
1.  **Mithilfe einer Transaktion veröffentlichen** – Verwendet Transaktionen beim Veröffentlichen zu einem Remote-Webhostinganbieter. Wenn die Zieldatenbank die Veröffentlichung nicht abschließen kann, werden die Transaktionen zurückgesetzt. Der Standardwert ist **True**.  
  
 **Tabellen-/Sichtoptionen** – Die folgenden Optionen gelten nur für Tabellen oder Sichten.  
  
1.  **Check-Einschränkungen veröffentlichen** -schließt die Erstellung von `CHECK` Einschränkungen in den Veröffentlichungsprozess. Der Standardwert ist **True**. Für `CHECK`-Einschränkungen ist es erforderlich, dass Daten, die in eine Tabelle eingegeben werden, eine angegebene Bedingung erfüllen. Weitere Informationen finden Sie unter [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).  
  
2.  **Fremdschlüssel veröffentlichen** – Schließt die Erstellung von Fremdschlüsseln in den Veröffentlichungsprozess ein. Der Standardwert ist **True**. Mit Fremdschlüsseln können Beziehungen zwischen Tabellen angezeigt und erzwungen werden. Weitere Informationen finden Sie unter [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md).  
  
3.  **Volltextindizes veröffentlichen** – Dient zur Skripterstellung für Volltextindizes. Der Standardwert ist **False**.  
  
4.  **Indizes veröffentlichen** – Schließt Indizes für Tabellen in den Veröffentlichungsprozess ein. Der Standardwert ist **True**. Mit Indizes können Sie Daten schneller finden.  
  
5.  **Primärschlüssel veröffentlichen** – Schließt die Erstellung von Primärschlüsseln in den Veröffentlichungsprozess ein. Der Standardwert ist **True**. Mit Primärschlüsseln kann jede Zeile einer Tabelle eindeutig identifiziert werden. Weitere Informationen finden Sie unter [Primary and Foreign Key Constraints](../tables/primary-and-foreign-key-constraints.md).  
  
6.  **Trigger veröffentlichen** – Schließt die Erstellung von DML-Triggern in den Veröffentlichungsprozess ein. Der Standardwert ist **True**. Ein DML-Trigger ist eine Aktion, die so programmiert ist, dass sie bei Auftreten eines DML-Ereignisses (Data Manipulation Language, Datenbearbeitungssprache) auf dem Datenbankserver ausgeführt wird. Weitere Informationen finden Sie unter [DML Triggers](../triggers/dml-triggers.md).  
  
7.  **Eindeutige Schlüssel veröffentlichen** – Schließt die Erstellung eindeutiger Schlüssel für Tabellen in den Veröffentlichungsprozess ein. Mit eindeutigen Schlüsseln kann verhindert werden, dass doppelte Daten eingegeben werden. Der Standardwert ist **True**. Weitere Informationen finden Sie unter [Unique Constraints and Check Constraints](../tables/unique-constraints-and-check-constraints.md).  
  
8.  **Änderungsnachverfolgung veröffentlichen** – Schließt die Änderungsnachverfolgung in den Veröffentlichungsprozess ein, wenn es in der Ursprungsdatenbank oder den Tabellen in der Ursprungsdatenbank aktiviert wird. Der Standardwert ist **False**. Weitere Informationen finden Sie unter [Informationen zur Änderungsnachverfolgung &#40;SQL Server&#41;](../track-changes/about-change-tracking-sql-server.md).  
  
9. **Datenkomprimierungsoptionen veröffentlichen** – Schließt Datenkomprimierungsoptionen in den Veröffentlichungsprozess ein, wenn sie in der Ursprungsdatenbank oder den Tabellen in der Ursprungsdatenbank konfiguriert werden. Der Standardwert ist **True**. Weitere Informationen finden Sie unter [Data Compression](../data-compression/data-compression.md).  
  
###  <a name="ProvConfig"></a> Seite "Anbieterkonfiguration"  
 Mithilfe dieses Dialogfelds können Sie Hostinganbieter-Einstellungen anzeigen oder ändern. Mithilfe dieses Dialogfeld können Sie folgende Aufgaben ausführen:  
  
-   Anzeigen, Hinzufügen oder Bearbeiten der Verbindungsinformationen für einen Hostinganbieter.  
  
-   Anzeigen, Hinzufügen, Bearbeiten oder Löschen einer Datenbank für eine Anbieterverbindung.  
  
-   Automatisches Konfigurieren von Datenbanken für einen Hostinganbieter  
  
 Ein Hostinganbieter gibt die Verbindungsinformationen für einen Webdienst an, der auf der CodePlex-Website vom Server Hosting Toolkit aus mithilfe des Projekts für Datenbank-Veröffentlichungsdienste erstellt wurde.  
  
 **Name** – Name des Hostinganbieters.  
  
 **Webdienstadresse** – HTTPS-Adresse des Hostingdiensts.  
  
 **Webdienstauthentifizierung** – Der Benutzername und das Kennwort, die beide zum Anmelden am Hostingdienst erforderlich sind.  
  
 **Kennwort speichern** – Verschlüsseln und speichern Sie das Kennwort auf dem lokalen Computer.  
  
 **Verfügbare Datenbanken** – Für Hostinganbieter konfigurierte Datenbanken werden in aufsteigender Reihenfolge in folgendem Format aufgeführt: *server_name*.*database_name*.  
  
 **Neu** – Öffnet das Konfigurationsdialogfeld **Datenbank** und fügt eine neue Datenbank hinzu.  
  
 **Bearbeiten** – Öffnet das Konfigurationsdialogfeld **Datenbank** für die ausgewählte Datenbank.  
  
 **Löschen** – Löscht die ausgewählte Datenbank.  
  
 **Als Standard festlegen** – Legt die Datenbank als Standard fest.  
  
 **OK** – Speichert alle in diesem Dialogfeld vorgenommenen Änderungen und ruft den Assistenten erneut auf.  
  
 **Abbrechen** – Verwirft alle in diesem Dialogfeld vorgenommenen Änderungen und kehrt zum Assistenten zurück.  
  
###  <a name="Summary"></a> Seite "Zusammenfassung"  
 Auf dieser Seite sind die Optionen zusammengefasst, die Sie in diesem Assistenten ausgewählt haben. Um eine Option zu ändern, klicken Sie auf **Zurück**. Um mit der Generierung von Skripts zu beginnen, die gespeichert oder veröffentlicht werden, klicken Sie auf **Weiter**.  
  
 **Überprüfen Sie Ihre Auswahl** – Zeigt die auf den einzelnen Seiten des Assistenten getroffene Auswahl an. Erweitern Sie einen Knoten, um die auf der betreffenden Seite ausgewählten Optionen anzuzeigen.  
  
###  <a name="SavePubScripts"></a> Seite "Skripts speichern oder veröffentlichen"  
 Mithilfe dieser Seite können Sie den Status des Assistenten überwachen.  
  
 **Details** – Zeigen Sie die Spalte **Aktion** an, um den Status des Assistenten anzuzeigen. Nach der Generierung speichert der Assistent die Skripts in einer Datei oder verwendet sie zum Veröffentlichen in einem Webdienst, abhängig von Ihrer Auswahl. Wenn diese Schritte abgeschlossen sind, klicken Sie auf den Wert in der Spalte **Ergebnis** , um das Ergebnis des entsprechenden Schritts anzuzeigen.  
  
 **Bericht speichern** – Klicken Sie hier, um den Status des Assistenten in eine Datei zu speichern.  
  
 **Abbrechen** – Klicken Sie hier, um den Assistenten vor Abschließen der Verarbeitung oder bei Auftreten eines Fehlers zu schließen.  
  
 **Fertig stellen:** Klicken Sie hier, um den Assistenten nach der Verarbeitung oder bei Auftreten eines Fehlers zu schließen.  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von SMO](../server-management-objects-smo/installing-smo.md)   
 [Kopieren von Datenbanken auf andere Server](../databases/copy-databases-to-other-servers.md)  
  
  
