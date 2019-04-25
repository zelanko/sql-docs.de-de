---
title: Erstellen erweiterter gespeicherter Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- warnings [SQL Server]
- extended stored procedures [SQL Server], debugging
- extended stored procedures [SQL Server], creating
- messages [SQL Server], extended stored procedures
ms.assetid: 9f7c0cdb-6d88-44c0-b049-29953ae75717
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 0d0343113b350c48cbc42ec5b79bbd0b849f2860
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62512634"
---
# <a name="creating-extended-stored-procedures"></a>Erstellen erweiterter gespeicherter Prozeduren
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Eine erweiterte gespeicherte Prozedur ist eine Funktion mit einem Prototyp:  
  
 SRVRETCODE *xp_extendedProcName* **(** SRVPROC **\*);**  
  
 Die Verwendung des Präfix xp_ ist optional. Bei den Namen erweiterter gespeicherter Prozeduren wird die Groß-/Kleinschreibung beachtet, wenn in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen auf sie verwiesen wird, und zwar unabhängig von der auf dem Server installierten Codepage/Sortierreihenfolge. Wenn Sie eine DLL erstellen:  
  
-   Wenn ein Einstiegspunkt erforderlich ist, schreiben Sie eine DllMain-Funktion.  
  
     Diese Funktion ist optional; wenn Sie sie nicht im Quellcode angeben, erstellt der Compiler einen Link zu seiner eigenen Version, die keine Aktionen ausführt, außer TRUE zurückzugeben. Wenn Sie eine DllMain-Funktion bereitstellen, ruft das Betriebssystem diese Funktion auf, wenn ein Thread oder ein Prozess mit der DLL verbunden oder von ihr getrennt wird.  
  
-   Alle von außerhalb der DLL aufgerufenen Funktionen (alle e-Funktionen einer erweiterten gespeicherten Prozedur) müssen exportiert werden.  
  
     Sie können eine Funktion exportieren, indem Sie seinen Namen im Abschnitt EXPORTS einer DEF-Datei auflisten, oder Sie können den Funktionsnamen im Quellcode __declspec(dllexport), eine Microsoft-compilererweiterung Präfix (Beachten Sie, dass \__declspec() mit zwei unterstrichen beginnt).  
  
 Diese Dateien sind zum Erstellen einer DLL einer erweiterten gespeicherten Prozedur erforderlich.  
  
|Datei|Description|  
|----------|-----------------|  
|Srv.h|API-Headerdatei für erweiterte gespeicherte Prozeduren|  
|Opends60.lib|Importbibliothek für Opends60.dll|  
  
 Um eine DLL für eine erweiterte gespeicherte Prozedur zu erstellen, erstellen Sie ein Projekt des Typs Dynamic Link Library. Weitere Informationen über das Erstellen einer DLL finden Sie in der Dokumentation zur Entwicklungsumgebung.  
  
 Es wird empfohlen, dass alle DLLs für erweiterte gespeicherte Prozeduren die folgende Funktion implementieren und exportieren:  
  
```  
__declspec(dllexport) ULONG __GetXpVersion()  
{  
   return ODS_VERSION;  
}  
```  
  
> [!NOTE]  
>  __declspec (dllexport) ist eine Microsoft-spezifische Compilererweiterung. Wenn Ihr Compiler diese Direktive nicht unterstützt, sollten Sie diese Funktion in Ihre DEF-Datei im Abschnitt EXPORTS exportieren.  
  
 Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird gestartet, mit dem Ablaufverfolgungsflag flag - T260 oder wenn ein Benutzer mit Systemadministratorprivilegien DBCC TRACEON (260) durchführt und die erweiterte gespeicherte Prozedur-DLL __GetXpVersion() nicht unterstützt, eine Warnmeldung (Fehler 8131: Erweiterte gespeicherte Prozedur-DLL "%" nicht exportiert \__GetXpVersion().) wird im Fehlerprotokoll ausgegeben. (Beachten Sie, dass \__GetXpVersion() mit zwei unterstrichen beginnt.)  
  
 Wenn die DLL für die erweiterte gespeicherte Prozedur __GetXpVersion() exportiert, die von der Funktion zurückgegebene Version jedoch niedriger ist als die vom Server benötigte Version, wird eine Warnmeldung ausgegeben. Diese gibt die von der Funktion zurückgegebene Version und die vom Server benötigte Version im Fehlerprotokoll an. Wenn Sie diese Meldung erhalten, werden Sie einen falschen Wert von zurückgeben \__GetXpVersion(), oder Sie mit einer älteren Version von SRV.h für die Kompilierung kompiliert werden.  
  
> [!NOTE]  
>  SetErrorMode, eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 Funktion, sollte in erweiterten gespeicherten Prozeduren nicht aufgerufen werden.  
  
 Es wird empfohlen, dass eine erweiterte gespeicherte Prozedur mit langer Ausführungszeit in regelmäßigen Abständen srv_got_attention aufruft, damit die Prozedur sich selbst beenden kann, falls die Verbindung unterbrochen oder der Batch abgebrochen wird.  
  
 Wenn Sie eine DLL für eine erweiterte gespeicherte Prozedur debuggen möchten, kopieren Sie sie in das Verzeichnis [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Binn. Um die ausführbare Datei für die Debugsitzung angeben möchten, geben Sie den Pfad und den Namen des der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausführbare Datei (z. B. c:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSSQL12. MSSQLSERVER\MSSQL\Binn\Sqlservr.exe). Weitere Informationen zu Sqlservr-Argumenten finden Sie unter [sqlservr (Anwendung)](../../tools/sqlservr-application.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Srv_got_attention &#40;gespeicherte API für erweiterte Prozeduren&#41;](../extended-stored-procedures-reference/srv-got-attention-extended-stored-procedure-api.md)  
  
  
