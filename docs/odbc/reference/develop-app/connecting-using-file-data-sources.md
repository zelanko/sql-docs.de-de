---
title: Verbinden mit Dateidatenquellen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287410"
---
# <a name="connecting-using-file-data-sources"></a>Herstellen einer Verbindung mithilfe von Dateidatenquellen
Die Verbindungsinformationen für eine Dateidatenquelle werden in einer DSN-Datei gespeichert. Daher kann die Verbindungszeichenfolge wiederholt von einem einzelnen Benutzer verwendet oder von mehreren Benutzern gemeinsam genutzt werden, wenn der entsprechende Treiber installiert ist. Die Datei enthält einen Treibernamen (oder einen anderen Datenquellennamen im Fall einer nicht gemeinsam genutzten Dateidatenquelle) und optional eine Verbindungszeichenfolge, die von **SQLDriverConnect**verwendet werden kann. Der Treiber-Manager erstellt die Verbindungszeichenfolge für den Aufruf von **SQLDriverConnect** aus den Schlüsselwörtern in der Dsn-Datei.  
  
 Eine Dateidatenquelle ermöglicht es einer Anwendung, Verbindungsoptionen anzugeben, ohne eine Verbindungszeichenfolge für die Verwendung mit **SQLDriverConnect**erstellen zu müssen. Die Dateidatenquelle wird normalerweise durch Angabe des **Schlüsselworts SAVEFILE** erstellt, wodurch der Treiber-Manager die Ausgabeverbindungszeichenfolge speichert, die durch einen Aufruf von **SQLDriverConnect** in der .dsn-Datei erstellt wurde. Diese Verbindungszeichenfolge kann wiederholt verwendet werden, indem **SQLDriverConnect** mit dem **Schlüsselwort FILEDSN** aufgerufen wird. Dadurch wird der Verbindungsprozess optimiert und eine persistente Quelle der Verbindungszeichenfolge bereitstellt.  
  
 Dateidatenquellen können auch durch Aufrufen von **SQLCreateDataSource** in der Installations-DLL erstellt werden. Informationen können in die .dsn-Datei geschrieben werden, indem **SQLWriteFileDSN**aufgerufen und aus der .dsn-Datei gelesen werden, indem **SQLReadFileDSN**aufgerufen wird. beide Funktionen befinden sich ebenfalls in der Installations-DLL. Informationen zur Installations-DLL finden Sie unter [Konfigurieren von Datenquellen](../../../odbc/reference/install/configuring-data-sources.md).  
  
 Die Schlüsselwörter, die für Verbindungsinformationen verwendet werden, befinden sich im Abschnitt [ODBC] einer .dsn-Datei. Die Mindestinformationen, die eine gemeinsam nutzende .dsn-Datei im Abschnitt [ODBC] haben würde, sind das SCHLÜSSELwort DRIVER:  
  
```  
DRIVER = SQL Server  
```  
  
 Die gemeinsam nutzende .dsn-Datei enthält in der Regel eine Verbindungszeichenfolge wie folgt:  
  
```  
DRIVER = SQL Server  
UID = Larry  
DATABASE = MyDB  
```  
  
 Wenn die Dateidatenquelle nicht mehr gemeinsam nutzen kann, enthält die DSN-Datei nur ein **DSN-Schlüsselwort.** Wenn der Treiber-Manager die Informationen in einer nicht gemeinsam nutzenden Dateidatenquelle sendet, stellt er bei Bedarf eine Verbindung mit der Datenquelle her, die durch das **DSN-Schlüsselwort** angegeben wird. Eine nicht gemeinsam nutzende .dsn-Datei würde das folgende Schlüsselwort enthalten:  
  
```  
DSN = MyDataSource  
```  
  
 Die Verbindungszeichenfolge, die für eine Dateidatenquelle verwendet wird, ist die Vereinigung der Schlüsselwörter, die in der .dsn-Datei angegeben sind, und der Schlüsselwörter, die in der Verbindungszeichenfolge im Aufruf von **SQLDriverConnect**angegeben sind. Wenn eines der Schlüsselwörter in der .dsn-Datei mit Schlüsselwörtern in der Verbindungszeichenfolge in Konflikt steht, entscheidet der Treiber-Manager, welcher Schlüsselwortwert verwendet werden soll. Weitere Informationen finden Sie unter [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [https://support.microsoft.com/kb/165866](https://support.microsoft.com/kb/165866)
