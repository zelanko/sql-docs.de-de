---
title: Verwalten einer CDC-Instanz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5d9e677f-b872-497d-9cde-472184a214ab
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 058010d0e32fb26cf4c12e720342af04bd784768
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52804782"
---
# <a name="how-to-manage-a-cdc-instance"></a>How to Manage a CDC Instance
  In diesem Verfahren wird beschrieben, wie Sie die CDC Designer Console zum Verwalten von CDC-Instanzvorgängen zur Laufzeit verwenden.  
  
### <a name="to-manage-cdc-instance-operations"></a>So verwalten Sie CDC-Instanzvorgänge  
  
1.  Wählen Sie im Menü **Start** die Option **CDC Designer Console**aus.  
  
2.  Erweitern Sie im linken Bereich die Option **Change Data Capture** , und erweitern Sie dann den Dienst, der die anzuzeigende Instanz enthält.  
  
3.  Wählen Sie den Namen einer Instanz aus, die Sie verwenden möchten.  
  
4.  Klicken Sie in der CDC Designer Console rechts im **Aktionsbereich** auf den Vorgang, den Sie ausführen möchten.  
  
     Sie können auch im linken Bereich mit der rechten Maustaste auf den Namen der Instanz klicken und den auszuführenden Vorgang auswählen.  
  
     Sie können die folgenden Tasks ausführen:  
  
    -   **Starten Sie**: Starten Sie die Aufzeichnung der Änderungen.  
  
    -   **Beenden Sie**: Zum Beenden der Aufzeichnung der Änderungen  
  
    -   **Zurücksetzen**: Klicken Sie auf **Zurücksetzen** , um die CDC-Instanz auf ihren ursprünglichen (leeren) Zustand zurückzusetzen. Diese Option ist verfügbar, wenn die CDC-Instanz beendet wurde. Alle Änderungen in den Änderungstabellen und der interne Status der CDC-Instanz werden gelöscht. Wenn die CDC-Instanz später dann gestartet wird, beginnt die Änderungsaufzeichnung ab diesem Zeitpunkt und schließt nur Transaktionen ein, die nach dem Starten der CDC-Instanz gestartet wurden.  
  
    -   **Löschen Sie**: So löschen Sie die CDC-Instanz.  
  
    -   **Oracle-Protokollierungsskript**: Klicken Sie auf **Oracle Logging Script** um das entsprechende Dialogfeld mit dem Oracle-protokollierungsskript anzuzeigen. Informationen zu den Schritten, die Sie in diesem Dialogfeld ausführen können, finden Sie unter [Oracle Supplemental Logging Script](oracle-supplemental-logging-script.md).  
  
         **Hinweis**: Wenn Sie die ergänzenden Protokollierungsskripts ausführen, wird das Dialogfeld Oracle Credentials for Running Script geöffnet, in dem Sie einen gültigen Oracle-Benutzernamen und das dazugehörige Kennwort angeben können. Informationen zum Bereitstellen der richtigen Oracle-Anmeldeinformationen finden Sie unter [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md).  
  
    -   **CDC Instance Deployment**: Zum Generieren eines Bereitstellungsskripts für die CDC-Instanz. Informationen zu diesem Dialogfeld finden Sie unter [CDC Instance Deployment Script](cdc-instance-deployment-script.md).  
  
     Weitere Informationen zu diesen Tasks finden Sie unter [Manage a CDC Instance](manage-a-cdc-instance.md).  
  
 Sie können auch **Eigenschaften** wählen, um die Konfigurationseigenschaften der CDC-Instanz zu bearbeiten. Weitere Informationen zum Bearbeiten der CDC-Instanzeigenschaften finden Sie unter [Edit Instance Properties](edit-instance-properties.md).  
  
  
