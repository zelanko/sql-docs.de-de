---
title: Optionen (Abfrageergebnisse und "Abhängigkeitsdienste") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
caps.latest.revision: 6
author: mashamsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ecc1b6d238189ca0b9c33dd97d136d3283f1ae6b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37192100"
---
# <a name="options-query-results-and-dependency-services-page"></a>Optionen (Abfrageergebnisse und "Abhängigkeitsdienste")
  Geben Sie auf dieser Seite den Server an, mit dem eine Verbindung für Abhängigkeitsdienste hergestellt werden soll. Mithilfe von Abhängigkeitsdiensten können Sie Informationen zu Abhängigkeiten zwischen [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Objekten und [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Objekten extrahieren, die auf anderen Servern gespeichert sind. Sie objektabhängigkeiten anzeigen, indem die **Objektabhängigkeiten** im Dialogfeld [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
 **Was möchten Sie tun?**  
  
1.  [Öffnen Sie im Dialogfeld Optionen (Abfrage Ergebnisse / "Abhängigkeitsdienste")](#open_dialog)  
  
2.  [Konfigurieren der Optionen](#options)  
  
##  <a name="open_dialog"></a> Öffnen Sie im Dialogfeld Optionen (Abfrage Ergebnisse / "Abhängigkeitsdienste")  
  
1.  In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], klicken Sie auf **Optionen** auf die **Tools** Menü.  
  
2.  Erweitern Sie **Abfrageergebnisse**, und klicken Sie dann auf **Abhängigkeitsdienste**.  
  
##  <a name="options"></a> Konfigurieren der Optionen  
  
### <a name="options"></a>Tastatur  
 **Dependency Services-server**  
 Geben Sie den Server an, auf dem die Abhängigkeitsdienste installiert sind.  
  
 **Authentifizierung**  
 Wählen Sie die Windows-Authentifizierung aus, um sich mithilfe eines Microsoft Windows-Benutzerkontos anzumelden, oder wählen Sie die SQL Server-Authentifizierung aus.  
  
 Wenn ein Benutzer eine Verbindung mit einem angegebenen Benutzernamen und einem Kennwort von einer nicht vertrauenswürdigen Verbindung herstellt, führt SQL Server die Authentifizierung aus, indem überprüft wird, ob ein SQL Server-Anmeldekonto eingerichtet wurde und ob das angegebene Kennwort mit dem zuvor aufgezeichneten übereinstimmt. Wenn SQL Server das Anmeldekonto nicht finden kann, schlägt die Authentifizierung fehl und der Benutzer erhält eine Fehlermeldung.  
  
 **Benutzername**  
 Wenn Sie die SQL Server-Authentifizierung verwenden, geben Sie einen Benutzernamen an.  
  
 **Kennwort**  
 Geben Sie ein Kennwort an, wenn Sie die SQL Server-Authentifizierung verwenden.  
  
 **Testen**  
 Klicken Sie auf die Option, um die Verbindung zu überprüfen.  
  
  
