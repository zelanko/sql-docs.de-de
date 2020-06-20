---
title: Unterstützte Konstrukte für nativ kompilierte gespeicherte Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
author: rothja
ms.author: jroth
ms.openlocfilehash: ba83dbb706b674581a35d5927639208adc061122
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85025648"
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
 [System intern kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md)  
  
  
