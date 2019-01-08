---
title: Matrix der sperrenkompatibilität | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b1d0fc510c7c45dab8fbc79cc8e74001ff1855b6
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52528237"
---
# <a name="compatibility-matrix"></a>Kompatibilitätsmatrix
Die folgende Tabelle enthält Informationen zur Kompatibilität der Typen von Anwendungen und Treiber, die zuvor in diesem Abschnitt definiert.  
  
|Anwendungstyp<br /><br /> und version|32-Bit-ODBC<br /><br /> 2.*x* Treiber|ODBC 3. *x*<br /><br /> Treiber|ODBC 3.8-Treiber|ISO "und" Open Group-kompatiblen Treiber|  
|--------------------------------------|-----------------------------------|---------------------------|---------------------|-----------------------------------------|  
|eine beliebige Version 16-Bit-Anwendung|Kompatibel|Kompatibel|Kompatibel|Kompatibel|  
|Reine 2. *x* Anwendung|Kompatibel|Kompatibel|Kompatibel|Nicht kompatible [3]|  
|Reine 2. *x* neu kompiliert die Anwendung|Kompatibel|Kompatible [1]|Kompatible [1]|Nicht kompatible [3]|  
|Reine 2. *x* Unicode-Anwendung|Kompatibel|Kompatible [1]|Kompatible [1]|Nicht kompatible [3]|  
|Reine Open Group und ISO-kompatible Anwendung|Nicht kompatibel|Kompatible [2]|Kompatible [2]|Kompatible [2]|  
|Reine 3.0-Anwendung|Nicht kompatibel|Kompatibel|Kompatibel|Nicht kompatible [4]|  
|Reine 3.5-Anwendung|Nicht kompatibel|Kompatibel|Kompatibel|Nicht kompatible [4]|  
|Reine 3.8 (oder höher)-Anwendung|Nicht kompatible [5]|Nicht kompatible [5]|Kompatibel|Nicht kompatible [4]|  
|Ersetzten Anwendung|Kompatibel|Kompatibel|Kompatibel|Nicht kompatible [3]|  
  
 [1] die Anwendung muss erneut kompilieren mithilfe von ODBC 3.5 (oder höher)-Header mit der UNICODE-Option (sofern es sich um eine Unicode-Anwendung ist) und ODBCVER auf 0x0250 festlegen.  
  
 [2] für die Anwendung muss Kompilieren mit der ODBC 3.5 (oder höher) Header und Verknüpfen mit der ODBC-Treiber-Manager. Sie müssen auch das seitenheaderflag ODBC_STD festgelegt.  
  
 [3] für diese Konfiguration kann möglicherweise fehlschlagen, funktioniert, weil in ODBC 2. Features stehen. *x* , die nicht in den Standards, z. B. Lesezeichen sind.  
  
 [4] in dieser Konfiguration kann ausfallen funktioniert, weil es Funktionen in ODBC 3. gibt *.x* , die nicht in den Standards, z. B. Lesezeichen sind.  
  
 [5] für diese Konfiguration kann möglicherweise fehlschlagen, da es sich bei verfügt über Features sind ODBC 3.8, die nicht in ODBC 2.x oder 3.x-Treiber, z. B. treiberspezifische [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
## <a name="driver-manager-compatibility"></a>Treiber-Manager-Kompatibilität  
 Eine ODBC-Version 3.0-Anwendung, die mit allen-Treiber-Manager-Versionen ausgeführt werden muss sollten beim Starten Folgendes tun:  
  
-   Ein Umgebungshandle zuzuordnen.  
  
-   Umgebungsattributs SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC3_80 festgelegt. Wenn der Treiber-Manager wird SQL_ERROR zurückgegeben wird, ist der Treiber-Manager älter als 3.8. Setzen Sie SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC3 fest oder SQL_OV_ODBC2, entsprechend, um den Treiber-Manager zu entsprechen.  
  
-   Zuordnen eines Verbindungshandles.  
  
-   Stellen Sie eine Verbindung.  
  
-   Rufen Sie SQLGetInfo für SQL_DRIVER_ODBC_VER, um zu bestimmen, der Version des Treibers. Wenn der Treiber einen ODBC 3.8-Treiber ist, können Sie die Treiber-spezifischen C-Typen. Verwenden Sie andernfalls nicht Driver-spezifischen C-Datentypen.  
  
 Beachten Sie, dass es sich bei eine neu kompilierten ODBC 3.x-Anwendung ODBC 3.8-Funktionen als Treiber-spezifischen C-Typen verwenden kann, ohne Angabe von SQL_OV_ODBC3_80 für SQL_ATTR_ODBC_VERSION. Dies ähnelt einer neu kompilierten ODBC 2.x-Anwendung mit ODBC 3.x-Funktionen.  
  
## <a name="using-sqlcancelhandle-in-an-application-compatible-with-all-driver-managers"></a>Verwenden von SQLCancelHandle in einer Anwendung kompatibel mit dem alle Treiber-Manager  
 Da [SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) wird nicht unterstützt im Treiber-Manager, die vor Windows 7 veröffentlicht wurden, kann keine Anwendung in älteren Versionen von Windows geladen werden, wenn sie ruft **SQLCancelHandle** direkt. Zum Arbeiten mit allen Versionen der Treiber-Manager, und verwenden Sie **SQLCancelHandle** bei neuen Versionen von Windows, sollte eine Anwendung aufrufen **SQLCancelHandle** indirekt mithilfe **LoadLibrary** und **GetProcAddress.**  
  
## <a name="see-also"></a>Siehe auch  
 [What's New in ODBC 3.8 (Neues in ODBX 3.8)](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
