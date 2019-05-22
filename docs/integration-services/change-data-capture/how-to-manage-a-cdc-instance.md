---
title: Verwalten einer CDC-Instanz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5d9e677f-b872-497d-9cde-472184a214ab
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5fd3788cb31e7e3e6408cc7161f45ba008cf081c
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65728783"
---
# <a name="how-to-manage-a-cdc-instance"></a>How to Manage a CDC Instance

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  In diesem Verfahren wird beschrieben, wie Sie die CDC Designer Console zum Verwalten von CDC-Instanzvorgängen zur Laufzeit verwenden.  
  
### <a name="to-manage-cdc-instance-operations"></a>So verwalten Sie CDC-Instanzvorgänge  
  
1.  Wählen Sie im Menü **Start** die Option **CDC Designer Console**aus.  
  
2.  Erweitern Sie im linken Bereich die Option **Change Data Capture** , und erweitern Sie dann den Dienst, der die anzuzeigende Instanz enthält.  
  
3.  Wählen Sie den Namen einer Instanz aus, die Sie verwenden möchten.  
  
4.  Klicken Sie in der CDC Designer Console rechts im **Aktionsbereich** auf den Vorgang, den Sie ausführen möchten.  
  
     Sie können auch im linken Bereich mit der rechten Maustaste auf den Namen der Instanz klicken und den auszuführenden Vorgang auswählen.  
  
     Sie können die folgenden Tasks ausführen:  
  
    -   **Start**: Die Aufzeichnung der Änderungen wird gestartet.  
  
    -   **Stop**: Dient zum Beenden der Aufzeichnung der Änderungen  
  
    -   **Reset**: Klicken Sie auf **Zurücksetzen** , um die CDC-Instanz auf ihren ursprünglichen (leeren) Zustand zurückzusetzen. Diese Option ist verfügbar, wenn die CDC-Instanz beendet wurde. Alle Änderungen in den Änderungstabellen und der interne Status der CDC-Instanz werden gelöscht. Wenn die CDC-Instanz später dann gestartet wird, beginnt die Änderungsaufzeichnung ab diesem Zeitpunkt und schließt nur Transaktionen ein, die nach dem Starten der CDC-Instanz gestartet wurden.  
  
    -   **Löschen:** Dient zum Löschen der CDC-Instanz.  
  
    -   **Oracle Logging Script**: Klicken Sie auf **Oracle Logging Script**, um das entsprechende Dialogfeld mit dem Oracle-Skript für ergänzende Protokollierung anzuzeigen. Informationen zu den Schritten, die Sie in diesem Dialogfeld ausführen können, finden Sie unter [Oracle Supplemental Logging Script](../../integration-services/change-data-capture/oracle-supplemental-logging-script.md).  
  
         **Hinweis**: Wenn Sie die ergänzenden Protokollierungsskripts ausführen, wird das Dialogfeld Oracle Credentials for Running Script geöffnet, in dem Sie einen gültigen Oracle-Benutzernamen und das dazugehörige Kennwort angeben können. Informationen zum Bereitstellen der richtigen Oracle-Anmeldeinformationen finden Sie unter [Oracle Credentials for Running Script](../../integration-services/change-data-capture/oracle-credentials-for-running-script.md).  
  
    -   **CDC Instance Deployment**: Dient zum Generieren eines Bereitstellungsskripts für die CDC-Instanz. Informationen zu diesem Dialogfeld finden Sie unter [CDC Instance Deployment Script](../../integration-services/change-data-capture/cdc-instance-deployment-script.md).  
  
     Weitere Informationen zu diesen Tasks finden Sie unter [Manage a CDC Instance](../../integration-services/change-data-capture/manage-a-cdc-instance.md).  
  
 Sie können auch **Eigenschaften** wählen, um die Konfigurationseigenschaften der CDC-Instanz zu bearbeiten. Weitere Informationen zum Bearbeiten der CDC-Instanzeigenschaften finden Sie unter [Edit Instance Properties](../../integration-services/change-data-capture/edit-instance-properties.md).  
  
  
