---
title: SQLServer-Beispiel durchsuchen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBrowseConnect function [ODBC], example
- connecting to data source [ODBC], SqlBrowseConnect
- connecting to driver [ODBC], SQLBrowseConnect
ms.assetid: 6e0d5fd1-ec93-4348-a77a-08f5ba738bc6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8dc57d738c1d5726d2208b930c5d4fadcd93b39
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149320"
---
# <a name="sql-server-browsing-example"></a>SQL Server-Suchbeispiel
Das folgende Beispiel zeigt wie **SQLBrowseConnect** kann verwendet werden, um die Verbindungen zur Verfügung, mit einem Treiber für SQL Server zu durchsuchen. Zunächst fordert die Anwendung ein Verbindungshandle:  
  
```  
SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
```  
  
 Anschließend wird die Anwendung ruft **SQLBrowseConnect** und gibt an, die mithilfe der treiberbeschreibung, die vom SQL Server-Treiber **SQLDrivers**:  
  
```  
SQLBrowseConnect(hdbc, "DRIVER={SQL Server};", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Da dies der erste Aufruf ist **SQLBrowseConnect**, der Treiber-Manager lädt den SQL Server-Treiber und Aufrufe des Treibers **SQLBrowseConnect** -Funktion mit den gleichen Argumenten, die sie empfangen, aus der die Anwendung.  
  
> [!NOTE]  
>  Wenn Sie für einen Datenanbieter der Datenquelle, der Windows-Authentifizierung unterstützt herstellen, sollten Sie angeben `Trusted_Connection=yes` anstelle von Benutzer-ID und Kennwort-Informationen in der Verbindungszeichenfolge.  
  
 Der Treiber ermittelt, dass dies der erste Aufruf ist **SQLBrowseConnect** und gibt die zweite Ebene der Verbindungsattribute: Server, Benutzername, Kennwort, Anwendungsname und Workstation-ID. Für das Serverattribut wird eine Liste der gültigen Servernamen zurückgegeben. Den Rückgabecode **SQLBrowseConnect** wird SQL_NEED_DATA zurückgegeben. Hier wird die Ergebniszeichenfolge durchsuchen:  
  
```  
"SERVER:Server={red,blue,green,yellow};UID:Login ID=?;PWD:Password=?;  
   *APP:AppName=?;*WSID:WorkStation ID=?;"  
```  
  
 Jedes Schlüsselwort in der Ergebniszeichenfolge durchsuchen wird von einem Doppelpunkt und ein oder mehrere Wörter vor dem Gleichheitszeichen folgen. Diese Wörter sind den benutzerfreundlichen Namen, den eine Anwendung verwenden können, um ein Dialogfeld zu erstellen. Die **APP** und **Angaben für WSID** Schlüsselwörter werden mit dem Präfix durch ein Sternchen, d. h., sie sind optional. Die **SERVER**, **UID**, und **PWD** Schlüsselwörter werden nicht durch ein Sternchen als Präfix; die Werte müssen für diese in die nächste Zeichenfolge der durchsuchen-Anforderung angegeben werden. Der Wert für die **SERVER** Schlüsselwort möglicherweise eines der vom Server **SQLBrowseConnect** oder einen vom Benutzer angegebenen Namen.  
  
 Ruft die Anwendung **SQLBrowseConnect** wieder Angabe des grünen-Servers und das Auslassen der **APP** und **Angaben für WSID** Schlüsselwörter und benutzerfreundlichen Namen nach jedes Schlüsselwort:  
  
```  
SQLBrowseConnect(hdbc, "SERVER=green;UID=Smith;PWD=Sesame;", SQL_NTS,  
                  BrowseResult, sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Der Treiber versucht, die mit dem grünen Server herzustellen. Wenn alle nicht schwerwiegenden Fehler, wie z. B. eine fehlende Schlüsselwort-Wert-Paar vorliegen **SQLBrowseConnect** wird SQL_NEED_DATA zurückgegeben und bleibt im gleichen Zustand wie vor dem Fehler. Die Anwendung kann Aufrufen **SQLGetDiagField** oder **SQLGetDiagRec** um den Fehler zu ermitteln. Wenn die Verbindung erfolgreich ist, wird der Treiber wird SQL_NEED_DATA zurückgegeben, und gibt die Ergebniszeichenfolge durchsuchen:  
  
```  
"*DATABASE:Database={master,model,pubs,tempdb};  
   *LANGUAGE:Language={us_english,Franais};"  
```  
  
 Da die Attribute in dieser Zeichenfolge optional sind, kann die Anwendung diese ausschließen. Allerdings muss die Anwendung aufrufen **SQLBrowseConnect** erneut aus. Wenn die Anwendung auswählt, um den Datenbanknamen und die Sprache zu unterdrücken, gibt es eine leere durchsuchen-Anforderungs-Zeichenfolge an. In diesem Beispiel wählt die Anwendung die Pubs-Datenbank und ruft **SQLBrowseConnect** ein letztes Mal aus, das Auslassen der **Sprache** -Schlüsselwort und das Sternchen, bevor Sie die **Datenbank**Schlüsselwort:  
  
```  
SQLBrowseConnect(hdbc, "DATABASE=pubs;", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Da die **Datenbank** Attribut ist das letzte Verbindungsattribut, das vom Treiber erforderlich sind, die zum Durchsuchen Prozess abgeschlossen ist, die Anwendung mit der Datenquelle verbunden ist und **SQLBrowseConnect** Gibt SQL_SUCCESS zurück. **SQLBrowseConnect** gibt auch die vollständige Verbindungszeichenfolge als Ergebniszeichenfolge durchsuchen:  
  
```  
"DSN=MySQLServer;SERVER=green;UID=Smith;PWD=Sesame;DATABASE=pubs;"  
```  
  
 Die endgültigen Verbindungszeichenfolge, die vom Treiber zurückgegebene benutzerfreundlichen Namen nach dem keinen jedes Schlüsselwort, noch enthält sie optionale Schlüsselwörter, die nicht von der Anwendung angegeben. Die Anwendung kann diese Zeichenfolge mit verwenden **SQLDriverConnect** (nach dem Trennen der Verbindung) eine Verbindung mit der Datenquelle auf dem aktuellen Verbindungshandle bzw. zum Verbinden mit der Datenquelle in eine andere Verbindung-Handle. Zum Beispiel:  
  
```  
SQLDriverConnect(hdbc, hwnd, BrowseResult, SQL_NTS, ConnStrOut,  
                  sizeof(ConnStrOut), &ConnStrOutLen, SQL_DRIVER_NOPROMPT);  
```
