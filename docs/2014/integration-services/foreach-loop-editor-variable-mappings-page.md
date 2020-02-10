---
title: Foreach-Schleifen-Editor (Seite Variablen Zuordnungen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.mapping.f1
ms.assetid: aa847b87-f391-48a5-9849-eeda2d6b00b9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 03488e4cfd3a0cc905a58166f381f68eb3292c49
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66058524"
---
# <a name="foreach-loop-editor-variable-mappings-page"></a>Foreach-Schleifen-Editor (Seite Variablenzuordnungen)
  Auf der Seite **Variablenzuordnungen** des Dialogfelds **Foreach-Schleifen-Editor** können Sie dem Sammlungswert Variablen zuordnen. Der Wert der Variablen wird bei jeder Iteration der Schleife mit den Sammlungswerten aktualisiert.  
  
 Informationen zum Verwenden des Foreach-Schleifencontainers in einem Integration Services-Paket finden Sie unter [Foreach Loop Container](control-flow/foreach-loop-container.md) . Informationen zum Konfigurieren dieses Containers finden Sie unter [Konfigurieren eines Foreach-Schleifencontainers](../../2014/integration-services/configure-a-foreach-loop-container.md).  
  
 Das [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Tutorial zum Erstellen eines einfachen ETL-Pakets enthält eine Lektion, in der Sie eine foreach-Schleife hinzufügen und konfigurieren können.  
  
## <a name="options"></a>Tastatur  
 **Variable**  
 Wählen Sie eine vorhandene Variable aus, \<oder klicken Sie auf **neue Variable...**>, um eine neue Variable zu erstellen.  
  
> [!NOTE]  
>  Nachdem Sie eine Variable zugeordnet haben, wird der Liste **Variable** automatisch eine neue Zeile hinzugefügt.  
  
 **Verwandte Themen**: [Integration Services &#40;SSIS-&#41; Variablen](integration-services-ssis-variables.md), [Variable hinzufügen](../../2014/integration-services/add-variable.md)  
  
 **Sin**  
 Geben Sie bei Verwendung des Foreach-Element-Enumerators den Index der Spalte im Sammlungswert an, der der Variable zugeordnet werden soll. Bei anderen Enumeratortypen ist der Index schreibgeschützt.  
  
> [!NOTE]  
>  Der Index basiert auf 0.  
  
 **Verwandte Themen**: [Schleife durch Excel-Dateien und-Tabellen mit einem Foreach-Schleifen Container](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
 **Löschen**  
 Wählen Sie eine Variable aus, und klicken Sie auf **Löschen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Foreach-Schleifen-Editor &#40;Seite "Allgemein"&#41;](general-page-of-integration-services-designers-options.md)   
 [Foreach-Schleifen-Editor &#40;Sammlungs Seite&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [For-Schleifencontainer](control-flow/for-loop-container.md)  
  
  
