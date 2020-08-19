---
description: SQLGetInstalledDrivers-Funktion
title: Sqlgetinstalleddrivers-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetInstalledDrivers
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetInstalledDrivers
helpviewer_keywords:
- SQLGetInstalledDrivers function [ODBC]
ms.assetid: a1983a2e-0edf-422e-bd1b-ec5db40a34bc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0599cb187dee9d3b860f619538b1e0dc148ad58d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421264"
---
# <a name="sqlgetinstalleddrivers-function"></a>SQLGetInstalledDrivers-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0  
  
 **Zusammenfassung**  
 **Sqlgetinstalleddrivers** liest den Abschnitt [ODBC Drivers] der Systeminformationen und gibt eine Liste mit Beschreibungen der installierten Treiber zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLGetInstalledDrivers(  
     LPSTR   lpszBuf,  
     WORD    cbBufMax,  
     WORD *  pcbBufOut);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszbuf*  
 Ausgeben Liste mit Beschreibungen der installierten Treiber. Weitere Informationen zur Listenstruktur finden Sie unter "comments".  
  
 *cbbuf Max*  
 Der Länge von *lpszbuf*.  
  
 *pcbbuf*  
 Ausgeben Die Gesamtanzahl der Bytes (mit Ausnahme des NULL-Terminierungs Byte), die in *lpszbuf*zurückgegeben wurde. Wenn die Anzahl von Bytes, die zurückgegeben werden können, größer oder gleich *cbbufmax*ist, wird die Liste der Treiber Beschreibungen in *lpszbuf* auf *cbbufmax* abzüglich des NULL-Beendigungs Zeichens gekürzt. Das *pcbbuf out* -Argument kann ein NULL-Zeiger sein.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlgetinstalleddrivers** "false" zurückgibt, kann ein zugeordneter " * \* pferrorcode* "-Wert durch Aufrufen von **sqlinstallererror**abgerufen werden. In der folgenden Tabelle sind die " * \* pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge.|Das *lpszbuf* -Argument war NULL oder ungültig, oder das *cbbufmax* -Argument war kleiner als oder gleich 0.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Komponente wurde in der Registrierung nicht gefunden.|Der Installer konnte den Abschnitt [ODBC Drivers] in der Registrierung nicht finden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 Jede Treiber Beschreibung wird mit einem NULL-Byte beendet, und die gesamte Liste wird mit einem NULL-Byte beendet. (Das heißt, zwei NULL-Bytes markieren das Ende der Liste.) Wenn der zugeordnete Puffer nicht groß genug ist, um die gesamte Liste aufzunehmen, wird die Liste ohne Fehler abgeschnitten. Wenn ein NULL-Zeiger als *lpszbuf*übergeben wird, wird ein Fehler zurückgegeben.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zurückgeben von Treiber Beschreibungen und-Attributen|[SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|
