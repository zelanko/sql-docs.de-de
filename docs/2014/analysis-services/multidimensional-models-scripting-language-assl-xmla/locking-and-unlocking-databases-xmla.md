---
title: Sperren und Entsperren von Datenbanken (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dbcf03fee7b0b286a88c4c3089f42741e60dbff0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161687"
---
# <a name="locking-and-unlocking-databases-xmla"></a>Sperren und Entsperren von Datenbanken (XMLA)
  Sperren und Entsperren von Datenbanken verwenden, bzw. die [Sperre](../xmla/xml-elements-commands/lock-element-xmla.md) und [Unlock](../xmla/xml-elements-commands/unlock-element-xmla.md) -Befehle in XML for Analysis (XMLA). In der Regel sperren und entsperren andere XMLA-Befehle Objekte je nach Bedarf automatisch, um den Befehl während der Ausführung abschließen zu können. Kann explizit sperren oder Entsperren Sie eine Datenbank, um mehrere Befehle innerhalb einer einzelnen Transaktion auszuführen, beispielsweise eine [Batch](../xmla/xml-elements-commands/batch-element-xmla.md) Befehl, während andere Anwendungen eine Schreibtransaktion in der Datenbank verhindert.  
  
## <a name="locking-databases"></a>Sperren von Datenbanken  
 Die `Lock` Befehl wird ein Objekt, das gemeinsame oder exklusive Nutzung innerhalb des Kontexts der gerade aktiven Transaktion gesperrt. Eine Sperre in einem Objekt verhindert, dass ein Commit für Transaktionen ausgeführt wird, bevor die Sperre entfernt wurde. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt zwei Arten von Sperren: gemeinsame Sperren und exklusive Sperren. Weitere Informationen zu den von unterstützten Typen von Sperren [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], finden Sie unter [Mode-Element &#40;XMLA&#41;](../xmla/xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ermöglicht nur die Sperrung von Datenbanken. Die [Objekt](../xmla/xml-elements-properties/object-element-xmla.md) Element muss einen Objektverweis auf enthalten eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank. Wenn das `Object`-Element nicht angegeben ist oder wenn das `Object`-Element auf ein Objekt verweist, bei dem es sich nicht um eine Datenbank handelt, tritt ein Fehler auf.  
  
> [!IMPORTANT]  
>  Nur Datenbankadministratoren oder Serveradministratoren können explizit einen `Lock`-Befehl ausgeben.  
  
 Andere Befehle geben implizit eine `Lock` Befehl eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank. Jeder Vorgang, Daten oder Metadaten aus einer Datenbank, z. B. alle einliest [Discover](../xmla/xml-elements-methods-discover.md) Methode oder ein [Execute](../xmla/xml-elements-methods-execute.md) externen ausgeführte Methode ein [Anweisung](../xmla/xml-elements-commands/statement-element-xmla.md) Befehl, gibt implizit eine gemeinsame für die Datenbank zu sperren. Jede Transaktion, die Änderungen an Daten oder Metadaten zu einem Objekt auf führt einen Commit für eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank, z. B. ein `Execute` externen ausgeführte Methode ein [Alter](../xmla/xml-elements-commands/alter-element-xmla.md) Befehl, gibt implizit eine exklusive Sperre für die Datenbank.  
  
## <a name="unlocking-objects"></a>Objekte entsperren  
 Der Befehl `Unlock` entfernt eine innerhalb des Kontexts der gerade aktiven Transaktion begründete Sperre.  
  
> [!IMPORTANT]  
>  Nur Datenbankadministratoren oder Serveradministratoren können explizit Ausgeben einer `Unlock` Befehl.  
  
 Alle Sperren werden im Kontext der aktuellen Transaktion abgehalten. Wenn die aktuelle Transaktion ausgeführt oder für diese ein Rollback durchgeführt wird, werden alle Sperren, die innerhalb der Transaktion definiert sind, automatisch aufgehoben.  
  
## <a name="see-also"></a>Siehe auch  
 [Element sperren &#40;XMLA&#41;](../xmla/xml-elements-commands/lock-element-xmla.md)   
 [Unlock-Element &#40;XMLA&#41;](../xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  