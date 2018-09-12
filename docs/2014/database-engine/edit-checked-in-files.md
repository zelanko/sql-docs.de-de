---
title: Bearbeiten von eingecheckten Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying checked-in files
- checking in files
ms.assetid: 560cd19f-ab22-4273-b00c-149993a630e6
caps.latest.revision: 24
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 065f8d2d32d8ad16fe955ba8e36c7e65926bec95
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43808286"
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
  
  
