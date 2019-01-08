---
title: Lock:Released (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Released event class
ms.assetid: a150c300-72fa-4231-8f41-f1abd550a429
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cf04a73d2ecc100ae5e9b41b5807aa25b05ba32a
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52761642"
---
# <a name="lockreleased-event-class"></a>Lock:Released (Ereignisklasse)
  Die Lock:Released-Ereignisklasse zeigt an, dass eine Sperre einer Ressource, wie z. B. einer Seite, freigegeben wurde.  
  
 Die Ereignisklassen Lock:Acquired und Lock:Released können zum Überwachen verwendet werden, wenn Objekte gesperrt werden, der Sperrentyp bekannt ist und wenn aufgezeichnet wurde, wie lange die Sperren beibehalten wurden. Sperren, die für längere Zeit beibehalten werden, können zu Konflikten führen und sollten untersucht werden. So kann z. B. eine Anwendung Sperren für Zeilen in einer Tabelle erhalten und anschließend auf Benutzereingaben warten. Da bis zur Benutzereingabe längere Zeit vergehen kann, besteht die Möglichkeit, dass die Sperren andere Benutzer blockieren. In diesem Fall sollte die Anwendung geändert werden, damit Sperranforderungen nur bei Bedarf ausgegeben werden und keine Benutzereingaben notwendig sind, wenn Sperren bereits eingerichtet wurden.  
  
## <a name="lock-released-event-class-data-columns"></a>Sperren: Veröffentlicht die Ereignisklassen-Datenspalten  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|BinaryData|`image`|ID der LOCK-Ressource.|2|Ja|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Ja|  
|DatabaseID|`int`|Die ID der Datenbank, in der die Sperre freigegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die ServerName-Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|EventClass|`int`|Ereignistyp = 23.|27|Nein|  
|EventSequence|`int`|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|GroupID|`int`|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Ja|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|IntegerData2|`int`|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|55|Ja|  
|IsSystem|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|LoginName|`nvarchar`|Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Ja|  
|LoginSid|`image`|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|Modus|`int`|Resultierender Modus nach der Freigabe der Sperre.<br /><br /> 0 = NULL - Kompatibel mit allen anderen Sperrmodi (LCK_M_NL)<br /><br /> 1 = Schemastabilitätssperre (LCK_M_SCH_S)<br /><br /> 2 = Schemaänderungssperre (LCK_M_SCH_M)<br /><br /> 3 = Freigegebene Sperre (LCK_M_S)<br /><br /> 4 = Updatesperre (LCK_M_U)<br /><br /> 5 = Exklusive Sperre (LCK_M_X)<br /><br /> 6 = Beabsichtigte freigegebene Sperre (LCK_M_IS)<br /><br /> 7 = Beabsichtigte Updatesperre (LCK_M_IU)<br /><br /> 8 = Beabsichtigte exklusive Sperre (LCK_M_IX)<br /><br /> 9 = Freigegebene Sperre mit beabsichtigter Updatesperre (LCK_M_SIU)<br /><br /> 10 = Freigegebene Sperre mit beabsichtigter exklusiver Sperre (LCK_M_SIX)<br /><br /> 11 = Updatesperre mit beabsichtigter exklusiver Sperre (LCK_M_UIX)<br /><br /> 12 = Massenupdatesperre (LCK_M_BU)<br /><br /> 13 = Freigegebene Sperren für Schlüsselbereich und Ressource (LCK_M_RS_S)<br /><br /> 14 = Freigegebene Sperre für Schlüsselbereich und Updatesperre für Ressource (LCK_M_RS_U)<br /><br /> 15 = Einfügungssperre für Schlüsselbereich und NULL-Sperre für Ressource (LCK_M_RI_NL)<br /><br /> 16 = Einfügungssperre für Schlüsselbereich und freigegebene Ressourcensperre (LCK_M_RI_S)<br /><br /> 17 = Einfügungssperre für Schlüsselbereich und Updatesperre (LCK_M_RI_U)<br /><br /> 18 = Einfügungssperre für Schlüsselbereich und exklusive Ressourcensperre (LCK_M_RI_X)<br /><br /> 19 = Exklusive Sperren für Schlüsselbereich und freigegebene Ressource (LCK_M_RX_S)<br /><br /> 20 = Exklusive Sperren für Schlüsselbereich und Update (LCK_M_RX_U)<br /><br /> 21 = Exklusive Sperren für Schlüsselbereich und Ressource (LCK_M_RX_X)|32|Ja|  
|NTDomainName|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|NTUserName|`nvarchar`|Windows-Benutzername.|6|Ja|  
|ObjectID|`int`|Vom System zugewiesene ID des freigegebenen Objekts (sofern verfüg- und anwendbar).|22|Ja|  
|ObjectID2|`bigint`|Die ID des verbundenen Objekts oder der verbundenen Entität (sofern verfügbar und anwendbar).|56|Ja|  
|OwnerID|`int`|1 = TRANSACTION<br /><br /> 2 = CURSOR<br /><br /> 3 = SESSION<br /><br /> 4 = SHARED_TRANSACTION_WORKSPACE<br /><br /> 5 = EXCLUSIVE_TRANSACTION_WORKSPACE|58|Ja|  
|RequestID|`int`|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|ServerName|`nvarchar`|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|SessionLoginName|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie beispielsweise mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und eine Anweisung als Login2 ausführen, zeigt SessionLoginName den Wert Login1 an und LoginName den Wert Login2. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|SPID|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|StartTime|`datetime`|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|TextData|`ntext`|Textwert, der von der Ereignisklasse abhängt, die in der Ablaufverfolgung aufgezeichnet wurde.|1|Ja|  
|TransactionID|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
|Typ|`int`|1 = NULL_RESOURCE<br /><br /> 2 = DATABASE<br /><br /> 3 = FILE<br /><br /> 5 = OBJECT<br /><br /> 6 = PAGE<br /><br /> 7 = KEY<br /><br /> 8 = EXTENT<br /><br /> 9 = RID<br /><br /> 10 = APPLICATION<br /><br /> 11 = METADATA<br /><br /> 12 = AUTONAMEDB<br /><br /> 13 = HOBT<br /><br /> 14 = ALLOCATION_UNIT|57|Ja|  
  
## <a name="see-also"></a>Siehe auch  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Lock:Acquired (Ereignisklasse)](lock-acquired-event-class.md)   
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql)  
  
  
