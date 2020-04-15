---
title: Unterschlüssel für Treiberspezifikation | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], driver specification subkeys
- driver specification subkeys [ODBC]
- registry entries for components [ODBC], driver specification subkeys
- drivers subkey [ODBC]
ms.assetid: b4d802ef-b199-4e64-b7a5-6f2b3e5e2c80
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 47aa75f647e5fd8a88168611a3b21284962c70a4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280580"
---
# <a name="driver-specification-subkeys"></a>Unterschlüssel für Treiberspezifikationen
Jeder Treiber, der im Unterschlüssel ODBC Drivers aufgeführt ist, verfügt über einen eigenen Unterschlüssel. Dieser Unterschlüssel hat denselben Namen wie der entsprechende Wert unter dem Unterschlüssel ODBC-Treiber. Die Werte unter diesem Unterschlüssel listen die vollständigen Pfade der Treiber- und Treibereinrichtungs-DLLs, die Werte der von **SQLDrivers**zurückgegebenen Schlüsselwörter und die Verwendungsanzahl auf. Die Formate der Werte sind wie in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|APILevel|REG_SZ|**0** &#124; **1** &#124; **2**|  
|ConnectFunctions|REG_SZ|Y**Y**&#124;**N**-**Y**&#124;**N**-**Y**&#124;**N**|  
|CreateDSN|REG_SZ|*Treiberbeschreibung*|  
|Treiber|REG_SZ|*treiber-DLL-Pfad*|  
|DriverODBCVer|REG_SZ|*nn.nn*|  
|FileExtns|REG_SZ|**\*.** *Dateierweiterung1*[**\*, .** *Dateierweiterung2*] ...|  
|FileUsage|REG_SZ|**0** &#124; **1** &#124; **2**|  
|Einrichten|REG_SZ|*Setup-DLL-Pfad*|  
|SQLLevel|REG_SZ|**0** &#124; **1** &#124; **2**|  
|UsageCount|REG_DWORD|*count*|  
  
 Die Verwendung der einzelnen Schlüsselwörter wird in der folgenden Tabelle angezeigt.  
  
|Schlüsselwort|Verwendung|  
|-------------|-----------|  
|**APILevel**|Eine Zahl, die die vom Treiber unterstützte ODBC-Schnittstellenkonformitätsstufe angibt:<br /><br /> 0 = Keine<br /><br /> 1 = Stufe 1 unterstützt<br /><br /> 2 = Stufe 2 unterstützt<br /><br /> Dies muss mit dem Wert identisch sein, der für die Option SQL_ODBC_INTERFACE_CONFORMANCE in **SQLGetInfo**zurückgegeben wird.|  
|**CreateDSN**|Der Name einer oder mehrerer Datenquellen, die bei der Installation des Treibers erstellt werden sollen. Die Systeminformationen müssen einen Datenquellenspezifikationsabschnitt für jede Datenquelle enthalten, die mit dem **CreateDSN-Schlüsselwort** aufgeführt ist. Diese Abschnitte sollten das **Schlüsselwort Driver** nicht enthalten, da dies im Abschnitt "Treiberspezifikation" angegeben ist, aber genügend Informationen für die **ConfigDSN-Funktion** in der Treibereinrichtungs-DLL enthalten müssen, um eine Datenquellenspezifikation zu erstellen, ohne Dialogfelder anzuzeigen. Informationen zum Format eines Abschnitts zur Datenquellenspezifikation finden Sie unter Unterschlüssel für [Datenquellenspezifikation](../../../odbc/reference/install/data-source-specification-subkeys.md).|  
|**ConnectFunctions**|Eine zeichenfolgedreistellige Zeichenfolge, die angibt, ob der Treiber **SQLConnect**, **SQLDriverConnect**und **SQLBrowseConnect**unterstützt. Wenn der Treiber **SQLConnect**unterstützt, lautet das erste Zeichen "Y"; andernfalls ist es "N". Wenn der Treiber **SQLDriverConnect**unterstützt, lautet das zweite Zeichen "Y"; andernfalls ist es "N". Wenn der Treiber **SQLBrowseConnect**unterstützt, lautet das dritte Zeichen "Y"; andernfalls ist es "N". Wenn ein Treiber beispielsweise **SQLConnect** und **SQLDriverConnect** unterstützt, aber nicht **SQLBrowseConnect**, lautet die zeichenfolge mit drei Zeichen "YYN".|  
|**DriverODBCVer**|Eine Zeichenfolge mit der ODBC-Version, die vom Treiber unterstützt wird. Die Version ist von der Form *nn.nn*, wobei die ersten beiden Ziffern die Hauptversion und die nächsten beiden Ziffern die Nebenversion sind. Für die in diesem Handbuch beschriebene ODBC-Version muss der Treiber "03.00" zurückgeben.<br /><br /> Dies muss mit dem Wert identisch sein, der für die SQL_DRIVER_ODBC_VER-Option in **SQLGetInfo**zurückgegeben wird.|  
|**FileExtns**|Bei dateibasierten Treibern eine durch Kommas getrennte Liste der Erweiterungen der Dateien, die der Treiber verwenden kann. Ein dBASE-Treiber kann \*z. B. .dbf angeben, \*und ein\*formatierter Textdateitreiber kann .txt, .csv angeben. Ein Beispiel dafür, wie eine Anwendung diese **FileUsage** Informationen verwenden kann, finden Sie im FileUsage-Schlüsselwort.|  
|**FileUsage**|Eine Zahl, die angibt, wie ein dateibasierter Treiber Dateien in einer Datenquelle direkt behandelt.<br /><br /> 0 = Der Treiber ist kein dateibasierter Treiber. Ein ORACLE-Treiber ist beispielsweise ein DBMS-basierter Treiber.<br /><br /> 1 = Ein dateibasierter Treiber behandelt Dateien in einer Datenquelle als Tabellen. Ein Xbase-Treiber behandelt z. B. jede Xbase-Datei als Tabelle.<br /><br /> 2 = Ein dateibasierter Treiber behandelt Dateien in einer Datenquelle als Katalog. Ein Microsoft® Access-Treiber behandelt z. B. jede Microsoft Access-Datei als vollständige Datenbank.<br /><br /> Eine Anwendung kann dies verwenden, um zu bestimmen, wie Benutzer Daten auswählen. Beispielsweise denken Xbase- und Paradox-Benutzer häufig an Daten, die in Dateien gespeichert sind, während ORACLE- und Microsoft Access-Benutzer Daten im Allgemeinen als in Tabellen gespeichert betrachten.<br /><br /> Wenn ein Benutzer im Menü **Datei** Datei die Option **Datendatei öffnen** auswählt, kann eine Anwendung das allgemeine Dialogfeld **Windows File Open** anzeigen. Die Liste der Dateitypen würde die Dateierweiterungen verwenden, die mit dem **FileExtns-Schlüsselwort** für Treiber angegeben sind, die einen **FileUsage-Wert** von 1 und "Y" als zweites Zeichen des Werts des **ConnectFunctions-Schlüsselworts** angeben. Nachdem der Benutzer eine Datei ausgewählt hat, ruft die Anwendung **SQLDriverConnect** mit dem **Schlüsselwort DRIVER** auf und führt dann eine **SELECT \* *FROM-Tabellenname-Anweisung* ** aus.<br /><br /> Wenn der Benutzer daten **importieren** aus dem Menü **Datei** auswählt, kann eine Anwendung eine Liste von Beschreibungen für Treiber anzeigen, die einen **FileUsage-Wert** von 0 oder 2 und "Y" als zweites Zeichen des Werts des **ConnectFunctions-Schlüsselworts** angeben. Nachdem der Benutzer einen Treiber ausgewählt hat, ruft die Anwendung **SQLDriverConnect** mit dem **Schlüsselwort DRIVER** auf und zeigt dann ein benutzerdefiniertes Dialogfeld Tabelle **auswählen** an.|  
|**SQLLevel**|Eine Zahl, die die SQL-92-Grammatik angibt, die vom Treiber unterstützt wird:<br /><br /> 0 = SQL-92-Eintrag<br /><br /> 1 = FIPS127-2 Übergang<br /><br /> 2 = SQL-92 Zwischenstufe<br /><br /> 3 = SQL-92 Voll<br /><br /> Dies muss mit dem Wert identisch sein, der für die Option SQL_SQL_CONFORMANCE in **SQLGetInfo**zurückgegeben wird.|  
  
 Informationen zu den Nutzungszahlen finden Sie weiter oben in diesem Abschnitt unter [Verwendungszählung.](../../../odbc/reference/install/usage-counting.md)  
  
 Anwendungen sollten die Verwendungsanzahl nicht festlegen. ODBC behält diese Anzahl bei.  
  
 Angenommen, ein Treiber für formatierte Textdateien verfügt über eine Treiber-DLL mit dem Namen Text.dll, eine separate Treiber-Setup-DLL mit dem Namen Txtsetup.dll, und wurde dreimal installiert. Wenn der Treiber die API-Konformitätsebene der Ebene 1 unterstützt, die Konformitätsebene der SQL-Grammatik mit der Mindestsql-Grammatik unterstützt, Dateien als Tabellen behandelt und Dateien mit den Erweiterungen .txt und .csv verwenden kann, können die Werte unter dem Unterschlüssel Text wie folgt lauten:  
  
```  
APILevel : REG_SZ : 1  
ConnectFunctions : REG_SZ : YYN  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\TEXT.DLL  
DriverODBCVer : REG_SZ : 03.00.00  
FileExtns : REG_SZ : *.txt,*.csv  
FileUsage : REG_SZ : 1  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\TXTSETUP.DLL  
SQLLevel : REG_SZ : 0  
UsageCount : REG_DWORD : 0x3  
```
