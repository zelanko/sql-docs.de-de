---
title: Zählen der Verwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- usage counts [ODBC]
- file usage counts [ODBC]
- installing ODBC components [ODBC], usage counts
- subkeys [ODBC], usage counts
ms.assetid: 0678aee9-8256-463c-89dd-77b1a0dfdd60
author: MightyPen
ms.author: genemi
ms.openlocfilehash: edf9976dd3e5d890b46919808e896a8e81a0cd93
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093794"
---
# <a name="usage-counting"></a>Zählen der Verwendung
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003, ist ODBC in das Windows-Betriebssystem enthalten. Sie sollten nur explizit ODBC in früheren Versionen von Windows installieren.  
  
 Zwei Arten von Verwendungszähler bleiben in der Registrierung für die einzelnen Komponenten: einen Verwendungszähler für die Komponente und eine oder mehrere optionale Datei Verwendungszähler. Die Verwendungsanzahl der Komponente können Sie das Installationsprogramm DLL Registrierungseinträge beizubehalten. Es wird in den UsageCount-Wert unter der ODBC Core, Treiber und Translator Unterschlüsseln gespeichert. Das Format des Werts UsageCount und Weitere Informationen zu folgenden Unterschlüssel, finden Sie unter [Registrierungseinträge für ODBC-Komponenten](../../../odbc/reference/install/registry-entries-for-odbc-components.md).  
  
 Wenn eine Komponente erstmals installiert wird, das Installationsprogramm DLL für sie erstellt und die Daten für den UsageCount-Wert in dieser Unterschlüssel auf 1. Wenn die Komponente erneut installiert wird, erhöht die Installationsprogramm-DLL die Verwendungsanzahl der. Wenn die Komponente entfernt wird, die Installer-DLL-dekrementiert die Nutzung gezählt. Fällt die Verwendungsanzahl der auf 0, werden vom Installationsprogramm-DLL den Unterschlüssel für die Komponente entfernt.  
  
> [!CAUTION]  
>  Eine Anwendung sollte nicht physisch Treiber-Manager-Dateien entfernen, wenn die Verwendungsanzahl der Komponente und die Verwendungsanzahl der Datei 0 (null) erreicht.  
  
 Verwendung der Datei, die Anzahl ermitteln, wenn eine Datei muss tatsächlich kopiert oder gelöscht werden, als dagegen spricht, erhöhen oder verringern die Verwendungsanzahl der. Dies ist wichtig, da der ODBC-Komponenten und die Dateien im ODBC-Komponenten, aus diesem Grund werden gemeinsam genutzt und können installiert oder entfernt werden durch eine Vielzahl von Anwendungen. Die Anwendung kann Treiber und -Übersetzer-Dateien löschen, wenn die Verwendungsanzahl der Komponente und die Verwendungsanzahl der Datei 0 (null) erreicht. Treiber-Manager-Dateien sollten jedoch nicht, werden gelöscht, wenn sowohl "der Verwendungszähler für die Komponente" und "der Verwendungszähler für die Datei auf 0 (null) ist, erreicht haben, da diese Dateien von anderen Anwendungen verwendet werden können, die nicht die Verwendungsanzahl der Datei erhöht haben.  
  
> [!NOTE]  
>  Verwendungszähler für die Datei sind optional in Microsoft® WindowsNT®/Windows 2000.  
  
 Verwendungszähler für die Datei vom Setup-Programm verwaltet werden, nach dem Aufruf **SQLInstallDriverManager**, **SQLInstallDriverEx**, **SQLInstallTranslatorEx**, **SQLRemoveDriverManager**, **SQLRemoveDriver**, oder **SQLRemoveTranslator**.  
  
 Wenn eine Komponente erstmals installiert wird, erstellt der Setup-Programm oder ein Installer DLL einen Wert unter dem folgenden Schlüssel für jede Datei in dieser Komponente, die auf dem System noch nicht vorhanden ist:  
  
> [!NOTE]  
>  HKEY_LOCAL_MACHINE  
>   
>  SOFTWARE  
>   
>  Microsoft  
>   
>  Windows  
>   
>  CurrentVersion  
>   
>  "SharedDlls"  
  
 Es legt die Daten für diese Werte auf 1 fest und kopiert die Datei in das System. Wenn die Komponente erneut installiert wird, wird der Setup-Programm oder die Installationsprogramm-DLL die Verwendungszähler erhöht. Wenn die Komponente entfernt wird, zählt der Setup-Programm oder Installer DLL verringert die Nutzung an. Fällt Verwendungsanzahl auf 0, der Setup-Programm oder die Installationsprogramm-DLL entfernt den Wert für die Datei und, wenn die Komponente einen Treiber oder Übersetzer, ist die Datei gelöscht. Treiber-Manager-Dateien sollten nicht gelöscht werden.  
  
 Das Format von der Anzahl der Wert für die Nutzung ist in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|*full-path*|REG_DWORD|*count*|  
  
 Beispielsweise nehmen wir an, dass ein Treiber für Informix die Infrmx32.dll und Infrmx32.hlp-Dateien verwendet, und nehmen Sie an, dass diese Treiber zweimal installiert wurde. Die Werte unter dem Unterschlüssel "SharedDlls" für den Treiber für Informix würde wie folgt lauten:  
  
```  
C:\WINDOWS\SYSTEM32\INFRMX32.DLL : REG_DWORD : 0x2  
C:\WINDOWS\SYSTEM32\INFRMX32.HLP : REG_DWORD : 0x2  
```
