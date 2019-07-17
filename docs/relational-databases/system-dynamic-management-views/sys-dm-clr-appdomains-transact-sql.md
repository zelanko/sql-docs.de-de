---
title: dm_clr_appdomains (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_clr_appdomains
- sys.dm_clr_appdomains
- dm_clr_appdomains_TSQL
- sys.dm_clr_appdomains_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_appdomains dynamic management dynamic management view
ms.assetid: 9fe0d4fd-950a-4274-a493-85e776278045
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3ebcda61d95cc5131048ab32701d9d68228646ea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138412"
---
# <a name="sysdmclrappdomains-transact-sql"></a>sys.dm_clr_appdomains (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Anwendungsdomäne auf dem Server zurück. Die Anwendungsdomäne (**AppDomain**) ist ein Konstrukt in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common Language Runtime (CLR, der die Einheit der Isolation für eine Anwendung ist). Verwenden Sie diese Ansicht, verstehen und Behandeln von CLR-integrationsobjekte, die in ausgeführt werden [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Es stehen mehrere Typen von CLR-Integrationsobjekten für verwaltete Datenbanken zur Verfügung. Allgemeine Informationen zu diesen Objekten finden Sie unter [Erstellen von Datenbankobjekten mit Integration der Common Language Runtime (CLR)](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md). Wenn diese Objekte ausgeführt werden, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt eine **AppDomain** unter dem sich können, laden, und führen Sie den erforderlichen Code. Die Isolationsstufe für eine **AppDomain** ist eine **AppDomain** pro Datenbank und Besitzer. Alle CLR-Objekte, die im Besitz eines Benutzers werden, also immer ausgeführt, in der gleichen **AppDomain** pro Datenbank (wenn ein Benutzer CLR-Datenbankobjekte in anderen Datenbanken, der CLR-Datenbank, die Objekte in verschiedenen Anwendungsdomänen ausgeführt registriert). Ein **AppDomain** wird nicht zerstört, nachdem der Code die Ausführung abgeschlossen ist. Stattdessen wird sie für die zukünftige Ausführung im Arbeitsspeicher zwischengespeichert. Dies verbessert die Leistung.  
  
 Weitere Informationen finden Sie unter [Anwendungsdomänen](https://go.microsoft.com/fwlink/p/?LinkId=299658).  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**appdomain_address**|**varbinary(8)**|Adresse von der **AppDomain**. Alle verwalteten Objekte im Besitz eines Benutzers immer, in der gleichen geladen werden Datenbank **AppDomain**. Verwenden Sie diese Spalte, um alle in diesem derzeit geladenen Assemblys suchen **AppDomain** in **dm_clr_loaded_assemblies**.|  
|**appdomain_id**|**int**|ID der **AppDomain**. Jede **AppDomain** hat eine eindeutige ID.|  
|**appdomain_name**|**varchar(386)**|Name des der **AppDomain** wie von zugewiesen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**creation_time**|**datetime**|Uhrzeit der Erstellung der **AppDomain** erstellt wurde. Da **AppDomains** zwischengespeichert und wiederverwendet werden, zur Verbesserung der Leistung **Creation_time** ist nicht unbedingt die Zeit, wenn der Code ausgeführt wurde.|  
|**db_id**|**int**|ID der Datenbank, in dem diese **AppDomain** erstellt wurde. Code, die in zwei verschiedenen Datenbanken gespeichert, kann keine gemeinsame **AppDomain**.|  
|**user_id**|**int**|ID des Benutzers an, deren Objekte können in dieser ausführen **AppDomain**.|  
|**state**|**nvarchar(128)**|Ein Deskriptor für den aktuellen Zustand des der **AppDomain**. Eine AppDomain kann sich in verschiedenen Zuständen befinden, von Erstellung bis Löschung. Weitere Informationen finden Sie im Abschnitt "Hinweise" in diesem Thema.|  
|**strong_refcount**|**int**|Anzahl der starken Verweise auf **AppDomain**. Hiermit wird die Anzahl der derzeit ausgeführten Batches, die diesen **AppDomain**. Beachten Sie, dass die Ausführung dieser Ansicht erstellen, wird eine **strong Refcount**; selbst wenn ist derzeit kein Code ausgeführt, **Strong_refcount** wird der Wert 1 haben.|  
|**weak_refcount**|**int**|Anzahl der schwachen Verweise auf **AppDomain**. Dies gibt an, wie viele Objekte der **AppDomain** zwischengespeichert werden. Wenn Sie ein verwaltetes Datenbankobjekt ausführen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] speichert Sie in der **AppDomain** zur späteren Wiederverwendung. Dies verbessert die Leistung.|  
|**cost**|**int**|Kosten für die **AppDomain**. Je höher die Kosten, desto wahrscheinlicher dies **AppDomain** ist mit ungenügendem Arbeitsspeicher entladen wird. Kosten hängen normalerweise wie viel Arbeitsspeicher, zum erneuten Erstellen dieser erforderlich ist **AppDomain**.|  
|**value**|**int**|Der Wert der **AppDomain**. Je niedriger der Wert, desto wahrscheinlicher dies **AppDomain** ist mit ungenügendem Arbeitsspeicher entladen wird. Wert in der Regel hängt wie viele Verbindungen oder Batches diese verwenden **AppDomain**.|  
|**total_processor_time_ms**|**bigint**|Gesamtprozessorzeit in Millisekunden, die von allen Threads beim Ausführen in der aktuellen Anwendungsdomäne ab dem Start des Prozesses verwendet wird. Dies entspricht dem **System.AppDomain.MonitoringTotalProcessorTime**.|  
|**total_allocated_memory_kb**|**bigint**|Gesamtgröße, in Kilobyte, aller Speicherbelegungen durch die Anwendungsdomäne seit der Erstellung, ohne Abzug des bei Sammlungsvorgängen freigegebenen Speichers. Dies entspricht dem **System.AppDomain.MonitoringTotalAllocatedMemorySize**.|  
|**survived_memory_kb**|**bigint**|Menge der Daten in KB, die die letzte vollständige Sammlung mit exklusivem Zugriff überdauert haben, und von denen bekannt ist, dass sie von der aktuellen Anwendungsdomäne referenziert werden. Dies entspricht dem **System.AppDomain.MonitoringSurvivedMemorySize**.|  
  
## <a name="remarks"></a>Hinweise  
 Es gibt eine 1: n-Beziehung zwischen **dm_clr_appdomains** und **appdomain_address**.  
  
 Die folgenden Tabellen Liste möglich **Zustand** Werte, Beschreibungen, und wenn die Zeitpunkte in der **AppDomain** Lebenszyklus. Sie können diese Informationen verwenden, um Lebenszyklus folgen eine **AppDomain** und zum Überwachen verdächtiger oder sich wiederholender **AppDomain** -Instanzen zu achten, ohne dass das Windows-Ereignisprotokoll analysiert werden muss.  
  
## <a name="appdomain-initialization"></a>AppDomain-Initialisierung  
  
|Status|Beschreibung|  
|-----------|-----------------|  
|E_APPDOMAIN_CREATING|Die **AppDomain** erstellt wird.|  
  
## <a name="appdomain-usage"></a>AppDomain-Verwendung  
  
|Status|Beschreibung|  
|-----------|-----------------|  
|E_APPDOMAIN_SHARED|Die Laufzeit **AppDomain** ist für die Verwendung von mehreren Benutzern bereit.|  
|E_APPDOMAIN_SINGLEUSER|Die **AppDomain** ist zur Verwendung in DDL-Vorgängen bereit. Diese unterscheiden sich von E_APPDOMAIN_SHARED, indem im Gegensatz zu DDL-Vorgängen freigegebene AppDomains für die CLR-Integration verwendet werden, . Solche AppDomains werden von anderen gleichzeitigen Vorgängen isoliert.|  
|E_APPDOMAIN_DOOMED|Die **AppDomain** ist geplant, entladen werden, aber es gibt derzeit Threads darin ausgeführt.|  
  
## <a name="appdomain-cleanup"></a>AppDomain-Cleanup  
  
|Status|Beschreibung|  
|-----------|-----------------|  
|E_APPDOMAIN_UNLOADING|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hat angefordert, dass der CLR Entladen der **AppDomain**, in der Regel, da die Assembly, die verwalteten Datenbankobjekte enthält, geändert oder gelöscht wurde.|  
|E_APPDOMAIN_UNLOADED|Die CLR wurde entladen der **AppDomain**. Dies ist normalerweise das Ergebnis einer ausweitungsprozedur aufgrund von **ThreadAbort**, **OutOfMemory**, oder eine nicht behandelte Ausnahme im Benutzercode.|  
|E_APPDOMAIN_ENQUEUE_DESTROY|Die **AppDomain** wurde in CLR entladen und Festlegen von zerstört werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|E_APPDOMAIN_DESTROY|Die **AppDomain** gerade zerstört wird durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|E_APPDOMAIN_ZOMBIE|Die **AppDomain** zerstört wurde von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], aber nicht alle Verweise auf die **AppDomain** wurden bereinigt.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt, wie zum Anzeigen der Details einer **AppDomain** für eine bestimmte Assembly:  
  
```  
select appdomain_id, creation_time, db_id, user_id, state  
from sys.dm_clr_appdomains a  
where appdomain_address =   
(select appdomain_address   
 from sys.dm_clr_loaded_assemblies  
   where assembly_id = 500);  
```  
  
 Das folgende Beispiel zeigt, wie Sie alle Assemblys in einer bestimmten **AppDomain**:  
  
```  
select a.name, a.assembly_id, a.permission_set_desc, a.is_visible, a.create_date, l.load_time   
from sys.dm_clr_loaded_assemblies as l   
inner join sys.assemblies as a  
on l.assembly_id = a.assembly_id  
where l.appdomain_address =   
(select appdomain_address   
from sys.dm_clr_appdomains  
where appdomain_id = 15);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sys.dm_clr_loaded_assemblies &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)   
 [Dynamische Verwaltungssichten in Verbindung mit Common Language Runtime &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  
