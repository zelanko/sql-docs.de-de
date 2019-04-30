---
title: Zuordnen des Umgebungshandles | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a8eefe5bc6678462099afda8381d6b16bd076dd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63287667"
---
# <a name="allocating-the-environment-handle"></a>Zuordnen des Umgebungshandles
Die erste Aufgabe für jede ODBC-Anwendung ist beim Laden der Treiber-Manager. wie Sie dies tun, ist abhängig vom Betriebssystem. Z. B. auf einem Computer unter Microsoft® Windows NT® Server/Windows 2000 Server, Windows NT Workstation/Windows 2000 Professional oder Microsoft Windows® 95/98, die Anwendung entweder enthält links zu der Treiber-Manager-Bibliothek oder Aufrufe  **LoadLibrary** zum Laden der DLL-Treiber-Manager.  
  
 Die nächste Aufgabe, die ausgeführt werden muss, bevor eine Anwendung eine ODBC-Funktion aufrufen kann, ist die ODBC-Umgebung zu initialisieren, und ordnen Sie ein Umgebungshandle wie folgt:  
  
1.  Die Anwendung deklariert eine Variable vom Typ SQLHENV. Es ruft dann **SQLAllocHandle** und übergibt die Adresse dieser Variablen und die SQL_HANDLE_ENV-Option. Zum Beispiel:  
  
    ```  
    SQLHENV henv1;  
  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv1);  
    ```  
  
2.  Der Treiber-Manager weist eine Struktur zum Speichern von Informationen über die Umgebung und gibt das Umgebungshandle in der Variablen.  
  
 Der Treiber-Manager wird nicht aufgerufen. **SQLAllocHandle** im Treiber auf dieser Zeit, da er nicht, welcher Treiber weiß für das aufrufen. Erfolgt eine Verzögerung, Aufrufen **SQLAllocHandle** im Treiber, bis die Anwendung eine Funktion für die Verbindung mit einer Datenquelle aufruft. Weitere Informationen finden Sie unter [Treiber-Manager-Rolle in der Verbindungsprozess](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)weiter unten in diesem Abschnitt.  
  
 Wenn die Anwendung mithilfe von ODBC abgeschlossen ist, gibt das Umgebungshandle mit frei **SQLFreeHandle**. Nach der Freigabe der der umgebungs, ist es ein anwendungsprogrammierungsfehler Fehler Handle von der Umgebung in einem Aufruf von einer ODBC-Funktion zu verwenden. Dies ist also nicht definierte, aber wahrscheinlich schwerwiegende Folgen.  
  
 Wenn **SQLFreeHandle** aufgerufen wird, wird der Treiberversionen, die die Struktur verwendet, um Informationen über die Umgebung zu speichern. Beachten Sie, dass **SQLFreeHandle** kann nicht für ein Umgebungshandle erst aufgerufen werden, nachdem alle Verbindungshandles, die auf diesem Umgebungshandle freigegeben wurden.  
  
 Weitere Informationen über das Umgebungshandle finden Sie unter [Umgebung verarbeitet](../../../odbc/reference/develop-app/environment-handles.md).
