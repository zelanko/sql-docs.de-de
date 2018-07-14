---
title: Abfrage-Generator (Berichts-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.dataview.vdtquerydesigner.f1
- sql12.rtp.rptwizard.querybuilder.f1
helpviewer_keywords:
- Query Builder [Reporting Services]
ms.assetid: 1b0904ea-28c1-448e-b56c-c0fdfbc8b222
caps.latest.revision: 21
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8fef45f5ec6c4b9e0682ea625b2cc84bc8aaa089
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37253462"
---
# <a name="query-builder-report-wizard"></a>Abfrage-Generator (Berichts-Assistent)
  Mithilfe des Abfrage-Generators können Sie eine Abfrage angeben, die ein Resultset abruft, das in einem Bericht verwendet werden soll. Sie können zwischen zwei Abfrage-Generatoren auswählen:  
  
-   Der textbasierte Abfrage-Generator (Standard) stellt einen einfachen Arbeitsbereich zum Angeben einer Abfrage und Anzeigen der Ergebnisse zur Verfügung. Sie können mehrere [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen, Abfrage- oder Befehlssyntaxen für benutzerdefinierte Datenverarbeitungserweiterungen und Abfragen angeben, die als Ausdrücke angegeben sind. Da der allgemeine Abfrage-Generator die Abfrage nicht zuvor verarbeitet und eine beliebige Abfragesyntax aufnehmen kann, handelt es sich hierbei um das standardmäßige Abfrage-Generator-Tool für den Berichts-Designer.  
  
-   Der grafische Abfrage-Generator bietet mehr visuelle Möglichkeiten. Er kommt in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und anderen Teilen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]zum Einsatz. Sie können den grafischen Abfrage-Generator verwenden, wenn Sie keine Ausdrücke oder mehrteilige SQL-Anweisungen erstellen.  
  
     Um zum grafischen Abfrage-Generator zu wechseln, schalten Sie die Schaltfläche **Als Text bearbeiten** in der oberen linken Ecke des Fensters um.  
  
 Sie können auch eine Abfrage aus einem anderen Bericht importieren.  
  
## <a name="query-builder-options"></a>Optionen des Abfrage-Generators  
 **Als Text bearbeiten**  
 Wechselt zwischen dem textbasierten und dem grafischen Abfrage-Designer, wenn beide für die Abfrage einsetzbar sind.  
  
 **Importieren**  
 Öffnet das Dialogfeld **Abfrage importieren** und zeigt RDL- und SQL-Dateien für jeden verfügbaren Bericht an. Sie können die importierte Abfrage so verwenden, wie sie ist, oder diese im Abfrage-Generator ändern.  
  
 **! (Ausführen)**  
 Führt die Abfrage aus und gibt ein Resultset zurück, falls die Abfrage gültig ist. Beachten Sie, dass Sie die Abfrage nicht ausführen können, wenn sie ein Ausdruck ist. Um eine ausdruckbasierte Abfrage zu überprüfen, müssen Sie eine Vorschau des Berichts anzeigen.  
  
 **Befehlstyp**  
 Gibt Text, die gespeicherte Prozedur oder den Tabellendirektmodus (TableDirect) an. Ob ein Befehlstyp verfügbar ist, hängt von der Datenverarbeitungserweiterung ab, die Sie angegeben haben.  
  
 **Abfragebereich**  
 Geben Sie die Abfrage ein.  
  
 **Ergebnisbereich**  
 Zeigt das von der Abfrage zurückgegebene Resultset an.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Hilfe des Berichts-Assistenten](../../2014/reporting-services/report-wizard-help.md)  
  
  
