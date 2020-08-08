---
title: Erstellen von Test Fällen (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester component,Test Case Wizard
ms.assetid: b52dfd93-95af-4299-bc8f-83f2a7a6a518
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 146e6975dd8880f750e7bb449e8d42ca3e6a4e62
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87931914"
---
# <a name="creating-test-cases-sybasetosql"></a>Erstellen von Testfällen (SybaseToSQL)
Verwenden Sie den Testfall-Assistenten, um einen Test zu erstellen. Mit diesem Assistenten können Sie Testfälle erstellen, indem Sie getestete und überprüfte Objekte auswählen und die Testparameter angeben.  
  
## <a name="starting-the-test-case-wizard"></a>Der Testfall-Assistent wird gestartet.  
Um den Testfall-Assistenten zu starten, klicken Sie im Menü **Tester** auf **neuer Testfall...** .  
  
Beim Start sucht der Assistent nach der Datenbank ssmatester2005db oder ssmatester2008db (abhängig vom Projekttyp) auf dem Sybase-Quell Server. Es ist das Test Erweiterungs Schema, das zum Speichern von Hilfsobjekten verwendet wird. Wenn der Testfall-Assistent ssmatester2005db oder ssmatester2008db nicht finden kann, wird ein Dialogfeld angezeigt, in dem die Erstellung der Tester-Erweiterungs Datenbank vorgeschlagen wird. (Diese Situation tritt in der Regel während der ersten Ausführen von SSMA Tester auf.)  
  
Wenn das Dialogfeld angezeigt wird, klicken Sie auf **Ja** , um die Sybase-Tester-Datenbank auf dem Quell Server zu erstellen. Daraufhin wird ein neues Dialogfeld angezeigt, in dem Sie ein oder mehrere Geräte hinzufügen müssen, auf denen die neue Tester-Datenbank zu finden ist. Klicken Sie auf **Hinzufügen** , um ein Gerät hinzuzufügen. Wählen Sie im Dialogfeld **Speicherplatz für Tester Datenbank** das Gerät aus, und geben Sie die Größe der Tester-Datenbank an. Darüber hinaus können Sie das separate Gerät für Daten Bank Protokolle festlegen. Beachten Sie, dass Sie über Sybase-Berechtigungen zum Erstellen von Datenbanken verfügen müssen.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Übersicht über das Erstellen von Test Fällen mithilfe des Assistenten  
Der Vorgang zum Erstellen eines Testfalls besteht aus fünf Schritten:  
  
1.  [Initialisieren von Test Fällen &#40;Sybase-SQL-&#41;](../../ssma/sybase/initializing-test-cases-sybasetosql.md).  
  
2.  [Auswählen und Konfigurieren von zu testenden Objekten &#40;sybaseto SQL-&#41;](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md).  
  
3.  Die [Auswahl und Konfiguration der betroffenen Objekte &#40;Sybase&#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md).  
  
4.  Das [Anpassen von Aufruf Reihenfolge &#40;sybasedesql-&#41;](../../ssma/sybase/customizing-calls-order-sybasetosql.md).  
  
5.  [Fertigstellung der Test Fall Vorbereitung &#40;Sybase&#41;](../../ssma/sybase/finishing-test-case-preparation-sybasetosql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Testen von migrierten Datenbankobjekten &#40;sybaseto SQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
