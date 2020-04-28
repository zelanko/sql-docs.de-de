---
title: Kompatibilitäts Matrix | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307453"
---
# <a name="compatibility-matrix"></a>Kompatibilitätsmatrix
In der folgenden Tabelle wird die Kompatibilität der Typen von Anwendungen und Treibern beschrieben, die zuvor in diesem Abschnitt definiert wurden.  
  
|Anwendungstyp<br /><br /> und Version|32-Bit-ODBC<br /><br /> *2. x* -Treiber|ODBC *3. x*<br /><br /> Treiber|ODBC 3,8-Treiber|ISO und offener Gruppen kompatibler Treiber|  
|--------------------------------------|-----------------------------------|---------------------------|---------------------|-----------------------------------------|  
|16-Bit-Anwendung, beliebige Version|Kompatibel|Kompatibel|Kompatibel|Kompatibel|  
|Reine *2. x* -Anwendung|Kompatibel|Kompatibel|Kompatibel|Nicht kompatibel [3]|  
|Reine *2. x* -Anwendung neu kompiliert|Kompatibel|Kompatibel [1]|Kompatibel [1]|Nicht kompatibel [3]|  
|Reine *2. x* -Unicode-Anwendung|Kompatibel|Kompatibel [1]|Kompatibel [1]|Nicht kompatibel [3]|  
|Reine Open Group-und ISO-kompatible Anwendung|Nicht kompatibel|Kompatibel [2]|Kompatibel [2]|Kompatibel [2]|  
|Reine 3,0-Anwendung|Nicht kompatibel|Kompatibel|Kompatibel|Nicht kompatibel [4]|  
|Reine 3,5-Anwendung|Nicht kompatibel|Kompatibel|Kompatibel|Nicht kompatibel [4]|  
|Reine 3,8-Anwendung (oder höher)|Nicht kompatibel [5]|Nicht kompatibel [5]|Kompatibel|Nicht kompatibel [4]|  
|Ersetzte Anwendung|Kompatibel|Kompatibel|Kompatibel|Nicht kompatibel [3]|  
  
 [1] die Anwendung muss mithilfe von ODBC 3,5 (oder höher)-Headern mit der Unicode-Option (sofern es sich um eine Unicode-Anwendung handelt) neu kompiliert werden, und ODBCVer muss auf 0x0250 festgelegt werden.  
  
 [2] die Anwendung muss mithilfe von ODBC 3,5-Headern (oder höher) kompiliert und mit dem ODBC-Treiber-Manager verknüpft werden. Außerdem muss das Header Flag ODBC_STD festgelegt werden.  
  
 [3] Diese Konfiguration kann möglicherweise nicht funktionieren, da in ODBC *2. x* Features vorhanden sind, die nicht den Standards entsprechen, wie z. b. Lesezeichen.  
  
 [4] Diese Konfiguration kann möglicherweise nicht funktionieren, da in ODBC *3. x* Features vorhanden sind, die nicht den Standards entsprechen, wie z. b. Lesezeichen.  
  
 [5] Diese Konfiguration kann möglicherweise fehlschlagen, weil in ODBC 3,8 Features vorhanden sind, die nicht in ODBC 2. x-oder 3. x-Treibern enthalten sind, z. b. Treiber spezifische [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).  
  
## <a name="driver-manager-compatibility"></a>Treiber-Manager-Kompatibilität  
 Eine ODBC 3,0-Anwendung, die mit allen Treiber-Manager-Versionen funktionieren muss, sollte beim Start Folgendes ausführen:  
  
-   Zuordnen eines Umgebungs Handles.  
  
-   Legen Sie das SQL_ATTR_ODBC_VERSION-Umgebungs Attribut auf SQL_OV_ODBC3_80 fest. Wenn der Treiber-Manager SQL_ERROR zurückgibt, ist der Treiber-Manager älter als 3,8. Setzen Sie SQL_ATTR_ODBC_VERSION nach Bedarf auf SQL_OV_ODBC3 oder SQL_OV_ODBC2 zurück, damit Sie dem Treiber-Manager entspricht.  
  
-   Zuordnen eines Verbindungs Handles.  
  
-   Stellen Sie eine Verbindung her.  
  
-   Aufrufen von SQLGetInfo für SQL_DRIVER_ODBC_VER, um die Treiber Version zu bestimmen. Wenn der Treiber ein ODBC 3,8-Treiber ist, können Sie Treiber spezifische C-Typen verwenden. Andernfalls sollten Sie keine treiberspezifischen C-Datentypen verwenden.  
  
 Beachten Sie, dass eine neu kompilierte ODBC 3. x-Anwendung ODBC 3,8-Features verwenden kann, die keine treiberspezifischen C-Typen sind, ohne SQL_OV_ODBC3_80 für SQL_ATTR_ODBC_VERSION anzugeben. Dies ähnelt einer neu kompilierten ODBC 2. x-Anwendung, die ODBC 3. x-Funktionen verwendet.  
  
## <a name="using-sqlcancelhandle-in-an-application-compatible-with-all-driver-managers"></a>Verwenden von sqlcancelhandle in einer Anwendung, die mit allen Treiber-Managern kompatibel ist  
 Da die [sqlcancelhandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md) in Treiber-Managern, die vor Windows 7 veröffentlicht wurden, nicht unterstützt wird, kann eine Anwendung in älteren Versionen von Windows nicht geladen werden, wenn **sqlcancelhandle** direkt aufgerufen wird. Um mit allen Versionen der Treiber-Manager zu arbeiten und **sqlcancelhandle** in neuen Versionen von Windows zu verwenden, sollte eine Anwendung **sqlcancelhandle** indirekt mithilfe von **LoadLibrary** und **GetProcAddress aufrufen.**  
  
## <a name="see-also"></a>Weitere Informationen  
 [Neuerungen in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
