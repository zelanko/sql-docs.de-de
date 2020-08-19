---
description: SQLInstallerError-Funktion
title: Sqlinstallererror-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallerError
helpviewer_keywords:
- SQLInstallerError [ODBC]
ms.assetid: e6474b79-4d55-458f-81ce-abfafe357f83
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fcc5f89a40802e6efa405771474cda3e86f4519c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421164"
---
# <a name="sqlinstallererror-function"></a>SQLInstallerError-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0  
  
 **Zusammenfassung**  
 **Sqlinstallererror** gibt Fehler-oder Statusinformationen für die ODBC-Installer-Funktionen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
RETCODE SQLInstallerError(  
     WORD      iError,  
     DWORD *   pfErrorCode,  
     LPSTR     lpszErrorMsg,  
     WORD      cbErrorMsgMax,  
     WORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>Argumente  
 *IError*  
 Der Fehler Datensatznummer. Gültige Zahlen liegen zwischen 1 und 8.  
  
 *pferrorcode*  
 Ausgeben Installationsprogramm Fehlercode. (Weitere Informationen finden Sie unter "Kommentare").  
  
 *lpszerrormsg*  
 Ausgeben Zeiger auf den Speicher für den Fehlermeldungs Text.  
  
 *cberrormsgmax*  
 Der Maximale Länge des *szErrorMsg* -Puffers. Dieser Wert muss kleiner oder gleich SQL_MAX_MESSAGE_LENGTH minus dem NULL-Terminierungs Zeichen sein.  
  
 *cberrormsgmax*  
 Der Maximale Länge des *szErrorMsg* -Puffers. Dieser Wert muss kleiner oder gleich SQL_MAX_MESSAGE_LENGTH minus dem NULL-Terminierungs Zeichen sein.  
  
 *pcberrormsg*  
 Ausgeben Ein Zeiger auf die Gesamtzahl der Bytes (ausgenommen des NULL-Beendigungs Zeichens), die in *lpszerrormsg*zurückgegeben werden können. Wenn die Anzahl von Bytes, die zurückgegeben werden können, größer oder gleich *cberrormsgmax*ist, wird der Fehlermeldungs Text in *lpszerrormsg* auf *cberrormsgmax* abzüglich der NULL-Beendigungs Zeichen Bytes abgeschnitten. Das *pcberrormsg* -Argument kann ein NULL-Zeiger sein.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA oder SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnose  
 **Sqlinstallererror** sendet keine Fehler Werte für sich selbst. **Sqlinstallererror** gibt SQL_NO_DATA zurück, wenn keine Fehlerinformationen abgerufen werden können (in diesem Fall ist " *staufrorcode* " nicht definiert). Wenn **sqlinstallererror** aus irgendeinem Grund, der normalerweise SQL_ERROR zurückgeben würde, nicht auf Fehler Werte zugreifen kann, gibt **sqlinstallererror** SQL_ERROR zurück, stellt jedoch keine Fehler Werte bereit. Wenn Sie die Länge der Warnungs Zeichenfolge (*lpszerrormsg*) nicht kennen, können Sie *lpszerrormsg* auf NULL festlegen und **sqlinstallererror**aufzurufen. **Sqlinstallererror** gibt dann die Länge der Warnungs Zeichenfolge in *cberrormsgmax*zurück. Wenn der Puffer für die Fehlermeldung zu kurz ist, gibt **sqlinstallererror** SQL_SUCCESS_WITH_INFO zurück und gibt den korrekten Wert von " *pferrorcode* " für **sqlinstallererror**zurück.  
  
 Um zu ermitteln, ob ein Abschneiden in der Fehlermeldung aufgetreten ist, kann eine Anwendung den Wert im *cberrormsgmax* -Argument mit der tatsächlichen Länge des Nachrichten Texts vergleichen, der in das *pcberrormsg* -Argument geschrieben wurde. Wenn es zu einem Abschneiden kommt, sollte die richtige Pufferlänge für *lpszerrormsg* zugewiesen werden, und **sqlinstallererror** sollte erneut mit dem entsprechenden *IError* -Datensatz aufgerufen werden.  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung ruft **sqlinstallererror** auf, wenn ein vorheriger Aufruf der ODBC-Installationsfunktion false zurückgibt. ODBC Installer-und Treiber-oder Konvertierungs Setup Funktionen stellen NULL oder mehr Fehler nur dann bereit, wenn die Funktion fehlschlägt (gibt false zurück); Daher ruft eine Anwendung **sqlinstallererror** nur auf, wenn eine ODBC-Installationsfunktion fehlschlägt.  
  
 Die Fehler Warteschlange des ODBC-Installers wird bei jedem Aufruf einer neuen Installer-Funktion geleert. Daher kann eine Anwendung nicht erwarten, dass Fehler für andere Funktionen als vom letzten Installer-Funktionsaufrufen abgerufen werden.  
  
 Zum Abrufen mehrerer Fehler für einen Funktionsaufruf Ruft eine Anwendung **sqlinstallererror** mehrmals auf.  
  
 Wenn keine zusätzlichen Informationen vorhanden sind, gibt **sqlinstallererror** SQL_NO_DATA zurück, das " *pferrorcode* "-Argument ist nicht definiert, das *pcberrormsg* -Argument ist gleich "0", und das *lpszerrormsg* -Argument enthält ein einzelnes Null-Beendigungs Zeichen (es sei denn, das *cberrormsgmax* -Argument ist gleich 0).
