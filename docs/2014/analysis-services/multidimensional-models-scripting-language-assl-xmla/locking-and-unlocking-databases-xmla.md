---
title: Sperren und Entsperren von Datenbanken (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 120326066a9145c6e223f9af5735c4b3435222c6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219496"
---
# <a name="locking-and-unlocking-databases-xmla"></a>Sperren und Entsperren von Datenbanken (XMLA)
  Sperren und Entsperren von Datenbanken verwenden, bzw. die [Sperre](../xmla/xml-elements-commands/lock-element-xmla.md) und [Unlock](../xmla/xml-elements-commands/unlock-element-xmla.md) -Befehle in XML for Analysis (XMLA) verwenden. In der Regel sperren und entsperren andere XMLA-Befehle Objekte je nach Bedarf automatisch, um den Befehl während der Ausführung abschließen zu können. Explizit sperren oder Entsperren Sie eine Datenbank, um mehrere Befehle innerhalb einer einzelnen Transaktion auszuführen, z. B. können einem [Batch](../xmla/xml-elements-commands/batch-element-xmla.md) -Befehl aus, und verhindert, dass andere Anwendungen eine Schreibtransaktion in die Datenbank.  
  
## <a name="locking-databases"></a>Sperren von Datenbanken  
 Die `Lock` -Befehl sperrt die gemeinsame oder exklusive Nutzung innerhalb des Kontexts der gerade aktiven Transaktion ein Objekt. Eine Sperre in einem Objekt verhindert, dass ein Commit für Transaktionen ausgeführt wird, bevor die Sperre entfernt wurde. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt zwei Arten von Sperren: gemeinsame Sperren und exklusive Sperren. Weitere Informationen zu der von unterstützten Sperrentypen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], finden Sie unter [Mode-Element &#40;XMLA&#41;](../xmla/xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ermöglicht nur die Sperrung von Datenbanken. Die [Objekt](../xmla/xml-elements-properties/object-element-xmla.md) -Element muss einen Objektverweis auf enthalten eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank. Wenn das `Object`-Element nicht angegeben ist oder wenn das `Object`-Element auf ein Objekt verweist, bei dem es sich nicht um eine Datenbank handelt, tritt ein Fehler auf.  
  
> [!IMPORTANT]  
>  Nur Datenbankadministratoren oder Serveradministratoren können explizit einen `Lock`-Befehl ausgeben.  
  
 Andere Befehle geben implizit eine `Lock` Befehl eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank. Jeder Vorgang, der Daten oder Metadaten aus einer Datenbank, z. B. eine liest [Discover](../xmla/xml-elements-methods-discover.md) Methode oder ein [Execute](../xmla/xml-elements-methods-execute.md) ausgeführte Methode ein [Anweisung](../xmla/xml-elements-commands/statement-element-xmla.md) Befehl, gibt implizit eine freigegebene Sperren Sie für die Datenbank. Jede Transaktion, die Daten-oder Metadatenänderungen an ein Objekt auf übermittelt eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank, z. B. eine `Execute` ausgeführte Methode ein [Alter](../xmla/xml-elements-commands/alter-element-xmla.md) Befehl, gibt implizit eine exklusive Sperre für die Datenbank.  
  
## <a name="unlocking-objects"></a>Entsperren von Objekten  
 Der Befehl `Unlock` entfernt eine innerhalb des Kontexts der gerade aktiven Transaktion begründete Sperre.  
  
> [!IMPORTANT]  
>  Nur Datenbankadministratoren oder Serveradministratoren können explizit Ausgeben einer `Unlock` Befehl.  
  
 Alle Sperren werden im Kontext der aktuellen Transaktion abgehalten. Wenn die aktuelle Transaktion ausgeführt oder für diese ein Rollback durchgeführt wird, werden alle Sperren, die innerhalb der Transaktion definiert sind, automatisch aufgehoben.  
  
## <a name="see-also"></a>Siehe auch  
 [Element sperren &#40;XMLA&#41;](../xmla/xml-elements-commands/lock-element-xmla.md)   
 [Element Entsperren &#40;XMLA&#41;](../xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
