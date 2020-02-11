---
title: Unterstützte Konstrukte für nativ kompilierte gespeicherte Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc064eb8a4c6b206d3b690a4c4e7ca196c7475dc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62467874"
---
# <a name="supported-constructs-on-natively-compiled-stored-procedures"></a>Unterstützte Konstrukte für systemintern kompilierte gespeicherte Prozeduren
  In diesem Thema werden die unterstützten Konstrukte für systemintern kompilierte gespeicherte Prozeduren aufgelistet.  
  
 Informationen zu nicht unterstützten Knstrukten finden Sie unter [Von In-Memory OLTP nicht unterstützte Transact-SQL-Konstrukte](transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
## <a name="procedure-ddl"></a>Prozedur-DDL  
 Folgende werden unterstützt:  
  
-   CREATE PROCEDURE  
  
-   DROP PROCEDURE  
  
-   SCHEMABINDING (in systemintern kompilierten gespeicherten Prozeduren erforderlich)  
  
-   NATIVE_COMPILATION  
  
-   Parameter können als NOT NULL deklariert werden.  
  
-   Tabellenwertparameter.  
  
## <a name="security"></a>Sicherheit  
 Folgende werden unterstützt:  
  
-   Für Prozeduren: EXECUTE AS SELF, OWNER und Benutzer.  
  
-   GRANT- und DENY-Berechtigungen in Tabellen und Prozeduren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Nativ kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md)  
  
  
