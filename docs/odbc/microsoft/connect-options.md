---
title: Optionen für die verbindungsherstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection options [ODBC]
- ODBC driver for Oracle [ODBC], connection options
- custom connection options [ODBC]
ms.assetid: abfdc133-cb33-435f-a467-fbe15444f687
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 06695bf1770c9e362decac5702dcd924d47c23bb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47750465"
---
# <a name="connect-options"></a>Verbindungsoption
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Diese Optionen ermöglichen die Anpassung der Verbindung mit der Datenbank in einer Anwendung.  
  
|Verbindungsoption|Hinweise|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|Wenn Sie auf SQL_AUTOCOMMIT_OFF auswählen, Ihre Anwendung muss explizit einen commit oder Rollback Transaktionen mit [SQLTransact](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md).|  
|SQL_ODBC_CURSORS|Dieses Verbindungsattribut wird im Treiber-Manager implementiert werden.|  
|SQL_OPT_TRACE|Dieses Verbindungsattribut wird im Treiber-Manager implementiert werden.|  
|SQL_OPT_TRACEFILE|Dieses Verbindungsattribut wird im Treiber-Manager implementiert werden.|  
|SQL_TRANSLATE_DLL|Gibt Fehler zurück: "Treiber nicht unterstützt."|  
|SQL_TRANSLATE_OPTION|Ein 32-Bit-Wert, die an die Übersetzung-DLL-Datei übergeben werden.|  
|SQL_TXN_ISOLATION|Der Treiber kann nur SQL_TXN_READ_COMMITTED.<br /><br /> Die folgenden vParams werden nicht unterstützt:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE FESTGELEGT SIND|  
|SQL_ATTR_ENLIST_IN_DTC|Dieses Verbindungsattribut ODBC 3.0 ermöglicht Ihnen die Verwendung der ODBC-Treiber für Oracle in verteilten Transaktionen, die von Microsoft Component Services (oder MTS, bei Verwendung von Windows NT) koordiniert. Es bietet den Schnittstellenzeiger auf *pITransaction* für die Transaktion als die *vParam* Argument.|  
|SQL_ATTR_CONNECTION_DEAD|Dieses Verbindungsattribut schreibgeschützte ODBC 3.5 können Sie bestimmen, ob die Verbindung mit dem Oracle-Server fehlgeschlagen ist. Erhalten Sie nur; kann nicht festgelegt.|
