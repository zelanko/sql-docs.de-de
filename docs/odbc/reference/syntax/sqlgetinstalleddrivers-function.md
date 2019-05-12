---
title: SQLGetInstalledDrivers-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0ff675a184ea0804988972ef10e9a383cdd45230
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537220"
---
# <a name="sqlgetinstalleddrivers-function"></a>SQLGetInstalledDrivers-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 1.0  
  
 **Zusammenfassung**  
 **SQLGetInstalledDrivers** liest den Abschnitt [ODBC Drivers], der die Systeminformationen und gibt eine Liste mit Beschreibungen der installierten Treiber zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLGetInstalledDrivers(  
     LPSTR   lpszBuf,  
     WORD    cbBufMax,  
     WORD *  pcbBufOut);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszBuf*  
 [Ausgabe] Liste mit Beschreibungen der installierten Treiber. Informationen zu den richtigen Listenstruktur finden Sie unter "Kommentare".  
  
 *cbBufMax*  
 [Eingabe] Länge der *LpszBuf*.  
  
 *pcbBufOut*  
 [Ausgabe] Gesamte Anzahl der Bytes, die (mit Ausnahme der Null-Terminierung Byte) in zurückgegebenen *LpszBuf*. Wenn die Anzahl der Bytes, die für die Rückgabe verfügbar, größer als oder gleich ist *CbBufMax*, die Liste der Beschreibungen der Treiber in *LpszBuf* auf abgeschnitten *CbBufMax* minus der NULL-Terminierungszeichen. Die *PcbBufOut* Argument kann ein null-Zeiger sein.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLGetInstalledDrivers** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge.|Die *LpszBuf* -Argument war NULL oder ungültig, oder die *CbBufMax* Argument war kleiner als oder gleich 0.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Komponente wurde in der Registrierung nicht gefunden.|Das Installationsprogramm wurde im Abschnitt [ODBC Drivers] in der Registrierung nicht gefunden werden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund von unzureichendem Speicher nicht ausgeführt werden.|  
  
## <a name="comments"></a>Kommentare  
 Die Beschreibungen der Treiber wird mit null Byte beendet, und die gesamte Liste wird mit null Byte beendet. (D. h., markieren Sie zwei null-Bytes am Ende der Liste.) Wenn es sich bei der zugeordnete Puffer nicht groß genug für die gesamte Liste ist, wird die Liste ohne Fehler abgeschnitten. Wenn ein null-Zeiger als übergeben wird, wird ein Fehler zurückgegeben. *LpszBuf*.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Zurückgeben von Beschreibungen der Treiber und Attribute|[SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|
