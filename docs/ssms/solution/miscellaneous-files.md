---
title: sonstige Dateien
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- files [SQL Server Management Studio], miscellaneous
- projects [SQL Server Management Studio], files
- solutions [SQL Server Management Studio], files
- miscellaneous files folder [SQL Server]
ms.assetid: 3c952b0b-8f5f-4d86-9e5d-616c10b9df0d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 79438b43ed00fb30b7f70c832ebf8830bf20f7bf
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75251887"
---
# <a name="miscellaneous-files"></a>sonstige Dateien
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Dateien, die als extern zu allen Projekte betrachtet werden, werden als *sonstige Dateien* bezeichnet. Wenn eine Projektmappe geöffnet ist, können Sie sonstige Dateien, die zum Projekt gehören, öffnen und ändern. Dateien werden als sonstige Dateien eingestuft, wenn die Dateierweiterung nicht dem Code-Editor des Projekts zugeordnet ist. So werden beispielsweise in einem [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Skriptprojekt Dateien mit der Dateierweiterung TXT oder MDX als sonstige Dateien behandelt. In einem MDX-Projekt werden Dateien mit der Dateinamenerweiterung TXT oder SQL als sonstige Dateien behandelt. Informationen zum Zuordnen einer Dateierweiterung zu einem Code-Editor finden Sie unter [Vorgehensweise: Zuordnen von Dateierweiterungen zu einem Code-Editor](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md).  
  
Das Hinzufügen von sonstigen Dateien zu Ihren Projekten bietet sich aus mehreren Gründen an. Möglicherweise gibt es eine Datei, die nicht unbedingt ein erkanntes Skript ist, aber wesentlich zur Entwicklung der Projektmappe beiträgt. Typische Beispiele dafür sind Entwicklungshinweise oder -anweisungen, Datendateien und Code Clips.  
  
Durch die sonstigen Dateien erhalten Sie mehr Flexibilität. Angenommen, Sie haben ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Skriptprojekt mit mehreren Skripts zum Erstellen von Tabellen und gespeicherten Prozeduren in Ihrer Datenbank. Außerdem gibt es für die Tabellen mehrere Datendateien mit der Dateinamenerweiterung BCP und eine Infodatei Readme.txt mit Anweisungen zur Ausführung. Sie können die Daten- und die Infodateien als sonstige Dateien zum Projekt hinzufügen, um die Vorteile der Quellcodeverwaltung und der anderen Funktionen des Projektsystems zu nutzen.  
  
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Menüs und Symbolleisten hängen vom Format der Datei ab, die Sie öffnen. Wenn Sie beispielsweise eine Textdatei öffnen, wird die Symbolleiste des Text-Editors angezeigt. Wenn Sie eine XML-Schemadatei öffnen, wird die Symbolleiste des XML-Schemas angezeigt. Beim Bearbeiten des XML-Schemas ist die Symbolleiste des Text-Editors nicht verfügbar. Wenn Sie zwischen einer Projektdatei und einer der sonstigen Dateien wechseln, werden alle projektbezogenen Befehle und Symbolleisten durch solche ersetzt, die für die sonstigen Dateien gelten.  
  
## <a name="see-also"></a>Weitere Informationen  
[Dateien zum Verwalten von Projektmappen und Projekten](../../ssms/solution/files-that-manage-solutions-and-projects.md)  
[Projektmappen &#40;SQL Server Management Studio&#41;](../../ssms/solution/solutions-sql-server-management-studio.md)  
[Projekte &#40;SQL Server Management Studio&#41;](../../ssms/solution/projects-sql-server-management-studio.md)  
  
