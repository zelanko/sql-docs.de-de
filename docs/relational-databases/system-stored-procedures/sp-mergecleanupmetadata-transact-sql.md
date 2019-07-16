---
title: Sp_mergecleanupmetadata (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_mergecleanupmetadata_TSQL
- sp_mergecleanupmetadata
helpviewer_keywords:
- sp_mergecleanupmetadata
ms.assetid: 892f8628-4cbe-4cc3-b959-ed45ffc24064
author: stevestein
ms.author: sstein
ms.openlocfilehash: ebdc7b55cde31198007e05de1603df7134ed3bfc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020000"
---
# <a name="spmergecleanupmetadata-transact-sql"></a>sp_mergecleanupmetadata (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Sollte verwendet werden, nur in Replikationstopologien mit Servern, auf denen Versionen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 1. **Sp_mergecleanupmetadata** ermöglicht Administratoren das Bereinigen von Metadaten in die **MSmerge_genhistory**, **MSmerge_contents** und **MSmerge_tombstone** -Systemtabellen. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_mergecleanupmetadata [ [ @publication = ] 'publication' ]  
    [ , [ @reinitialize_subscriber = ] 'reinitialize_subscriber' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat den Standardwert **%** , die Metadaten für alle Veröffentlichungen bereinigt. Die Veröffentlichung muss bereits vorhanden sein, wenn sie explizit angegeben wird.  
  
`[ @reinitialize_subscriber = ] 'subscriber'` Gibt an, ob der Abonnent erneut initialisiert werden soll. *Abonnenten* ist **nvarchar(5)** , kann **"true"** oder **"false"** , hat den Standardwert **"true"** . Wenn **"true"** , Abonnements für die erneute Initialisierung gekennzeichnet. Wenn **"false"** , die Abonnements werden nicht für die erneute Initialisierung markiert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_mergecleanupmetadata** sollte verwendet werden, nur in Replikationstopologien mit Servern, auf denen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 1. Topologien mit ausschließlich [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 1 oder höher sollten eine auf Metadatencleanup basierende automatische Beibehaltung verwenden. Beim Ausführen dieser gespeicherten Prozedur müssen Sie beachten, dass die Protokolldatei auf dem Computer, auf dem die gespeicherte Prozedur ausgeführt wird, stark anwachsen kann.  
  
> [!CAUTION]
>  Nach dem **Sp_mergecleanupmetadata** ausgeführt wird, wird standardmäßig alle Abonnements auf den Abonnenten von Veröffentlichungen, die in gespeicherten Metadaten **MSmerge_genhistory**, **' MSmerge_contents '**  und **MSmerge_tombstone** gekennzeichnet sind zur erneuten Initialisierung auf dem Abonnenten alle ausstehenden Änderungen verloren, und die aktuelle Momentaufnahme als veraltet markiert ist.  
> 
> [!NOTE]
>  Wenn mehrere Veröffentlichungen in einer Datenbank vorhanden sind, und eine dieser Veröffentlichungen eine unbegrenzte Beibehaltungsdauer Veröffentlichungen verwendet ( **@retention** =**0**), ausgeführte  **Sp_mergecleanupmetadata** wird nicht bereinigt die Merge-Replikation Metadaten zur änderungsnachverfolgung für die Datenbank. Aus diesem Grund sollten Sie die unbegrenzte Aufbewahrungsdauer für Veröffentlichungen mit Vorsicht verwenden.  
  
 Beim Ausführen dieser gespeicherten Prozedur, können Sie wählen, ob zum erneuten Initialisieren der Abonnenten durch Festlegen der **@reinitialize_subscriber** Parameter **"true"** (Standard) oder **"false"** . Wenn **Sp_mergecleanupmetadata** ausgeführt wird, mit der **@reinitialize_subscriber** Parametersatz zu **"true"** , eine Momentaufnahme wird erneut auf dem Abonnenten angewendet, selbst wenn das Abonnement wurde erstellt, ohne dass eine anfangsmomentaufnahme (z. B., wenn die momentaufnahmedaten und das Schema manuell angewendet oder bereits vorhanden, auf dem Abonnenten war wurden). Festlegen des Parameters auf **"false"** sollte mit Vorsicht, verwendet werden, da, wenn die Veröffentlichung nicht erneut initialisiert wird, müssen Sie sicherstellen, dass die Daten auf dem Verleger und Abonnenten synchronisiert werden.  
  
 Unabhängig vom Wert der **@reinitialize_subscriber** , **Sp_mergecleanupmetadata** schlägt fehl, wenn Sie vorhanden sind Mergeprozesse, die versuchen, Änderungen für einen Wiederveröffentlichungsabonnenten auf einen Verleger hochgeladen werden. der Zeitpunkt, zu die gespeicherte Prozedur aufgerufen wird.  
  
 **Ausführen von Sp_mergecleanupmetadata mit @reinitialize_subscriber = "true":**  
  
1.  Es ist nicht vorgeschrieben, wird jedoch empfohlen, alle Updates der Veröffentlichungs- und Abonnementdatenbanken zu beenden. Falls Updates fortgesetzt werden, gehen alle seit der letzten Zusammenführung beim Abonnenten vorgenommenen Updates beim erneuten Initialisieren der Veröffentlichung verloren. Die Datenkonvergenz bleibt jedoch erhalten.  
  
2.  Ausführen eines Mergeprozesses durch Ausführen des Merge-Agents. Wir empfehlen die Verwendung der **-überprüfen** Befehlszeilenoption Agent auf jedem Abonnenten, wenn Sie den Merge-Agent ausführen. Wenn Sie Mergeprozesse im fortlaufenden Modus ausgeführt werden, finden Sie unter *spezielle Überlegungen zu Mergeprozessen im fortlaufenden Modus* weiter unten in diesem Abschnitt.  
  
3.  Nachdem alle Mergeprozesse abgeschlossen wurden, führen Sie **Sp_mergecleanupmetadata**.  
  
4.  Führen Sie **Sp_reinitmergepullsubscription** auf alle Abonnenten, die benannte oder anonyme Pullabonnements zum Sicherstellen der Datenkonvergenz verwenden.  
  
5.  Wenn Sie Mergeprozesse im fortlaufenden Modus ausgeführt werden, finden Sie unter *spezielle Überlegungen zu Mergeprozessen im fortlaufenden Modus* weiter unten in diesem Abschnitt.  
  
6.  Generieren Sie Snaphotdateien für alle beteiligten Mergeveröffentlichungen auf allen Ebenen erneut. Wenn Sie das Zusammenführen versuchen, ohne die Momentaufnahme zuvor erneut zu generieren, wird eine Eingabeaufforderung angezeigt, die Sie dazu auffordert, die Momentaufnahme erneut zu generieren.  
  
7.  Sichern Sie die Veröffentlichungsdatenbank. Wenn dies versäumt wird, kann es zu einem Mergefehler führen, nachdem die Veröffentlichungsdatenbank wiederhergestellt wurde.  
  
 **Ausführen von Sp_mergecleanupmetadata mit @reinitialize_subscriber = FALSE:**  
  
1.  Beenden Sie **alle** Updates der Veröffentlichungs- und Abonnementdatenbanken.  
  
2.  Ausführen eines Mergeprozesses durch Ausführen des Merge-Agents. Wir empfehlen die Verwendung der **-überprüfen** Befehlszeilenoption Agent auf jedem Abonnenten, wenn Sie den Merge-Agent ausführen. Wenn Sie Mergeprozesse im fortlaufenden Modus ausgeführt werden, finden Sie unter *spezielle Überlegungen zu Mergeprozessen im fortlaufenden Modus* weiter unten in diesem Abschnitt.  
  
3.  Nachdem alle Mergeprozesse abgeschlossen wurden, führen Sie **Sp_mergecleanupmetadata**.  
  
4.  Wenn Sie Mergeprozesse im fortlaufenden Modus ausgeführt werden, finden Sie unter *spezielle Überlegungen zu Mergeprozessen im fortlaufenden Modus* weiter unten in diesem Abschnitt.  
  
5.  Generieren Sie Snaphotdateien für alle beteiligten Mergeveröffentlichungen auf allen Ebenen erneut. Wenn Sie das Zusammenführen versuchen, ohne die Momentaufnahme zuvor erneut zu generieren, wird eine Eingabeaufforderung angezeigt, die Sie dazu auffordert, die Momentaufnahme erneut zu generieren.  
  
6.  Sichern Sie die Veröffentlichungsdatenbank. Wenn dies versäumt wird, kann es zu einem Mergefehler führen, nachdem die Veröffentlichungsdatenbank wiederhergestellt wurde.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

 **Spezielle Überlegungen zu Mergeprozessen im fortlaufenden Modus**  
  
 Wenn Sie Mergeprozesse im fortlaufenden Modus ausführen, müssen Sie einen der folgenden Schritte ausführen:  
  
-   Beenden Sie den Merge-Agent, und führen Sie einen weiteren Mergeprozess ohne die **-Continuous** Parameter wurde angegeben.  
  
-   Deaktivieren Sie die Veröffentlichung mit **Sp_changemergepublication** um sicherzustellen, dass alle Mergeprozesse im fortlaufenden-Modus, die den Veröffentlichungsstatus abrufen.  
  
    ```  
    EXEC central..sp_changemergepublication @publication = 'dynpart_pubn', @property = 'status', @value = 'inactive'  
    ```  
  
 Sie nach Abschluss von Schritt 3 der Ausführung **Sp_mergecleanupmetadata**, Mergeprozesse im fortlaufenden Modus, die basierend auf der Sie sie gestoppt fortsetzen. Führen Sie einen der folgenden Schritte aus:  
  
-   Hinzufügen der **-Continuous** -Parameter für den Merge-Agent zurück.  
  
-   Reaktivieren Sie die Veröffentlichung mit **Sp_changemergepublication.**  
  
    ```  
    EXEC central..sp_changemergepublication @publication = 'dynpart_pubn', @property = 'status', @value = 'active'  
    ```  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_mergecleanupmetadata**.  
  
 Zum Verwenden dieser gespeicherten Prozedur muss der Verleger [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ausführen. Die Abonnenten müssen ausgeführt werden, entweder [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0, Service Pack 2.  
  
## <a name="see-also"></a>Siehe auch  
 [MSmerge_genhistory &#40;Transact-SQL&#41;](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md)   
 [MSmerge_contents &#40;Transact-SQL&#41;](../../relational-databases/system-tables/msmerge-contents-transact-sql.md)   
 [MSmerge_tombstone &#40;Transact-SQL&#41;](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md)  
  
  
