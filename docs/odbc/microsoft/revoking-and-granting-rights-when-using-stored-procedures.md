---
title: Widerrufen und Gewähren von Rechten bei Verwendung gespeicherter Prozeduren | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303986"
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Widerrufen und Erteilen von Berechtigungen beim Verwenden gespeicherter Prozeduren
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Der Microsoft ODBC-Treiber für Oracle gibt die folgende Fehlermeldung zurück, wenn Benutzerrechte für eine Tabelle, auf die eine gespeicherte Prozedur zugriff, erteilt und dann widerrufen werden:  
  
 SQL_ERROR=-1  
  
 szErrorMsg="[Microsoft][ODBC-Treiber für Oracle]Falsche Anzahl von Parametern"  
  
 szErrorMsg="[Microsoft][ODBC-Treiber für Oracle]Syntaxfehler oder Zugriffsverletzung"  
  
 Der Aufruf der Oracle OCI-Funktion Odessp() schlägt in diesem Szenario fehl, ist jedoch erforderlich, um Standardparameter zu implementieren. Nachdem die zugrunde liegenden Tabellenberechtigungen geändert wurden, muss die gespeicherte Prozedur neu kompiliert werden, bevor sie erneut ausgeführt wird.
