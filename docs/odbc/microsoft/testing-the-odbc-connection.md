---
title: Testen der ODBC-Verbindung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- testing connections [ODBC]
- ODBC driver for Oracle [ODBC], testing connections
ms.assetid: 5e671665-2aba-49a7-8871-70784d8b3cc9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 02509ddb6a986ebb7796d80aca10c6f18cde6e69
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67939705"
---
# <a name="testing-the-odbc-connection"></a>Testen der ODBC-Verbindung
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Bei der Problembehandlung der ODBC-Zugriff auf Oracle 7.x und 8 RDBMS-Server, ist es möglicherweise erforderlich, zu überprüfen, ob die zugrunde liegende SQL * Net und Adapter für Oracle-Protokoll ordnungsgemäß installiert sind. Zu diesem Zweck verwenden Sie das Hilfsprogramm Oracle bereitgestellte Nettest.exe im Verzeichnis Orawin\Bin.  
  
 Nettest ist ein einfaches Dienstprogramm, das versucht, melden Sie sich an den ausgewählten Server mit nur der installierten SQL * Net-Software, die Teil der Oracle-Client ist. Das Dienstprogramm fragt einen Anmeldenamen, verbinden Sie das Kennwort und TNS Zeichenfolge. Wenn der Oracle-Client ordnungsgemäß installiert ist, wird das Hilfsprogramm "Ping erfolgreich." einfach anzeigen. Wenn die Anmeldung nicht erfolgreich war, müssen Sie mit einem Datenbankadministrator in Verbindung setzen.
