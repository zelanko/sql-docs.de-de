---
title: Bearbeiten von eingecheckten Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying checked-in files
- checking in files
ms.assetid: 560cd19f-ab22-4273-b00c-149993a630e6
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 97d6ab997a1ece36919a49243e0f1dc3cc6f3593
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48202410"
---
# <a name="edit-checked-in-files"></a>Bearbeiten eingecheckter Dateien
  In der Regel müssen Sie quellcodeverwaltete Dateien zunächst auschecken, bevor Sie sie bearbeiten können. Sie können jedoch [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] so konfigurieren, dass Sie Dateien ändern können ,die Sie nicht ausgecheckt haben. Dabei bleiben die Änderungen im Arbeitsspeicher, bis Sie die Dateien speichern. Sie werden dann aufgefordert, die Datei aus der Quellcodeverwaltung auszuchecken.  
  
 Beim teambasierten Arbeiten ist es nicht empfehlenswert, eingecheckte Dateien zur Bearbeitung freizugeben, es sei denn, der Quellcodeverwaltungsanbieter unterstützt das Auschecken von lokalen Versionen und von Serverversionen. Die meisten Anbieter unterstützen kein Auschecken lokaler Versionen. Wenn Ihr Anbieter kein Auschecken lokaler Versionen unterstützt und Sie eine eingecheckte Datei bearbeiten, müssen Sie die Versionen im Arbeitsspeicher und auf dem Server manuell zusammenführen, bevor die Datei eingecheckt werden kann. In diesem Fall werden automatische und vom Anbieter unterstützte Zusammenführungen nicht unterstützt.  
  
### <a name="to-edit-checked-in-files"></a>So bearbeiten Sie eingecheckte Dateien  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  In der **Optionen** Dialogfeld erweitern Sie die **Quellcodeverwaltung**l-Ordner, und klicken Sie dann auf **Umgebung**.  
  
3.  Klicken Sie auf **eingecheckter Elemente bearbeitet werden können**, und klicken Sie dann auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Eincheckvorgängen](../../2014/database-engine/manage-checkins.md)   
 [Verwalten von Auscheckvorgängen](../../2014/database-engine/manage-checkouts.md)  
  
  
