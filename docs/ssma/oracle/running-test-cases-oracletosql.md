---
title: Ausführen von Test Fällen (oracleto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: fc208cdb-7373-4f6b-8f6c-cdff9d3dcd02
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 79d3905c130e37c973a79a40369f97ae8f30ac5b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68266547"
---
# <a name="running-test-cases-oracletosql"></a>Ausführen von Testfällen (OracleToSQL)
Wenn der SSMA-Tester einen Testfall ausführt, führt er die für das Testen ausgewählten Objekte aus und erstellt einen Bericht über Überprüfungs Ergebnisse. Wenn die Ergebnisse auf beiden Plattformen identisch sind, war der Test erfolgreich. Die Entsprechung von Objekten zwischen Oracle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und wird anhand der Schema-Mapping-Einstellungen für das aktuelle SSMA-Projekt festgelegt.  
  
Eine erforderliche Anforderung für einen erfolgreichen Test besteht darin, dass alle Oracle-Objekte konvertiert und in die Zieldatenbank geladen werden. Außerdem sollten die Tabellendaten migriert werden, damit die Inhalte der Tabellen auf beiden Plattformen synchronisiert werden.  
  
## <a name="run-test-case"></a>Testfall ausführen  
So führen Sie den vorbereiteten Testfall aus  
  
1.  Klicken Sie auf die Schaltfläche **Ausführen**.  
  
2.  Geben Sie im Dialogfeld **mit Oracle verbinden** die Verbindungsinformationen ein, und klicken Sie dann auf **verbinden**.  
  
Wenn der Test fertig ist, wird der Test Fallbericht erstellt. Klicken Sie auf die Schaltfläche **Bericht** , um den [Test Fallbericht](viewing-test-case-reports-oracletosql.md)anzuzeigen. Das Ergebnis des Tests (Test Fallbericht) wird für die spätere Verwendung automatisch im [Testergebnisse Repository](using-test-repositories-oracletosql.md) gespeichert.  
  
## <a name="test-case-execution-steps"></a>Testfall-Ausführungs Schritte  
  
### <a name="prerequisites"></a>Voraussetzungen  
Der SSMA-Tester prüft, ob alle Voraussetzungen für die Testausführung vor dem Start des Tests erfüllt sind. Wenn einige Bedingungen nicht erfüllt sind, wird eine Fehlermeldung angezeigt.  
  
### <a name="initialization"></a>Initialisierung  
In diesem Schritt erstellt SSMA Tester Hilfsobjekte (Tabellen, Trigger und Sichten) im SSMATESTER_ORACLE Schema des Oracle-Servers. Sie ermöglichen Ablauf Verfolgungs Änderungen an den betroffenen Objekten, die für die Überprüfung ausgewählt wurden.  
  
Angenommen, die überprüfte Tabelle hat den Namen USER_TABLE. Für eine solche Tabelle werden die folgenden Hilfsobjekte in Oracle erstellt.  
  
||||  
|-|-|-|  
|Name|type|BESCHREIBUNG|  
|USER_TABLE $ trg|Trigger (trigger)|Löst die Überprüfung der Änderungen in der verifizierten Tabelle aus.|  
|USER_TABLE $ AUD|table|Tabelle, in der gelöschte und über schriebene Zeilen gespeichert werden.|  
|USER_TABLE $ audid|table|Tabelle, in der neue und geänderte Zeilen gespeichert werden.|  
|USER_TABLE|Ansicht|Vereinfachte Darstellung der Tabellen Änderungen.|  
|USER_TABLE $ New|Ansicht|Vereinfachte Darstellung von eingefügten und über schriebenen Zeilen.|  
|USER_TABLE $ NEW_ID|Ansicht|Identifizierung eingefügter und geänderter Zeilen.|  
|USER_TABLE $ Old|Ansicht|Vereinfachte Darstellung gelöschter und überschriebener Zeilen.|  
  
Das folgende Objekt wird im Schema der verifizierten Tabelle unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erstellt.  
  
||||  
|-|-|-|  
|Name|type|BESCHREIBUNG|  
|USER_TABLE $ trg|Trigger (trigger)|Löst die Überprüfung der Änderungen in der verifizierten Tabelle aus.|  
  
Und die folgenden Objekte werden unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in der ssmatesterdb-Datenbank erstellt.  
  
||||  
|-|-|-|  
|Name|type|BESCHREIBUNG|  
|USER_TABLE $ AUD|table|Tabelle, in der gelöschte und über schriebene Zeilen gespeichert werden.|  
|USER_TABLE $ audid|table|Tabelle, in der neue und geänderte Zeilen gespeichert werden.|  
|USER_TABLE|Ansicht|Vereinfachte Darstellung der Tabellen Änderungen.|  
|USER_TABLE $ New|Ansicht|Vereinfachte Darstellung von eingefügten und über schriebenen Zeilen.|  
|USER_TABLE $ new_id|Ansicht|Identifizierung eingefügter und geänderter Zeilen.|  
|USER_TABLE $ Old|Ansicht|Vereinfachte Darstellung gelöschter und überschriebener Zeilen.|  
  
### <a name="test-object-calls"></a>Testen von Objekt aufrufen  
Bei diesem Schritt ruft der SSMA-Tester alle für die Tests ausgewählten Objekte auf, vergleicht die Ergebnisse und zeigt den Bericht an.  
  
### <a name="finalization"></a>Abschluss  
Während der Fertigstellung bereinigt SSMA Tester die Hilfsobjekte, die beim **Initialisierungs** Schritt erstellt wurden.  
  
## <a name="next-step"></a>Nächster Schritt  
[Anzeigen von Test Fall berichten &#40;oracleto SQL&#41;](../../ssma/oracle/viewing-test-case-reports-oracletosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Auswählen und Konfigurieren von zu testenden Objekten &#40;oracleto SQL&#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
[Auswählen und konfigurieren betroffener Objekte &#40;oracleto SQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
[Testen von migrierten Datenbankobjekten &#40;oracleto SQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
