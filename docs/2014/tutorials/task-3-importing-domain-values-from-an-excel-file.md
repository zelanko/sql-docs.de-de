---
title: 'Aufgabe 3: Importieren von Domänenwerten aus einer Exceldatei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: 242e8309-1195-495b-9cd5-aa127748c185
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 56aa693625ecf78ddd5084b88e6fd6c3e2e0f5b5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48215100"
---
# <a name="task-3-importing-domain-values-from-an-excel-file"></a>Aufgabe 3: Importieren von Domänenwerten aus einer Excel-Datei
  In dieser Aufgabe importieren Sie Werte für die Domäne **State** aus einem Arbeitsblatt einer Excel-Datei.  
  
1.  Klicken Sie in der **Domänenliste** auf die Domäne **State**.  
  
2.  Stellen Sie sicher, dass die Registerkarte **Domänenwerte** im rechten Bereich aktiv ist.  
  
3.  Klicken Sie im rechten Bereich auf der Symbolleiste auf den **Nach-unten-Pfeil** neben der Schaltfläche **Werte importieren** , und klicken Sie auf **Gültige Werte aus Excel importieren**.  
  
     ![Gültige Werte im Menü von Excel importieren](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-01.jpg "gültige Werte werden im Menü von Excel importieren.")  
  
4.  Klicken Sie auf **Durchsuchen**, wählen Sie **Suppliers.xls**aus, und klicken Sie auf **Öffnen**.  
  
5.  Wählen Sie **StatesToImport$** als **Arbeitsblatt**aus.  
  
     ![Dialogfeld "Domänenwerte" Import](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-02.jpg "im Dialogfeld \"Domänenwerte\" Importieren")  
  
6.  Klicken Sie auf **OK** , um das Dialogfeld **Domänenwerte importieren** zu schließen. Die Namen aller importierten Bundesstaaten sollten in der Liste angezeigt werden. Die Option **Nur neue anzeigen** wird nach dem Import automatisch aktiviert. Wenn Sie Werte importieren und die alten Werte nicht in der Liste angezeigt werden, liegt dies daran, dass diese Option nach dem Import automatisch aktiviert ist. Um alle Werte anzuzeigen, deaktivieren Sie das Kontrollkästchen. Wenn Sie den gleichen Satz Werte erneut importieren, wird keiner der Werte importiert, da sie bereits in der Domäne vorhanden sind.  
  
     ![Zeigen Sie nur neues Kontrollkästchen auf Domänenwerte](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-03.jpg "nur neues Kontrollkästchen auf Domänenwerte anzeigen")  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 4: Festlegen von Domänenregeln](../../2014/tutorials/task-4-setting-domain-rules.md)  
  
  
