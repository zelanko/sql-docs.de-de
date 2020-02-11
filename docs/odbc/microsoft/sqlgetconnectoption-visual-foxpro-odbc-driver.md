---
title: SQLGetConnectOption (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetConnectOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5703eb39-f3b2-4f3a-8676-a5625ae29a41
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c17cd473d3c96032817c2b183bf65fe360cf3cdc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053683"
---
# <a name="sqlgetconnectoption-visual-foxpro-odbc-driver"></a>SQLGetConnectOption (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: partiell  
  
 ODBC-API-Konformität: Ebene 1  
  
 Gibt die aktuelle Einstellung einer Verbindungs Option zurück. Diese Funktion wird teilweise unterstützt: der Treiber unterstützt alle Werte für das *fOption* -Argument, unterstützt jedoch einige der *vParam* -Werte für das *fOption* -Argument SQL_TXN_ISOLATION nicht.  
  
 In der folgenden Tabelle werden nur die Argumente beschrieben, deren Verhalten spezifisch für die Implementierung von **SQLGetConnectOption**des Visual FoxPro-ODBC-Treibers ist.  
  
|*fOption*|Bemerkungen|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Wenn Sie SQL_AUTOCOMMIT_OFF auswählen, muss Ihre Anwendung mit [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); einen expliziten Commit oder Rollback für Transaktionen ausführen. der Visual FoxPro-ODBC-Treiber führt einen Commit für eine fähige-Anweisung nach Abschluss nicht automatisch aus. Der Treiber startet eine Transaktion, wenn die Anweisung Transaktions basiert ist.|  
|SQL_CURRENT_QUALIFIER|Kann ein voll qualifizierter Daten Bank Name (DBC-Datei) oder ein voll qualifizierter Pfad zu einem Verzeichnis sein, das keine oder mehrere Tabellen (DBF-Dateien) enthält.|  
|SQL_LOGINTIMEOUT|Gibt den Fehler "Treiber nicht fähig" zurück.|  
|SQL_CURSORS|Gibt den Fehler "Treiber nicht fähig" zurück.|  
|SQL_PACKET_SIZE|Gibt den Fehler "Treiber nicht fähig" zurück.|  
|SQL_TXN_ISOLATION|Der Treiber lässt nur SQL_TXN_READ_COMMITTED zu.<br /><br /> Die folgenden *vParam*-s werden nicht unterstützt:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Weitere Informationen finden Sie unter [SQLGetConnectOption](../../odbc/reference/syntax/sqlgetconnectoption-function.md) in der *ODBC Programmer es Reference*.
