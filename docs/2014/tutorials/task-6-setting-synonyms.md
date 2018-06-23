---
title: 'Aufgabe 6: Festlegen von Synonymen | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7d35ee9-d1c9-41d9-bbc5-0ca7db93e54d
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3019c7cf3466fae5579548e3aa8fa9c028145f98
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049079"
---
# <a name="task-6-setting-synonyms"></a>Aufgabe 6: Festlegen von Synonymen
  In dieser Aufgabe legen Sie zwei Domänenwerte **USA** und **United States**, der die **Land** Domäne als Synonyme mit **United States** wie die führender Wert. Da der **führende Werte** ausgewählt wurde beim Erstellen der **Land** Domäne alle **USA** Werte für die **Land** Domäne wird als Ausgabe werden **United States** (wie United States der führende Wert ist). Finden Sie unter [Change Domain Values](http://msdn.microsoft.com/library/hh510408.aspx) Weitere Details.  
  
1.  Wählen Sie **Land** aus der Liste der Domänen.  
  
2.  Wechseln Sie zu der **Domänenwerte** Registerkarte.  
  
3.  Klicken Sie auf **neuen Domänenwert hinzufügen** auf der Symbolleiste.  
  
4.  Typ **USA** für den Wert, und drücken Sie **EINGABETASTE**.  
  
5.  Kann die Mehrfachauswahl **United States** und **USA** STRG-Taste oder UMSCHALTTASTE rechten Maustaste auf die ausgewählten Elemente, und klicken Sie dann auf **als Synonyme festlegen**. DQS gruppiert diese Werte und legt einen der Werte als führenden Wert fest, durch den die anderen Werte ersetzt werden.  
  
     ![Legen Sie als Synonyme Menü](../../2014/tutorials/media/et-settingsynonyms-01.jpg "als Synonyme Menü festlegen")  
  
6.  Beachten Sie, dass **United States** als führender Wert festgelegt ist. Wenn Sie USA der führende Wert sein soll, können Sie mit der rechten Maustaste auf die USA und auswählen **als führend festlegen** Option. Für dieses Lernprogramm verwenden wir **United States** als führenden Wert fest.  
  
     ![Vereinigte Staaten und USA als Synonyme](../../2014/tutorials/media/et-settingsynonyms-02.jpg "Vereinigte Staaten und USA als Synonyme")  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 7: Erstellen einer Verbunddomänenregel](../../2014/tutorials/task-7-creating-a-composite-domain.md)  
  
  