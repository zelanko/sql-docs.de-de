---
description: sp_fulltext_service (Transact-SQL)
title: sp_fulltext_service (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_service
- sp_fulltext_service_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], properties
- sp_fulltext_service
- Full-Text Search Upgrade Option
ms.assetid: 17a91433-f9b6-4a40-88c4-8c704ec2de9f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f29ad11ca5b1df94e445466a5402637a2abab023
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546120"
---
# <a name="sp_fulltext_service-transact-sql"></a>sp_fulltext_service (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Ändert die Servereigenschaften der Volltextsuche für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_fulltext_service [ [@action=] 'action'   
     [ , [ @value= ] value ] ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @action = ] 'action'` Die Eigenschaft, die geändert oder zurückgesetzt werden soll. *Action* ist vom Datentyp **nvarchar (100) und hat** keinen Standardwert. Eine Liste mit den Eigenschaften von*c*tion, deren Beschreibungen und den Werten, die festgelegt werden können, finden Sie in der Tabelle unter dem *value* -Argument. Dieses Argument gibt die folgenden Eigenschaften zurück: Datentyp, aktuell zur Ausführung verwendeter Wert, Minimal- oder Maximalwert und ggf. Status zur Aktualität.  
  
`[ @value = ] value` Der Wert der angegebenen Eigenschaft. der *Wert* ist **sql_variant**. der Standardwert ist NULL. Wenn @value NULL ist, gibt **sp_fulltext_service** die aktuelle Einstellung zurück. In dieser Tabelle werden Aktionseigenschaften, zugehörige Beschreibungen und die festzulegenden Werte aufgelistet.  
  
> [!NOTE]  
>  Die folgenden Aktionen werden in einer zukünftigen Version von entfernt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **clean_up**, **connect_timeout**, **data_timeout**und **resource_usage**. Vermeiden Sie die Verwendung dieser Aktionen bei neuen Entwicklungsarbeiten, und planen Sie die Änderung von Anwendungen, die diese Aktionen zurzeit verwenden.  
  
|Aktion|Datentyp|BESCHREIBUNG|  
|------------|---------------|-----------------|  
|**clean_up**|**int**|Wird nur aus Gründen der Abwärtskompatibilität unterstützt. Der Wert lautet stets 0.|  
|**connect_timeout**|**int**|Wird nur aus Gründen der Abwärtskompatibilität unterstützt. Der Wert lautet stets 0.|  
|**data_timeout**|**int**|Wird nur aus Gründen der Abwärtskompatibilität unterstützt. Der Wert lautet stets 0.|  
|**load_os_resources**|**int**|Gibt an, ob Wörtertrennungen, Wortstammerkennungen und Filter des Betriebssystems mit dieser Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registriert sind und verwendet werden. Enthält einen der folgenden Werte:<br /><br /> 0 = Nur spezifische Filter und Wörtertrennungen für diese Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwenden.<br /><br /> 1 = Betriebssystemfilter und Wörtertrennungen laden.<br /><br /> Standardmäßig ist diese Eigenschaft deaktiviert, damit das Verhalten durch Updates des Systems nicht versehentlich geändert wird. Das Aktivieren der Verwendung von Betriebssystemressourcen ermöglicht den Zugriff auf Ressourcen für Sprachen und Dokumenttypen [!INCLUDE[msCoName](../../includes/msconame-md.md)] , die im Index Dienst registriert sind und auf denen keine instanzspezifische Ressource installiert ist. Wenn Sie das Laden von Betriebssystemressourcen aktivieren, stellen Sie sicher, dass die Betriebssystemressourcen vertrauenswürdige signierte Binärdateien sind; Andernfalls können Sie nicht geladen werden, wenn **verify_signature** (siehe unten) auf 1 festgelegt ist.|  
|**master_merge_dop**|**int**|Gibt die Anzahl der Threads an, die vom Masterzusammenführungsprozess verwendet werden soll. Dieser Wert darf die Anzahl der verfügbaren CPUs oder CPU-Kerne nicht überschreiten.<br /><br /> Wenn dieses Argument nicht angegeben wird, verwendet der Dienst den kleinsten der 4 oder die Anzahl der verfügbaren CPUs oder CPU-Kerne.|  
|**pause_indexing**|**int**|Gibt an, ob die Volltextindizierung angehalten werden soll, wenn sie ausgeführt wird, oder fortgesetzt werden soll, wenn sie angehalten wurde.<br /><br /> 0 = Setzt die Aktivitäten zur Volltextindizierung für die Serverinstanz fort.<br /><br /> 1 = Hält die Aktivitäten zur Volltextindizierung für die Serverinstanz an.|  
|**resource_usage**|**int**|Hat in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höheren Versionen keine Funktion und wird ignoriert.|  
|**update_languages**|NULL|Aktualisiert die Liste der für die Volltextsuche registrierten Sprachen. Die Sprachen werden beim Konfigurieren der Indizierung und in Volltextabfragen angegeben. Filter werden vom Filterdaemonhost verwendet, um Textinformationen aus entsprechenden Dateiformaten wie z. b. ". docx" zu extrahieren, die in Datentypen wie z. b. **varbinary**, **varbinary (max)**, **Image**oder **XML**für die Volltextindizierung gespeichert werden.<br /><br /> Weitere Informationen finden Sie unter [anzeigen oder Ändern von registrierten filtern und Wörtertrennungen](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md).|  
|**upgrade_option**|**int**|Steuert, wie Volltextindizes migriert werden, wenn Sie eine Datenbank von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] auf eine höhere Version aktualisieren. Diese Eigenschaft ist für die folgenden Aktionen gültig: Upgrade durch Anfügen einer Datenbank, Wiederherstellen einer Datenbanksicherung, Wiederherstellen einer Dateisicherung oder Kopieren der Datenbank mit dem Assistenten zum Kopieren von Datenbanken.<br /><br /> Enthält einen der folgenden Werte:<br /><br /> 0 = Volltextkataloge werden mithilfe der neuen und verbesserten Worttrennmodule neu erstellt. Das Neuerstellen von Indizes kann einige Zeit dauern, und nach dem Upgrade ist ggf. eine beträchtliche Menge an CPU-Leistung und Arbeitsspeicherkapazität erforderlich.<br /><br /> 1 = Volltextkataloge werden zurückgesetzt. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Volltextkatalogdateien werden entfernt. Die Metadaten für die Volltextkataloge und die Volltextindizes bleiben jedoch erhalten. Nach der Upgrade wird die Änderungsnachverfolgung für alle Volltextindizes deaktiviert, und Durchforstungen werden nicht automatisch gestartet. Der Katalog bleibt leer, bis Sie ihn nach Beendigung des Upgrades manuell vollständig auffüllen.<br /><br /> 2 = Volltextkataloge werden importiert. Normalerweise ist der Import bedeutend schneller als eine Neuerstellung. Wenn Sie zum Beispiel nur eine CPU verwenden, läuft ein Import etwa zehnmal schneller ab als eine Neuerstellung. Ein importierter Volltextkatalog verwendet jedoch nicht die neuen und erweiterten Wörtertrennungen. Aus diesem Grund sollten Sie zu einem späteren Zeitpunkt eine Neuerstellung der Volltextkataloge durchführen.<br /><br /> Hinweis: die Neuerstellung kann im Multithread-Modus ausgeführt werden. wenn mehr als 10 CPUs verfügbar sind, kann die erneute Erstellung schneller ausgeführt werden als der Import, wenn Sie die Neuerstellung verwenden, um alle CPUs zu verwenden.<br /><br /> Wenn ein Volltextkatalog nicht verfügbar ist, werden die zugehörigen Volltextindizes neu erstellt. Diese Option ist nur für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Datenbanken verfügbar.<br /><br /> Informationen zum Auswählen einer Option für das Volltextupgrade finden Sie unter[Upgrade der Volltextsuche](../../relational-databases/search/upgrade-full-text-search.md).<br /><br /> Hinweis: [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwenden Sie die Eigenschaft **Volltext-Upgradeoption** , um diese Eigenschaft in festzulegen. Weitere Informationen finden Sie unter [Verwalten und Überwachen der Volltextsuche auf einer Serverinstanz](../../relational-databases/search/manage-and-monitor-full-text-search-for-a-server-instance.md).|  
|**verify_signature**|**int**|Gibt an, ob nur signierte Binärdateien von der Volltext-Engine geladen werden. Standardmäßig werden nur vertrauenswürdige signierte Binärdateien geladen.<br /><br /> 1 = Überprüfen, ob ausschließlich vertrauenswürdige signierte Binärdateien geladen werden (Standardeinstellung).<br /><br /> 0 = Nicht überprüfen, ob Binärdateien signiert sind.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der Server Rolle **serveradmin** oder der Systemadministrator können **sp_fulltext_service**ausführen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-updating-the-list-of-registered-languages"></a>A. Aktualisieren der Liste registrierter Sprachen  
 Im folgenden Beispiel wird die Liste der für die Volltextsuche registrierten Sprachen aktualisiert.  
  
```  
EXEC sp_fulltext_service 'update_languages';  
GO  
```  
  
### <a name="b-changing-the-full-text-upgrade-option-to-reset-full-text-catalogs"></a>B. Ändern der Volltext-Upgradeoption, um Volltextkataloge zurückzusetzen  
 Im folgenden Beispiel wird die Volltext-Upgradeoption geändert, sodass Volltextkataloge zurückgesetzt werden. Damit werden die Kataloge vollständig entfernt. In diesem Beispiel werden die optionalen Schlüsselwörter `@action` und `@value` angegeben.  
  
```  
EXEC sp_fulltext_service @action='upgrade_option', @value=1;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Volltextsuche](../../relational-databases/search/full-text-search.md)   
 [FULLTEXTSERVICEPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
