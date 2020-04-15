---
title: Kompatibilitätsmatrix | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
- application compatibility issues [ODBC]
- application upgrades [ODBC], compatibility matrix
- upgrading applications [ODBC], compatibility matrix
ms.assetid: 0690b463-15a1-48fa-9d0b-9cc9e5bf7fc6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0406599e1657a900d1669861572ff13834cec670
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307453"
---
# <a name="compatibility-matrix"></a>Kompatibilitätsmatrix
In der folgenden Tabelle wird die Kompatibilität der zuvor in diesem Abschnitt definierten Anwendungstypen und Treiber beschrieben.  
  
|Anwendungstyp<br /><br /> und Version|32-Bit ODBC<br /><br /> *2.x* Treiber|ODBC *3.x*<br /><br /> Treiber|ODBC 3.8-Treiber|ISO- und Open Group-konformer Treiber|  
|--------------------------------------|-----------------------------------|---------------------------|---------------------|-----------------------------------------|  
|16-Bit-Anwendung, jede Version|Kompatibel|Kompatibel|Kompatibel|Kompatibel|  
|Pure *2.x* Anwendung|Kompatibel|Kompatibel|Kompatibel|Nicht kompatibel[3]|  
|Pure *2.x* neu kompilierte Anwendung|Kompatibel|Kompatibel[1]|Kompatibel[1]|Nicht kompatibel[3]|  
|Pure *2.x* Unicode-Anwendung|Kompatibel|Kompatibel[1]|Kompatibel[1]|Nicht kompatibel[3]|  
|Pure Open Group und ISO-konforme Anwendung|Nicht kompatibel|Kompatibel[2]|Kompatibel[2]|Kompatibel[2]|  
|Pure 3.0 Anwendung|Nicht kompatibel|Kompatibel|Kompatibel|Nicht kompatibel[4]|  
|Pure 3.5 Anwendung|Nicht kompatibel|Kompatibel|Kompatibel|Nicht kompatibel[4]|  
|Reine 3.8 (oder höher) Anwendung|Nicht kompatibel [5]|Nicht kompatibel [5]|Kompatibel|Nicht kompatibel [4]|  
|Ersetzte Anwendung|Kompatibel|Kompatibel|Kompatibel|Nicht kompatibel[3]|  
  
 [1] Die Anwendung muss mit ODBC 3.5 (oder höher) Headern mit der UNICODE-Option neu kompilieren (wenn es sich um eine Unicode-Anwendung handelt) und ODBCVER auf 0x0250 setzen.  
  
 [2] Die Anwendung muss mit ODBC 3.5 (oder höher)headerkompiliert und mit dem ODBC Driver Manager verknüpft werden. Außerdem muss das Header-Flag ODBC_STD festgelegt werden.  
  
 [3] Diese Konfiguration kann möglicherweise nicht funktionieren, da odBC *2.x* Features enthält, die nicht in den Standards vorhanden sind, z. B. Lesezeichen.  
  
 [4] Diese Konfiguration kann möglicherweise nicht funktionieren, da odBC *3.x* Features enthält, die nicht in den Standards vorhanden sind, z. B. Lesezeichen.  
  
 [5] Diese Konfiguration kann möglicherweise fehlschlagen, da es Features in ODBC 3.8 gibt, die nicht in ODBC 2.x- oder 3.x-Treibern enthalten sind, z. B. treiberspezifische [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
## <a name="driver-manager-compatibility"></a>Treiber-Manager-Kompatibilität  
 Eine ODBC 3.0-Anwendung, die mit allen Driver Manager-Versionen arbeiten muss, sollte beim Start folgendes tun:  
  
-   Weisen Sie ein Umgebungshandle zu.  
  
-   Legen Sie das SQL_ATTR_ODBC_VERSION-Umgebungsattribut auf SQL_OV_ODBC3_80 fest. Wenn der Treiber-Manager SQL_ERROR zurückkehrt, ist der Treiber-Manager älter als 3.8. Setzen Sie SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC3 zurück oder SQL_OV_ODBC2, um dem Treiber-Manager zu entsprechen.  
  
-   Weisen Sie ein Verbindungshandle zu.  
  
-   Stellen Sie eine Verbindung her.  
  
-   Rufen Sie SQLGetInfo für SQL_DRIVER_ODBC_VER auf, um die Treiberversion zu bestimmen. Wenn es sich bei dem Treiber um einen ODBC 3.8-Treiber handelt, können Sie treiberspezifische C-Typen verwenden. Verwenden Sie andernfalls keine treiberspezifischen C-Datentypen.  
  
 Beachten Sie, dass eine neu kompilierte ODBC 3.x-Anwendung ODBC 3.8-Features mit Ausnahme von treiberspezifischen C-Typen verwenden kann, ohne SQL_OV_ODBC3_80 für SQL_ATTR_ODBC_VERSION anzugeben. Dies ähnelt einer neu kompilierten ODBC 2.x-Anwendung mit ODBC 3.x-Funktionen.  
  
## <a name="using-sqlcancelhandle-in-an-application-compatible-with-all-driver-managers"></a>Verwenden von SQLCancelHandle in einer Anwendung, die mit allen Treiber-Managern kompatibel ist  
 Da [die SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) in Treiber-Managern, die vor Windows 7 veröffentlicht wurden, nicht unterstützt wird, kann eine Anwendung nicht in ältere Versionen von Windows geladen werden, wenn **sie SQLCancelHandle** direkt aufruft. Um mit allen Versionen von Treiber-Managern zu arbeiten und **SQLCancelHandle** für neue Windows-Versionen zu verwenden, sollte eine Anwendung **SQLCancelHandle** indirekt aufrufen, indem **sie LoadLibrary** und **GetProcAddress verwendet.**  
  
## <a name="see-also"></a>Weitere Informationen  
 [Neuerungen in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
