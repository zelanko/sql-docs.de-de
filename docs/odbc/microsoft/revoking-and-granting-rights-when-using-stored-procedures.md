---
title: Entziehen und Erteilen von Berechtigungen, bei Verwendung von gespeicherten Prozeduren | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67987956"
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Widerrufen und Erteilen von Berechtigungen beim Verwenden gespeicherter Prozeduren
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Der Microsoft ODBC-Treiber für Oracle wird die folgende Fehlermeldung zurück, wenn Benutzerrechte gewährt und Sie dann für eine Tabelle, die von einer gespeicherten Prozedur zugegriffen widerrufen werden:  
  
 SQL_ERROR=-1  
  
 von SQLDiagRec() = "Falsche Anzahl von Parametern [Microsoft] [ODBC-Treiber für Oracle]"  
  
 von SQLDiagRec() = "[Microsoft] [ODBC-Treiber für Oracle]-Syntaxfehler oder zugriffsverletzung"  
  
 Der Aufruf an die Oracle OCI-Funktion Odessp() in diesem Szenario schlägt fehl, jedoch ist erforderlich, um die Standardparameter zu implementieren. Nachdem die zugrunde liegende Tabellenberechtigungen geändert werden, muss die gespeicherte Prozedur neu kompiliert werden, bevor Sie ihn erneut ausführen.
