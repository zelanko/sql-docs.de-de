---
title: Importieren der Richtlinien in eine einzelne Instanz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: bc5bcd87-663f-41d9-bb7b-b3e083cd63df
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 410f3a317a9d3ad2f8cab52d9f57fd4a63c1c36c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62865099"
---
# <a name="import-the-policies-to-a-single-instance"></a>Importieren der Richtlinien auf eine einzelne Instanz
  In diesem Task importieren Sie die Best Practices-Richtlinien, die Sie in der richtlinienbasierten Verwaltung zeitgesteuert ausführen möchten, auf eine einzelne Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Sie müssen diese Prozedur auf einem Server ausführen, auf dem [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] oder eine höhere Version ausgeführt wird.  
  
### <a name="import-the-best-practices-policies-for-the-database-engine"></a>Importieren der Best Practices-Richtlinien für die Datenbank-Engine  
  
1.  Starten Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], und stellen Sie dann eine Verbindung mit dem [!INCLUDE[ssDE](../includes/ssde-md.md)]her.  
  
2.  Erweitern Sie im Objekt-Explorer **Verwaltung**, und erweitern Sie dann **Richtlinienverwaltung**.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Richtlinien**und dann auf **Richtlinie importieren**.  
  
4.  Klicken Sie im Dialogfeld **importieren** neben dem Feld **zu importierende Dateien** auf die Schaltfläche mit den Auslassungs Punkten (**...**).  
  
5.  Wechseln Sie in der Liste **Suchen in** zum folgenden Ordner, in dem die Best Practices-Richtlinien enthalten sind:  
  
     **C:\Programme (x86)\Microsoft SQL Server\110\Tools\Policies\DatabaseEngine\1033**  
  
    > [!NOTE]  
    >  Abhängig davon, wo die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Programmdateien installiert sind, ob ein 32-Bit- oder 64-Bit-Betriebssystem ausgeführt bzw. ein Sprachbezeichner verwendet wird, kann sich der Dateipfad ändern.  
  
6.  Wählen Sie im Dialogfeld **Richtlinie auswählen** mindestens eine Richtliniendatei aus.  
  
     Um nicht aufeinander folgende Dateien auszuwählen, klicken Sie auf eine Datei, halten die STRG-Taste gedrückt und klicken dann jeweils auf die nächste Datei. Um aufeinander folgende Dateien auszuwählen, klicken Sie auf die erste Datei in der Abfolge, halten Sie die UMSCHALTTASTE gedrückt und klicken dann auf die letzte Datei.  
  
7.  Nachdem Sie alle Dateien ausgewählt haben, klicken Sie auf **Öffnen**.  
  
8.  Stellen Sie im Dialogfeld **importieren** sicher, dass die Liste **Richtlinien Status** für den **Richtlinien Status beim Import beibehalten** (Standardeinstellung) festgelegt ist, und klicken Sie dann auf **OK**.  
  
     Die Richtlinien werden dann unter der **Richtlinienverwaltung** in den Knoten **Richtlinien**importiert. Standardmäßig wird für die importierten Richtlinien der Auswertungsmodus "Bedarfsgesteuert" festgelegt.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Planen der Richtlinien](../../2014/tutorials/schedule-the-policies.md)  
  
  
