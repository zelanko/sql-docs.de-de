---
title: Quell Code Verwaltung ändern | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62812746"
---
# <a name="change-source-control"></a>Quellcodeverwaltung ändern
  Erstellt und verwaltet die Verbindungen und Bindungen, über die eine lokal gespeicherte Projektmappe bzw. ein Projekt mit einem Ordner in der Datenbank für die Quellcodeverwaltung verknüpft ist.  
  
## <a name="dialog-box-access"></a>Zugriff auf das Dialogfeld  
 Wählen Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ein Element im Projektmappen-Explorer aus. Klicken Sie im Menü **Datei** auf **Quell**Code Verwaltung, und **ändern**Sie dann Quell Code Verwaltung.  
  
> [!NOTE]  
>  Als Alternative können Sie auch im Projektmappen-Explorer mit der rechten Maustaste auf das entsprechende Element klicken, um das Dialogfeld aufzurufen.  
  
## <a name="options"></a>Optionen  
 **Zwick**  
 Ordnet ausgewählte Elemente einem angegebenen Speicherort auf dem Quellcode-Verwaltungsserver zu. So können Sie mit dieser Schaltfläche beispielsweise den letzten bekannten Ordner und die Datenbank auf dem Quellcode-Verwaltungsserver binden. Wenn kein zuletzt verwendeter Serverordner bzw. eine Serverdatenbank gefunden wird, werden Sie aufgefordert einen anderen bzw. eine andere anzugeben.  
  
 **Durchsuchen**  
 Navigiert zu einem neuen Speicherort auf dem Quellcode-Verwaltungsserver für das angegebene Element.  
  
 **Spalten**  
 Identifizieren Sie die anzuzeigenden Spalten und die Reihenfolge, in der Sie angezeigt werden.  
  
 **Herstellen einer Verbindung**  
 Erstellt eine Verbindung zwischen ausgewählten Elementen und dem Quellcode-Verwaltungsserver.  
  
 **Verbunden**  
 Zeigt den Verbindungsstatus einer ausgewählten Projektmappe bzw. eines Projekts an.  
  
 **Verschluss**  
 Trennt die Verbindung der lokalen Kopie einer Projektmappe bzw. eines Projekts auf Ihrem Computer zu ihrer Masterkopie in der Datenbank. Verwenden Sie diesen Befehl, bevor Sie Ihren Computer vom Quellcode-Verwaltungsserver trennen (z. B., wenn Sie auf Ihrem Laptop offline arbeiten).  
  
 **OK**  
 Nimmt die im Dialogfeld vorgenommenen Änderungen an.  
  
 **Anbieter**  
 Zeigt den Namen Ihres Quellcodeverwaltungs-Plug-Ins an.  
  
 **Aktualisieren**  
 Aktualisiert die in diesem Dialogfeld aufgelisteten Verbindungsinformationen für alle Projekte.  
  
 **Serverbindung**  
 Gibt die Bindung des Elements an einen Quellcode-Verwaltungsserver an.  
  
 **Server Name**  
 Zeigt den Namen des Quellcode-Verwaltungsservers an, an den die betreffende Projektmappe bzw. das Projekt gebunden ist.  
  
 **Projektmappe/Projekt**  
 Zeigt die Namen der einzelnen Projektmappen und Projekte in der aktuellen Auswahl an.  
  
 **Sortieren**  
 Sortiert die Reihenfolge der angezeigten Spalten.  
  
 **Status**  
 Identifiziert den Bindungs- und Verbindungsstatus eines Elements. Folgende Optionen sind möglich:  
  
|**Option**|**Beschreibung**|  
|----------------|---------------------|  
|Gültig|Das Element ist ordnungsgemäß an den Serverordner, zu dem es gehört, gebunden und mit ihm verbunden.|  
|Ungültig|Das Element ist ordnungsgemäß an den Serverordner, zu dem es gehört, gebunden bzw. von ihm getrennt. Verwenden Sie den Befehl **zur Quell Code Verwaltung hinzufügen** anstelle von **Bind** für dieses Element.|  
|Unbekannt|Der Status des Elements, das sich unter Quellcodeverwaltung befindet, wurde noch nicht ermittelt.|  
|Nicht gesteuert|Das Element wurde nicht unter Quellcodeverwaltung gestellt.|  
  
 **Bindung**  
 Zeigt das Dialogfeld **Quell** Code Verwaltung an, in dem Sie ausgewählte Elemente aus der Quell Code Verwaltung entfernen und die Zuordnung der Elemente zu Ihren aktuellen Ordnern dauerhaft aufheben können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Quellcodeverwaltung des Projektmappen-Explorers](../../2014/database-engine/solution-explorer-source-control.md)  
  
  
