---
title: Erstellen von Testfällen (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Tester component,Test Case Wizard
ms.assetid: b52dfd93-95af-4299-bc8f-83f2a7a6a518
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 95a6724ab836fb3dddb54fadc82821ad68f29e98
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47746358"
---
# <a name="creating-test-cases-sybasetosql"></a>Erstellen von Testfällen (SybaseToSQL)
Verwenden Sie den Testfall-Assistenten, um einen Test zu erstellen. Mit diesem Assistenten können Sie die Testfälle erstellen, durch Auswählen von Objekten überprüft und getestet und die Test-Parameter angeben.  
  
## <a name="starting-the-test-case-wizard"></a>Starten des Assistenten für Testfall  
Zum Starten der Testfall-Assistenten auf **Neuer Testfall...** von der **Tester** Menü.  
  
Beim Starten, sucht der Assistent Datenbank ssmatester2005db oder ssmatester2008db (je nach Projekttyp) auf dem Quellserver für die Sybase. Es ist die Tester Erweiterungsschema zum Speichern von zusätzlichen Objekte verwendet. Wenn der Assistent Testfall ssmatester2005db oder ssmatester2008db finden kann, wird ein Dialogfeld an, die zum Erstellen der Tester Erweiterung-Datenbank vorgeschlagen angezeigt. (Diesem Fall geschieht in der Regel während der ersten Ausführung der SSMA-Tester.)  
  
Wenn das Dialogfeld angezeigt wird, klicken Sie auf **Ja** Tester Sybase-Datenbank auf dem Quellserver zu erstellen. Anschließend wird ein neues Dialogfeld angezeigt, Sie sollten ein oder mehrere Geräte auf dem neuen Tester-Datenbank hinzufügen. Klicken Sie auf **hinzufügen** zum Hinzufügen eines Geräts. In der **Zuordnung von Speicherplatz für Tester Datenbank** Dialogfeld Wählen Sie das Gerät, und geben Sie die Größe von Tester-Datenbank verwendet werden. Darüber hinaus können Sie das separate Gerät für Datenbankprotokolle festlegen. Beachten Sie, dass Sie Sybase-Berechtigungen zum Erstellen von Datenbanken.  
  
## <a name="overview-of-creating-test-cases-using-the-wizard"></a>Übersicht über das Erstellen von Testfällen, die mithilfe des Assistenten  
Das Verfahren zum Erstellen eines Testfalls besteht aus fünf Schritten:  
  
1.  [Initialisieren von Testfällen &#40;SybaseToSQL&#41;](../../ssma/sybase/initializing-test-cases-sybasetosql.md).  
  
2.  [Auswählen und Konfigurieren von Objekten mit Test &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md).  
  
3.  [Auswählen und Konfigurieren von betroffenen Objekten &#40;SybaseToSQL&#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md).  
  
4.  [Customizing Calls Order anpassen &#40;SybaseToSQL&#41;](../../ssma/sybase/customizing-calls-order-sybasetosql.md).  
  
5.  [Finishing Test Case Preparation beenden &#40;SybaseToSQL&#41;](../../ssma/sybase/finishing-test-case-preparation-sybasetosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Testen von migrierten Datenbankobjekten &#40;SybaseToSQL&#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
