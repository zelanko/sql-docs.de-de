---
title: Optionen (Seite "Abfrageergebnisse und Abhängigkeits Dienste") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.QueryResults.DependencyServicesGeneral
ms.assetid: dd7f6c31-7d7f-4972-854a-1419a2826dca
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: d19228fdf17788e9118367a6f0f0eb3be90cb72a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84930131"
---
# <a name="options-query-results-and-dependency-services-page"></a>Optionen (Abfrageergebnisse und Seite „Abhängigkeitsdienste“)
  Geben Sie auf dieser Seite den Server an, mit dem eine Verbindung für Abhängigkeitsdienste hergestellt werden soll. Mithilfe von Abhängigkeitsdiensten können Sie Informationen zu Abhängigkeiten zwischen [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Objekten und [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Objekten extrahieren, die auf anderen Servern gespeichert sind. Objektabhängigkeiten werden mithilfe des Dialog Felds **Objektabhängigkeiten** in angezeigt [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] .  
  
 **Was möchten Sie tun?**  
  
1.  [Öffnen des Dialogfelds "Optionen" (Seite "Abfrageergebnisse"/"Abhängigkeitsdienste")](#open_dialog)  
  
2.  [Konfigurieren der Optionen](#options)  
  
##  <a name="open-the-options-query-resultsdependency-services-page-dialog-box"></a><a name="open_dialog"></a>Öffnen Sie das Dialog Feld Optionen (Seite Abfrageergebnisse/Abhängigkeits Dienste).  
  
1.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] Klicken Sie **in im** Menü Extras auf **Optionen** .  
  
2.  Erweitern Sie **Abfrageergebnisse**, und klicken Sie dann auf **Abhängigkeitsdienste**.  
  
##  <a name="configure-the-options"></a><a name="options"></a>Konfigurieren der Optionen  
  
### <a name="options"></a>Tastatur  
 **Dependency Services-Server**  
 Geben Sie den Server an, auf dem die Abhängigkeitsdienste installiert sind.  
  
 **Authentifizierung**  
 Wählen Sie die Windows-Authentifizierung aus, um sich mithilfe eines Microsoft Windows-Benutzerkontos anzumelden, oder wählen Sie die SQL Server-Authentifizierung aus.  
  
 Wenn ein Benutzer eine Verbindung mit einem angegebenen Benutzernamen und einem Kennwort von einer nicht vertrauenswürdigen Verbindung herstellt, führt SQL Server die Authentifizierung aus, indem überprüft wird, ob ein SQL Server-Anmeldekonto eingerichtet wurde und ob das angegebene Kennwort mit dem zuvor aufgezeichneten übereinstimmt. Wenn SQL Server das Anmeldekonto nicht finden kann, schlägt die Authentifizierung fehl und der Benutzer erhält eine Fehlermeldung.  
  
 **Benutzername**  
 Wenn Sie die SQL Server-Authentifizierung verwenden, geben Sie einen Benutzernamen an.  
  
 **Kennwort**  
 Geben Sie ein Kennwort an, wenn Sie die SQL Server-Authentifizierung verwenden.  
  
 **Test**  
 Klicken Sie auf die Option, um die Verbindung zu überprüfen.