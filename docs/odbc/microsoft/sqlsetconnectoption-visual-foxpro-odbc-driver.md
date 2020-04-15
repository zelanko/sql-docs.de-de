---
title: SQLSetConnectOption (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301501"
---
# <a name="sqlsetconnectoption-visual-foxpro-odbc-driver"></a>SQLSetConnectOption (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: Teilweise  
  
 ODBC-API-Konformität: Ebene 1  
  
 Legt Optionen fest, die Aspekte von Verbindungen steuern. Diese Funktion wird teilweise unterstützt: Der Treiber unterstützt alle Werte für das *fOption-Argument,* unterstützt jedoch einige *vParam-Werte* für das *fOption-Argument* SQL_TXN_ISOLATION nicht.  
  
 In der folgenden Tabelle werden nur die Argumente mit einem verhalten beschrieben, das für die Visual FoxPro ODBC-Treiberimplementierung von **SQLSetConnectOption**spezifisch ist.  
  
|*fOption*|Bemerkungen|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Wenn Sie SQL_AUTOCOMMIT_OFF auswählen, muss Ihre Anwendung Transaktionen mit [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md)explizit festschreiben oder zurücksetzen. Der Visual FoxPro ODBC-Treiber überträgt nach Abschluss keine automatisch übertragbare Anweisung. Der Treiber beginnt eine Transaktion, wenn die Anweisung transaktionierbar ist.|  
|SQL_CURRENT_QUALIFIER|Kann ein vollqualifizierter [Datenbankname](../../odbc/microsoft/visual-foxpro-terminology.md) oder ein vollqualifizierter Pfad zu einem Verzeichnis mit null oder mehr [freien Tabellen](../../odbc/microsoft/visual-foxpro-terminology.md)sein.|  
|SQL_LOGINTIMEOUT|Gibt den Fehler "Driver not capable" zurück.|  
|SQL_CURSORS|Gibt den Fehler "Driver not capable" zurück.|  
|SQL_PACKET_SIZE|Gibt den Fehler "Driver not capable" zurück.|  
|SQL_TXN_ISOLATION|Der Treiber lässt nur SQL_TXN_READ_COMMITTED zu.<br /><br /> Die folgenden *vParam*s werden nicht unterstützt:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Weitere Informationen finden Sie unter [SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md) in der *ODBC-Programmiererreferenz*.
