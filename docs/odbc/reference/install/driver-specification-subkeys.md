---
title: Für Treiberspezifikationen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b15aa278e2fe38afe93f5628433a6c8f4b41cd8e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47656818"
---
# <a name="driver-specification-subkeys"></a>Unterschlüssel für Treiberspezifikationen
Jeder Treiber aufgeführt, die in den Unterschlüssel für ODBC-Treiber hat einen Unterschlüssel eigene. Dieser Unterschlüssel hat den gleichen Namen wie der entsprechende Wert unter dem Unterschlüssel für ODBC-Treiber. Die Werte unter diesem Unterschlüssel auflisten, die vollständigen Pfade der Treiber und Treiber-Setup-DLLs, die Werte der vom Treiber Schlüsselwörter **SQLDrivers**, und die Anzahl der Nutzung. Die Formate der-Werte sind wie in der folgenden Tabelle gezeigt.  
  
|Name|Datentyp|data|  
|----------|---------------|----------|  
|APILevel|REG_SZ|**0** &#124; **1** &#124; **2**|  
|ConnectFunctions|REG_SZ|{**Y**&AMP;#124;**N**} {**Y**&AMP;#124;**N**} {**Y**&AMP;#124;**N**}|  
|CreateDSN|REG_SZ|*Treiber-Beschreibung*|  
|Treiber|REG_SZ|*Treiber-DLL-Pfad*|  
|DriverODBCVer|REG_SZ|*nn.nn*|  
|FileExtns|REG_SZ|**\*.** *Datei-extension1*[**,\*.** *Datei-extension2*]...|  
|FileUsage|REG_SZ|**0** &#124; **1** &#124; **2**|  
|Setup|REG_SZ|*Setup-DLL-Pfad*|  
|SQLLevel|REG_SZ|**0** &#124; **1** &#124; **2**|  
|UsageCount|REG_DWORD-WERT|*count*|  
  
 Die Verwendung von jedes Schlüsselwort wird in der folgenden Tabelle angezeigt.  
  
|Schlüsselwort|Verwendung|  
|-------------|-----------|  
|**APILevel**|Eine Zahl, der angibt, der ODBC Schnittstellen-Konformitätsgrad, die vom Treiber unterstützt werden:<br /><br /> 0 = Keine<br /><br /> 1 = Ebene-1 unterstützt<br /><br /> 2 = Ebene-2 unterstützt<br /><br /> Dies muss identisch mit der für die SQL_ODBC_INTERFACE_CONFORMANCE-Option in der zurückgegebene Wert **SQLGetInfo**.|  
|**CreateDSN**|Der Name des einen oder mehrere Datenquellen erstellt werden, wenn der Treiber installiert ist. Die Systeminformationen muss eine Data Source-Spezifikation Abschnitt enthalten für jede Datenquelle aufgeführt, mit der **CreateDSN** Schlüsselwort. Diese Abschnitte sollten nicht enthalten. die **Treiber** -Schlüsselwort, da dies im Abschnitt Spezifikation Treiber angegeben ist, jedoch muss ausreichende Informationen für die **ConfigDSN** -Funktion in der Treiber Setup-DLL für die Angabe einer Datenquelle zu erstellen, ohne dass Sie alle Dialogfelder angezeigt. Das Format eines Abschnitts Data Source-Spezifikation finden Sie unter [Datenquellenspezifikationen](../../../odbc/reference/install/data-source-specification-subkeys.md).|  
|**ConnectFunctions**|Eine drei Zeichen bestehende Zeichenfolge, die angibt, ob der Treiber unterstützt **SQLConnect**, **SQLDriverConnect**, und **SQLBrowseConnect**. Wenn der Treiber unterstützt **SQLConnect**, das erste Zeichen ist "J"; andernfalls wird "N". Wenn der Treiber unterstützt **SQLDriverConnect**, das zweite Zeichen ist "J"; andernfalls wird "N". Wenn der Treiber unterstützt **SQLBrowseConnect**, das dritte Zeichen ist "J"; andernfalls wird "N". Wenn ein Treiber unterstützt z. B. **SQLConnect** und **SQLDriverConnect** , nicht jedoch **SQLBrowseConnect**, die drei Zeichen bestehende Zeichenfolge ist "YYN".|  
|**DriverODBCVer**|Eine Zeichenfolge mit der Version von ODBC, die der Treiber unterstützt. Die Version des Formulars wird *nn.nn*, wobei die ersten beiden Ziffern die Hauptversionsnummer sind und die nächsten beiden Ziffern die Nebenversion sind. Die Version von ODBC, die in diesem Handbuch beschriebenen muss der Treiber "03.00" zurück.<br /><br /> Dies muss identisch mit der für die SQL_DRIVER_ODBC_VER-Option in der zurückgegebene Wert **SQLGetInfo**.|  
|**FileExtns**|Dateibasierte Treiber kann eine durch Trennzeichen getrennte Liste von Erweiterungen der Dateien auf den Treiber verwenden. DBASE-Treiber kann angeben, z. B. \*DBF und eine formatierte Textdatei-Treiber geben möglicherweise \*txt,\*CSV. Ein Beispiel dafür, wie eine Anwendung diese Informationen verwenden kann, finden Sie die **FileUsage** Schlüsselwort.|  
|**FileUsage**|Eine Zahl, der angibt, wie einem dateibasierten Treibers Dateien in einer Datenquelle direkt behandelt.<br /><br /> 0 = der Treiber ist nicht mit einem dateibasierten Treibers. Beispielsweise ist ein ORACLE-Treiber eine DBMS-basierten Treibers.<br /><br /> 1 = eine dateibasierte Treiber behandelt Dateien in einer Datenquelle als Tabellen. Ein Xbase-Treiber werden z. B. jede Xbase-Datei als Tabelle behandelt.<br /><br /> 2 = einen dateibasierten Treibers behandelt Dateien in einer Datenquelle als Katalog. Ein Microsoft® Access-Treiber werden z. B. jeder Microsoft Access-Datei als eine vollständige Datenbank behandelt.<br /><br /> Eine Anwendung kann diese verwenden, um zu bestimmen, wie Benutzer Daten auswählen. Angenommen, Benutzer Xbase und Paradox häufig von Daten in Dateien gespeichert werden, während ORACLE und Microsoft Access-Benutzer im Allgemeinen von Daten vorstellen, wie Sie in Tabellen gespeichert.<br /><br /> Wenn ein Benutzer auswählt **-Datendatei öffnen** aus der **Datei** Menü, eine Anwendung könnte Anzeigen der **Windows-Datei öffnen** Standarddialogfeld. Die Liste der Dateitypen verwenden die Dateierweiterungen, die mit angegebenen der **FileExtns** -Schlüsselwort für Treiber, die angeben, eine **FileUsage** Wert 1 und "Y", als das zweite Zeichen des Werts der  **ConnectFunctions** Schlüsselwort. Nachdem der Benutzer eine Datei auswählt, würde die Anwendung aufrufen **SQLDriverConnect** mit der **Treiber** Schlüsselwort und führen Sie dann eine **wählen \* FROM *Tabellenname***   Anweisung.<br /><br /> Wenn der Benutzer auswählt **Importieren von Daten** aus der **Datei** Menü zeigt eine Anwendung kann eine Liste der Beschreibungen für Treiber, die angeben, ein **FileUsage** Wert von 0 oder 2 und "Y" als das zweite Zeichen des Werts der **ConnectFunctions** Schlüsselwort. Nachdem der Benutzer einen Treiber ausgewählt hat, würde die Anwendung aufrufen **SQLDriverConnect** mit der **Treiber** -Schlüsselwort, und klicken Sie dann anzeigen, eine benutzerdefinierte **Tabelle auswählen** Dialogfeld.|  
|**SQLLevel**|Eine Zahl, der angibt, der SQL-92-Grammatik, die vom Treiber unterstützt werden:<br /><br /> 0 = SQL-92-Eintrag<br /><br /> 1 = Transitional FIPS127-2<br /><br /> 2 = SQL-92-Zwischenspeicher<br /><br /> 3 = SQL-92-vollständig<br /><br /> Dies muss identisch mit der für die SQL_SQL_CONFORMANCE-Option in der zurückgegebene Wert **SQLGetInfo**.|  
  
 Informationen über die Verwendungszähler, finden Sie unter [zählen der Verwendung](../../../odbc/reference/install/usage-counting.md) weiter oben in diesem Abschnitt.  
  
 Anwendungen sollten nicht die Verwendungsanzahl der festlegen. ODBC wird dieser Zähler zu verwalten.  
  
 Beispielsweise angenommen, ein Treiber für formatierten Text-Dateien einen Treiber-DLL mit dem Namen Text.dll enthält, eine separate Treiber Setup DLL mit dem Namen Txtsetup.dll und drei Mal installiert wurde. Wenn der Treiber die API-Ebene-1-Konformitätsgrad unterstützt, die minimale SQL-Grammatik-Konformitätsgrad unterstützt, Dateien als Tabellen behandelt und mit den Erweiterungen ".txt" und CSV-Dateien verwenden, können die Werte unter dem Unterschlüssel Text wie folgt lauten:  
  
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
