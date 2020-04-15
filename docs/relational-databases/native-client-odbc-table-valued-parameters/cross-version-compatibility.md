---
title: Versionsübergreifende Kompatibilität | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7990072ac539addf733720fd8c1eaba0652f5d70
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304509"
---
# <a name="cross-version-compatibility"></a>Versionsübergreifende Kompatibilität
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Konflikte zwischen Versionen können auftreten, wenn Client- oder Serverinstanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Tabellenwertparameter verarbeiten sollen.  
  
 Im Allgemeinen ist die Tabellenwertparameter-Funktionalität nur für [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Clients oder höher verfügbar (unter Verwendung von SQL Server Native Client 10.0), die mit [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Servern (oder höher) verbunden sind. Neue Spalten in Katalogfunktionsergebnissätzen sind nur [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] vorhanden, wenn sie mit einem (oder neueren) Server verbunden sind.  
  
 Wenn eine mit einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client kompilierte Clientanwendung Anweisungen ausführt, für die Tabellenwertparameter erwartet werden, wird dies vom Server als Datenkonvertierungsfehler erkannt, und ODBC gibt einen SQLSTATE 07006-Fehler und die Meldung "Attributverletzung beschränkter Datentypen" zurück.  
  
 Wenn eine Clientanwendung, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit Native Client 10.0 oder höher kompiliert wurde, [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]versucht, Tabellenwertparameter zu verwenden, wenn sie mit einer Serverinstanz früher als verbunden ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erkennt Native Client dies, und SQLBindCol, SQLBindParameter, SQLSetDescFields und SQLSetDescRec-Aufrufe schlagen mit SQLSTATE 07006 und der Meldung "Restricted data type attribute violation (die Version von SQL Server für diese Verbindung unterstützt keine Tabellenparameter nicht)" fehl."  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenbewertete Parameter &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
