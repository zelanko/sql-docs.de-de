---
title: Sperren und Entsperren von Datenbanken (XMLA) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- locking [XML for Analysis]
- XML for Analysis, locking
- XMLA, locking
- unlocking objects
ms.assetid: 451afa58-ce03-4ecc-8dd3-9e7e8559b5f1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 96afa94f7c9c20072ae88b09a436d079ce0478ae
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544992"
---
# <a name="locking-and-unlocking-databases-xmla"></a>Sperren und Entsperren von Datenbanken (XMLA)
  Sie können Datenbanken Sperren und entsperren, indem Sie die Befehle [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) und [Unlock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) in XML for Analysis (XMLA) verwenden. In der Regel sperren und entsperren andere XMLA-Befehle Objekte je nach Bedarf automatisch, um den Befehl während der Ausführung abschließen zu können. Sie können eine Datenbank explizit sperren oder entsperren, um mehrere Befehle innerhalb einer einzelnen Transaktion (z. b. eines [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) -Befehls) auszuführen, und gleichzeitig verhindern, dass andere Anwendungen eine Schreib Transaktion an die Datenbank übergeben.  
  
## <a name="locking-databases"></a>Sperren von Datenbanken  
 Der `Lock`-Befehl sperrt die gemeinsame oder exklusive Nutzung eines Objekts im Rahmen der derzeit aktiven Transaktion. Eine Sperre in einem Objekt verhindert, dass ein Commit für Transaktionen ausgeführt wird, bevor die Sperre entfernt wurde. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt zwei Arten von Sperren: gemeinsame Sperren und exklusive Sperren. Weitere Informationen zu den von unterstützten Sperr Typen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] finden Sie unter [Mode-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/mode-element-xmla).  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ermöglicht nur die Sperrung von Datenbanken. Der [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) -Element muss einen Objektverweis zu einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank enthalten. Wenn das `Object`-Element nicht angegeben ist oder wenn das `Object`-Element auf ein Objekt verweist, bei dem es sich nicht um eine Datenbank handelt, tritt ein Fehler auf.  
  
> [!IMPORTANT]  
>  Nur Datenbankadministratoren oder Serveradministratoren können explizit einen `Lock`-Befehl ausgeben.  
  
 Andere Befehle geben implizit auf einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenbank einen `Lock`-Befehl aus. Jeder Vorgang, der Daten oder Metadaten aus einer Datenbank einliest (z. B. jede [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) -Methode oder eine [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) -Methode, die einen [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) -Befehl ausführt), gibt implizit eine gemeinsame Sperre der Datenbank aus. Jede Transaktion, die Änderungen an Daten oder Metadaten für ein Objekt in einer- [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Datenbank ausführt, z. b. eine-Methode, die `Execute` einen [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) -Befehl ausführt, gibt implizit eine exklusive Sperre für die Datenbank aus.  
  
## <a name="unlocking-objects"></a>Entsperren von Objekten  
 Der Befehl `Unlock` entfernt eine innerhalb des Kontexts der gerade aktiven Transaktion begründete Sperre.  
  
> [!IMPORTANT]  
>  Nur Datenbankadministratoren oder Server Administratoren können explizit einen `Unlock` Befehl ausgeben.  
  
 Alle Sperren werden im Kontext der aktuellen Transaktion abgehalten. Wenn die aktuelle Transaktion ausgeführt oder für diese ein Rollback durchgeführt wird, werden alle Sperren, die innerhalb der Transaktion definiert sind, automatisch aufgehoben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Lock-Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)   
 [Element &#40;XMLA entsperren&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)   
 [Entwickeln mit XMLA in Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
