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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 91fcf722554fe1840465329e707c792a6bbab6db
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67987956"
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Widerrufen und Erteilen von Berechtigungen beim Verwenden gespeicherter Prozeduren
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Der Microsoft ODBC Driver for Oracle gibt die folgende Fehlermeldung zurück, wenn Benutzerrechte erteilt und dann für eine Tabelle aufgehoben werden, auf die von einer gespeicherten Prozedur zugegriffen wird:  
  
 SQL_ERROR =-1  
  
 szErrorMsg = "[Microsoft] [ODBC Driver for Oracle] falsche Anzahl von Parametern"  
  
 szErrorMsg = "[Microsoft] [ODBC Driver for Oracle] Syntax Fehler oder Zugriffsverletzung"  
  
 Der aufrufsvorgang der Oracle OCI-Funktion odessp () schlägt in diesem Szenario fehl, ist jedoch erforderlich, um Standardparameter zu implementieren. Nachdem die zugrunde liegenden Tabellen Berechtigungen geändert wurden, muss die gespeicherte Prozedur vor der erneuten Ausführung erneut kompiliert werden.
