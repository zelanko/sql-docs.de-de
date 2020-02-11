---
title: Sqlremovedrivermanager-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: 5cd31a45ed891a8dc95f4f23981d4b626a6095b6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68024537"
---
# <a name="sqlremovedrivermanager-function"></a>SQLRemoveDriverManager-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0: veraltet in Windows XP Service Pack 2, Windows Server 2003 Service Pack 1 und höheren Betriebssystemen.  
  
 **Zusammenfassung**  
 **Sqlremovedrivermanager** ändert oder entfernt Informationen zu den ODBC-Kernkomponenten aus dem Eintrag "Odbcinst. ini" in den Systeminformationen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLRemoveDriverManager(  
     LPDWORD     pdwUsageCount);  
```  
  
## <a name="arguments"></a>Argumente  
 *pdwusagecount*  
 Ausgeben Die Verwendungs Anzahl des Treiber-Managers, nachdem diese Funktion aufgerufen wurde.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false. Wenn in den Systeminformationen kein Eintrag vorhanden ist, wenn diese Funktion aufgerufen wird, gibt die Funktion false zurück.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlremovedrivermanager** false zurückgibt, kann ein zugeordneter " * \*pferrorcode* "-Wert durch Aufrufen von " **sqlinstallererror**" abgerufen werden. In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Komponente wurde in der Registrierung nicht gefunden.|Der Installer konnte die Treiber-Manager-Informationen nicht entfernen, weil er entweder nicht in der Registrierung vorhanden war oder in der Registrierung nicht gefunden wurde.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Die Anzahl der Komponenten Verwendung konnte nicht erhöht oder verringert werden.|Der Installer konnte die Verwendungs Anzahl des Treiber-Managers nicht Dekrementen.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **Sqlremovedrivermanager** ergänzt die **sqlinstalldrivermanager** -Funktion und aktualisiert die Anzahl der Komponenten Verwendung in den Systeminformationen. Diese Funktion sollte nur von einer Setup Anwendung aufgerufen werden.  
  
 **Sqlremovedrivermanager** dekretet die Kernkomponenten Verwendungs Anzahl um 1. Wenn die Anzahl der Komponenten Verwendungs Daten auf 0 (null) sinkt, werden die Informationen zum Eintrags System entfernt. Der Kernkomponenten Eintrag befindet sich an folgendem Speicherort in den Systeminformationen unter dem Titel "ODBC Core":  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
> [!CAUTION]  
>  Treiber-Manager-Dateien sollten von einer Anwendung nicht physisch entfernt werden, wenn die Anzahl der Komponenten und die Anzahl der Datei Nutzung Null erreicht.  
  
 **Sqlremovedrivermanager** entfernt tatsächlich keine Dateien. Das aufrufende Programm ist für das Löschen von Dateien und das Beibehalten der Datei Verwendungs Anzahl zuständig. Treiber-Manager-Dateien sollten jedoch nicht entfernt werden, wenn die Anzahl der Komponenten Verwendung und die Anzahl von Datei Verwendungs Daten Null erreicht haben, da diese Dateien möglicherweise von anderen Anwendungen verwendet werden, die die Datei Verwendungs Anzahl nicht erhöht haben.  
  
 **Sqlremovedrivermanager** wird im Rahmen des Deinstallations Vorgangs aufgerufen. ODBC-Kernkomponenten (einschließlich Treiber-Manager, Cursor Bibliothek, Installer, sprach Bibliothek, Administrator, Thunking-Dateien usw.) werden als Ganzes deinstalliert. Die folgenden Dateien werden nicht entfernt, wenn **sqlremovedrivermanager** im Rahmen des Deinstallations Vorgangs aufgerufen wird:  
  
|||  
|-|-|  
|ODBC32DLL|Datei odbccp32. DLL|  
|ODBCCR32. DLL|ODBC16GT. DLL|  
|ODBCCU32. DLL|ODBC32GT. DLL|  
|Odbcint. DLL|DS16GT. DLL|  
|Odbctrac. DLL|DS32GT. DLL|  
|MSVCRT40. DLL|ODBCAD32. Speichert|  
|Datei odbccp32. CPL||  
  
 **Sqlremovedrivermanager** wird auch als Teil eines Upgradevorgangs aufgerufen. Wenn eine Anwendung erkennt, dass ein Upgrade ausgeführt werden muss, und der Treiber bereits installiert wurde, sollte der Treiber entfernt und dann neu installiert werden.  
  
 **Sqlremovedrivermanager** muss zuerst aufgerufen werden, um die Anzahl von Komponenten Verwendungsraten zu verringern. **Sqlinstalldriverex** sollte dann aufgerufen werden, um die Anzahl von Komponenten Verwendungsraten zu erhöhen. Das Setup Programm der Anwendung muss die alten Kernkomponenten Dateien durch die neuen Dateien ersetzen. Die Anzahl von Datei Verwendungs Anzahlen bleibt unverändert, und andere Anwendungen, die die älteren Versions Kernkomponenten Dateien verwenden, verwenden nun die neueren Versions Dateien.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Installieren eines Treiber-Managers|[Sqlinstalldrivermanager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|
