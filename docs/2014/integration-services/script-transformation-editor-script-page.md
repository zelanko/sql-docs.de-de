---
title: Transformations-Editor (Skriptseite) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scriptcomponent.script.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 102988ac347543a4d2e2110d4c8511c398be9348
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48060680"
---
# <a name="script-transformation-editor-script-page"></a>Transformations-Editor für Skripterstellung (Seite Skript)
  Auf der Registerkarte **Skript** des Dialogfelds **Transformations-Editor für Skripterstellung** können Sie ein Skript und verknüpfte Eigenschaften angeben.  
  
 Weitere Informationen zur Skriptkomponente finden Sie unter [Script Component](data-flow/transformations/script-component.md) und [Konfigurieren der Skriptkomponente im Skriptkomponenten-Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md). Weitere Informationen zur Programmierung der Skriptkomponente finden Sie unter [Erweitern des Datenflusses mit der Skriptkomponente](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
## <a name="options"></a>Tastatur  
 **Eigenschaften**  
 Zeigt die Skripttransformationseigenschaften an und ermöglicht Änderungen. Viele dieser Eigenschaften sind schreibgeschützt. Die folgenden Eigenschaften können Sie ändern:  
  
|value|Description|  
|-----------|-----------------|  
|**Beschreibung**|Beschreibt den Zweck der Skripttransformation.|  
|**LocaleID**|Gibt das Gebietsschema für die Bereitstellung regionsspezifischer Informationen für das Bestellen sowie für Datums- und Zeitformate an.|  
|**Name**|Geben Sie einen aussagekräftigen Namen für die Komponente ein.|  
|**ValidateExternalMetadata**|Zeigt an, ob von der Skripttransformation zur Entwurfszeit Spaltenmetadaten mithilfe externer Datenquellen überprüft werden. Der Wert `false` wird die Überprüfung bis zur Ausführungszeit verzögert.|  
|**ReadOnlyVariables**|Geben Sie eine durch Trennzeichen getrennte Liste von Variablen für den schreibgeschützten Zugriff durch die Skripttransformation ein.<br /><br /> Hinweis: Bei Variablennamen wird nach Groß-/Kleinschreibung unterschieden.|  
|**ReadWriteVariables**|Geben Sie eine durch Trennzeichen getrennte Liste von Variablen für den Lese-/Schreibzugriff durch die Skripttransformation ein.<br /><br /> Hinweis: Bei Variablennamen wird nach Groß-/Kleinschreibung unterschieden.|  
|**ScriptLanguage**|Wählen Sie die Skriptsprache aus, die von der Skriptkomponente verwendet werden soll.<br /><br /> Um die Standardskriptsprache für Skriptkomponenten und Skripttasks festzulegen, verwenden Sie im Dialogfeld **Optionen** auf der Seite **Allgemein** die Option **Skriptsprache** . Weitere Informationen finden Sie unter [General Page](general-page-of-integration-services-designers-options.md).|  
|**UserComponentTypeName**|Gibt die <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost>-Klasse und die `Microsoft.SqlServer.TxScript`-Assembly an, die die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Infrastruktur unterstützen.|  
  
 **Skript bearbeiten**  
 Verwenden Sie [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Tools für Anwendungen (VSTA), um ein Skript zu erstellen oder zu ändern.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Skriptkomponententyp auswählen](../../2014/integration-services/select-script-component-type.md)   
 [Transformations-Editor &#40;Geben Sie die Seite "Spalten"&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md)   
 [Transformations-Editor &#40;Eingaben und Ausgaben Seite&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md)   
 [Transformations-Editor &#40;Verbindungsseite-Manager&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md)   
 [Zusätzliche Skriptkomponentenbeispiele](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
