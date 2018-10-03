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
manager: v-thobro
ms.openlocfilehash: ce59e126ce24e30e091b4a5456d8b78c84355e88
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47641768"
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
  
