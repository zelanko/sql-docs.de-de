---
title: Versions übergreifende Kompatibilität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f23b0f43b32d737f03cb7c9b00368558e89e9288
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63199996"
---
# <a name="cross-version-compatibility"></a>Versionsübergreifende Kompatibilität
  Konflikte zwischen Versionen können auftreten, wenn Client- oder Serverinstanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Tabellenwertparameter verarbeiten sollen.  
  
 Im Allgemeinen ist die Tabellenwertparameter-Funktionalität nur für [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Clients oder höher verfügbar (unter Verwendung von SQL Server Native Client 10.0), die mit [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Servern (oder höher) verbunden sind. Neue Spalten in Resultsets von Katalog Funktionen sind nur vorhanden, wenn eine [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Verbindung mit einem-Server (oder höher) besteht.  
  
 Wenn eine mit einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client kompilierte Clientanwendung Anweisungen ausführt, für die Tabellenwertparameter erwartet werden, wird dies vom Server als Datenkonvertierungsfehler erkannt, und ODBC gibt einen SQLSTATE 07006-Fehler und die Meldung "Attributverletzung beschränkter Datentypen" zurück.  
  
 Wenn eine Client Anwendung, die mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10,0 oder höher kompiliert wurde, versucht, Tabellenwert Parameter zu verwenden [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], wenn eine Verbindung mit einer Server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz vor hergestellt wurde, dies wird von Native Client erkannt, und die Aufrufe SQLBindCol, SQLBindParameter, sqlsetdescfields und SQLSetDescRec schlagen mit SQLState 07006 und der Meldung "Attribut Verletzung eingeschränkter Datentypen (die Version von SQL Server für diese Verbindung unterstützt keine Tabellenwert Parameter)" fehl.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenwert Parameter &#40;ODBC-&#41;](table-valued-parameters-odbc.md)  
  
  
