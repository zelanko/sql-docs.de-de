---
title: Unterschlüssel für Treiber Spezifikation | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280580"
---
# <a name="driver-specification-subkeys"></a>Unterschlüssel für Treiberspezifikationen
Jeder im Unterschlüssel für ODBC-Treiber aufgelistete Treiber hat seinen eigenen Unterschlüssel. Dieser Unterschlüssel hat denselben Namen wie der entsprechende Wert unter dem Unterschlüssel für ODBC-Treiber. Die Werte unter diesem Unterschlüssel Listen die vollständigen Pfade der Treiber-und Treiber-Setup-DLLs, die Werte der von **SQLDrivers**zurückgegebenen Treiber Schlüsselwörter und die Verwendungs Anzahl auf. Die Formate der Werte sind wie in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|Apilevel|REG_SZ|**0** &#124; **1** &#124; **2**|  
|Connectfunctions|REG_SZ|{**Y**&#124;**n**} {**y**&#124;**N**} {**y**&#124;**n**}|  
|"Kreatedsn"|REG_SZ|*Treiber Beschreibung*|  
|Treiber|REG_SZ|*Treiber-DLL-Pfad*|  
|DriverODBCVer|REG_SZ|*NN. NN*|  
|Fileextns|REG_SZ|**\*.** *File-extension1*[**,\*.** *File-extension2*] ...|  
|Fileusage|REG_SZ|**0** &#124; **1** &#124; **2**|  
|Setup|REG_SZ|*Setup-DLL-Pfad*|  
|Sqllevel|REG_SZ|**0** &#124; **1** &#124; **2**|  
|Usagecount|REG_DWORD|*count*|  
  
 Die Verwendung der einzelnen Schlüsselwörter ist in der folgenden Tabelle dargestellt.  
  
|Stichwort|Verwendung|  
|-------------|-----------|  
|**Apilevel**|Eine Zahl, die den vom Treiber unterstützten ODBC-Schnittstellen Konformitäts Grad angibt:<br /><br /> 0 = Keine<br /><br /> 1 = Ebene 1 wird unterstützt.<br /><br /> 2 = Ebene 2 wird unterstützt<br /><br /> Dieser Wert muss mit dem Wert identisch sein, der für die SQL_ODBC_INTERFACE_CONFORMANCE-Option in **SQLGetInfo**zurückgegeben wurde.|  
|**"Kreatedsn"**|Der Name einer oder mehrerer Datenquellen, die erstellt werden sollen, wenn der Treiber installiert wird. Die Systeminformationen müssen für jede Datenquelle, die mit dem Schlüsselwort " **fiatedsn** " aufgelistet ist, einen Datenquellen Spezifikations Abschnitt enthalten. Diese Abschnitte sollten das **Driver** -Schlüsselwort nicht enthalten, da dies im Abschnitt "Treiber Spezifikation" angegeben ist, aber genügend Informationen enthalten muss, damit die **ConfigDSN** -Funktion in der Treiber-Setup-DLL eine Datenquellen Spezifikation erstellt, ohne dass Dialogfelder angezeigt werden. Das Format eines Datenquellen Spezifikations Abschnitts finden Sie [Unterschlüssel der Datenquellen Spezifikation](../../../odbc/reference/install/data-source-specification-subkeys.md).|  
|**Connectfunctions**|Eine Zeichenfolge mit drei Zeichen, die angibt, ob der Treiber **SQLCONNECT**, **SQLDriverConnect**und **sqlbrowseconnetct**unterstützt. Wenn der Treiber **SQLCONNECT**unterstützt, ist das erste Zeichen "Y". Andernfalls ist der Wert "N". Wenn der Treiber **SQLDriverConnect**unterstützt, ist das zweite Zeichen "Y". Andernfalls ist der Wert "N". Wenn der Treiber **sqlbrowseconnetct**unterstützt, ist das dritte Zeichen "Y". Andernfalls ist der Wert "N". Wenn ein Treiber z. b. **SQLCONNECT** und **SQLDriverConnect** , aber nicht **sqlbrowseconnetct**unterstützt, ist die Zeichenfolge mit drei Zeichen "yyn".|  
|**DriverODBCVer**|Eine Zeichenfolge mit der Version von ODBC, die der Treiber unterstützt. Die Version hat die Form *NN. NN*, wobei die ersten beiden Ziffern die Hauptversion und die nächsten zwei Ziffern die neben Version sind. Für die in diesem Handbuch beschriebene Version von ODBC muss der Treiber "03,00" zurückgeben.<br /><br /> Dieser Wert muss mit dem Wert identisch sein, der für die SQL_DRIVER_ODBC_VER-Option in **SQLGetInfo**zurückgegeben wurde.|  
|**Fileextns**|Bei dateibasierten Treibern eine durch Trennzeichen getrennte Liste mit Erweiterungen der Dateien, die der Treiber verwenden kann. Ein dBase-Treiber könnte z \*. b.. DBF und einen formatierten Text Datei Treiber \*angeben. txt\*,. CSV. Ein Beispiel dafür, wie eine Anwendung diese Informationen verwenden kann, finden Sie im **fileusage** -Schlüsselwort.|  
|**Fileusage**|Eine Zahl, die angibt, wie ein Datei basierter Treiberdateien in einer Datenquelle direkt behandelt.<br /><br /> 0 = der Treiber ist kein Datei basierter Treiber. Beispielsweise handelt es sich bei einem Oracle-Treiber um einen DBMS-basierten Treiber.<br /><br /> 1 = ein Datei basierter Treiber behandelt Dateien in einer Datenquelle als Tabellen. Ein xbase-Treiber behandelt z. b. die einzelnen xbase-Dateien als Tabelle.<br /><br /> 2 = von einem dateibasierten Treiber werden Dateien in einer Datenquelle als Katalog behandelt. Beispielsweise behandelt ein Microsoft® Access-Treiber jede Microsoft Access-Datei als eine komplette Datenbank.<br /><br /> Diese kann von einer Anwendung verwendet werden, um zu bestimmen, wie Benutzerdaten auswählen. Beispielsweise betrachten xbase-und Paradox-Benutzer häufig Daten, die in Dateien gespeichert sind, während Oracle-und Microsoft Access-Benutzer in der Regel Daten als in Tabellen gespeicherten Daten betrachten.<br /><br /> Wenn ein Benutzer im Menü **Datei** die Option **Datendatei öffnen** auswählt, kann eine Anwendung das Dialogfeld " **Windows-Datei öffnen** (allgemein)" anzeigen. In der Liste der Dateitypen werden die Dateierweiterungen verwendet, die mit dem Schlüsselwort **fileextns** für Treiber angegeben werden, die den **fileusage** -Wert 1 und "Y" als zweites Zeichen des Werts des **connectfunctions** -Schlüssel Worts angeben. Nachdem der Benutzer eine Datei ausgewählt hat, ruft die Anwendung **SQLDriverConnect** mit dem **Treiber** Schlüsselwort auf und führt dann eine ** \* SELECT FROM *Table-Name-* Anweisung aus** .<br /><br /> Wenn der Benutzer aus dem Menü **Datei** die Option **Daten importieren** auswählt, kann eine Anwendung eine Liste von Beschreibungen für Treiber anzeigen, die einen **fileusage** -Wert von 0 oder 2 angeben, und "Y" als zweites Zeichen des Werts des **connectfunctions** -Schlüssel Worts. Nachdem der Benutzer einen Treiber ausgewählt hat, ruft die Anwendung **SQLDriverConnect** mit dem **Treiber** Schlüsselwort auf und zeigt dann ein benutzerdefiniertes Dialogfeld **Tabelle auswählen** an.|  
|**Sqllevel**|Eine Zahl, die die vom Treiber unterstützte SQL-92-Grammatik angibt:<br /><br /> 0 = SQL-92-Eintrag<br /><br /> 1 = FIPS127-2 Übergangs<br /><br /> 2 = SQL-92 Intermediate<br /><br /> 3 = SQL-92 voll<br /><br /> Dieser Wert muss mit dem Wert identisch sein, der für die SQL_SQL_CONFORMANCE-Option in **SQLGetInfo**zurückgegeben wurde.|  
  
 Weitere Informationen zu Verwendungs Anzahlen finden Sie unter [Nutzungs Zählung](../../../odbc/reference/install/usage-counting.md) weiter oben in diesem Abschnitt.  
  
 Anwendungen sollten die Verwendungs Anzahl nicht festlegen. Diese Anzahl wird von ODBC beibehalten.  
  
 Nehmen wir beispielsweise an, dass ein Treiber für formatierte Textdateien über eine Treiber-DLL namens "Text. dll" verfügt, eine separate Treiber-Setup-DLL mit dem Namen "Txtsetup. dll" und drei Mal installiert wurde. Wenn der Treiber die API-Konformitäts Ebene der Ebene 1 unterstützt, den minimalen SQL-Grammatik-Konformitäts Grad unterstützt, Dateien als Tabellen behandelt und Dateien mit den Erweiterungen ". txt" und ". csv" verwenden kann, können die Werte unter dem Text Unterschlüssel wie folgt lauten:  
  
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
