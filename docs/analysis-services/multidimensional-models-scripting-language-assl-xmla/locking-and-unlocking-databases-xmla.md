---
title: Sperren und Entsperren von Datenbanken (XMLA) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1f827221a6334b0ff1daf523460562527c3a3f66
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63262070"
---
# <a name="locking-and-unlocking-databases-xmla"></a>Sperren und Entsperren von Datenbanken (XMLA)
  Sperren und Entsperren von Datenbanken verwenden, bzw. die [Sperre](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) und [Unlock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) -Befehle in XML for Analysis (XMLA) verwenden. In der Regel sperren und entsperren andere XMLA-Befehle Objekte je nach Bedarf automatisch, um den Befehl während der Ausführung abschließen zu können. Explizit sperren oder Entsperren Sie eine Datenbank, um mehrere Befehle innerhalb einer einzelnen Transaktion auszuführen, z. B. können einem [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) -Befehl aus, und verhindert, dass andere Anwendungen eine Schreibtransaktion in die Datenbank.  
  
## <a name="locking-databases"></a>Sperren von Datenbanken  
 Der **Lock** -Befehl sperrt die gemeinsame oder exklusive Nutzung eines Objekts im Rahmen der derzeit aktiven Transaktion. Eine Sperre in einem Objekt verhindert, dass ein Commit für Transaktionen ausgeführt wird, bevor die Sperre entfernt wurde. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt zwei Arten von Sperren: gemeinsame Sperren und exklusive Sperren. Weitere Informationen zu der von unterstützten Sperrentypen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], finden Sie unter [Mode-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/mode-element-xmla).  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ermöglicht nur die Sperrung von Datenbanken. Der [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) -Element muss einen Objektverweis zu einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank enthalten. Wenn das **Object** -Element nicht angegeben ist oder wenn das **Object** -Element auf ein Objekt verweist, bei dem es sich nicht um eine Datenbank handelt, tritt ein Fehler auf.  
  
> [!IMPORTANT]  
>  Nur Datenbankadministratoren oder Serveradministratoren können explizit einen **Lock** -Befehl ausgeben.  
  
 Andere Befehle geben implizit auf einer **Lock** -Datenbank einen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank enthalten. Jeder Vorgang, der Daten oder Metadaten aus einer Datenbank einliest (z. B. jede [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) -Methode oder eine [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) -Methode, die einen [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) -Befehl ausführt), gibt implizit eine gemeinsame Sperre der Datenbank aus. Jede Transaktion, die Daten- oder Metadatenänderungen an ein Objekt auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank übermittelt (z. B. eine **Execute** -Methode, die einen [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) -Befehl ausführt), gibt implizit eine exklusive Sperre der Datenbank aus.  
  
## <a name="unlocking-objects"></a>Entsperren von Objekten  
 Der Befehl **Unlock** entfernt eine innerhalb des Kontexts der gerade aktiven Transaktion begründete Sperre.  
  
> [!IMPORTANT]  
>  Nur Datenbankadministratoren oder Serveradministratoren können explizit einen **Unlock** -Befehl ausgeben.  
  
 Alle Sperren werden im Kontext der aktuellen Transaktion abgehalten. Wenn die aktuelle Transaktion ausgeführt oder für diese ein Rollback durchgeführt wird, werden alle Sperren, die innerhalb der Transaktion definiert sind, automatisch aufgehoben.  
  
## <a name="see-also"></a>Siehe auch  
 [Element sperren &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)   
 [Element Entsperren &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)   
 [Entwickeln mit XMLA in Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
