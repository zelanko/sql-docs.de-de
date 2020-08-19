---
description: SQLGetPrivateProfileString-Funktion
title: Sqlgetprivateprofilestring-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: b2223d46d507df2a9cf82e7feb800caf5b8f82cc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421234"
---
# <a name="sqlgetprivateprofilestring-function"></a>SQLGetPrivateProfileString-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 2,0  
  
 **Zusammenfassung**  
 **Sqlgetprivateprofilestring** Ruft eine Liste mit Namen von Werten oder Daten ab, die einem Wert der Systeminformationen entsprechen.  
  
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
 *lpszsection*  
 Der Verweist auf eine mit NULL endenden Zeichenfolge, die den Abschnitt angibt, der den Schlüsselnamen enthält. Wenn dieses Argument NULL ist, kopiert die-Funktion alle Abschnittsnamen in der Datei in den angegebenen Puffer.  
  
 *lpszentry*  
 Der Verweist auf die auf NULL endende Zeichenfolge, die den Schlüsselnamen enthält, dessen zugehörige Zeichenfolge abgerufen werden soll. Wenn dieses Argument NULL ist, werden alle Schlüsselnamen in dem Abschnitt, der durch das *lpszsection* -Argument angegeben wird, in den Puffer kopiert, der durch das *retbuffer* -Argument angegeben wird.  
  
 *lpszdefault*  
 Der Verweist auf eine auf NULL endende Zeichenfolge, die den Standardwert für den angegebenen Schlüssel angibt, wenn der Schlüssel nicht in der Initialisierungsdatei gefunden werden kann. Dieses Argument darf nicht NULL sein.  
  
 *Retbuffer*  
 Ausgeben Verweist auf den Puffer, der die abgerufene Zeichenfolge empfängt.  
  
 *cbretbuffer*  
 Der Gibt die Größe des Puffers in Zeichen an, auf den das *retbuffer* -Argument zeigt.  
  
 *lpszfilename*  
 Der Verweist auf eine mit NULL endenden Zeichenfolge, die die Initialisierungsdatei benennt. Wenn dieses Argument keinen vollständigen Pfad zur Datei enthält, wird das Standardverzeichnis durchsucht.  
  
## <a name="returns"></a>Rückgabe  
 **Sqlgetprivateprofilestring** gibt einen ganzzahligen Wert zurück, der die Anzahl der gelesenen Zeichen angibt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn ein Aufruf von **sqlgetprivateprofilestring** fehlschlägt, kann ein zugeordneter " * \* pferrorcode* "-Wert durch Aufrufen von " **sqlinstallererror**" abgerufen werden. In der folgenden Tabelle sind die " * \* pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **Sqlgetprivateprofilestring** ist eine einfache Möglichkeit zum Portieren von Treibern und Treiber Setup-DLLs von Microsoft® Windows® an Microsoft Windows NT®/Windows 2000. Aufrufe von **GetPrivateProfileString** , die eine Profil Zeichenfolge aus der Odbc.ini Datei abrufen, sollten durch Aufrufe von **sqlgetprivateprofilestring**ersetzt werden. **Sqlgetprivateprofilestring** Ruft Funktionen in der Win32-®-API auf, um die angeforderten Namen von Werten oder Daten abzurufen, die einem Wert des Odbc.ini unter Schlüssels der Systeminformationen entsprechen.  
  
 Der Konfigurations Modus (wie von **sqlsetconfigmode**festgelegt) gibt an, wo der Odbc.ini Eintrag mit den DSN-Werten in den Systeminformationen steht. Wenn es sich bei dem DSN um einen Benutzer-DSN handelt (der Konfigurations Modus ist USERDSN_ONLY), liest die Funktion aus dem Odbc.ini Eintrag in HKEY_CURRENT_USER. Wenn es sich bei dem DSN um einen System-DSN (SYSTEMDSN_ONLY) handelt, liest die Funktion aus dem Odbc.ini Eintrag in HKEY_LOCAL_MACHINE. Wenn der Konfigurations Modus bothdsn ist, wird HKEY_CURRENT_USER versucht, und wenn er fehlschlägt, wird HKEY_LOCAL_MACHINE verwendet.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Schreiben eines Werts in die Systeminformationen|[Sqlschreiteprivateprofilestring](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
