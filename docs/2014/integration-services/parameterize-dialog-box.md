---
title: Dialog Feld ' parametrisieren ' | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.parameter.f1
ms.assetid: fac02b6d-d247-447a-8940-e8700c7ac350
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 50bd1674dcc31240864f87a6e0d13c2599996e0b
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85423527"
---
# <a name="parameterize-dialog-box"></a>Parameterize Dialog Box
  Im Dialogfeld **Parametrisieren** können Sie einen neuen oder vorhandenen Parameter der Eigenschaft eines Tasks zuordnen. Sie öffnen das Dialogfeld, indem Sie mit der rechten Maustaste auf einen Task oder die Registerkarte „Ablaufsteuerung“ im [!INCLUDE[ssIS](../includes/ssis-md.md)]-Designer klicken und dann auf **Parametrisieren** klicken. Die folgende Liste beschreibt Benutzeroberflächenelemente im Dialogfeld. Weitere Informationen zu Parametern finden Sie unter [Integration Services-Parameter &#40;SSIS&#41;](integration-services-ssis-package-and-project-parameters.md).  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächen Elemente  
 **Eigenschaft**  
 Wählen Sie die Eigenschaft der Aufgabe aus, der Sie einem Parameter zuordnen möchten. Diese Liste wird mit allen Eigenschaften aufgefüllt, die parametrisiert werden können.  
  
 **Vorhandenen Parameter verwenden**  
 Aktivieren Sie diese Option, um die Eigenschaft der Aufgaben einem vorhandenen Parameter zuzuordnen und dann den Parameter aus Dropdownliste auszuwählen.  
  
 **Parameter nicht verwenden**  
 Wählen Sie diese Option aus, um einen Verweist auf einen Parameter zu entfernen. Der Parameter wurde nicht gelöscht.  
  
 **Neuen Parameter erstellen**  
 Aktivieren Sie diese Option, um einen neuen Parameter zu erstellen, den Sie der Eigenschaft der Aufgabe zuordnen möchten.  
  
 **Name**  
 Geben Sie den Namen des Parameters an, den Sie erstellen möchten.  
  
 **Beschreibung**  
 Geben Sie die Beschreibung für den Parameter an.  
  
 **Wert**  
 Geben Sie den Standardwert für den Parameter an. Dies wird auch als der Entwurfsstandard bezeichnet, der später zur Bereitstellungszeit überschrieben werden kann.  
  
 **Umfang**  
 Geben Sie den Bereich des Parameters an, indem Sie die Option **Projekt** oder die Option **Paket** aktivieren. Projektparameter werden verwendet, um jegliche externen Eingaben bereitzustellen, die das Projekt für ein oder mehrere Pakete im Projekt empfängt. Mit Paketparametern können Sie die Paketausführung ändern, ohne das Paket bearbeiten und erneut bereitstellen zu müssen.  
  
 **Heikles**  
 Geben Sie an, ob der Parameter vertraulich ist, indem Sie das Kontrollkästchen aktivieren oder deaktivieren. Vertrauliche Parameterwerte werden im Katalog verschlüsselt und in Transact-SQL oder SQL Server Management Studio als NULL-Wert angezeigt.  
  
 **Erforderlich**  
 Geben Sie an, ob für den Parameter ein anderer als der Entwurfsstandardwert angegeben werden muss, bevor das Paket ausgeführt werden kann.  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächen Elemente  
  
