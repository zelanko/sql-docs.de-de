---
description: SQLGetConnectOption (Visual FoxPro-ODBC-Treiber)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dd22ec3862ff2f0f3c4f7b5aa9dbeff53a5d8cfe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411786"
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
