---
title: SQL Server-Erweiterung „Zentrale Verwaltungsserver“
description: Installieren und Verwenden der SQL Server-Erweiterung „Zentrale Verwaltungsserver“ (Vorschauversion) für Azure Data Studio
ms.reviewer: alayu, maghan, sstein
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.custom: seodec18
ms.date: 06/06/2019
ms.openlocfilehash: 5c866ee04194bcbb1d26598766483f03019ebb47
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758353"
---
# <a name="sql-server-central-management-servers-extension-preview"></a>Erweiterung: zentrale Verwaltungsserver von SQL Server (Vorschauversion)

Die Erweiterung „Zentrale Verwaltungsserver“ ermöglicht es Benutzern, eine Liste von SQL Server-Instanzen zu speichern, die in mindestens einer Gruppe zusammengestellt sind. Aktionen, die mit einer Gruppe zentraler Verwaltungsserver ausgeführt werden, wirken sich auf alle Server in der Servergruppe aus.

Diese Funktion befindet sich derzeit in der ersten Vorschauversion. Probleme und Featureanforderungen können Sie [hier](https://github.com/microsoft/azuredatastudio/issues) mitteilen.

![Erweiterung „Zentrale Verwaltungsserver“](media/sql-server-cms-extension/cms-list.png)

## <a name="install-the-sql-server-central-management-servers-extension"></a>Installieren der SQL Server-Erweiterung „Zentrale Verwaltungsserver“

1. Um den Erweiterungs-Manager zu öffnen und auf die verfügbaren Erweiterungen zuzugreifen, klicken Sie auf das Symbol für Erweiterungen, oder wählen Sie im Menü **Ansicht** den Befehl **Erweiterungen** aus.
2. Wählen Sie eine verfügbare Erweiterung aus, um deren Details anzuzeigen.
1. Wählen Sie die gewünschte Erweiterung (SQL Server „Zentrale Verwaltungsserver“) aus, und **Installieren** Sie diese.

### <a name="how-do-i-start-central-management-servers"></a>Wie wird „Zentrale Verwaltungsserver“ gestartet?
 „Zentrale Verwaltungsserver“ kann angezeigt werden, indem Sie auf das Symbol für Verbindungen geklickt wird (STRG/Cmd+G). Wenn Sie die Erweiterung zum ersten Mal herunterladen, ist die Ansicht „Zentrale Verwaltungsserver“ minimiert, und Sie können Sie öffnen, indem Sie auf **Zentrale Verwaltungsserver** klicken.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zum Konzept von „Zentrale Verwaltungsserver“ [finden Sie hier](https://docs.microsoft.com/sql/ssms/register-servers/create-a-central-management-server-and-server-group).


