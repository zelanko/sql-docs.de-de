---
title: Verwalten von (öffnen, entsperren, umbenennen und löschen) ein Data Quality-Projekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.dqproject.opendqproject.f1
helpviewer_keywords:
- data quality project,delete
- data quality project,rename
- data quality project,unlock
- data quality project,open
ms.assetid: de8a2b04-4673-4beb-b4cf-96a28cdf3a93
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d08b2de75796b602c1f275c456d463c44a894fe7
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033157"
---
# <a name="manage-open-unlock-rename-and-delete-a-data-quality-project"></a>Verwalten von Data Quality-Projekten (Öffnen, Entsperren, Umbenennen, Löschen)
  In diesem Thema wird beschrieben, wie ein Data Quality-Projekt mithilfe von [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] verwaltet wird, zum Beispiel das Öffnen, Entsperren, Umbenennen und Löschen eines Data Quality-Projekts.  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="LimitationsRestrictions"></a> Einschränkungen  
  
-   Sie können kein gesperrtes Projekt öffnen, das von einem anderen Benutzer erstellt wurde.  
  
-   Sie können kein Data Quality-Projekt entsperren, umbenennen oder löschen, das von einem anderen Benutzer erstellt wurde.  
  
-   Sie können kein gesperrtes Data Quality-Projekt löschen. Zum Löschen müssen Sie es zunächst entsperren.  
  
-   Sie können nur ein Data Quality-Projekt entsperren, das von Ihnen erstellt wurde.  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
 Sie müssen mindestens ein Data Quality-Projekt verwalten.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Sie müssen über die Rolle „dqs_kb_editor“ oder „dqs_kb_operator“ in der Datenbank DQS_MAIN verfügen, um ein Data Quality-Projekt zu verwalten.  
  
##  <a name="Open"></a> Öffnen eines Data Quality-Projekts  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Ausführen der Data Quality-Clientanwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Klicken Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm auf **Data Quality-Projekt öffnen**. Der Bildschirm **Projekt öffnen** wird angezeigt.  
  
     Sie können ein unter **Zuletzt verwendetes Data Quality-Projekt** aufgelistetes Data Quality-Projekt auch direkt öffnen, indem Sie darauf klicken.  
  
3.  Wählen Sie auf dem Bildschirm **Projekt öffnen** das zu öffnende Data Quality-Projekt durch Klicken aus, und klicken Sie auf **Weiter**.  
  
4.  Das Data Quality-Projekt wird mit demselben Aktivitätsstatus geöffnet, mit dem es zuletzt geschlossen wurde. Ein Data Quality-Projekt hat die folgenden Status:  
  
    -   Für die **Bereinigungsaktivität** kann ein Data Quality-Projekt die folgenden Status haben: **Bereinigung - Zuordnen**, **Bereinigung - Bereinigen**, **Bereinigung - Ergebnisse verwalten und anzeigen**und **Bereinigung - Export**.  
  
    -   Für die **Abgleichsaktivität** kann ein Data Quality-Projekt die folgenden Status haben: **Abgleich - Zuordnung**, **Abgleich - Übereinstimmung**, **Abgleich - Survivorship**und **Abgleich - Export**.  
  
##  <a name="Unlock"></a> Entsperren eines Data Quality-Projekts  
 Wenn Sie ein Data Quality-Projekt erstellen, ist es gesperrt, um zu verhindern, dass es von anderen Benutzern verwendet oder geändert wird. Sie müssen das Data Quality-Projekt entsperren, nachdem Sie die Arbeit abgeschlossen haben, wenn Sie möchten, dass andere Benutzer am Data Quality-Projekt arbeiten können. Ein Schlosssymbol wird für gesperrte Projekte angezeigt.  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Ausführen der Data Quality-Clientanwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Klicken Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm auf **Data Quality-Projekt öffnen**. Der Bildschirm **Projekt öffnen** wird angezeigt.  
  
3.  Klicken Sie auf dem Bildschirm **Projekt öffnen** mit der rechten Maustaste auf ein gesperrtes Data Quality-Projekt, das von Ihnen erstellt wurde, und klicken Sie dann im Kontextmenü auf **Entsperren** . Ein grünes Häkchen wird für das Projekt angezeigt, das angibt, dass es entsperrt wurde.  
  
##  <a name="Rename"></a> Umbenennen eines Data Quality-Projekts  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Ausführen der Data Quality-Clientanwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Klicken Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm auf **Data Quality-Projekt öffnen**. Der Bildschirm **Projekt öffnen** wird angezeigt.  
  
3.  Klicken Sie auf dem Bildschirm **Projekt öffnen** mit der rechten Maustaste auf ein Data Quality-Projekt, das von Ihnen erstellt wurde, und klicken Sie dann im Kontextmenü auf **Umbenennen** .  
  
4.  Der Name des Data Quality-Projekts kann in der Spalte **Name** bearbeitet werden. Heben Sie einen neuen Namen ein, und drücken Sie die EINGABETASTE.  
  
##  <a name="Delete"></a> Löschen eines Data Quality-Projekts  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Ausführen der Data Quality-Clientanwendung](../../2014/data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Klicken Sie im [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] -Startbildschirm auf **Data Quality-Projekt öffnen**. Der Bildschirm **Projekt öffnen** wird angezeigt.  
  
3.  Klicken Sie auf dem Bildschirm **Projekt öffnen** mit der rechten Maustaste auf ein entsperrtes Data Quality-Projekt, das von Ihnen erstellt wurde, und klicken Sie dann im Kontextmenü auf **Löschen** .  
  
4.  Eine Bestätigungsmeldung wird angezeigt. Klicken Sie auf **Ja**.  
  
  
