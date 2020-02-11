---
title: Verarbeiten einer Mining Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], processing
ms.assetid: 4162f33e-c23f-4293-8905-271781e45fa4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 92793adcf2fd04b1dac0c26933c1d5969a31f1a5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66083113"
---
# <a name="process-a-mining-structure"></a>Verarbeiten einer Miningstruktur
  Bevor Sie die einer Miningstruktur zugeordneten Miningmodelle durchsuchen und verwenden können, müssen Sie das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt bereitstellen und die Miningstruktur und die Miningmodelle verarbeiten. Wenn Sie eine Änderung an der Miningstruktur oder den Miningmodellen vornehmen, werden Sie zur erneuten Bereitstellung und Verarbeitung aufgefordert. Beim Verarbeiten der Struktur auf der Registerkarte **Miningstruktur** des Data Mining-Designers von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] werden auch alle zugeordneten Modelle verarbeitet.  
  
 Sie können eine Miningstruktur mit den folgenden Tools verarbeiten:  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   XMLA: Process-Befehl  
  
 Informationen zum Verarbeiten einzelner Modelle finden Sie unter [Verarbeiten eines Miningmodells](process-a-mining-model.md).  
  
### <a name="to-process-a-mining-structure-and-all-associated-mining-models-using-sql-server-data-tools"></a>So verarbeiten Sie eine Miningstruktur und alle zugeordneten Miningmodelle mit SQL Server-Datentools  
  
1.  Wählen Sie in **im Menüelement** Miningmodell **die Option** Miningstruktur und alle Modelle verarbeiten [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]aus.  
  
     Wenn Sie Änderungen an der Struktur vorgenommen haben, werden Sie aufgefordert, die Struktur erneut bereitzustellen, bevor die Modelle verarbeitet werden. Klicken Sie auf **Ja**.  
  
2.  Klicken Sie im Dialogfeld **Mining Struktur verarbeiten \<-Struktur>** auf **Ausführen** .  
  
     Das Dialogfeld **Verarbeitungsstatus** wird geöffnet und zeigt detaillierte Informationen zur Verarbeitung des Modells an.  
  
3.  Klicken Sie nach Abschluss der Modellverarbeitung im Dialogfeld **Verarbeitungsstatus** auf **Schließen** .  
  
4.  Klicken Sie im Dialogfeld **Mining Struktur verarbeiten \<-Struktur>** auf **Schließen** .  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tasks und Anweisungen für Miningstrukturen](mining-structure-tasks-and-how-tos.md)  
  
  
