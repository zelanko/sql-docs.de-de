---
title: Eingecheckte Dateien bearbeiten | Microsoft-Dokumentation
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
ms.openlocfilehash: e2dbe1aad203dfdc83e438d5b7f4ed19c15038c1
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933111"
---
# <a name="edit-checked-in-files"></a>Bearbeiten eingecheckter Dateien
  In der Regel müssen Sie quellcodeverwaltete Dateien zunächst auschecken, bevor Sie sie bearbeiten können. Sie können jedoch so konfigurieren [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , dass Sie Dateien ändern können, die Sie nicht ausgecheckt haben. Wenn Sie dies tun, werden die Änderungen im Arbeitsspeicher gespeichert, bis Sie die Dateien speichern. Sie werden dann aufgefordert, die Datei aus der Quellcodeverwaltung auszuchecken.  
  
 Beim teambasierten Arbeiten ist es nicht empfehlenswert, eingecheckte Dateien zur Bearbeitung freizugeben, es sei denn, der Quellcodeverwaltungsanbieter unterstützt das Auschecken von lokalen Versionen und von Serverversionen. Die meisten Anbieter unterstützen kein Auschecken lokaler Versionen. Wenn Ihr Anbieter kein Auschecken lokaler Versionen unterstützt und Sie eine eingecheckte Datei bearbeiten, müssen Sie die Versionen im Arbeitsspeicher und auf dem Server manuell zusammenführen, bevor die Datei eingecheckt werden kann. In diesem Fall werden automatische und vom Anbieter unterstützte Zusammenführungen nicht unterstützt.  
  
### <a name="to-edit-checked-in-files"></a>So bearbeiten Sie eingecheckte Dateien  
  
1.  Klicken Sie im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie im Dialogfeld **Optionen** den Ordner **Quell**Ordner, und klicken Sie dann auf **Umgebung**.  
  
3.  Klicken Sie auf **zu bearbeitende eingegebene Elemente zulassen**, und klicken Sie dann auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Check-Ins verwalten](../../2014/database-engine/manage-checkins.md)   
 [Verwalten von Auscheckvorgängen](../../2014/database-engine/manage-checkouts.md)  
  
  
