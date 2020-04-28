---
title: Verwendungs Zählung | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8d516a591bfde47522c0ccfe08bd2bd706218e07
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296020"
---
# <a name="usage-counting"></a>Zählen der Verwendung
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur in früheren Versionen von Windows explizit installieren.  
  
 Zwei Arten von Verwendungs Anzahlen werden in der Registrierung für jede Komponente verwaltet: eine Anzahl von Komponenten Verwendungs Daten und eine oder mehrere optionale Datei Verwendungs Zähler. Die Anzahl der Komponenten Verwendungs Hilfen ermöglicht der Installer-dll, Registrierungseinträge zu verwalten. Sie wird im Wert usagecount unter den unter Schlüsseln ODBC Core, Driver und Translator gespeichert. Das Format des usagecount-Werts und weitere Informationen zu diesen unter Schlüsseln finden Sie unter [Registrierungseinträge für ODBC-Komponenten](../../../odbc/reference/install/registry-entries-for-odbc-components.md).  
  
 Wenn eine Komponente erstmalig installiert wird, erstellt die Installationsprogramm-dll einen Unterschlüssel dafür und legt die Daten für den Wert usagecount in diesem Unterschlüssel auf 1 fest. Wenn die Komponente erneut installiert wird, erhöht die Installer-dll die Verwendungs Anzahl. Wenn die Komponente entfernt wird, verringert die Installer-dll die Verwendungs Anzahl. Wenn die Verwendungs Anzahl auf 0 (null) fällt, entfernt die Installationsprogramm-dll den Unterschlüssel für die Komponente.  
  
> [!CAUTION]  
>  Treiber-Manager-Dateien sollten von einer Anwendung nicht physisch entfernt werden, wenn die Anzahl der Komponenten und die Anzahl der Datei Nutzung Null erreicht.  
  
 Datei Verwendungs Zähler helfen, zu bestimmen, wann eine Datei tatsächlich kopiert oder gelöscht werden muss, anstatt die Verwendungs Anzahl zu erhöhen oder zu dekrementieren. Dies ist wichtig, da ODBC-Komponenten und somit die Dateien in ODBC-Komponenten gemeinsam genutzt werden und von verschiedenen Anwendungen installiert oder entfernt werden können. Die Anwendung kann Treiber-und Konvertierungs Dateien löschen, wenn die Anzahl der Komponenten Verwendung und die Anzahl der Datei Nutzung Null erreichen. Treiber-Manager-Dateien sollten jedoch nicht gelöscht werden, wenn die Anzahl der Komponenten Verwendung und die Anzahl der Datei Verwendung Null erreicht haben, da diese Dateien von anderen Anwendungen verwendet werden können, die die Anzahl der Datei Auslastung nicht erhöht haben.  
  
> [!NOTE]  
>  Die Anzahl von Datei Verwendungs Anzahlen ist in Microsoft® Windows NT®/Windows2000. optional.  
  
 Die Anzahl von Datei Verwendungs Anzahlen wird durch das Setup Programm verwaltet, nachdem **sqlinstalldrivermanager**, **sqlinstalldriverex**, **sqlinstalltranslatorex**, **sqlremovedrivermanager**, **sqlremovedriver**oder **sqlremovetranslator**aufgerufen wurde.  
  
 Wenn eine Komponente erstmalig installiert wird, erstellt das Setup Programm oder die Installationsprogramm-dll für jede Datei in der Komponente, die sich nicht bereits im System befindet, einen Wert unter dem folgenden Schlüssel:  
  
> [!NOTE]  
>  HKEY_LOCAL_MACHINE  
>   
>  Software  
>   
>  Microsoft  
>   
>  Windows  
>   
>  CurrentVersion  
>   
>  SharedDLLs  
  
 Die Daten für diese Werte werden auf 1 festgelegt, und die Datei wird in das System kopiert. Wenn die Komponente erneut installiert wird, erhöht das Setup Programm oder die Installationsprogramm-dll die Verwendungs Zähler. Wenn die Komponente entfernt wird, verringert das Setup Programm oder die Installationsprogramm-dll die Verwendungs Zähler. Wenn eine Verwendungs Anzahl auf 0 (null) fällt, wird der Wert für die Datei vom Setup Programm oder von der Installationsprogramm-dll entfernt Treiber-Manager-Dateien sollten nicht gelöscht werden.  
  
 Das Format des Werts der Datei Verwendungs Anzahl ist in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|*vollständiger Pfad*|REG_DWORD|*count*|  
  
 Nehmen wir beispielsweise an, dass ein Treiber für Informix die Dateien Infrmx32. dll und Infrmx32. hlp verwendet und dass dieser Treiber zweimal installiert wurde. Die Werte unter dem Unterschlüssel SharedDLLs für den Informix-Treiber lauten wie folgt:  
  
```  
C:\WINDOWS\SYSTEM32\INFRMX32.DLL : REG_DWORD : 0x2  
C:\WINDOWS\SYSTEM32\INFRMX32.HLP : REG_DWORD : 0x2  
```
