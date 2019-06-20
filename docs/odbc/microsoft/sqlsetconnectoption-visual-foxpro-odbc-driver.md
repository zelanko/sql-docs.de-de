---
title: SQLSetConnectOption (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5a35449e-4694-4ee5-9fa1-45d5a8fe7823
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 398d098615a0453cb016286867836388fd817540
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63473032"
---
# <a name="sqlsetconnectoption-visual-foxpro-odbc-driver"></a>SQLSetConnectOption (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Teilweise  
  
 ODBC-API-Übereinstimmung: Ebene 1  
  
 Legt Optionen fest, die Aspekte der Verbindungen steuern. Diese Funktion wird teilweise unterstützt: Der Treiber unterstützt alle Werte für die *fOption* Argument unterstützt jedoch nicht einige *vParam* Werte für die *fOption* SQL_TXN_ISOLATION-Argument.  
  
 Die folgende Tabelle beschreibt nur die Argumente mit der Visual FoxPro-ODBC-Treiber-Implementierung von Verhalten **SQLSetConnectOption**.  
  
|*fOption*|Hinweise|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Wenn Sie auf SQL_AUTOCOMMIT_OFF auswählen, Ihre Anwendung muss explizit einen commit oder Rollback Transaktionen mit [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); des Visual FoxPro-ODBC-Treibers nicht automatisch nach Abschluss eine transactable-Anweisung fest. Der Treiber beginnt eine Transaktion, wenn die Anweisung transactable ist.|  
|SQL_CURRENT_QUALIFIER|Kann eine vollqualifiziert sein [Datenbank](../../odbc/microsoft/visual-foxpro-terminology.md) Namen oder den vollqualifizierten Pfad zu einem Verzeichnis mit NULL oder mehr [kostenlose Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|SQL_LOGINTIMEOUT|Gibt "Vom Treiber nicht unterstützt"-Fehler zurück.|  
|SQL_CURSORS|Gibt "Vom Treiber nicht unterstützt"-Fehler zurück.|  
|SQL_PACKET_SIZE|Gibt "Vom Treiber nicht unterstützt"-Fehler zurück.|  
|SQL_TXN_ISOLATION|Der Treiber kann nur SQL_TXN_READ_COMMITTED.<br /><br /> Die folgenden *vParam*wird nicht unterstützt:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Weitere Informationen finden Sie unter [SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md) in die *ODBC Programmer's Reference*.
