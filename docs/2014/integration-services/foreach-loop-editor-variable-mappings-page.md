---
title: Foreach-Schleifen-Editor (Seite Variablenzuordnungen) | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.foreachloopcontainer.mapping.f1
ms.assetid: aa847b87-f391-48a5-9849-eeda2d6b00b9
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b38583d5fe07315f6f80a54a188312f3becb3e28
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148397"
---
# <a name="foreach-loop-editor-variable-mappings-page"></a>Foreach-Schleifen-Editor (Seite Variablenzuordnungen)
  Mithilfe der Seite **Variablenzuordnungen** des Dialogfelds **Foreach-Schleifen-Editor** können Sie dem Auflistungswert Variablen zuordnen. Der Wert der Variable wird bei jeder Iteration der Schleife mit den Ausflistungswerten aktualisiert.  
  
 Informationen zum Verwenden des Foreach-Schleifencontainers in einem Integration Services-Paket finden Sie unter [Foreach Loop Container](control-flow/foreach-loop-container.md) . Informationen zum Konfigurieren dieses Containers finden Sie unter [Konfigurieren eines Foreach-Schleifencontainers](../../2014/integration-services/configure-a-foreach-loop-container.md).  
  
 Das Lernprogramm für [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] zum Erstellen eines einfachen ETL-Pakets enthält eine Lektion, die Ihnen zeigt, wie Sie eine Foreach-Schleife hinzufügen und konfigurieren können.  
  
## <a name="options"></a>Tastatur  
 **Variable**  
 Wählen Sie eine vorhandene Variable aus, oder klicken Sie auf \<**Neue Variable...**>, um eine neue Variable zu erstellen.  
  
> [!NOTE]  
>  Nachdem Sie eine Variable zugeordnet haben, wird der Liste **Variable** automatisch eine neue Zeile hinzugefügt.  
  
 **Verwandte Themen:** [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md), [Hinzufügen von Variablen](../../2014/integration-services/add-variable.md)  
  
 **Index**  
 Geben Sie bei Verwendung des Foreach-Elementenumerators den Index der Spalte im Auflistungswert an, der der Variable zugeordnet werden soll. Bei anderen Enumeratortypen ist der Index schreibgeschützt.  
  
> [!NOTE]  
>  Der Index basiert auf 0.  
  
 **Verwandte Themen**: [Schleife durch Excel-Dateien und Tabellen mit einem Foreach-Schleifencontainer](control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
 **Delete**  
 Wählen Sie eine Variable aus, und klicken Sie auf **Löschen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Foreach-Schleifen-Editor &#40;Seite "Allgemein"&#41;](general-page-of-integration-services-designers-options.md)   
 [Foreach-Schleifen-Editor &#40;Datensammlung (Seite)&#41;](../../2014/integration-services/foreach-loop-editor-collection-page.md)   
 [Seite Ausdrücke](expressions/expressions-page.md)   
 [For-Schleifencontainer](control-flow/for-loop-container.md)  
  
  