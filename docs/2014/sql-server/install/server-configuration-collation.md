---
title: Serverkonfiguration – Sortierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- collation configuration, SQL Server
- collation configuration, Setup
- collation configuration
ms.assetid: e3986870-5be4-458b-b671-5ff12a27b022
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: abd57940e3caf8af66cb58fdeceebc802e877f6e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37290176"
---
# <a name="server-configuration---collation"></a>Serverkonfiguration – Sortierung
  Auf der Seite Serverkonfiguration - Sortierung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installations-Assistenten können Sie die Sortierungseinstellungen von [!INCLUDE[ssDE](../../includes/ssde-md.md)] und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] für die Sortierung ändern. Wählen Sie die entsprechende Option aus, um die Sortierungseinstellungen von verschiedenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installationen oder verschiedenen Computern abzugleichen.  
  
## <a name="options"></a>Tastatur  
 Anpassen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt zwei Gruppen von Sortierungen: Windows-Sortierungen und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sortierungen. Sie können die Sortierungseinstellungen für [!INCLUDE[ssDE](../../includes/ssde-md.md)] und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]entweder getrennt oder die gleiche Sortierung für beide Programme angeben.  
  
 Bei englischsprachigen (USA) Systemgebietsschemas wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sortierung standardmäßig automatisch ausgewählt. Die Standardsortierung für lokalisierte Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird durch das Systemgebietsschema von Windows für den Computer bestimmt.  
  
 Sie sollten die Standardeinstellungen nur ändern, wenn die Sortierungseinstellungen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installation mit den Sortierungseinstellungen einer anderen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz oder mit dem Windows-Systemgebietsschema eines anderen Computers übereinstimmen muss.  
  
 **Hinweis** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verwendet ausschließlich Windows-Sortierungen. Wenn Sie [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]installieren möchten, wählen Sie während des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setups eine Windows-Sortierung aus, um einheitliche Ergebnisse zwischen [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]sicherzustellen.  
  
 Weitere Informationen finden Sie unter [Sortierungseinstellungen im Setup-Programm](http://go.microsoft.com/fwlink/?LinkId=190977).  
  
## <a name="best-practices"></a>Bewährte Methoden  
 Weitere Informationen zu einer Tabelle von Windows-Systemgebietsschemas und den entsprechenden Standardsortierungen, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup verwendet werden, finden Sie unter [Sortierungseinstellungen im Setup-Programm](http://go.microsoft.com/fwlink/?LinkId=190977).  
  
 Wenn möglich, sollte in Unternehmen eine Sortierung verwendet werden. Auf diese Weise müssen Sie die Sortierung nicht explizit für jede Datenbank, jede Spalte, jeden Ausdruck oder jeden Bezeichner angeben. Wenn Sie mit mehreren Sortierungen und Codepageeinstellungen arbeiten müssen, codieren Sie Ihre Abfragen so, dass diese den Regeln der Sortierungspriorität entsprechen. Weitere Informationen finden Sie in der Onlinedokumentation im Thema [Rangfolge von Sortierungen &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql).  
  
 Berücksichtigen Sie folgende Empfehlungen beim Auswählen einer Sortierung für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Wählen Sie eine BINARY2-Sortierung aus, wenn auf Binärcodepunkten basierende Sortierungen zulässig sind.  
  
-   Wählen Sie eine Windows-Sortierung für einen einheitlichen, datentypübergreifenden Vergleich aus.  
  
-   Verwenden Sie die neue Sortierung (gekennzeichnet mit "* _100") für eine bessere sprachliche Sortierungsunterstützung. Weitere Informationen finden Sie unter [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
-   Wenn Sie planen, eine Datenbank zur aktualisierten Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu migrieren, wählen Sie die Sortierung aus, die zur vorhandenen Sortierung der Datenbank passt.  
  
  
