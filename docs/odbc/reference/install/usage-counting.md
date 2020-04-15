---
title: Nutzungszählung | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296020"
---
# <a name="usage-counting"></a>Zählen der Verwendung
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur explizit auf früheren Windows-Versionen installieren.  
  
 In der Registrierung werden für jede Komponente zwei Arten von Verwendungszahlen beibehalten: eine Anzahl der Komponentenverwendung und eine oder mehrere optionale Anzahl von Dateiverwendungen. Die Anzahl der Komponentenverwendungen hilft der Installations-DLL, Registrierungseinträge zu verwalten. Sie wird im UsageCount-Wert unter den Unterschlüsseln ODBC Core, Treiber und Übersetzer gespeichert. Informationen zum Format des UsageCount-Werts und weitere Informationen zu diesen Unterschlüsseln finden Sie unter [Registrierungseinträge für ODBC-Komponenten](../../../odbc/reference/install/registry-entries-for-odbc-components.md).  
  
 Wenn eine Komponente zum ersten Mal installiert wird, erstellt die Installations-DLL einen Unterschlüssel dafür und legt die Daten für den UsageCount-Wert in diesem Unterschlüssel auf 1 fest. Wenn die Komponente erneut installiert wird, erhöht die Installations-DLL die Nutzungsanzahl. Wenn die Komponente entfernt wird, dekrementiert die Installations-DLL die Verwendungsanzahl. Wenn die Verwendungsanzahl auf 0 sinkt, entfernt die Installations-DLL den Unterschlüssel für die Komponente.  
  
> [!CAUTION]  
>  Eine Anwendung sollte Driver Manager-Dateien nicht physisch entfernen, wenn die Anzahl der Komponentenverwendung und die Anzahl der Dateiverwendungen Null erreichen.  
  
 Anhand der Dateiverwendung wird ermittelt, wann eine Datei tatsächlich kopiert oder gelöscht werden muss, anstatt die Verwendungsanzahl zu erhöhen oder zu dekrementieren. Dies ist wichtig, da ODBC-Komponenten und damit die Dateien in ODBC-Komponenten gemeinsam genutzt werden und von einer Vielzahl von Anwendungen installiert oder entfernt werden können. Die Anwendung kann Treiber- und Übersetzerdateien löschen, wenn die Anzahl der Komponentenverwendung und die Dateinutzungsanzahl Null erreichen. Treiber-Manager-Dateien sollten jedoch nicht gelöscht werden, wenn sowohl die Anzahl der Komponentenverwendung als auch die Dateinutzungsanzahl Null erreicht haben, da diese Dateien von anderen Anwendungen verwendet werden können, die die Dateinutzungsanzahl nicht erhöht haben.  
  
> [!NOTE]  
>  Die Anzahl der Dateiverwendungen ist in Microsoft® WindowsNT®/Windows2000 optional.  
  
 Die Anzahl der Dateiverwendungen wird vom Setupprogramm verwaltet, nachdem **SQLInstallDriverManager**, **SQLInstallDriverEx**, **SQLInstallTranslatorEx**, **SQLRemoveDriverManager**, **SQLRemoveDriverManager , SQLRemoveDriver**oder **SQLRemoveTranslator**aufgerufen wurden.  
  
 Wenn eine Komponente zum ersten Mal installiert wird, erstellt das Installationsprogramm oder die Installations-DLL einen Wert unter dem folgenden Schlüssel für jede Datei in dieser Komponente, die sich noch nicht auf dem System befindet:  
  
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
>  SharedDlls  
  
 Die Daten für diese Werte werden auf 1 festgelegt und die Datei in das System kopiert. Wenn die Komponente erneut installiert wird, erhöht das Installationsprogramm oder die Installations-DLL die Verwendungszahlen. Wenn die Komponente entfernt wird, dekrementiert das Installationsprogramm oder die Installations-DLL die Verwendungsanzahl. Wenn die Verwendungsanzahl auf 0 fällt, entfernt das Installationsprogramm oder die Installations-DLL den Wert für die Datei und löscht die Datei, wenn es sich bei der Komponente um einen Treiber oder Übersetzer handelt. Treiber-Manager-Dateien sollten nicht gelöscht werden.  
  
 Das Format des Werts für die Anzahl der Dateiverwendungen wird in der folgenden Tabelle angezeigt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|*Full-Path*|REG_DWORD|*count*|  
  
 Angenommen, ein Treiber für Informix verwendet die Dateien Infrmx32.dll und Infrmx32.hlp, und nehmen Sie an, dass dieser Treiber zweimal installiert wurde. Die Werte unter dem Unterschlüssel SharedDlls für den Informix-Treiber lauten wie folgt:  
  
```  
C:\WINDOWS\SYSTEM32\INFRMX32.DLL : REG_DWORD : 0x2  
C:\WINDOWS\SYSTEM32\INFRMX32.HLP : REG_DWORD : 0x2  
```
