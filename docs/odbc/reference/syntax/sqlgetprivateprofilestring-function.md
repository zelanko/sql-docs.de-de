---
title: SQLGetPrivateProfileString-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77d1f433732cf710e715418df94eba5184e9a907
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53210129"
---
# <a name="sqlgetprivateprofilestring-function"></a>SQLGetPrivateProfileString-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 2.0  
  
 **Zusammenfassung**  
 **SQLGetPrivateProfileString** Ruft eine Liste der Namen von Werten oder Daten, die für den Wert der Systeminformationen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
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
 [Eingabe] Verweist auf eine auf Null endende Zeichenfolge, die den Abschnitt mit den Namen des Schlüssels angibt. Wenn dieses Argument NULL ist, kopiert die Funktion alle Abschnittsnamen in der Datei auf den angegebenen Puffer.  
  
 *lpszEntry*  
 [Eingabe] Verweist auf die Null-terminierte Zeichenfolge, die mit dem Schlüsselnamen, deren zugeordnete Zeichenfolge ist, abgerufen werden sollen. Wenn dieses Argument NULL ist, werden alle Schlüssel Namen im Abschnitt gemäß der *LpszSection* Argument in den vom angegebenen Puffer kopiert werden die *RetBuffer* Argument.  
  
 *lpszDefault*  
 [Eingabe] Verweist auf eine auf Null endende Zeichenfolge, die der Standardwert für den angegebenen Schlüssel gibt an, wenn der Schlüssel in der Initialisierungsdatei nicht gefunden werden kann. Dieses Argument darf nicht NULL sein.  
  
 *RetBuffer*  
 [Ausgabe] Verweist auf den Puffer, der die abgerufene Zeichenfolge empfängt.  
  
 *cbRetBuffer*  
 [Eingabe] Gibt die Größe in Zeichen, der die Puffer, der auf die *RetBuffer* Argument.  
  
 *lpszFilename*  
 [Eingabe] Verweist auf eine auf Null endende Zeichenfolge, die Namen die Initialisierungsdatei. Wenn dieses Argument nicht über einen vollständigen Pfad zu der Datei enthält, wird das Standardverzeichnis durchsucht.  
  
## <a name="returns"></a>Rückgabewert  
 **SQLGetPrivateProfileString** gibt einen ganzzahligen Wert, der die Anzahl der gelesenen Zeichen angibt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn ein Aufruf von **SQLGetPrivateProfileString** ein Fehler auftritt, ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund von unzureichendem Speicher nicht ausgeführt werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLGetPrivateProfileString** dient als eine einfache Möglichkeit, die Port-Treiber und Treiber-Setup-DLLs von Microsoft® Windows® für Microsoft Windows/Windows 2000. Aufrufe von **GetPrivateProfileString über** , abrufen, die eine Profil-Zeichenfolge aus der Datei Odbc.ini werden durch ersetzt sollte Aufrufe von **SQLGetPrivateProfileString**. **SQLGetPrivateProfileString** Aufrufe von Funktionen in der Win32®-API zum Abrufen von Werten oder Daten, die einen Wert des Unterschlüssels Odbc.ini die Systeminformationen für der angeforderten Namen.  
  
 Den Konfigurationsmodus zu wechseln (entsprechend der Festlegung durch **SQLSetConfigMode**) gibt an, in dem der Odbc.ini Eintrag Auflisten von DSN-Werte in den Systeminformationen ist. Wenn der DSN eine Benutzer-DSN ist (der Konfigurationsmodus USERDSN_ONLY), liest die Funktion aus dem Eintrag der Odbc.ini in HKEY_CURRENT_USER. Wenn der DSN eine System-DSN (SYSTEMDSN_ONLY) ist, liest die Funktion aus dem Eintrag der Odbc.ini in HKEY_LOCAL_MACHINE. HKEY_CURRENT_USER wird versucht, wenn der Konfigurationsmodus BOTHDSN ist, und schlägt fehl, HKEY_LOCAL_MACHINE verwendet wird.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Das Schreiben eines Werts, um die Systeminformationen|[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
