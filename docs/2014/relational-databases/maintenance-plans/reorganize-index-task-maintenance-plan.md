---
title: Task „Index neu organisieren“ (Wartungsplan) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.defrag.f1
helpviewer_keywords:
- Reorganize Index Task dialog box
ms.assetid: e9cbebbd-f36f-4176-9832-382a46ac946c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a0f354280da857be236049a564a77716e93cd351
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62807065"
---
# <a name="reorganize-index-task-maintenance-plan"></a>Task 'Index neu organisieren' (Wartungsplan)
  Verwenden Sie das Dialogfeld **reorganizeindex Task** , um Indexseiten in eine effizientere Such Reihenfolge zu verschieben. Dieser Task verwendet die `ALTER INDEX REORGANIZE` -Anweisung mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Datenbanken.  
  
## <a name="options"></a>Tastatur  
 **Verbindung**  
 Wählen Sie die Serververbindung aus, die bei der Ausführung dieses Tasks verwendet werden soll.  
  
 **Neu**  
 Erstellen Sie eine neue Serververbindung, die bei der Ausführung dieses Tasks verwendet werden soll. Das Dialogfeld **Neue Verbindung** wird im Folgenden beschrieben.  
  
 **Datenbanken**  
 Gibt die Datenbanken an, die von dieser Aufgabe betroffen sind.  
  
-   **Alle Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken außer tempdb ausführt.  
  
-   **Alle System Datenbanken**  
  
     Generieren Sie einen Wartungsplan, der Wartungs Tasks für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] System Datenbanken außer **tempdb**ausführt. Für benutzerdefinierte Datenbanken werden keine Wartungstasks ausgeführt.  
  
-   **Alle Benutzer Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks für alle benutzerdefinierten Datenbanken ausführt. Für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Systemdatenbanken werden keine Wartungstasks ausgeführt.  
  
-   **Diese speziellen Datenbanken**  
  
     Generiert einen Wartungsplan, der Wartungstasks nur für die ausgewählten Datenbanken ausführt. Wenn diese Option ausgewählt wird, muss mindestens eine Datenbank in der Liste ausgewählt werden.  
  
 **Object**  
 Begrenzt das Raster **Auswahl** auf die Anzeige von Tabellen, Sichten oder beides.  
  
 **End**  
 Gibt die Tabellen oder Indizes an, auf die sich dieser Task auswirkt. Nicht verfügbar, wenn im Feld **Objekt** die Option **Tabellen und Sichten** ausgewählt ist.  
  
 **Komprimieren von großen Objekten**  
 Hebt die Speicherplatzzuordnung für Tabellen und Sichten nach Möglichkeit auf. Diese Option verwendet `ALTER INDEX LOB_COMPACTION = ON`.  
  
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
  
 **Integrierte Sicherheit von Windows verwenden**  
 Stellen Sie mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung eine Verbindung mit einer Instanz von her.  
  
 **Einen bestimmten Benutzernamen und ein bestimmtes Kennwort verwenden**  
 Stellt mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Authentifizierung eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her. Diese Option ist nicht verfügbar.  
  
 **Benutzername**  
 Stellt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
 **Kennwort**  
 Stellt ein Kennwort für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [DBCC indexdebug &#40;Transact-SQL-&#41;](/sql/t-sql/database-console-commands/dbcc-indexdefrag-transact-sql)  
  
  
