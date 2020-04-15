---
title: SQLValidDSN-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLValidDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLValidDSN
helpviewer_keywords:
- SQLValidDSN [ODBC]
ms.assetid: 930d1d89-337a-4429-85a2-84ee10555ac9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6dfafca22d0b04f2147b1af24b53e787493efe67
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286970"
---
# <a name="sqlvaliddsn-function"></a>SQLValidDSN-Funktion
**Konformität**  
 Eingeführte Version: ODBC 2.0  
  
 **Zusammenfassung**  
 **SQLValidDSN** überprüft die Länge und Gültigkeit des Datenquellennamens, bevor der Name zu den Systeminformationen hinzugefügt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLValidDSN(  
     LPCSTR    lpszDSN);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszDSN*  
 [Eingabe] Datenquellenname, der überprüft werden soll.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn der Datenquellenname gültig ist. Es gibt FALSE zurück, wenn der Datenquellenname ungültig ist oder der Funktionsaufruf fehlgeschlagen ist.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLValidDSN** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallerError**aufgerufen wird. Ein * \*pfErrorCode* wird nur zurückgegeben, wenn der Funktionsaufruf fehlgeschlagen ist, nicht, wenn FALSE zurückgegeben wurde, da der Datenquellenname ungültig ist. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLValidDSN** wird vom [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) eines Treibers aufgerufen, um die Länge des Datenquellennamens und die Gültigkeit der einzelnen Zeichen im Datenquellennamen zu überprüfen. Es wird überprüft, ob die Länge des Namens größer als SQL_MAX_DSN_LENGTH ist, wie in Sqlext.h definiert. (Die Länge des Datenquellennamens wird auch von [SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)überprüft.) **SQLValidDSN** überprüft, ob eines der folgenden ungültigen Zeichen im Datenquellennamen enthalten ist:  
  
 [ ] { } ( ) , ; ? * = ! \@ \  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, Ändern oder Entfernen einer Datenquelle|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (in der Setup-DLL)|  
|Hinzufügen, Ändern oder Entfernen einer Datenquelle|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Schreiben eines Datenquellennamens in die Systeminformationen|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
