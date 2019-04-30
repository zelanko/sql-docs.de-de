---
title: SQLRemoveDriverManager-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDriverManager
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDriverManager
helpviewer_keywords:
- SQLRemoveDriverManager function function [ODBC]
ms.assetid: 3a41511f-6603-4b81-a815-7883874023c4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4949d84f75483bd4379366621e4a8921d9b4de39
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63186037"
---
# <a name="sqlremovedrivermanager-function"></a>SQLRemoveDriverManager-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0: In Windows XP Service Pack 2, Windows Server 2003 Service Pack 1 und höher veraltet.  
  
 **Zusammenfassung**  
 **SQLRemoveDriverManager** ändert oder Informationen zu den ODBC-Core-Komponenten aus dem Eintrag "Odbcinst.ini" in den Systeminformationen entfernt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BOOL SQLRemoveDriverManager(  
     LPDWORD     pdwUsageCount);  
```  
  
## <a name="arguments"></a>Argumente  
 *pdwUsageCount*  
 [Ausgabe] Die Verwendungsanzahl des Treiber-Managers nach dieser Funktion aufgerufen wurde.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt. Wenn kein Eintrag in den Systeminformationen ist vorhanden, wenn diese Funktion aufgerufen wird, gibt die Funktion "false".  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLRemoveDriverManager** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Komponente wurde in der Registrierung nicht gefunden.|Der Installer konnte nicht die Informationen des Treiber-Manager entfernt, da sie in der Registrierung nicht vorhanden noch oder nicht in der Registrierung gefunden werden konnte.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Konnte nicht inkrementiert oder dekrementiert werden die Verwendungsanzahl der Komponente|Fehler des Installationsprogramms, um die Verwendungsanzahl des Treiber-Managers zu verringern.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund von unzureichendem Speicher nicht ausgeführt werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLRemoveDriverManager** ergänzt die **SQLInstallDriverManager** -Funktion und Updates, die die Verwendung von Komponenten in den Systeminformationen zu zählen. Diese Funktion sollte nur von einem Setup-Anwendung aufgerufen werden.  
  
 **SQLRemoveDriverManager** die Verwendungsanzahl der Core-Komponente wird um 1 verringert wird. Wenn die Anzahl der Zugriffe auf 0 zurückgeht, wird die Systeminformationen Eintrag entfernt werden. Der Eintrag der Core-Komponente ist an folgendem Speicherort in den Systeminformationen, unter dem Titel "ODBC Core":  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
> [!CAUTION]  
>  Eine Anwendung sollte nicht physisch Treiber-Manager-Dateien entfernen, wenn die Verwendungsanzahl der Komponente und die Verwendungsanzahl der Datei 0 (null) erreicht.  
  
 **SQLRemoveDriverManager** Dateien wird nicht tatsächlich entfernt. Das aufrufende Programm ist verantwortlich für das Löschen von Dateien, und zählt, verwalten die Verwendung der Datei. Treiber-Manager-Dateien sollten jedoch nicht, werden entfernt, wenn sowohl "der Verwendungszähler für die Komponente" und "der Verwendungszähler für die Datei auf 0 (null) ist, erreicht haben, da diese Dateien von anderen Anwendungen verwendet werden können, die nicht die Verwendungsanzahl der Datei erhöht haben.  
  
 **SQLRemoveDriverManager** als Teil der Deinstallation aufgerufen wird. ODBC-Komponenten (einschließlich der Treiber-Manager, Cursor-Bibliothek, Installer, Language-Bibliothek, Administrator, thunking Dateien usw.) werden als Ganzes deinstalliert. Die folgenden Dateien werden nicht entfernt wird, wenn **SQLRemoveDriverManager** als Teil der Deinstallation aufgerufen wird:  
  
|||  
|-|-|  
|ODBC32DLL|ODBCCP32.DLL|  
|ODBCCR32.DLL|ODBC16GT.DLL|  
|ODBCCU32.DLL|ODBC32GT.DLL|  
|ODBCINT.DLL|DS16GT.DLL|  
|ODBCTRAC.DLL|DS32GT.DLL|  
|MSVCRT40.DLL|ODBCAD32.EXE|  
|ODBCCP32.CPL||  
  
 **SQLRemoveDriverManager** wird auch als Teil eines Upgradevorgangs bezeichnet. Wenn eine Anwendung erkennt, dass sie ein Upgrade durchführen und den Treiber wurde bereits installierte, sollte der Treiber entfernt und anschließend neu installiert werden.  
  
 **SQLRemoveDriverManager** zuerst aufgerufen werden, um die Verwendungsanzahl der Komponente zu verringern. **SQLInstallDriverEx** dann aufgerufen werden, um die Verwendungsanzahl der Komponente zu erhöhen. Das Installationsprogramm der Anwendung muss die alten Kerndateien Komponente durch die neuen Dateien ersetzen. Die Datei Verwendungszähler bleiben unverändert, und weitere Anwendungen, die ältere Version Komponente Kerndateien verwenden nun die Dateien für die neuere Version.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Installieren einen Treiber-Manager|[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|
