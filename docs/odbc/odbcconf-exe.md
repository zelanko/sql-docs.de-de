---
title: ODBCCONF. EXE | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d771f01d292312f8a0f0060c16e3c348bf2e009e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307531"
---
# <a name="odbcconfexe"></a>ODBCCONF. EXE
ODBCCONF.exe ist ein Befehlszeilentool, mit dem Sie ODBC-Treiber und Datenquellennamen konfigurieren können.  
  
> [!NOTE]  
>  ODBCCONF.exe wird in einer zukünftigen Version von Windows Data Access Components entfernt. Vermeiden Sie die Verwendung dieser Funktion, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Sie können PowerShell-Befehle verwenden, um Treiber und Datenquellen zu verwalten. Weitere Informationen zu diesen PowerShell-Befehlen finden Sie unter [Windows Data Access Components cmdlets](/powershell/module/wdac).  
  
## <a name="syntax"></a>Syntax  
  
```console  
ODBCCONF [switches] action  
```  
  
## <a name="arguments"></a>Argumente  
 *Schalter*  
 Null oder mehr Schalteroptionen. Die Liste der verfügbaren Switches finden Sie im Abschnitt "Hinweise" weiter unten in diesem Thema.  
  
 *action*  
 Eine auszuführende Aktion. Die Liste der verfügbaren Optionen finden Sie im Abschnitt "Bemerkungen".  
  
## <a name="remarks"></a>Bemerkungen  
 Folgende Schalter sind verfügbar:  
  
|Schalter|Beschreibung|  
|------------|-----------------|  
|/A -*Aktion*|Geben Sie eine Aktion an.<br /><br /> /A ist optional, wenn nur eine Aktion angegeben ist.|  
|/?|Anzeigeverwendung für ODBCCONF. EXE.|  
|/C|Die Verarbeitung wird fortgesetzt, wenn eine Aktion fehlschlägt.|  
|/E|Löschen Sie die Antwortdatei, die mit /F angegeben wurde, wenn die Verarbeitung abgeschlossen ist.|  
|/F|Verwenden Sie eine Antwortdatei, z. `odbcconf /F my.rsp`B. .<br /><br /> my.rsp könnte wie folgt aussehen:`REGSVR c:\my.dll`<br /><br /> /A wird in einer Antwortdatei nicht verwendet.|  
|/H|Anzeigederverwendung (Hilfe). Dieser Schalter ist derselbe wie /?.|  
|/L[*Modus*] *Dateiname*|Senden Sie die Programmausgabe an eine Datei in einem von drei Modi: normal (n), ausführlich (v) und debug (d). Der Debugmodus zeichnet die DLLs auf, die von odbcconf.exe geladen werden.<br /><br /> Wenn Sie /L ohne Modus angeben, ist die Protokolldatei leer.<br /><br /> Beispiel: **/Lv log.txt**.|  
|/R|Die Aktion wird nach einem Neustart ausgeführt.|  
|/S|Unbeaufsichtigter Modus. Keine Fehlermeldungen anzeigen.|  
  
 Die folgenden Aktionen sind verfügbar:  
  
|Aktion|BESCHREIBUNG|  
|------------|-----------------|  
|CONFIGDRIVER *driver_name**treiberspezifische Konfigurationsparams*|Lädt die entsprechende Treiber-Setup-DLL und ruft die **ConfigDriver-Funktion** auf.<br /><br /> Entspricht der [SQLConfigDriver-Funktion](../odbc/reference/syntax/sqlconfigdriver-function.md).<br /><br /> Beispiel:<br /><br /> /A CONFIGDRIVER "Treibername" "CPTimeout=60""<br /><br /> /A CONFIGDRIVER "Treibername" "DriverODBCVer=03.80"|  
|CONFIGDSN *driver_name* DSN=-Name &#124; *Attribute* *name*|Fügt eine Systemdatenquelle hinzu oder ändert sie.<br /><br /> Entspricht der [SQLConfigDataSource-Funktion](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Beispiel:<br /><br /> "DSN=Name &#124; Server=srv"|  
|CONFIGSYSDSN *driver_name* DSN=-Name &#124; *Attribute* *name*|Fügt eine Systemdatenquelle hinzu oder ändert sie.<br /><br /> Entspricht der [SQLConfigDataSource-Funktion](../odbc/reference/syntax/sqlconfigdatasource-function.md).<br /><br /> Beispiel:<br /><br /> /A -CONFIGSYSDSN "SQL Server" "DSN=Name &#124; Server=srv"|  
|INSTALLDRIVER|Entspricht [der SQLInstallDriverEx-Funktion](../odbc/reference/syntax/sqlinstalldriverex-function.md).<br /><br /> Informationen zur Syntax von Schlüsselwort-Wert-Paaren, die an INSTALLDRIVER übergeben wird, finden Sie unter [Driver Specification Subkeys](../odbc/reference/install/driver-specification-subkeys.md).<br /><br /> Beispiel:<br /><br /> /A "Ihr Treiber &#124; Driver=c:'your.dll &#124; Setup=c:'your.dll &#124; APILevel=2 &#124; ConnectFunctions=YYY &#124; DriverODBCVer=03.50 &#124; FileUsage=0 &#124; SQLLevel=1''|  
|*INSTALLTRANSLATOR-Übersetzerkonfiguration**Treiberpfad*|Fügt Informationen zu einem Übersetzer zum **HKEY_LOCAL_MACHINE-SOFTWARE-ODBC-ODBCINST hinzu. Registrierungsschlüssel für INI-ODBC-Übersetzer.**<br /><br /> Entspricht [der SQLInstallTranslatorEx-Funktion](../odbc/reference/syntax/sqlinstalltranslatorex-function.md).<br /><br /> Informationen zur Syntax von Schlüsselwort-Wert-Paaren, die an INSTALLDRIVER übergeben wird, finden Sie unter [Translator Specification Subkeys](../odbc/reference/install/translator-specification-subkeys.md).<br /><br /> Beispiel:<br /><br /> /A "Mein Übersetzer &#124; Übersetzer=c:'my.dll &#124; Setup=c:'my.dll''|  
|REGSVR *dll*|Registriert eine DLL.<br /><br /> Entspricht regsvr32.exe.<br /><br /> Beispiel:<br /><br /> /A-REGSVR c:-my.dll|  
|SETFILEDSNDIR|Wenn HKEY_LOCAL_MACHINE-SOFTWARE-ODBC-ODBC. Die Aktion SETFILEDSNDIR erstellt sie nicht und weist ihr den Wert unter HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-Windows-CurrentVersion-CommonFilesDir zu, der mit dem Anfügen an die Datei "ODBC"-Datenquellen" angehängt wird.<br /><br /> Der Wert bei HKEY_LOCAL_MACHINE-SOFTWARE-ODBC-ODBC. InI-ODBC-Datei DSN-DefaultDSNDir gibt den Standardspeicherort an, der vom ODBC-Datenquellenadministrator beim Erstellen einer dateibasierten Datenquelle verwendet wird.<br /><br /> Beispiel:<br /><br /> /A -SETFILEDSNDIR|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft Open Database Connectivity (ODBC)](../odbc/microsoft-open-database-connectivity-odbc.md)
