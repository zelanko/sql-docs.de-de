---
title: Ausführen von Testfällen (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fc208cdb-7373-4f6b-8f6c-cdff9d3dcd02
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 5368db04a4f5442620a8f347608bf5aded86703b
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982372"
---
# <a name="running-test-cases-oracletosql"></a>Ausführen von Testfällen (OracleToSQL)
Wenn SSMA Tester einen Testfall ausgeführt wird, führt die Objekte, die zu Testzwecken ausgewählt, und erstellt einen Bericht über die Ergebnisse der Überprüfung. Wenn die Ergebnisse auf beiden Plattformen identisch sind, war der Test erfolgreich. Die Entsprechung von Objekten zwischen Oracle und [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] richtet sich danach die schemazuordnung Einstellungen für das aktuelle SSMA-Projekt.  
  
Eine unerlässliche Anforderung für der Test erfolgreich ist, dass alle Oracle-Objekte konvertiert und in die Zieldatenbank geladen werden. Darüber hinaus sollten die Daten der migriert werden, damit der Inhalt der Tabellen auf beiden Plattformen synchronisiert werden.  
  
## <a name="run-test-case"></a>Testfall ausführen  
So führen Sie die vorbereiteten Testfall aus:  
  
1.  Klicken Sie auf die **ausführen** Schaltfläche.  
  
2.  In der **Herstellen einer Verbindung mit Oracle** Dialogfeld Geben Sie die Verbindungsinformationen, und klicken Sie dann auf **Connect**.  
  
Wenn der Test abgeschlossen ist, wird der Testfall-Bericht erstellt. Klicken Sie auf die **Bericht** Schaltfläche zum Anzeigen der [Testfall Bericht](http://msdn.microsoft.com/8da14323-9dd6-4019-bf79-3e8b972a9bc0). Das Ergebnis des Tests (Bericht "Testfall") wird automatisch gespeichert, der [Ergebnisrepository](http://msdn.microsoft.com/f941cce4-d3e3-4aeb-a88a-4f101a97a9f4) für die spätere Verwendung.  
  
## <a name="test-case-execution-steps"></a>Testfall-Ausführungsschritte  
  
### <a name="prerequisites"></a>Erforderliche Komponenten  
SSMA-Tester wird überprüft, ob alle Voraussetzungen, für die testausführung vor Beginn des Tests erfüllt sind. Wenn bestimmte Bedingungen nicht erfüllt sind, wird eine Fehlermeldung angezeigt.  
  
### <a name="initialization"></a>Initialisierung  
An diesem Punkt erstellt SSMA Tester zusätzliche Objekte (Tabellen, Trigger und Sichten), in der Oracle-Server SSMATESTER_ORACLE Schema. Sie können die Ablaufverfolgung-Änderungen in die betroffenen Objekte für die Überprüfung ausgewählt.  
  
Wird davon ausgegangen Sie, dass die überprüfte Tabelle USER_TABLE heißt. Für eine Tabelle werden die folgenden zusätzlichen Objekte in Oracle erstellt.  
  
||||  
|-|-|-|  
|Name|Typ|Description|  
|USER_TABLE$ "TRG"|Trigger (trigger)|Trigger, die Überwachung der Änderungen in der Tabelle überprüft werden.|  
|USER_TABLE$ AUD|-Tabelle|Die Tabelle, in dem Zeilen gelöschte und überschriebene gespeichert werden.|  
|USER_TABLE$ AUDID|-Tabelle|Die Tabelle, in dem ein neue und geänderte Zeilen gespeichert werden.|  
|USER_TABLE|Ansicht|Vereinfachte Darstellung der tabellenänderungen.|  
|USER_TABLE$ NEU|Ansicht|Vereinfachte Darstellung von Zeilen eingefügt und überschrieben.|  
|USER_TABLE$ NEW_ID|Ansicht|ID des eingefügten und geänderter Zeilen.|  
|USER_TABLE$ ALTE|Ansicht|Vereinfachte Darstellung von Zeilen gelöscht und überschrieben.|  
  
Das folgende Objekt wird erstellt, in das Schema der überprüften Tabelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
||||  
|-|-|-|  
|Name|Typ|Description|  
|USER_TABLE$ "TRG"|Trigger (trigger)|Trigger, die Überwachung der Änderungen in der Tabelle überprüft werden.|  
  
Und die folgenden Objekte werden erstellt, auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]in der Datenbank Ssmatesterdb.  
  
||||  
|-|-|-|  
|Name|Typ|Description|  
|USER_TABLE$ Aud|-Tabelle|Die Tabelle, in dem Zeilen gelöschte und überschriebene gespeichert werden.|  
|USER_TABLE$ AudID|-Tabelle|Die Tabelle, in dem ein neue und geänderte Zeilen gespeichert werden.|  
|USER_TABLE|Ansicht|Vereinfachte Darstellung der tabellenänderungen.|  
|USER_TABLE$new|Ansicht|Vereinfachte Darstellung von Zeilen eingefügt und überschrieben.|  
|USER_TABLE$new_id|Ansicht|ID des eingefügten und geänderter Zeilen.|  
|USER_TABLE$old|Ansicht|Vereinfachte Darstellung von Zeilen gelöscht und überschrieben.|  
  
### <a name="test-object-calls"></a>Testen der Aufrufe  
SSMA-Tester an dieser Stelle ruft jedes Objekt, das für die Tests ausgewählt haben, werden die Ergebnisse verglichen und zeigt den Bericht.  
  
### <a name="finalization"></a>Beendigung  
Während der Finalisierung bereinigt SSMA Tester die zusätzlichen Objekte, erstellt die **Initialisierung** Schritt.  
  
## <a name="next-step"></a>Nächster Schritt  
[Anzeigen von Berichten für Testfall &#40;OracleToSQL&#41;](../../ssma/oracle/viewing-test-case-reports-oracletosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Auswählen und Konfigurieren von Objekten mit Test &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
[Auswählen und Konfigurieren von betroffenen Objekten &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
[Testen von migrierten Datenbankobjekten &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
