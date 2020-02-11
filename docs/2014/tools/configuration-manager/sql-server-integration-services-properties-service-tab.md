---
title: Eigenschaften von SQL Server Integration Services (Registerkarte „Dienst“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 37f0acd9-c96f-48fd-9b53-2ca0097af242
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d4cb1b821604d125bc81148a06fb613c8547a449
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68186717"
---
# <a name="sql-server-integration-services-properties-service-tab"></a>Eigenschaften von SQL Server Integration Services (Registerkarte Dienst)
  Verwenden Sie die Registerkarte **Dienst** im Dialogfeld [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **-Eigenschaften**, um die folgenden Optionen anzuzeigen oder anzugeben.  
  
## <a name="options"></a>Tastatur  
 **Binärer Pfad**  
 Zeigt den Speicherort der Programmdateien an, die von diesem Dienst verwendet werden.  
  
 **Fehler Steuerung**  
 1 steht für `SERVICE_ERROR_NORMAL`. Wenn der Dienst nicht zusammen mit dem Computer gestartet werden kann, wird der Fehler vom Startprogramm protokolliert und eine Popupmeldung angezeigt, der Startvorgang aber fortgesetzt. Dieser Wert kann nicht geändert werden.  
  
 **Exitcode**  
 Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Fehlercode, der alle Probleme definiert, die beim Starten oder Beenden des Dienstes aufgetreten sind. Diese Eigenschaft wird auf **ERROR_SERVICE_SPECIFIC_ERROR** (1066) festgelegt, wenn der Fehler in Bezug auf den Dienst eindeutig ist, der durch diese Klasse repräsentiert wird, und Informationen zu dem Fehler stehen in der **ServiceSpecificExitCode** -Eigenschaft zur Verfügung. Vom Dienst wird dieser Wert bei der Ausführung und erneut bei normaler Beendigung auf NO_ERROR (0) festgelegt.  
  
 **Hostname**  
 Zeigt den Namen des Computers oder Clusters an, auf dem der [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Dienst ausgeführt wird.  
  
 **Name**  
 Zeigt den Anzeigenamen des Dienstes an.  
  
 **Prozess-ID**  
 Zeigt die Prozess-ID von Windows an.  
  
 **SQL-Diensttyp**  
 Zeigt den für aufrufende Prozesse bereitgestellten Diensttyp an. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert mehrere Dienste.  
  
 **Start Modus**  
 Richten Sie den Dienst mit den folgenden Auswahlmöglichkeiten ein:  
  
-   Manuell: Dieser Dienst wird nicht automatisch zusammen mit dem Computer gestartet. Zum Starten des Dienstes verwenden Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager oder ein anderes Tool.  
  
-   Automatisch: Dieser Dienst wird zusammen mit dem Computer gestartet.  
  
-   Deaktiviert: Dieser Dienst kann nicht gestartet werden.  
  
 **State**  
 Zeigt an, ob dieser Dienst ausgeführt wird, angehalten oder deaktiviert ist. „**…**“ gibt einen ausstehenden Statuswechsel an.  
  
  
