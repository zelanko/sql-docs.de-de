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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8de19af2b50a58eef22ec074a308f86717278a48
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303111"
---
# <a name="testing-the-odbc-connection"></a>Testen der ODBC-Verbindung
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Bei der Problembehandlung des ODBC-Zugriffs auf Oracle 7. x-und Oracle8 RDBMS-Server muss möglicherweise überprüft werden, ob die zugrunde liegenden SQL * Net-und Oracle-Protokoll Adapter ordnungsgemäß installiert sind. Verwenden Sie hierzu das von Oracle bereitgestellte Hilfsprogramm NetTest. exe im Verzeichnis orawin\bin.  
  
 NetTest ist ein einfaches Hilfsprogramm, das versucht, sich mit der installierten SQL * Net-Software, die zum Oracle-Client gehört, beim ausgewählten Server anzumelden. Das Hilfsprogramm fordert einen Anmelde Namen, ein Kennwort und eine TNS-Verbindungs Zeichenfolge an. Wenn der Oracle-Client ordnungsgemäß installiert ist, zeigt das Hilfsprogramm einfach "Ping erfolgreich" an. Wenn die Anmeldung nicht erfolgreich war, müssen Sie sich an einen Datenbankadministrator wenden.
