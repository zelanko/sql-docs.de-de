---
description: Objekte löschen
title: Objekte löschen
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.deleteobjects.f1
helpviewer_keywords:
- Delete Objects dialog box
ms.assetid: 49541441-179c-40d3-ba0c-01bcae545984
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 71ae7cf7aaff0eab0701ef83f7258389e52eb37e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497428"
---
# <a name="delete-objects"></a>Objekte löschen
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
In diesem Dialogfeld können Sie eine Datenbank oder ein Datenbankobjekt löschen.  
  
## <a name="ui-element-list"></a>Liste der Benutzeroberflächenelemente  
**Zu löschendes Objekt**  
Zeigt die Namen, Typen, Besitzer und den Status von zu löschenden Objekten sowie Fehlermeldungen während der Ausführung an.  
  
> [!NOTE]  
> Das Ausführen von **Löschen** für eine Datenbank entspricht der Verwendung von DROP DATABASE in [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
**Abhängigkeiten anzeigen**  
Klicken Sie hier, um sowohl die vom gerade ausgewählten Objekt abhängigen Objekte als auch die Objekte anzuzeigen, von denen das aktuelle Objekt abhängt (Aufwärts- und Abwärtsabhängigkeit). Die im Dialogfeld **Abhängigkeiten anzeigen** angezeigten Informationen sind schreibgeschützt.  
  
> [!NOTE]  
> Die Schaltfläche **Abhängigkeiten anzeigen** wird nicht für alle Datenbankobjekttypen angezeigt. Wenn Sie die Abhängigkeiten anzeigen möchten und die Schaltfläche **Abhängigkeiten anzeigen** nicht verfügbar ist, klicken Sie im Objekt-Explorer mit der rechten Maustaste auf das Objekt, und klicken Sie dann auf **Abhängigkeiten anzeigen**.  
  
**Sicherungs- und Wiederherstellungsverlaufsinformationen für Datenbanken löschen**  
Wird nur angezeigt, wenn eine Datenbank gelöscht wird. Bei Aktivierung dieses Kontrollkästchens wird der Sicherungs- und Wiederherstellungsverlauf für die betroffene Datenbank aus der **msdb** -Datenbank gelöscht.  
  
**Bestehende Verbindungen schließen**  
Wird nur angezeigt, wenn eine Datenbank gelöscht wird. Bei Aktivierung dieses Kontrollkästchens werden die Verbindungen zur betreffenden Datenbank beendet.  
  
