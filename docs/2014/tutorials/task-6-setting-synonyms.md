---
title: 'Aufgabe 6: Festlegen von Synonymen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b7d35ee9-d1c9-41d9-bbc5-0ca7db93e54d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 4499a0a099c92a9b1802cc905da3d0a473808eeb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78177228"
---
# <a name="task-6-setting-synonyms"></a>Aufgabe 6: Festlegen von Synonymen
  In dieser Aufgabe legen Sie zwei Domänen Werte ( **USA** und **USA**) der Domäne **Country** als Synonyme fest, wobei **USA** als führender Wert festgelegt ist. Da die Option **führende Werte verwenden** beim Erstellen der Domäne **Country** ausgewählt wurde, werden alle **US** -Werte für die Domäne **Country** als **USA** ausgegeben (da USA der führende Wert ist). Weitere Informationen finden Sie unter [Ändern von Domänen Werten](https://msdn.microsoft.com/library/hh510408.aspx) .

1.  Wählen Sie **Land** aus der Liste der Domänen aus.

2.  Wechseln Sie zur Registerkarte **Domänen Werte** .

3.  Klicken Sie auf der Symbolleiste auf **neue Domänen Wert hinzufügen** .

4.  Geben Sie **USA** als Wert ein, und drücken **Sie die Eingabe**Taste.

5.  Wählen Sie **USA** und **USA** mit STRG oder Umschalttaste aus, klicken Sie mit der rechten Maustaste auf die ausgewählten Elemente, und klicken Sie dann auf **als Synonyme festlegen**. DQS gruppiert diese Werte und legt einen der Werte als führenden Wert fest, durch den die anderen Werte ersetzt werden.

     ![Als Synonyme festlegen (Menü)](../../2014/tutorials/media/et-settingsynonyms-01.jpg "Als Synonyme festlegen (Menü)")

6.  Beachten Sie, dass **USA** als führender Wert festgelegt ist. Wenn Sie möchten, dass "USA" der führende Wert ist, können Sie mit der rechten Maustaste auf "USA" klicken und **als führende Option festlegen** auswählen. In diesem Tutorial verwenden wir **USA** als führenden Wert.

     ![Vereinigte Staaten und USA als Synonyme](../../2014/tutorials/media/et-settingsynonyms-02.jpg "Vereinigte Staaten und USA als Synonyme")

## <a name="next-step"></a>Nächster Schritt
 [Aufgabe 7: Erstellen einer Verbunddomäne](../../2014/tutorials/task-7-creating-a-composite-domain.md)


