---
title: Unterstützte Konstrukte für systemintern kompilierte gespeicherte Prozeduren | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6b21f47e-bceb-4054-8b3c-9d39bb9583c0
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: jhubbard
ms.openlocfilehash: c54f811f2257adcb5c08f1741018be3211c1e874
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162468"
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
  
## <a name="security"></a>Security  
 Folgende werden unterstützt:  
  
-   Für Prozeduren: EXECUTE AS SELF, OWNER und Benutzer.  
  
-   GRANT- und DENY-Berechtigungen in Tabellen und Prozeduren.  
  
## <a name="see-also"></a>Siehe auch  
 [Systemintern kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md)  
  
  