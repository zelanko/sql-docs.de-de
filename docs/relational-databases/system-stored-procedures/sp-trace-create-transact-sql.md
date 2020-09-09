---
description: sp_trace_create (Transact-SQL)
title: sp_trace_create (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_trace_create_TSQL
- sp_trace_create
dev_langs:
- TSQL
helpviewer_keywords:
- sp_trace_create
ms.assetid: f3a43597-4c5a-4520-bcab-becdbbf81d2e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 47e16f40b7cdd9ea9c65d3262487a7a68c8cb6ff
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89547323"
---
# <a name="sp_trace_create-transact-sql"></a>sp_trace_create (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Erstellt eine Ablaufverfolgungsdefinition. Die neue Ablaufverfolgung weist einen beendeten Status auf.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen erweiterte Ereignisse.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_trace_create [ @traceid = ] trace_id OUTPUT   
          , [ @options = ] option_value   
          , [ @tracefile = ] 'trace_file'   
     [ , [ @maxfilesize = ] max_file_size ]  
     [ , [ @stoptime = ] 'stop_time' ]  
     [ , [ @filecount = ] 'max_rollover_files' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @traceid = ] trace_id` Die Zahl, die von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der neuen Ablauf Verfolgung zugewiesen wird. Benutzereingaben werden ignoriert. *trace_id* ist vom Datentyp **int**und hat den Standardwert NULL. Der Benutzer verwendet den *trace_id* Wert, um die von dieser gespeicherten Prozedur definierte Ablauf Verfolgung zu identifizieren, zu ändern und zu steuern.  
  
`[ @options = ] option_value` Gibt die für die Ablauf Verfolgung festgelegten Optionen an. *option_value* ist vom Datentyp **int**und hat keinen Standardwert. Benutzer können eine Kombination dieser Optionen wählen, indem sie den Summenwert der gewünschten Optionen angeben. Wenn Sie z. b. die Optionen TRACE_FILE_ROLLOVER und SHUTDOWN_ON_ERROR aktivieren möchten, geben Sie **6** für *option_value*an.  
  
 In der folgenden Tabelle werden die Optionen, Beschreibungen und die zugehörigen Werte aufgeführt.  
  
|Optionsname|Optionswert|BESCHREIBUNG|  
|-----------------|------------------|-----------------|  
|TRACE_FILE_ROLLOVER|**2**|Gibt an, dass die aktuelle Ablauf Verfolgungs Datei geschlossen und eine neue Datei erstellt wird, wenn der *max_file_size* erreicht wird. Alle neuen Datensätze werden in die neue Datei geschrieben. Die neue Datei hat denselben Namen wie die vorherige Datei, es wird jedoch eine ganze Zahl angehängt, um die zugehörige Reihenfolge anzugeben. Ist z. B. der Name der ursprünglichen Ablaufverfolgungsdatei filename.trc, so wird die nächste Datei mit filename_1.trc benannt, dann folgt filename_2.trc usw.<br /><br /> Wenn weitere Ablaufverfolgungs-Rolloverdateien erstellt werden, erhöht sich der an die Dateinamen angefügte ganzzahlige Wert sequenziell.<br /><br /> SQL Server verwendet den Standardwert *max_file_size* (5 MB), wenn diese Option ohne Angabe eines Werts für *max_file_size*angegeben wird.|  
|SHUTDOWN_ON_ERROR|**4**|Gibt an, dass SQL Server heruntergefahren wird, wenn die Ablaufverfolgung nicht in die Datei geschrieben werden kann, unabhängig vom Grund. Diese Option ist beim Ausführen von Ablaufverfolgungen zur Sicherheitsüberwachung hilfreich.|  
|TRACE_PRODUCE_BLACKBOX|**8**|Gibt an, dass eine Aufzeichnung der letzten 5 MB der Ablaufverfolgungsinformationen, die vom Server erzeugt wurden, von diesem Server gespeichert werden. TRACE_PRODUCE_BLACKBOX ist mit keiner der anderen Optionen kompatibel.|  
  
`[ @tracefile = ] 'trace_file'` Gibt den Speicherort und den Dateinamen an, in den die Ablauf Verfolgung geschrieben wird. *trace_file* ist vom Datentyp **nvarchar (245)** und hat keinen Standardwert. *trace_file* kann entweder ein lokales Verzeichnis (z. b. n ' c:\MSSQL\Trace\trace.trc ') oder eine UNC-Freigabe für eine Freigabe oder einen Pfad (n ' \\ \\ *Servername* \\ *ShareName* \\ *Verzeichnis*\Trace.trc ') sein.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fügt eine **TRC** -Erweiterung an alle Namen von Ablauf Verfolgungs Dateien an. Wenn die TRACE_FILE_ROLLOVER-Option und eine *max_file_size* angegeben werden, wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von eine neue Ablauf Verfolgungs Datei erstellt, wenn die ursprüngliche Ablauf Verfolgungs Datei die maximale Größe erreicht. Die neue Datei hat denselben Namen wie die ursprüngliche Datei, aber _*n* wird angehängt, um die zugehörige Sequenz anzugeben, beginnend mit **1**. Wenn die erste Ablauf Verfolgungs Datei z. b. den Namen **filename. trc**hat, wird die zweite Ablauf Verfolgungs Datei **filename_1. trc**benannt.  
  
 Wenn Sie die Option TRACE_FILE_ROLLOVER verwenden, sollten im ursprünglichen Dateinamen keine Unterstriche enthalten sein. Bei Verwendung von Unterstrichen tritt Folgendes auf:  
  
-   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] wird nicht automatisch geladen oder fordert Sie auf, die Rolloverdateien zu laden (wenn eine dieser dateirolloveroptionen konfiguriert ist).  
  
-   Die fn_trace_gettable-Funktion lädt keine Rolloverdateien (wenn Sie mithilfe des *number_files* -Arguments angegeben wird), wobei der ursprüngliche Dateiname mit einem Unterstrich und einem numerischen Wert endet. (Dies gilt nicht für den Unterstrich und die Zahl, die beim Rollover automatisch angehängt werden.)  
  
> [!NOTE]  
>  Um diese beiden Probleme zu umgehen, können Sie die Dateien umbenennen und die Unterstriche im ursprünglichen Dateinamen entfernen. Wenn die ursprüngliche Datei z **. b. den Namen my_trace. trc**hat und die Rolloverdatei **my_trace_1. trc**benannt ist, können Sie die Dateien in **mytrace. trc** und **mytrace_1. trc** umbenennen, bevor Sie die Dateien in öffnen [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] .  
  
 *trace_file* kann nicht angegeben werden, wenn die TRACE_PRODUCE_BLACKBOX-Option verwendet wird.  
  
`[ @maxfilesize = ] max_file_size` Gibt die maximale Größe in Megabyte (MB) an, die eine Ablauf Verfolgungs Datei vergrößern kann. *max_file_size* ist vom Datentyp **bigint**und hat den Standardwert **5**.  
  
 Wenn dieser Parameter ohne die Option TRACE_FILE_ROLLOVER angegeben wird, beendet die Ablauf Verfolgung die Aufzeichnung in der Datei, wenn der verwendete Speicherplatz den von *max_file_size*angegebenen Wert überschreitet.  
  
`[ @stoptime = ] 'stop_time'` Gibt das Datum und die Uhrzeit an, zu der die Ablauf Verfolgung beendet wird. *stop_time* ist vom **Datentyp DateTime**und hat den Standardwert NULL. Beim Wert NULL wird die Ablaufverfolgung so lange ausgeführt, bis sie manuell beendet oder der Server heruntergefahren wird.  
  
 Wenn sowohl *stop_time* als auch *max_file_size* angegeben sind und TRACE_FILE_ROLLOVER nicht angegeben ist, wird die Ablauf Verfolgung beendet, wenn entweder die angegebene Endzeit oder die maximale Dateigröße erreicht ist. Wenn *stop_time*, *max_file_size*und TRACE_FILE_ROLLOVER angegeben werden, wird die Ablauf Verfolgung zur angegebenen Endzeit angehalten, vorausgesetzt, dass die Ablauf Verfolgung das Laufwerk nicht auffüllen kann.  
  
`[ @filecount = ] 'max_rollover_files'` Gibt die maximale Anzahl oder Ablauf Verfolgungs Dateien an, die mit dem gleichen Basis Dateinamen verwaltet werden sollen. *MAX_ROLLOVER_FILES* ist vom Datentyp **int**, größer als 1. Dieser Parameter ist nur dann gültig, wenn die Option TRACE_FILE_ROLLOVER angegeben wird. Wenn *MAX_ROLLOVER_FILES* angegeben wird, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versucht, nicht mehr als *MAX_ROLLOVER_FILES* Ablauf Verfolgungs Dateien beizubehalten, indem die älteste Ablauf Verfolgungs Datei gelöscht wird, bevor eine neue Ablauf Verfolgungs Datei geöffnet wird. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird das Alter von Ablaufverfolgungsdateien durch das Anfügen einer Nummer an den Basisdateinamen nachverfolgt.  
  
 Wenn der *trace_file* -Parameter z. b. als "c:\mytrace" angegeben wird, ist eine Datei mit dem Namen "c:\ mytrace_123. trc" älter als eine Datei mit dem Namen "c:\ mytrace_124. trc". Wenn *MAX_ROLLOVER_FILES* auf 2 festgelegt ist, löscht SQL Server die Datei "c:\ mytrace_123. trc", bevor die Ablauf Verfolgungs Datei "c:\ mytrace_125. trc" erstellt wird.  
  
 Beachten Sie, dass in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] jede Datei nur einmal zu löschen versucht wird und eine Datei nicht gelöscht werden kann, wenn diese von einem anderen Prozess verwendet wird. Wenn in einer anderen Anwendung Ablaufverfolgungsdateien verwendet werden, während die Ablaufverfolgung ausgeführt wird, werden diese Ablaufverfolgungsdateien daher möglicherweise von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Dateisystem belassen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 In der folgenden Tabelle werden die Codewerte beschrieben, die die Benutzer nach Abschluss der gespeicherten Prozedur möglicherweise erhalten.  
  
|Rückgabecode|Beschreibung|  
|-----------------|-----------------|  
|0|Kein Fehler.|  
|1|Unbekannter Fehler.|  
|10|Ungültige Optionen. Wird zurückgegeben, wenn angegebene Optionen inkompatibel sind.|  
|12|Datei nicht erstellt.|  
|13|Nicht genügend Arbeitsspeicher. Wird zurückgegeben, wenn nicht genügend Arbeitsspeicher zum Ausführen der angegebenen Aktion verfügbar ist.|  
|14|Ungültige Beendigungszeit. Wird zurückgegeben, wenn die angegebene Beendigungszeit bereits verstrichen ist.|  
|15|Ungültige Parameter. Wird zurückgegeben, wenn der Benutzer inkompatible Parameter angegeben hat.|  
  
## <a name="remarks"></a>Hinweise  
 **sp_trace_create** ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherte Prozedur, die viele der zuvor durch **xp_trace_ \* ** erweiterten gespeicherten Prozeduren ausführt, die in früheren Versionen von SQL Server verfügbar waren. Verwenden Sie **sp_trace_create** anstelle von:  
  
-   **xp_trace_addnewqueue**  
  
-   **xp_trace_setqueuecreateinfo**  
  
-   **xp_trace_setqueuedestination**  
  
 **sp_trace_create** erstellt nur eine Ablauf Verfolgungs Definition. Diese gespeicherte Prozedur kann nicht verwendet werden, um eine Ablaufverfolgung zu starten oder zu ändern.  
  
 Parameter aller gespeicherten Prozeduren der SQL-Ablaufverfolgung (**sp_trace_xx**) haben eine strikte Typbindung. Wenn diese Parameter nicht mit den richtigen Datentypen für Eingabeparameter aufgerufen werden, wie in der Argumentbeschreibung angegeben, gibt die gespeicherte Prozedur einen Fehler zurück.  
  
 Für **sp_trace_create**muss das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienst Konto über die Schreib Berechtigung für den Ordner für die Ablauf Verfolgungs Datei verfügen. Wenn das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienstkonto kein Administrator auf dem Computer ist, auf dem die Ablaufverfolgungsdatei gespeichert ist, müssen Sie dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienstkonto explizit die Schreibberechtigung erteilen.  
  
> [!NOTE]  
>  Sie können die mit **sp_trace_create** erstellte Ablauf Verfolgungs Datei mithilfe der **fn_trace_gettable** -Systemfunktion automatisch in eine-Tabelle laden. Weitere Informationen zur Verwendung dieser Systemfunktion finden Sie unter [sys. fn_trace_gettable &#40;Transact-SQL-&#41;](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md).  
  
 Ein Beispiel zum Verwenden gespeicherter Prozeduren der Ablaufverfolgung finden Sie unter [Erstellen einer Ablaufverfolgung &#40;Transact-SQL&#41;](../../relational-databases/sql-trace/create-a-trace-transact-sql.md).  
  
 **TRACE_PRODUCE_BLACKBOX** weist die folgenden Eigenschaften auf:  
  
-   Es handelt sich um eine Rollover-Ablaufverfolgung. Der Standard *file_count* ist 2, kann jedoch vom Benutzer mithilfe der *FileCount* -Option überschrieben werden.  
  
-   Der Standard *file_size* wie bei anderen Ablauf Verfolgungen beträgt 5 MB und kann geändert werden.  
  
-   Es kann kein Dateiname angegeben werden. Die Datei wird gespeichert unter: **N '%SQLDIR%\MSSQL\DATA\blackbox.trc '**  
  
-   Nur die folgenden Ereignisse und deren Spalten sind in der Ablaufverfolgung enthalten:  
  
    -   **RPC-Start**  
  
    -   **BatchStarting**  
  
    -   **Exception**  
  
    -   **Hingewiesen**  
  
-   Für diese Ablaufverfolgung können Ereignisse oder Spalten nicht hinzugefügt oder entfernt werden.  
  
-   Filter können für diese Ablaufverfolgung nicht angegeben werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Benutzer müssen über die ALTER TRACE-Berechtigung verfügen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_trace_generateevent &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [SQL-Ablaufverfolgung](../../relational-databases/sql-trace/sql-trace.md)  
  
  
