---
title: Erstellen von Test Fällen (oracleto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Test Case Wizard
ms.assetid: 22f38901-ec35-4707-a911-784e6ad8dafb
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 697f7049a60aa7ae2b8c89d1fb6c5ce8e3d29312
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68266134"
---
# <a name="creating-test-cases-oracletosql"></a>Erstellen von Testfällen (OracleToSQL)
Verwenden Sie den Testfall-Assistenten, um einen Test zu erstellen. Mit diesem Assistenten können Sie Testfälle erstellen, indem Sie getestete und überprüfte Objekte auswählen und die Testparameter angeben.  
  
## <a name="starting-the-test-case-wizard"></a>Der Testfall-Assistent wird gestartet.  
Um den Testfall-Assistenten zu starten, klicken Sie im Menü **Tester** auf **neuer Testfall...** .  
  
Beim Start sucht der Assistent nach Schema SSMATESTER_ORACLE auf dem Oracle-Quell Server. Es ist das Test Erweiterungs Schema, das zum Speichern von Hilfsobjekten verwendet wird. Wenn der Testfall-Assistent SSMATESTER_ORACLE nicht finden kann, wird ein Dialogfeld angezeigt, in dem die Erstellung des Schemas vorgeschlagen wird. (Diese Situation tritt in der Regel während der ersten Ausführen von SSMA Tester auf.)  
  
Wenn Sie das Dialogfeld Fenster erhalten, klicken Sie auf **Ja** , um SSMATESTER_ORACLE Schema auf dem Quell Server zu erstellen. Beachten Sie, dass Sie über Oracle-Berechtigungen zum Erstellen eines neuen Benutzers und zum Erstellen von Objekten im Schema dieses Benutzers verfügen müssen.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Übersicht über das Erstellen von Test Fällen mithilfe des Assistenten  
Der Vorgang zum Erstellen eines Testfalls besteht aus fünf Schritten:  
  
1.  [Initialisieren von Test Fällen &#40;oracleto SQL&#41;](../../ssma/oracle/initializing-test-cases-oracletosql.md)  
  
2.  [Auswählen und Konfigurieren von zu testenden Objekten &#40;oracleto SQL&#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
  
3.  [Auswählen und konfigurieren betroffener Objekte &#40;oracleto SQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
4.  [Anpassen von Aufruf Reihenfolge &#40;oracleto SQL&#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
5.  [Fertigstellung der Test Fall Vorbereitung &#40;oracleto SQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Testen von migrierten Datenbankobjekten &#40;oracleto SQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
