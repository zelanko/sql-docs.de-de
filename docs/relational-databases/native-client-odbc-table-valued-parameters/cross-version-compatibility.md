---
title: Versionsübergreifende Kompatibilität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: bafa21a0f85e18cd30572cf00b62d81a46323100
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37429119"
---
# <a name="cross-version-compatibility"></a>Versionsübergreifende Kompatibilität
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Konflikte zwischen Versionen können auftreten, wenn Client- oder Serverinstanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Tabellenwertparameter verarbeiten sollen.  
  
 Im Allgemeinen ist die Tabellenwertparameter-Funktionalität nur für [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Clients oder höher verfügbar (unter Verwendung von SQL Server Native Client 10.0), die mit [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Servern (oder höher) verbunden sind. Neue Spalten in Resultsets von Katalogfunktionen ist nur vorhanden sein, beim Verbinden mit einem [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (oder höher) Server.  
  
 Wenn eine mit einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client kompilierte Clientanwendung Anweisungen ausführt, für die Tabellenwertparameter erwartet werden, wird dies vom Server als Datenkonvertierungsfehler erkannt, und ODBC gibt einen SQLSTATE 07006-Fehler und die Meldung "Attributverletzung beschränkter Datentypen" zurück.  
  
 Wenn eine Clientanwendung, die mit kompiliert wurde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 oder höher versucht, verwenden Sie Tabellenwertparameter beim Verbinden mit einer Server-Instanz vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client erkennt dies und SQLBindCol, SQLBindParameter SQLSetDescFields und SQLSetDescRec Aufrufe schlagen mit SQLSTATE 07006 und der Meldung fehl "Restricted Daten attributverletzung (die Version von SQLServer für diese Verbindung unterstützt keine Tabellenwertparameter)".  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenwertparameter &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
