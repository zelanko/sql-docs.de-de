---
title: Verbindungsoptionen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 25cfe2a897b0c312f91cd0c1e41ad6fa11725ab8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281310"
---
# <a name="connect-options"></a>Verbindungsoption
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Diese Optionen ermöglichen die Anpassung der Datenbankverbindung innerhalb einer Anwendung.  
  
|Connect-Option|Notizen|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|Wenn Sie SQL_AUTOCOMMIT_OFF auswählen, muss Ihre Anwendung Transaktionen mit [SQLTransact](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md)explizit festschreiben oder zurücksetzen.|  
|SQL_ODBC_CURSORS|Dieses Verbindungsattribut wird im Treiber-Manager implementiert.|  
|SQL_OPT_TRACE|Dieses Verbindungsattribut wird im Treiber-Manager implementiert.|  
|SQL_OPT_TRACEFILE|Dieses Verbindungsattribut wird im Treiber-Manager implementiert.|  
|SQL_TRANSLATE_DLL|Gibt Fehler zurück: "Treiber nicht fähig."|  
|SQL_TRANSLATE_OPTION|Ein 32-Bit-Wert, der an die Übersetzung .dll übergeben wird.|  
|SQL_TXN_ISOLATION|Der Treiber lässt nur SQL_TXN_READ_COMMITTED zu.<br /><br /> Die folgenden vParams werden nicht unterstützt:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
|SQL_ATTR_ENLIST_IN_DTC|Mit diesem ODBC 3.0-Verbindungsattribut können Sie den ODBC-Treiber für Oracle in verteilten Transaktionen verwenden, die von Microsoft Component Services (oder MTS, wenn Sie Windows NT verwenden) koordiniert werden. Es stellt den Schnittstellenzeiger *pITransaction* für die Transaktion als *vParam-Argument* bereit.|  
|SQL_ATTR_CONNECTION_DEAD|Mit diesem schreibgeschützten ODBC 3.5-Verbindungsattribut können Sie ermitteln, ob die Verbindung zum Oracle-Server fehlgeschlagen ist. Nur erhalten; kann nicht festgelegt werden.|
