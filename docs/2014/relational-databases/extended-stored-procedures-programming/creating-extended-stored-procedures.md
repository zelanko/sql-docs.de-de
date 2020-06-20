---
title: Erstellen von erweiterten gespeicherten Prozeduren | Microsoft-Dokumentation
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
ms.openlocfilehash: fcdfcc3ca1999e01b29e7b0c7abdd77f710aae9e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050868"
---
# <a name="creating-extended-stored-procedures"></a>Erstellen erweiterter gespeicherter Prozeduren
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Eine erweiterte gespeicherte Prozedur ist eine Funktion mit einem Prototyp:  
  
 Srvretcode *xp_extendedProcName* **(** srvproc ** \* );**  
  
 Die Verwendung des Präfix xp_ ist optional. Bei den Namen erweiterter gespeicherter Prozeduren wird die Groß-/Kleinschreibung beachtet, wenn in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen auf sie verwiesen wird, und zwar unabhängig von der auf dem Server installierten Codepage/Sortierreihenfolge. Wenn Sie eine DLL erstellen:  
  
-   Wenn ein Einstiegspunkt erforderlich ist, schreiben Sie eine DllMain-Funktion.  
  
     Diese Funktion ist optional; wenn Sie sie nicht im Quellcode angeben, erstellt der Compiler einen Link zu seiner eigenen Version, die keine Aktionen ausführt, außer TRUE zurückzugeben. Wenn Sie eine DllMain-Funktion bereitstellen, ruft das Betriebssystem diese Funktion auf, wenn ein Thread oder ein Prozess mit der DLL verbunden oder von ihr getrennt wird.  
  
-   Alle von außerhalb der DLL aufgerufenen Funktionen (alle e-Funktionen einer erweiterten gespeicherten Prozedur) müssen exportiert werden.  
  
     Sie können eine Funktion exportieren, indem Sie Ihren Namen im Abschnitt Exports einer DEF-Datei auflisten, oder Sie können den Funktionsnamen im Quellcode mit __declspec (dllexport), einer Microsoft-Compilererweiterung, als Präfix versehen (Beachten Sie, dass \_ _declspec () mit zwei unterstrichen beginnt).  
  
 Diese Dateien sind zum Erstellen einer DLL einer erweiterten gespeicherten Prozedur erforderlich.  
  
|Datei|BESCHREIBUNG|  
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
  
 Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit dem Ablaufverfolgungsflag gestartet wird T260 gestartet oder wenn ein Benutzer mit Systemadministrator Berechtigungen DBCC TRACEON (260) ausführt und die dll der erweiterten gespeicherten Prozedur __GetXpVersion () nicht unterstützt, wird eine Warnmeldung (Fehler 8131: die dll "%" der erweiterten gespeicherten Prozedur \_ wird nicht _GetXpVersion ().) in das-Fehlerprotokoll ausgegeben. (Beachten Sie, dass \_ _GetXpVersion () mit zwei unterstrichen beginnt.)  
  
 Wenn die DLL für die erweiterte gespeicherte Prozedur __GetXpVersion() exportiert, die von der Funktion zurückgegebene Version jedoch niedriger ist als die vom Server benötigte Version, wird eine Warnmeldung ausgegeben. Diese gibt die von der Funktion zurückgegebene Version und die vom Server benötigte Version im Fehlerprotokoll an. Wenn Sie diese Meldung erhalten, geben Sie einen falschen Wert aus \_ _GetXpVersion () zurück, oder Sie Kompilieren mit einer älteren Version von SRV. h.  
  
> [!NOTE]  
>  SetErrorMode, eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] Win32 Funktion, sollte in erweiterten gespeicherten Prozeduren nicht aufgerufen werden.  
  
 Es wird empfohlen, dass eine erweiterte gespeicherte Prozedur mit langer Ausführungszeit in regelmäßigen Abständen srv_got_attention aufruft, damit die Prozedur sich selbst beenden kann, falls die Verbindung unterbrochen oder der Batch abgebrochen wird.  
  
 Wenn Sie eine DLL für eine erweiterte gespeicherte Prozedur debuggen möchten, kopieren Sie sie in das Verzeichnis [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\Binn. Wenn Sie die ausführbare Datei für die Debugsitzung angeben möchten, geben Sie den Pfad und den Dateinamen der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausführbaren Datei ein (z. b. c:\Programme\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Sqlservr.exe). Weitere Informationen zu sqlservr-Argumenten finden Sie unter [sqlservr-Anwendung](../../tools/sqlservr-application.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [srv_got_attention &#40;API für erweiterte gespeicherte Prozeduren&#41;](../extended-stored-procedures-reference/srv-got-attention-extended-stored-procedure-api.md)  
  
  
