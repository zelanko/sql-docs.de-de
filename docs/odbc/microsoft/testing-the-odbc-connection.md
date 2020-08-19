---
description: Testen der ODBC-Verbindung
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
ms.openlocfilehash: 61a471af3c5681ca58ca3268ad4512ee80abb9cb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421544"
---
# <a name="testing-the-odbc-connection"></a>Testen der ODBC-Verbindung
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Bei der Problembehandlung des ODBC-Zugriffs auf Oracle 7. x-und Oracle8 RDBMS-Server muss möglicherweise überprüft werden, ob die zugrunde liegenden SQL * Net-und Oracle-Protokoll Adapter ordnungsgemäß installiert sind. Verwenden Sie hierzu das von Oracle bereitgestellte Dienstprogramm Nettest.exe im Verzeichnis orawin\bin.  
  
 NetTest ist ein einfaches Hilfsprogramm, das versucht, sich mit der installierten SQL * Net-Software, die zum Oracle-Client gehört, beim ausgewählten Server anzumelden. Das Hilfsprogramm fordert einen Anmelde Namen, ein Kennwort und eine TNS-Verbindungs Zeichenfolge an. Wenn der Oracle-Client ordnungsgemäß installiert ist, zeigt das Hilfsprogramm einfach "Ping erfolgreich" an. Wenn die Anmeldung nicht erfolgreich war, müssen Sie sich an einen Datenbankadministrator wenden.
