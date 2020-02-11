---
title: Alle Prinzipale durchsuchen (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.browseprincipals.f1
ms.assetid: f11d2c5e-ee05-45f3-8dc2-0feb99b2f76f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 46d6fd5d4ecd821a3ccfeb35679e8fa7bab6104e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62771718"
---
# <a name="browse-all-principals-dialog-box"></a>Alle Prinzipale durchsuchen (Dialogfeld)
  Wählen Sie über das Dialogfeld **Alle Prinzipale durchsuchen** einen Datenbankprinzipal aus und ändern Sie die Berechtigungen des Prinzipals für das ausgewählte Projekt oder alle in einem ausgewählten Ordner enthaltenen Projekte.  
  
 **Was möchten Sie tun?**  
  
-   [Öffnen des Dialogfelds "Alle Prinzipale durchsuchen"](#open_dialog)  
  
-   [Konfigurieren der Optionen](#options)  
  
##  <a name="open_dialog"></a> Öffnen des Dialogfelds "Alle Prinzipale durchsuchen"  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung zum [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server her.  
  
     Sie stellen eine Verbindung mit der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Instanz her, die den SSISDB-Katalog hostet.  
  
2.  Erweitern Sie im Objekt-Explorer die Struktur, um den Knoten **Integration Services-Kataloge** anzuzeigen.  
  
3.  Erweitern Sie den **SSISDB** -Knoten.  
  
4.  Klicken Sie zum Ändern der Berechtigungen des Prinzipals für alle in einem ausgewählten Ordner enthaltenen Projekte mit der rechten Maustaste auf den Ordner, und klicken Sie anschließend auf **Eigenschaften**.  
  
     Wenn Sie die Berechtigungen des Prinzipals für ein ausgewähltes Projekt ändern möchten, erweitern Sie den Ordner, der das Projekt enthält, klicken Sie mit der rechten Maustaste auf das Projekt, und klicken Sie anschließend auf **Eigenschaften**.  
  
5.  Wählen Sie die Seite **Berechtigungen** aus, und klicken Sie dann auf **Durchsuchen**.  
  
##  <a name="options"></a> Konfigurieren der Optionen  
 Auf dieser Seite werden die Prinzipale aus der Katalogsicht sys.database_principals der SSISDB-Datenbank angezeigt.  
  
 Durch Auswählen von Prinzipalen werden diese der Liste **Anmeldenamen oder Rollen** auf der Seite **Berechtigungen** des übergeordneten Dialogfelds hinzugefügt, sobald Sie auf **OK** geklickt und das Dialogfeld **Alle Prinzipale durchsuchen** geschlossen haben. Nachdem Sie die Prinzipale der Liste **Anmeldenamen oder Rollen** hinzugefügt haben, können Sie die entsprechenden Berechtigungen für das ausgewählte Projekt ändern.  
  
 **Spaltenauswahl**  
 Mit dieser Option können Sie den Prinzipal der Liste **Anmeldenamen oder Rollen** auf der Seite **Berechtigungen** im übergeordneten Dialogfeld hinzufügen.  
  
 **Symbolspalte**  
 Ein Symbol, das dem **Typ** des Prinzipals entspricht.  
  
 **Name**  
 Der Name des Prinzipals.  
  
 **Typ**  
 Der Typ des Prinzipals. Häufig verwendeten Typen sind folgende:  
  
-   SQL-Benutzer  
  
-   Windows-Benutzer  
  
-   Datenbankrolle  
  
  
