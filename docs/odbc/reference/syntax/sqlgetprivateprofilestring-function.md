---
title: SQLGetPrivateProfileString-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetPrivateProfileString
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetPrivateProfileString
helpviewer_keywords:
- SQLGetPrivateProfileString function [ODBC]
ms.assetid: b72ca065-4d67-48df-baac-e18379a8320a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c12fc8d08535960cbb239c14e017b2ad5faa6c0e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303292"
---
# <a name="sqlgetprivateprofilestring-function"></a>SQLGetPrivateProfileString-Funktion
**Konformität**  
 Eingeführte Version: ODBC 2.0  
  
 **Zusammenfassung**  
 **SQLGetPrivateProfileString** ruft eine Liste mit Namen von Werten oder Daten ab, die einem Wert der Systeminformationen entsprechen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
int SQLGetPrivateProfileString(  
     LPCSTR   lpszSection,  
     LPCSTR   lpszEntry,  
     LPCSTR   lpszDefault,  
     LPCSTR   RetBuffer,  
     INT      cbRetBuffer,  
     LPCSTR   lpszFilename);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszSection*  
 [Eingabe] Verweist auf eine null-terminierte Zeichenfolge, die den Abschnitt angibt, der den Schlüsselnamen enthält. Wenn dieses Argument NULL ist, kopiert die Funktion alle Abschnittsnamen in der Datei in den angegebenen Puffer.  
  
 *lpszEntry*  
 [Eingabe] Verweist auf die null-terminierte Zeichenfolge, die den Schlüsselnamen enthält, dessen zugeordnete Zeichenfolge abgerufen werden soll. Wenn dieses Argument NULL ist, werden alle Schlüsselnamen in dem vom *Argument lpszSection* angegebenen Abschnitt in den durch das *RetBuffer-Argument* angegebenen Puffer kopiert.  
  
 *lpszDefault*  
 [Eingabe] Verweist auf eine null-terminierte Zeichenfolge, die den Standardwert für den angegebenen Schlüssel angibt, wenn der Schlüssel in der Initialisierungsdatei nicht gefunden werden kann. Dieses Argument darf nicht NULL sein.  
  
 *RetBuffer*  
 [Ausgabe] Zeigt auf den Puffer, der die abgerufene Zeichenfolge empfängt.  
  
 *cbRetBuffer*  
 [Eingabe] Gibt die Größe des Puffers in Zeichen an, auf den das *RetBuffer-Argument* zeigt.  
  
 *lpszDateiname*  
 [Eingabe] Verweist auf eine null-terminierte Zeichenfolge, die die Initialisierungsdatei benennt. Wenn dieses Argument keinen vollständigen Pfad zur Datei enthält, wird das Standardverzeichnis durchsucht.  
  
## <a name="returns"></a>Rückgabe  
 **SQLGetPrivateProfileString** gibt einen Ganzzahlwert zurück, der die Anzahl der gelesenen Zeichen angibt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn ein Aufruf von **SQLGetPrivateProfileString** fehlschlägt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallerError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLGetPrivateProfileString** wird als einfache Möglichkeit zum Portieren von Treibern und Treiber-Setup-DLLs von Microsoft® Windows® auf Microsoft Windows NT®/Windows 2000 bereitgestellt. Aufrufe von **GetPrivateProfileString,** die eine Profilzeichenfolge aus der Datei Odbc.ini abrufen, sollten durch Aufrufe von **SQLGetPrivateProfileString**ersetzt werden. **SQLGetPrivateProfileString** ruft Funktionen in der Win32®-API auf, um die angeforderten Namen von Werten oder Daten abzurufen, die einem Wert des Unterschlüssels Odbc.ini der Systeminformationen entsprechen.  
  
 Der Konfigurationsmodus (wie von **SQLSetConfigMode**festgelegt ) gibt an, wo sich der Odbc.ini-Eintrag mit DSN-Werten in den Systeminformationen befindet. Wenn es sich bei dem DSN um einen Benutzer-DSN handelt (der Konfigurationsmodus ist USERDSN_ONLY), liest die Funktion aus dem Eintrag Odbc.ini in HKEY_CURRENT_USER. Wenn es sich bei dem DSN um ein System-DSN (SYSTEMDSN_ONLY) handelt, liest die Funktion aus dem Eintrag Odbc.ini in HKEY_LOCAL_MACHINE. Wenn der Konfigurationsmodus BOTHDSN ist, wird HKEY_CURRENT_USER ausprobiert, und wenn er fehlschlägt, wird HKEY_LOCAL_MACHINE verwendet.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Schreiben eines Werts in die Systeminformationen|[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
