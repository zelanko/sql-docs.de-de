---
title: Reparieren einer Distributed Replay-Installation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fcd8ca8-1ceb-457d-9545-096c74e274d7
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8adf917831b33c1603b3c0c4a1e7b678900cf7dd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147617"
---
# <a name="repair-a-distributed-replay-installation"></a>Reparieren einer Distributed Replay-Installation
  Zur Reparatur einer Distributed Replay-Komponente (Controller oder Client) gehen Sie wie folgt vor:  
  
1.  Installieren Sie alle zugehörigen Dateien erneut auf dem Datenträger, und ersetzen Sie dabei alle vorhandenen Dateien.  
  
2.  Wenn das entsprechende Windows-Dienstkonto entfernt wurde, erstellen Sie dieses erneut.  
  
 Über den Reparaturvorgang können Sie Komponenten nicht hinzuzufügen oder entfernen. Klicken Sie zum Hinzufügen oder Entfernen von Komponenten, überprüfen Sie, oder deaktivieren Sie die entsprechende Komponente in der Funktionsstruktur auf der **Funktionsauswahl** auf der Seite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.  
  
### <a name="to-repair-a-failed-installation-of-distributed-replay"></a>So reparieren Sie eine fehlerhafte Distributed Replay-Installation  
  
1.  Aus der **starten** Menü klicken Sie auf **Systemsteuerung**, und doppelklicken Sie dann auf **Software**.  
  
2.  Wählen Sie [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in der **deinstallieren oder Ändern eines Programms** Fenster, und klicken Sie dann in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (Dialogfeld), klicken Sie auf **Reparatur**.  
  
3.  Führen Sie die Schritte in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Assistenten, und klicken Sie auf die **Features auswählen** Seite, wählen Sie die Distributed Replay-Komponenten zu reparieren, und klicken Sie dann auf **weiter.**.  
  
4.  Schließen Sie den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Installations-Assistenten ab, um die ausgewählten Distributed Replay-Funktionen zu reparieren.  
  
  