---
title: Testen der ODBC-Verbindung | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303111"
---
# <a name="testing-the-odbc-connection"></a>Testen der ODBC-Verbindung
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Bei der Fehlerbehebung beim ODBC-Zugriff auf Oracle 7.x- und Oracle8 RDBMS-Server muss möglicherweise überprüft werden, ob die zugrunde liegenden SQL*Net- und Oracle-Protokolladapter ordnungsgemäß installiert sind. Verwenden Sie dazu das von Oracle bereitgestellte Dienstprogramm Nettest.exe im Verzeichnis Orawin-Bin.  
  
 Nettest ist ein einfaches Dienstprogramm, das versucht, sich am ausgewählten Server anzumelden, indem nur die installierte SQL*Net-Software verwendet wird, die Teil des Oracle-Clients ist. Das Dienstprogramm fragt nach einem Anmeldenamen, einem Kennwort und einer TNS-Verbindungszeichenfolge. Wenn der Oracle-Client ordnungsgemäß installiert ist, zeigt das Dienstprogramm einfach "Ping erfolgreich" an. Wenn die Anmeldung nicht erfolgreich war, müssen Sie sich an einen Datenbankadministrator wenden.
