---
title: Versions übergreifende Kompatibilität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 196c99bebaf0255f095055bef6c9c6a64c41908b
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73776288"
---
# <a name="cross-version-compatibility"></a>Versionsübergreifende Kompatibilität
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Konflikte zwischen Versionen können auftreten, wenn Client- oder Serverinstanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Tabellenwertparameter verarbeiten sollen.  
  
 Im Allgemeinen ist die Tabellenwertparameter-Funktionalität nur für [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Clients oder höher verfügbar (unter Verwendung von SQL Server Native Client 10.0), die mit [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Servern (oder höher) verbunden sind. Neue Spalten in Resultsets von Katalog Funktionen sind nur vorhanden, wenn eine Verbindung mit einem [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Server (oder höher) hergestellt wird.  
  
 Wenn eine mit einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client kompilierte Clientanwendung Anweisungen ausführt, für die Tabellenwertparameter erwartet werden, wird dies vom Server als Datenkonvertierungsfehler erkannt, und ODBC gibt einen SQLSTATE 07006-Fehler und die Meldung "Attributverletzung beschränkter Datentypen" zurück.  
  
 Wenn eine Client Anwendung, die mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10,0 oder höher kompiliert wurde, versucht, Tabellenwert Parameter zu verwenden, wenn eine Verbindung mit einer Serverinstanz hergestellt wird, die älter als [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]ist, wird diese von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client erkannt, und SQLBindCol, SQLBindParameter, Sqlsetdescfields-und SQLSetDescRec-Aufrufe schlagen mit SQLState 07006 und der Meldung "Attribut Verletzung eingeschränkter Datentypen (die Version von SQL Server für diese Verbindung unterstützt keine Tabellenwert Parameter)" fehl.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenwert Parameter &#40;(ODBC)&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
