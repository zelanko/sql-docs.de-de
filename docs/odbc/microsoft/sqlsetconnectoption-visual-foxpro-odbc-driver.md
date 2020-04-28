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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2af208663f1e91250faad0ca9538b76bcec43b06
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301501"
---
# <a name="sqlsetconnectoption-visual-foxpro-odbc-driver"></a>SQLSetConnectOption (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: partiell  
  
 ODBC-API-Konformität: Ebene 1  
  
 Legt Optionen fest, die die Aspekte von Verbindungen steuern. Diese Funktion wird teilweise unterstützt: der Treiber unterstützt alle Werte für das *fOption* -Argument, unterstützt jedoch einige der *vParam* -Werte für das *fOption* -Argument SQL_TXN_ISOLATION nicht.  
  
 In der folgenden Tabelle werden nur die Argumente beschrieben, deren Verhalten spezifisch für die Implementierung von **SQLSetConnectOption**des Visual FoxPro-ODBC-Treibers ist.  
  
|*fOption*|Bemerkungen|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Wenn Sie SQL_AUTOCOMMIT_OFF auswählen, muss Ihre Anwendung mit [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); einen expliziten Commit oder Rollback für Transaktionen ausführen. der Visual FoxPro-ODBC-Treiber führt einen Commit für eine fähige-Anweisung nach Abschluss nicht automatisch aus. Der Treiber startet eine Transaktion, wenn die Anweisung Transaktions basiert ist.|  
|SQL_CURRENT_QUALIFIER|Kann ein voll qualifizierter [Datenbankname](../../odbc/microsoft/visual-foxpro-terminology.md) oder ein voll qualifizierter Pfad zu einem Verzeichnis sein, das 0 (null) oder mehr [freie Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md)enthält.|  
|SQL_LOGINTIMEOUT|Gibt den Fehler "Treiber nicht fähig" zurück.|  
|SQL_CURSORS|Gibt den Fehler "Treiber nicht fähig" zurück.|  
|SQL_PACKET_SIZE|Gibt den Fehler "Treiber nicht fähig" zurück.|  
|SQL_TXN_ISOLATION|Der Treiber lässt nur SQL_TXN_READ_COMMITTED zu.<br /><br /> Die folgenden *vParam*-s werden nicht unterstützt:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Weitere Informationen finden Sie unter [SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md) in der *ODBC Programmer es Reference*.
