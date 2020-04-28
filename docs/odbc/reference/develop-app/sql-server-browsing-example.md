---
title: Beispiel für SQL Server durchsuchen | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7b15aa8e3d573660a312fceb5b9100a41f0384d2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301981"
---
# <a name="sql-server-browsing-example"></a>SQL Server-Suchbeispiel
Im folgenden Beispiel wird gezeigt, wie **sqlbrowseconnetct** verwendet werden kann, um die Verbindungen zu durchsuchen, die mit einem Treiber für SQL Server verfügbar sind. Zunächst fordert die Anwendung ein Verbindungs Handle an:  
  
```  
SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
```  
  
 Als nächstes Ruft die Anwendung **sqlbrowseconnetct** auf und gibt den SQL Server Treiber mithilfe der von **SQLDrivers**zurückgegebenen Treiber Beschreibung an:  
  
```  
SQLBrowseConnect(hdbc, "DRIVER={SQL Server};", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Da dies der erste Aufruf von **sqlbrowseconnetct**ist, lädt der Treiber-Manager den SQL Server Treiber und ruft die **sqlbrowseconnetct** -Funktion des Treibers mit denselben Argumenten auf, die er von der Anwendung erhalten hat.  
  
> [!NOTE]  
>  Wenn Sie eine Verbindung mit einem Datenquellen Anbieter herstellen, der die Windows-Authentifizierung unter `Trusted_Connection=yes` stützt, sollten Sie anstelle von Benutzer-ID-und Kenn Wort Informationen in der Verbindungs Zeichenfolge angeben.  
  
 Der Treiber ermittelt, dass dies der erste Befehl von **sqlbrowseconnetct** ist, und gibt die zweite Ebene der Verbindungs Attribute zurück: Server, Benutzername, Kennwort, Anwendungsname und Arbeitsstations-ID. Für das Server-Attribut wird eine Liste gültiger Servernamen zurückgegeben. Der Rückgabecode von **sqlbrowseconnetct** ist SQL_NEED_DATA. Hier ist die Ergebnis Zeichenfolge zum Durchsuchen:  
  
```  
"SERVER:Server={red,blue,green,yellow};UID:Login ID=?;PWD:Password=?;  
   *APP:AppName=?;*WSID:WorkStation ID=?;"  
```  
  
 Auf jedes Schlüsselwort in der Ergebnis Zeichenfolge zum Durchsuchen folgt ein Doppelpunkt und mindestens ein Wort vor dem Gleichheitszeichen. Diese Wörter sind der benutzerfreundliche Name, den eine Anwendung verwenden kann, um ein Dialogfeld zu erstellen. Den Schlüsselwörtern **App** und **wsid** wird ein Sternchen vorangestellt. Dies bedeutet, dass Sie optional sind. Die Schlüsselwörter " **Server**", " **UID**" und " **pwd** " sind nicht als Präfix gekennzeichnet. Werte müssen in der nächsten Such Anforderungs Zeichenfolge angegeben werden. Der Wert für das **Server** -Schlüsselwort kann einer der von **sqlbrowseconnetct** zurückgegebenen Server oder ein vom Benutzer bereitgestellter Name sein.  
  
 Die Anwendung ruft **sqlbrowseconnetct** erneut auf, gibt den grünen Server an und lässt die Schlüsselwörter **App** und **wsid** und die benutzerfreundlichen Namen nach jedem Schlüsselwort aus:  
  
```  
SQLBrowseConnect(hdbc, "SERVER=green;UID=Smith;PWD=Sesame;", SQL_NTS,  
                  BrowseResult, sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Der Treiber versucht, eine Verbindung mit dem grünen Server herzustellen. Wenn nicht schwerwiegende Fehler auftreten, z. b. ein fehlendes Schlüsselwort-Wert-Paar, gibt **sqlbrowseconnetct** SQL_NEED_DATA zurück und verbleibt in demselben Zustand wie vor dem Fehler. Die Anwendung kann **SQLGetDiagField** oder **SQLGetDiagRec** aufrufen, um den Fehler zu ermitteln. Wenn die Verbindung erfolgreich ist, gibt der Treiber SQL_NEED_DATA zurück und gibt die Ergebnis Zeichenfolge zum Durchsuchen zurück:  
  
```  
"*DATABASE:Database={master,model,pubs,tempdb};  
   *LANGUAGE:Language={us_english,Franais};"  
```  
  
 Da die Attribute in dieser Zeichenfolge optional sind, kann Sie von der Anwendung ausgelassen werden. Allerdings muss die Anwendung **sqlbrowseconnetct** erneut aufzurufen. Wenn die Anwendung auswählt, den Datenbanknamen und die Sprache auszulassen, gibt Sie eine leere Such Anforderungs Zeichenfolge an. In diesem Beispiel wählt die Anwendung die pubs-Datenbank aus und ruft **sqlbrowseconnetct** ein letztes Mal auf, wobei das Schlüsselwort " **Language** " und das Sternchen vor dem Schlüsselwort " **Database** " weggelassen werden:  
  
```  
SQLBrowseConnect(hdbc, "DATABASE=pubs;", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Da das **Database** -Attribut das abschließende Verbindungs Attribut ist, das für den Treiber erforderlich ist, ist der Suchvorgang abgeschlossen, die Anwendung ist mit der Datenquelle verbunden, und **sqlbrowseconnetct** gibt SQL_SUCCESS zurück. **Sqlbrowseconnetct** gibt auch die vollständige Verbindungs Zeichenfolge als Suchergebnis Zeichenfolge zurück:  
  
```  
"DSN=MySQLServer;SERVER=green;UID=Smith;PWD=Sesame;DATABASE=pubs;"  
```  
  
 Die vom Treiber zurückgegebene abschließende Verbindungs Zeichenfolge enthält nicht die benutzerfreundlichen Namen nach jedem Schlüsselwort und keine optionalen Schlüsselwörter, die nicht von der Anwendung angegeben werden. Die Anwendung kann diese Zeichenfolge mit **SQLDriverConnect** verwenden, um erneut eine Verbindung mit der Datenquelle auf dem aktuellen Verbindungs Handle herzustellen (nachdem die Verbindung getrennt wurde) oder um eine Verbindung mit der Datenquelle auf einem anderen Verbindungs Handle herzustellen. Beispiel:  
  
```  
SQLDriverConnect(hdbc, hwnd, BrowseResult, SQL_NTS, ConnStrOut,  
                  sizeof(ConnStrOut), &ConnStrOutLen, SQL_DRIVER_NOPROMPT);  
```
