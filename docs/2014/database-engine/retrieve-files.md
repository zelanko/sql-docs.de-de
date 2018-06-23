---
title: Abrufen von Dateien | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- version control services [SQL Server], file retrieval
- file retrieval [SQL Server]
- retrieving files
ms.assetid: 37b74426-e262-43b2-a81f-79b1fd1a36ec
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f1b53eb99abc77e809bd7aaac30f8f218cd4ee03
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049265"
---
# <a name="retrieve-files"></a>Abrufen von Dateien
  Wenn Sie ein quellcodeverwaltetes Projekt geöffnet haben, können Sie mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] lokale Kopien von Projektdateien aus dem Speicher der Quellcodeverwaltung in das lokale Verzeichnis abrufen, in dem sich das Projekt befindet.  
  
 Mit der integrierten Quellcodeverwaltung können Sie Dateien wie folgt abrufen:  
  
-   **Letzte Version abrufen (rekursiv)** Befehl  
  
     Ruft die jeweils aktuelle eingecheckte Version der ausgewählten Dateien ab. Wenn eine Projektmappe oder ein Projekt ausgewählt ist, wird mit diesem Befehl die jeweils letzte Version aller Projektmappen und Projektdateien abgerufen.  
  
-   **Abrufen** Befehl  
  
     Zeigt die **abrufen** (Dialogfeld), die Sie verwenden können, um die neueste Version einer ausgewählten Datei abzurufen oder beim Abrufen von einer Teilmenge Ihrer Dateien in der ausgewählten Projektmappe bzw. das Projekt.  
  
### <a name="to-retrieve-the-latest-version-of-all-the-files-in-a-project"></a>So rufen Sie die letzte Version aller Dateien in einem Projekt ab  
  
1.  Wählen Sie im Projektmappen-Explorer das Projekt aus.  
  
2.  Auf der **Datei** Sie im Menü **Quellcodeverwaltung**, und klicken Sie dann auf **neuste Version abrufen (rekursiv)**.  
  
 Die jeweils aktuellen Versionen der Dateien im Projekt werden in den Projektspeicherort auf dem lokalen Datenträger abgerufen.  
  
#### <a name="to-retrieve-only-certain-files-in-a-project"></a>So rufen Sie nur bestimmte Dateien in einem Projekt ab  
  
1.  Wählen Sie im Projektmappen-Explorer das Element aus, das Sie abrufen möchten.  
  
2.  Auf der **Datei** Sie im Menü **Quellcodeverwaltung**, und klicken Sie dann auf **abrufen**.  
  
3.  In der **abrufen** (Dialogfeld), klicken Sie auf **OK**. Wenn Sie eine Projektmappe oder ein Projekt im Projektmappen-Explorer ausgewählt haben, können Sie auch die Kontrollkästchen neben den Elementen deaktivieren, die Sie nicht abrufen möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Abrufen (Dialogfeld) &#40;Quellcodeverwaltung&#41;](../../2014/database-engine/get-dialog-box-source-control.md)   
 [Festlegen und Abrufen von Versionsinformationen](../../2014/database-engine/set-and-retrieve-version-information.md)   
 [Anzeigen der Projektversionsgeschichte](../../2014/database-engine/view-project-history.md)   
 [Anzeigen des Dateistatus](../../2014/database-engine/view-file-status.md)  
  
  