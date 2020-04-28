---
title: Zuordnen des Umgebungs Handles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], environment handles
- allocating environment handles [ODBC]
- connecting to driver [ODBC], environment handles
- environment handles [ODBC]
- data sources [ODBC], environment handles
- connecting to data source [ODBC], environment handles
- handles [ODBC], environment
ms.assetid: 77b5d1d6-7eb7-428d-bf75-a5c5a325d25c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e33b850b2786960a368720deaf89a2203c7dd159
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303003"
---
# <a name="allocating-the-environment-handle"></a>Zuordnen des Umgebungshandles
Die erste Aufgabe für jede ODBC-Anwendung besteht darin, den Treiber-Manager zu laden. wie dies geschieht, hängt vom Betriebssystem ab. Beispielsweise wird auf einem Computer, auf dem Microsoft® Windows NT® Server/Windows 2000 Server, Windows NT Workstation/Windows 2000 Professional oder Microsoft Windows® 95/98 ausgeführt wird, die Anwendung entweder mit der Treiber-Manager-Bibliothek verknüpft, oder es wird **LoadLibrary** aufgerufen, um die Treiber-Manager-DLL zu laden.  
  
 Der nächste Task, der ausgeführt werden muss, bevor eine Anwendung eine andere ODBC-Funktion aufruft, besteht darin, die ODBC-Umgebung zu initialisieren und ein Umgebungs Handle wie folgt zuzuordnen:  
  
1.  Die Anwendung deklariert eine Variable vom Typ sqlhenv. Anschließend wird **sqlzugewiesene CHandle** aufgerufen und die Adresse dieser Variablen und die SQL_HANDLE_ENV-Option weitergeleitet. Beispiel:  
  
    ```  
    SQLHENV henv1;  
  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv1);  
    ```  
  
2.  Der Treiber-Manager ordnet eine Struktur zu, in der Informationen über die Umgebung gespeichert werden, und gibt das Umgebungs Handle in der Variablen zurück.  
  
 Der Treiber-Manager ruft zu diesem Zeitpunkt nicht " **sqlzuweisung** " im Treiber auf, weil er nicht weiß, welcher Treiber aufgerufen werden soll. Der Aufruf von **sqlverbinchandle** im Treiber wird verzögert, bis die Anwendung eine Funktion zum Herstellen einer Verbindung mit einer Datenquelle aufruft. Weitere Informationen finden Sie unter [Treiber-Manager-Rolle im Verbindungsprozess](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)weiter unten in diesem Abschnitt.  
  
 Wenn die Anwendung die Verwendung von ODBC beendet hat, gibt Sie das Umgebungs Handle mit **SQLFreeHandle**frei. Nach dem Freigeben der Umgebung handelt es sich um einen Anwendungs Programmierfehler, der das Handle der Umgebung in einem Rückruf einer ODBC-Funktion verwendet. Dies hat nicht definierte, aber wahrscheinlich schwerwiegende Konsequenzen.  
  
 Wenn **SQLFreeHandle** aufgerufen wird, gibt der Treiber die Struktur frei, die zum Speichern von Informationen über die Umgebung verwendet wird. Beachten Sie, dass **SQLFreeHandle** für ein Umgebungs Handle erst aufgerufen werden kann, nachdem alle Verbindungs Handles für dieses Umgebungs Handle freigegeben wurden.  
  
 Weitere Informationen zum Umgebungs Handle finden Sie unter [Umgebungs Handles](../../../odbc/reference/develop-app/environment-handles.md).
