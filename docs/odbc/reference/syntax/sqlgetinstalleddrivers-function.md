---
title: SQLGetInstalledDrivers-Funktion | Microsoft Docs
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
ms.openlocfilehash: 24793473bf4f25253ac11673df852d10cfb2c558
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303327"
---
# <a name="sqlgetinstalleddrivers-function"></a>SQLGetInstalledDrivers-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0  
  
 **Zusammenfassung**  
 **SQLGetInstalledDrivers** liest den Abschnitt [ODBC Drivers] der Systeminformationen und gibt eine Liste der Beschreibungen der installierten Treiber zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLGetInstalledDrivers(  
     LPSTR   lpszBuf,  
     WORD    cbBufMax,  
     WORD *  pcbBufOut);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszBuf*  
 [Ausgabe] Liste der Beschreibungen der installierten Treiber. Informationen zur Listenstruktur finden Sie unter "Kommentare".  
  
 *cbBufMax*  
 [Eingabe] Länge von *lpszBuf*.  
  
 *pcbBufOut*  
 [Ausgabe] Gesamtanzahl der Bytes (mit Ausnahme des Null-Beendigungsbytes), die in *lpszBuf*zurückgegeben wurden. Wenn die Anzahl der zurückzugebenden Bytes größer oder gleich *cbBufMax*ist, wird die Liste der Treiberbeschreibungen in *lpszBuf* auf *cbBufMax* abzüglich des Null-Beendigungszeichens abgeschnitten. Das *Argument pcbBufOut* kann ein Nullzeiger sein.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetInstalledDrivers** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge|Das *Argument lpszBuf* war NULL oder ungültig, oder das *argument cbBufMax* war kleiner oder gleich 0.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Komponente, die in der Registrierung nicht gefunden wurde|Das Installationsprogramm konnte den Abschnitt [ODBC-Treiber] in der Registrierung nicht finden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 Jede Treiberbeschreibung wird mit einem NULL-Byte beendet, und die gesamte Liste wird mit einem NULL-Byte beendet. (Das heißt, zwei Nullbytes markieren das Ende der Liste.) Wenn der zugewiesene Puffer nicht groß genug ist, um die gesamte Liste aufzunehmen, wird die Liste fehlerfrei abgeschnitten. Ein Fehler wird zurückgegeben, wenn ein Nullzeiger als *lpszBuf*übergeben wird.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Zurückgeben von Treiberbeschreibungen und -attributen|[SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|
