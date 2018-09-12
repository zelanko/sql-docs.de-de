---
title: Warnungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent alerts, event types
- SQL Server Agent alerts, names
- alerts [SQL Server], performance conditions
- alerts [SQL Server], about alerts
- WMI event responses [SQL Server Agent alerts]
- events [WMI]
- performance condition alerts [SQL Server Agent]
- alerts [SQL Server], event types
- SQL Server Agent alerts, performance conditions
- SQL Server Agent alerts, about alerts
- alerts [SQL Server], names
ms.assetid: 3f57d0f0-4781-46ec-82cd-b751dc5affef
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5233e3bcb0ce6b03c754819ead74eef7f014a3d0
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43818506"
---
# <a name="alerts"></a>Warnungen
  Ereignisse werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erzeugt und in das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anwendungsprotokoll geschrieben. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent liest das Anwendungsprotokoll und vergleicht die dort festgehaltenen Ereignisse mit den von Ihnen definierten Warnungen. Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent eine Übereinstimmung findet, wird eine Warnung ausgelöst, also eine automatische Antwort auf das Ereignis. Mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent können Sie nicht nur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ereignisse überwachen, sondern auch den Leistungsstatus und die WMI-Ereignisse (Windows Management Instrumentation oder Windows-Verwaltungsinstrumentation).  
  
 Zur Definition einer Warnung geben Sie Folgendes an:  
  
-   Der Name der Warnung.  
  
-   Das Ereignis oder den Leistungsstatus, mit dem die Warnung ausgelöst wird.  
  
-   Die Aktion, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent als Reaktion auf das Ereignis oder den Leistungsstatus ausführt.  
  
## <a name="naming-an-alert"></a>Benennen einer Warnung  
 Jede Warnung muss einen Namen aufweisen. Warnungsnamen müssen innerhalb der jeweiligen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eindeutig sein und dürfen nicht länger als **128** Zeichen lang sein.  
  
## <a name="selecting-an-event-type"></a>Auswählen eines Ereignistyps  
 Eine Warnung beantwortet ein Ereignis eines bestimmten Typs. Die folgenden Ereignistypen werden mithilfe von Warnungen beantwortet:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Ereignisse  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Leistungsbedingungen  
  
-   WMI-Ereignisse  
  
 Der Typ des Ereignisses bestimmt die Parameter, mit denen Sie das jeweilige Ereignis angeben.  
  
## <a name="specifying-a-sql-server-event"></a>Angeben eines SQL Server-Ereignisses  
 Sie können angeben, dass eine Warnung als Antwort auf ein Ereignis oder mehrere Ereignisse eintritt. Mit den folgenden Parametern geben Sie die Ereignisse an, die eine Warnung auslösen:  
  
-   **Fehlernummer**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent löst eine Warnung aus, wenn ein bestimmter Fehler eintritt. Geben Sie beispielsweise an, dass die Fehlernummer 2571 als Antwort auf den unbefugten Versuch, die Datenbank-Konsolenbefehle (Database Console Commands, DBCC) aufzurufen, ausgegeben werden soll.  
  
-   **Schweregrad**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent löst eine Warnung aus, wenn ein Fehler des bestimmten Schweregrades eintritt. Geben Sie beispielsweise einen Schweregrad von 15 für Syntaxfehler in Transact-SQL-Anweisungen an.  
  
-   **Datenbank**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent löst nur dann eine Warnung aus, wenn das Ereignis in einer bestimmten Datenbank auftritt. Diese Option kann zusätzlich zur Fehlernummer und zum Schweregrad verwendet werden. Enthält eine Instanz beispielsweise eine Datenbank für die Produktion und eine zweite Datenbank für die Berichterstellung, können Sie eine Warnung definieren, die nur bei Syntaxfehlern in der Produktionsdatenbank ausgelöst werden soll.  
  
-   **Fehlermeldungstext**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent löst eine Warnung aus, wenn die Ereignismeldung für das angegebene Ereignis eine bestimmte Textzeichenfolge enthält. Definieren Sie beispielsweise eine Warnung als Antwort auf Meldungen, die den Namen einer bestimmten Tabelle oder Einschränkung enthält.  
  
## <a name="selecting-a-performance-condition"></a>Auswählen einer Leistungsbedingung  
 Sie können Warnungen als Reaktion auf einen bestimmten Leistungsstatus angeben. In diesem Fall geben Sie den zu überwachenden Leistungsindikator, einen Schwellwert für die Warnung sowie das Verhalten des Leistungsindikators, an, bei dem die Warnung ausgelöst werden soll. Zum Festlegen eines Leistungsstatus definieren Sie die folgenden Punkte im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent auf der Seite **Allgemein** im Dialogfeld **Neue Warnung** oder **Eigenschaften von Warnung** :  
  
-   **Objekt**  
  
     Das Objekt stellt den zu überwachenden Leistungsbereich dar.  
  
-   **Leistungsindikator**  
  
     Ein Leistungsindikator ist ein Attribut des zu überwachenden Leistungsbereichs.  
  
-   **Instanz**  
  
     Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz (sofern vorhanden) bestimmt die Instanz des zu überwachenden Attributs.  
  
-   **Warnung, falls Leistungsindikator** und **Wert**  
  
     Der Schwellwert für die Warnung sowie das Verhalten, bei dem die Warnung ausgelöst wird. Der Schwellwert ist ein numerischer Wert. Es liegt eines der **folgenden Verhalten vor: unterschreitet**, **wird gleich**oder **übersteigt eine für den Wert festgelegte Zahl**. Der **Wert** ist eine Zahl, die den Leistungsindikator beschreibt. Soll beispielsweise eine Warnung für das Leistungsobjekt **SQLServer:Sperren** ausgelöst werden, wenn die **Wartezeit für Sperre** länger als 30 Minuten ist, können Sie die Option **übersteigt** verwenden und **die Zahl 30 als Wert**angeben.  
  
     Ein weiteres Beispiel wäre, wenn Sie festlegen, dass eine  Warnung für das Leistungsobjekt **SQLServer:Transactions** ausgegeben wird, wenn der freie Speicherplatz in **tempdb** unter 1000 KB fällt. Um dies festzulegen, wählen Sie den Leistungsindikator **Freier Speicherplatz in 'tempdb' (KB)**, **Unterschreitet**und einen **Wert** von **1000**aus.  
  
    > [!NOTE]  
    >  Leistungsdaten werden in regelmäßigen Abständen geprüft, was zu einer geringfügigen Verzögerung (wenige Sekunden) zwischen dem Erreichen des Schwellwerts und dem Auslösen der Leistungswarnung führen kann.  
  
## <a name="selecting-a-wmi-event"></a>Auswählen eines WMI-Ereignisses  
 Sie können Warnungen als Reaktion auf ein bestimmtes WMI-Ereignis angeben. Zum Auswählen eines WMI-Ereignisses definieren Sie die folgenden Punkte im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent auf der Seite **Allgemein** im Dialogfeld **Neue Warnung** oder **Eigenschaften von Warnung** :  
  
-   **Namespace**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent wird als WMI-Client im WMI-Namespace registriert, der zur Abfrage nach Ereignissen dient.  
  
-   **Abfrage**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent erkennt das angegebene Ereignis mithilfe der WQL-Anweisung (Windows Management Instrumentation Query Language, Abfragesprache der Windows-Verwaltungsinstrumentation).  
  
 Die folgenden Links führen zu häufig anfallenden Aufgaben:  
  
 **So erstellen Sie eine Warnung auf der Grundlage einer Meldungsnummer**  
  
-   [SQL Server Management Studio](create-an-alert-using-an-error-number.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 **So erstellen Sie eine Warnung auf der Grundlage von Schweregraden**  
  
-   [SQL Server Management Studio](create-an-alert-using-severity-level.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 **So erstellen Sie eine Warnung auf der Grundlage eines WMI-Ereignisses**  
  
-   [SQL Server Management Studio](create-a-wmi-event-alert.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 **So definieren Sie die Antwort auf eine Warnung**  
  
-   [SQL Server Management Studio](../sql-server-management-studio-ssms.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
 **So erstellen Sie eine benutzerdefinierte Ereignisfehlermeldung**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql)  
  
 **So ändern Sie eine benutzerdefinierte Ereignisfehlermeldung**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
 **So löschen Sie eine benutzerdefinierte Ereignisfehlermeldung**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-dropmessage-transact-sql)  
  
 **So deaktivieren oder reaktivieren Sie eine Warnung**  
  
-   [SQL Server Management Studio](disable-or-reactivate-an-alert.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von SQL Server-Objekten](../../relational-databases/performance-monitor/use-sql-server-objects.md)  
  
  
