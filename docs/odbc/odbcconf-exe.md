---
title: ODBCCONF. EXE-DATEI | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- odbcconf.exe
ms.assetid: 3bf2be83-61f9-4183-836b-85204ac7116a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33688a46be5e5e33aa940f3553c98db5091b159d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62677370"
---
# <a name="odbcconfexe"></a>ODBCCONF.EXE
ODBCCONF.exe ist ein Befehlszeilentool, das Sie zum Konfigurieren der ODBC-Treiber und Namen von Datenquellen ermöglicht.  
  
> [!NOTE]  
>  ODBCCONF.exe wird in einer zukünftigen Version von Windows Data Access Components entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion, und Planen Sie der Änderung von Anwendungen, die diese Funktion derzeit verwenden. Sie können PowerShell-Befehle verwenden, zum Verwalten von Treibern und Datenquellen. Weitere Informationen zu diesen PowerShell-Befehlen finden Sie unter [Windows Data Access Components Cmdlets](https://technet.microsoft.com/library/hh771019.aspx).  
  
## <a name="syntax"></a>Syntax  
  
```  
ODBCCONF [switches] action  
```  
  
## <a name="arguments"></a>Argumente  
 *switches*  
 NULL oder mehr Switch-Optionen. Die Liste der verfügbaren Befehlszeilenoptionen finden Sie unter im Abschnitt "Hinweise" weiter unten in diesem Thema.  
  
 *action*  
 Eine Aktion ausführen. Die Liste der verfügbaren Optionen finden Sie im Abschnitt "Hinweise".  
  
## <a name="remarks"></a>Hinweise  
 Die folgenden Schalter sind verfügbar:  
  
|Schalter|Description|  
|------------|-----------------|  
|/ A {*Aktion*}|Geben Sie eine Aktion.<br /><br /> / A ist optional, wenn nur eine Aktion angegeben wird.|  
|/?|Syntax für ODBCCONF anzeigen. EXE-DATEI.|  
|/C|Verarbeitung wird fortgesetzt, wenn eine Aktion fehlschlägt.|  
|/E|Löschen Sie die Antwortdatei, die mit/f angegeben wird, wenn die Verarbeitung abgeschlossen ist.|  
|/F|Verwenden Sie eine Antwortdatei, z. B. `odbcconf /F my.rsp`.<br /><br /> My.rsp könnte folgendermaßen aussehen: `REGSVR c:\my.dll`<br /><br /> / A wird nicht in einer Antwortdatei verwendet.|  
|/H|Syntax (Hilfe) anzeigen. Dieser Schalter ist identisch mit /?.|  
|/ L [*Modus*] *Dateiname*|Senden der Ausgabe in eine Datei in einem von drei Modi: Normal (n), ausführliche (V) und Debuggen (d). Debuggen Sie im Modus zeichnet die DLLs, die von odbcconf.exe geladen werden.<br /><br /> Wenn Sie/l ohne einen Modus angeben, wird die Protokolldatei leer sein.<br /><br /> Z. B. **/LV "log.txt"**.|  
|/R|Die Aktion wird nach einem Neustart ausgeführt werden.|  
|/S|Unbeaufsichtigter Modus. Fehlermeldungen werden nicht angezeigt werden.|  
  
 Die folgenden Aktionen sind verfügbar:  
  
|Aktion|Description|  
|------------|-----------------|  
|CONFIGDRIVER *Treibername **-Treiber-spezifische Konfiguration Params*|Lädt die Setup-DLL für geeigneter Treiber und ruft die **ConfigDriver** Funktion.<br /><br /> Entspricht der [SQLConfigDriver-Funktion](../odbc/reference/syntax/sqlconfigdriver-function.md).<br /><br /> Zum Beispiel:<br /><br /> / A {CONFIGDRIVER "Namen des Treibers" "CPTimeout = 60"}<br /><br /> /A {CONFIGDRIVER " Driver Name" "DriverODBCVer=03.80"}|  
|CONFIGDSN *Treibername* DSN =*Namen* &#124; *Attribute*|Fügt oder eine Systemdatenquelle ändert.<br /><br /> Entspricht der [SQLConfigDataSource-Funktion](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Zum Beispiel:<br /><br /> /A {CONFIGDSN "SQL Server" "DSN=name &#124; Server=srv"}|  
|CONFIGSYSDSN *driver_name* DSN=*name* &#124; *attributes*|Fügt oder eine Systemdatenquelle ändert.<br /><br /> Entspricht der [SQLConfigDataSource-Funktion](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Zum Beispiel:<br /><br /> /A {CONFIGSYSDSN "SQL Server" "DSN=name &#124; Server=srv"}|  
|INSTALLDRIVER|Äquivalent zu [SQLInstallDriverEx-Funktion](../odbc/reference/syntax/sqlinstalldriverex-function.md).<br /><br /> Informationen über die Syntax der Schlüsselwort-Wert-Paare an INSTALLDRIVER übergeben, finden Sie unter [Treiberspezifikationen](../odbc/reference/install/driver-specification-subkeys.md).<br /><br /> Zum Beispiel:<br /><br /> /A {INSTALLDRIVER  "Your Driver &#124; Driver=c:\your.dll &#124; Setup=c:\your.dll &#124; APILevel=2 &#124; ConnectFunctions=YYY &#124; DriverODBCVer=03.50 &#124; FileUsage=0 &#124; SQLLevel=1"}|  
|INSTALLTRANSLATOR *Translator Konfiguration ** Treiberpfad*|Fügt Informationen über eine konvertierers, damit die **HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBCINST. INI\ODBC Übersetzer** Registrierungsschlüssel.<br /><br /> Äquivalent zu [SQLInstallTranslatorEx-Funktion](../odbc/reference/syntax/sqlinstalltranslatorex-function.md).<br /><br /> Informationen über die Syntax der Schlüsselwort-Wert-Paare an INSTALLDRIVER übergeben, finden Sie unter [Konvertierungsprogrammspezifikationen](../odbc/reference/install/translator-specification-subkeys.md).<br /><br /> Zum Beispiel:<br /><br /> /A {INSTALLTRANSLATOR  "My Translator &#124; Translator=c:\my.dll &#124; Setup=c:\my.dll"}|  
|REGSVR *dll*|Registriert eine DLL-Datei an.<br /><br /> Äquivalent zu regsvr32.exe.<br /><br /> Zum Beispiel:<br /><br /> /A {REGSVR c:\my.dll}|  
|SETFILEDSNDIR|Wenn HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC. INI\ODBC Datei DSN\DefaultDSNDir ist nicht vorhanden, die SETFILEDSNDIR-Aktion erstellt, und weisen sie den Wert am HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\CommonFilesDir, \ODBC\Data Quellen angefügt.<br /><br /> Der Wert im HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\ODBC. INI\ODBC Datei DSN\DefaultDSNDir gibt es sich um den Standardspeicherort an, die von ODBC-Datenquellen-Administrator verwendet, wenn Sie eine dateibasierte Datenquelle zu erstellen.<br /><br /> Zum Beispiel:<br /><br /> / A {SETFILEDSNDIR}|  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Open Database Connectivity (ODBC)](../odbc/microsoft-open-database-connectivity-odbc.md)
