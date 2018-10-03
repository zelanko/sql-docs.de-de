---
title: Alle Prinzipale durchsuchen (Dialogfeld) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.browseprincipals.f1
ms.assetid: f11d2c5e-ee05-45f3-8dc2-0feb99b2f76f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8389729eac371f01d32d610d69d1d1a8a3d9e8dd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128250"
---
# <a name="browse-all-principals-dialog-box"></a>Alle Prinzipale durchsuchen (Dialogfeld)
  Verwenden Sie das Dialogfeld **Alle Prinzipale durchsuchen** , um einen Datenbankprinzipal auszuwählen und die Berechtigungen des Prinzipals für das ausgewählte Projekt oder alle in einem ausgewählten Ordner enthaltenen Projekte zu ändern.  
  
 **Was möchten Sie tun?**  
  
-   [Öffnen des Dialogfelds "Alle Prinzipale durchsuchen"](#open_dialog)  
  
-   [Konfigurieren der Optionen](#options)  
  
##  <a name="open_dialog"></a> Öffnen des Dialogfelds "Alle Prinzipale durchsuchen"  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung zum [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server her.  
  
     Sie stellen eine Verbindung mit der [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Instanz her, die den SSISDB-Katalog hostet.  
  
2.  Erweitern Sie im Objekt-Explorer die Struktur, um den Knoten **Integration Services-Kataloge** anzuzeigen.  
  
3.  Erweitern Sie den **SSISDB** -Knoten.  
  
4.  Um die Berechtigungen des Prinzipals für alle in einem ausgewählten Ordner enthaltenen Projekte zu ändern, klicken Sie mit der rechten Maustaste auf den Ordner, und klicken Sie dann auf **Eigenschaften**.  
  
     Um die Berechtigungen des Prinzipals für ein ausgewähltes Projekt zu ändern, erweitern Sie den Ordner, der das Projekt enthält, klicken Sie mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.  
  
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
  
  
