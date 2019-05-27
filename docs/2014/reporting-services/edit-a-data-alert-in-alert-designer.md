---
title: Bearbeiten einer Datenwarnung im Warnungs-Designer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- editing, data alerts
- updating, data alerts
- editing, alerts
- updating, alerts
ms.assetid: dde3664d-90b5-4b12-969e-39152c86e58a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 948bf1fd8145da9db9d0e0b81beabb8e7b3efaf2
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66109251"
---
# <a name="edit-a-data-alert-in-alert-designer"></a>Bearbeiten einer Datenwarnung im Warnungs-Designer
  Öffnen Sie die mit dem Datenwarnungs-Manager zu bearbeitende Datenwarnungsdefinition. Nur der Benutzer, der die Warnungsdefinition erstellt hat, kann sie bearbeiten. Weitere Informationen zum Öffnen des Datenwarnungs-Managers finden Sie unter [Verwalten meiner Datenwarnungen im Datenwarnungs-Manager](manage-my-data-alerts-in-data-alert-manager.md).  
  
 Das folgende Bild zeigt das Kontextmenü einer Datenwarnung im Datenwarnungs-Manager.  
  
 ![Datenwarnungs-Designer öffnen, indem Sie auf „Bearbeiten“ klicken](media/rs-alertmanageriwopendesigner.gif "Open Data Alert Designer by clicking Edit")  
  
 Die folgende Prozedur enthält die Schritte zum Öffnen der Warnungsdefinition im Datenwarnungs-Designer über den Datenwarnungs-Manager, um sie zu bearbeiten.  
  
### <a name="to-edit-a-data-alert-definition-in-data-alert-designer"></a>So bearbeiten Sie eine Datenwarnungsdefinition mit dem Datenwarnungs-Designer  
  
1.  Klicken Sie im Datenwarnungs-Manager mit der rechten Maustaste auf die zu bearbeitende Datenwarnungsdefinition, und klicken Sie dann auf **Bearbeiten**.  
  
     Die Warnungsdefinition wird im Datenwarnungs-Designer geöffnet.  
  
2.  Aktualisieren Sie die Regeln, Zeitplaneinstellungen und E-Mail-Einstellungen. Weitere Informationen finden Sie unter [Datenwarnungs-Designer](../../2014/reporting-services/data-alert-designer.md) und [Erstellen einer Datenwarnung im Datenwarnungs-Designer](create-a-data-alert-in-data-alert-designer.md).  
  
    > [!NOTE]  
    >  Sie können keinen anderen Datenfeed auswählen. Um einen anderen Datenfeed zu verwenden, erstellen Sie eine neue Datenwarnungsdefinition.  
  
3.  Klicken Sie auf **Speichern**.  
  
    > [!NOTE]  
    >  Wenn der Bericht und die aus dem Bericht generierten Datenfeeds geändert wurden, ist die Warnungsdefinition möglicherweise nicht mehr gültig. Dies tritt auf, wenn eine Spalte, auf die die Warnungsdefinition in ihren Regeln verweist, vom Bericht gelöscht wird, den Datentyp ändert, oder wenn der Bericht gelöscht oder verschoben wird. Sie können eine ungültige Warnungsdefinition öffnen. Sie können sie jedoch nicht erneut speichern, sofern sie nicht gemäß der aktuellen Version des Berichtsdatenfeeds gültig ist, auf dem sie basiert. Weitere Informationen dazu, wie Datenfeeds aus Berichten generiert werden, finden Sie unter [Generieren von Datenfeeds aus Berichten (Berichts-Generator und SSRS)](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Datenwarnungs-Manager für Warnungsadministratoren](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md)   
 [Reporting Services-Datenwarnungen](../ssms/agent/alerts.md)  
  
  
