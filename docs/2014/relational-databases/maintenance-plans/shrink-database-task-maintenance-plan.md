---
title: Task 'Datenbank verkleinern' (Wartungsplan) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.shrink.f1
- Shrink Database Task
- Shrink Database(s) Task
helpviewer_keywords:
- Shrink Database Task dialog box
ms.assetid: a9874cac-cded-4145-9c38-8aafd267dbee
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6f96e45cdf5f94e3e8b71514e1bb3e7ed4d99cfb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62806741"
---
# <a name="shrink-database-task-maintenance-plan"></a>Task 'Datenbank verkleinern' (Wartungsplan)
  Verwenden Sie das Dialogfeld **Task ' Datenbank verkleinern** ', um eine Aufgabe zu erstellen, die versucht, die Größe der ausgewählten Datenbanken zu verringern. Legen Sie mithilfe der folgenden Optionen die Menge des nicht verwendeten Speicherplatzes fest, der in der Datenbank zur Verfügung stehen soll, nachdem diese verkleinert wurde (je höher der Prozentsatz, desto geringer der Spielraum für die Verkleinerung der Datenbank). Der Wert basiert auf dem Prozentsatz der tatsächlichen Daten in der Datenbank. So würde z. B. eine 100-MB-Datenbank mit 60 MB Daten und 40 MB freiem Speicherplatz und einem Prozentsatz von 50 für den freien Speicherplatz zu folgendem Ergebnis führen: 60 MB Daten und 30 MB freier Speicherplatz (da 50 % von 60 MB einen Wert von 30 MB ergibt). Es wird lediglich überschüssiger Speicherplatz aus der Datenbank entfernt. Die gültigen Werte sind 0 bis 100.  
  
 Mit dem Verkleinern von Datendateien wird Platz gewonnen, indem Datenseiten vom Ende der Datei an nicht belegten Platz weiter am Dateianfang verschoben werden. Wurde am Ende der Datei ausreichend Platz geschaffen, kann die Zuordnung der Datenseiten am Ende der Datei aufgehoben und die Datenseiten können ins Dateisystem zurückgegeben werden.  
  
> [!WARNING]  
>  Die zum Verkleinern einer Datei verschobenen Daten können an beliebigen freien Platz in der Datei verschoben werden. Dies führt zur Indexfragmentierung und kann die Leistung von Abfragen, die einen Bereich des Indexes suchen, verlangsamen. Zur Vermeidung von Fragmentierung sollten die Dateiindizes nach der Verkleinerung neu erstellt werden.  
  
 Dieser Task führt die DBCC SHRINKDATABASE-Anweisung aus.  
  
## <a name="options"></a>Tastatur  
 **Verbindung**  
 Wählen Sie die Serververbindung aus, die bei der Ausführung dieses Tasks verwendet werden soll.  
  
 **Neu**  
 Erstellen Sie eine neue Serververbindung, die bei der Ausführung dieses Tasks verwendet werden soll. Das Dialogfeld **Neue Verbindung** wird im Folgenden beschrieben.  
  
 **Datenbanken**  
 Gibt die Datenbanken an, die von dieser Aufgabe betroffen sind.  
  
-   **Alle Datenbanken**  
  
     Generieren Sie einen Wartungsplan, der Wartungs Tasks für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alle Datenbanken mit Ausnahme von tempdb ausführt.  
  
-   **Alle System Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Systemdatenbanken außer tempdb ausführt. Für benutzerdefinierte Datenbanken werden keine Wartungstasks ausgeführt.  
  
-   **Alle Benutzer Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks für alle benutzerdefinierten Datenbanken ausführt. Für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Systemdatenbanken werden keine Wartungstasks ausgeführt.  
  
-   **Diese Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks nur für die ausgewählten Datenbanken ausführt. Wenn diese Option ausgewählt wird, muss mindestens eine Datenbank in der Liste ausgewählt werden.  
  
    > [!NOTE]  
    >  Wartungspläne werden nur für Datenbanken mit Kompatibilitätsgrad 80 oder höher ausgeführt. Datenbanken mit Kompatibilitätsgrad 70 oder niedriger werden nicht angezeigt.  
  
 **Datenbank verkleinern, wenn Sie übersteigt**  
 Gibt die Größe in Megabytes an, die zur Ausführung des Tasks führt.  
  
 **Menge des freien Speicherplatzes nach dem Verkleinern**  
 Beendet das Verkleinern, wenn der freie Speicherplatz in der Datenbankdatei diesen Wert erreicht.  
  
 **T-SQL anzeigen**  
 Zeigt die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen an, die für diesen Task auf dem Server auf Basis der ausgewählten Optionen ausgeführt werden.  
  
> [!NOTE]  
>  Wenn die Anzahl der betroffenen Objekte groß ist, kann die Anzeige erhebliche Zeit in Anspruch nehmen.  
  
## <a name="new-connection-dialog-box"></a>Neue Verbindung (Dialogfeld)  
 **Verbindungs Name**  
 Geben Sie einen Namen für die neue Verbindung ein.  
  
 **Servernamen auswählen oder eingeben**  
 Wählen Sie den Server aus, zu dem bei der Ausführung dieses Tasks eine Verbindung hergestellt werden soll.  
  
 **Aktualisieren**  
 Mithilfe dieser Option aktualisieren Sie die Liste der verfügbaren Server.  
  
 **Geben Sie Informationen ein, um sich beim Server anzumelden.**  
 Legt fest, wie die Authentifizierung gegenüber dem Server stattfindet.  
  
 **Integrierte Sicherheit von Windows NT verwenden**  
 Stellen Sie mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung eine Verbindung mit einer Instanz von her.  
  
 **Einen bestimmten Benutzernamen und ein bestimmtes Kennwort verwenden**  
 Stellt mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Authentifizierung eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her. Diese Option ist nicht verfügbar.  
  
 **Benutzername**  
 Stellt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
 **Kennwort**  
 Stellt ein Kennwort für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [DBCC SHRINKDATABASE &#40;Transact-SQL-&#41;](/sql/t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql)  
  
  
