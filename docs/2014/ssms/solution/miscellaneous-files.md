---
title: Sonstige Dateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio], miscellaneous
- projects [SQL Server Management Studio], files
- solutions [SQL Server Management Studio], files
- miscellaneous files folder [SQL Server]
ms.assetid: 3c952b0b-8f5f-4d86-9e5d-616c10b9df0d
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d0bffcec84abd3d743141342c2b8dde65df48ceb
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43813616"
---
# <a name="miscellaneous-files"></a>sonstige Dateien
  Dateien, die als extern zu allen Projekte betrachtet werden, werden als *sonstige Dateien*bezeichnet. Wenn eine Projektmappe geöffnet ist, können Sie sonstige Dateien, die zum Projekt gehören, öffnen und ändern. Dateien werden als sonstige Dateien eingestuft, wenn die Dateierweiterung nicht dem Code-Editor des Projekts zugeordnet ist. So werden beispielsweise in einem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Skriptprojekt Dateien mit der Dateinamenerweiterung TXT oder MDX als sonstige Dateien behandelt. In einem MDX-Projekt werden Dateien mit der Dateinamenerweiterung TXT oder SQL als sonstige Dateien behandelt. Um eine Dateierweiterung mit einem Code-Editor zu verknüpfen, finden Sie unter [Zuordnen von Dateierweiterungen zu einem Code-Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).  
  
 Das Hinzufügen von sonstigen Dateien zu Ihren Projekten bietet sich aus mehreren Gründen an. Möglicherweise gibt es eine Datei, die nicht unbedingt ein erkanntes Skript ist, aber wesentlich zur Entwicklung der Projektmappe beiträgt. Typische Beispiele dafür sind Entwicklungshinweise oder -anweisungen, Datendateien und Code Clips.  
  
 Durch die sonstigen Dateien erhalten Sie mehr Flexibilität. Angenommen, Sie haben ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Skriptprojekt mit mehreren Skripts zum Erstellen von Tabellen und gespeicherten Prozeduren in Ihrer Datenbank. Außerdem gibt es für die Tabellen mehrere Datendateien mit der Dateinamenerweiterung BCP und eine Infodatei Readme.txt mit Anweisungen zur Ausführung. Sie können die Daten- und die Infodateien als sonstige Dateien zum Projekt hinzufügen, um die Vorteile der Quellcodeverwaltung und der anderen Funktionen des Projektsystems zu nutzen.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Menüs und Symbolleisten hängen vom Format der Datei ab, die Sie öffnen. Wenn Sie beispielsweise eine Textdatei öffnen, wird die Symbolleiste des Text-Editors angezeigt. Wenn Sie eine XML-Schemadatei öffnen, wird die Symbolleiste des XML-Schemas angezeigt. Beim Bearbeiten des XML-Schemas ist die Symbolleiste des Text-Editors nicht verfügbar. Wenn Sie zwischen einer Projektdatei und einer der sonstigen Dateien wechseln, werden alle projektbezogenen Befehle und Symbolleisten durch solche ersetzt, die für die sonstigen Dateien gelten.  
  
## <a name="see-also"></a>Siehe auch  
 [Dateien, die Projektmappen und Projekte verwalten](files-that-manage-solutions-and-projects.md)   
 [Lösungen &#40;SQL Server Management Studio&#41;](solutions-sql-server-management-studio.md)   
 [Projekte &#40;SQL Server Management Studio&#41;](projects-sql-server-management-studio.md)  
  
  
