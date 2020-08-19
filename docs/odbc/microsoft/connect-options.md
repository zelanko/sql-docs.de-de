---
description: Verbindungsoption
title: Verbindungsoptionen | Microsoft-Dokumentation
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
ms.openlocfilehash: 22326ca650f575c6a4f0503093306d8b68581475
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483683"
---
# <a name="connect-options"></a>Verbindungsoption
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Diese Optionen ermöglichen eine Anpassung der Datenbankverbindung in einer Anwendung.  
  
|Connect-Option|Notizen|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|Wenn Sie SQL_AUTOCOMMIT_OFF auswählen, muss Ihre Anwendung mit [SQLTransact](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md)explizit ein Commit oder ein Rollback für Transaktionen ausführen.|  
|SQL_ODBC_CURSORS|Dieses Verbindungs Attribut wird im Treiber-Manager implementiert.|  
|SQL_OPT_TRACE|Dieses Verbindungs Attribut wird im Treiber-Manager implementiert.|  
|SQL_OPT_TRACEFILE|Dieses Verbindungs Attribut wird im Treiber-Manager implementiert.|  
|SQL_TRANSLATE_DLL|Gibt den folgenden Fehler zurück: "Treiber ist nicht fähig."|  
|SQL_TRANSLATE_OPTION|Ein 32-Bit-Wert, der an die Translation. dll übermittelt wird.|  
|SQL_TXN_ISOLATION|Der Treiber lässt nur SQL_TXN_READ_COMMITTED zu.<br /><br /> Die folgenden vparameams werden nicht unterstützt:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
|SQL_ATTR_ENLIST_IN_DTC|Mit diesem ODBC 3,0-Verbindungs Attribut können Sie den ODBC-Treiber für Oracle in verteilten Transaktionen verwenden, die von Microsoft-Komponenten Diensten (oder MTS, wenn Sie Windows NT verwenden) koordiniert werden. Der Schnittstellen Zeiger *pitransaction* wird der Transaktion als *vParam* -Argument bereitstellt.|  
|SQL_ATTR_CONNECTION_DEAD|Mit diesem schreibgeschützten ODBC 3,5-Verbindungs Attribut können Sie feststellen, ob die Verbindung mit dem Oracle-Server fehlgeschlagen ist. Nur Get; Festlegen von nicht möglich.|
