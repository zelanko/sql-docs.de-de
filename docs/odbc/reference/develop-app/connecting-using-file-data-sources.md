---
title: Herstellen einer Verbindung mithilfe von Datei Datenquellen | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8c752fc3b09c06c68dcc216cacac63744dc3101b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81287410"
---
# <a name="connecting-using-file-data-sources"></a>Herstellen einer Verbindung mithilfe von Dateidatenquellen
Die Verbindungsinformationen für eine Datei Datenquelle werden in einer DSN-Datei gespeichert. Folglich kann die Verbindungs Zeichenfolge wiederholt von einem einzelnen Benutzer verwendet werden oder von mehreren Benutzern gemeinsam verwendet werden, wenn der entsprechende Treiber installiert ist. Die Datei enthält einen Treiber Namen (oder einen anderen Datenquellen Namen im Fall einer nicht in der Share baren Datei Datenquelle) und optional eine Verbindungs Zeichenfolge, die von **SQLDriverConnect**verwendet werden kann. Der Treiber-Manager erstellt die Verbindungs Zeichenfolge für den **SQLDriverConnect** -Befehl aus den Schlüsselwörtern in der DSN-Datei.  
  
 Mit einer Datei Datenquelle kann eine Anwendung Verbindungsoptionen angeben, ohne eine Verbindungs Zeichenfolge für die Verwendung mit **SQLDriverConnect**erstellen zu müssen. Die Datei Datenquelle wird normalerweise durch Angabe des **SaveFile** -Schlüssel Worts erstellt, das bewirkt, dass der Treiber-Manager die von einem **SQLDriverConnect** -Befehl erstellte Ausgabe Verbindungs Zeichenfolge in der DSN-Datei speichert. Diese Verbindungs Zeichenfolge kann wiederholt durch Aufrufen von **SQLDriverConnect** mit dem **FILEDSN** -Schlüsselwort verwendet werden. Dadurch wird der Verbindungsprozess optimiert, und es wird eine persistente Quelle der Verbindungs Zeichenfolge bereitstellt.  
  
 Datei Datenquellen können auch durch Aufrufen von **SQLCreateDataSource** in der Installationsprogramm-dll erstellt werden. Sie können Informationen in die DSN-Datei schreiben, indem Sie **sqlwrite tefiledsn**aufrufen und aus der DSN-Datei lesen, indem Sie **sqllesefiledsn**aufrufen. Beide Funktionen sind ebenfalls in der Installationsprogramm-dll. Weitere Informationen zur Installationsprogramm-dll finden Sie unter [Konfigurieren von Datenquellen](../../../odbc/reference/install/configuring-data-sources.md).  
  
 Die Schlüsselwörter, die für Verbindungsinformationen verwendet werden, befinden sich im Abschnitt [ODBC] einer DSN-Datei. Die minimalen Informationen, die eine freigegeben. DSN-Datei im [ODBC]-Abschnitt enthalten würde, sind das Driver-Schlüsselwort:  
  
```  
DRIVER = SQL Server  
```  
  
 Die Datei "freigegeben. DSN" enthält in der Regel eine Verbindungs Zeichenfolge wie folgt:  
  
```  
DRIVER = SQL Server  
UID = Larry  
DATABASE = MyDB  
```  
  
 Wenn die Datei Datenquelle nicht Share fähig ist, enthält die DSN-Datei nur ein **DSN** -Schlüsselwort. Wenn der Treiber-Manager die Informationen in einer nicht Share baren Datei Datenquelle sendet, stellt er bei Bedarf eine Verbindung mit der Datenquelle her, die durch das **DSN** -Schlüsselwort angegeben wird. Eine nicht Shareable. DSN-Datei enthält das folgende Schlüsselwort:  
  
```  
DSN = MyDataSource  
```  
  
 Die für eine Datei Datenquelle verwendete Verbindungs Zeichenfolge ist die Kombination der Schlüsselwörter, die in der DSN-Datei angegeben sind, und der Schlüsselwörter, die in der Verbindungs Zeichenfolge im **SQLDriverConnect**-Befehl angegeben sind. Wenn eines der Schlüsselwörter in der DSN-Datei mit Schlüsselwörtern in der Verbindungs Zeichenfolge in Konflikt steht, entscheidet der Treiber-Manager, welcher Schlüsselwort Wert verwendet werden soll. Weitere Informationen finden Sie unter [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [https://support.microsoft.com/kb/165866](https://support.microsoft.com/kb/165866)
