---
title: Azure Arc-Erweiterung (Vorschauversion)
description: Hier erfahren Sie, wie Sie die Azure Arc-Erweiterung installieren und verwenden, um Azure Arc-Datendienste auszuprobieren.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.reviewer: maghan, sstein
ms.custom: ''
ms.date: 09/22/2020
ms.openlocfilehash: 3bcdd76cf143c94dc1e200a21972d00419f26b96
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725211"
---
# <a name="azure-arc-extension-for-azure-data-studio-preview"></a>Azure Arc-Erweiterung für Azure Data Studio (Vorschauversion)

Die [Azure Arc-Erweiterung (Vorschauversion)](/azure/azure-arc/data/) ist eine Erweiterung zum Erstellen und Verwalten von Azure Arc-Datendienstressourcen.

**Zu den wichtigsten Aktionen gehören:**
- Erstellen einer Ressource
    - Datencontroller
    - SQL Managed Instance für Azure Arc
    - PostgreSQL für Azure Arc
- Verwalten einer Ressource
    - Anzeigen des Datencontrollerdashboards
    - Anzeigen des SQL Managed Instance-Dashboards für Azure Arc
    - Anzeigen des PostgreSQL-Dashboards für Azure Arc
- Ausführen eines Jupyter-Notebooks für Azure Arc

## <a name="install-the-extension"></a>Installieren der Erweiterung
- Installieren Sie die **Azure Data CLI**-Erweiterung aus dem Katalog.
- Installieren Sie die **Azure Arc**-Erweiterung aus dem Katalog.
- Starten Sie Azure Data Studio neu.

## <a name="sign-in-with-azure-account"></a>Anmelden mit Azure-Konto
1. Klicken auf „Konten“ unten links
1. Klicken auf „Konto hinzufügen“
1. Durch diese Aktion wird ein Browser gestartet. Melden Sie sich bei Ihrem Azure-Konto an.

## <a name="create-a-resource"></a>Erstellen einer Ressource
Diese Erweiterung unterstützt die Bereitstellung von Azure Arc-Datencontrollern, Postgres für Azure Arc und SQL Managed Instance für Azure Arc. Bereitstellungen können über den integrierten Bereitstellungs-Assistenten ausgeführt werden.

1. Klicken Sie auf das Viewlet „Verbindungen“ auf der linken Aktivitätsleiste.
1. Klicken auf die drei Punkte und dann auf **Neue Bereitstellung**
1. Befolgen Sie die Anweisungen, um eine neue Azure Arc-Ressource zu erstellen.

## <a name="manage-a-resource"></a>Verwalten einer Ressource
Nachdem Sie einen Azure Arc-Datencontroller mit azdata, dem Azure-Portal oder Azure Data Studio bereitgestellt haben, können Sie über Azure Data Studio eine Verbindung mit diesem herstellen.

1. Öffnen Sie das Viewlet „Verbindungen“ auf der linken Aktivitätsleiste.
1. Erweitern **Azure Arc controllers** (Azure Arc-Controller).
1. Klicken Sie auf **Connect controller** (Controller verbinden).
1. Füllen Sie die Parameterfelder aus, und stellen Sie eine Verbindung her.

Nachdem die Verbindung hergestellt wurde, können Sie die auf dem Datencontroller bereitgestellten Ressourcen anzeigen. Klicken Sie mit der rechten Maustaste, und klicken Sie dann auf **Verwalten**, um auf das Ressourcendashboard zuzugreifen.  

Diese Dashboards bieten zusätzliche Informationen über die Ressource einschließlich der Option zum Öffnen im Azure-Portal.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zu Azure Arc-Datendiensten [finden Sie in der Dokumentation](/azure/azure-arc/data/).