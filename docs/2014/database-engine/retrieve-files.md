---
title: Dateien abrufen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], file retrieval
- file retrieval [SQL Server]
- retrieving files
ms.assetid: 37b74426-e262-43b2-a81f-79b1fd1a36ec
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 548fac7dbc7d1f2750a130da9847be406361d8bf
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62843656"
---
# <a name="retrieve-files"></a>Abrufen von Dateien
  Wenn Sie ein quellcodeverwaltetes Projekt geöffnet haben, können Sie mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] lokale Kopien von Projektdateien aus dem Speicher der Quellcodeverwaltung in das lokale Verzeichnis abrufen, in dem sich das Projekt befindet.  
  
 Mit der integrierten Quellcodeverwaltung können Sie Dateien wie folgt abrufen:  
  
-   Befehl " **neueste Version (rekursiv)" erhalten**  
  
     Ruft die jeweils aktuelle eingecheckte Version der ausgewählten Dateien ab. Wenn eine Projektmappe oder ein Projekt ausgewählt ist, wird mit diesem Befehl die jeweils letzte Version aller Projektmappen und Projektdateien abgerufen.  
  
-   Befehl " **Get** "  
  
     Zeigt das **Dialogfeld** abrufen an, mit dem Sie die neueste Version einer ausgewählten Datei abrufen oder eine Teilmenge der Dateien in der ausgewählten Projekt Mappe oder im Projekt abrufen können.  
  
### <a name="to-retrieve-the-latest-version-of-all-the-files-in-a-project"></a>So rufen Sie die letzte Version aller Dateien in einem Projekt ab  
  
1.  Wählen Sie im Projektmappen-Explorer das Projekt aus.  
  
2.  Zeigen Sie im Menü **Datei** auf **Quell**Code Verwaltung, und klicken Sie dann auf **aktuellste Version erhalten (rekursiv)**.  
  
 Die jeweils aktuellen Versionen der Dateien im Projekt werden in den Projektspeicherort auf dem lokalen Datenträger abgerufen.  
  
#### <a name="to-retrieve-only-certain-files-in-a-project"></a>So rufen Sie nur bestimmte Dateien in einem Projekt ab  
  
1.  Wählen Sie im Projektmappen-Explorer das Element aus, das Sie abrufen möchten.  
  
2.  Zeigen Sie im Menü **Datei** auf **Quell**Code Verwaltung, und klicken Sie dann auf **Get**.  
  
3.  Klicken Sie im Dialogfeld **Get** auf **OK**. Wenn Sie eine Projektmappe oder ein Projekt im Projektmappen-Explorer ausgewählt haben, können Sie auch die Kontrollkästchen neben den Elementen deaktivieren, die Sie nicht abrufen möchten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dialog Feld "Get" &#40;&#41;der Quell Code Verwaltung](../../2014/database-engine/get-dialog-box-source-control.md)   
 [Festlegen und Abrufen von Versionsinformationen](../../2014/database-engine/set-and-retrieve-version-information.md)   
 [Anzeigen des Projektverlaufs](../../2014/database-engine/view-project-history.md)   
 [Anzeigen des Dateistatus](../../2014/database-engine/view-file-status.md)  
  
  
