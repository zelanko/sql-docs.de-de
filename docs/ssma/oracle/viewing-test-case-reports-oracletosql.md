---
title: Anzeigen von Test Case Reports (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8da14323-9dd6-4019-bf79-3e8b972a9bc0
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 2d40fd986c68968680bcd39821d762101723b87b
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56026728"
---
# <a name="viewing-test-case-reports-oracletosql"></a>Anzeigen von Testfallberichten (OracleToSQL)
Der Testfall-Bericht zeigt die Testergebnisse für die Überprüfung und allgemeine Testinformationen. Im Fall eines Testfehlers wird auch Informationen zur nicht übereinstimmenden Daten in überprüften Objekten angezeigt.  
  
## <a name="report-structure"></a>Berichtsstruktur  
Der Anfang des Berichts zeigt diese Statistiken:  
  
-   Die Gesamtanzahl der getesteten Objekte und die Anzahl der Objekte, die für die der Test erfolgreich war.  
  
-   Die Gesamtzahl der überprüften Tabellen und Fremdschlüssel, und die Anzahl von Tabellen und Fremdschlüssel, die erfolgreich abgeglichen.  
  
-   Die Startzeit, Endzeit des Testfalls und die Gesamtzeit für die Ausführung.  
  
Der Rest des Berichts werden die Informationen in vier Kategorien:  
  
**Erforderliche Komponenten Fehler**  
Zeigt aufgetretene Fehler an die **Voraussetzungen Schritt.** In der Regel wird übersprungen.  
  
**Initialisierung**  
Zeigt den Status der Ausführung als **Erfolg** oder **Fehler**.  
  
**Testergebnis-Objekte**  
Einen Vergleich der Ergebnisse (Erfolg oder Fehler) und der stimmen nicht überein, die SSMA-Tester bei einem Ausfall erkannt werden soll.  
  
**Beendigung**  
Zeigt den Status der Ausführung als **Erfolg** oder **Fehler**.  
  
## <a name="see-also"></a>Siehe auch  
[Ausführen von Testfällen &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Testen von migrierten Datenbankobjekten &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
