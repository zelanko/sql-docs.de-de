---
title: Objekte löschen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.deleteobjects.f1
helpviewer_keywords:
- Delete Objects dialog box
ms.assetid: 49541441-179c-40d3-ba0c-01bcae545984
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 45752cebe285a109463eaa1c8e529f0c45a6734b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159457"
---
# <a name="delete-objects"></a>Objekte löschen
  In diesem Dialogfeld können Sie eine Datenbank oder ein Datenbankobjekt löschen.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Zu löschendes Objekt**  
 Zeigt die Namen, Typen, Besitzer und den Status von zu löschenden Objekten sowie Fehlermeldungen während der Ausführung an.  
  
> [!NOTE]  
>  Das Ausführen von **Löschen** für eine Datenbank entspricht der Verwendung von DROP DATABASE in [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Abhängigkeiten anzeigen**  
 Klicken Sie hier, um sowohl die vom gerade ausgewählten Objekt abhängigen Objekte als auch die Objekte anzuzeigen, von denen das aktuelle Objekt abhängt (Aufwärts- und Abwärtsabhängigkeit). Die im Dialogfeld **Abhängigkeiten anzeigen** angezeigten Informationen sind schreibgeschützt.  
  
> [!NOTE]  
>  Die Schaltfläche **Abhängigkeiten anzeigen** wird nicht für alle Datenbankobjekttypen angezeigt. Wenn Sie die Abhängigkeiten anzeigen möchten und die Schaltfläche **Abhängigkeiten anzeigen** nicht verfügbar ist, klicken Sie im Objekt-Explorer mit der rechten Maustaste auf das Objekt, und klicken Sie dann auf **Abhängigkeiten anzeigen**.  
  
 **Sicherungs- und Wiederherstellungsverlaufsinformationen für Datenbanken löschen**  
 Wird nur angezeigt, wenn eine Datenbank gelöscht wird. Bei Aktivierung dieses Kontrollkästchens wird der Sicherungs- und Wiederherstellungsverlauf für die betroffene Datenbank aus der **msdb** -Datenbank gelöscht.  
  
 **Bestehende Verbindungen schließen**  
 Wird nur angezeigt, wenn eine Datenbank gelöscht wird. Bei Aktivierung dieses Kontrollkästchens werden die Verbindungen zur betreffenden Datenbank beendet.  
  
  