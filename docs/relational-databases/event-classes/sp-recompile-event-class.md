---
title: SP:Recompile (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SP:Recompile event class
ms.assetid: 526c8eae-a07b-4d0e-b91e-8e537835d77d
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7d25f529ddc0bb4e7bc3add5189a5ee9aadccad2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85749558"
---
# <a name="sprecompile-event-class"></a>SP:Recompile (Ereignisklasse)
[!INCLUDE [SQL Server - ASDB](../../includes/applies-to-version/sql-asdb.md)]
  Die SP:Recompile-Ereignisklasse gibt an, dass eine gespeicherte Prozedur, ein Trigger oder eine benutzerdefinierte Funktion neu kompiliert wurde. Die von dieser Ereignisklasse gemeldeten Neukompilierungen finden auf der Anweisungsebene statt.  
  
 Die SQL:StmtRecompile-Ereignisklasse stellt die bevorzugte Methode für die Ablaufverfolgung von Neukompilierungen auf Anweisungsebene dar. Die SP:Recompile-Ereignisklasse ist als veraltet markiert. Weitere Informationen finden Sie unter [SQL:StmtRecompile Event Class](../../relational-databases/event-classes/sql-stmtrecompile-event-class.md).  
  
## <a name="sprecompile-event-class-data-columns"></a>Datenspalten der SP:Recompile-Ereignisklasse  
  
|Datenspaltenname|**Datentyp**|BESCHREIBUNG|Column ID|Filterbar|  
|----------------------|-------------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|Dies ist der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|ClientProcessID|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Prozess-ID durch den Client bereitgestellt wird.|9|Ja|  
|DatabaseID|**int**|ID der Datenbank, in der die gespeicherte Prozedur ausgeführt wird. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|DatabaseName|**nvarchar**|Name der Datenbank, in der die gespeicherte Prozedur ausgeführt wird.|35|Ja|  
|EventClass|**int**|Ereignistyp = 37.|27|Nein|  
|EventSequence|**int**|Die Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|EventSubClass|**int**|Der Typ der Ereignisunterklasse. Gibt den Grund für die Neukompilierung an.<br /><br /> 1 = Schema geändert<br /><br /> 2 = Statistiken geändert<br /><br /> 3 = DNR neu kompilieren<br /><br /> 4 = Festgelegte Option geändert<br /><br /> 5 = Temp. Tabelle geändert<br /><br /> 6 = Remoterowset geändert<br /><br /> 7 = FOR BROWSE-Berechtigung geändert<br /><br /> 8 = Abfragebenachrichtigungsumgebung geändert<br /><br /> 9 = MPI-Sicht geändert<br /><br /> 10 = Cursoroptionen geändert<br /><br /> 11 = WITH RECOMPILE-Option|21|Ja|  
|GroupID|**int**|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Ja|  
|HostName|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|IntegerData2|**int**|Endoffset der Anweisung innerhalb der gespeicherten Prozedur oder des Batches, die bzw. der die Neukompilierung verursacht hat. Der Endoffset ist -1, falls die Anweisung die letzte Anweisung im Batch ist.|55|Ja|  
|IsSystem|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|LoginName|**nvarchar**|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Ja|  
|LoginSid|**image**|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|NestLevel|**int**|Die Schachtelungsebene der gespeicherten Prozedur.|29|Ja|  
|NTDomainName|**nvarchar**|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|NTUserName|**nvarchar**|Windows-Benutzername.|6|Ja|  
|ObjectID|**int**|Vom System zugewiesene ID der gespeicherten Prozedur.|22|Ja|  
|ObjectName|**nvarchar**|Der Name des Objekts, das die Neukompilierung ausgelöst hat.|34|Ja|  
|ObjektType|**int**|Der Wert, der den Typ des am Ereignis beteiligten Objekts darstellt. Weitere Informationen finden Sie unter [ObjectType Trace Event Column](../../relational-databases/event-classes/objecttype-trace-event-column.md).|28|Ja|  
|Offset|**int**|Startoffset der Anweisung innerhalb der gespeicherten Prozedur oder des Batches, die bzw. der die Neukompilierung verursacht hat.|61|Ja|  
|RequestID|**int**|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|ServerName|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|SessionLoginName|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie beispielsweise mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und eine Anweisung als Login2 ausführen, zeigt SessionLoginName den Wert Login1 an und LoginName den Wert Login2. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|SPID|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|SqlHandle|**varbinary**|64-Bit-Hash, der auf dem Text einer Ad-hoc-Abfrage oder der Datenbank- und Objekt-ID eines SQL-Objekts basiert. Dieser Wert kann an sys.dm_exec_sql_text übergeben werden, um den zugehörigen SQL-Text abzurufen.|63|Ja|  
|StartTime|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|TextData|**ntext**|Der Text der Transact-SQL-Anweisung, die eine Neukompilierung auf Anweisungsebene verursacht hat.|1|Ja|  
|TransactionID|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
|XactSequence|**bigint**|Token zur Beschreibung der aktuellen Transaktion.|50|Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [SQL:StmtRecompile (Ereignisklasse)](../../relational-databases/event-classes/sql-stmtrecompile-event-class.md)  
  
  
