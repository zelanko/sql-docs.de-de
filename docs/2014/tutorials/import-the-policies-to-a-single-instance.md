---
title: Importieren der Richtlinien auf eine Einzelinstanz | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc5bcd87-663f-41d9-bb7b-b3e083cd63df
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 945cd03bb574bc180af5567888a6d171966bccf6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149761"
---
# <a name="import-the-policies-to-a-single-instance"></a>Importieren der Richtlinien auf eine einzelne Instanz
  In diesem Task importieren Sie die Best Practices-Richtlinien, die Sie in der richtlinienbasierten Verwaltung zeitgesteuert ausführen möchten, auf eine einzelne Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Sie müssen diese Prozedur auf einem Server ausführen, auf dem [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] oder eine höhere Version ausgeführt wird.  
  
### <a name="import-the-best-practices-policies-for-the-database-engine"></a>Importieren der Best Practices-Richtlinien für die Datenbank-Engine  
  
1.  Starten Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], und stellen Sie dann eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)] her.  
  
2.  Erweitern Sie im Objekt-Explorer **Verwaltung**, und erweitern Sie dann **Richtlinienverwaltung**.  
  
3.  Mit der rechten Maustaste **Richtlinien**, und klicken Sie dann auf **Importrichtlinie**.  
  
4.  In der **importieren** Dialogfeld neben der **zu importierende Dateien** klicken Sie auf die Auslassungspunkte (**...** ) Schaltfläche.  
  
5.  Wechseln Sie in der Liste **Suchen in** zum folgenden Ordner, in dem die Best Practices-Richtlinien enthalten sind:  
  
     **C:\Programme\Microsoft Dateien (x86) \Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**  
  
    > [!NOTE]  
    >  Abhängig davon, wo die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Programmdateien installiert sind, ob ein 32-Bit- oder 64-Bit-Betriebssystem ausgeführt bzw. ein Sprachbezeichner verwendet wird, kann sich der Dateipfad ändern.  
  
6.  Wählen Sie im Dialogfeld **Richtlinie auswählen** mindestens eine Richtliniendatei aus.  
  
     Um nicht aufeinander folgende Dateien auszuwählen, klicken Sie auf eine Datei, halten die STRG-Taste gedrückt und klicken dann jeweils auf die nächste Datei. Um aufeinander folgende Dateien auszuwählen, klicken Sie auf die erste Datei in der Abfolge, halten Sie die UMSCHALTTASTE gedrückt und klicken dann auf die letzte Datei.  
  
7.  Nachdem Sie alle Dateien ausgewählt haben, klicken Sie auf **Öffnen**.  
  
8.  In der **importieren** Dialogfeld Feld, stellen Sie sicher, dass die **Richtlinienstatus** Liste wird festgelegt, um **Richtlinienstatus beim Import** (Standard), und klicken Sie dann auf **OK**.  
  
     Die Richtlinien werden dann unter der **Richtlinienverwaltung** in den Knoten **Richtlinien**importiert. Standardmäßig wird für die importierten Richtlinien der Auswertungsmodus "Bedarfsgesteuert" festgelegt.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Planen der Richtlinien](../../2014/tutorials/schedule-the-policies.md)  
  
  