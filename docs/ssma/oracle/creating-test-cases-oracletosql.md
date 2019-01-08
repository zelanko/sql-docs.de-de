---
title: Erstellen von Testfällen (OracleToSQL) | Microsoft-Dokumentation
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
manager: v-thobro
ms.openlocfilehash: a2c1bd3fea167a784d86f7e323566f73c3a01f86
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52512946"
---
# <a name="creating-test-cases-oracletosql"></a>Erstellen von Testfällen (OracleToSQL)
Verwenden Sie den Testfall-Assistenten, um einen Test zu erstellen. Mit diesem Assistenten können Sie die Testfälle erstellen, durch Auswählen von Objekten überprüft und getestet und die Test-Parameter angeben.  
  
## <a name="starting-the-test-case-wizard"></a>Starten des Assistenten für Testfall  
Zum Starten der Testfall-Assistenten auf **Neuer Testfall...**  aus der **Tester** Menü.  
  
Beim Starten, sucht der Assistent Schema SSMATESTER_ORACLE auf dem Quellserver für Oracle. Es ist die Tester Erweiterungsschema zum Speichern von zusätzlichen Objekte verwendet. Wenn der Assistent Testfall SSMATESTER_ORACLE finden kann, wird ein Dialogfeld, das das Schema erstellen möchte. (Diesem Fall geschieht in der Regel während der ersten Ausführung der SSMA-Tester.)  
  
Wenn das Dialogfeld angezeigt wird, klicken Sie auf **Ja** SSMATESTER_ORACLE Schema auf dem Quellserver zu erstellen. Beachten Sie, dass Sie Oracle-Berechtigungen zum Erstellen eines neuen Benutzers ein, und erstellen Objekte im Schema dieses Benutzers.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Übersicht über das Erstellen von Testfällen, die mithilfe des Assistenten  
Das Verfahren zum Erstellen eines Testfalls besteht aus fünf Schritten:  
  
1.  [Initialisieren von Testfällen &#40;OracleToSQL&#41;](../../ssma/oracle/initializing-test-cases-oracletosql.md)  
  
2.  [Auswählen und Konfigurieren von Objekten mit Test &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-objects-to-test-oracletosql.md)  
  
3.  [Auswählen und Konfigurieren von betroffenen Objekten &#40;OracleToSQL&#41;](../../ssma/oracle/selecting-and-configuring-affected-objects-oracletosql.md)  
  
4.  [Customizing Calls Order anpassen &#40;OracleToSQL&#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
5.  [Finishing Test Case Preparation beenden &#40;OracleToSQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Testen von migrierten Datenbankobjekten &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
