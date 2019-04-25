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
manager: craigg
ms.openlocfilehash: 543ab436ac7dca5e0d5965220cd90a798afb5ccf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62633175"
---
# <a name="testing-the-odbc-connection"></a>Testen der ODBC-Verbindung
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Bei der Problembehandlung der ODBC-Zugriff auf Oracle 7.x und 8 RDBMS-Server, ist es möglicherweise erforderlich, zu überprüfen, ob die zugrunde liegende SQL * Net und Adapter für Oracle-Protokoll ordnungsgemäß installiert sind. Zu diesem Zweck verwenden Sie das Hilfsprogramm Oracle bereitgestellte Nettest.exe im Verzeichnis Orawin\Bin.  
  
 Nettest ist ein einfaches Dienstprogramm, das versucht, melden Sie sich an den ausgewählten Server mit nur der installierten SQL * Net-Software, die Teil der Oracle-Client ist. Das Dienstprogramm fragt einen Anmeldenamen, verbinden Sie das Kennwort und TNS Zeichenfolge. Wenn der Oracle-Client ordnungsgemäß installiert ist, wird das Hilfsprogramm "Ping erfolgreich." einfach anzeigen. Wenn die Anmeldung nicht erfolgreich war, müssen Sie mit einem Datenbankadministrator in Verbindung setzen.
