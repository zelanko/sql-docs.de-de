---
title: Analysis Services Editor für den Task ' DDL ausführen ' (DDL-Seite) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asexecuteddltask.ddl.f1
helpviewer_keywords:
- Analysis Services Execute DDL Task Editor
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 7cb1c84cccf4123f6ca1894baba5676937d80a15
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84925641"
---
# <a name="analysis-services-execute-ddl-task-editor-ddl-page"></a>Editor für den Analysis Services-Task 'DDL ausführen' (Seite DDL)
  Auf der Seite **DDL** des Dialogfelds **Editor für den Analysis Services-Task „DDL ausführen“** können Sie eine Verbindung mit einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt oder einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Datenbank angeben sowie Informationen zur Quelle der DDL-Anweisungen (Data Definition Language) angeben.  
  
 Informationen, um sich mit diesem Thema vertraut zu machen, finden Sie unter [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md).  
  
## <a name="static-options"></a>Statische Optionen  
 **Connection**  
 Wählen Sie ein [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Projekt oder einen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Verbindungs-Manager aus der Liste aus, oder klicken Sie auf, \<**New connection...**> und verwenden Sie das Dialogfeld **Analysis Services Verbindungs-Manager hinzufügen** , um eine neue Verbindung herzustellen.  
  
 **Verwandte Themen:** [Referenz zur Benutzeroberfläche des Dialogfelds Analysis Services-Verbindungs-Manager hinzufügen](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md), [Analysis Services-Verbindungs-Manager](connection-manager/analysis-services-connection-manager.md)  
  
 **SourceType**  
 Geben Sie den Quelltyp der DDL-Anweisung an. Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten Optionen verfügbar:  
  
|Value|Beschreibung|  
|-----------|-----------------|  
|**Direkte Eingabe**|Legen Sie die Quelle der im Textfeld **SourceDirect** gespeicherten DDL-Anweisung fest. Wenn Sie diesen Wert auswählen, werden im folgenden Abschnitt die dynamischen Optionen angezeigt.|  
|**Dateiverbindung**|Legen Sie die Quelle für eine Datei fest, in der die DDL-Anweisung enthalten ist. Wenn Sie diesen Wert auswählen, werden im folgenden Abschnitt die dynamischen Optionen angezeigt.|  
|**Variable**|Legen Sie die Quelle für eine Variable fest. Wenn Sie diesen Wert auswählen, werden im folgenden Abschnitt die dynamischen Optionen angezeigt.|  
  
## <a name="dynamic-options"></a>Dynamische Optionen  
  
### <a name="sourcetype--direct-input"></a>SourceType = Direkteingabe  
 **Quelle**  
 Geben Sie die DDL-Anweisungen ein, oder klicken Sie auf die Schaltfläche mit den Auslassungs Punkten **(...)** , und geben Sie dann im Dialogfeld **DDL-Anweisungen**  
  
### <a name="sourcetype--file-connection"></a>SourceType = File Connection  
 **Quelle**  
 Wählen Sie eine Dateiverbindung aus der Liste aus, oder klicken Sie \<**New connection...**> auf, und verwenden Sie das Dialogfeld **Dateiverbindungs-Manager** , um eine neue Verbindung herzustellen.  
  
 **Verwandte Themen:** [Dateiverbindungs-Manager](connection-manager/file-connection-manager.md)  
  
### <a name="sourcetype--variable"></a>SourceType = Variable  
 **Quelle**  
 Wählen Sie eine Variable aus der Liste aus, oder klicken Sie \<**New variable...**> auf das Dialogfeld **Variable hinzufügen** , um eine neue Variable zu erstellen.  
  
 **Verwandte Themen:** [Integration Services-Variablen &#40;SSIS&#41;](integration-services-ssis-variables.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Analysis Services Editor für den Task ' DDL ausführen ' &#40;Seite Allgemein&#41;](general-page-of-integration-services-designers-options.md)   
 [Ausdrucks Seite](expressions/expressions-page.md)   
 [Ablaufsteuerung](control-flow/control-flow.md)   
 [Analysis Services Skriptsprache &#40;ASSL&#41; Referenz](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)   
 [XML for Analysis-Referenz &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)  
  
  
