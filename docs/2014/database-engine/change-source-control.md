---
title: Quellcodeverwaltung ändern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- IDD_SCC_CONNECTION_DIALOG
helpviewer_keywords:
- Change Source Control dialog box
ms.assetid: e6a5d83c-5809-4c56-907a-73d0c7ccdd7a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 939e3befd0cbec87dbba7046761637c4b7655e22
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48092540"
---
# <a name="change-source-control"></a>Quellcodeverwaltung ändern
  Erstellt und verwaltet die Verbindungen und Bindungen, über die eine lokal gespeicherte Projektmappe bzw. ein Projekt mit einem Ordner in der Datenbank für die Quellcodeverwaltung verknüpft ist.  
  
## <a name="dialog-box-access"></a>Zugriff auf das Dialogfeld  
 Wählen Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ein Element im Projektmappen-Explorer aus. Auf der **Datei** Menü klicken Sie auf **Quellcodeverwaltung**, und klicken Sie dann **Quellcodeverwaltung ändern**.  
  
> [!NOTE]  
>  Als Alternative können Sie auch im Projektmappen-Explorer mit der rechten Maustaste auf das entsprechende Element klicken, um das Dialogfeld aufzurufen.  
  
## <a name="options"></a>Tastatur  
 **Binden**  
 Ordnet ausgewählte Elemente einem angegebenen Speicherort auf dem Quellcode-Verwaltungsserver zu. So können Sie mit dieser Schaltfläche beispielsweise den letzten bekannten Ordner und die Datenbank auf dem Quellcode-Verwaltungsserver binden. Wenn kein zuletzt verwendeter Serverordner bzw. eine Serverdatenbank gefunden wird, werden Sie aufgefordert einen anderen bzw. eine andere anzugeben.  
  
 **Durchsuchen**  
 Navigiert zu einem neuen Speicherort auf dem Quellcode-Verwaltungsserver für das angegebene Element.  
  
 **Spalten**  
 Identifizieren Sie die anzuzeigenden Spalten sowie die Reihenfolge, in der sie angezeigt werden.  
  
 **Verbinden**  
 Erstellt eine Verbindung zwischen ausgewählten Elementen und dem Quellcode-Verwaltungsserver.  
  
 **Verbunden**  
 Zeigt den Verbindungsstatus einer ausgewählten Projektmappe bzw. eines Projekts an.  
  
 **Trennen**  
 Trennt die Verbindung der lokalen Kopie einer Projektmappe bzw. eines Projekts auf Ihrem Computer zu ihrer Masterkopie in der Datenbank. Verwenden Sie diesen Befehl, bevor Sie Ihren Computer vom Quellcode-Verwaltungsserver trennen (z. B., wenn Sie auf Ihrem Laptop offline arbeiten).  
  
 **OK**  
 Nimmt die im Dialogfeld vorgenommenen Änderungen an.  
  
 **Anbieter**  
 Zeigt den Namen Ihres Quellcodeverwaltungs-Plug-Ins an.  
  
 **Aktualisieren**  
 Aktualisiert die in diesem Dialogfeld aufgelisteten Verbindungsinformationen für alle Projekte.  
  
 **Serverbindung**  
 Gibt die Bindung des Elements an einen Quellcode-Verwaltungsserver an.  
  
 **Servername**  
 Zeigt den Namen des Quellcode-Verwaltungsservers an, an den die betreffende Projektmappe bzw. das Projekt gebunden ist.  
  
 **Projektmappe oder eines Projekts**  
 Zeigt die Namen der einzelnen Projektmappen und Projekte in der aktuellen Auswahl an.  
  
 **Sort**  
 Sortiert die Reihenfolge der angezeigten Spalten.  
  
 **Status**  
 Identifiziert den Bindungs- und Verbindungsstatus eines Elements. Optionen sind möglich:  
  
|**Option**|**Beschreibung**|  
|----------------|---------------------|  
|Gültig|Das Element ist ordnungsgemäß an den Serverordner, zu dem es gehört, gebunden und mit ihm verbunden.|  
|Ungültig|Das Element ist ordnungsgemäß an den Serverordner, zu dem es gehört, gebunden bzw. von ihm getrennt. Verwenden der **zur Quellcodeverwaltung hinzufügen** Befehl anstelle von **binden** für dieses Element.|  
|Unknown|Der Status des Elements, das sich unter Quellcodeverwaltung befindet, wurde noch nicht ermittelt.|  
|Nicht gesteuert|Das Element wurde nicht unter Quellcodeverwaltung gestellt.|  
  
 **Aufheben der Bindung**  
 Anzeigen der **Quellcodeverwaltung** im Dialogfeld können Sie ausgewählte Elemente aus der quellcodeverwaltung zu entfernen und dauerhaft von ihren aktuellen Ordnern trennen.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltung des Projektmappen-Explorers](../../2014/database-engine/solution-explorer-source-control.md)  
  
  
