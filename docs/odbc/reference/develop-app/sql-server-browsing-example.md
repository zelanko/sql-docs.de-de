---
title: SQL Server-Browsing-Beispiel | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301981"
---
# <a name="sql-server-browsing-example"></a>SQL Server-Suchbeispiel
Das folgende Beispiel zeigt, wie **SQLBrowseConnect** verwendet werden kann, um die Verbindungen zu durchsuchen, die mit einem Treiber für SQL Server verfügbar sind. Zunächst fordert die Anwendung ein Verbindungshandle an:  
  
```  
SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
```  
  
 Als Nächstes ruft die Anwendung **SQLBrowseConnect** auf und gibt den SQL Server-Treiber mithilfe der von **SQLDrivers**zurückgegebenen Treiberbeschreibung an:  
  
```  
SQLBrowseConnect(hdbc, "DRIVER={SQL Server};", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Da dies der erste Aufruf von **SQLBrowseConnect**ist, lädt der Treiber-Manager den SQL Server-Treiber und ruft die **SQLBrowseConnect-Funktion** des Treibers mit den gleichen Argumenten auf, die er von der Anwendung erhalten hat.  
  
> [!NOTE]  
>  Wenn Sie eine Verbindung zu einem Datenquellenanbieter herstellen, `Trusted_Connection=yes` der die Windows-Authentifizierung unterstützt, sollten Sie anstelle von Benutzer-ID- und Kennwortinformationen in der Verbindungszeichenfolge angeben.  
  
 Der Treiber stellt fest, dass dies der erste Aufruf von **SQLBrowseConnect** ist, und gibt die zweite Ebene der Verbindungsattribute zurück: Server, Benutzername, Kennwort, Anwendungsname und Arbeitsstations-ID. Für das Serverattribut wird eine Liste gültiger Servernamen zurückgegeben. Der Rückgabecode von **SQLBrowseConnect** ist SQL_NEED_DATA. Hier ist die Suchergebniszeichenfolge:  
  
```  
"SERVER:Server={red,blue,green,yellow};UID:Login ID=?;PWD:Password=?;  
   *APP:AppName=?;*WSID:WorkStation ID=?;"  
```  
  
 Auf jedes Schlüsselwort in der Suchergebniszeichenfolge folgen ein Doppelpunkt und ein oder mehrere Wörter vor dem Gleichheitszeichen. Diese Wörter sind der benutzerfreundliche Name, den eine Anwendung zum Erstellen eines Dialogfelds verwenden kann. Den Schlüsselwörtern **APP** und **WSID** wird ein Sternchen vorangestellt, d. h., sie sind optional. Den Schlüsselwörtern **SERVER**, **UID**und **PWD** wird kein Sternchen vorangestellt. Werte müssen für sie in der nächsten Suchanforderungszeichenfolge angegeben werden. Der Wert für das **Schlüsselwort SERVER** kann einer der von **SQLBrowseConnect** zurückgegebenen Server oder ein vom Benutzer angegebener Name sein.  
  
 Die Anwendung ruft **SQLBrowseConnect** erneut auf, gibt den grünen Server an und lässt die **Schlüsselwörter APP** und **WSID** sowie die benutzerfreundlichen Namen nach jedem Schlüsselwort weg:  
  
```  
SQLBrowseConnect(hdbc, "SERVER=green;UID=Smith;PWD=Sesame;", SQL_NTS,  
                  BrowseResult, sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Der Treiber versucht, eine Verbindung mit dem grünen Server herzustellen. Wenn nicht schwerwiegende Fehler auftreten, z. B. ein fehlendes Schlüsselwortwertpaar, gibt **SQLBrowseConnect** SQL_NEED_DATA zurück und verbleibt im gleichen Zustand wie vor dem Fehler. Die Anwendung kann **SQLGetDiagField** oder **SQLGetDiagRec** aufrufen, um den Fehler zu ermitteln. Wenn die Verbindung erfolgreich ist, gibt der Treiber SQL_NEED_DATA zurück und gibt die Suchergebniszeichenfolge zurück:  
  
```  
"*DATABASE:Database={master,model,pubs,tempdb};  
   *LANGUAGE:Language={us_english,Franais};"  
```  
  
 Da die Attribute in dieser Zeichenfolge optional sind, kann die Anwendung sie weglassen. Die Anwendung muss **SQLBrowseConnect** jedoch erneut aufrufen. Wenn die Anwendung den Datenbanknamen und die Datenbanksprache weglässt, gibt sie eine leere Suchanforderungszeichenfolge an. In diesem Beispiel wählt die Anwendung die pubs-Datenbank aus und ruft **SQLBrowseConnect** ein letztes Mal auf, ohne das **LANGUAGE-Schlüsselwort** und das Sternchen vor dem DATABASE-Schlüsselwort: **DATABASE**  
  
```  
SQLBrowseConnect(hdbc, "DATABASE=pubs;", SQL_NTS, BrowseResult,  
                  sizeof(BrowseResult), &BrowseResultLen);  
```  
  
 Da das **DATABASE-Attribut** das letzte Verbindungsattribut ist, das vom Treiber benötigt wird, ist der Browservorgang abgeschlossen, die Anwendung ist mit der Datenquelle verbunden, und **SQLBrowseConnect** gibt SQL_SUCCESS zurück. **SQLBrowseConnect** gibt auch die vollständige Verbindungszeichenfolge als Suchergebniszeichenfolge zurück:  
  
```  
"DSN=MySQLServer;SERVER=green;UID=Smith;PWD=Sesame;DATABASE=pubs;"  
```  
  
 Die endgültige Verbindungszeichenfolge, die vom Treiber zurückgegeben wird, enthält weder die benutzerfreundlichen Namen nach jedem Schlüsselwort noch optionale Schlüsselwörter, die nicht von der Anwendung angegeben wurden. Die Anwendung kann diese Zeichenfolge mit **SQLDriverConnect** verwenden, um eine erneute Verbindung mit der Datenquelle am aktuellen Verbindungshandle (nach dem Trennen) oder zum Herstellen einer Verbindung mit der Datenquelle in einem anderen Verbindungshandle herzustellen. Beispiel:  
  
```  
SQLDriverConnect(hdbc, hwnd, BrowseResult, SQL_NTS, ConnStrOut,  
                  sizeof(ConnStrOut), &ConnStrOutLen, SQL_DRIVER_NOPROMPT);  
```
