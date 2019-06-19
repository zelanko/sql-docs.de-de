---
title: Hinzufügen eines SSIS Scale Out-Workers mit dem Manager für horizontales Hochskalieren | Microsoft-Dokumentation
description: In diesem Artikel wird beschrieben, wie ein SSIS Scale Out-Worker mithilfe des Scale Out-Managers in eine vorhandene Scale Out-Umgebung hinzugefügt wird.
ms.custom: performance
ms.date: 12/19/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: 5375f3992cd5d969276b02612f02ab4c32842689
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65718781"
---
# <a name="add-a-scale-out-worker-with-scale-out-manager"></a>Hinzufügen eines SSIS Scale Out-Workers mit dem Manager für horizontales Hochskalieren

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Der Scale Out-Manager für Integration Services vereinfacht das Hinzufügen des Scale Out-Workers zu Ihrer bereits bestehenden Scale Out-Umgebung. 

Führen Sie die folgenden Schritte aus, um Ihrer Scale Out-Topologie einen Scale Out-Worker hinzufügen:

## <a name="1-install-scale-out-worker"></a>1. Installieren des SSIS Scale Out-Workers
Wählen Sie im Assistenten zum Installieren von SQL Server auf der Seite **Funktionsauswahl** „Integration Services“ und „Worker für horizontales Hochskalieren“ aus. 
![Komponentenauswahl Worker](media/feature-select-worker.PNG)

Auf der Seite **Integration Services Scale Out-Konfiguration – Workerknoten** können Sie auf **Weiter** klicken, um die Konfiguration an dieser Stelle zu überspringen, und den **Scale Out-Manager** verwenden, um die Konfiguration nach der Installation durchzuführen.

Schließen Sie den Installations-Assistenten ab.

## <a name="2-open-the-firewall-on-the-scale-out-master-computer"></a>2. Öffnen Sie die Firewall auf dem Scale Out-Mastercomputer.
Öffnen Sie in der Windows-Firewall auf dem Scale Out-Mastercomputer den Port, der während der Installation des Scale Out-Masters angegeben wurde (standardmäßig 8391), sowie den Port für SQL Server (standardmäßig 1433).

## <a name="3-add-a-scale-out-worker-with-scale-out-manager"></a>3. Hinzufügen eines SSIS Scale Out-Workers mit dem Manager für horizontales Hochskalieren
Führen Sie SQL Server Management Studio als Administrator aus, und stellen Sie eine Verbindung mit der SQL Server-Instanz des Masters für horizontales Hochskalieren her.

Klicken Sie in Objekt-Explorer mit der rechten Maustaste auf **SSISDB**, und wählen Sie **Manage Scale Out** (Scale Out verwalten) aus. 

![Zentrales Hochskalieren verwalten](media/manage-scale-out.PNG)

Wechseln Sie im Dialogfeld **Scale Out-Manager** zu **Worker-Manager**. Klicken Sie auf die **+** , und befolgen Sie die Anweisungen im Dialogfeld **Connect Worker** (Worker verbinden). 

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen finden Sie unter [Scale Out-Manager](integration-services-ssis-scale-out-manager.md).
