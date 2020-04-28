---
title: Aufheben und erteilen von Rechten bei der Verwendung gespeicherter Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 24070039-03ab-4623-a681-6308802eb399
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 469e6f0fdc6794e3bd163844e43821798aa4a617
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303986"
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Widerrufen und Erteilen von Berechtigungen beim Verwenden gespeicherter Prozeduren
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Der Microsoft ODBC Driver for Oracle gibt die folgende Fehlermeldung zurück, wenn Benutzerrechte erteilt und dann für eine Tabelle aufgehoben werden, auf die von einer gespeicherten Prozedur zugegriffen wird:  
  
 SQL_ERROR =-1  
  
 szErrorMsg = "[Microsoft] [ODBC Driver for Oracle] falsche Anzahl von Parametern"  
  
 szErrorMsg = "[Microsoft] [ODBC Driver for Oracle] Syntax Fehler oder Zugriffsverletzung"  
  
 Der aufrufsvorgang der Oracle OCI-Funktion odessp () schlägt in diesem Szenario fehl, ist jedoch erforderlich, um Standardparameter zu implementieren. Nachdem die zugrunde liegenden Tabellen Berechtigungen geändert wurden, muss die gespeicherte Prozedur vor der erneuten Ausführung erneut kompiliert werden.
