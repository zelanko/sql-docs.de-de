---
title: Transformations-Editor (Skriptseite) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.script.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1628acc984433b1def07c63387b1630c902885aa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66056057"
---
# <a name="script-transformation-editor-script-page"></a>Transformations-Editor für Skripterstellung (Seite Skript)
  Auf der Registerkarte **Skript** des Dialogfelds **Transformations-Editor für Skripterstellung** können Sie ein Skript und verknüpfte Eigenschaften angeben.  
  
 Weitere Informationen zur Skriptkomponente finden Sie unter [Skriptkomponente](data-flow/transformations/script-component.md) und [Konfigurieren der Skriptkomponente im Skriptkomponenten-Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md). Weitere Informationen zur Programmierung der Skriptkomponente finden Sie unter [Erweitern des Datenflusses mit der Skriptkomponente](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
## <a name="options"></a>Tastatur  
 **Eigenschaften**  
 Zeigt die Skripttransformationseigenschaften an und ermöglicht Änderungen. Viele dieser Eigenschaften sind schreibgeschützt. Die folgenden Eigenschaften können Sie ändern:  
  
|Wert|Description|  
|-----------|-----------------|  
|**Beschreibung**|Beschreibt den Zweck der Skripttransformation.|  
|**LocaleID**|Gibt das Gebietsschema für die Bereitstellung regionsspezifischer Informationen für das Bestellen sowie für Datums- und Zeitformate an.|  
|**Name**|Geben Sie einen aussagekräftigen Namen für die Komponente ein.|  
|**ValidateExternalMetadata**|Zeigt an, ob von der Skripttransformation zur Entwurfszeit Spaltenmetadaten mithilfe externer Datenquellen überprüft werden. Bei dem Wert `false` wird die Überprüfung bis zur Ausführungszeit verzögert.|  
|**ReadOnlyVariables**|Geben Sie eine durch Trennzeichen getrennte Liste von Variablen für den schreibgeschützten Zugriff durch die Skripttransformation ein.<br /><br /> Hinweis: Bei Variablennamen wird nach Groß-/Kleinschreibung unterschieden.|  
|**ReadWriteVariables**|Geben Sie eine durch Trennzeichen getrennte Liste von Variablen für den Lese-/Schreibzugriff durch die Skripttransformation ein.<br /><br /> Hinweis: Bei Variablennamen wird nach Groß-/Kleinschreibung unterschieden.|  
|**ScriptLanguage**|Wählen Sie die Skriptsprache aus, die von der Skriptkomponente verwendet werden soll.<br /><br /> Um die Standardskriptsprache für Skriptkomponenten und Skripttasks festzulegen, verwenden Sie im Dialogfeld **Optionen** auf der Seite **Allgemein** die Option **Skriptsprache** . Weitere Informationen finden Sie unter [General Page](general-page-of-integration-services-designers-options.md).|  
|**UserComponentTypeName**|Gibt die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost>-Klasse und die `Microsoft.SqlServer.TxScript`-Assembly an, die die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Infrastruktur unterstützen.|  
  
 **Skript bearbeiten**  
 Verwenden Sie [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Tools für Anwendungen (VSTA), um ein Skript zu erstellen oder zu ändern.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Skriptkomponententyp auswählen](../../2014/integration-services/select-script-component-type.md)   
 [Transformations-Editor für Skripterstellung &#40;Seite Eingabespalten&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md)   
 [Transformations-Editor für Skripterstellung &#40;Seiten Eingaben und Ausgaben&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md)   
 [Transformations-Editor für Skripterstellung &#40;Seite Verbindungs-Manager&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md)   
 [Zusätzliche Skriptkomponentenbeispiele](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
