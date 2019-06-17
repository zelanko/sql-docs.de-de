---
title: Herstellen einer Verbindung mithilfe von Dateidatenquellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to driver [ODBC], file data sources
- SQLDriverConnect function [ODBC], connecting using file data sources
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], file data sources
- file data sources [ODBC]
ms.assetid: 3003f8c2-8be6-41cc-8d9c-612e9bd0f3ae
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6fec2cea71ba818e955e0b6c2ce31c58f2c07357
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63043885"
---
# <a name="connecting-using-file-data-sources"></a>Herstellen einer Verbindung mithilfe von Dateidatenquellen
Die Verbindungsinformationen für eine Datenquelle wird in einer DSN-Datei gespeichert. Daher kann die Verbindungszeichenfolge wiederholt durch einen einzelnen Benutzer verwendet oder von mehreren Benutzern gemeinsam genutzt, wenn sie den entsprechenden Treiber installiert haben. Die Datei enthält ein Treibername (oder einen anderen Datenquellennamen im Fall von eine Dateidatenquelle) und optional eine Verbindungszeichenfolge, die von verwendet werden kann **SQLDriverConnect**. Der Treiber-Manager erstellt die Verbindungszeichenfolge für den Aufruf von **SQLDriverConnect** in den Schlüsselwörtern in der Datei ".DSN".  
  
 Eine Datenquelle ermöglicht einer Anwendung, die Verbindungsoptionen angeben, ohne dass zum Erstellen einer Verbindungszeichenfolge für die Verwendung mit **SQLDriverConnect**. Die Datei als Datenquelle in der Regel wird erstellt, indem die **SAVEFILE** -Schlüsselwort, das bewirkt, der Treiber-Manager dass, speichern Sie die ausgegebene Verbindungszeichenfolge, die durch einen Aufruf von erstellt **SQLDriverConnect** auf die DSN-Datei. Dass die Verbindungszeichenfolge wiederholt verwendet werden kann, können Sie durch Aufrufen von **SQLDriverConnect** mit der **FILEDSN** Schlüsselwort. Dies optimiert die Verbindung und stellt eine permanente Datenquelle der Verbindungszeichenfolge bereit.  
  
 Dateidatenquellen können auch erstellt werden durch Aufrufen von **SQLCreateDataSource** im DLL-Installer. Informationen in die DSN-Datei geschrieben werden kann, durch den Aufruf **SQLWriteFileDSN**, und Lesen aus der Datei ".DSN" durch den Aufruf **SQLReadFileDSN**; beide Funktionen sind auch im DLL-Installer. Informationen zu den Installer-DLL finden Sie unter [Konfigurieren von Datenquellen](../../../odbc/reference/install/configuring-data-sources.md).  
  
 Schlüsselwörter für Verbindungsinformationen sind im Abschnitt [ODBC] eine DSN-Datei. Die mindestens erforderlichen Informationen, die eine freigegebenen DSN-Datei im Abschnitt [ODBC] hätte ist das DRIVER-Schlüsselwort:  
  
```  
DRIVER = SQL Server  
```  
  
 Die gemeinsam nutzbar DSN-Datei enthält eine Verbindungszeichenfolge in der Regel wie folgt aus:  
  
```  
DRIVER = SQL Server  
UID = Larry  
DATABASE = MyDB  
```  
  
 Wenn die Datei als Datenquelle Dateidatenquelle ist, enthält nur die DSN-Datei eine **DSN** Schlüsselwort. Wenn der Treiber-Manager die Informationen in eine Dateidatenquelle gesendet wird, Verbindung nach Bedarf für die Datenquelle, angegeben durch die **DSN** Schlüsselwort. Eine Dateidatenquelle DSN-Datei enthält das folgende Schlüsselwort:  
  
```  
DSN = MyDataSource  
```  
  
 Die für eine Datei als Datenquelle verwendete Verbindungszeichenfolge ist die Kombination der Schlüsselwörter, die in der Datei ".DSN" angegeben und die Schlüsselwörter, die in der Verbindungszeichenfolge im Aufruf angegeben **SQLDriverConnect**. Wenn die Schlüsselwörter in der DSN-Datei mit Schlüsselwörtern in der Verbindungszeichenfolge einen Konflikt verursacht, entscheidet der Treiber-Manager an, die Schlüsselwortwert verwendet werden soll. Weitere Informationen finden Sie unter [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="see-also"></a>Siehe auch  
 [https://support.microsoft.com/kb/165866](https://support.microsoft.com/kb/165866)
