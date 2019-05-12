---
title: SQLInstallerError-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a0ae475ba4dc290f57eadf94d1e45e8a203a7ce5
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65536599"
---
# <a name="sqlinstallererror-function"></a>SQLInstallerError-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLInstallerError** gibt Fehler oder Status Informationen für die ODBC-Installer-Funktionen zurück.  
  
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
 *iError*  
 [Eingabe] Datensatz-Fehlernummer. Gültige Zahlen sind von 1 bis 8.  
  
 *pfErrorCode*  
 [Ausgabe] Installer-Fehlercode. (Weitere Informationen finden Sie auf "Kommentare".)  
  
 *lpszErrorMsg*  
 [Ausgabe] Zeiger auf Speicher für den Text der Fehlermeldung.  
  
 *cbErrorMsgMax*  
 [Eingabe] Maximale Länge von der *von SQLDiagRec()* Puffer. Dies muss kleiner als oder gleich SQL_MAX_MESSAGE_LENGTH minus der Null-Terminierungszeichen sein.  
  
 *cbErrorMsgMax*  
 [Eingabe] Maximale Länge von der *von SQLDiagRec()* Puffer. Dies muss kleiner als oder gleich SQL_MAX_MESSAGE_LENGTH minus der Null-Terminierungszeichen sein.  
  
 *pcbErrorMsg*  
 [Ausgabe] Zeiger auf die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierungszeichen) zur Verfügung, die in zurückgegeben *LpszErrorMsg*. Wenn die Anzahl der Bytes, die für die Rückgabe verfügbar, größer als oder gleich ist *CbErrorMsgMax*, der Text der Fehlermeldung im *LpszErrorMsg* auf abgeschnitten *CbErrorMsgMax* minus der NULL-Terminierungszeichen Bytes. Die *PcbErrorMsg* Argument kann ein null-Zeiger sein.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, or SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnose  
 **SQLInstallerError** veröffentlichen Fehlerwerte nicht für sich selbst. **SQLInstallerError** gibt SQL_NO_DATA zurück, wenn sie keine Fehlerinformationen abrufen kann (in diesem Fall *PfErrorCode* ist nicht definiert). Wenn **SQLInstallerError** Fehlerwerte kann nicht zugegriffen werden, die aus irgendeinem Grund, die normalerweise SQL_ERROR, zurückgibt **SQLInstallerError** gibt SQL_ERROR zurück, aber alle Fehlerwerte wird nicht gesendet. Wenn Sie nicht, dass die Länge der warnungszeichenfolge wissen (*LpszErrorMsg*), Sie können festlegen, *LpszErrorMsg* auf NULL, und rufen **SQLInstallerError**. **SQLInstallerError** wird zurückzugeben: die Länge der warnungszeichenfolge im *CbErrorMsgMax*. Wenn der Puffer für die Fehlermeldung zu kurz ist **SQLInstallerError** gibt SQL_SUCCESS_WITH_INFO zurück, und die korrekte *PfErrorCode* Wert für **SQLInstallerError**.  
  
 Um zu bestimmen, ob das Abschneiden in der Fehlermeldung aufgetreten ist, kann eine Anwendung vergleichen Sie den Wert in der *CbErrorMsgMax* Argument für die tatsächliche Länge des Texts der geschrieben, um die *PcbErrorMsg* Argument. Wenn abgeschnitten wird, sollte die richtige Pufferlänge zugeordnet werden, für die *LpszErrorMsg* und **SQLInstallerError** erneut aufgerufen werden soll, mit dem entsprechenden *iError*Datensatz.  
  
## <a name="comments"></a>Kommentare  
 Ruft die Anwendung **SQLInstallerError** bei ein vorherigen Aufruf von der ODBC-Installer-Funktion gibt FALSE zurück. ODBC-Funktionen mit dem Setup-Installer und Treiber oder das Konvertierungsprogramm post NULL oder mehr Fehler nur, wenn die Funktion schlägt fehl (gibt "false"); Ruft die Anwendung daher **SQLInstallerError** erst nach eine ODBC-Installer-Funktion ein Fehler auftritt.  
  
 Die ODBC-Installer-Fehlerwarteschlange wird jedes Mal geleert, die eine neue Installer-Funktion aufgerufen wird. Aus diesem Grund kann nicht erwarten, dass eine Anwendung Fehler für Funktionen, die nicht aus dem letzten Aufruf des Installer-Funktion abzurufen.  
  
 Um mehrere Fehler für einen Funktionsaufruf abzurufen, eine Anwendung ruft **SQLInstallerError** mehrmals.  
  
 Wenn es keine zusätzlichen Informationen sind, **SQLInstallerError** SQL_NO_DATA zurückgibt, die *PfErrorCode* Argument ist nicht definiert ist, die *PcbErrorMsg* Argument gleich 0 ist, und die *LpszErrorMsg* -Argument enthält ein einzelnes Zeichen für den Null-Terminierung vorliegt (es sei denn, die *CbErrorMsgMax* Argument gleich 0 ist).
